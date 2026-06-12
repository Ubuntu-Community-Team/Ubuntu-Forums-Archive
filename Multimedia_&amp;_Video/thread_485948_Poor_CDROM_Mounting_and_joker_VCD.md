---
title: "Poor CDROM Mounting and joker VCD"
date: 2007-06-27
forum: Multimedia &amp; Video
---

### Post by Canis familiaris on 2007-06-27
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/106786](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/106786) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Well let me say first. I have run VCDs in my past Operating Systems as follows:
Win95/98/XP : Np problem Whatsoever
Dapper/Edgy: Codec Problem! Again Not much! Managed to run VCDs pretty well.
Feisty: DOES NOT EVEN MOUNT ANY OF MY VCDs
:(

> What's the problem eh? Why can't it even read a VCD.
:(
Tried running VCD off Totem-gstreamer and it does NOT detect a cdrom!!!
:(

> "Well what's the matterrrr...........?????"

I go to terminal:
```
sudo mount /dev/cdrom /media/cdrom
```

and open /media/cdrom and lo it has been mounted.


(Of course to unmount it, you can
```
sudo umount /dev/cdrom
```
and unmount if before ejecting)

> Oh! Relief...er...OH NOOOOOO???
Tried running cdrom with totem but still fails miserably. Opened the .DAT in mpegav, eh! Cannot read!

Then tried:
```
totem vcd://mnt/cdrom
```
Message: CODEC Missing

Scratched my head, how to install codec, (I used Automatix in dapper, but in no mood to use Automatix or EasyUbuntu now)

I do not want to bother with codec just now, what's bothering me is why Ubuntu is not mounting the VCD automatically and why even if I manually mount it, applications like Wine do not recognise it as a cdrom!!!

The difference I found in CDROM mounting in Feisty and Dapper is that in Feisty it mounted the CDROM in /media/cdrom which is symbolically linked to /media/cdrom0.
But in Feisty I found that the CDROM does NOT mount in /media/cdrom0, it mounts in something like /media/<CDROM Label> where <CDROM Label> is the label of the CDROM.
What falls beyond my understanding is why this approach? I mean the Dapper way was working fine and VCDs ran but with this change it is not coincidental that VCDs do not mount automatically. The Kernel can read its different FS if I can manually mount it, so why can't it properly recognise as Dapper did?
I am pretty sure it is due to this reason the bug is apparent. 
Even more problems I faced i this approach is the facts that when I tried to add Ubuntu Install CD as repos:
```
sudo apt-cdrom add
```
It did not recognise the cd at all. Of course I then inserted the CD before the command, it automatically mounted and I added it to my sources list by:
```
sudo apt-cdrom -m add
```

These bugs do make a pattern. I am sure if i can revert to the old way of mount/unmount of dapper in Feisty, I would be able to solve these problems.

---

### Post by avik on 2007-06-27
I haven't tried a VCD, but I know the only way I could get a DVD to play was through xine.  Install the gxine package and see if that works.

---

### Post by Canis familiaris on 2007-06-27
Oh! DVDs work fine (on better hardware than mine though) but not VCDs. VCDs are NOT read at all.

---

### Post by disiungo on 2007-08-16
I can't get ubuntu Feisty Fawn to mount VCD automatically either, but I can play it OK.

I use MPlayer (you can install MPlayer with synaptic). After inserting the VCD I just open the MPlayer window and choose VCD - open disk. It plays the files OK ever since I have chosen xv x11/Xv drivers in Preferences > Video , although there's no disk icon on the screen and no disk in the CD-ROM drive as you browse through system.

However, I would like to know how to get Feisty Fawn to mount the VCD, because I can't copy my disks now. The burning/copying program (Brasero Disk Burning Application) seems unable to skip the problem of an unmounted disk.

Any ideas?

---

### Post by manmath on 2007-11-27
Anurag here is the fix!

I copy the disc to the hard disk as a raw/iso (dd if=/dev/cdrom of=/tmp/image.iso) then I use vcdgear to extract the dat to mpg:

vcdgear -raw2mpg /tmp/image.iso movie.mpg


This is pretty much the method I would recommend as well, the one change I would add is that I use readcd as it handles copying from the CD medium much better than dd, IMHO.

"vcdgear -fix -cue2mpg" has been reliable in extracting a working mpg from a standard image file set.

Just tried with DD and had an issue. readcd is a good tool, I prefer cdrdao myself and this command line should get you a lovelly bin/cue to use vcdgear on:

cdrdao read-cd --device ATA:1,1,0 --driver generic-mmc-raw --read-raw image.cue

Change the device for whatever is your reader!

OR

install readvcd and then 

# readvcd 2 > mv.mpg

OR

Install vcdimager
# vcdxrip

OR

install cdfs
mount -t cdfs /dev/cdrom (or whatever your drive is) /home/movie (or whatever your destination)

---

