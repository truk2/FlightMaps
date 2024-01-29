FlightMaps
==========

Flights provides a simple HTML template for creating a map with flights plotted between arrival and destination. 

Description
-----------

The FLightsMaps project exists only to provide a HTML Template. This allows for easier collaboration with citizen developers. 
While technical team members may write code applications that pull in the HTML from github, less technical and graphical focussed team members can create and PUSH changes to the HTML.


Usage
-----

Local and third party applications may download the HTML template to create a map view with the user's desired set of flights.

Note that on creation of the map it will:
- Apply variable line thickness as defined by the user
- Be zoomed to match bounds of included flight area
- Use geodesic paths to match curvature of the earth
- **NOT** include location markers


Requirements
============
As this project is merely a text template, it has very few requirements.  
It may be implemented on any platform capable of HTML5 with JS scripting.
Required string formats are discussed in the section on _Required String Variables_



Required String Variables
=========================
Note that the HTML template includes the following placeholders that must be replaced with the users data

* "GOOGLE_MAPS_API_STRING"
* "DESTINATIONS_COLLECTION"
* "FLIGHTPATHS_COLLECTION"

As these strings variables are used in 'Find/Replace' opperations they MUST NOT BE RENAMED.

"GOOGLE_MAPS_API_STRING"
------------------------
This placeholder must be replaced with a string in the form:
"https://maps.googleapis.com/maps/api/js?key=INSERT_KEY_HERE"

example of use:
`<script async defer src="GOOGLE_MAPS_API_STRING&callback=initMap">`


"DESTINATIONS_COLLECTION"
-------------------------
This variable represents a collection of locations as terminal points for the included flights (ie Airports) in Json format. IE:

[{name: "NAME1", coordinates: {lat: xx.xxxxx, lng: yy.yyyyy},
{name: "NAME2", coordinates: {lat: xx.xxxxx, lng: yy.yyyyy},
{name: "NAME3", coordinates: {lat: xx.xxxxx, lng: yy.yyyyy}]


"FLIGHTPATHS_COLLECTION"
------------------------
This variable represents a collect of pairs of locations from the DESTINATIONS_COLLECTION that will have routes plotted on the maps
This collection should be in Json format and include required line thickness as defined below:

[{origin: destinations[x_].coordinates, destination: destinations[x_].coordinates, lineThickness: z1},
{origin: destinations[x_].coordinates, destination: destinations[x_].coordinates, lineThickness: z2},
{origin: destinations[x_].coordinates, destination: destinations[x_].coordinates, lineThickness: z3}]

where x_ is any valid index in the DESTINATIONS_COLLECTION
where z_ is any valid integer or double value representing the required line thickness.

