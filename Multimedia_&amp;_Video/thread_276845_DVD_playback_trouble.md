---
title: "DVD playback trouble"
date: 2006-10-13
forum: Multimedia &amp; Video
---

### Post by SonicSteve on 2006-10-13
Greetings,

I have scoured the many threads that relate to this but none of them have helped me get very far in my troubleshooting process.

I am highly skilled in in pc hardware and windows. I very much like ubuntu and my skill is growing but I will need anyone who helps to be quite specific in any commands to used in a terminal. I'm not afraid of the terminal though.

Shortly after installing Ubuntu I installed the codecs for playing DVD's. However at some point during an update or ? DVD has stopped working.

I have tried all the players I can find, Gxine, mplayer, ogle and VLC. None work. Gxine works best for what it's worth, it starts for about .5 seconds then shutsdown very abruptly without a message.

I can play mpeg, avi, and perhaps other types of media with these players but DVD. 
I will post my FSTAB file though I don't think that its the problem. I can read and play avi's from the DVD player, just not play actual DVD's.

Thanks.

---

### Post by SonicSteve on 2006-10-13
Here is my FStab file content.
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb1       /media/hdb      ext3	defaults, 0 0
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   iso9660, ro,noauto,user,exec  	0 0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
//server2/mp3 /media/mp3files smbfs credentials=/home/steve/.smbpasswd,uid=steve,gid=steve 0 0
//server2/NetSh /media/NetSh smbfs  credentials=/home/steve/.smbpasswd,uid=steve,gid=steve 0 0

---

### Post by SonicSteve on 2006-10-13
I should mention that I'm not entirely sure which packages/codec files are needed for proper playback.

---

### Post by Kateikyoushi on 2006-10-13
As far as I know you need the libdvdcss2 package, is it installed ?

[Read here.]("https://help.ubuntu.com/community/RestrictedFormats#head-38508785e53c611dde1859232189b2e823135eb9")

---

### Post by JoxBG on 2006-10-13
Just follow the instructions in the online User's guide, DVD playback section under Video chapter. It has a link for the downloding DVD decryption, plus all the needed codecs. I did mine yesterday and everything is working fine.

Also, FWIW, here's a copy of my fstab. Seems to have a sligthly different entry for cdrom devices that what you have:

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda14      /               ext3    defaults,errors=remount-ro 0       1
/dev/hda11      /home/jg/FAT       vfat    umask=000        0       0
/dev/hda10      /home/jg/SHARED    ntfs    umask=0222        0       0
/dev/hda15      none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
j

Hope it helps.

Jox

---

### Post by SonicSteve on 2006-10-13
OK so I tried to do this, it said the database was "locked"

steve@ubuntu:~$ sudo  /usr/share/doc/libdvdread3/examples/install-css.sh
--20:54:29--  [http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss2_1.2.5-1_i386.deb](http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss2_1.2.5-1_i386.deb)
           => `/tmp/libdvdcss.deb'
Resolving [www.dtek.chalmers.se](www.dtek.chalmers.se)... 129.16.30.198
Connecting to www.dtek.chalmers.se|129.16.30.198|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 25,178 (25K) [text/plain]

100%[====================================>] 25,178        72.07K/s

20:54:30 (71.95 KB/s) - `/tmp/libdvdcss.deb' saved [25178/25178]

dpkg:** status database area is locked by another process**
[B][U]
Any idea what I do about this? [/U][/B]

---

### Post by SonicSteve on 2006-10-13
OK so I rebooted, then tried the command again. Success!!
My DVD trouble is now solved.
Thank you so much for your help. You better stop helping me or I may just relegate windows for gaming only.

---

### Post by JoxBG on 2006-10-14
Great. :)  Enjoy your DVD's.

---

