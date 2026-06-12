---
title: "Upgrading: Copy Working Install Image to new Partition?"
date: 2009-05-13
forum: Mythbuntu
---

### Post by SeanOB on 2009-05-13
Hello Mythbuntites!

This is ultimately not a mythbuntu question - but it applies for those of us who use ubuntu as a media center and care about the WAF.

So I just brought up a frontend 9.04 with mythbuntu.
And I was pretty pleased with my idea to install it to a new partition -- so that the working 8.10 install wasn't affected.  This was great - 'cause it allowed me to not break 'the tv' while allowing a leisurely bringup of 9.04.
[http://ubuntuforums.org/showthread.php?t=1148696](http://ubuntuforums.org/showthread.php?t=1148696)
And 9.04 is now my default boot partition and its working great.

So - now I want to try to move to the VDPAU enabled mythtv.  But I don't want to break my existing setup while I try to get this running.

Is there an (easy) way to copy this working 9.04 to a new partition?
I'd like to use grub to default boot to this working one - while I attempt to upgrade the copy with the VDPAU enabled packages.

I could do yet another fresh install of 09.04 -- but I'd rather take this working setup and build from here.

Any ideas?  Pointers?

Ultimately I'd like to have 2 boot options:
- stable working
- hobby / testing / tinkering
This will minimize the chances of me breaking something while I'm tinkering with new features.  And will greatly improve the WAF!


-Sean

---

### Post by logos34 on 2009-05-13
you can use either Partimage or Clonezilla live cd ('[[disk-to-disk' clone]("http://clonezilla.org/clonezilla-live/doc/")).  Then reinstall grub, so it points to 9.04 at the new location, or 8.10.

---

### Post by ian dobson on 2009-05-13
Hi,

Maybe you could use dd to copy the entire partition to a new one. The new partition need to be the same size or larger as dd copies every single bit. I've used it to create backups of harddisks to other harddisks. You need to boot in safe mode/use a live cd then do:-

dd if=/dev/sda1 of=/dev/sdb2

where sda1 is the source and sdb2 is the destinition partition.

Regards
Ian Dobson

---

### Post by dsauter on 2009-05-13
I use GParted live CD for this kind of thing. Works great for getting all your partitions just right.

[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")

Now the real question is if you will need to manually edit your /etc/fstab and /boot/grub/menu.lst files for it to work. I can't answer that for you, but here's something I've done in the past:

Copy the working partition (9.04, in your case) to the spare partition using GParted. Play around all you want to on your "live" partition. If you blow it up, copy the spare partition over the top of your "live-but-now-dead" partition (using GParted again), and you are back up and running!

---

### Post by nickrout on 2009-05-14
In fact you can install and then back out of JYA's vdpau packages with no problems. See this thread for example:

[http://www.gossamer-threads.com/lists/mythtv/mythtvnz/381661](http://www.gossamer-threads.com/lists/mythtv/mythtvnz/381661)

---

### Post by tobiz on 2009-05-14
> **SeanOB said:**
> Hello Mythbuntites!

This is ultimately not a mythbuntu question - but it applies for those of us who use ubuntu as a media center and care about the WAF.

So I just brought up a frontend 9.04 with mythbuntu.
And I was pretty pleased with my idea to install it to a new partition -- so that the working 8.10 install wasn't affected.  This was great - 'cause it allowed me to not break 'the tv' while allowing a leisurely bringup of 9.04.
[http://ubuntuforums.org/showthread.php?t=1148696](http://ubuntuforums.org/showthread.php?t=1148696)
And 9.04 is now my default boot partition and its working great.

So - now I want to try to move to the VDPAU enabled mythtv.  But I don't want to break my existing setup while I try to get this running.

Is there an (easy) way to copy this working 9.04 to a new partition?
I'd like to use grub to default boot to this working one - while I attempt to upgrade the copy with the VDPAU enabled packages.

I could do yet another fresh install of 09.04 -- but I'd rather take this working setup and build from here.

Any ideas?  Pointers?

Ultimately I'd like to have 2 boot options:
- stable working
- hobby / testing / tinkering
This will minimize the chances of me breaking something while I'm tinkering with new features.  And will greatly improve the WAF!


-Sean
SeanOB,
I've just gone through similar to this using Clonezilla to copy my working mythtv s/w partition from an HDD to a SDD leaving /var/lib/mythtv on the HDD. Little tricky to start with but only due to it being the first time I've used Clonezilla. I copied the s/w partition to a USB drive as a backup and then restored from the backup to the SDD expanding the partition on the way. Now I've got a backup of my working 8.10 I can consider an upgrade to try out 9.04 without affecting the WAF (mythtv is the only pvr we have now!)

---

