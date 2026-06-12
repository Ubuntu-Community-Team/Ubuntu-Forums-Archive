---
title: "Taking an image of an EXT4 partition?"
date: 2009-12-07
forum: Mythbuntu
---

### Post by byronmyth on 2009-12-07
I'd like to take a "Ghost" like image of my 9.10 system, annoyingly it seems that Ghost doesn't currently support EXT4 partitions. Anyone got a recomendation, it needs to be able to only store the actual partition in use rather than the whole drive?

---

### Post by matt06 on 2009-12-07
Both [Clonezilla]("http://clonezilla.org/") and [GParted]("http://gparted.sourceforge.net/index.php") both say they support ext4, although there may be caveats.  Just be sure to verify that your image actually works.

Also, doesn't the 9.10 LiveCD have GParted on it?  Just boot that up :)

---

### Post by confused_user on 2009-12-07
use dd, it's easier than all of the other methods out there.

here's a guide, there are loads more

[http://www.backuphowto.info/linux-backup-hard-disk-clone-dd](http://www.backuphowto.info/linux-backup-hard-disk-clone-dd)

another

[http://www.ghacks.net/2009/01/17/dd-the-ultimate-disk-cloning-tool/](http://www.ghacks.net/2009/01/17/dd-the-ultimate-disk-cloning-tool/)

i would pip the output of tar into gzip as well, since dd does not compression on it's own.

---

### Post by byronmyth on 2009-12-07
Are the methods mentioned above able to do the following:
 
I have two internal drives, 1.5Tb each with about 200Gb used on each. I also have an external USB 500gb drive. If that was a Windows system using Ghost, I'd be able to get an image of both the 1.5's onto the external 500 until of course they start to be bigger than the capacity of the 500. Is DD able to do that? Also how much prep would I need to do to for a restore, Ghost would just overwrite anything on the drive, reboot and I'm back in business.
 
The reason I'm wanting to do this is due to the precarious nature of the updates that come down, I've been able to sort everthing that became broken so far, but I get the impression that one will screw up big time sooner or later and I'd like to have a robust image based backup in place so that I keep my other half happy!

---

### Post by SiHa on 2009-12-07
Clonezilla definitely **won't** do this, neither will dd, as both do a 'bitwise' copy of the HDD - empty space looks the same as full space. 

Not sure if gparted will do it either, but it's probably your best bet, epecially as it is available as a Live CD image. Although looking [[COLOR="Blue"]_here_[/COLOR]](http://gparted.sourceforge.net/livecd.php). It seems to be saying that it can't backup a drive/partition itself

---

### Post by byronmyth on 2009-12-07
Hum, that was my fear, 1.5Gb partitions saved that size are no good, It might take me years before I fill those and warrant buying something bigger to backup to. Typically if I'd stuck with EXT3 partitions my copy of Ghost would still work [sigh]

---

### Post by sk8er3810 on 2009-12-07
Could you just use Gparted to shrink the actual partitions down enough and then use dd?

---

