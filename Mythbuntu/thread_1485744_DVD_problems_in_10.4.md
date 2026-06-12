---
title: "DVD problems in 10.4"
date: 2010-05-17
forum: Mythbuntu
---

### Post by Billsputters on 2010-05-17
I am having real problems with trying to play a DVD within MytvTv

As soon as I insert a disc, the whole Frontend exits back to the desktop and the Frontend will not run again until the disc is ejected.

I have the device set up as /dev/sr0, have enabled the Medibuntu option and I have even disabled the 'watch for media' option in the DVD player setup.

Totally stumped here. Anyone any ideas?

---

### Post by mathog on 2010-05-17
> **Billsputters said:**
> 
As soon as I insert a disc, the whole Frontend exits back to the desktop and the Frontend will not run again until the disc is ejected.

Check the /var/log/mythtv log files and see what the error was.

Is this all disks?  I spent the weekend trying to get "Leatherheads" to play (apparently heavily copy protected, lots of intentionally bad sectors) without success.  It wouldn't even play with VLC using dvdnav, which was surprising since I thought that was supposed to emulate a regular DVD player, and only open the blocks in the order the media said to - which should avoid touching any of the toxic sectors.  Bringing this up because depending on how your machine is configured a disk like this could be leading the player to keep trying to read the media, only stopping when you remove it.

---

### Post by pauna on 2010-05-17
I had the same problem. It turned out to be a bug in MythTV 0.23 and it has now been corrected in auto-builds.

[http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds)

---

### Post by Billsputters on 2010-05-17
Ok. I enabled the audo-builds. But it says I'm up to date!

Maybe it'll change overnight.

BTW, the DVD in question plays fine on the desktop and a mighty fine movie 'Heat' is too.

---

### Post by Billsputters on 2010-05-18
Got an update this morning.

Solved the problem. Many thanks

---

