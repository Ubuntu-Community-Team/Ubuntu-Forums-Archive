---
title: "GPRSEC : port problem"
date: 2009-03-30
forum: Networking &amp; Wireless
---

### Post by bigbamboo on 2009-03-30
Hi,
i'm trying to configure gprsec in order to use it with an Aircard 850 (sierra) on an HP TC1100 tablet laptop.

When I have to set the port, I can't find the one I'm using : **tyyS2**(as shown in "dmesg | tty" and "var/log/messages")

gprsec only allow mw to set ttyS0, ttyS1 and ttyS3
moreover, if i browse the filesystem to select another port, I can't find any ttyS2 entry in /dev/ folder, but just ttys2 (lowercase).

If I select ttys2 port (I can fin it in /dev/ folder) the connection ends up in a "turn on the phone" message.

any advice?

many thanks

E.

---

### Post by bigbamboo on 2009-03-31
bump!

---

