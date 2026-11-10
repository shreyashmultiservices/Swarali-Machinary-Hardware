SWARALI MACHINERY – INDEPENDENT TEST APP

This is a separate copy of the working rental app design and features.
It has been rebranded as Swarali Machinery.

DATA PRIVACY / SEPARATION
- No Shreyash customer names, phone numbers, addresses, or business phone details are included.
- The browser storage keys are unique to this app (Swarali).
- Firebase settings are placeholders. The app is NOT connected to the Shreyash Firebase project.
- Before using online login / multi-device sync, create a NEW Firebase project for Swarali and add its own config below.
- Do not paste or reuse the Shreyash Firebase configuration.

GITHUB PAGES DEPLOYMENT
1. Create a NEW GitHub repository, for example: swarali-machinery-rental.
2. Upload index.html from this package to the root of that repository.
3. In GitHub: Settings > Pages > Deploy from a branch > main > /(root) > Save.
4. Wait for GitHub Pages to publish the site.

FIREBASE SETUP FOR SEPARATE ONLINE DATA
1. Sign in to Firebase Console and create a NEW project named Swarali Machinery (not the Shreyash project).
2. Add a Web App in the new project and copy its Firebase configuration.
3. In Authentication > Sign-in method, enable Email/Password.
4. In Firestore Database, create a database.
5. Open index.html and find: const firebaseConfig = { ... };
6. Replace every placeholder value with the values from the NEW Swarali Firebase Web App config:
   apiKey, authDomain, projectId, storageBucket, messagingSenderId, appId.
7. Save and upload the updated index.html to the NEW GitHub repository.
8. In Firebase Authentication, add a test user email and password for your friend.

IMPORTANT SECURITY NOTE
- Use a separate Firebase project so the friend's customer, rental, invoice, and payment records do not mix with Shreyash data.
- Do not share your Shreyash Firebase credentials or project.
- Configure Firestore security rules so only authenticated users can read/write. A basic starting rule is:

rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /{document=**} {
      allow read, write: if request.auth != null;
    }
  }
}

- For a real business deployment, use stricter per-user or role-based rules and test them before adding real customer information.

FIRST LOGIN / TEST
- Customer list starts EMPTY. No existing Shreyash contacts are copied.
- Add Swarali's own customers manually or use the Excel import option.
- Default sample machinery inventory is retained as editable sample items. Review/edit it for Swarali before testing.
- Use test data only until the new Firebase project and access rules are verified.

This package intentionally does not contain Firebase credentials for any project.
