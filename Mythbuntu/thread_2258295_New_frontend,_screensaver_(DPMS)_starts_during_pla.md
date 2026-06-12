---
title: "New frontend, screensaver (DPMS) starts during playback"
date: 2014-12-26
forum: Mythbuntu
---

### Post by crow-jamesm on 2014-12-26
Hello all,

I just installed Ubuntu 14.04 (and added MythTV from the Mythbuntu-control-centre program). I have two monitors connected with Mythfrontend running on the second monitor. Everything is working except the screensaver (blank screen) does not get disabled when recording playback starts in Myth. The screensaver is set to blank the display after 5 minutes. Every 5 minutes the screen blanks and I have to press a button on the remote to restore the video. Audio continues to play through the TV speakers.

From the frontend log I see that DPMS is disabled right after playback starts. Approximately 5 minutes later DPMS is re-enabled. Any idea how to get Myth to disable the screen blanking while playing back recordings?

The video card is Intel (Core i7 CPU). The primary monitor is builtin because the PC is an all in one. The second monitor (TV) is connected by HDMI and the screen is just expanded across both monitors.

```

james@bedroom:~$ egrep "(DPMS|StartTV)" /var/log/mythtv/mythfrontend.log
Dec 26 11:56:04 bedroom mythfrontend.real: mythfrontend[27298]: I CoreContext tv_play.cpp:412 (StartTV) TV: Entering main playback loop.
Dec 26 11:56:04 bedroom mythfrontend.real: mythfrontend[27298]: I CoreContext screensaver-x11.cpp:149 (DisableDPMS) ScreenSaverX11Private: DPMS Deactivated 1
Dec 26 12:03:06 bedroom mythfrontend.real: mythfrontend[27298]: I CoreContext screensaver-x11.cpp:161 (RestoreDPMS) ScreenSaverX11Private: DPMS Reactivated 1
Dec 26 12:03:18 bedroom mythfrontend.real: mythfrontend[27298]: I CoreContext screensaver-x11.cpp:149 (DisableDPMS) ScreenSaverX11Private: DPMS Deactivated 1
Dec 26 12:06:35 bedroom mythfrontend.real: mythfrontend[27298]: I CoreContext tv_play.cpp:414 (StartTV) TV: Exiting main playback loop.

```

Thank you,
James

---

### Post by crow-jamesm on 2014-12-26
Forgot to include my version of Mythfrontend.
```
james@bedroom:~$ dpkg -l | grep mythtv-frontend
ii  mythtv-frontend     2:0.27.4+fixes.20141212.40506c2-0ubuntu0mythbuntu2  amd64        Personal video recorder application (client)



```

---

