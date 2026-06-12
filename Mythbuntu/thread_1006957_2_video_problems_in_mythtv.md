---
title: "2 video problems in mythtv"
date: 2008-12-09
forum: Mythbuntu
---

### Post by mdwildcat04 on 2008-12-09
First, my system specs:

Amd Sempron 3200+ socket 393
1.5 gb DDR 400mhz ram
nVidia 6150se onboard graphics
200GB IDE maxtor for OS and recordings
500GB SATA Western Digital for videos
2x PVR-150
720p HDTV connected via DVI to HDMI cable

the first problem, I have stutters in the video.  on live TV, it will pause a few times at first, then will be fine from there on.  However, I have a few 720p videos that have an odd stutter.  the audio will continue as normal, however the video will at times slow down or stop, then speed up to catch up.  This will happen 3-10 times in a normal movie.  anything 480p and under is fine.

the 2nd problem is, when the system is idle, it will blank the screen, and eventually shut off the TV.  this is fine, except that when I move the mouse or press a key on the keyboard, video never comes back.  If I leave mythstream  playing, and press esc, the audio stops, but video never returns.  after a ctrl+alt+backspace, I get video back, but this shows up in my dmesg:
```
[38926.866990] mythfrontend.re[6131]: segfault at 91596ea ip 08b28ed0 sp b164e1cc error 6
[50613.505083] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.

```

---

### Post by ian dobson on 2008-12-09
Hi,

What video drivers are you using? Open source or Nvidia?

Try the Nvidia drivers they're usually better than the open source ones when it comes to hardware acceleration.

Also a Sempron 3200+ might be abit slow for HD playback. SD shuould be OK.

What you you see in your frontend log (/var/log/mythtv) when the video stutters.

Regards
Ian Dobson

---

### Post by mdwildcat04 on 2008-12-10
I am using the Nvidia drivers.

This apeared once in my log, 

```
Movie-Aspect is 1.86:1 - prescaling to correct movie aspect.
VO: [xv] 1280x688 => 1280x688 Planar YV12  [fs] [zoom]


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

---

