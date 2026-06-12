---
title: "Problems with my soundcard USB 2.0 / 1.1"
date: 2009-09-05
forum: Multimedia Software
---

### Post by smaba on 2009-09-05
Hey,

I'm using a Tascam US-122 Soundcard (external) on a Kubuntu 9.04 64-bit. The problem is that sound (for example when I play music with amarok) stops after a few seconds or minutes. 

That s what my log file tells me:

```
 Cause could be too long delays in usb-hcd interrupt handling.
Sep  5 12:57:49 user-laptop kernel: [ 8016.385452] ALSA /usr/src/Alsa-1.0.20/alsa-driver-1.0.20/usb/usx2y/usbusx2yaudio.c:314: Sequence Error!(hcd_frame=8013791 ep=8in;wait=8013772,frame=8013776).
```

I ve read that unloading the ehci module could help. But I can't unload this module:

```
sudo rmmod ehci_hcd
[sudo] password for smaxyx:
ERROR: Module ehci_hcd does not exist in /proc/modules
```

But I need to unload that modul in order to solve the problems caused by the USB 1.1 Tascam device and my USB 2.0 port. Is there any other way to do that?

regards

smaba

---

