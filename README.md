An Implementation of Initializing GATT Server from a JSON file

# Features

* Initialize GATT server from a json file

# A brief look

When I come first with the original repo (https://github.com/nettlep/gobbledegook), GATT server is initialized with static code.
So I'm trying to create a version allowing to setup GATT server structure from a JSON - a more familiar approach.

The user just need to handle the remain things - the dataSetter and dataGetter delegate method in main application.

An example of JSON file wil be as below :
```json
{  "services": [
    { "name": "device",
      "uuid": "180A",
      "characteristics": [
        { "name": "mfgr_name",
          "uuid": "2A29",
          "flags": ["read", "write"],
          "default-value": "Acme Inc."
        },
        { "name": "model_num",
          "uuid": "2A24",
          "flags": ["read", "write"],
          "default-value": "Marvin-PA"
        }]
    },
    { "name": "battery",
      "uuid": "180F",
      "characteristics": [
        { "name": "level",
          "uuid": "2A19",
          "flags": ["read", "write", "notify"],
          "default-value": "60%"
        }]
    }]
}
```
# How to use

This project will use the https://github.com/nlohmann/json for parsing the JSON file

```
git clone "this repo"
git clone https://github.com/ArthurSonzogni/nlohmann_json_cmake_fetchcontent.git
export JSON_LIBRARY_INCLUDE=`pwd`/nlohmann_json_cmake_fetchcontent/include

cd gobbledegook
./configure CXXFLAGS=-I$JSON_LIBRARY_INCLUDE
make

sudo ./src/standalone -d`
```
