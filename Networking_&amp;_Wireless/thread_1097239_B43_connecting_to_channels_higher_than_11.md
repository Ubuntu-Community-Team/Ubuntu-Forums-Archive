---
title: "B43 connecting to channels higher than 11"
date: 2009-03-15
forum: Networking &amp; Wireless
---

### Post by kane77 on 2009-03-15
Hi, is it possible to connect to channels greater than 11 using b43 driver? I don't think anygthing has changed and wifi does not work.. it is able to see the AP with kismet on channel 12, but the networkmanager applet neither iwlist show no AP :( is there any trick to that?

---

### Post by kevdog on 2009-03-15
1-11 is probably locked by your firmware.  I do know of a way however to unlock channels 12 and 13, have it would require recompiling the mac layer and actually requires the jaunty kernel version or higher.  I'm looking for the source right now but I can't remember seem to find the instructions.  I do know that you need a more recent kernel version than hardy or intrepid however.

---

### Post by kane77 on 2009-03-16
> **kevdog said:**
> 1-11 is probably locked by your firmware.  I do know of a way however to unlock channels 12 and 13, have it would require recompiling the mac layer and actually requires the jaunty kernel version or higher.  I'm looking for the source right now but I can't remember seem to find the instructions.  I do know that you need a more recent kernel version than hardy or intrepid however.
thank you, I will be probably installing jaunty sometime soon as I usually install any new version on my laptop first.. :D

---

### Post by kane77 on 2009-03-16
I just upgraded to Jaunty and it went well. wifi now works on channel 12.. :D

---

### Post by trevornetley on 2009-03-17
I think you just inadvertently solved my problem too. It would be good if this info was on linuxwireless and linuxfans - I've been using channel 12 with bcm43xx driver for several years and it never even ocurred to me that b43 wouldn't have it built in.

---

