---
title: "Two audio inputs simultaneously  -- gnome alsamixer"
date: 2017-02-01
forum: Multimedia Software
---

### Post by cigtoxdoc on 2017-02-01
On one of my PCs that is dual-boot Ubuntu 16.04 and Win 10 64 Pro, I can do something on the Win side w/o any modifications that it appears I cannot do (at least easily) with Ubuntu.  I have the headset output from a Radio Shack Pro-2037 scanner going to the audio input on the back of the PC.  I also listen to streaming audio streams (for example, [www.wqxr.org](www.wqxr.org)) using the website or going through WinAmp (like VLC player).  In the Win Volume Mixer, the scanner output shows as "Line in (High Definition Audio...", and there are other volume controls in the mixer for WinAmp, Firefox, and Plugin Container for Firefox, System Sounds, and Speakers.  So the question is

How do I do the same thing in Ubuntu 16.04?  One approach that seems to work is gnome-alsa mixer.  Seems that available documentation appears to be old and explanations of the abbreviations at the top of each slider assumes you know what you are doing.  Is there anything better?

Here are my slider settings beyond Master: Headphon Mute, PCM slider at top, Front and Front MI Mute, Surround slider at top, Center Mute, LFE Mute, Line (this is output form Radio Shack scanner) about 60% up, Line Boo (Boost?) slider at bottom, both Capture sliders at top, and both Rear Mic sliders are at the bottom and Mute box is ticked.  Also, please note that some of the slider settings will cause all sounds to be muted and you need to go to Sounds under System Settings to unmute them.

There are five tick boxes under the sliders labeled Auto-Mute Mode, Channel Mode, Input Source, Input Source, and Loopback Mixing.  I don't know what these do, so I left them unticked.

John

---

