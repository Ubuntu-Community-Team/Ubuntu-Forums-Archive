---
title: "Standard DVD's and Video files won't play"
date: 2011-06-11
forum: Multimedia Software
---

### Post by Thomas Witten on 2011-06-11
Hi. I'm VERY new to Ubuntu.

Just recently converted and I'm running both Ubuntu 11.04 (the Natty Narwhal?) (about 10 gig partitioned) and Windows Vista.

As said in the title, All DVD's and Video files won't play well: DVD's are pixelated most times, jumpy and sometimes the sound is scratchy - sound usually sorts itself out in a minute or so, but not always and similarly with any video files, like MP4s and other ripped files. I usually use VLC but others also don't work well or not at all. When playing MP4's do work it usually freezes the rest of the computer and I have to force switch off by the main switch as nothing works.

I've tried out tips like the following from users with previous problems on Ubuntu forums but still nothing seems to work:
I've installed libdvdcss2 and the latest vlc. I've uninstalled all my players and reinstalled them.

I don't believe it's a restricted format problem as the DVD drive works fine in vista as does all the video files.

I wondered if perhaps my system specs aren't good enough for Ubuntu:  intel(r) celeron(r) d cpu 220@1.2ghz 1.5ghz   2 gigs ram 32 bit operating system
I drew this while on vista - when I tried to check my system specs using these commands on Ubuntu the "commands were not found": sudo ishw -html > mySpecs.html   and sudo 1shw

Can anyone help please?

Thanks

---

### Post by cottfcfan on 2011-06-12
Could do with some more info really.
Have you installed the restricted codecs.
```
sudo apt-get install ubuntu-restricted-extras
```
Also what Graphics card are you using? and have you installed any graphics card drivers? or are you using the standard open source ones?
Any info will help.

---

