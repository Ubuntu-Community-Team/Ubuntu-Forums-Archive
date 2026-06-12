---
title: "VLC - Glitchy Video AND Audio"
date: 2008-08-13
forum: Multimedia Software
---

### Post by natrik on 2008-08-13
After having made a mess of things completely on this computer, I started over with the 8.04.1 ubuntu desktop install, keeping only my "/mymedia" partition.  I added KDE4, in case that matters, but the following takes place under gnome.

My problem here is with VLC, which was the one thing that worked just fine under my previous (otherwise really hosed) installation of xubuntu/kubuntu.   Now though, there are disruptive glitches in video and audio playback.  

**Video:  **playback hesitates, then catches up real quick like it's fast forwarding to catch up.  The "pause delay" ranges from barely perceptible to more than a full second.  Intervals between glitches range from 10sec to 5min.   

Also, the screen updates seem to be non-synchronous with the refresh rate, so that there are horizontal lines, especially when scenes pan left or right, or when someone walks by.  This is constant when it happens, but does not seem to happen with all files.

**Audio:  **Snap, Crackle, Pop! (tm)  ...  Intervals between glitches range from 5sec to about 2 minutes.  Just a single "click" every once in a while, or a very quick double click, or a very short silence followed by a click or series of clicks/pops.  Affects the tweeters mainly, but sometimes sets off the subwoofer in an uncanny way.

The audio / video glitches ALMOST NEVER happen at the same time, except near the beginning of a file (first few seconds).

I have tried changing all kinds of settings, like increasing the priority (in the VLC advanced preferences, the gnome system monitor, and manually with "renice" which requires root/sudo.)  Windowed and full screen behave the same, by the way.  I have tried all kinds of different video output methods: GL, XV, X11, all of those listed in the prefs.  I tried adjusting streaming settings, in case that would take effect somehow on a local file.  Tried alternate fullscreen.  Tried just about every combination of advanced gui (CTRL-G) settings, e.g. with/without audio equalizer, with/without video settings (hue, contrast, etc.)

The same files (just about any xvid / divx file I have tried) give me **flawless playback with mplayer, xine, and Miro** (formerly DemocracyTV)   But I really really like the interface of VLC, and want to keep it, if I can get it working properly.  I love the ease of use for example, of video settings and audio equalizer.

For now I'm using mplayer, and trying to figure out how to set the keymap the way I want it.  Once I get those settings down, I will be less attached to VLC, I suppose.

Thanks for any insight.   Oh, and I HAVE installed the nvidia-glx driver, the xserver-xorg-video-nv driver, all kinds of opengl stuff, and whatever else was autodetected for my GeForce4 MX 440.

-- Nate

---

### Post by 'gdanel on 2009-07-11
In case anyone is still reading this thread:

I had the same problem on an Ubuntu 8.10 running on an Intel dual-core @2GHZ. What was happening:

By default (my) Ubuntu runs the processors in "Ondemand" mode, so when the computer is idle the frequency is scaled down (to 1GHZ in my case). VLC is usually not computationally-intensive enough to kick the processor to full power, so when running VLC the processor will probably run scaled-down most of the time. However, when spikes occur in the music/video, Ubuntu will sometimes power up the processor to full frequency for a short time, which introduces glitches in the playback. 

How to fix it:
Set your frequency setting to "Performance" when using VLC. An easy way to do this is add a CPU Frequency Scaling Monitor applet to one of your panels, which will then allow you to choose the frequency settings you want for your processors. I guess you could even write a script to switch to full frequency whenever you start-up VLC.

It hope it helps. :)

'gdanel

---

