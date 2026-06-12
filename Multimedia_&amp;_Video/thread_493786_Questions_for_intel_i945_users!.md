---
title: "Questions for intel i945 users!"
date: 2007-07-06
forum: Multimedia &amp; Video
---

### Post by xubu_caapn on 2007-07-06
Can I see your xorg.conf?
Are you able to play any semi-demanding/3D games like Nexuiz, Warsow, Sauerbraten, Doom 3, etc? What are your framerates? What are your settings?
What driver are you using- i810 or intel?
What resolution are you using (if non-widescreen)?

---

### Post by xubu_caapn on 2007-07-09
bump.

---

### Post by xubu_caapn on 2007-07-13
bump.

---

### Post by josys36 on 2007-07-21
The only resolution I can EVER get from my i945 is 1024X768. No matter what I do it stays the same. I am using the intel driver and not the i810 driver.

Jason

---

### Post by fredj on 2007-07-21
The i945 video is not that great. It's slower than an Nvidia Geforce 2 which is a very very old 3D card.
Open a terminal and type glxgears then post your fps here. I will tell you if its the same as mine.

---

### Post by xubu_caapn on 2007-07-22
```
9425 frames in 5.0 seconds = 1884.948 FPS
18294 frames in 5.0 seconds = 3658.698 FPS
18340 frames in 5.0 seconds = 3667.862 FPS
18031 frames in 5.0 seconds = 3606.074 FPS
14684 frames in 5.0 seconds = 2936.419 FPS
5085 frames in 5.0 seconds = 1016.889 FPS
5350 frames in 5.0 seconds = 1069.865 FPS
5351 frames in 5.0 seconds = 1070.128 FPS
4961 frames in 5.0 seconds = 992.172 FPS
4723 frames in 5.0 seconds = 944.499 FPS
15498 frames in 5.0 seconds = 3099.488 FPS
19270 frames in 5.0 seconds = 3853.875 FPS
17058 frames in 5.0 seconds = 3411.440 FPS
12418 frames in 5.0 seconds = 2483.429 FPS
5473 frames in 5.0 seconds = 1094.507 FPS
5486 frames in 5.0 seconds = 1097.063 FPS
5953 frames in 5.0 seconds = 1190.591 FPS
18163 frames in 5.0 seconds = 3623.897 FPS
17534 frames in 5.0 seconds = 3506.660 FPS
18255 frames in 5.0 seconds = 3650.845 FPS
17783 frames in 5.0 seconds = 3556.567 FPS
19077 frames in 5.0 seconds = 3815.183 FPS
19100 frames in 5.0 seconds = 3819.811 FPS
18815 frames in 5.0 seconds = 3762.804 FPS
20757 frames in 5.0 seconds = 4151.238 FPS
16081 frames in 5.0 seconds = 3216.189 FPS
18833 frames in 5.0 seconds = 3766.446 FPS
18446 frames in 5.0 seconds = 3689.192 FPS
18765 frames in 5.0 seconds = 3752.803 FPS

```

i probably included too much, but it seemed to get stable at 3500 later on, so i added everything :)

---

### Post by fredj on 2007-07-23
Well that's not bad. Using the default Ubuntu driver I only get about 1500 on a 1280x800 screen at 24 bit
colour depth. However its not going to set the world on fire. For example I get over 7000 using an Nvidia
6600GT card at 24bits on a 1240x1024 screen and that card is a few generations behind and will only play
modern games at lower resolution and reduced detail. The fact is that the Intel 3D cards are not really
gaming cards and if you look at tests in the computer magazines you will see that often they fail Windows
DirectX 9 tests. You may be able to get some older games working. But don't expect the performance of
a real 3D card.

---

