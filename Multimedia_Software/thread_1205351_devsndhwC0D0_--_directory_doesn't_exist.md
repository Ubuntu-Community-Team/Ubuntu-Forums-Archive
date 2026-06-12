---
title: "/dev/snd/hwC0D0 -- directory doesn't exist"
date: 2009-07-05
forum: Multimedia Software
---

### Post by ertayone on 2009-07-05
Today after restarting my computer I tried the [sound fix for HP dvX users]("http://ubuntuforums.org/showthread.php?t=1073090&page=7"), which toggles sound on/off for the laptop speakers and headphone jack manually using hda-verb, and this happened:

```
~/hda-verb-0.3$ sudo hda-verb /dev/snd/hwC0D0 0x0f SET_CONNECT_SEL 1
open: No such file or directory
```I checked my /dev/snd/ directory and sure enough, there aren't any hw files. The fix worked previous before this, and I'm not sure what I might have done recently to erase whatever was in that folder. Is there any way I can recover /dev/snd/hwC0D0 and get my sound working again?

Let me know if there's any other information I can provide to help solve this problem.

Thanks

---

### Post by ertayone on 2009-07-06
Problem solved by [upgrading to the latest version of ALSA](http://ubuntuforums.org/showthread.php?p=6589810), which appears to be the source of the hwC0D0 file. I'm not sure how my version got reverted (or deleted, whatever the case may be), but upgrading did the trick.

---

