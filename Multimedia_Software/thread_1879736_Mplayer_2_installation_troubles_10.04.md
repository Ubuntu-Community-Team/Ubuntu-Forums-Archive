---
title: "Mplayer 2 installation troubles 10.04"
date: 2011-11-12
forum: Multimedia Software
---

### Post by yusuo85 on 2011-11-12
Im using 10.04lts and already had mplayer 1 installed on the system, having trouble playing mkv files smoothly I was advised to upgrade to mplayer 2 only problem being is I cant get the thing installed, I've added the ppa and tried to update but whenever I try it throws me the error seen below

"E: /var/cache/apt/archives/mplayer_3%3a2.0+git20111108.fcbe2b2-0ubuntu1~ripps1~lucid_i386.deb: trying to overwrite '/usr/share/pixmaps/mplayer.xpm', which is also in package mplayer-gui 2"

Thats the error I get running it through update-manager

"Preparing to replace mplayer 2:1.0~rc3+svn20090426-1ubuntu16.1 (using .../mplayer_3%3a2.0+git20111108.fcbe2b2-0ubuntu1~ripps1~lucid_i386.deb) ...
Unpacking replacement mplayer ...
dpkg: error processing /var/cache/apt/archives/mplayer_3%3a2.0+git20111108.fcbe2b2-0ubuntu1~ripps1~lucid_i386.deb (--unpack):
 trying to overwrite '/usr/share/pixmaps/mplayer.xpm', which is also in package mplayer-gui 2:1.0~rc3+svn20090426-1ubuntu16.1
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/mplayer_3%3a2.0+git20111108.fcbe2b2-0ubuntu1~ripps1~lucid_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)"

Thats what I get it if I try and update via terminal

Does anyone have any ideas on how I can get this installed, thanks

---

### Post by MoreOrLess on 2011-11-12
You can force-install it or remove the mplayer-gui package.

---

### Post by yusuo85 on 2011-11-12
Right got it installed, thanks for that, mkv's still arent playing properly though, which is a pain, considering they work fine on my Windows 7 partition

---

### Post by SeijiSensei on 2011-11-12
What video card do you have?  If it's an NVIDIA or ATI card, did you install the proprietary drivers?

---

### Post by yusuo85 on 2011-11-12
Its an ati card, and I do have the drivers installed, grabbed them off the ati website and after installation I could change my screen resolution so I guess they installed correctly

---

### Post by andrew.46 on 2011-11-12
> **yusuo85 said:**
> Im using 10.04lts and already had mplayer 1 installed on the system, having trouble playing mkv files smoothly I was advised to upgrade to mplayer 2 [...]

Just a small and reasonably pedantic point: MPlayer2 is not an *upgrade* from MPlayer it is actually a *fork* of the project...

---

### Post by beew on 2011-11-12
I use mplayer2 in 10.10 and 11.04 to play mkv flawlessly, even with just the nouveau driver on my Nvidia machine (upgraded with xorg-edgres, with the proprietary driver it has the added advantage of vdpau) I tested it only on one ati machine, it works fine with the open source driver as well,- but the card is no longer supported by ADM so there is no proprietary driver, and the open driver is from xorg-edgers. I have installed mplayer2 with ripps ppa and now compile from git, both work extremely well. I think it worked well in 10.04 too, but that was a long time ago so maybe I had just mplayer then, can't remember.

If you use a gui it may cause some problems for some video cards. I remember Umplayer used to throw a fit on the ati machine I tested on, after an upgrade the problem was solved,. you may want to trying playing back with the command line or different gui front ends to see if there is a difference.

---

