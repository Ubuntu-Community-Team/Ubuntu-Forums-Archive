---
title: "Format DVD"
date: 2006-12-07
forum: Multimedia &amp; Video
---

### Post by dontgetshocked on 2006-12-07
I cant burn my dvd, it says among others things I am not root
Also it is not in Fstab, whatever that is?

What can I do to correct this?


Thanks,

---

### Post by taurus on 2006-12-07
What program did you use and do you belong to group cdrom?  From a terminal, Applications -> Accessories -> Terminal, type

```
groups
```

---

### Post by dontgetshocked on 2006-12-08
Yes, I belong to group cdrom
What next? I am also in root and adm as well

---

### Post by taurus on 2006-12-08
Well, I have this line in /etc/fstab for the CD-ROM...

```

/dev/hdc        /media/cdrom0   udf,iso9660   user,noauto     0       0

```

---

### Post by dontgetshocked on 2006-12-08
My Fstab is the same and I also CAN use Nautilus to format dvd's, just not CD/DVD Creator or GnomeBaker ?

---

### Post by taurus on 2006-12-08
Have you tried burning DVD with k3b?

---

### Post by dontgetshocked on 2006-12-08
This is the error message when I try K3B


umount: /media/dvdrecorder is not in the fstab (and you are not root)
:-( unable to proceed with format: Device or resource busy

---

### Post by taurus on 2006-12-08
I have a DVD burner and I didn't have that line in my /etc/fstab!!!  Are you running Dapper or Edgy?

---

### Post by dontgetshocked on 2006-12-08
Edgy

---

### Post by taurus on 2006-12-08
Did you upgrade from Dapper to Edgy or did you do a fresh install of Edgy?

---

### Post by dontgetshocked on 2006-12-08
Upgraded from within dapper

---

### Post by dontgetshocked on 2006-12-08
upgrade

---

### Post by taurus on 2006-12-08
Can you please paste the output here?

```
groups
```

---

### Post by dontgetshocked on 2006-12-08
david root adm dialout fax cdrom floppy tape audio dip plugdev users scanner admin fuse

---

### Post by taurus on 2006-12-08
> **dontgetshocked said:**
> david root adm dialout fax cdrom floppy tape audio dip plugdev users scanner admin fuse
Why did you add yourself to group root in /etc/group?  Remove your login name from group root in /etc/group and see if you can burn it now!!!

```
gksudo gedit /etc/group
```

---

### Post by dontgetshocked on 2006-12-08
umount: only root can unmount /dev/hdd from /media/dvdrecorder
:-( unable to proceed with format: Device or resource busy

dvd+rw-format command:
-----------------------
/usr/bin/X11/dvd+rw-format -gui -force=full /dev/hdd

---

### Post by dontgetshocked on 2006-12-08
I removed myself from root

---

### Post by taurus on 2006-12-08
Is /dev/hdc your DVD burner?  Try modifying your /etc/fstab to look like this then!

```

/dev/hdc        /media/dvdrecorder   udf,iso9660   user,noauto     0       0

```
Then, create a new mount point for it with

```
sudo mkdir /media/dvdrecorder
```

p.s.  Also, make sure you have installed "dvd+rw-format" as well...

```
sudo aptitude update
sudo aptitude install dvd+rw-format
```

---

### Post by dontgetshocked on 2006-12-08
umount: only root can unmount /dev/hdd from /media/dvdrecorder
:-( unable to proceed with format: Device or resource busy

---

### Post by dontgetshocked on 2006-12-08
david@dave-desktop:~$ sudo mkdir /media/dvdrecorder
mkdir: cannot create directory `/media/dvdrecorder': File exists
david@dave-desktop:~$

---

### Post by taurus on 2006-12-08
Let me see your /etc/fstab then...

```
cat /etc/fstab
```

---

### Post by dontgetshocked on 2006-12-08
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdf1 -- converted during upgrade to edgy
UUID=affd439c-e5f4-449b-bff1-51550e3a0334 / ext3 defaults,errors=remount-ro 0 1
# /dev/hdf5 -- converted during upgrade to edgy
UUID=01296063-2cf7-41dd-83bd-377905135cab none swap sw 0 0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdg1   /media/windows   ntfs   defaults,umask=0222   0   0
/dev/hdd        /media/dvdrecorder   udf,iso9660   user,noauto     0       0
# /dev/hdd        /media/dvdrecorder   udf,iso9660 user,noauto     0       0
# /usr/bin/X11/dvd+rw-format -gui -force=full /dev/hdd
# umount: /media/dvdrecorder

---

### Post by ingo on 2006-12-13
Ok, clutching at straws, but you are not in the video group nor lpadmin. Try putting yourself in those and give it another go.

---

