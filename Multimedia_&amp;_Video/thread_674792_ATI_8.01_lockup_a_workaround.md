---
title: "ATI 8.01 lockup: a workaround"
date: 2008-01-22
forum: Multimedia &amp; Video
---

### Post by mikelito on 2008-01-22
Just wanted to share a workaround for the ATI 8.01 driver freeze-on-xstop problem, devised by some clever guys on phoronix
[http://www.phoronix.com/forums/showthread.php?t=7448&page=4](http://www.phoronix.com/forums/showthread.php?t=7448&page=4)

The trick is to kill atieventsd, which seems to be the culprit (or maybe just the one who makes the problem apparent). Obvioulsy this is going to affect the lifetime of laptop users on battery, but it seems to me a reasonable drawback, until a fixed version of the driver appears.

So, for a quick fix, 

$ sudo /etc/init.d/atieventsd stop

and to avoid the daemon to load on startup

$ sudo for a in /etc/rc*/S*atieventsd; do mv $a ${a%???atieventsd}s${a#*rc?.d/S}; done

a change which can be reverted by

$ sudo for a in /etc/rc*/s*atieventsd; do mv $a ${a%???atieventsd}S${a#*rc?.d/s}; done

hope this helps more to solve the problem

m

---

