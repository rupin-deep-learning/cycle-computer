# Web Cycling Computer
This is a single-file, client-side web application that functions as a cycling computer. It can track and display key metrics for a bike ride, either using your device's live GPS or a simulated ride. All ride data is stored locally in your browser's storage, and you have the option to download it as a CSV or GPX file.

## Features
Live GPS Mode: Uses the browser's Geolocation API to track your ride in real-time.

Simulation Mode: Simulates a ride on a predefined circular path, useful for indoor training or testing.

Ride Metrics: Displays real-time data including speed, power, distance, elevation, grade, and elapsed time.

Map Visualization: Plots your ride on a dynamic map using the Leaflet.js library.

Physics-Based Power Calculation: Estimates power output based on speed, grade, and a configurable set of rider and bike parameters.

Ride History: Saves ride data locally in your browser, allowing you to review past rides, view them on the map, and export them.

Customizable Settings: Adjust rider mass, rolling resistance, aerodynamic drag coefficients (CdA), drivetrain efficiency, and air density to get more accurate power estimations.

Data Export: Download ride data as a CSV or GPX file.

## How to Use
Simply open the index.html file in any modern web browser. There is no need for a web server or any dependencies other than an internet connection to load the external libraries (Leaflet and Pako).

Select Mode: Choose between "Live GPS" or "Simulation" from the dropdown menu.

Start Ride: Click the Start button to begin recording your ride.

Pause/Resume: Click Pause to temporarily stop the timer and data collection. Click it again to Resume.

Stop Ride: Click Stop to end the ride. The ride data will be saved to your history automatically.

View History: Click the Ride History button to open a panel with a list of all your saved rides. From here, you can load a ride onto the map, delete it, or export it.

Adjust Settings: Click the Settings button to open a panel where you can fine-tune the physics parameters for power calculation.

## File Structure
This is a single-file application, so all the HTML, CSS, and JavaScript are contained within the index.html file.

index.html: The main file containing the entire application.

## Technology Stack
HTML5: The structure of the web page.

CSS3: For styling the user interface.

JavaScript (ES6+): Handles all the application logic, including state management, event listeners, and calculations.

Leaflet.js: An open-source JavaScript library for interactive maps.

pako.js: A zlib-compatible compression library used to compress ride data before storing it in local storage.

## Known Issues & Fixes
The original code had three issues that have been addressed in this version:

Obscured History Panel: The history panel was partially hidden behind the map due to an incorrect z-index. The CSS has been updated to give the history panel a higher z-index value, ensuring it appears on top of the map.

Simulation Ride Doesn't Resume: The simulation timer was not properly resuming after being paused. The fix involves adding a simTimeoutId variable to store the timer ID, allowing the application to clear the timeout when paused and restart it when resumed.

Live GPS Timer Resumes Incorrectly: When paused and resumed, the live GPS timer would count the entire elapsed time, including the pause duration. The fix introduces a pauseTime variable to store the timestamp when the ride is paused, and then adjusts the startTime upon resuming to account for the pause duration.
