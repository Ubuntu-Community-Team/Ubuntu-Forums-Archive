---
title: "DVD Playback halts in vlc."
date: 2008-11-25
forum: Multimedia Software
---

### Post by LinuxFanBoi on 2008-11-25
Hello everyone, this is my first post.  

I'm having difficulty with playing some DVDs in vlc but not all.  after taking the steps in the install instructions stickied to this form,  Playback is good accept when I tried to play "The Core."  I got no error messages either in a window in in the console,  vlc did not crash,  it just simply stopped playing the DVD.  It always stops at the same points in only certain scenes.

I have a fealing that what I found in my console window may lend a hint to what the problem is.

```
libdvdnav: Using dvdnav version 4.1.2 from http://dvd.sf.net
libdvdnav: DVD Title: CORE_WS
libdvdnav: DVD Serial Number: 2EDA5F43
libdvdnav: DVD Title (Alternative): CORE_WS
libdvdnav: Unable to find map file '/home/admin/.dvdnav/CORE_WS.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
libdvdnav: Suspected RCE Region Protection!!!
libdvdnav: Suspected RCE Region Protection!!!
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[00000474] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
libdvdnav: Suspected RCE Region Protection!!!
[00000513] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[00000515] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:448000
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
```

Any Ideas?  This is a US region DVD and I made sure that my DVD player was set to 'US.'  The audio/video is great for as long as vlc continues to play the DVD.

---

### Post by Bablefish on 2008-11-25
2 First is install the Kaffiene player, I find it works best for playing DVDs. Second is Automatrix just Google it.

---

### Post by LinuxFanBoi on 2008-11-25
Probably should mention that I use Gnome not KDE.

---

### Post by LinuxFanBoi on 2008-11-25
Same issue in Kaffeine, only instead of closing the Window it just stops the playback.  When I hit play it resumes from the beginning of that chapter and then stops again at the same point.

I took a look at the disk and it does look fairly beaten up.

---

