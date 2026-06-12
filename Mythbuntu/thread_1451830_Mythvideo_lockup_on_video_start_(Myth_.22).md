---
title: "Mythvideo lockup on video start (Myth .22)"
date: 2010-04-11
forum: Mythbuntu
---

### Post by JamesNorris on 2010-04-11
I have a Mythbuntu 9.10 installation which has, since installation, occasionally locked up Myth when I try to play a recorded video or a DVD I have ripped to the HDD. The screen stays blank with the MythTV theme's background image still visible and I am unable to task-switch out and kill the process. 

It has started happening more often and I decided to run Myth with the '-v playback' switch and then just kill the process from a virtual terminal when it happened so I can see the debug information. 

Unfortunately, the debug information wasn't completely helpful, so I've pasted it below in the hope someone else can help. I have attached only the tail-end from where it stopped looking like normal output. 

```
2010-04-11 07:43:22.677 VidOutVDPAU: VDPAU Colorkey: 0x20202 (depth 24)
2010-04-11 07:43:22.677 VideoOutput: Pixel dimensions: Screen 1920x1080, window 1920x1080
2010-04-11 07:43:22.678 VideoOutput: Actual display dimensions: 488x274 mm  Aspect: 1.78102
2010-04-11 07:43:22.678 VideoOutput: Estimated window dimensions: 488x274 mm  Aspect: 1.78102
2010-04-11 07:43:23.804 VDPAU: Version 0
2010-04-11 07:43:23.804 VDPAU: Information NVIDIA VDPAU Driver Shared Library  185.18.36  Fri Aug 14 18:28:21 PDT 2009
2010-04-11 07:43:35.733 WriteAudio: buffer underrun
2010-04-11 07:43:42.654 playCtx, Error: StartDecoderThread() Failed to startdecoder

```

I don't think it is a VDPAU error as I've tried running Myth with the CPU+ option rather than VDPAU... but all suggestions are welcome!

---

