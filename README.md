# GIS Mapping Engine
 
An interactive C++ map application built on OpenStreetMap data. You can search for streets and intersections, look up nearby points of interest, and get driving routes between two places. Built by a team of 3 (Jan – Apr 2024).
 
![Map interface](Screenshot%202024-04-05%20200602.png)
 
More screenshots are in [`User Interface (screenshots)`](User%20Interface%20(screenshots)).
 
## Features
 
- **Map loading.** Reads a city's street database and raw OpenStreetMap data, then precomputes the lookups the app needs.
- **Search.** Street search by partial name, plus finding the intersections of a street, the intersections where two streets meet, and the nearest intersection or point of interest to any location.
- **Geometry.** Distances on the Earth's surface, segment and street lengths, travel times from speed limits, turn angles between segments, and polygon areas for map features such as parks and lakes.
- **Routing.** Shortest-time routes between intersections using Dijkstra's algorithm, plus a greedy heuristic for multi-stop routing.
- **Interface.** An interactive map drawn with the EZGL graphics library: pan and zoom, street and feature drawing by type, point-of-interest icons, and route highlighting.
## What's in this repo
 
| File | Contents |
|---|---|
| `m1.cpp` | The map data layer: loading, precomputed data structures, and all query and geometry functions |
| `User Interface (screenshots)/` | Screenshots of the finished app |
 
The routing and drawing code was written in the course repository and isn't included here.
 
## How the data layer works
 
`loadMap()` loads the map once and builds lookup tables, so later queries don't have to rescan the raw data:
 
- Street segments attached to each intersection.
- Intersections on each street.
- Total length of each street.
- Travel time of every street segment, from its length and speed limit.
- OpenStreetMap ways and nodes stored by ID, so their tags can be looked up quickly.
- Map features grouped by shape: single points, closed polygons and open lines.
- The map's latitude and longitude bounds, used to convert coordinates to screen x/y for drawing.
Memory for these tables is reserved up front from the map's counts, so loading a large city doesn't trigger repeated reallocations.
 
## Tech
 
C++ (object-oriented, STL containers and algorithms), OpenStreetMap data, the EZGL/GTK graphics library, Dijkstra's algorithm, Git
 
## Team
 
Built with two teammates. **[Sissi: add your part here, e.g. "I wrote the map data layer (`m1.cpp`) and ..."]**
 
