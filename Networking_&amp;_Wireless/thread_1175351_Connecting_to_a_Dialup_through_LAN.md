---
title: "Connecting to a Dialup through LAN"
date: 2009-06-01
forum: Networking &amp; Wireless
---

### Post by Smartflight on 2009-06-01
Yesterday, the USB ports of my laptop (Ubuntu) stopped working.

Now, the PC (Windows XP) is connected to the internet using wireless dial up. But as my USB ports are damaged, I can't connect to the net.

LAN is working between the two, but the dial up that is shared in XP doesn't work in Ubuntu.

What to do ??

---

### Post by ptsubin on 2009-06-01
Set a static IP address for the linux system and then configure lan to use the windows system as gateway and DNS, by setting up the addresses manually.

---

### Post by Smartflight on 2009-06-01
I figured out what was wrong. The PC was using a strong firewall, I disabled it and bingo !

It's up and working now..!! :D

---

### Post by charkoal on 2009-07-29
> Set a static IP address for the linux system and then configure lan to use the windows system as gateway and DNS, by setting up the addresses manually. 

How do I do that please?

---

### Post by superprash2003 on 2009-07-29
here's a guide on setting up static ip [http://www.prash-babu.com/2009/01/how-to-setup-static-ip-in-ubuntu.html](http://www.prash-babu.com/2009/01/how-to-setup-static-ip-in-ubuntu.html)

---

