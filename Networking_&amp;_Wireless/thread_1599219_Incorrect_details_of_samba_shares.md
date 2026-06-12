---
title: "Incorrect details of samba shares"
date: 2010-10-17
forum: Networking &amp; Wireless
---

### Post by officerdibble on 2010-10-17
**Spent two days now trying for a solution - head hurts - solution required.**

Just set up Ubuntu 10.4 AMD64 on an old machine. We have an existing Ubuntu machine acting as a SAMBA file sharer. The other machines, windows and ubuntu have no problem in accessing files on the server. This machine reports that it can see the server on the network but instead of the expected data we see what is on the local machine. I admit I am out of my depth with SAMBA, someone put me out of my misery please.:confused:

---

### Post by macem29 on 2010-10-17
samba will display the folders/files on all the workgroup machines, including the client you
are looking at, if all you see is the client files you are probably not connected to the server

---

