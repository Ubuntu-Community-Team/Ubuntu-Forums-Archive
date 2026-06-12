---
title: "Lower volume levels have to sound"
date: 2010-09-29
forum: Multimedia Software
---

### Post by shiajun on 2010-09-29
Hello there

I have a little niggle I'd like to solve. I just recently installed ubuntu so I'm quite lost on some stuff. This little annoyance comes from the volume levels in Ubuntu 10.04. I have partitioned my computer to have dual boot into windows and ubuntu, so I know the problems are not related to the hardware itself as everything works just fine in windows. I am using a Dell Inspiron 9400, for reference.

So, the problem is this. The multimedia keys on the computer respond correctly but on the lower three volume settings sound completely drops out as if I had muted the computer. I went into the Alsa mixer to see if I could configure these sound levels and sure enough the master volume was down to zero, PCM and LFE are also low . I changed the settings of the lower levels but when I press on the volume up or down media keys to switch level the settings get reset. I tried just changing one level, exiting and saving through alsactl but it didn't stick. Even after reboot the settings are back to the zero volume on the first levels.  Does anybody have any suggestions?

---

### Post by lidex on 2010-09-30
Have a look here:
[http://ubuntuforums.org/showpost.php?p=9377246&postcount=33](http://ubuntuforums.org/showpost.php?p=9377246&postcount=33)

---

