---
title: "Missing decoder for WMA9"
date: 2008-11-18
forum: Multimedia Software
---

### Post by InuY4sha on 2008-11-18
Hi guys,

I just burned and installed 8.10 + Medibuntu and restricted extras.
of course before to post I made sure that...
     ... w32codecs is already the newest version.
[and]...libdvdcss2 is already the newest version.

STILL when I log in (thanks to Rythmbox loading my music) I get a pop up from "gstreamer-codec-install" asking to "Search for suitable codec?"
I reply Yes but nothing is found.
I guess the attached picture explains much better the situation (I get this every time I login!) 
To put it in text and make it searchable to other users:
I miss Windows Media Audio 9 decoder | decoder-audio/x-wma, wmaversion=(int)3, bitrate=(int)440016 ...
Where should I look for it? oR how can I identify the file which needs it OR how can I tell rhythmbox not to pop up the annoying message every time (if it can't be solved the clean way)?

---

### Post by gandaran on 2008-11-18
rhythmbox and any gstreamer based player will play wma 8 files but don't play some wma codecs like lossless wma
try another player like mplayer or any xine based player, they can handle any wma/wmv file except drm protected wma/wmv files

---

### Post by Tomatz on 2008-11-18
Try vlc. It has pretty much all codecs installed internally. You can install it via synaptic ;)

---

