---
title: "Any program to watch current internet activity?"
date: 2009-01-25
forum: Networking &amp; Wireless
---

### Post by Roasted on 2009-01-25
Is there a program in Ubuntu to watch current internet activity on your LAN? Like can I see what web sites are being accessed? Tracking isn't really important here... I guess almost like wireshark, but... something visual... or something?? :KS

---

### Post by dmizer on 2009-01-26
I don't have anything which meets your needs exactly, but I saw this yesterday. Perhaps it is a piece of the puzzle? [http://ubuntuforums.org/showthread.php?t=550287](http://ubuntuforums.org/showthread.php?t=550287)

---

### Post by kevdog on 2009-01-26
dmizer

Good find on that escoteric piece of software!

---

### Post by |{urse on 2009-01-26
[http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-ubuntu-users.html](http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-ubuntu-users.html)

---

### Post by Roasted on 2009-01-26
Don't any of these tools show that 192.168.1.109 is currently visiting [www.google.com](www.google.com), or anything?

---

### Post by dmizer on 2009-01-26
> **Roasted said:**
> Don't any of these tools show that 192.168.1.109 is currently visiting [www.google.com](www.google.com), or anything?

You'll probably want a sophisticated gateway of some kind, like a dedicated linux gateway. I'm playing with [untangle](http://www.untangle.com/). You'll need either a dedicated computer or a virtual machine to run something like that though.

Unless your activity monitor is located at your gateway, you'll only be able to monitor traffic from your own machine.

---

