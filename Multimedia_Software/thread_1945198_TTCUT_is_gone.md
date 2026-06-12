---
title: "TTCUT is gone?"
date: 2012-03-22
forum: Multimedia Software
---

### Post by MartinusEx on 2012-03-22
Hi folks,

i used to use ttcut and projectx to work on videos , especially the cutting part.

I used it under lucid, after upgrade to oneric it does not start und now, looking for a download i came up blank.
Nothing in synaptic nothing on the web, a tar.gz is a dead link.

Simply nothing on ttcut since 2008

Does any body know what happend, is ttcut still available or not?
Is there any program that provides the same functions?

thanks for your support

Martin

---

### Post by BicyclerBoy on 2012-03-22
Never heard of ttcut..

Programs that I have tried while cutting h264/aac/latm-aac ts etc.. so my comments are biased for that..
(compiled from source)

ProjectX:
- latest ver seems to work with h264
- no latm-aac support (remux first)

tsmuxer:
maybe mpeg.ts only
- should be okay with h264 aac etc
- commercial s/w

avidemux:
- cli & gui
- no latm-aac
- 2.6 uses time cutlist
- 2.5 uses frame cutlist
- sometimes flakey, confusing options

HandBrake:
- cli & gui
- very stable
- very easy to use
- no external cutlist

mkvtoolnix:
- mkvmerge  gui & cli
- does not like latm-aac (remux with ffmpeg)
- okay with h264 in mpeg2ts
- cuts to time or frame count
- cutlist

ffmpeg:
(if you have a version that works)
- cuts to frame counts; only in decode video filter (slow)
- cuts to time (fast inaccurate)
- can use cutlist in cmd line
- video filters available (deshake etc)

mjpegtools:
- not much activity
- doubt any h264 or latm-aac support
- useful for DV frame rate conversions

---

### Post by Eolinwen on 2012-03-25
```
Does any body know what happend, is ttcut still available or not?
Is there any program that provides the same functions?
```

It seems to be a death project unfortunately. :frown:
It was the most powerful application for remove advertising from DVB recording, based on Transcode mainly and ffmpeg too. I've never understood his author to not use a function of Transcode for demultiplexing streams instead of using an external tool like ProjectX.
Links of the project :
[http://ttcut.tritime.de/startseite.2.html](http://ttcut.tritime.de/startseite.2.html)
[http://developer.berlios.de/projects/ttcut/](http://developer.berlios.de/projects/ttcut/)

---

### Post by BicyclerBoy on 2012-03-26
There is dvbcut (no mpeg4 codec support).
A new version dvbcut2 was 'announced' but never materialised.

ProjectX is held is high regard for its ability to fix broken/damaged streams that other programs have problems...

---

