---
title: "Fastforwarding with no sound"
date: 2011-07-07
forum: Multimedia Software
---

### Post by sirishy2k on 2011-07-07
I don't understand what happened today but all the media players in Ubuntu are playing videos in fast forward mode with no sound. I don't understand what is the problem.I tried restarting even that did not work.
The system sounds are working fine. I am using Ubuntu 11.04

---

### Post by sirishy2k on 2011-07-07
I removed the pulse audio package and all the dependencies and installed libsdl1.2debian-all and then installed vlc now I am able to play the youtube videos perfectly. But unable to play any files offline on my computer and I got a error while play a mp4 in my mplayer . 

```
 
           ************************************************
           **** Your system is too SLOW to play this!  ****
           ************************************************

Possible reasons, problems, workarounds:
- Most common: broken/buggy _audio_ driver
  - Try -ao sdl or use the OSS emulation of ALSA.
  - Experiment with different values for -autosync, 30 is a good start.
- Slow video output
  - Try a different -vo driver (-vo help for a list) or try -framedrop!
- Slow CPU
  - Don't try to play a big DVD/DivX on a slow CPU! Try some of the lavdopts,
    e.g. -vfm ffmpeg -lavdopts lowres=1:fast:skiploopfilter=all.
- Broken file
  - Try various combinations of -nobps -ni -forceidx -mc 0.
- Slow media (NFS/SMB mounts, DVD, VCD etc)
  - Try -cache 8192.
- Are you using -cache to play a non-interleaved AVI file?
  - Try -nocache.
Read DOCS/HTML/en/video.html for tuning/speedup tips.
If none of this helps you, read DOCS/HTML/en/bugreports.html.

```

Please let me know if you need any logs files which will help detect the problem.

--Thank you

---

