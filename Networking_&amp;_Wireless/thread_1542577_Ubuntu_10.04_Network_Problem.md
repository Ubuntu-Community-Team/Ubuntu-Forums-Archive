---
title: "Ubuntu 10.04 Network Problem"
date: 2010-07-30
forum: Networking &amp; Wireless
---

### Post by R[wc]BADFISH on 2010-07-30
I'm setting up a server box but i'm having some issues, please help!

First, I started with a clean Ubuntu 10.04 desktop Install. I then installed OpenSSH & Lamp. I went with the desktop version because I couldn't configure a working wireless network in the terminal... yeah I know I'm a rookie! Anyway, I plan on putting the box in a closet and accessing it with openssh. However, I can't access the server through openssh or my network without logging into the system. How can I fix this?

---

### Post by Iowan on 2010-07-30
Have you set up the connection to be "Available to all users"? Other threads suggest that this makes Network Manager configure interfaces at startup - rather than waiting for login. (I presume it's also set to "Connect automatically").

---

