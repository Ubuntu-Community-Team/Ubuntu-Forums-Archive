---
title: "while switching user (to another X or VT) all glx apps get suspended/freeze"
date: 2011-09-22
forum: Multimedia Software
---

### Post by der_hede on 2011-09-22
Hi,

I'm using Ubuntu Natty with a radeon HD5770. Everything is fine, except if I switch to some virtual Terminal (F1-F6) every glx/3d Application gets stalled/paused/freezes while in background.

Sometimes I play games and I want to have some Instant Messenger or Voice Chat in the Background. So I have to switch between different X Servers, because with Linux there's no way to minimize games like with windows and [alt]-[tab] or [ctrl]-[esc] or some Windows Key.

The non-glx/3d Voice System works fine after switching to system-wide pulseaudio. (Yes, I know, pulseaudio renders useless the time they omit system wide mode because then it will be impossible to have different users have sound at the same time. I will omit pulseaudio then.)

The Problem is: While this works with two other Systems (Ubuntu 10.04 with radeon non-kms and Ubuntu 11.04 with NVidia proprietary) here at this PC all glx/3d applications, even glxgears, get suspended while in Backgound. They get paused, freezed, whatever. Fact is, this way the in-game online connection get lost. Server disconnects because of network errors, clearly because the game stops receiving and sending packets.

For example, maybe others can confirm or falsify: If I start glxgears and then switch to some VT (i.e. press [ctrl]-[alt]-[F2]) and wait some time and then switch back to Xorg, the output of glxgears is as follows: 

```

der_hede@computer:~$ glxgears 
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
405 frames in 5.0 seconds = 80.954 FPS
398 frames in 5.0 seconds = 79.557 FPS
150 frames in 37.6 seconds =  3.989 FPS
405 frames in 5.0 seconds = 80.888 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 4652 requests (4652 known processed) with 0 events remaining.
der_hede@computer:~$ 
```

Here after ~12 seconds and 953 rendered Frames (405+398+150) I switched to the VT, then the next 35 seconds glxgears rendered _nothing_ and even the timer event (every 5 seconds) is stopped! Then I switched back and glxgears continues to render opengl content.

Is this a normal behaviour?

System Information: 
AMD 880G chipset with AMD Phenom CPU
AMD Radeon HD 5770 Graphics Card
Ubuntu 11.04 "natty" AMD64, Ubuntu repositories only (no PPA etc.)
linux-image-2.6.38-11-generic 2.6.38-11.48
xserver-xorg-video-radeon 1:6.14.0-0ubuntu4.1

---

