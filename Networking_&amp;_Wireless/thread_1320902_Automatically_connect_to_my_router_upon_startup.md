---
title: "Automatically connect to my router upon startup?"
date: 2009-11-09
forum: Networking &amp; Wireless
---

### Post by kerbitroy on 2009-11-09
I am running Ubuntu 9.04 on my laptop with Windows 7 (I "dual booted" using WIMP to try out Ubuntu). I can connect to my router fine, but I have to do so manually everytime I boot to Ubuntu. Is there any way of getting this to happen automatically? Thanks in advance, Kerbitroy.

---

### Post by t0mppa on 2009-11-09
Sure there is, but first you need to tell a bit more information about how you're connecting to your router. Is your connection wired or wireless? What are you using to configure your connection (Network Manager, WICD, Wifi Radar, /etc/network/interfaces, CLI or perhaps something else)?

---

### Post by kerbitroy on 2009-11-10
It is a wireless router, I connect via the network connection symbol at the top right corner (no idea if this has a name). All I had to do to connect the first time was search for a network, put in my password for the router and it connected fine. Although upon startup I have to click this same icon and click on the network to connect.

---

### Post by mr_steve on 2009-11-10
> **kerbitroy said:**
> It is a wireless router, I connect via the network connection symbol at the top right corner (no idea if this has a name). All I had to do to connect the first time was search for a network, put in my password for the router and it connected fine. Although upon startup I have to click this same icon and click on the network to connect.

Sure, right click on that icon, click edit connections. Find your wireless connection and click edit. There'll be a box that says "Connect automatically" or something along those lines.

---

### Post by t0mppa on 2009-11-10
That icon would be for Network Manager and like mr_steve already said, you just need to edit the connection details to make it happen.

---

### Post by kerbitroy on 2009-11-11
> **mr_steve said:**
> Sure, right click on that icon, click edit connections. Find your wireless connection and click edit. There'll be a box that says "Connect automatically" or something along those lines.

> **t0mppa said:**
> That icon would be for Network Manager and like mr_steve already said, you just need to edit the connection details to make it happen.
Cheers guys, I feel silly now :D

---

### Post by Iowan on 2009-11-11
Connect at startup or login? There's a subtle difference - or used to be (Jaunty).

---

### Post by kerbitroy on 2009-11-20
> **Iowan said:**
> Connect at startup or login? There's a subtle difference - or used to be (Jaunty).
Login

---

### Post by Iowan on 2009-11-20
**mr_steve** and **t0mppa** help you get it solved - or is it still a problem?

---

