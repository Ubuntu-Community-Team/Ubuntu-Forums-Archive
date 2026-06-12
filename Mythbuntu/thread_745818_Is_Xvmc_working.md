---
title: "Is Xvmc working?"
date: 2008-04-04
forum: Mythbuntu
---

### Post by 4dognight on 2008-04-04
I have my doubts that Xvmc is working. The reason is I have a P4 1.6 and an FX5200, and it uses 24% CPU on playback for SD . I have deinterlace off. This seems high to me. I am on .21 of myth. I also get these messages in my FE log.

```
2008-04-04 21:39:07.957 Connected to database 'mythconverg' at host: 192.168.2.6
2008-04-04 21:39:07.985 DPMS Deactivated 
2008-04-04 21:39:09.011 AFD: Opened codec 0x8749310, id(MPEG2VIDEO_XVMC) type(Video)
2008-04-04 21:39:09.012 AFD: codec MP2 has 2 channels
2008-04-04 21:39:09.012 AFD: Opened codec 0x8749690, id(MP2) type(Audio)
2008-04-04 21:39:09.103 Opening audio device 'default'. ch 2(2) sr 48000
2008-04-04 21:39:09.104 Opening ALSA audio device 'default'.
2008-04-04 21:39:09.239 VideoOutputXv: XvMC Adaptor Name: 'NV17 Video Texture'
2008-04-04 21:39:09.263 NVP: Forcing decode extra audio option on. 
                        XvMC playback requires it.
2008-04-04 21:39:09.274 OSD Theme Dimensions W: 640 H: 480
2008-04-04 21:39:10.297 TV: Changing from None to WatchingLiveTV
2008-04-04 21:39:10.309 XvMC: picture structure FRAME
2008-04-04 21:39:10.359 The realtime priority setting is not enabled.
2008-04-04 21:39:10.368 Failed to approve 'none' deinterlacer
2008-04-04 21:39:10.368 Couldn't load deinterlace filter 
2008-04-04 21:39:10.469 Video timing method: USleep with busy wait
2008-04-04 21:39:10.480 VideoOutputXv Error: ProcessFrameXvMC: Failed to get OSD lock
2008-04-04 21:39:10.973 VideoOutputXv Error: ProcessFrameXvMC: Failed to get OSD lock
2008-04-04 21:39:17.740 NVP: prebuffering pause
2008-04-04 21:39:17.840 NVP: prebuffering pause
2008-04-04 21:39:21.721 NVP: prebuffering pause
2008-04-04 21:39:21.725 WriteAudio: buffer underrun
2008-04-04 21:39:35.536 NVP: prebuffering pause
2008-04-04 21:39:35.537 WriteAudio: buffer underrun
2008-04-04 21:39:48.019 NVP: prebuffering pause
2008-04-04 21:39:48.119 NVP: prebuffering pause
2008-04-04 21:40:59.024 NVP: prebuffering pause
2008-04-04 21:40:59.140 NVP: prebuffering pause
2008-04-04 21:41:03.911 NVP: prebuffering pause
2008-04-04 21:41:09.930 NVP: prebuffering pause
2008-04-04 21:41:09.939 NVP: prebuffering pause
2008-04-04 21:41:28.348 NVP: prebuffering pause
2008-04-04 21:41:28.454 WriteAudio: buffer underrun
```

---

### Post by 4dognight on 2008-04-04
I should also mention, I tried using both libmpeg and ffmpeg and I get about the same 24% CPU use. But, I DON'T get any of those errors  about buffer underrun or prebuffer pause. So, my guess is XvMC is not configured properly. Any ideas?

---

### Post by superm1 on 2008-04-05
Open nvidia-settings and adjust your xv vertical sync settings.  Also toggle with the opengl vsync setting in Myth.

---

### Post by 4dognight on 2008-04-05
OK, I tried them all, one at a time. Only difference was CPU went up to 30% when I changed one of the settings. All others CPU stayed same.

Is there a test pgm or something that I can run to verify the settings of XvMC?

---

### Post by superm1 on 2008-04-05
> **4dognight said:**
> OK, I tried them all, one at a time. Only difference was CPU went up to 30% when I changed one of the settings. All others CPU stayed same.

Is there a test pgm or something that I can run to verify the settings of XvMC?
If you have a b/w OSD, XvMC is turned on.

Make sure you have the UseEvents "true" in xorg.conf.

---

### Post by 4dognight on 2008-04-05
ok, I checked and its there in the xorg.conf.

What I have noticed is libmpeg uses a lot more cpu than ffmpeg. ffmpeg is using only a few % more CPU than XvMC. Plus I dont get all that annoying choppiness with , like I do with XvMC, due to the buffer underrun errors and prebuffer pauses.

So, my XvMC is enabled. It produces very choppy video and audio, and only saves a few % over using ffmpeg. libmpeg uses almost all the CPU.

I'm not impressed with XvMC, and unless someone can figure out why its so crappy , I will stick to ffmpeg for now.

---

