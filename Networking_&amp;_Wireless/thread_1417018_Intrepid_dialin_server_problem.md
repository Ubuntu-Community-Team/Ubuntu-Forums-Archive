---
title: "Intrepid dialin server problem"
date: 2010-02-26
forum: Networking &amp; Wireless
---

### Post by einstein on 2010-02-26
This will seem a little archaic but ... I have an Intrepid server set up that I need to be able to dial in to.  I have an AOpen FM56EXV modem that, using minicom, will dial out and will answer an incoming call IF I first set ATS0=1 using minicom.
My current problem is that I have to re-issue ATSO=1 manually after each dialin.  This, of course, needs to be automated but I cannot figure out how to do it.  A lot of Googling has not returned anything useful.  Could someone point me to a howto or otherwise offer some guidance? ppp stuff just isn't my forte.

Thanks in advance,
       Dennis

---

### Post by einstein on 2010-02-26
Try this .... add a file, for example, ttyS0 to /etc/event.d.  In that file put:
```
start on runlevel 2
# ttyS0 - mgetty
#
# This service maintains a mgetty on ttyS0 from the point the system is
# started until it is shut down again.

start on stopped rc2
start on stopped rc3
start on stopped rc4
start on stopped rc5

stop on runlevel 0
stop on runlevel 1
stop on runlevel 6

respawn
exec /sbin/mgetty -n 3 ttyS0



```
Now mgetty is restarted upon termination of a dialin sessions and is ready to receive the next.  And, yes, I answered my own question. Again.

HTH
 -Dennis

---

