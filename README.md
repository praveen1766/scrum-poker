# Scrum Poker - Real-time Story Pointing

A simple, clean, and real-time web application for agile teams to conduct scrum poker (or planning poker) sessions for story point estimation. Built with plain HTML, Tailwind CSS, and Firebase, this tool is designed to be fast, easy to use, and requires no user sign-up.

**Live Demo:** [https://praveen1766.github.io/scrum-poker/](https://praveen1766.github.io/scrum-poker/)
---

## Features

-   **Real-time Interaction:** See participants join and vote in real-time.
-   **No Sign-up Required:** Uses anonymous authentication for temporary sessions.
-   **Shareable Rooms:** Create a room and share the URL with your team to have them join instantly.
-   **Host Controls:** The room creator (host) has special privileges to control the session.
    -   Reveal or hide votes for all participants.
    -   Clear all estimates to start a new round.
    -   Remove all participants from the room.
    -   Close the room, deleting all its data permanently.
-   **Session Persistence:** Reloading the page will automatically rejoin you to the same room.
-   **Clean & Simple UI:** A professional and intuitive interface that works great on desktop and mobile.

## How to Use

1.  **Create a Room:** Go to the website and click "Create New Room".
2.  **Share the URL:** Copy the URL from your browser's address bar (it will include your unique Room ID) and share it with your team.
3.  **Join a Room:** Team members can either click the shared link or enter the Room ID on the main page to join.
4.  **Vote:** Each participant selects a card to provide their estimate.
5.  **Reveal & Discuss:** The host can click "Show" to reveal all votes for discussion. Clicking "Hide" will flip the cards back over.
6.  **Next Round:** The host can click "Delete Estimates" to clear the board for the next story.

## Technology Stack

-   **Frontend:** HTML5, Tailwind CSS
-   **Backend & Real-time Database:** Google Firebase (Firestore)
-   **Authentication:** Firebase Anonymous Authentication
-   **Icons:** Font Awesome

## Setup for Local Development

To run this project locally or to fork it for your own use, you will need to set up your own free Firebase project.

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/praveen1766/scrum-poker.git](https://github.com/praveen1766/scrum-poker.git)
    cd scrum-poker
    ```

2.  **Create a Firebase Project:**
    -   Go to the [Firebase Console](https://firebase.google.com/) and create a new project.
    -   Add a **Web App** to your project.
    -   Copy the `firebaseConfig` object that Firebase provides you.

3.  **Update Configuration:**
    -   Open the `index.html` file.
    -   Find the `firebaseConfig` object inside the `<script>` tag.
    -   Replace the existing placeholder keys with the keys from your own Firebase project.

4.  **Enable Firebase Services:**
    -   In the Firebase Console, go to **Build > Authentication > Sign-in method** and enable the **Anonymous** provider.
    -   Go to **Build > Firestore Database** and click "Create database". Start it in **Production mode** and choose your server location.

5.  **Set Security Rules:**
    -   In the Firestore section, go to the **Rules** tab.
    -   Replace the existing rules with the following to allow your app to function:
        ```javascript
        rules_version = '2';
        service cloud.firestore {
          match /databases/{database}/documents {
            match /scrum-poker-rooms/{roomId}/{documents=**} {
              allow read, write: if true;
            }
          }
        }
        ```
    -   Click **Publish**.

6.  **Run Locally:**
    -   Simply open the `index.html` file in your browser.

## Contributing

Contributions, issues, and feature requests are welcome! Feel free to check the [issues page](https://github.com/praveen1766/scrum-poker/issues).

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details.
