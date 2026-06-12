---
title: "pchdtv 5500 problems"
date: 2006-09-02
forum: Multimedia &amp; Video
---

### Post by hedcold on 2006-09-02
i posted this on the pchdtv forums, but there was no help, so maybe someone here can

i use a cable line straight into my pchdtv card, and i've been trying to play it with mplayer
for 3 of the local hd channels, it plays fine, a little choppy but i never lose sound or have mplayer crash.
with 2 other hd channels, i get an error like this

************************************************
**** Your system is too SLOW to play this! ****
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

A:10745.6 V:10741.5 A-V: 4.121 ct: -0.794 1189/1189 30% 4% 57.0% 114 0
Too many video packets in the buffer: (140 in 8513255 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
a52: CRC check failed!
a52: error at resampling

Too many video packets in the buffer: (140 in 8513255 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

and i lose sound. i know my system isn't to slow, but i'm also pretty sure i don't have XVMC set up.

for the 2 channels that cause this error, when i use -ao sdl it helps a little at first, but i still eventually lose sound.
i have a nvidia video card (6800), nvidia motherboard with sound, and amd64 4400, but using the 386 k7 smp kernel. 

i have the nvidia driver setup, but i check the usr/X11R6/lib/nvidia folder and its empty, and from what i've been reading it shouldn't be

what do i have to do to enable it? and is that why i'm losing sound, or is that a seperate sound driver issue?

thanks

---

### Post by tseliot on 2006-09-03
> **hedcold said:**
> i have the nvidia driver setup, but i check the usr/X11R6/lib/nvidia folder and its empty, and from what i've been reading it shouldn't be
The fact that that folder is empty does not imply that your driver is not working.

Post the ouput of the following commands:
```
dmesg | grep NVIDIA
```

```
glxinfo | grep direct
```


P.S. I can't help you with the other problems.

---

### Post by hedcold on 2006-09-04
> **tseliot said:**
> The fact that that folder is empty does not imply that your driver is not working.

Post the ouput of the following commands:
```
dmesg | grep NVIDIA
```

```
glxinfo | grep direct
```


P.S. I can't help you with the other problems.

dmesg | grep NVIDIA
[17179569.184000] ACPI: DSDT (v001 NVIDIA AWRDACPI 0x00001000 MSFT 0x0100000e) @ 0x00000000
[17179585.724000] nvidia: module license 'NVIDIA' taints kernel.
[17179586.220000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8762  Mon May 15 13:06:38 PDT 2006

glxinfo | grep direct
direct rendering: No

---

### Post by tseliot on 2006-09-05
The driver does work but not at its full (direct rendering is disabled).

Try asking here:
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

---

### Post by Kadin2048 on 2006-09-29
> **tseliot said:**
> The driver does work but not at its full (direct rendering is disabled).

Try asking here:
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

tseliot, can you elaborate a little more on what you mean? Is it the Nvidia graphics card driver that's the issue, or is it the HD-5500's driver that's not working?

I ask because I'm thinking of getting a HD-5500 and I'm also using the NVIDIA 1.0-8762 driver, with a Quadro4 200/400 NVS card. (It seems to work perfectly in all other respects, though.)

---

