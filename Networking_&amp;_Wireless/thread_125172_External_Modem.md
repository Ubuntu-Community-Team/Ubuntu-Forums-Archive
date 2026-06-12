---
title: "External Modem"
date: 2006-02-03
forum: Networking &amp; Wireless
---

### Post by simonkitch on 2006-02-03
Hi

I'm using an external modem conected through the serial port on my PC.
I have configured the device through the Gnome Administration Network Poperties dialog and its working fine. Problem is it dials up when the system starts! I have know way of knowing wether its conected or disconected from the desktop. Is there a way I can take better control of this device? Or just set a idle time out limit etc. I'm a bit conserned about my phone bill here :-k 

AMD k7400 Breezy 5.10

Simon

---

### Post by Mustard on 2006-02-03
I had a similar problem when I set up the modem using the Administration Network dialog to connect.  I had more success by disabling that setup and using this HOW TO from the wiki to set up my modem.

[https://wiki.ubuntu.com/DialupModemHowto](https://wiki.ubuntu.com/DialupModemHowto)

The parts most relevant to you would be towards the end of the guide, and it even mentions the problem you are having.  I set up my modem using the pppconfig command in terminal and initially used the pon and poff commands to connect and disconnect.  Having gained a connection though, I found the gnome-ppp application to be the best way to connect.  Anyway, read over the wiki guide and I'm sure you will find what works best for you. :)

---

