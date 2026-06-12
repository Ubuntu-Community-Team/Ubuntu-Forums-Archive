---
title: "[SOLVED] Hardy Heron thinks my DVD player is a CD player?!"
date: 2008-08-27
forum: Multimedia Software
---

### Post by Alphonso B on 2008-08-27
Hello.  I am a new member and not technically gifted.  Please help.  

I have a DVD player that worked fine using VLC under Gutsy Gibbon.  Now I have upgraded to Hardy and it does not work properly.  It plays CDs, no problem.  When I insert a DVD and use VLC to play it I get about 10 seconds of crackle/white noise then silence.  VLC is telling me that it is playing "Audio CD: Track 1".  No it is not, it is Withnail & I!

I am sure I have installed all the correct codecs and lib-wotsits.  I have tired a full re-install (that was fun) but still the same outcome.

I *think* that Hardy has the drive identified somehow, somewhere as a CD not a DVD drive.  My questions are:

1.  How can I find out?
2.  How can I tell my OS that the kit is, in fact, a DVD R+RW?

As I say, I am not tech-savvy; maybe my theory is all wrong.

---

### Post by Alphonso B on 2008-09-03
Either no-one can help or this is in the wrong place.  I will try my query in hardware.

---

### Post by mc4man on 2008-09-03
the only thing that particularly matters is the file system being mounted and how your trying to access it.

With the dvd in the drive run and post
```
sudo lshw -C disk
```

for vlc - open a terminal, type vlc and press enter. When vlc opens go file -> open disc
Post output

---

### Post by wolfen69 on 2008-09-03
"upgrading" can cause problems. perhaps a fresh install of Hardy is in order.

---

### Post by Alphonso B on 2008-09-04
Thanks Mc4man here is the output, I don't understand a lot of it, but I can see the DVD drive listed.  

biz@biz-desktop:~$ sudo lshw -C disk
  *-disk                  
       description: ATA Disk
       product: SAMSUNG SP0812N
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: TK10
       serial: S00MJ10XB35688
       size: 74GiB (80GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000a364f
  *-cdrom:0
       description: DVD-RAM writer
       product: CDDVDW SH-S202J
       vendor: TSSTcorp
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom2
       logical name: /dev/dvd2
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /media/DVDVolume
       version: SB01
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,relatime state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom2
          logical name: /media/DVDVolume
          configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,relatime state=mounted
  *-cdrom:1
       description: CD-R/CD-RW writer
       product: CD-R/RW SW-252B
       vendor: SAMSUNG
       physical id: 0.1.0
       bus info: scsi@1:0.1.0
       logical name: /dev/scd1
       logical name: /dev/sr1
       version: R701
       serial: [SAMSUNG CD-R/RW SW-252B R701EXP
       capabilities: removable audio cd-r cd-rw
       configuration: ansiversion=5 status=open

From the vlc command you suggested all I got was the program running, the white noise and the statement that vlc thought it was a Audio CD again.  Did I do the right thing?  Sorry if I am being stupid here, but this is really annoying me - especially given that it worked before!

Any further advice greatly appreciated.

---

### Post by Alphonso B on 2008-09-04
Wolfen - tried that too, all it did was eat up a load of my ISPs monthly download allocation and I ended up with the same end result.  10secs of white noise and vlc thinking it was an Audio CD.

Odd, I know.

---

### Post by mc4man on 2008-09-04
what's odd is getting results like this after a fresh install, no matter though.

Points of interest in red

> *-cdrom:0
description: DVD-RAM writer
product: CDDVDW SH-S202J
vendor: TSSTcorp
physical id: 1
bus info: scsi@1:0.0.0
logical name: [COLOR="Red"]/dev/cdrom2[/COLOR]
logical name: /[COLOR="Red"]dev/dvd2[/COLOR]
logical name: /dev/scd0
logical name: /dev/sr0

> logical name: /dev/[COLOR="Red"]cdrom2[/COLOR]
logical name: [COLOR="Red"]/media/DVDVolume[/COLOR]
configuration: [COLOR="Red"]mount.fstype=udf mount.options=ro,nosuid,nodev,relatime state=mounted[/COLOR]

your dev links are to high and there is no fstab entry being used for the drive - that's why the filesystem is being mounted to /media/<volume name>
Note though that it is a udf volume (dvd)

So run ```
cat /etc/fstab
``` and post

Also run (from maximized terminal for readability 
```

cat /etc/udev/rules.d/70-persistent-cd.rules
```
----------------------------------------------------------------------------

now if you want, instead of the above and waiting on instructions run this (probably will end up doing this anyway

```
sudo gedit /etc/udev/rules.d/70-persistent-cd.rules
```

and delete all the entries and **reboot** (with no usb flash cards or external drives connected

Leave it looking like this (before rebooting
```

# This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-cd-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.

```

If you do that then try your dvd again and if no go then post the results of the two cat commands (particularly the fstab

---

### Post by Alphonso B on 2008-09-04
Tried the command you kindly supplied, followed the instructions and restarted the computer.  Same result, boo hoo!

Here are the outputs of the 2 cat commands you suggested.  Does this shed any further light on it for you?

biz@biz-desktop:~$ cat /etc/fstab

# /etc/fstab: static file system information.

#

# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc            /proc           proc    defaults        0       0

# /dev/hda1

UUID=b7176b45-1e83-4677-81d9-bdb7aa0ecdc6 /               ext3    defaults,errors=remount-ro 0       1

# /dev/hda5

UUID=9be97189-fea1-42ce-a453-2e95015a309d none            swap    sw              0       0

/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0

/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

biz@biz-desktop:~$ 


Here is what the other command gave me...

biz@biz-desktop:~$ cat /etc/udev/rules.d/70-persistent-cd.rules

# This file maintains persistent names for CD/DVD reader and writer devices.

# See udev(7) for syntax.

#

# Entries are automatically added by the 75-persistent-cd-generator.rules

# file; however you are also free to add your own entries provided you

# add the ENV{GENERATED}=1 flag to your own rules as well.

# CDDVDW_SH-S202J (pci-0000:00:11.1-scsi-1:0:0:0)

ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:11.1-scsi-1:0:0:0", SYMLINK+="cdrom", ENV{GENERATED}="1"

ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:11.1-scsi-1:0:0:0", SYMLINK+="cdrw", ENV{GENERATED}="1"

ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:11.1-scsi-1:0:0:0", SYMLINK+="dvd", ENV{GENERATED}="1"

ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:11.1-scsi-1:0:0:0", SYMLINK+="dvdrw", ENV{GENERATED}="1"

# CD-RRW_SW-252B (pci-0000:00:11.1-scsi-1:0:1:0)

ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:11.1-scsi-1:0:1:0", SYMLINK+="cdrom1", ENV{GENERATED}="1"

ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:11.1-scsi-1:0:1:0", SYMLINK+="cdrw1", ENV{GENERATED}="1"

biz@biz-desktop:~$ 

This is after deleting the previous stuff and re-starting.


Hope this helps you with your sleuthing.  I really appreciate your efforts so far!

---

### Post by mc4man on 2008-09-04
Considering you have a copy of your fstab here and when you edit it I believe you'll get a backup so no need to back it up.

Change these 2 lines and **reboot**
> /dev/hdc /media/cdrom0 udf,iso9660 user,noauto,exec 0 0

/dev/hdd /media/cdrom1 udf,iso9660 user,noauto,exec 0 0

Change to this
```

/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0

/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto,exec 0 0
```


note that's  s[COLOR="Red"]c[/COLOR]d not s[COLOR="Red"]d[/COLOR]c ( 0 = number not letter, or just copy & paste

---

### Post by Alphonso B on 2008-09-04
Sigh.  You really have tried hard to help me Mc4man, but still no joy.:(

Changed the fstab as advised using :~$sudo gedit /etc/fstab (quite proud that I knew how to do that!)

I have realise that there was a terminal output as well when I ran vlc from the terminal.  Here it is, I hope that it can provide a few more clues.  Don't give up on me!  I think that this must be nearly cracked!

VLC media player 0.8.6e Janus
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.5 for DVD access
libdvdnav: DVD Title: DVDVolume
libdvdnav: DVD Serial Number: bec62c6f        
libdvdnav: DVD Title (Alternative): DVDVolume
libdvdnav: Unable to find map file '/home/biz/.dvdnav/DVDVolume.map'
libdvdnav: DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav: DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: faild to read VIDEO_TS.IFO
[00000298] vcd access error: no movie tracks found
[00000298] vcdx access error: unknown ID encountered -- maybe not a proper (S)VCD?
[00000298] access_file access error: file /dev/scd0 is empty, aborting
[00000305] main private error: cannot pre fill buffer
[00000308] cdda access error: could not read block 260 from disc
[00000308] cdda access error: could not read block 280 from disc
[00000308] cdda access error: could not read block 320 from disc
[00000308] cdda access error: could not read block 340 from disc
[00000308] cdda access error: could not read block 360 from disc
[00000308] cdda access error: could not read block 400 from disc
[00000284] main playlist: stopping playback

That line about unable to find map file - that must have something to do with it, or am I getting desperate!

---

### Post by mc4man on 2008-09-04
> Don't give up on me don't worry about that. 

To confirm the settings with a dvd in the drive run the sudo lshw -C disk again and just post the *cdrom entries.

> That line about unable to find map file - that must have something to do with it, or am I getting desperate!
that line is irrelevant 

If the lshw checks out we'll fix vlc and your libs

before we do that run and post this
```
gedit /etc/apt/sources.list
```

Note:
After pasting into reply highlight the text with your mouse  and then click on # in the message taskbar - will put text into a code box - easier to read

---

### Post by Alphonso B on 2008-09-05
I wondered how you got things into those little boxes!  

OK, here's the first one...

 ```
*-cdrom:0

       description: DVD-RAM writer

       product: CDDVDW SH-S202J

       vendor: TSSTcorp

       physical id: 1

       bus info: scsi@1:0.0.0

       logical name: /dev/cdrom

       logical name: /dev/dvd

       logical name: /dev/scd0

       logical name: /dev/sr0

       logical name: /media/cdrom0

       version: SB01

       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram

       configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,relatime state=mounted status=ready

     *-medium

          physical id: 0

          logical name: /dev/cdrom

          logical name: /media/cdrom0

          configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,relatime state=mounted

  *-cdrom:1

       description: CD-R/CD-RW writer

       product: CD-R/RW SW-252B

       vendor: SAMSUNG

       physical id: 0.1.0

       bus info: scsi@1:0.1.0

       logical name: /dev/cdrom1

       logical name: /dev/scd1

       logical name: /dev/sr1

       version: R701

       serial: [SAMSUNG CD-R/RW SW-252B R701EXP

       capabilities: removable audio cd-r cd-rw

       configuration: ansiversion=5 status=open


```

...and here is gedit /etc/apt/sources.list.  Be warned there is loads of it!...
```

# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy universe
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
```

Over to you again, it is all goobledigook to me.

---

### Post by mc4man on 2008-09-05
If you look at the latest lshw you'll see your dvd drive is now  the way it should be now (picking out some relevant lines 
```
logical name: /dev/cdrom
logical name: /dev/dvd
logical name: /dev/scd0
logical name: /dev/sr0
logical name: /media/cdrom0  [COLOR="Red"]<- mountpoint[/COLOR]
configuration:mount.fstype=udfmount.options=ro,nosuid,nodev,relatime state=mounted

```

I'd remove vlc and libdvdcss2
Either do it from synaptic or run this (I'd do below, more complete

```
sudo aptitude purge vlc libdvdcss2
```

After that go into home folder -> click view -> show hidden files and shift+delete the **.vlc** and **.dvdcss** folders. (a must do

after that go here and follow the instr's and commands (copy and paste 

[http://ubuntuforums.org/showthread.php?p=5182809#post5182809](http://ubuntuforums.org/showthread.php?p=5182809#post5182809)

when you get to this line
> sudo apt-get install vlc libdvdcss2 [COLOR="Red"]ubuntu-restricted-extras[/COLOR] w32codecs
remove  what's in red (time consuming and not needed for vlc - add later after vlc is squared away, you really don't even need the w32codecs atm either but it never hurts to have 

If you wish, follow link out to add and set vlc as default dvd player ( at very least follow instr. to change launch command to %m

then try vlc again (try a couple of different titles if possible

Plus it wouldn't hurt to know title your trying to play, some (rare) need a different libdvdnav4 (can set up later or now if needed

---

### Post by Alphonso B on 2008-09-05
Followed all of the instructions.  Still no joy.  I am sure that I did everything correctly - it was nice and clear but still the same effect.

When I put a DVD in before upgrading to Hardy it autoplayed; opening up on the DVD menu.  Now it opens as if it is a data disc (as a window showing a Video_VS folder and an Audio_VS).  When I initiate play using vlc I still get the 10 secs of crackle and hiss and the bottom info bar of vlc reads "Audio CD: track 1".

Arrrgh!  Now what?!

---

### Post by Alphonso B on 2008-09-05
Incidentally I have tried Withnail & I, Gangs of New York, Roll Correctly (a skateboard DVD) and Steamboy (an anime film which was in US format - all of the others being Region 2 = Europe).

---

### Post by mc4man on 2008-09-05
Somewhat perplexing.  
The assumption is a region as been set on the drive (due to previous playback ability. Do you know if one has. 
If not install regionset ( sudo apt-get install regionset
**Then with a dvd** in the drive from the terminal run regionset (just type regionset) and see if it says set about 3 or so lines down (if it has been set answer no and exit.


Also while this shouldn't affect playback go into fstab and make your /dev/scd0 line look like this
> /dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

Your just adding utf8 directly after exec, (no space
Then reboot and describe

What exactly happens when you insert a dvd and do nothing else?

What does the terminal produce from these
> 
vlc dvd:///dev/scd0

> vlc dvd:///media/cdrom0

Also right click on the dvd icon on desktop -> properties -> volume and compare the last 3 lines to screen below (mount point, file system, mount options

---

### Post by Alphonso B on 2008-09-07
OK, back again.  

vlc dvd:///dev/scd0

Gives me...

```
biz@biz-desktop:~$ vlc dvd:///dev/scd0
VLC media player 0.8.6e Janus
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.5 for DVD access
libdvdnav: DVD Title: DVDVolume
libdvdnav: DVD Serial Number: c289f925        
libdvdnav: DVD Title (Alternative): DVDVolume
libdvdnav: Unable to find map file '/home/biz/.dvdnav/DVDVolume.map'
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: faild to read VIDEO_TS.IFO
[00000298] vcd access error: no movie tracks found
[00000298] vcdx access error: unknown ID encountered -- maybe not a proper (S)VCD?
[00000298] access_file access error: file /dev/scd0 is empty, aborting
[00000305] main private error: cannot pre fill buffer
[00000308] cdda access error: could not read block 260 from disc
```

The cdda access error part runs on and on saying it is not able to read from subsequent blocks until it aborts.

running vlc dvd:///media/cdrom0 gives the output...

```
biz@biz-desktop:~$ vlc dvd:///media/cdrom0
VLC media player 0.8.6e Janus
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.5 for DVD access
libdvdread: Attempting to use device /dev/scd0 mounted on /media/cdrom0 for CSS authentication
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/biz/.dvdnav/.map'
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: faild to read VIDEO_TS.IFO
Killed
```

...and vlc greyed over and stopped responding so I just forced quit - hence the Killed line at the end.

I am beginning to wonder if this is a hardware problem.  In other words the actual drive is fubar'd.  Is there anyway to check that?

---

### Post by mc4man on 2008-09-07
What the error is indicating is vlc is trying to access the disk first by properly looking for a dvd structure / udf file system and when not finding it looking for a vcd. When it doesn't find that it looks for an audio cd and obviously fails there too.

> libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.5 for DVD access

Where are you getting libdvdcss2? It should be **1.2.9** if you purged vlc, libdvdcss2, deleted .dvdcss and .vlc, added medibuntu and re-installed? (in other words medibuntu won't give you that version, so was anything else not done?

What about the region thing?
Did you edit the fstab?

_If all the above are done or goo_d what happens if you right click on the dvd icon -> browse folder -> right click on the VIDEO_TS -> open with other application -> Use a custom command 
Use this
```
vlc %m
```


Edit: if above is no go try, with a **dvd in the drive** from the terminal
```
export DVDCSS_METHOD=title && vlc dvd://
```

---

### Post by Alphonso B on 2008-09-10
Sorry mc4man, been busy with work for a couple of days.  Now re-focused on this problem.

The libdvdcss situation? well, ah, I found the original instructions I used to set up DVD playback in Gutsy and though "I'll give this a go - it worked last time" :oops:.  Needless to say I have now baked up a big ol' humble pie and eaten the lot.  I will not try and be clever again.:(

So, I have gone back through this whole thread and re-done all the instructions, as per your  posts. I have also tried the regionset command which gave me:

```
biz@biz-desktop:~$ regionset
regionset version 0.1 -- reads/sets region code on DVD drives
ERROR: Could not open disc "(null)"!
Please ensure there is a readable CD or DVD in the drive.
```

The command ```
vlc %m
``` with a DVD in the drive opened the program but nothing happened at all.  Not even the hiss/crackle Audio CD thing.

The command ```
export DVDCSS_METHOD=title && vlc dvd://

``` sent everything crazy!  Endless scrolling message about "check value failed" it was hard to read as it just kept flashing past.  I killed vlc and terminal in the end.  This with 3 different disks tried.

So, still no progress. Sigh.  What do you think?

---

### Post by mc4man on 2008-09-10
Don't know
Did you have a disk in the drive when you ran regionset?

**If so** try using a data or audio cd instead, if needed specify the device -  regionset /dev/scd0

---

### Post by Alphonso B on 2008-09-11
Yep, tried 3 different DVD from 2 different regions with the regionset command.

Data CD opens with File Browser but I cannot open or copy files.  Error command states disk cannot be accessed.

Audio CD opens with Rhythmbox and lists tracks but I only get jumbled sound when play is selected.

Is it time to go for a re-re-install? :(

Or get the back off and check the hardware? :(:(

---

### Post by SunnyRabbiera on 2008-09-11
it might very well be a hardware issue, and its possible that your DVD drive died.
This might not even be Herons fault, I have had a DVD drive die on me once and even XP picked it up as a CD player that barely worked.

---

### Post by mc4man on 2008-09-12
> its possible that your dvd drive died. +1


> yep, tried 3 different dvd from 2 different regions with the regionset command.

Data cd opens with file browser but i cannot open or copy files. Error command states disk cannot be accessed.

Audio cd opens with rhythmbox and lists tracks but i only get jumbled sound when play is selected.


If you replace the drive reset the 70 .....rules as you did before after installing the drive  or while you'll get /dev/scd0 the rest will be probably be bumped up (/dev/dvd1, /dev/cdrom2, ect

---

### Post by Alphonso B on 2008-09-12
Yes, sadly I think that that has got to be the case.  I had some time this afternoon; got the box open.  Checked the physical appearance of the drive, disconnected, re-booted and then reconnected.  Still the same problems. 

So then I decided to go for a full re-install of the OS.  After all that still had the same issues.  Conclusion?  The drive is dead.

Mc4man - I cannot thank you enough for your promptness, patience and detailed advice.  Although the process has not resolved my hardware issue - not for want of trying (Well, it has; it has shown me what the problem is) I have learnt a lot about Ubuntu along the way.  I had read a lot about the decent people who make up the Ubuntu community and now I have seen the evidence and had the pleasure of interacting with one of them.

Cheers mate - much appreciated!=D>

---

### Post by mc4man on 2008-09-24
@ Alphonso B

I had that feeling it might not be the drive right after you logged out last week as per the unfortunately late / unreceived pm.

What comes to mind is a motherboard/chipset issue. There are several boot parameters available, what you might want to try is to identify your hardware and search if there are any known or random issues specific to it and if so possible fixes.

```
sudo lshw -html > hardware.html
```

This should provide a lot of info in a very readable format, look in home folder for hardware.html

---

### Post by Alphonso B on 2008-10-08
Sorry I have been away.  Tried the command you recommended Mc4man - you're right very user friendly info.  I have not been able to identify any compatibility issues.  I am ready to give up.  The system now works except for the DVD issue.  I don't really want to tinker again.  I am frustrated that I cannot understand the problem (and that I shelled out for a new drive) but I am going with the philosophy that as long as everything else is working I can do my job, surf the 'net and send e-mails I will stick with that.

Again, thanks for your detailed advice.

---

