---
title: "nVidia's SLI + Dual Monitors of mixed resolutions"
date: 2012-09-18
forum: Multimedia Software
---

### Post by Everdras on 2012-09-18
My issue is that I have a 1920x1080 monitor (primary) and a 1280x1024 monitor (secondary). I have two nVidia GTS 450's in SLI. SLI works fine in Windows (it's an Alienware Aurora, so, worked out of the box...).

My issue is that I can't get Twinview and SLI working at the same time in linux. If I enable Twinview and SLI in xorg.conf, I have to enable Xinerama to get my desktop to display over both screens (a result of the mixed resolutions?). However, with Xinerama enabled, SLI seems to get cancelled and it only runs on one video card.

Running either monitor alone works just fine with SLI, but I can't go back to just one monitor.
So, right now I can either use only one monitor, or use only one video card.

Does anyone have any solutions or solutions to similar problems?
I've tried using both the nvidia configuration GUI and the CLI tool to generate xorg.confs, but I just get similar results to above.



Specifically, here are the xorg.conf's I tried:

This xorg.conf gives me dual-monitor support but with no SLI: [http://pastebin.com/64LNGUNt](http://pastebin.com/64LNGUNt)

This xorg gives me SLI but only supports one monitor: [http://pastebin.com/KAqGYQgf](http://pastebin.com/KAqGYQgf)

So, I took those two and tried to splice them together: [http://pastebin.com/FuWx6DP5](http://pastebin.com/FuWx6DP5)

When this loads, it seems to basically ignore the SLI options and behaves like the first config.

So, I made a few more tweaks... [http://pastebin.com/rTBXJWW2](http://pastebin.com/rTBXJWW2)
This causes X to crash repeatedly until it gets throttled because it respawns too fast. No terminal output.

So, finally, after much tinkering... [http://pastebin.com/HcVCZdB8](http://pastebin.com/HcVCZdB8)
This seems to be close to what I want. Both monitors are enables in nvidia-settings, SLI is on and the master graphics card reports that it's driving displays on both monitors.

However, my left monitor is blank and the power light is orange (sleep/power-save mode) and nothing seems to wake it.

Can anyone spot anything with my configs that may be awry, or recommend some solutions?

EDIT: Oh, and for the record, I'm running 64-bit Arch Linux. However, this issue should be pretty distro-agnostic.

---

