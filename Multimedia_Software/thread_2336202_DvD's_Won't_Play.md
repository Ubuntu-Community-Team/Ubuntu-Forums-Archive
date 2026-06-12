---
title: "DvD's Won't Play"
date: 2016-09-05
forum: Multimedia Software
---

### Post by DeadlyOats on 2016-09-05
I don't know what happened, but for some reason, DvD's will not play in Kubuntu anymore...  I'm using Kubuntu 16.04, fully updated.

Here's what I've done, so far:

1) I used a lens cleaner to clean the DvD lens.

2) I followed these instructions: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs") (That did not work).

3) Then I did a fresh install of Kubuntu 16.04.1.

4) Then I did step two, again.

None of that worked.  The drive definitely works.  I can use it to install Kubuntu. It can view files on the DvD, and most importantly, the same drive can play the same DvDs in Windows, without issue.

When the DvD is put in the drive, the "Most Recent Device" icon in the panel shows the DvD, with the name of the movie, in the list.  It doesn't mount it automatically, nor does Dragon Player automatically come up to play the movie.  Also, if I attempt to manually mount the DvD, it mounts.  I can view files on the DvD, but not play them.

Again, the drive works well without issues in Windows....  So, what can I do to fix this problem?

EDIT:

Looking for answers, I ran:

> export DVDCSS_METHOD=title && export DVDCSS_VERBOSE=2

and:

> vlc dvd://  > vlc_output.log 2>&1

and got:

> [00000000021ab148] core libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 5.0.3
libdvdread: Encrypted DVD support unavailable.
************************************************
**                                            **
**  No css library available. See             **
**  /usr/share/doc/libdvdread4/README.css     **
**  for more information.                     **
**                                            **
************************************************
libdvdnav: DVD Title: FMA_BS_S2_D1
libdvdnav: DVD Serial Number: 3d68b4bd
libdvdnav: DVD Title (Alternative): 
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
[00007f5a200009b8] core input error: ES_OUT_RESET_PCR called
[00007f5a200009b8] core input error: ES_OUT_RESET_PCR called
[00007f5a200009b8] core input error: ES_OUT_RESET_PCR called
[00007f5a200009b8] core input error: ES_OUT_RESET_PCR called


Then I ran:

> sudo lshw -c disk

and got:

> myusername@MYCOMPUTER'SNAME:~$ sudo lshw -c disk
[sudo] password for myusername: 
  *-cdrom                 
       description: DVD-RAM writer
       product: DRW-24B3ST
       vendor: ASUS
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/sr0
       logical name: /media/myusername/FMA_BS_S2_D1
       version: 1.00
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8 state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
          logical name: /media/myusername/FMA_BS_S2_D1
          configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8 state=mounted
  *-cdrom
       description: DVD-RAM writer
       physical id: 0.0.0
       bus info: scsi@3:0.0.0
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/sr1
       logical name: /media/myusername/FULLMETAL_ALCHEMIST
       capabilities: audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8 state=mounted status=ready
  *-disk
       description: ATA Disk
       product: JMicron H/W RAID
       physical id: 0.0.0
       bus info: scsi@7:0.0.0
       logical name: /dev/sda
       version: 0958
       serial: M1MXEM2ZAI1SFJ9WW109
       size: 698GiB (750GB)
       capabilities: removable
       configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512
     *-medium
          physical id: 0
          logical name: /dev/sda
          size: 698GiB (750GB)
          capabilities: partitioned partitioned:dos
          configuration: signature=000c87a5
myusername@MYCOMPUTER'SNAME:~$ 


UPDATE:

I also have a blue ray player.  So, if I have to do extra steps to get that up and running, then I'll need help with that too.

---

### Post by mc4man on 2016-09-05
Run 
```
sudo dpkg-reconfigure libdvd-pkg
```
Then see..

---

### Post by DeadlyOats on 2016-09-05
Yay!  That fixed the DvD playback issue!  However, for Blue Ray playback, I got this error from VLC:

> Blu-ray error:
No valid processing key found in AACS config file.
Your input can't be opened:
VLC is unable to open the MRL 'bluray:///dev/sr1'. Check the log for details.

Since DvD was playing from "/dev/sr0", I figured that the Blue Ray player was "/dev/sr1", and I got that error.  Did I figure correctly?

UPDATE:

Found the answer.  Now I can play Blue Ray movies, too.  The link, goes to an article that explains how to get DvD's and Blue Rays to play on Ubuntu.

[http://www.howtogeek.com/240487/how-to-play-dvds-and-blu-rays-on-linux/]("http://www.howtogeek.com/240487/how-to-play-dvds-and-blu-rays-on-linux/")

It's too bad, though.  It seems the newest version of BD's, (BD+) won't work with this fix.  I guess that means, I won't be buying anymore BD movies.

Here's where I found the answer:

[https://ubuntuforums.org/showthread.php?t=2334555&highlight=valid+processing+key+found+AACS+config+file]("https://ubuntuforums.org/showthread.php?t=2334555&highlight=valid+processing+key+found+AACS+config+file")

Thanks to Geoffrey_Arndt for pointing to the article, a couple of weeks back with the Blue Ray playback fix (a couple of weeks back as of the date of this post) ( and it was in response to someone else's cry for help).

And thank you, mc4man, for your quick and targeted help with my original DvD playback issue.  You're a champ among champions!

---

### Post by bayvista on 2017-03-06
I get the following with VLC trying to read a video I created with DeVeDe.

david@hp-desktop ~ $ vlc
VLC media player 2.2.2 Weatherwax (revision 2.2.2-0-g6259d80)
[00000000009a9148] core libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 5.0.3
libdvdnav: DVD Title: DVDVIDEO
libdvdnav: DVD Serial Number: 58BB7D840000487A
libdvdnav: DVD Title (Alternative): 
libdvdnav: DVD disk reports itself with Region mask 0x00000000. Regions: 1 2 3 4 5 6 7 8

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000122
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00000141
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000007a2
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x000007d1
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x000007e1
libdvdread: Elapsed time 0
libdvdread: Found 2 VTS's
libdvdread: Elapsed time 0
[00007f85500009b8] core input error: ES_OUT_RESET_PCR called
[00007f85500009b8] core input error: ES_OUT_RESET_PCR called
Segmentation fault
david@hp-desktop ~ $ 

If this means anything, please advise.

---

