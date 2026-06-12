---
title: "Myth 8.04 0.21growisofs dvd author error 124"
date: 2008-11-24
forum: Mythbuntu
---

### Post by zf3636 on 2008-11-24
Hello I have standalone mythbackend/frontend machine I am trying to burn my tv recording file size 371MB to dvd using mytharchive I have the latest update for growisofs 1.1.9  I am using a sata dvdrw to burn disks I get the following errors

2008-11-24 14:42 Error failed while running growisofs
2008-11-24 14:42 Result 124, Command was:growisofs-dvd-compat-Z/dev/dvd/ -dvd-video -V "/var/lib/mythtv/recordings/1031_/home/username//mytharchivetemp
2008-11-24 14:42 Terminated
Please check the troubleshooting section of the readme for ways to fix this error. 

2 I do not why but when i get to the end to select the following options HQ, SP, EP, DO NO RE-ENCODE : SP requires 12GB of space to burn to disk. i have enough 30GB of hd space.  can anyone help with this thx.

---

### Post by ian dobson on 2008-11-24
Hi,

Have a look here: [http://ubuntuforums.org/showthread.php?t=918123&highlight=growisofs](http://ubuntuforums.org/showthread.php?t=918123&highlight=growisofs)

Regards
Ian Dobson

---

### Post by klc5555 on 2008-11-24
> **zf3636 said:**
> Hello I have standalone mythbackend/frontend machine I am trying to burn my tv recording file size 371MB to dvd using mytharchive I have the latest update for growisofs 1.1.9  I am using a sata dvdrw to burn disks I get the following errors

2008-11-24 14:42 Error failed while running growisofs
2008-11-24 14:42 Result 124, Command was:growisofs-dvd-compat-Z/dev/dvd/ -dvd-video -V "/var/lib/mythtv/recordings/1031_/home/username//mytharchivetemp
2008-11-24 14:42 Terminated
Please check the troubleshooting section of the readme for ways to fix this error. 

2 I do not why but when i get to the end to select the following options HQ, SP, EP, DO NO RE-ENCODE : SP requires 12GB of space to burn to disk. i have enough 30GB of hd space.  can anyone help with this thx.

genisoimage in Hardy is busted. If growisofs in 8.04 is reporting strange things, it's usually traceable to the wonky genisoimage. genisoimage has been patched in Intrepid but the patch has never been backported to Hardy (or at least hadn't been as of a month or so ago).

Supposedly the fix is to install the Debian package genisoimage_1.1.8-1+b1_i386.deb 

See the thread in this forum "[SOLVED]MythArchive hell" for details.

If this doesn't do it for you, there are other workarounds.

Good luck!

---

### Post by zf3636 on 2008-11-24
Hello thx for quick reply I will try the info above.

---

### Post by zf3636 on 2008-11-30
Hello i have installed the genisoimage 1.1.8 +b1_i386.deb and after updating this file I tried mytharchive to burn dvd and it came up with the same error 124,so I tried a DVD+R disk and dvd burned successfully,the problem was that I was using a DVD-RW disk instead of DVD+R for my previous DVD recording.

Q:1 is it possible to format the DVD-RW disk before and then burn to it thx.

---

### Post by klc5555 on 2008-11-30
> **zf3636 said:**
> Hello i have installed the genisoimage 1.1.8 +b1_i386.deb and after updating this file I tried mytharchive to burn dvd and it came up with the same error 124,so I tried a DVD+R disk and dvd burned successfully,the problem was that I was using a DVD-RW disk instead of DVD+R for my previous DVD recording.

Q:1 is it possible to format the DVD-RW disk before and then burn to it thx.



If your burner recognizes the one type of DVD medium, but not the other, I think that you may already be at the hardware stage of problem solving, rather than growisofs or other software. 

Some burners are fairly finicky about the quality of the media they'll accept. If you've found DVD+R's that yours will accept, I'd just go with those. Of course, on the off chance that the problem was a single defective DVD-RW, you could always run a little test by having mytharchive just create the .iso, then using something like k3b to try to burn the .iso to various media types, including a DVD-RW from a different manufacturer.

All the best!

---

