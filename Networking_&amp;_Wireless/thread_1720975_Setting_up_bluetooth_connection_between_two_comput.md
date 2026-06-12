---
title: "Setting up bluetooth connection between two computers throws Connection Refused (111)"
date: 2011-04-03
forum: Networking &amp; Wireless
---

### Post by DARKGuy on 2011-04-03
Hey!!

I'm trying to create a PAN (Personal Area Network) using a laptop (Siragon ML-1040) and my desktop computer, but I get the Connection Refused (111) error.

Blueman doesn't detect any network service between the two computers unless I start PAND on one of them and then it detects the NAP service. That, only after I enable the NAP/Workgroup services on the Services submenu in Blueman. However, it doesn't work neither with the NM plugins or without them (dhclient and that other one I can't remember the name of).

Any clues over here? I'm using pand 4.91 and blueman.

Any help is greatly appreciated!

- DARKGuy

---

### Post by rblomqui on 2011-08-17
DARKGuy, did you ever get this working?  I'm having the same problem (same configuration), and have tried multiple USB-Bluetooth dongles.

---

### Post by DARKGuy on 2011-08-17
Nope, I haven't as of today. Sucks huh, when nobody wants to help :/

---

### Post by rblomqui on 2011-08-17
I just got it working (since my first post)!  See thread  [http://ubuntuforums.org/showthread.php?t=1433981](http://ubuntuforums.org/showthread.php?t=1433981).  The key was to disable the network plugin in the main.conf file.  After doing this, I can setup my IP address and ping between the 2 devices.  Still need to do the routing, etc.

---

