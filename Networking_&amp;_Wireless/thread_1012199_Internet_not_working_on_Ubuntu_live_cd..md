---
title: "Internet not working on Ubuntu live cd."
date: 2008-12-15
forum: Networking &amp; Wireless
---

### Post by MikkyW on 2008-12-15
Just recently my computer running vista got a virus, so I decided, since I couldn't boot my os or system restore, that I was gonna get my files out of there, and convert to linux, specifically ubuntu. Unfortunately, when I loaded my ubuntu live cd, it doesn't allow me to access the internet. Does any body have any clue why it might not allow me to do this. I have an ethernet cable internet connection. If you need any other info, or if you need me to do something before you can help me, just tell me, I'll respond ASAP. Thanks.

---

### Post by spy_1134 on 2008-12-15
Click the network manager in the system tray.

It will bring up your connection settings so you can edit them to your liking

---

### Post by MikkyW on 2008-12-15
Well, yeah, it says Auto eth0, and it's set up as well as I would know how to set it up. If my understanding is correct, ubuntu is designed to automatically be able to work with ethernet connections without having to configure anything, yet this isn't working. Does anybody know why this would be happening? When I type ifconfig in terminal, I get eth0, and lo, which is a local loopback connection. I don't know if that is helpful, but I'm running out of straws. Any help would be hugely appreciated.

---

### Post by rajenpn on 2008-12-17
How to access internet (by connecting GPRS Mobile) on Ubuntu **Live CD**?
wvdialconf is not able to write configuration items, obviously it is running from CD. But, is there any way to get around this problem?

---

### Post by rajenpn on 2008-12-19
I got it resolved by myself :p

I saved the configuration file - wvdial.conf - in one of the windows drives and used the -C (capital letter) option of wvdial to connect to the internet. And it worked!
[FONT="Courier New"]
wvdial -C /media/drivename/wvdial.conf[/FONT]

---

