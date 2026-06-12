---
title: "DVDs Do Not Playback With Blu-Ray Drive on Ubuntu 8.10"
date: 2008-12-18
forum: Multimedia Software
---

### Post by BlenderBoy on 2008-12-18
Hi Folks,

I have Ubuntu 8.10 (64-bit) installed and I cannot play DVDs using the default movie player. VLC will play discs just fine, but mplayer or movie player will not. I have done 'sudo apt-get install ubuntu-restricted-extras' and still nothing. However, when I run regionset I get the following: 

[INDENT][COLOR="DarkRed"]sudo regionset

regionset version 0.1 -- reads/sets region code on DVD drives
ERROR: Could not open disc "(null)"!
Please ensure there is a readable CD or DVD in the drive.[/COLOR][/INDENT]

I have put multiple discs in the Blu-Ray drive (GGC-H20L) and still nothing. Any ideas on how to set the region code? I have a feeling this maybe my problem.

Thanks in advance.

---

### Post by mc4man on 2008-12-18
run this to ck. links and device node

```
sudo lshw -C disk
```

---

### Post by BlenderBoy on 2008-12-18
Ok, the output was the following (I'm omitting the HDD info):

[INDENT][COLOR="DarkRed"] *-cdrom
       description: DVD-RAM writer
       product: BDDVDRW GGC-H20L
       vendor: HL-DT-ST
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/cdrw1
       logical name: /dev/dvd1
       logical name: /dev/dvdrw1
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.03
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc[/COLOR][/INDENT]

---

### Post by mc4man on 2008-12-19
mplayer and movie player default to /dev/dvd for access, your set at /dev/dvd1,  (for cd's players default to /dev/cdrom, your /dev/cdrom1

We could change that or just go into the preferences of your players and make the change.

Ex. mplayer

Right click on video screen -> preferences -> misc.

If you want to change drive to /dev/dvd and /dev/cdrom  let me know

---

### Post by mc4man on 2008-12-19
Forgot about regionset, 
Should have worked because the drive is /dev/scd0
Try (with a disk in drive
```
regionset /dev/dvd1
```

---

### Post by BlenderBoy on 2008-12-19
Thanks! I tried the 'regionset /dev/dvd1' cmd & it let me set the region. Now when I play DVDs using movie player I get a white screen with audio. Will changing my config to /dev/dvd help?

---

### Post by mc4man on 2008-12-19
> Will changing my config to /dev/dvd help?

No , totem movie player in 8.10 isn't so good for dvd's. 

I'd stick with vlc or mplayer.
Maybe try smplayer, see this thread, 
[http://ubuntuforums.org/showthread.php?t=917700&highlight=smplayer](http://ubuntuforums.org/showthread.php?t=917700&highlight=smplayer)


What you could try as far as totem is to install totem-xine
```

sudo apt-get install totem-xine libxine1-ffmpeg
```

If totem-xine has same issue  try going right click on Applications -> edit menus and scroll down to Preferences. In right column enable 'multimedia systems selector' if not already enabled.

Then System -> Preferences -> multimedia systems.... and under 'Default output' video tab change to 'X Window System (No Xv)

---

