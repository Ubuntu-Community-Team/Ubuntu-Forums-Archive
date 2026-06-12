---
title: "No Sound Problem!Please Help!"
date: 2010-01-19
forum: Multimedia Software
---

### Post by vanor241992 on 2010-01-19
Well this is my first post...I am new to Linux...A friend of mine encouraged me to try out Linux some days ago...

So i installed Ubuntu 9.10 Karmic Coala(kernel 2.6.31.17 as i saw)...Well i am pretty fascinated by it and its capabilities as i can see that it's far better than Windows...

But there is a huge problem....Linux recognises my sound card(Creative SB X-Fi Xtreme Audio)but i get no sound at all....when i tried to install the driver from creative i got an Error 2 while giving the make command...i have tried many plugins countless configurations but still nothing...

Can somebody plz help me?Because i don't want to part ways with Linux over that matter...

P.S.I am dual booting with Windows 7 and i am using Ubuntu 9.10 i386..

---

### Post by ikt on 2010-01-19
> **vanor241992 said:**
> But there is a huge problem....Linux recognises my sound card(Creative SB X-Fi Xtreme Audio)but i get no sound at all....when i tried to install the driver from creative i got an Error 2 while giving the make command...i have tried many plugins countless configurations but still nothing...

Can somebody plz help me?Because i don't want to part ways with Linux over that matter...


Heya,

You shouldn't have to install the driver manually because it's already in the kernel. (AKA it's built in)

I have a Creative X-Fi Xtreme Audio myself and it was working first go from the install.

First off have you installed the codecs for MP3's etc?

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

> Ubuntu's commitment to only include completely free software by default means that proprietary media formats are not configured 'out of the box'.

Ubuntu can play the most popular non-free media formats, including DVD, MP3, Quicktime, Windows Media, and more by following the instructions below.

If it still doesn't work after installing support for MP3's etc here are some steps you can take to try and fix the issue:

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

For reference the output of aplay -l:

```
ikt@ikt-910:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: XFi [Creative X-Fi], device 0: ctxfi [Front/WaveIn]
  Subdevices: 7/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: XFi [Creative X-Fi], device 1: ctxfi [Surround]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: XFi [Creative X-Fi], device 2: ctxfi [Center/LFE]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: XFi [Creative X-Fi], device 3: ctxfi [Side]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: XFi [Creative X-Fi], device 4: ctxfi [IEC958 Non-audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Best of luck.

---

### Post by ikt on 2010-01-19
DELETED.

[http://www.homestarrunner.com/sbemail20.html](http://www.homestarrunner.com/sbemail20.html)

---

### Post by vanor241992 on 2010-01-19
Thanks I will try!

---

