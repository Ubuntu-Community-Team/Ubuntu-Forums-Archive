---
title: "Choppy 1080p playback"
date: 2010-04-22
forum: Multimedia Software
---

### Post by MrNatewood on 2010-04-22
These the specs of my laptop:
4GB DDR2
Core Duo P8700
Radeon HD 4570 512MB
(using Ubuntu Karmic 64-bit)

Tried playing 1080p h.264 video with VLC, GNOME MPlayer and totem, and it's choppy.

I searched here and found some guides but they all seem to be assuming an nvidia card is used.

Any ideas on how to improve playback?

---

### Post by hxcobd on 2010-04-22
Try the CPU scaling tips in the tutorial in my signature and post the results.

---

### Post by akand074 on 2010-04-22
Are you using the open-source or the proprietary drivers for your graphics card? I don't know very much about it but I've read around on issues with ATI drivers and Ubuntu though I thought most of them are fixed/no longer critical because it seems your specs are more than good enough to play a 1080p movie. What is the resolution on your screen? I've noticed playing 1080p movies on monitors with much smaller resolutions can be a pain. On my laptop the resolution is only 1280 by 720 (720p) so playing a 1080p video on it would be downscaling it showing a compressed image of a high resolution file which takes huge processing power. Hense, on my crap AMD Turion don't even think about it.

---

### Post by MrNatewood on 2010-04-23
Changing the scaling to "Performance" doesn't help. Exact same choppiness.
I am using the proprietary driver.
My laptop screen is 1920x1080.

---

### Post by gradinaruvasile on 2010-04-23
Use smplayer with mplayer-mt (thats mplayer's multi-threaded version) - select avivo in the display device field. Its probably best combination for your situation.

Also make sure you have the latest codecs - install w32codecs (i dont know if the 32 refers to the 32-bit version) etc from medibuntu. Codecs make a huge difference in HD playback.

I saw a test on a core2duo laptop with Ati HD3650/Ubuntu 9.10 and vlc played 1080p perfectly (ok, it got to about 90-95% CPU spikes but there were no skipped frames and the sound was sync'd).
And mplayer-mt is better because it uses multiple threads. Only you must find it for Ubuntu.

I use Debian and mplayer-mt is in the multimedia repos - it works well, i saw even 130% CPU spikes (core2duo/xv output on nvidia), but the playback is very smooth.
I use only 32-bit systems though (everything is working perfectly, no workarounds needed). There might be 64-bit related issues for you to solve.

---

### Post by MrNatewood on 2010-04-23
Installed mplayer-mt from a PPA. seems to be working much better. But I can't get GNOME-MPlayer to use it. I set it as the mplayer executable in the preferences but it's still choppy in GNOME-MPlayer.

Any ideas on how to get a GUI to use mplayer-mt?

---

### Post by cchhrriiss121212 on 2010-04-23
> Any ideas on how to get a GUI to use mplayer-mt?
Smpalyer is the best front end for mplayer.

---

### Post by MrNatewood on 2010-04-23
> **cchhrriiss121212 said:**
> Smpalyer is the best front end for mplayer.

Tried to set mplayer-mt as the executable in SMPlayer but still the choppiness is the same as with standard mplayer.

Only way I got smooth-ish playback is by playing directly with mplayer-mt and no GUI.

How can I get a GUI to get to the same performance?

---

### Post by rvm4000 on 2010-04-23
In smplayer you need to change the "mplayer executable" in preferences -> general, change mplayer to mplayer-mt.

Then you need to change the "threads for decoding" in preferences -> performance.

---

### Post by akand074 on 2010-04-23
Follow this: 
[URL="http://ubuntuforums.org/showthread.php?t=1305181"]
[/URL][http://ubuntuforums.org/showthread.php?t=1305181](http://ubuntuforums.org/showthread.php?t=1305181)

and everything should run perfectly, atleast it did for me.

---

