---
title: "New DVD encryption?"
date: 2008-03-18
forum: Multimedia &amp; Video
---

### Post by acirilo on 2008-03-18
this is the error i get with Kaffeine player when i try to go to Title Menu on (Hairspray) 
The source can't be read.
Maybe you don't have enough rights for this, or source doesn't contain data (e.g: no disc in drive). (Error opening vtsN=3, domain=2.)


i've installed every codec, libdvdcss. & player under the sun.. none of them will play past the trailers..

[http://www.sabayonlinux.org/forum/viewtopic.php?f=59&t=12355](http://www.sabayonlinux.org/forum/viewtopic.php?f=59&t=12355)

this seems similar to what i'm going thru...

any ideas?

---

### Post by Cresho on 2008-03-18
no but other players can probably read it...like vlc or ...well

---

### Post by acirilo on 2008-03-18
> **Cresho said:**
> no but other players can probably read it...like vlc or ...well

i've tryed gxine, vlc, mplayer & totem... 

totem says it's appears to be encrypted...

---

### Post by jrusso2 on 2008-03-18
Are you able to read any other encrypted DVD's?

---

### Post by acirilo on 2008-03-18
> **jrusso2 said:**
> Are you able to read any other encrypted DVD's?

yes.. playing "dick and Jane" now... the older ones it appears ok..

---

### Post by Neo0351 on 2008-03-18
I had the same problem with Mr. Woodcock a couple days ago.  Wouldn't play vlc, mplayer, and totem.  Somehow played fine in my old tv/dvd combo though.

---

### Post by xc3RnbFO8P on 2008-03-18
Did you install this:
> sudo apt-get install libdvdread3 libxine1-ffmpeg totem-xine build-essential debhelper fakeroot
sudo /usr/share/doc/libdvdread3/install-css.sh

---

### Post by acirilo on 2008-03-18
> **Neo0351 said:**
> I had the same problem with Mr. Woodcock a couple days ago.  Wouldn't play vlc, mplayer, and totem.  Somehow played fine in my old tv/dvd combo though.

lol.. yea.. looks like that will have to work for me.. thanks guys...can't win em all

---

### Post by acirilo on 2008-03-18
> **Ringi said:**
> Did you install this:

yea..  3x total

---

### Post by xc3RnbFO8P on 2008-03-18
I cant find this player** klv**:
[http://ubuntuforums.org/showthread.php?t=727591]("http://ubuntuforums.org/showthread.php?t=727591")
and look at this:
[http://ubuntuforums.org/showthread.php?t=723861&page=2]("http://ubuntuforums.org/showthread.php?t=723861&page=2")

---

### Post by acirilo on 2008-03-18
> **Ringi said:**
> I cant find this player** klv**:
[http://ubuntuforums.org/showthread.php?t=727591]("http://ubuntuforums.org/showthread.php?t=727591")
and look at this:
[http://ubuntuforums.org/showthread.php?t=723861&page=2]("http://ubuntuforums.org/showthread.php?t=723861&page=2")

..interesting... i'm with you... i can't find the klv player

---

### Post by mc4man on 2008-03-18
you can get playback of new line (hairspray) and similar titles by preloading a patched libdvdnav for vlc or compiling mplayer with a patched libdvdread
[http://tobias.rautenkranz.ch/libdvdread_ifo.html](http://tobias.rautenkranz.ch/libdvdread_ifo.html)  for patches
a quick how to
[http://ubuntuforums.org/showthread.php?t=652528&page=2](http://ubuntuforums.org/showthread.php?t=652528&page=2)
works perfectly (to date) - post if any questions - (the vlc patch is under linux i386)

---

### Post by acirilo on 2008-03-18
> **mc4man said:**
> you can get playback of new line (hairspray) and similar titles by preloading a patched libdvdnav for vlc or compiling mplayer with a patched libdvdread
[http://tobias.rautenkranz.ch/libdvdread_ifo.html](http://tobias.rautenkranz.ch/libdvdread_ifo.html)  for patches
a quick how to
[http://ubuntuforums.org/showthread.php?t=652528&page=2](http://ubuntuforums.org/showthread.php?t=652528&page=2)
works perfectly (to date) - post if any questions - (the vlc patch is under linux i386)

AWESOME! thanks mucho

---

### Post by mc4man on 2008-03-18
if you want to make a launcher for preload (vlc)
[http://ubuntuforums.org/showthread.php?t=714499&page=2](http://ubuntuforums.org/showthread.php?t=714499&page=2)
not that elegant - just mucking around

---

### Post by acirilo on 2008-03-18
> **mc4man said:**
> if you want to make a launcher for preload (vlc)
[http://ubuntuforums.org/showthread.php?t=714499&page=2](http://ubuntuforums.org/showthread.php?t=714499&page=2)
not that elegant - just mucking around

ok... i'm a little lost on scripts.. i know ya got to make them executable (can figure that out i think) but the

> #!/bin/bash
cd Desktop;LD_PRELOAD=./libdvdnav.so.4.0.0 vlc

what is happening with the cd Desktop ? 

and if my path to libdvdnav is
> /usr/lib/libdvdnav.so.4.0.0


do i preload that directory?

sorry, i'm a bit ignorante here:confused:

---

### Post by mc4man on 2008-03-18
Did you dl the libdvdnav.so.4.0.0 to your desktop? (patched version)

---

### Post by acirilo on 2008-03-18
> **mc4man said:**
> Did you dl the libdvdnav.so.4.0.0 to your desktop? (patched version)

i added the repository to my source.lists 
and>  sudo apt-get install libdvdnav-ifo4

following the instructions on this page 

[http://tobias.rautenkranz.ch/debian/](http://tobias.rautenkranz.ch/debian/)

---

### Post by mc4man on 2008-03-18
Forget the whole launcher thing - I had tried replacing libdvdnav.so.4.0.0 in /usr/lib with the patched one
before and it didn't work - just tried after making it executablable and it works
Your method with the -ifo4 seems like another way - never tried that - used the dl'ed libdvdnav.so.4.0.0 instead - hence the reason for running the preload command
Edit; assuming vlc now plays these titles fine your method (with the-ifo4) would be the way for other people to go - easier/ less confusing

---

### Post by acirilo on 2008-03-18
> **mc4man said:**
> Forget the whole launcher thing - I had tried replacing libdvdnav.so.4.0.0 in /usr/lib with the patched one
before and it didn't work - just tried after making it executablable and it works
Your method with the -ifo4 seems like another way - never tried that - used the dl'ed libdvdnav.so.4.0.0 instead - hence the reason for running the preload command

vlc does work now.. ... much thanks

---

### Post by enchantedsky on 2008-03-19
I just got the movie Enchanted today, and it won't play. I believe there might be a new encryption on DVDs. I'll try updating my codecs though

---

### Post by acirilo on 2008-03-20
> **enchantedsky said:**
> I just got the movie Enchanted today, and it won't play. I believe there might be a new encryption on DVDs. I'll try updating my codecs though

you will only get it to play >>i think<< using VLC player with the patched libdvdnav-ifo4...

---

### Post by warbread on 2008-04-24
I am also having this problem with Shoot 'Em Up, though just yesterday Cloverfield worked perfectly.

:confused::confused:

---

