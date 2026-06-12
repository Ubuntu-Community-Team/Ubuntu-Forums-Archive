---
title: "DVD sound"
date: 2010-02-28
forum: Mythbuntu
---

### Post by prunesquallor on 2010-02-28
Ican play a dvd (with sound) in VLC and XINE but I don't get any sound when I try to play a DVD via mythtv. 

Any ideas?

---

### Post by byStanderone on 2010-02-28
...[http://www.mythtv.org/wiki/Configuring_Digital_Sound](http://www.mythtv.org/wiki/Configuring_Digital_Sound)

---

### Post by nickrout on 2010-02-28
> **prunesquallor said:**
> Ican play a dvd (with sound) in VLC and XINE but I don't get any sound when I try to play a DVD via mythtv. 

Any ideas?

yes, what does the frontend log say when you try to play a dvd?

---

### Post by prunesquallor on 2010-03-01
> **nickrout said:**
> yes, what does the frontend log say when you try to play a dvd?

Thanks for your response. Below is the tail of the log:


2010-03-01 19:21:54.037 Opened DVD device at /dev/dvd
2010-03-01 19:21:54.078 There are 11 titles on the disk
2010-03-01 19:21:54.079 Title 0 has 0 parts.
2010-03-01 19:21:54.079 Title 1 has 29 parts.
2010-03-01 19:21:54.079 Title 2 has 2 parts.
2010-03-01 19:21:54.079 Title 3 has 9 parts.
2010-03-01 19:21:54.079 Title 4 has 1 parts.
2010-03-01 19:21:54.079 Title 5 has 1 parts.
2010-03-01 19:21:54.079 Title 6 has 1 parts.
2010-03-01 19:21:54.079 Title 7 has 1 parts.
2010-03-01 19:21:54.080 Title 8 has 1 parts.
2010-03-01 19:21:54.080 Title 9 has 1 parts.
2010-03-01 19:21:54.080 Title 10 has 1 parts.
2010-03-01 19:21:54.152 DPMS Deactivated 
2010-03-01 19:21:55.069 AFD: Opened codec 0x9a408f0, id(MPEG2VIDEO) type(Video)
2010-03-01 19:21:55.069 NVP: Disabling Audio, params(-1,-1,-1)
2010-03-01 19:21:56.543 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2010-03-01 19:21:56.787 OSD Theme Dimensions W: 640 H: 480
2010-03-01 19:21:58.454 TV: Changing from None to WatchingPreRecorded
2010-03-01 19:21:58.559 OpenGLVideoSync()
2010-03-01 19:21:59.080 Video timing method: SGI OpenGL
2010-03-01 19:21:59.483 AFD: Warning, video codec 0x9a408f0 id(MPEG2VIDEO) type (Video) already open.
2010-03-01 19:21:59.616 AFD: codec AC3 has 0 channels
2010-03-01 19:21:59.667 AFD: Opened codec 0xab22700, id(AC3) type(Audio)
2010-03-01 19:21:59.680 Opening audio device 'spdif'. ch 2(2) sr 48000
2010-03-01 19:21:59.680 Opening ALSA audio device 'iec958:{ AES0 0x02 }'.
2010-03-01 19:21:59.811 Mixer unable to find control Master
2010-03-01 19:21:59.811 Mixer unable to find control Master
2010-03-01 19:21:59.813 NVP: Enabling Audio
2010-03-01 19:21:59.820 Opening audio device 'spdif'. ch 2(2) sr 48000
2010-03-01 19:21:59.820 Opening ALSA audio device 'iec958:{ AES0 0x02 }'.
2010-03-01 19:21:59.836 Mixer unable to find control Master
2010-03-01 19:21:59.836 Mixer unable to find control Master
2010-03-01 19:22:00.647 WriteAudio: buffer underrun
2010-03-01 19:22:10.033 AFD: Warning, video codec 0x9a408f0 id(MPEG2VIDEO) type (Video) already open.
2010-03-01 19:22:10.177 AFD: Warning, audio codec 0xab22700 id(AC3) type (Audio) already open, leaving it alone.
2010-03-01 19:22:10.178 AFD: codec AC3 has 2 channels
2010-03-01 19:22:10.204 AFD: Opened codec 0xa4bd9bc0, id(DVD_SUBTITLE) type(Subtitle)
2010-03-01 19:22:10.210 AFD: Warning, video codec 0x9a408f0 id(MPEG2VIDEO) type (Video) already open.
2010-03-01 19:22:10.210 AFD: Warning, audio codec 0xab22700 id(AC3) type (Audio) already open, leaving it alone.
2010-03-01 19:22:10.210 AFD: codec AC3 has 2 channels
2010-03-01 19:22:10.210 AFD: Opened codec 0xa4bc3c90, id(DVD_SUBTITLE) type(Subtitle)
2010-03-01 19:22:10.543 GetNextFreeFrame() served a busy frame D. Dropping. AAUUUUUUUUUUUUUUUUUUUUUUUUUUUUL
2010-03-01 19:22:21.715 DPMS Reactivated.
2010-03-01 19:22:22.323 DPMS Deactivated 
2010-03-01 19:22:22.354 NVP: prebuffering pause
2010-03-01 19:22:22.706 NVP: Disabling Audio, params(-1,-1,-1)



Thanks for any help.

---

