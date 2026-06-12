---
title: "I need login two times in gnome"
date: 2008-04-29
forum: Multimedia Software
---

### Post by DFalconX on 2008-04-29
Since I install the nVidia drivers I need login two times in gnome. 
somebody now how can I repair this problem??

---

### Post by warbread on 2008-04-30
Can you describe your problem in a little more detail?

---

### Post by matthias24 on 2008-05-20
> **warbread said:**
> Can you describe your problem in a little more detail?

I have the exact same problem!
After I boot up the normal login screen appears. I enter the login information and click login. afterwards the console reapears, then the nvidia logo is shown and afterwards the same login screen is shown again. 
With the second login it works.

The only error message I found in my xorg.log was this:
```

(II) NVIDIA(0): Initialized GPU GART.
(WW) NVIDIA(0): Error: Unable to find DOS (Enable/Disable output switching)
(WW) NVIDIA(0):     file path under /proc/acpi/video. NVIDIA X driver will not
(WW) NVIDIA(0):     be able to respond to  display change hotkey events.
(II) NVIDIA(0): Setting mode "1280x1024"

```
But I have no clue what it means

by the way its Ubuntu 8.04 and the original nvidia drivers

Hope someone can help

---

### Post by Dell-Net on 2008-06-11
I have the exact same problem!
any solutions yet? is it a nvidia driver problem? gnome problem? ubuntu problem? need help! its very annoying!

---

