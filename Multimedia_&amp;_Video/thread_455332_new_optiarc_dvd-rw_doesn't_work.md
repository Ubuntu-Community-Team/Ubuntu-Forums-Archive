---
title: "new optiarc dvd-rw doesn't work?"
date: 2007-05-26
forum: Multimedia &amp; Video
---

### Post by kshbaja on 2007-05-26
hi,
i am running 7.04.  i just replaced a cendyne cd burner that worked fine with the sony-nec optiarc dvd burner (AD-7170A).  it doesn't seem to work.  when i look at the advanced system settings under 'disks and filesystems' the device is recognized but disabled.  attempts to enable the device fail with this error:

"The system reported: mount: block device /dev/scd0 is write-protected, mounting read-only
mount: you must specify the filesystem type"

 it even recognizes the tracks on the audio CDs i put into it, but when it goes to play the tracks it just skips from one to the next.

here is my somewhat mangled fstab file.  i think i screwed up the original setting for cdrom0 when was trying to get this to work.  

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/hda1
UUID=82c70af6-303a-4385-b027-2c4f912f531a / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/hda5
UUID=1444812d-bfd5-4648-9427-0a77054a3d72 none swap sw 0 0
/dev/cdrom /media/cdrom0 iso9660  0 0
/dev/scd0 /media/dvd0 auto nouser,noauto,atime,rw,nodev,noexec,nosuid 0 0


does anyone have a working fstab entry for this device?
thanks.

---

### Post by Talon2 on 2007-05-26
This works here:

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by kshbaja on 2007-05-26
i tried that and it complains it can't find /media/dvd in fstab?  not sure what is telling it to look for that?

are you using the ad-7170A?  did you have to upload any drivers or anything?

-thanks

---

### Post by Talon2 on 2007-05-26
> **kshbaja said:**
> i tried that and it complains it can't find /media/dvd in fstab?  not sure what is telling it to look for that?

are you using the ad-7170A?  did you have to upload any drivers or anything?


Mine is indeed a Silver Optiarc (NEC/Sony) 7170A.

I built a new system a few months ago.  The line I sent you is how Ubuntu 7.04 detected and set it up.  I have not modified fstab.  It just works.

---

### Post by kshbaja on 2007-05-26
hmmm....i wonder if the fact that i upgraded from edgy is whats giving me grief???  thanks for the input.

---

### Post by fflarex on 2007-06-08
@kshbaja: I'm have the exact same drive you do, and mine seems to be acting up as well. Most of the time it will not recognize that I have even put a cd into it, or if it does, it will take 10+ minutes before I can do anything with it (like rip with Sound Juicer). The fact that it *does* work sometimes, without any apparent reason, really confuses me.

I ran some searches and came up with [this topic]("http://ubuntuforums.org/showthread.php?t=409054"), though that solution didn't work for me as I did not find any previous versions of cdparanoia for Feisty. If you figure anything out let me know.

---

