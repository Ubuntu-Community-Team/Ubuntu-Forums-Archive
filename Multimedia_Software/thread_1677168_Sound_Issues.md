---
title: "Sound Issues"
date: 2011-01-28
forum: Multimedia Software
---

### Post by webron on 2011-01-28
Hi everyone,
I'm trying to solve some sound issues I'm having in Ubuntu. I've searched and read numerous threads and tried to get help from different sources on IRC, but I'm afraid I can't get it to work quite the way I want to.

I've recently switched from Windows 7 to Ubuntu 10.10 on my mediacenter pc. The pc is connected to a Pioneer receiver via HDMI which is connected to my TV also via HDMI.
The PC is an atom-based machine running on a ZOTAC NVidia Ion board. Before I go on, allow me to say that in Windows I had absolutely no sound problems whatsoever (just to clarify that this is not some hardware configuration problem).

Currently I use VLC to watch videos, but I'd like to switch to XBMC for that.

In attempts to solve this issue, I followed some instuctions from:
[https://answers.launchpad.net/ubuntu/+source/vlc/+question/125187](https://answers.launchpad.net/ubuntu/+source/vlc/+question/125187)

Unfortunately, now I can get sound from Youtube (for example) in my browser, but I get the following error message from VLC (only stereo output):
Potential ALSA version problem:
VLC failed to initialize your sound output device (if any).
Please update alsa-lib to version 1.0.23-2-g8d80d5f or higher to try to fix this issue.

Before this change, I managed to get passthrough output in VLC.

With these settings, I can't get passthrough sounds in XBMC. If I switch PA to use a different output hardware (such as the analog stereo), I can get the sound in XBMC working, but all other sound on the machine is gone.

My receiver is fairly new and can do pretty much all the decoding I need, so I just want to set it to passthrough hdmi and get the sound working.

Is there any way to solve this issue?
Please take into account that I'm fairly a novice when it comes to Linux and very much a newbie when it comes to Ubuntu, so if you'd like me to check on something, please tell me the full commands you want me to run.

Thanks!

---

### Post by lidex on 2011-01-29
These may point the way:
[http://ubuntuforums.org/showthread.php?t=1552250](http://ubuntuforums.org/showthread.php?t=1552250)
[https://help.ubuntu.com/community/SoundTroubleshootingProcedure#Step%2017](https://help.ubuntu.com/community/SoundTroubleshootingProcedure#Step%2017)

---

