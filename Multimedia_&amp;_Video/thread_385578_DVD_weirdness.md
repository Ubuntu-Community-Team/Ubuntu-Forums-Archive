---
title: "DVD weirdness"
date: 2007-03-15
forum: Multimedia &amp; Video
---

### Post by snitz70 on 2007-03-15
Hi all.  I am fairly new to ubuntu, but I am impressed so far.  I only have one problem.  :(    I can't seeem to mount data dvd-r that were burned in winxp.  I keep getting this error.


mount: block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Then a lot of these appear in my log

[24306.133242] attempt to access beyond end of device
[24306.133246] hdc: rw=0, want=68, limit=4
[24306.133277] isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16

Here are the relavent lines from my fstab

/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0

Strangely enough, I can mount cd-r and commercial dvds on that same drive, so I know the drive is good.  I can also read the dvd in windows xp, so I know that is good.

I am pretty new to the whole linux thing, but not completly clueless.  (although I feel like it on this one)

I am hoping some on you gurus could shed some light on this.  It is driving me crazy.

BTW, I am running on 6.10 with the 2.6.17-11 kernel.

Thanks,

---

### Post by snitz70 on 2007-03-16
I Just updated the firmware on my drive with no luck.

Help!!  This is really starting to get on my nerves.

Thanks,

Brian.

---

### Post by granny4linux on 2007-03-17
Hi snitz70, welcome to Ubuntu. I know there is a solution to your problem so hang in there, it will be worth it.

Try this thread [http://ubuntuforums.org/showthread.php?t=282515&highlight=mount+dvd](http://ubuntuforums.org/showthread.php?t=282515&highlight=mount+dvd)

This thread shows the results of a search I did on "dvd mount", there may be an answer in there for you.

[http://ubuntuforums.org/search.php?searchid=16406807](http://ubuntuforums.org/search.php?searchid=16406807)

I hope this helps you resolve the problem.

---

