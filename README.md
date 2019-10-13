# Admin
Set up firebase:

- Create a project at the [Firebase console].
- Get your account credentials from the Firebase console at project settings>service accounts, where you can click on generate new private key and download the credentials as a json file. It will contain keys such as project_id, client_email and client id. Now copy them into your project in the credentials/server.js file.
- Get your authentication credentials from the Firebase console under project settings>general>your apps Add a new web app if you don't already have one. Under Firebase SDK snippet choose Config to get the configuration as JSON. It will include keys like apiKey, authDomain and databaseUrl and it goes into your project in credentials/client.js.
- Back at the Firebase web console, go to Authentication>Sign-in method and enable Google.
- Create a database in the "Database" tab and select Firestore. Then go to "rules" and set up your write, read rules to this:

// Allow read/write access on all documents to any user signed in to the application
> 
service cloud.firestore {
  match /databases/{database}/documents {
    match /{document=**} {
      allow read, write: if request.auth.uid != null;
    }
  }
}

Install it and run:
npm install
npm run dev
# or
yarn
yarn dev
