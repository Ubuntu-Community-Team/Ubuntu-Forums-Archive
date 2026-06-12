---
title: "saved amarok eq not in amarokrc"
date: 2017-10-27
forum: Multimedia Software
---

### Post by accounts0 on 2017-10-27
I have this custom EQ saved as "Curvy":

Pic:
[https://imgur.com/a/yUiuA](https://imgur.com/a/yUiuA)

Text values:
```
[COLOR=#000000][FONT=Consolas]band0:  18.0
band1:  5.0
band2: -3.1
band3: -6.5
band4: -3.8
band5: -0.4
band6:  3.1
band7:  6.5
band8:  13.3
band9:  13.9[/FONT][/COLOR]
```[COLOR=#000000][FONT=Consolas]

[/FONT][/COLOR]I look in /home/cb/.kde/share/config/amarokrc & see every other saved EQ except this one that I want.

```
[Playback]EqualizerGains=0,100,43,-55,-17,2,21,40,55,74,85
EqualizerMode=23
EqualizerPresestValues=0,30,-100,-27,-3,0,0,0,0,0,0,0,30,-100,-27,-3,0,0,0,40,74,85,0,30,-100,-43,-9,0,0,0,28,32,32,0,100,43,-55,-17,2,21,40,55,74,85
EqualizerPresetsNames=ResCut0,ResCut1,ResCut2,ResCut3
FadeoutOnPause=false
FadeoutOnStop=false
Master Volume=57
```

I search the file for "Curvy" & nothing.

So I search for one of "Curvy's" EQ values, '13.9'. Still nothing.

Where can I find it?

---

### Post by accounts0 on 2017-11-05
bump

---

