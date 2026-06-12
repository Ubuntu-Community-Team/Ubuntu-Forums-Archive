---
title: "SIOCSIFADDR: No such device"
date: 2005-03-22
forum: Networking &amp; Wireless
---

### Post by fjleal on 2005-03-22
Greetings!

I'm using a laptop to test Hoary. After today's upgrade, my PCMCIA ethernet card stopped working. When I do a "ifup eth0", I get:

```
sit0: unknown hardware address type 776
SIOCSIFADDR: No such device
eth0: No such device
...

```
Any ideas on how to solve it? Thanks.

---

### Post by alastair on 2005-03-22
Not sure. The "eth0" is not being created - so the driver is probably failing to load.

Best thing is - look in the logs and find any relevant (eth,pcmcia,hotplug) messages.

/var/log/syslog

Perhaps also worth booting without the card inserted, open a shell and type :

sudo tail -f /var/log/syslog

to see kernel messages as they happen. Then insert the card - what is printed?

---

### Post by fjleal on 2005-03-22
Thanks alastair for your answer! I don't exactly know how I did it, but after a reboot, removind and inserting the card, several "ifups" and a new reboot, it started working. Now it seems to be fine... ;)

---

