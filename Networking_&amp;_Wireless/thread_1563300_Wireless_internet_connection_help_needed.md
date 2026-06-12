---
title: "Wireless internet connection help needed"
date: 2010-08-28
forum: Networking &amp; Wireless
---

### Post by linuxdude7 on 2010-08-28
Okay, At this moment I've got my Linux system Ubuntu 10.04 64-bit using my macbook's shared wireless connection via ethernet cable to gain access to the internet. I'm having a problem connecting to my wireless N router, with my RaLink Wireless N PCI card. The thing is it sees the network, it won't connect, my router is a Netgear DGN1000 Router/Modem. My Router is setup by WPA & WPA 2 Personal password. Why won't it connect? It keeps saying Disconnected from Wireless.

Anyone have any ideas?

---

### Post by linuxdude7 on 2010-08-29
Anyone?

---

### Post by sKuarecircle on 2010-08-29
I have the same problem...

---

### Post by linuxdude7 on 2010-08-30
Somebody has to know why this is happening.

---

### Post by linuxdude7 on 2010-08-30
Okay I made a mistake on what wireless card I have it's a Rosewill RNX-N300 802.11N 2.0, 1T2R PCI Adapter. The drivers are ralink

---

### Post by dtoronto on 2010-08-30
you may have to install the windows drivers using ndiswrapper.  It's a piece of software that will allow you to run windows based drivers on your PC when the open source drivers are non-existent or not working correctly.

---

### Post by JBAlaska on 2010-08-30
Ubuntu has native support for most ralink chipsets, but your install may need to use a different driver.

Open a terminal and do:
```
sudo gedit /etc/modprobe.d/blacklist.conf
```

And add this to the list:
```
blacklist rt2800usb
blacklist rt2870sta
```

Restart Ubuntu and your wireless should work.

---

### Post by barrieluv on 2010-11-06
I've had issues with not being able to connect to my Netgear DGN1000 Modem/Router, too.  I can see the network but not connect.
The only answer for me so far is to go into the Wireless Settings in the router and create a Wireless Access List, allowing only my machine to connect.  I don't know why this works, but it does.

---

