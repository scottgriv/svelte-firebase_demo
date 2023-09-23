<script>
import { collection, addDoc } from 'firebase/firestore';
import { db } from "./firebase.js";

let messageId = 1;  // Initialize with 1 or any starting value
let message = "Test Message!";  // Default value

function addData() {
  const firebaseDemoCollection = collection(db, "firebase_demo"); // Change to your collection name
  addDoc(firebaseDemoCollection, { // Change to your document structure
    messageId: messageId,
    message: message
  })
  .then((docRef) => {
    console.log("Document written with ID:", docRef.id);
  })
  .catch((error) => {
    console.error("Error adding document:", error);
  });
}

</script>

<div>
    <input type="number" bind:value={messageId} placeholder="Enter message ID" />
    <input type="text" bind:value={message} placeholder="Enter message" />
    <button on:click={addData}>Add Data</button>    
</div>
