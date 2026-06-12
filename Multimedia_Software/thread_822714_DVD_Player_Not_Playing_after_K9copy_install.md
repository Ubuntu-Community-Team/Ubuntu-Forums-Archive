---
title: "DVD Player Not Playing after K9copy install"
date: 2008-06-08
forum: Multimedia Software
---

### Post by cforput on 2008-06-08
I installed K9copy and had all sorts of errors. I have since removed K9. Now when I insert a DVD into my CD/DVD drive, the initial title plays (FBI warning and Intro stuff) and then it just goes blank. Similar things happen when I use Totem. Is there a way to reinstall my driver for the DVD drive? Everything worked fine before I installed K9. I have tried reinstalling both MPlayer and Totem but the same results happen.

No idea why it would play the first title and then stop so any other suggestions would be appreciated too.

I'm using gutsy.

---

### Post by mc4man on 2008-06-08
Do a search in synaptic for libdvdcss2 and see if it's installed
What I'd do is install vlc, make sure libdvdcss2 is installed and try playback. If there are any issues open vlc from the terminal, try to playback a disc and read/post output

---

### Post by cforput on 2008-06-08
> **mc4man said:**
> Do a search in synaptic for libdvdcss2 and see if it's installed
What I'd do is install vlc, make sure libdvdcss2 is installed and try playback. If there are any issues open vlc from the terminal, try to playback a disc and read/post output

VLC did the trick. I will use that instead of Mplayer. Thanks!

---

