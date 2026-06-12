---
title: "Trying to watch HDTV on laptop"
date: 2006-12-01
forum: Multimedia &amp; Video
---

### Post by Nelson-Ray on 2006-12-01
Hello...
I have a MacBook that I installed edgy on as well as MythTV frontend. I am trying to watch HDTV shows or files that have HD content usually in .TS format. VLC & MPlayer as well as MythFrontend will not play these files. I believe it is because the native resolution of these files are larger than my notebook's 1280x800 screen. Would someone know how to fix this? These files play fine in OS X. Thanks.

---

### Post by superm1 on 2006-12-01
These .TS files of yours, what codecs are they using?  TS is an encapsulation container format.  It can contain things ranging from mpeg2 to mpeg4 to h264.

---

### Post by Nelson-Ray on 2006-12-01
the .TS files are encoded in Mpeg2 or Mpeg4. Whatever is the standard in North America for HDTV broadcasts. I don't use H264 encoded HD files since even my Athlon X2 +4400 desktop chokes on playing those. Should there be a setting in xorg.conf or somewhere to tell these media players how to "downscale" these videos? (Laptop resolution 1280x800, video's are 1920x1080). 

When launched with Mplayer :

VO: [xv] 1920x1080 => 1920x1080 Planar YV12 
aspect: Warning: no suitable new res found!
aspect: Warning: no suitable new res found!
aspect: Warning: no suitable new res found!
aspect: Warning: no suitable new res found!
X11 error: BadAlloc (insufficient resources for operation) ??,?% 0 0 
MPlayer interrupted by signal 6 in module: vo_check_events
- MPlayer crashed. This shouldn't happen.

When launched with VLC :

No accelerated IMDCT transform found
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  141 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  84
  Current serial number in output stream:  85

Also on MythFrontend when it is tuned to a HDTV broadcast, it will show just a blue screen (no picture).

---

### Post by superm1 on 2006-12-02
In the past, when I have seen this, its been because of not enough video ram, or the card not physically supporting textures that large.  So it's kind of odd that it works in MacOS :).  I have a lady friend of mine that has windows on her box, and the same behavior happens in windows - except the computer goes to the blue screen and freezes on hidef content :)

I have an older ATI card that does this too.  Blue screen in myth, with lots of XV errors.  Never found a workaround other then using a newer card with more vram.

So if this laptop can allocate more ram to vram in the bios, try that.  Elsewise, hopefully someone else has some more useful information.

---

### Post by Nelson-Ray on 2006-12-03
Hey SuperM1 you were right about the memory allocation. I fixed my problem by adding :

Option          "LinearAlloc"   "16384"

in my xorg.conf under "Devices" and now I can watch HDTV & HD files on my MacBook in Edgy. Sweeeetttt.

---

### Post by superm1 on 2006-12-03
Great, glad I was able to prod in the right direction for a solution :)

---

### Post by ickyb0d on 2007-02-10
> **Nelson-Ray said:**
> Hey SuperM1 you were right about the memory allocation. I fixed my problem by adding :

Option          "LinearAlloc"   "16384"

in my xorg.conf under "Devices" and now I can watch HDTV & HD files on my MacBook in Edgy. Sweeeetttt.


wow! that fixed my problem as well.  I'm not sure if the number matters per se, but i just copy and pasted that into my Device section and it worked great.  thanks Nelson!

---

