# Scheduling Workbench

A responsive, browser-based room allocation and timetable optimisation workbench. Everything runs in one HTML file, with no backend, login, build step, or external JavaScript dependencies.

## Use it

Open [index.html](index.html) locally, or use the GitHub Pages website after Pages is enabled in repository settings.

## Features

- **Timetable-first workspace:** desktop sidebar / mobile tabs, colour-coded room schedules, utilisation metrics and unused-room summary.
- **Class editor:** add, edit, delete classes; set student counts, durations, required facilities, acceptable room types, flexible time windows, fixed slots, and preferred starts.
- **Room editor:** add, edit, delete rooms; set capacity, type, facilities and unavailability.
- **Randomise classes:** choose how many classes (1–24) to generate. The generator constructs a feasible non-overlapping reference placement against the current rooms.
- **Randomise rooms:** choose how many rooms (1–12) to generate. When the requested count retains all existing room templates, generated rooms preserve existing capacities/facilities or improve them, maintaining feasibility of any previously feasible schedule.
- **Optimisation:** a browser-side branch-and-bound constraint search that assigns all classes and minimises the number of rooms used, while meeting hard constraints. The interface differentiates a feasible solution from a proven optimum.
- **Scenario files:** import/export JSON; export the solved timetable as CSV. Edits are cached in browser local storage when available.
- **Offline-first:** no API calls or tracking; all scenario data stays in the browser unless exported manually.

## Quick start

1. Open the **Classes** or **Rooms** tab to edit individual records, or use **Randomise** to replace a set with fresh demo data.
2. Click **Run optimisation**.
3. Inspect the timetable, room utilisation and room-free statistics.
4. Export CSV or JSON as required.

Randomisation **replaces** the relevant records after asking for confirmation. Export the JSON first if you want a backup.

## Solver behaviour

The search respects class size, room capacity, required facilities, room types, permitted start windows, durations, room availability and non-overlap. It minimises the number of rooms used (equivalent to maximising unused rooms). If the search hits its effort cap, it may return the best feasible solution found without claiming global optimality. Some input scenarios may be infeasible.

The demo supports up to **24 classes**, **12 rooms** and **32 time slots**. For much larger instances, use a dedicated server-side MILP/CP-SAT solver.

## GitHub Pages

In the repository, go to **Settings → Pages → Build and deployment**, select **Deploy from a branch**, then choose **main** and **/(root)**. GitHub Pages will serve the root `index.html` at:

https://timothywong731.github.io/scheduling-workbench/

This URL becomes active after GitHub Pages is enabled and deployment completes.

## License

No license has been added. By default, standard copyright rules apply.
