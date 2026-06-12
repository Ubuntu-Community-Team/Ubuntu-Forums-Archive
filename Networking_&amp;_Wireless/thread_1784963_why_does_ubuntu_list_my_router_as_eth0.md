---
title: "why does ubuntu list my router as eth0?"
date: 2011-06-17
forum: Networking &amp; Wireless
---

### Post by sect0ss on 2011-06-17
i recently switched over from windows xp and instead of listing my 2wire router it just says eth0 now

---

### Post by DirtyPC on 2011-06-17
That's just the default name. You can rename it if you so wish.

---

### Post by nzjethro on 2011-06-17
> **sect0ss said:**
> i recently switched over from windows xp and instead of listing my 2wire router it just says eth0 now

Hi there, mine does the same. Linux names your ethernet cards as ethX, where X is a number starting from 0. Thus, your first ethernet card is eth0, your next (if you have one) would be eth1, etc.

[http://www.linuxquestions.org/questions/linux-wireless-networking-41/what-is-eth0-472344/](http://www.linuxquestions.org/questions/linux-wireless-networking-41/what-is-eth0-472344/)

---

### Post by DirtyPC on 2011-06-17
Network connections> right click> Edit connections> eth0>edit> change name

---

### Post by sect0ss on 2011-06-17
so its still my router its just renamed to eth0?

---

### Post by DirtyPC on 2011-06-17
yes of course, just rename it as above if it confuses you.

---

### Post by Iowan on 2011-06-17
Another opportunity to advertise my ignorance...
Is the 2wire a card that plugs into the computer - or do you connect to it via an ethernet card?

For what it's worth - my laptop has an ethernet connection and a wireless card. Ubuntu (9.04) labels the wireless card as eth1 rather than wan0 - but it works - so I've left it alone...

---

### Post by sect0ss on 2011-06-17
k thanks

---

### Post by redmk2 on 2011-06-17
> **sect0ss said:**
> i recently switched over from windows xp and instead of listing my 2wire router it just says eth0 now

Where does it say that?  

The term eth0 or eth1 is meant to describe the NIC (interface) in any computer using a Unix/Linux type OS.  It is mapped to a IP address in the LAN.  The 2wire router has 2 interfaces (LAN side and WAN side).  Your computer should have 1 interface.

Once again: where are you seeing this listing of *eth0 instead of 2wire*?

---

### Post by gordintoronto on 2011-06-17
eth0 is your Ethernet adapter, not your router. 2wire is a brand, like Toyota. What model of router do you have?

---

