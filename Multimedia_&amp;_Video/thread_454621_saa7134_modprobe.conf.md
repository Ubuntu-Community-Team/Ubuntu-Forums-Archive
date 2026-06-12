---
title: "saa7134: modprobe.conf?"
date: 2007-05-25
forum: Multimedia &amp; Video
---

### Post by Zalbor on 2007-05-25
I have a video capture card (not tv) which might have the saa7134 chip, I don't know for sure (EZmaker PCI deluxe, in case someone else knows).
I'm trying to follow the instructions [here](http://linuxtv.org/v4lwiki/index.php/Generic_SAA7134_Card_Installation) to get the driver to work, but it mentions inserting some lines into modprobe.conf.
The problem is that I can't find this file at all in ubuntu. What should I do?

---

### Post by steefjeqv on 2007-05-26
Hi,

Have you tried :

sudo modprobe saa7134

Greetings,
Steven

---

### Post by Zalbor on 2007-05-26
I have, I actually tried "sudo modprobe saa7134 i2c_scan=1" like that page says. But I get the impression that I'd need these lines there too. Or has the "modprobe.conf" file been dropped in recent kernel versions?

---

