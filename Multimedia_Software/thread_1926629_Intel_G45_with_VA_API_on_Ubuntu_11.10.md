---
title: "Intel G45 with VA API on Ubuntu 11.10"
date: 2012-02-16
forum: Multimedia Software
---

### Post by Heinz on 2012-02-16
Finally I got it to work!

Visit my blog at [http://www.emmolution.org/?p=192]("http://www.emmolution.org/?p=192") if you're interested.

---

### Post by Heinz on 2012-02-25
If you run into problems when pulling libva

```
git commit -a
```

followed by 

```
CTRL-X
```

from nano solves it.

---

### Post by taklap on 2012-07-23
Dude please i have really tried this a billion of times with almost any ubuntu based distro and i never had this working….my laptop got an x4500mhd as you have but……please tell me what im doing wrong even if i follow every step you wrote….now i just installed xubuntu 11.10 to see if the problem is with 12.04 but….same things

libva: VA-API version 0.33.0
libva: va_getDriverName() returns 0
libva: Trying to open /usr/local/lib/dri/i965_drv_video.so
libva: Found init function __vaDriverInit_0_33
libva: va_openDriver() returns 0
vainfo: VA-API version: 0.33 (libva 1.1.0.pre1)
vainfo: Driver version: Intel i965 driver – 1.1.0.pre1
vainfo: Supported profile and entrypoints
VAProfileMPEG2Simple : VAEntrypointVLD
VAProfileMPEG2Main : VAEntrypointVLD

please i dont want to go back in windows for this silly reason but my little kid wants to see H264 cartoons that i have on my server…..thx in advanced for any help.

---

### Post by DiabboVerdde on 2012-09-06
I have the same problem. Board is DG45FC with G45 chipset and X4500HD graphics. Follow the instructions to the letter, but nothing seems to make it work.

I was able to enable VAAPI on this board in the past, but I did so many things in order to make it work that I could never know what action was the correct one.

Any clues to make the DG45FC work with VAAPI?

---

