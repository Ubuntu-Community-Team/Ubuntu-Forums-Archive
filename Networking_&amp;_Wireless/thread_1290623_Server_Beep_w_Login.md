---
title: "Server Beep /w Login"
date: 2009-10-13
forum: Networking &amp; Wireless
---

### Post by Ransack on 2009-10-13
Hi, I am new to posting on the forums, I have been running a Ubuntu 8.10 intrepid box downstairs, and was wondering if I could somehow make the box beep when ever someone logs into the system through SHH, so I could login and write them when they are on.

The box is connected through ethernet cable (So not wireless)
This is mostly for convenience, I understand that there are commands like "who" and "w" or "list" to see who is online, but this is hit and miss. If you need more info please let me know. or maybe some other ideas or options for login alerts?

---

### Post by skillllllz on 2009-10-13
```
sudo apt-get install beep
```then edit the user's .bashrc file and add
 ```
beep
```at the bottom, after every thing else.

---

### Post by Ransack on 2009-10-14
ty very much, this actually adds a bit of a security feature in my mind.
You can have it beep every time a command is entered :P

---

