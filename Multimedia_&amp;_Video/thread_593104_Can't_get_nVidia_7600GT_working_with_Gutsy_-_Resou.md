---
title: "Can't get nVidia 7600GT working with Gutsy - Resource conflicts detected"
date: 2007-10-26
forum: Multimedia &amp; Video
---

### Post by Lemsip on 2007-10-26
I'm having problems getting my nVidia 7600GT working in Gutsy.  Using the restricted 'nvidia' driver, when I start gdm it fails and I get this error at the end of my Xorg.0.log (attached, along with my xorg.conf):

```
(II) Setting vga for screen 0.
(EE) NVIDIA(0): Resource conflicts detected
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
```

I can't find anything earlier in the log to explain the resource conflicts detected, but I'm assuming this is what's causing the problem.  Any ideas?

I've tried envy, and that resulted in the same issue.  I get the same with the 'nv' driver.  I've tried allowing BulletproofX to create me an xorg.conf, but whatever I enter in the config dialog, it fails and reverts to the vesa driver.  The only way I've been able to get X running is with the vesa driver, at 1280x1024.

Some extra info:

CPU is an Intel Core Duo 6300 at 1.86GHz

```
scanpci
pci bus 0x0003 cardnum 0x00 function 0x00: vendor 0x10de device 0x0391 nVidia Corporation G70 [GeForce 7600 GT]

cat /proc/iomem | grep nv
    fd000000-fdffffff : nvidia

```


Suggestions please - I'm going insane here!!! :confused:

---

### Post by lambono on 2007-12-08
Did you every get this working?

---

### Post by Lemsip on 2007-12-09
No, it's still unpredictable.  Half the time everything works fine, and the rest of the time I get these resource conflicts reported in my log and there appears to be no solution other than rebooting and hoping it works a second time.

Hmmm......

---

