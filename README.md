# RAM at SotM 2017
This repository contains the datasets used for a [Rural Accessibility Map](http://github.com/WorldBank-Transport/ram) demo at State of the Map US 2017 in Boulder.

## Boundaries
The administrative boundaries are the Commissioner Districts in Boulder county. No significant processing was done, beyond converting it to GeoJSON and setting the right projection.

Source: [Boulder County Geospatial Open Data portal](http://gis-bouldercounty.opendata.arcgis.com/)  
License: [CC BY 4.0](http://creativecommons.org/licenses/by/4.0/)

## Population
The population estimates are Census Block level data for 2010. Processing on the original data:

- reduced to Boulder County Border
- removed all blocks with 0 population
- converted polygons to center points

Source: [Tiger Population & Housing Unit Counts - Block](https://www.census.gov/geo/maps-data/data/tiger-data.html)  
License: Public Domain

## Road network
The road network was downloaded from OSM on October 18 using [Overpass](https://overpass-turbo.eu/#) with the following query:

```
http://overpass-api.de/api/interpreter?data=[out:xml][timeout:900][maxsize:2000000000];(way["highway"](39.85,-105.7,40.277,-105.05);>;);out body;>;
```

- `road_network-osm-baseline.xml` contains the raw OSM data
- `road_network-osm-living_street.xml` contains the same data, but all the highways have a value of `living_street`

Source: [OSM](http://openstreetmap.org)  
License: [ODbL](http://wiki.openstreetmap.org/wiki/Open_Database_License)

## POI
The POI data was downloaded from OSM on October 18 using [Overpass](https://overpass-turbo.eu/#) with the following query:

```
http://overpass-api.de/api/interpreter?data=[out:xml][timeout:900][maxsize:2000000000];(node["microbrewery"="yes"](39.85,-105.7,40.277,-105.05);>;);out body;>;
```

It was turned into geojson with [osmtogeojson](https://tyrasd.github.io/osmtogeojson/).

Source: [OSM](http://openstreetmap.org)  
License: [ODbL](http://wiki.openstreetmap.org/wiki/Open_Database_License)
