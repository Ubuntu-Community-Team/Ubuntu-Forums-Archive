---
title: "running out of video memory"
date: 2007-11-02
forum: Multimedia &amp; Video
---

### Post by Peevish on 2007-11-02
I have a AthlonXP 3200+, 2GB of PC3200 RAM, and a PNY 6600GT.  I am running Gutsy/7.10, 2.6.22-14-generic, nvidia-glx-new [the restricted one].

I'm having some of the [relatively common, so I hear] maximized-window-blackouts due to an apparent bug in the nvidia drivers.  Also, I get very poor playback on videos and games, doesn't matter the size or complexity, I never get more than about 4 spf [note, this is with mplayer, Totem doesn't play anything besides the lovely pink static that is xv trying to run through Compiz's GL base].

Looking around online, I found a short way to circumvent Compiz's stranglehold on video display.  I added these two lines to my xorg.conf ::
```
Option "VideoOverlay" "on"
Option "OpenGLOverlay" "off"
```
That seemed to work great for a bit, but now I get this error from mplayer whenever I fullscreen a video ::
```
X11 error: BadAlloc (insufficient resources for operation)
```

My BIOS shows my GPU as having 128MB, which is correct.  `nvidia-settings' says the same.  However, `lspci -v' returns this ::
```
02:00.0 VGA compatible controller [0300]: nVidia Corporation NV43 [GeForce 6600 GT] [10de:00f1] (rev a2) (prog-if 00 [VGA])
Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
Latency: 248 (1250ns min, 250ns max)
Interrupt: pin A routed to IRQ 19
Region 0: Memory at e8000000 (32-bit, non-prefetchable) [size=16M]
Region 1: Memory at d0000000 (32-bit, prefetchable) [size=256M]
Region 2: Memory at e9000000 (32-bit, non-prefetchable) [size=16M]
[virtual] Expansion ROM at ea000000 [disabled] [size=128K]

```

I would assume that my card/system is allocating RAM/swap to be used as video RAM, but I'm not entirely sure, and can't figure out how to change it.  I really would like to be able to use my computer again. :(

Note: all these issues still occur whether the "Visual Effects" are none, normal, or extra.


Any help ?

---

### Post by Light- on 2007-11-02
You could try disabling the nvidia proprietry driver and use the open-source one, which *should* support Compiz (I have ati so i dont know, but the open-source ati one does). I would also comment out those two lines in the xorg.conf at the same time to see if that makes any difference.

I dont know for sure, but disabling OpenGL overlays would have a severe impact on the performance of things that use OpenGL (games, or mplayer if you use OpenGL as your output)

---

