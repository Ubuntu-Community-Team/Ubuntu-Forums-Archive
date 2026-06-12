---
title: "no sound after some time ubuntu 11.10"
date: 2011-12-23
forum: Multimedia Software
---

### Post by gaurav1892 on 2011-12-23
Hi,

I installed ubuntu 11.10 server i386 on my desktop. Sound was working fine. After, some time it's gone. Currently no sound.

I followed this document - [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure) but no luck.

Please find the output of wget -O alsa-info.sh [http://www.alsa-project.org/alsa-info.sh;](http://www.alsa-project.org/alsa-info.sh;) chmod +x ./alsa-info.sh; ./alsa-info.sh command at :-

[http://www.alsa-project.org/db/?f=d4c57316ff51ebd94dfe6f7af02d2bf2d3a3d715](http://www.alsa-project.org/db/?f=d4c57316ff51ebd94dfe6f7af02d2bf2d3a3d715)

Please let me know If you need any other data.

Thanks,
Gaurav

---

### Post by shantiq on 2011-12-23
when you reload go to system monitor


and see if for pulse you have [B]uninterruptible
[/B]

if you do right-click and kill it


then try a sound app again

do it twice maybe it should kick in [i hope]

---

### Post by MoreOrLess on 2011-12-23
Try removing the temporary .pulse files with the command below, and then logging out and back in. Sometimes, one of them gets corrupted.

```
rm -rf ~/.pulse*
```

---

