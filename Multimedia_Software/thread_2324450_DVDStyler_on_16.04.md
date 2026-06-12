---
title: "DVDStyler on 16.04"
date: 2016-05-13
forum: Multimedia Software
---

### Post by charlie-watson2 on 2016-05-13
I am trying to compile DVDStyler 2.9.6 from Sourceforge on my new System76 laptop. There is an issue with wxWidgets:
./configure
wxWidgets media library (libwx_gtk2u_media) is missing. However,  "libwx_gtk2u_media-3.0.so.0 -> libwx_gtk2u_media-3.0.so.0.2.0" is on  my system. Does anyone have advice on how to deal with this?

---

### Post by mc4man on 2016-05-14
Not sure why that's an issue, it will build fine just using libwxgtk-media3.0-dev & libwxgtk3.0-dev 
However it won't build at all on 16.04 due to wxsvg being removed from Ubuntu.
[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=813151](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=813151)
A test here a while back produced a working dvdstyler for 16.04 but menus did not show or work correctly in players.
I had noticed this in 14.04 where a dvdstyler with wsvg built on ffmpeg produced some bad menus but wsvg built on libav11 worked fine.

Edit: made some changes from previous test, took a bit to build. A test ppa is here, note that it only exist for about a week.
It seems to be ok though I don't work with dvd material much anymore so only took a cursory look.
If desired add the ppa & test. If ok I'll move the packages to a more permanent ppa, otherwise will just get rid of..
[https://launchpad.net/~mc3man/+archive/ubuntu/check1](https://launchpad.net/~mc3man/+archive/ubuntu/check1)

---

### Post by charlie-watson2 on 2016-05-14
Thank you Doug. It installed quickly and I will test it out soon. I will be creating content in NTSC format in 16:9 aspect ratio.

---

### Post by cbraxton on 2016-05-16
I just tried it on my Ubuntu Mate 16.04 system and it works great! Thanks!

---

### Post by cbraxton on 2016-11-27
I've been using dvdstyler from the ppa for a while now and it mostly works great. One annoyance I'm noticing is that when entering text for a button or text box the editing keys don't work - no backspace/delete or back and forth arrows. They just don't do anything. I'm finding the only way to correct a typo is to highlight the offending character(s) with a mouse and hit the keyboard to replace. Anyone else seeing this problem?

---

