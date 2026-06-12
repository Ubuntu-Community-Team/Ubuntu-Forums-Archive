---
title: "weird sound issue (xubuntu 10.10)"
date: 2011-06-15
forum: Multimedia Software
---

### Post by muzit on 2011-06-15
Hi all,
I have a mediacenter with xbmc and xubuntu 10.10. Sound is provided to the 5.1 system by S/PDIF output.
Yesterday everything was working fine, but today only digital sound works, all my mp3 and regular movies (no hd) don't produce any sound.
I checked in xubuntu desktop, using a youtube video, and no luck, no sound at all. 
Trying to dig a little bit I tested using aplay, with digital files: 

xbmc@htpc:/media/disk/xbmc$ aplay -D iec958:CARD=NVidia,DEV=0 ./dts_hard_rock_44khz.wav 
Sonando WAVE './dts_hard_rock_44khz.wav' : Signed 16 bit Little Endian, Ratio 44100 Hz, Estéreo

this test was successfully completed, as expected. But when I tried with a regular file:

xbmc@htpc:/media/disk/xbmc$ aplay -D iec958:CARD=NVidia,DEV=0 ./Roland-GR-1-Pick-Bass-2-C4.wav 
Sonando WAVE './Roland-GR-1-Pick-Bass-2-C4.wav' : Signed 16 bit Little Endian, Ratio 44100 Hz, Estéreo

It also worked!, in my 5.1 system LCD it says "Stereo", as in the previous days. I tried again using youtube, vlc, xbmc... but no sound at all.

Summarizing, digital sound works fine, other kind of sound doesn't (but it seems to work from aplay)

Any clue where should I look to?

Thanks in advance!

---

