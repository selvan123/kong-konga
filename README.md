# Installation & Configuration of Kong and Konga Using Docker


Deployment process of Kong and Konga applications with basic example of accessing an API through the Kong 

## Execute following Docker files
- Dockercmd1 - postgres DB installation for Kong & Konga
- Dockercmd2 - ephemeral container for Kong which will run the appropriate migrations in postgres DB
- Dockercmd3 - Start Kong
- Dockercmd4 - ephemeral container for Konga which will run the appropriate migrations in postgres DB
- Dockercmd5 - Start Konga
## Validations
- curl -i http://{hostip}:8001/
- curl -i http://{hostip}:1337/
## Konga Configuration
- Open browser - http://{hostip}:1337/ and complete the registration
- Click "New Connection"  
- Provide Name as "KongAPIConnection"
- Kong Admin URL : http://{hostip}:8001/

Hit the activate button. If all is set up correctly, Konga will connect to Kong.
### Creating Services and Routes
- Go to services page and add a new service. Fill in the form as follows
- Name : example_service
- Protocols : https
- Host : jsonplaceholder.typicode.com
- Port : 443
- Retries : 5
- Connect timeout/Write timeout/Read timeout : 60000
- Keep other fields blank and Submit Changes

- Go to Route page and add a new route. Fill in the form as follows
- Name : mocking
- Paths: /api [click enter after added this text]
- Path handling : V0
- Https redirect status code : 426
- Regex priority : 0 
- Methods : Get [click enter after added this text]
- Strip Path : YES
    [If Strip path is set to YES, the Path here can be prefixed, such as: /api/users, but it will eventually be mapped to the real back-end API /users]
- Preserve Host : NO
- Protocols : http [click enter after added this text] , https [click enter after added this text] 
- Keep other fields blank and Submit Changes

### Test
 
- curl -i -X GET --url http://{hostip}}:8000/api/users
- curl -i -X GET --url http://{hostip}}:8000/api/todos



