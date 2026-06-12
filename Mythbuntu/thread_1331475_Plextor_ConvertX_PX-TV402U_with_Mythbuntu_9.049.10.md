---
title: "Plextor ConvertX PX-TV402U with Mythbuntu 9.04/9.10 wis-go7007-linux-0.9.8-4/5b"
date: 2009-11-19
forum: Mythbuntu
---

### Post by kjpires on 2009-11-19
I installed Mythbuntu 9.04 Jaunty Jackalope using mythbuntu-9.04-desktop-amd64.iso from the Torrent distribution.  Later I updated the go7007 driver using wis-go7007-linux-0.9.8-4 since wis-go7007-linux-0.9.8-5 had incompatible changes with my kernel (init_i2c_module has an extra argument in the new version).

gorecord (a go7007 driver-direct recording tool) seems to record just fine, but MythTV can not.

[time passes] I upgraded Mythbuntu 9.10 Karmic Koala hoping it might solve my problem...  This time I was able to used the newer wis-go7007-linux-098-5b.tgz (which matches the 2.6.31-14-generic kernel).  Again, gorecord works just fine, but again MythTV can not record.

Any ideas of what might need adjusting?

---

### Post by sf_basilix on 2009-11-21
I'd be happy to hear if you ever come across a solution for this.  The unfortunate news I have to bring is that I struggled with this for a long time but could not ever get Plextor's Convertx to work with mythbuntu.  I was, however, able to get it to work with mythdora and that is what I'm using today.  Sad, because I actually prefer the mythbuntu configuration menus better, but mythdora seems to be working at this point.

Good luck...

---

### Post by kjpires on 2009-11-24
Which version of MythDora are you using with the ConvertX?

---

