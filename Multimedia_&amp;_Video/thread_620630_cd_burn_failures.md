---
title: "cd burn failures"
date: 2007-11-22
forum: Multimedia &amp; Video
---

### Post by Bunny Boy on 2007-11-22
Running ubuntu 6.06

I have one IDE CD-RW drive and one IDE DVD RW drive, both by LiteOn. They have both been intermittently failing to burn CDs when I use the nautilus cd burning ap. At first I had a 40% failure rate, but now it is essentially 100%.

Here are some things I don't understand:

Sometimes when I put a blank CDR in the drive, the icon appears on the desktop but then disappears a second later. 

My fstab file indicates that one of the drives has a mount point, but when I browse for it nothing is ever there. BTW, FWIW, fstab looks like this:

proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc1       none            swap    sw              0       0
/dev/hdd        /mnt/cdrom0   udf,iso9660 user,noauto     0       0

I'm not sure why the other drive, /dev/hdb is not in there. 

I tried using a command line utility called "burn" but it does not detect my blank disc. 

So:  is this just cheap Chinese hardware that needs to be replaced? OR is it an OS bug? Does anybody have a clue?

---

