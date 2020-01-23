# Security rules example for Firestore

See firestore.rules also.

<hr>

The following rules will provide a great starting point for Firebase apps centered around the addition of new data.

These rules will only allow the creation of new data.

service cloud.firestore {
  match /databases/{database}/documents {
    match /{document=**} {
      allow read: if request.auth != null;
      allow create: if request.auth != null;
      allow update: if request.auth != null && !resource.data.exists();
    }
  }
}

These rules will prevent deletion or updating of data. Of course, this isn't suitable for all apps.

But if you're just exploring new concepts, this is a great way to ensure data isn't tampered with among users.
