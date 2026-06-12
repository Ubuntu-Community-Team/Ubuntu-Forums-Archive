---
title: "Can't read audio cd"
date: 2009-11-04
forum: Multimedia Software
---

### Post by fouvolant on 2009-11-04
Hi,

When I put in an audio CD in the cd/dvd writer, the disc icon doesn't appear on the desktop. But, under "Places", "Audio Disc" appears. If I click on "Audio Disc", the cd cd/dvd writer make some sound for 2-3 seconds and nothing else. If I launch Nautilus, I still see "Audio Disc", cd/dvd writer sound again, then Nautilus close by itself.

The cd/dvd writer reads movies DVD and software without any problems.

At first, this was in my fstab file:
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

I've replaced it with the followings without any better result:
/dev/hdc       /media/cdrom0   udf,iso9660 ro,user, noauto 0       0
/dev/sr0       /media/cdrom0   udf,iso9660 ro,user, noauto 0       0
/dev/sr1       /media/cdrom0   udf,iso9660 ro,user, noauto 0       0

I'm using Ubuntu 9.04. The cd/dvd writer is a PIONEER DVR-218L.

If I click on Applications/System tools/Device Manager, then "Optical Drive", here's what I see:
Model: DVD-RW  DVR-218L
Vendor: PIONEER
Device File: /dev/sr0
Firmware version: 1.01
Connection type: Internal
Removable media: Yes (ejectable)
Media compatibility: CD-ROM/CD-R/CD-RW/DVD-ROM/DVD+R/DVD+R DL/DVD+RW/DVD-R/DVD-RAM/DVD-RW
Maximum Read Speed: 14x (16,94 MBps)
Maximum Write Speed: 47x (56,45 MBps)
Media capacity: 462.9 MB (485,410,816 bytes)
Partioning: -

ls -l /dev/ | grep sd
brw-rw----  1 root   disk      8,   0 2009-11-02 23:34 sda
brw-rw----  1 root   disk      8,   1 2009-11-02 23:34 sda1
brw-rw----  1 root   disk      8,   2 2009-11-02 23:34 sda2
brw-rw----  1 root   disk      8,   5 2009-11-02 23:34 sda5
brw-rw----  1 root   disk      8,  16 2009-11-02 23:34 sdb
brw-rw----  1 root   disk      8,  17 2009-11-02 23:34 sdb1
brw-rw----  1 root   disk      8,  21 2009-11-02 23:34 sdb5


Right now, I don't have any clues to correct the bugs.

Thanks in advance for helping.

---

### Post by kircher on 2009-11-25
I have the exact same optical drive, and have the exact same problem. Here is the thread I started yesterday: [http://ubuntuforums.org/showthread.php?p=8381777](http://ubuntuforums.org/showthread.php?p=8381777)

---

### Post by kircher on 2009-11-25
does anyone know how I would best go about submitting a bug report for this particular hardware?

---

