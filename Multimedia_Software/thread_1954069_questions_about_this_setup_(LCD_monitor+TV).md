---
title: "questions about this setup (LCD monitor+TV)"
date: 2012-04-07
forum: Multimedia Software
---

### Post by ppjose on 2012-04-07
Hi!, (sorry for my english)

I want to buy a 40 inch LED TV and I have some questions to use with my current pc with ubuntu.

My graphics card is a Nvidia GeForce GTX 560 Ti (2xDVI + HDMI mini output) and my current monitor is a LCD DELL 2007WFP.

Well, my idea is to use the TV as a second monitor connected by HDMI to the PC graphics card (as extended desktop). 

That is, the DELL as primary monitor by DVI and the TV by HDMI set both its native resolution, TV at 1080p 16:9, and monitor at 1680x1050 16:10.

My idea is open a VLC and make it full screen (or run XBCM) on the TV via the HDMI **([B]is posible output also the audio by HDMI only on VLC/XBMC? although this is not 100% necessary it´s vey interesting**)[/B] while I browse the internet on the main monitor

**I wonder if anyone has a similar setup to know potential problems ... resolution, overscan problems ... etc**

**what features should look especially when I have to go buy the TV?**

thanks, greetings.

---

### Post by ppjose on 2012-04-15
up!! :(

---

### Post by BicyclerBoy on 2012-04-15
desktop:
Using nVidia proprietary driver (required for HDMI audio)..
I would recommend separate X screens & not twinview desktop setup.
This makes full screen apps work correctly/independently

effects:
You have a powerful GPU so should not have problems with effects redirection (composite compiz). But there are compiz settings to reduce the refresh/redraw timing damage (un-redirect full screen).
Composite effects cause VDPAU video overlay to use blitter redraw & this is not guaranteed to be tear free.

power consumption:
using 2 screens on nVidia GPU forces GPU to clock at maximum performance/power consumption. The GTX560 is greatly over powered for HTPC.
The GT240 is over powered for HTPC & GT430 is about right (debatable).

audio output:
XBMC & VLC can output directly to a specific audio device.

TV:
- make sure it has direct pixel mapping/direct-scan/just-scan settings.
- can play h264/AAC files direct from USB.
The rest is personal prefs.

---

### Post by ppjose on 2012-04-16
> **BicyclerBoy said:**
> desktop:
Using nVidia proprietary driver (required for HDMI audio)..
I would recommend separate X screens & not twinview desktop setup.
This makes full screen apps work correctly/independently

effects:
You have a powerful GPU so should not have problems with effects redirection (composite compiz). But there are compiz settings to reduce the refresh/redraw timing damage (un-redirect full screen).
Composite effects cause VDPAU video overlay to use blitter redraw & this is not guaranteed to be tear free.

power consumption:
using 2 screens on nVidia GPU forces GPU to clock at maximum performance/power consumption. The GTX560 is greatly over powered for HTPC.
The GT240 is over powered for HTPC & GT430 is about right (debatable).

audio output:
XBMC & VLC can output directly to a specific audio device.

TV:
- make sure it has direct pixel mapping/direct-scan/just-scan settings.
- can play h264/AAC files direct from USB.
The rest is personal prefs.

thank you very much for responding!

your answers are very helpful to me.

> **BicyclerBoy said:**
> desktop:
TV:
- can play h264/AAC files direct from USB.


now many tv have this feature but I'm going to use the PC to play the video and audio files.

Thanks once again, greetings ;)

---

