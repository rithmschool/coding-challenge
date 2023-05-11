# Rithm Coding Challenge

## What’s Required

Build a full stack application that does the following:

### Backend

Write an API endpoint that returns a filtered set of users from the csv provided below.

* Your API endpoint URL is /users
* Your API responds in the above format with valid GeoJSON
* Your API should correctly filter any combination of API parameters
* Your API should utilize a database
* Your API should support paginating the number of resulting users
* This should be built using Express or Flask
* Your API should be tested 

## API Structure

| Parameter | Description                                    |
| --------- | ---------------------------------------------- |
| fav_color | Your favorite color                            |
| dist      | Maximum match distance in miles                |
| origin    | lat/long string of your location               |
| min_age   | Minimum age preference                         |
| max_age   | Maximum age preference                         |

Given the following request:

GET `/users?fav_color=red&dist=100&origin=37.774929,-122.419416&min_age=21&max_age=29`

The expected response should contain the following:

```json
{
  "metadata": {
    "path": "/users",
    "query": {
      "fav_color": "red",
      "dist": 100,
      "origin": "37.774929,-122.419416",
      "min_age": 21,
      "max_age": 29
    }
  },
  "num_results": 1,
  "results": [
    {
      "type": "user",
      "locationHistory": {
        "type": "FeatureCollection",
        "features": [
          {
            "type": "Feature",
            "properties": {
              "city": "Oakland"
            },
            "geometry": {
              "type": "Point",
              "coordinates": [-122.2711, 37.8044]
            }
          },
          {
            "type": "Feature",
            "properties": {
              "city": "San Francisco"
            },
            "geometry": {
              "type": "Point",
              "coordinates": [-122.419416, 37.774929]
            }
          }
        ]
      },
      "properties": {
        "id": 1,
        "name": "Taylor Swift",
        "age": 27,
        "fav_color": "red"
      }
    }
  ]
}
```

All query parameters are optional. If a query parameter is missing or the value is invalid, you should skip the related filter.

All minimum and maximum fields should be inclusive (e.g. min_age=21&max_age=23 should return users with an age of 21, 22, or 23).

### Frontend

Your application should have a frontend built with React, that displays a form and allows a user to input a favorite color, distance, origin and min and max age. When the form is submitted, a map should render with markers for the location of the users found. You can use Mapbox, Leaflet or any provider for this functionality. 

