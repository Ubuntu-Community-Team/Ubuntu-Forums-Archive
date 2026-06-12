---
title: "[SOLVED] Mythtvfrontend starting at startup how to disable ?"
date: 2008-08-22
forum: Mythbuntu
---

### Post by Eldis on 2008-08-22
I have 2 users on my mythtvbackend server one of them is logged in automatically and opens mythtvfrontend automatically which is fine. But at some point I messed things up on my frontend default user and switched from mythbuntu control center so that my other user is logged in automatically and it added something somewhere so that mythfrontend is starting up automatically on that user aswell. Now that I fixed whatever I messed up with my original user and mythbuntu logs in at startup with that I wouldn't want my remote management users sessions starting up with the frontnend.

Where can I remove mythtvfrontend from starting up on a specific user?

---

### Post by DemonBob on 2008-08-22
login as the user with the problem, open the terminal. 

cd .config/autostart
rm mythtv.desktop

---

### Post by Eldis on 2008-08-22
> **DemonBob said:**
> login as the user with the problem, open the terminal. 

cd .config/autostart
rm mythtv.desktop

Thanks that did it, learning something new everyday :)

---

