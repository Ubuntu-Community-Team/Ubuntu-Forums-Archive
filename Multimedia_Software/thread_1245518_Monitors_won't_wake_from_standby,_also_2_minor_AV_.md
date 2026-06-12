---
title: "Monitors won't wake from standby, also 2 minor A/V issues"
date: 2009-08-20
forum: Multimedia Software
---

### Post by Kinyoobi on 2009-08-20
Finally decided to kill off Windows and get my system running Ubuntu, and so far it's been great. I've run into a few problems that I haven't been able to fix via forum and Google hunting though.

First, specs:
Running Ubuntu Jaunty 9.04, amd64
Athlon64 X2 6000+ (3ghz), 6gb RAM
Radeon HD 4870 using FGLRX driver, dual monitor setup (main at 1680x1050/60, secondary at 1280x1024/60)
PPA 1431v sound, listed as ICEnsemble ICE1724 (will be using onboard sound for mic usage at some point, as the mic port never has worked well on the PPA card)

Issues:
1) When the monitors are placed into standby mode via power management settings (haven't tried system standby yet), they will not wake back up by any means. Ubuntu is responsive in the background, and I'm able to reboot safely via a key combo. A few threads I found said to change the screensaver, which didn't work in my case (along with an extra problem I discovered below), and everything else I found were Nvidia-specific fixes. I've had to disable display standby for now.

2) Screensavers don't seem to work properly. They display fine on the smaller second monitor (Ubuntu insists that it's my primary display, which I find that I prefer) but are glitchy and distorted on the larger monitor. The blank screensaver occasionally shows the desktop background (not the desktop itself) for about a second, alternating once between the monitors, but otherwise works fine.

3) Little issue. Sound for each program is defaulting to the the video card's unused HDMI port until I switch it via PulseAudio. I have the PPA card set as default via the Pulse applet and have been switching programs over as I find them, but I'd prefer a less hands-on solution.

I'm really not too worried about 2 and 3, though fixing those would be nice.

Thanks for any help. I'll check back in after work.

---

### Post by Kinyoobi on 2009-08-21
Bump.

---

