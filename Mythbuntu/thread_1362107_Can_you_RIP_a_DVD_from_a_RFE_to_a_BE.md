---
title: "Can you RIP a DVD from a RFE to a BE?"
date: 2009-12-22
forum: Mythbuntu
---

### Post by radnor on 2009-12-22
Hello all!

Can you do this?

On my BE in the /etc exports file I have this:
/var/lib/mythtv/videos * 192.168.0.102(rw) 
BE is: ... 100

On my RFE /etc/fstab I have:
192.168.0.100://var/lib/mythtv/videos	/var/lib/mythtv/videos	nfs	defaults	0	0

On my RFE I get this if I type mount:
192.168.0.100://var/lib/mythtv/videos on /var/lib/mythtv/videos type nfs (rw,addr=192.168.0.100)

From my RFE, I did nano /var/lib/mythtv/videos/test.txt
typed in a little text.  saved file.

Then SSH to BE.  Went to /var/lib/mythtv/videos and my test.txt file IS THERE.  So I can write to it from the RFE.

Tried to RIP a DVD and NO JOY.

Anyone know of a way I can do this??

TIA,

Radnor


It plays fine on the RFE, watching it now.


I did all of this above AND, on the BE chmod 777 /var/lib/mythtv/video

---

