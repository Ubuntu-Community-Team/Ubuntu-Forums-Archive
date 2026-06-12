---
title: "Tiny lags/freezes on video playback on 13.04"
date: 2013-05-18
forum: Multimedia Software
---

### Post by hunterkil on 2013-05-18
Hi

After installing Ubuntu 13.04 (Or actually Ubuntu-Gnome) - i'm experiencing tiny tiny lags on video playback - the picture stands still in mayby 0.2 of i a second mayby every 10th second, and it gets a bit naggy. -It's just about long enough to notice

I'm experiencing this both with normal playback with totem, html5/flash playback on youtube/other video sites in firefox/chrome - it's pretty much the same.

This is not a behavior i have experienced with prior versions.

Hardware: 
Core2Duo E6420
Nvidia GTX 550ti (using proprietary driver nvidia-313)
4gb memory
Samsung 830 120gb SSD

Anyone experiencing similar behavior and/or have a solution? i'm freaking out

---

### Post by Tropcon on 2013-06-10
Hello, there!

I'll spare you the story of how I figured this out, but I was having the same problem and just managed to fix it.

**The Setup:**
I have have an NVIDIA MCP55 on an Asus M2N32-SLI Deluxe motherboard. It's the best sounding onboard card I've ever heard, but it gives me the same problems you were describing.

**The Problem:**
Video, audio, anything I play that has sound will randomly skip and stutter for a fraction of a second every 10 seconds or so. Sounds like a buffer overflowing.

**The Solution:**
Pop open a terminal and type:
```
gksu gedit /etc/pulse/default.pa
```
Type password when prompted.

Under the section > ### Automatically load driver modules depending on the hardware available
Find the line that reads:
> load-module module-udev-detect use_ucm=0
Add **tsched=0** to this line to make it read:
> load-module module-udev-detect tsched=0 use_ucm=0
Save and exit the file.

Now restart pulseaudio by typing into your terminal:
```
pactl exit
```

Pulseaudio will automatically restart and your audio should now be smooth. No restart required.
To reverse this fix, simply remove "tsched=0" from the "/etc/pulse/default.pa" file are restart pulse again.

**The Details:**
The problem is caused by a bad reaction to the timer-based scheduling introduced in newer versions of Pulseaudio. Adding "tsched=0" to the "/etc/pulse/default.pa" file, as described above, disables timer-based scheduling, causing pulseaudio to fall back to the traditional interrupt-driven method.

**Sources:**
[https://wiki.archlinux.org/index.php/PulseAudio#Glitches.2C_skips_or_crackling]("https://wiki.archlinux.org/index.php/PulseAudio#Glitches.2C_skips_or_crackling")

---

### Post by alkh3myst on 2013-06-29
Thanks Tropcon. Your fix is similar to the one on the Ubuntu wiki page: "Position Reporting" [https://wiki.ubuntu.com/Audio/PositionReporting](https://wiki.ubuntu.com/Audio/PositionReporting). Unfortunately, this fix makes the problem worse on my computer, turning this Launchpad-certified audio bug ('crackling'/stuttering: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1174696](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1174696)) into a full-fledged digital audio stutter, like what you get from a dirty CD player. The other two "fixes" on that wiki page make no difference. This is a widespread problem that seems to affect a number of different users. It seems that very little of any significance is being done to fix this, other than noting that there's a bug/problem. I'm going to keep looking through the bug reports, nothing else is showing ***any*** progress. #-o

---

