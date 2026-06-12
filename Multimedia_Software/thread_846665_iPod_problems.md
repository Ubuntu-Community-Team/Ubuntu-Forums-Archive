---
title: "iPod problems"
date: 2008-07-01
forum: Multimedia Software
---

### Post by TheMouse on 2008-07-01
I'm running Ubuntu 8.04.

I installed an up to date version of Banshee. It recognizes the iPod. It says that it has transferred the music. When I go the the iPod section of Banshee, I can play music from it. I can open the Music.m3u by clicking on it in a file browser window. I can play songs by going into iPod/iPod_control/Music. The iPod registers the 10 gigs as being full.

The thing is, when I try to play songs like normal, it says that I have 0 songs by 0 artists on 0 albums. I can't find where it could possibly have gone.

Anyone know what I need to do?

---

### Post by |{urse on 2008-07-01
whats the make and model of your ipod? what generation? And is it a macpod or has it been formatted as a winpod (did you ever use itunes on windows with it)

---

### Post by TheMouse on 2008-07-01
It's an 80 gig iPod classic, version 1.1.2 PC. It has never been connected to another computer before.

---

### Post by |{urse on 2008-07-01
yeah that's got te same problem as the nano 3g. Unfortunately our friends at apple have added an extra layer of encryption to the 5g and 5.5g ipod classic and the nano 3g which make syncing currently impossible with linux (until some nice nerd cracks it). Sorry man, i just had to trade my 3g to a friend for a 1g nano just because of this. I feel your frustration man.

---

### Post by TheMouse on 2008-07-01
That seriously sucks. I just spent a bunch of money on this thing, and I can't use it. Damn it.

---

### Post by |{urse on 2008-07-01
sell it on ebay and get an older model, install linux on it. =|

---

### Post by TheMouse on 2008-07-01
Well, if I absolutely have to, I'll just tag another computer and transfer all my music to that one and synch it with the iPod. I'll be stuck with only the music I have right now, but it's better than nothing.

---

### Post by |{urse on 2008-07-01
yeh or you could find an amdx or intelx edition of OSX .iso and run it in a vm, I think virtualbox is the only it works on currently. I've tried to get an xp vm + itunes + hal extender to sync my 3g but no love.

---

### Post by TheMouse on 2008-07-01
I'm not sure where one would do such a thing. I'm not terribly savvy. (:

---

### Post by TheMouse on 2008-07-01
Can one use VirtualBoxOSE to run an intel OS X iso? Or should I try some other version?

---

### Post by TheMouse on 2008-07-02
I'm trying to use Wine to solve my problems -- which sounds a little off, now that I think about it. I've tried a couple of times, and the installation of iTunes freezes at, "Status: Registering iTunes automation server." The terminal says:

Backtrace:
=>1 0x7f45062d in gearaspiwdm.sys (+0x62d) (0x7ecc592c)
  2 0x7f451c7e in gearaspiwdm.sys (+0x1c7e) (0x7ecc5938)
  3 0x7ee730d0 in winedevice (+0x30d0) (0x7ecc59e8)
  4 0x7ee4b6d9 in advapi32 (+0x2b6d9) (0x7ecc5a38)
  5 0x7bc6b0de call_thread_entry_point+0xe() in ntdll (0x7ecc5a48)
  6 0x7bc6b772 in ntdll (+0x5b772) (0x7ecc5ae8)
  7 0x7bc6b98c in ntdll (+0x5b98c) (0x7ecc63d8)
  8 0xb7e814fb start_thread+0xcb() in libpthread.so.0 (0x7ecc64c8)

Anyone had any luck with getting iTunes to run in Wine?

---

### Post by TheMouse on 2008-07-02
I have absolutely no idea what happened, but I messed around with gtkpod for a while, and the iPod recognizes the music as music, and the cover art as cover art. I can't add playlists, so I'm stuck with by artist or by album, but I'm okay with that over being able to do nothing.

Let's see if I can add videos...

---

### Post by tijmz on 2008-07-02
> yeah that's got te same problem as the nano 3g. Unfortunately our friends at apple have added an extra layer of encryption to the 5g and 5.5g ipod classic and the nano 3g which make syncing currently impossible with linux (until some nice nerd cracks it). Sorry man, i just had to trade my 3g to a friend for a 1g nano just because of this. I feel your frustration man.
Either I got the generation numbering wrong, or the iPod nano 3g (this is the nano video, right?) has been working well for me ever since I upgraded to Hardy Heron. The library to handle this generation was fixed [quite some time before](http://www.monroe.nu/archives/110-iPod-Classic-Will-Be-Supported.html), but was always to lazy to recompile Amarok (which was likely what I had to do), so only after the upgrade did things start working for me.

The Amarok wiki has some info on this:
[http://amarok.kde.org/wiki/Media_Device:IPod#My_iPod_does_not_show_any_music](http://amarok.kde.org/wiki/Media_Device:IPod#My_iPod_does_not_show_any_music)

I never tried adding video, so I don't know whether that works, too.

Edit: also see the [wiki of gtkpod on this subject](http://gtkpod.wikispaces.com/Sysinfo+File#ClassicNano3g)

---

