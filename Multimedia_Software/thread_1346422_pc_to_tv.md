---
title: "pc to tv"
date: 2009-12-05
forum: Multimedia Software
---

### Post by mikeize on 2009-12-05
I bought a pc to tv "video converter", to watch files and streaming media from my computer on my television set.  It works fine, in that I get my desktop to show up on my tv set, and I can surf the internet, etc.  However, I CANNOT watch videos of any type on the television (local, or streaming from server)!  The video will play just fine on my (ubuntu 9.10) laptop, but on the tv screen, the media player is just a blank window.  Using my wife's Windows 7 netbook, video plays fine!  I've tried .avi, .mpeg, .rmvb as well as vlc, and movieplayer.  Nothing works when coming from linux source.  I don't understand what could possibly be preventing this from working.  I've even tried every possible screen resolution to no avail.  Can someone please explain to me why this is happening?  Even if I can't fix it, I'd just like to know why.  Thanks!

---

### Post by mikeize on 2009-12-05
bump.

---

### Post by xc3RnbFO8P on 2009-12-05
In Vlc tools> preferences> video, output try change it to X11

---

### Post by efflandt on 2009-12-05
Typically for a simple VGA to TV converter to work, your screen resolution has to be 640x480 (since US NTSC is 480 lines).  Not sure if newer ones down convert higher resolutions.  The TV output of my old Sony laptop (circa January 2000) could display TV fine even with default 1024x768 laptop screen resolution.  But external devices might only convert 640x480 VGA to TV.

It is also possible that you may need to mirror your screen to the other output and screen resolution for both to 640x480, or be using the external screen "only" at that resolution.  Video often writes directly to video memory, so it might only show up on the "active" display (and maybe not both at same time).

It would be easier if you had a TV with VGA, DVI, or HDMI input.  Although, even that can have issues.  My laptop VGA will not properly display in the native resolution of my 40" HDTV (overscanned), although, it will display a lower resolution.  My desktop DVI works fine in the native resolution of an older 27" widescreen HDTV as monitor, but I had to disable "splash" in boot parameters because gpx grub2 crashed if splash was enabled on it.

---

### Post by mikeize on 2009-12-05
efflandt:

Thanks for the reply (you too, Ringi).  I was able to view video by disabling "Mirror" display.  This solves my problem, but I'm still a little confused, since my wife's laptop (win7) can play videos with mirrored displays just fine.  Anyway, thanks so much.

-Mike

---

