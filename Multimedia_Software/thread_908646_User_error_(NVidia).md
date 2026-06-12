---
title: "User error (NVidia)"
date: 2008-09-02
forum: Multimedia Software
---

### Post by Davini994 on 2008-09-02
So I have a problem with NVidia drivers, probably caused by me, and hopefully easy to sort.

I had it all working ok, but after updating it gave me "the could not configure display device" message on startup and had me booting into low graphics mode.

Which was because it's got "Nvidia-new" driver in somehow, when I have an FX card which requires an older one. It wouldn't let me install the correct driver, or remove the incorrect driver from Add/remove. 

So I disabled the incorrect one in restricted drivers manager. Next thing that I managed to do was remove the incorrect one completely using Synaptic, then put the correct one in on Add/remove. 

So, status now: 

The incorrect driver is still showing as present on restricted drivers, although disabled. 
System boots with nvidia driver, but to 800x600 and fails if I enable the second screen.

This, I think, is the important bit: when I try to open nvidia-settings I get this:

```
X@X-desktop:~$ sudo nvidia-settings
ERROR: NV-CONTROL extension not found on this Display.
ERROR: Unable to determine number of NVIDIA GPUs on ':0.0'.
ERROR: Unable to determine number of NVIDIA Frame Lock Devices on ':0.0'.
ERROR: Unable to determine number of NVIDIA VCSCs on ':0.0'.
```

Although it does open, I don't get any controls other than 5 tick boxes, "enable controls" etc.

Sorry if this has come up before on the forum, but I can't find it I'm afraid. Help please? [-o<

---

