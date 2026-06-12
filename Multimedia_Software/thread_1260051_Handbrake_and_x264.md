---
title: "Handbrake and x264"
date: 2009-09-07
forum: Multimedia Software
---

### Post by Shibblet on 2009-09-07
I've asked this over at the HandBrake forums, but I thought I'd ask here too.

Anyone out there converting DVD's to x264 with Handbrake?  I would like to know what your best settings are for speed vs. compression.

I've been encoding since VCD's were hot stuff, and I know that compression settings are all "in the eye of the beholder".  But right now, I am getting ~14-18 FPS on my encodes.  To me that is WAY too slow.

With Xvid, I can get encode speeds of ~50-70 fps.  I'm not expecting that kind of speed for x264, but I'd at least like to get it to work in realtime (24-30fps).  But tell me if that's an unrealistic goal.

My current x264 settings are...
ref=3
mixed-refs
bframes=6
weightb
direct=auto
b-pyramid
me=umh
8x8dct
trellis=1
psy-rd=1,1

---

### Post by Major_Kong on 2009-09-07
It might be possible by tweaking some options... but you are sure to lose compression and/or quality in the process.


[http://forum.doom9.org/forumdisplay.php?f=63](http://forum.doom9.org/forumdisplay.php?f=63) - You should also ask around in this forum.


EDIT:
By using the medium quality preset of h264enc (and encoding script - [http://debian-multimedia.org/dists/unstable/main/binary-i386/package/h264enc.php](http://debian-multimedia.org/dists/unstable/main/binary-i386/package/h264enc.php) ) i was able to encode at ~ 26 fps. But there's a *bit* of quality loss.

---

