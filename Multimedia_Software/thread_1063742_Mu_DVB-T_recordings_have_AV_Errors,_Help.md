---
title: "Mu DVB-T recordings have A/V Errors, Help"
date: 2009-02-08
forum: Multimedia Software
---

### Post by Col-1023 on 2009-02-08
I've just got a new system, i7 920 with 6GB ram, 3X750 GB HD and a Radeon HD4870 graphics, and the DVB-T receiver is a Dvico Fusion USB 2.0 box hooked to an external areal,and I'm running Ubuntu 8.10.amd64

I've installed Kaffeine and tried the instant record feature, the cpu usage when this is running is very low, however when I use project-x to demux the DVB-T file, ABC-HD (Australia) (1280x720p @ 50fps), it contains many errors, both in audio and video.

I know that the processor and disk systems can't be to blame, since I wasn't running anything else at the time of recording.

Kaffein reports tv reception at 85% SNR, whereas on another windwos pc I was getting around 93% and the stram has less errors.

Does the percent reception matter in regard to errors, and if it does, would an areal booster help?

Thanks In Advance.

---

### Post by xc3RnbFO8P on 2009-02-08
You can use **Devede** to correct these errors,
in Devede use **adjust file size** for better results.

---

### Post by Col-1023 on 2009-02-08
Thanks for your reply.

I had a quick look at Devede, and it seems to be a dvd authoring program.

What I want to do is take the raw DVB-T captures, demux them and then re-encode them with x264.

These errors seem to be part of the stream, for example audio errors are where audio is missing and an empty frame is inserted.

I'm just wondering if the strength of the signal my tuner box receives is the cause of these errors?

---

### Post by xc3RnbFO8P on 2009-02-08
Mobile, wireless, weather, your usb stick overheating, can cause errors.
If you use Devede to encode to mpeg and use Avidemux to encode x264.

---

