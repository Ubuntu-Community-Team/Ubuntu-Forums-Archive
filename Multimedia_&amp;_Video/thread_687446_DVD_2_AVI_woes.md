---
title: "DVD 2 AVI woes"
date: 2008-02-04
forum: Multimedia &amp; Video
---

### Post by Virtual_Ron on 2008-02-04
Hi All,

I'm having a strange problem ripping & transcoding DVD's to AVI.

Every time, my resulting AVI files are messed up.   When playing back, they have colored lines and stuff.  They skip around, etc..   hard to explain exactly.  Terribly quality.

I've tried multiple different ripping programs:   dvd::rip, AcidRip, Avidemux, K3B, etc

In each program, I've tried multiple different Codecs:   Xvid2-4, Divx, ffmpeg, etc

I first try the program's default settings, then I've manually messed with the various frame rates, and bit rates.

I've tried deinterlacing, and NO deinterlacing.

No matter what I try, the results are always bad to worse.

I have no problems going the other direction, btw.   I can take a AVI file I've downloaded, and burn a video DVD no problem. (using DeVeDe)

Various Specs:
   AMD64 X2 Dual 6000+
   Ubuntu "Gutsy"  **x86_64**
   ATI Radeon X1200
   ATI 8.1 video drivers
   KDE 3.5.8
   2G of ram
   6G of swap

I recently upgraded my ATI drivers, but this problem existed BEFORE I did that.

Any Ideas or suggestions on what I'm screwing up?
HELP?

Thanks,
Ron

---

### Post by gsmanners on 2008-02-04
Have you been able to play the DVD on that computer?

---

### Post by Virtual_Ron on 2008-02-04
> **gsmanners said:**
> Have you been able to play the DVD on that computer?

yes.  I have no problems playing the dvd, OR the vob files after i've ripped it to my HD.

---

### Post by gsmanners on 2008-02-04
I guess it may be the codec or some encoder issue. FWIW, here's one of the scripts I use:

```
#!/bin/bash
#
# scale=704:528, bitrate=820

# first pass

mencoder vid.vob -fps 30000/1001 -ofps 24000/1001\
 -vf pullup,softskip,crop=720:480:0:0,pp=ac,scale=704:528,hqdn3d=4:3:6,harddup\
 -nosound -ovc x264 -x264encopts\
 bitrate=820:subq=5:frameref=1:bframes=15:b_pyramid:weight_b:turbo=1:threads=auto:pass=1\
 -o /dev/null

# second pass

mencoder vid.vob -fps 30000/1001 -ofps 24000/1001\
 -vf pullup,softskip,crop=720:480:0:0,pp=ac,scale=704:528,hqdn3d=4:3:6,harddup\
 -nosound -ovc x264 -x264encopts\
 bitrate=820:subq=5:8x8dct:frameref=3:bframes=15:b_pyramid:weight_b:threads=auto:pass=2\
 -o vid.avi
```

You'll still have to mux the audio in afterward, but that shouldn't be too difficult. :)

---

### Post by Virtual_Ron on 2008-02-05
> **gsmanners said:**
> I guess it may be the codec or some encoder issue. FWIW, here's one of the scripts I use:

```
#!/bin/bash
#
# scale=704:528, bitrate=820

# first pass

mencoder vid.vob -fps 30000/1001 -ofps 24000/1001\
 -vf pullup,softskip,crop=720:480:0:0,pp=ac,scale=704:528,hqdn3d=4:3:6,harddup\
 -nosound -ovc x264 -x264encopts\
 bitrate=820:subq=5:frameref=1:bframes=15:b_pyramid:weight_b:turbo=1:threads=auto:pass=1\
 -o /dev/null

# second pass

mencoder vid.vob -fps 30000/1001 -ofps 24000/1001\
 -vf pullup,softskip,crop=720:480:0:0,pp=ac,scale=704:528,hqdn3d=4:3:6,harddup\
 -nosound -ovc x264 -x264encopts\
 bitrate=820:subq=5:8x8dct:frameref=3:bframes=15:b_pyramid:weight_b:threads=auto:pass=2\
 -o vid.avi
```

You'll still have to mux the audio in afterward, but that shouldn't be too difficult. :)


Thanks, I'll give that a shot tonight.

If anyone else has a suggestion, I'd love to hear it!    This is pretty much why I built the machine to begin with...

---

### Post by gwpritch on 2008-02-06
I've had the same problem with just about every app I've tried. However, there is a little script out there 'xvidenc' that has worked for me every time. It basically just automates input to mencoder. 

[http://xvidenc.sourceforge.net/](http://xvidenc.sourceforge.net/)

---

