---
title: "Can't stop integrated wireless from connecting"
date: 2009-10-28
forum: Networking &amp; Wireless
---

### Post by jimbob on 2009-10-28
Most people use this category when their wireless doesn't work but I have the opposite problem.  I am trying to test out a wireless dongle but my integrated wireless keeps jumping in and taking over the connection.  I have tried ifdown wlan0, iwconfig wlan0 txpower off, deleting the AP entry in Network Manager and it still finds it again.  
  The dongle connects fine as wlan1 and starts up but suddenly drops and the Network Manager announces "connection established" again but it is back to wlan0.
  There must be a file somewhere storing the information for the integrated device but I haven't found it yet.

---

### Post by Iowan on 2009-10-28
Kinda crude - but might work...
Try defining wlan0 in */etc/network/interfaces*. Define it as "manual" (as opposed to dhcp or static) and do not use the "auto wlan0" line.

Seems like there is a more elegant way...

---

### Post by jimbob on 2009-10-29
Hey thanks.  That worked.  I changed network/interfaces to look like

manual wlan0
iface wlan0 inet static

Rebooted and it ignored wlan0 and wlan1 saw my AP and several of the stronger neighbors also which it couldn't find before.

---

### Post by Iowan on 2009-10-29
I seem to remember a similar thread (to which I offered similar advice), but someone else had a more elegant solution.  If I happen across it, I'll try to pass it along - glad you have a workable solution, anyway.

---

