---
title: "remote destop"
date: 2009-04-30
forum: Networking &amp; Wireless
---

### Post by greynand on 2009-04-30
how to connect remote destop from work to home

---

### Post by RedSingularity on 2009-05-03
With 2 ubuntu PC's?

---

### Post by mattgyver83 on 2009-05-08
You'll have to do a little footwork on these topics but;

Install x11vnc, and tightvncserver

Make sure your setting up static IP addresses for the computers you want to connect to
Setup port forwarding on your router to point to the specific IP addresses

Use Remote Desktop viewier to connect to IPaddress:Port

Use internal while within network
Use external IP while outside of network.

---

