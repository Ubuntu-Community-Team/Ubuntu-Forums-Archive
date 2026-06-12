---
title: "Can Overscan be fixed with player?"
date: 2009-11-15
forum: Multimedia Software
---

### Post by mike909 on 2009-11-15
I have tried to fix overscan by setting custom resolution in /etc/X11/xorg.conf to no avail. I can deal with not seeing the top/bottom bars of the desktop, but it's tough to watch video with so much overscan. My question is this:
can overscan be dealt with from the playback software, like VLC? To be clear, I don't want to just "crop" the video, but I want it to be "zoomed out" so I can see all of it. See screenshots for explanation...
This is what I am currently dealing with:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=136341&stc=1&d=1258312117[/IMG]
and this is what I want it to be:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=136342&stc=1&d=1258312117[/IMG]
I know MythTV handles overscan correctly, but I would like to know if it's possible with a regular player (like VLC).

ubuntu 9.10
GeForce 6600 (nvidia drivers 1.90.42)
Hooked up to Toshiba RP HDTV via DVI

---

### Post by BFG on 2009-12-16
> **mike909 said:**
> I can deal with not seeing the top/bottom bars of the desktop

It sounds more like the video output of your PC doesn't match the HDTV, rather than an overscan issue.

---

### Post by mike909 on 2009-12-16
no, its overscan...happens when there's not a pixel for pixel match between vid card output res & tv, but I did figure out you can actually specify your resolution using mplayer from command line. I am now using xbmc to play my media which has its own overscan fix, built into interface.

---

