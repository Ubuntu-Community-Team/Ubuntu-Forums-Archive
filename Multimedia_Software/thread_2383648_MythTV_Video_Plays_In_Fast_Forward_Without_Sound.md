---
title: "MythTV Video Plays In Fast Forward Without Sound"
date: 2018-01-28
forum: Multimedia Software
---

### Post by jamoody on 2018-01-28
I'm setting up MythTV 0.28-2 on Ubuntu 16.04.3 with kernel 4.13.0-26 and  NVIDIA 384.111.  I setup the backend (combined frontend/backend) far  enough to play a video (no tuners, no program guide) and the frontend  plays a video fine.  However, after reboot, the frontend plays the same  video in fast forward without sound.  If I exit the frontend, play the  same video (or some other) in VLC for just a few seconds, then restart  MythTV frontend the same video plays fine.  

So the following workaround works:
* reboot
* play a video via VLC
* start mythfrontend
* play video via MythTV

If I skip the VLC step MythTV plays in fast forward mode.  It seems that  VLC is fixing some issue that MythTV can't do on it's own.  Any ideas  on how to proceed diagnosing?

---

### Post by jamoody on 2018-01-30
This problem has been resolved.  I reviewed mythfrontend.log (without --verbose audio) and found a flood of messages:
           AudioOutputBase audio/audiooutputpulse.cpp:282 (WriteAudio) PulseAudio: WriteAudio, short write, 0 of 6174
           AudioOutputBase audio/audiooutputpulse.cpp:279 (WriteAudio) PulseAudio: WriteAudio, stream write failed: PA_ERR_INVALID
some 416,000 of them for just a few seconds of error playback.  A search  on these messages pointed to PulseAudio as the culprit, and I had chosen  PulseAudio:Default during the MythTV frontend audio setup.  I tried a bunch of  other Audio Output Device options, some which worked and some which  didn't, until I settled on ALSA:hdmi:CARD=NVidia,DEV=1.  That consistently gave me  sound after reboot, without the need to start VLC first.

---

