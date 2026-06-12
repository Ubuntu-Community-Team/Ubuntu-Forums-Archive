---
title: "DVD player stopped working"
date: 2008-06-29
forum: Multimedia Software
---

### Post by tparker on 2008-06-29
My DVD player worked fine in this same install in this same computer, no hardware breaks or changes in the machine since it worked. A few weeks ago I ran the regular Ubuntu updates that showed up in the update manager and now the machine will not mount the DVD drive. If I switch to an old Windows hard drive it works fine so the drive itself is okay.

If I go through the drop downs Places>Computer and then click on the CD-RW/DVD+-RW Drive I get the response:
Unable to mount location
No media in the drive
(there is a commercial DVD in the drive that previously played fine on this machine and still plays fine on the DVD player at my TV, same response if I switch to other disks that also worked before)

If I open a program to try and play a DVD I get this:
(using Xine, same as it worked before)
1st error box:
-xine engine error- There is no input plugin available to handle 'dvd:/'. Maybe MRL syntax is wrong or file/stream source doesn't exist.
2nd error box:
The source can't be read. Maybe you don't have enough rights for this, or source doesn't contain data (e.g: not disc in drive). (/dev/scd0)

I have gone back through the 'how to play DVDs tutorial' and redone all it says, none of my files where changed or updated, all came back as already there and already current.

if I check /dev folder the drive shows up as:
cdrom	   ptyb8  ptyq6  ptyv4	ram10	    tty49  ttyda  ttys4  ttyx2
cdrw	   ptyb9  ptyq7  ptyv5	ram11	    tty5   ttydb  ttys5  ttyx3
dvd	   ptybf  ptyqd  ptyvb	ram3	    tty55  ttye1  ttysb  ttyx9
dvdrw	   ptyc0  ptyqe  ptyvc	ram4	    tty56  ttye2  ttysc  ttyxa

the command cat /etc/fstab gives me this:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=d6cb6439-7c8e-4d7d-b52d-14df7b47515d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=b08693d7-1f32-4903-8ab7-fdcb597ded6c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
core:/mnt/PublicShare/share	/mnt/public	nfs	defaults	0	0
core:/home	/home	nfs	defaults	0	0
/dev/scd0       /media/dvd0   udf,iso9660 user,noauto,exec,utf8 0       0

And that is already beyond my own knowledge of linux and what I could find to check in various forums.

Watching DVDs is one of the main uses I have for this computer, I need to fix this.

Any ideas?

computer is AMD Athlon 64 running 32bit Hardy, fresh install during release week, not upgrade.
DVD drive is HP 840i

---

