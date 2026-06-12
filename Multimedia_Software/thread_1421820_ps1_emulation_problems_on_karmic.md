---
title: "ps1 emulation problems on karmic"
date: 2010-03-04
forum: Multimedia Software
---

### Post by evo9 on 2010-03-04
I absolutely can not get pSX to work on karmic.

I've spent the past two hours reading through tutorials on this site and many others.

I can find a lot of solutions on earlier ubuntu releases but nothing has worked so far on 9.10

With pSX im using bios scph1001.bin and I'm getting this error in terminal when I try to run it:

[src/linux/sound.cpp, line 215]: 'snd_pcm_hw_params_set_access(pcm_handle,hwparams,SND_PCM_ACCESS_MMAP_INTERLEAVED)' returned 'Invalid argument'
pad=0
Segmentation fault


Any ideas?

p.s. This thread [http://ubuntuforums.org/showthread.php?t=394097](http://ubuntuforums.org/showthread.php?t=394097) seems to be the default answer to my question when asked by others but its done nothing for me.

---

### Post by dfreer on 2010-03-04
In response to your PM:
Unfortunately I haven't ran Ubuntu for over a year or so, and it seems ever since the inclusion of pulseaudio pSX has been unable to run. Let me cover some of the issues I've seen:

The original problem was that on 64-bit systems, a 32-bit library called libgtkglext was not available in the repositories, and since pSX is a 32-bit only program it could not run without it. I repackaged the 32-bit library for 64-bit systems and that was that.

Your particular problem came into affect sometime in the late 2008 release IIRC, when they decided to add pulseaudio. As far as I can tell from reports from other users is that the two conflict with each other, and so pulseaudio must be killed competely before pSX will function.

A third problem that sometimes coexists with the pulseaudio bug is that pSX doesn't always seem to detect the sound card correctly. Some say that running pSX as root works, and you can manually set the sound card from there or just continue running pSX as a root user (not recommended in general).

Let me do some research and see if I can come up with a 100% reliable method.

---

