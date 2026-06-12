---
title: "Radeon compatibility with old CRT Monitor problem."
date: 2009-05-12
forum: Multimedia Software
---

### Post by TheNTW on 2009-05-12
Here is the thing.
I installed Ubuntu Jaunty on my firends PC. 
He has Radeon HD2600 video card and an really (x2) old Philips CRT Monitor. This combination seems to be impossible, cause the image is flowing away (kind of spinning around), this occurred when we installed Windows (before installing ubuntu ), but I fixed the problem by setting the refresh rate to 60Mhz (from 80mhz...). 
As far as I understand the problem should be in refresh rate, but I don't see how that is possible, cause refresh rate is already set to 60 MHz.

This is very confusing to me. 
I tried re-installing, configuring xorg manually, and installing ATI Drivers. I succeeded installing, but it did not change a thing.

A really weird thing, is **when loading ubuntu via LiveCD** (before installing) - **it works** *(screen is displayed normally)*, when Ubuntu is installed and rebooted - does not work anymore.

I would really appreciate any suggestions.

---

### Post by TheNTW on 2009-05-14
[I][FONT="Courier New"][COLOR="DimGray"]* bump *
Still need a solution[/COLOR][/FONT][/I]

---

### Post by draynes on 2009-05-14
Many OLD monitors are only capable of 800x600 resolution max, and some really old ones are only capable of 640x480.  Some are only capable of 1024x768 max, etc, etc.

A Linux install on a box hooked to a recent monitor will most likely default to a pretty high screen resolution.  If you then hook that box up to an old, very limited monitor you will fry the monitor unless it's turned off pretty quickly.  The old monitors cannot handle video output that exceeds their horizontal and vertical sync rates, and screen resolution.

Ask me how I know - I have a motley collection of old and older monitors.  Some are 640x480 only, some are 800x600 max, some are 1024x768 max, and only a few are multi-sync and usable above 1024x768.

---

### Post by TheNTW on 2009-05-23
On windows it worked with 1024x768, didn't try anything bigger on Linux. 
And how about the paradox, that on Linux Live CD Everything is perfect, but in installed Ubuntu -> goodbye Kansas ?

---

