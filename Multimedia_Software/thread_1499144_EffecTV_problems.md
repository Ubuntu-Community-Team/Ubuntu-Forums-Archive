---
title: "EffecTV problems"
date: 2010-06-01
forum: Multimedia Software
---

### Post by duke.tim on 2010-06-01
I try running effectv and I get the following error:
```
v4lsetchannel:VIDIOCSCHAN: Invalid argument
Video initialization failed.
```
My Webcam seems to work fine, I found a Debian bug report that seems similar. [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=513883](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=513883)
i'm using uvcvideo,videodev,v4l2_compat_ioctl32,v4l1_compat,vloopback as kernel modules
I'm on Lucid, 10.04 64 bit
any help would be nice.
Is this a bug?

---

### Post by duke.tim on 2010-06-02
Bump

---

### Post by duke.tim on 2010-06-06
bump

---

### Post by xc3RnbFO8P on 2010-06-06
I have seen this problem with kdenlive, the solution was:
> LD_PRELOAD="/usr/lib/libv4l/v4l2convert.so" kdenlive
try 
> LD_PRELOAD="/usr/lib/libv4l/v4l2convert.so" effectv

---

### Post by duke.tim on 2010-06-07
didn't seem to work(e.g. the effectv). also kdenlive has some minor glitches but seems to work fine. would it make a difference that I use 64bit?

---

### Post by xc3RnbFO8P on 2010-06-07
> would it make a difference that I use 64bit?
Yes :
> LD_PRELOAD="/usr/lib32/libv4l/v4l2convert.so" effectv 

---

### Post by duke.tim on 2010-06-07
ERROR: ld.so: object '/usr/lib32/libv4l/v4l2convert.so' from LD_PRELOAD cannot be preloaded: ignored.

so I moved it to /usr/lib/ didn't work so i've removed them now. any ideas...

---

### Post by xc3RnbFO8P on 2010-06-07
Try this:
> LD_PRELOAD="/usr/lib/libv4l/v4l1compat.so" effectv 
> 
rob@ubuntu:~$ LD_PRELOAD="/usr/lib/libv4l/v4l1compat.so" effectv 
DumbTV OK.
QuarkTV OK.
FireTV OK.
BurningTV OK.
RadioacTV OK.
StreakTV OK.
BaltanTV OK.
1DTV OK.
DotTV OK.
MosaicTV OK.
PuzzleTV OK.
PredatorTV OK.
SpiralTV OK.
SimuraTV OK.
EdgeTV OK.
ShagadelicTV OK.
NoiseTV OK.
AgingTV OK.
TransFormTV OK.
LifeTV OK.
SparkTV OK.
warpTV OK.
HolographicTV OK.
cycleTV OK.
RippleTV OK.
DiceTV OK.
VertigoTV OK.
DeinterlaceTV OK.
NervousTV OK.
RndmTV OK.
RevTV OK.
RandomDotStereoTV OK.
lensTV OK.
DiffTV OK.
BrokenTV OK.
WarholTV OK.
MatrixTV OK.
PUPTV OK.
ChameleonTV OK.
OpTV OK.
NervousHalf OK.
SloFastTV OK.
DisplayWall OK.
BlueScreenTV OK.
ColourfulStreak OK.
TimeDistortion OK.
EdgeBlurTV OK.
47 effects are available.
---------------
Key description
Up/Down     change effect.
Right/Left  change TV channel.
Space       capture a background image(for FireTV, BurningTV, etc.).
            change mode(for SpiralTV, TransFormTV)
ALT+Enter   fullscreen mode(toggle).
TAB         Horizontal flipping(toggle).
Escape      Quit
ALT+0-9     change video input channel.
F1/F2       increase/decrease brightness of video input.
F3/F4       increase/decrease hue.
F5/F6       increase/decrease color balance.
F7/F8       increase/decrease contrast.
F12         show this usage.


---

### Post by duke.tim on 2010-06-07
YES!!! Thanks Alot for your help it Works! \\:D/

---

### Post by xc3RnbFO8P on 2010-06-07
Glad to help :)

---

### Post by michelepolo on 2011-01-18
> **Ringi said:**
> Glad to help :)

GLAD You helped me too!

you may add:

export LD_PRELOAD="/usr/lib/libv4l/v4l1compat.so" effectv

---

### Post by narcisgarcia on 2011-11-16
I've tried the v4l1compat solution in UBuntu GNU/Linux 11.04 (Natty Narwhal), and doesn't work:

```
effectv
```
> v4lopen:VIDIOCGCAP: Invalid argument
Video initialization failed.

```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so effectv
```
> v4lsetchannel:VIDIOCSCHAN: Invalid argument
Video initialization failed.


---

