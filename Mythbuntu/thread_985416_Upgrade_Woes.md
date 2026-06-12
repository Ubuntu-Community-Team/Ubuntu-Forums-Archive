---
title: "Upgrade Woes"
date: 2008-11-17
forum: Mythbuntu
---

### Post by prestomation on 2008-11-17
I upgraded to Mythbuntu 8.10 today, and I am having some problems.

I was using the i810 drivers(945G chipset) with 8.04.  I see that driver is now deprecated and am using the generic intel driver.  It appears something with OpenGL is broken.  Mythvideo is working fine, but upon watching Live TV or watching recorded shows, the frontend just dies. 

Tail of my frontend log
```

2008-11-17 15:04:35.733 TV: Changing from None to WatchingPreRecorded
2008-11-17 15:04:37.825 NVP: Timed out waiting for free video buffers.
2008-11-17 15:04:38.788 OpenGLVideoSync()
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  1
  Minor opcode:  0
  Resource id:  0x94
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode:  144
  Minor opcode:  7
  Resource id:  0x2800023

```


Upon further research, a "Option "NoAccel" "True"" in my xorg.conf causes shows to play, but frames drop, along with lots of warnings about that in the logs.  Also, menus are very slow, so it's certainly not a fix.
Also, nothing of interest in my Xorg logs, no errors at all.

I am getting about 1300fps with glxgears so it appears that OpenGL is working,


Thanks for your help

---

### Post by prestomation on 2008-11-17
Well, I found a temporary workaround. turning off DRI in my xorg config allows everything to act pretty much normal.  It killed OpenGL performance, so I turned off the OpenGL menu system(sllllooooooowwww), but I can live with that for now.

I'm not sure if there's extra CPU load because of the noDRI, but I can live with it

---

