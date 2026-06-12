---
title: "Has ANYONE gotten the GP-IR02BK Blaster to work?"
date: 2010-09-11
forum: Mythbuntu
---

### Post by eljeffe on 2010-09-11
Mediagate ir02bk remote and blaster.

The remote worked immediately with a new mythubu install. As far as the transmitting ....

I've been trying for a couple of weeks now. I've yet to see anything succeed for me; nor for anyone else.

I'm done trying unless someone has had some success with this.

I see lots of questions. Would be nice to have an answer as to whether this is possible, or not. 

Maybe we can save others the pain of trying this.

---

### Post by mulad on 2010-11-09
I did have it working under Ubuntu 9.10 Karmic, but I have been unable to get it going under 10.04 Lucid.  The lirc driver and utilities that came in 9.10 were too old to work, so I had to download the lirc source from CVS, compile new kernel modules, the daemon, and utilities, remove the existing lirc_dev and lirc_mceusb/lirc_mceusb2 modules, insert the replacement modules, and replace the daemon and utilities with my own compiled versions, and restart lircd.

Doing the same thing with 10.10, I've been unable to get it working.

---

