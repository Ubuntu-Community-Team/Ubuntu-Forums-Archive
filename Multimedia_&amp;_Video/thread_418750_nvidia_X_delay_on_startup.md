---
title: "nvidia X delay on startup"
date: 2007-04-22
forum: Multimedia &amp; Video
---

### Post by paradoxni on 2007-04-22
Im getting a long delay just before the X server starts, the screen goes black and remains black for approx 1 - 2 mins flashing on and off a few times before finally I get the Nvidia logo and the login screen. Where would I look to find out the cause of this delay?  A friend has a similar hardware setup with Nvidia card and drivers and his X boots instantly.

Otherwise the driver and X seem to be working perfectly.

---

### Post by redneckracin on 2007-04-22
yeah man i am getting the same exact issue....i know when i downloaded the lastest driver from my package manager it said i might have to run a command to restart X..but i was stupid and didn't do it and didn't right it down

---

### Post by paradoxni on 2007-05-02
can anyone point me to any logs etc? so I can try and narrow down the causes of this long delay before Xserver loads? its very annoying and taking twice as long to boot ubuntu as it does XP

---

### Post by paradoxni on 2007-05-12
the way the screen flickers on and off for several mines makes it seem like it has problems detecting modes or something?

---

### Post by paradoxni on 2007-06-24
in an attempt to get to the bottom of this here is a video of my ubuntu booting up, you will notice after the ubuntu scrolling bar a black screen for at least 1min30 sec before X loads!!

[http://www.youtube.com/v/jR4fiHq57UQ](http://www.youtube.com/v/jR4fiHq57UQ)

also immeditately afterloading X I ran DMESG and there is a lot of the following, not sure if its normal or not:

```
[   99.481396]  [<f908ccd0>] _nv009799rm+0x94/0xc4 [nvidia]
[   99.481453]  [<f90a3a63>] _nv002077rm+0x93/0xa4 [nvidia]
[   99.481513]  [<f90a3a3d>] _nv002077rm+0x6d/0xa4 [nvidia]
[   99.481573]  [<f90a39b8>] _nv002067rm+0x34/0x4c [nvidia]
[   99.481632]  [<f90ba132>] _nv002759rm+0x1a/0x20 [nvidia]
[   99.481697]  [<f90a3727>] _nv002085rm+0x117/0x160 [nvidia]
[   99.481760]  [<f90ba20a>] _nv002769rm+0x12/0x18 [nvidia]
[   99.481825]  [<f90999d1>] _nv003633rm+0x71/0xa8 [nvidia]
[   99.481886]  [<f90c460d>] _nv001996rm+0x3d/0x770 [nvidia]
[   99.481953]  [<f90c4cd5>] _nv001996rm+0x705/0x770 [nvidia]
```

I tried going back to the non accelerated "NV" driver and X loads up immediately so its def a nvidia driver issue.

---

