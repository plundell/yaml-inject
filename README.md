# YAML Inject

This is a simple npm module which injects the contents of the partial .yaml files into a specific property of the main .yaml file.

### Example
Let's say you have the following files:

*main.yaml*:
```yaml
title: "Team"
players:
description: "This is a soccer team."
```
*partial1.yaml*:
```yaml
bob:
  name: "Bob"
```
*partial2.yaml*:
```yaml
steve:
  name: "Steve"
  age: 15
```
This module can then generate *output.yaml* with the following contents:
```yaml
title: "Team"
players:
  bob:
    name: "Bob"
  steve:
    name: "Steve"
    age: 15
description: "This is a soccer team."
```

## Usage
You can either include [src/index.js](src/index.js) in another script and call the exported function:
```javascript
const yamlInject=require('yaml-inject')
yamlInject(mainFilePath,partialsGlobString,outputFilePath,propertyPath)
```
or you can call the binary directly from the command line:

```bash
npx yaml-merge --main <mainFilePath> --partials <partialsGlobString> --output <outputFilePath> --property <propertyPath>
```
where:  
 - *mainFilePath* is the path to the main YAML file  
 - *partialsGlobString* is the glob string to match the partial YAML files (e.g. 'partials/*.yml')  
 - *outputFilePath* is the path where the merged YAML file will be saved  
 - *propertyPath* is the property path in the main file where the partial YAML contents should be inserted (e.g. 'players')  

