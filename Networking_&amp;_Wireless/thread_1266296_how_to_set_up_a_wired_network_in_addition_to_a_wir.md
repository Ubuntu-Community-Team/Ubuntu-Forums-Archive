---
title: "how to set up a wired network in addition to a wired network"
date: 2009-09-14
forum: Networking &amp; Wireless
---

### Post by DrScum on 2009-09-14
I have a home network based on wireless adapters controlled by a WLAN router. This network has Windows and Linux machines and works fine.

Now I want to create a wired network including a station that has a WLAN card and an ETHERNET card as well and a three Linux machines having only ethernet cards. There is no need for the wired network seeing the WLAN network. Just the one station has to see them both.

How can I do this?

I had it set up this way when my Laptop, which is the station having WLAN and Ethernet was running XP but so far I couldn't get it to work with the Laptop running Ubuntu 9.04. The other Linux stations are on Ubuntu 8.04 by the way.

So far I tried to use Samba and the Network manager. I am familiar with creating samba shares and I did all that.

The following attempts didn't work:
-configure the ethernet card via static ip to be part of the WLAN network -configure the ethernet card via static ip NOT to be part of the WLAN network

Help is appreciated, thanks

---

### Post by Iowan on 2009-09-14
Do the other wired machines see each other?

---

### Post by DrScum on 2009-09-15
they can ping each other but they don't appear on places > network

---

