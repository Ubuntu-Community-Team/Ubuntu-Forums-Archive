---
title: "sufficient WiFi signal, low bandwidth"
date: 2011-11-23
forum: Networking &amp; Wireless
---

### Post by groundnut on 2011-11-23
Since today I have a new wireless router at a different location farther away from the computer.
Though the strength of the WiFi signal is sufficient according to the network icon at the upper left corner, the bandwidth is very low. So I cannot play videos without a lot of buffering.

What could be the problem?

---

### Post by sky5564 on 2011-11-23
Find out what driver your wireless card is using.

Open a terminal and type "sudo lspci -vv" find the part that says "network controller" its usually at the bottom of the list.

post what driver it says is in use.

Some times open source drivers just suck, You might have to find the windows driver for your sepecific card and install it with ndiswrapper.

Its somewhat complicated if you have never done it before but there are people on here that can help with that.

---

### Post by groundnut on 2011-11-24
I found the problem.

The WiFi USB stick was plugged in at the back of the desktop computer.
Now I placed an USB cable in between. 
I moved the USB stick one meter.

This was enough for a perfect reception.

---

