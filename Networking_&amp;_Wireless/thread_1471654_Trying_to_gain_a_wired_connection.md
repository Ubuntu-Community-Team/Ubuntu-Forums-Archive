---
title: "Trying to gain a wired connection"
date: 2010-05-03
forum: Networking &amp; Wireless
---

### Post by ShadowMosesGreen on 2010-05-03
I'm trying to gain access to a wired connection but I have no idea how on earth to do it.  I'm trying to get the connection so I can enable the broadcom wireless driver.  Can someone guide me through it, please?

I'm brand new to the whole Linux thing.  So don't just assume I know what things like the terminal are.  If you have a step and it involves going to something (ex: the terminal) please don't say "open the terminal," say "Go to system>applications>terminal" (or whatever the path is).  It would make things a lot clearer for me.

Thanks.

---

### Post by Iowan on 2010-05-04
I'm not sure how your thread managed to slip by a day without a reply, but...
To learn if your machine has an IP address, from a terminal (Applications>Accessories>Terminal), check:```
ifconfig -a
``` You can redirect the output to a file - which you can transfer to another (internet accessing) computer by:```
ifconfig -a > ifconfig.txt
``` Another version I recently learned about (also from terminal):```
ip address show
```
The next step depends on whether (or not) the machine has an IP address...

---

