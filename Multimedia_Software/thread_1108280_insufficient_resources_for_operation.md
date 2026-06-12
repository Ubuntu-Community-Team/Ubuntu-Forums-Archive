---
title: "insufficient resources for operation"
date: 2009-03-27
forum: Multimedia Software
---

### Post by held7over on 2009-03-27
I am new to linux and ubuntu 8.10, but am coming from Mandriva 2008. I have two IBM 600x laptops which played my videos without complaint under Mandriva 2008 right out of the box, so, the problem I am having surely must have a simple fix in Ubuntu....but I don't have the familiarity with Ubuntu or the technical expertise. 

Admittedly, the IBM 600's are old machines with only 288 MB of Ram, but they seem to do quite well with Linux.

My video's are loaded on my Hard drive. I have not tried to play them from DVD. Some of my videos play fine under Ubuntu. Some don't. Size doesn't seem to be the issue at all, as whole movies will play. 

If I start mplayer on the commandline, I get this following error:

X11 error: BadAlloc (insufficient resources for operation)0.2% 125 0

It says,

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



After reading the sticky at the front of this part of the forum, I downloaded alsa-oss, hoping to comply with the above suggestion to use the OSS emulation of alsa, but I have no idea where to go to enable it. I would greatly appreciate it if someone could help me solve this problem. Thanks.

P.S. Ubuntu looks pretty cool from what I have seen of it so far...

---

### Post by fifth on 2009-03-28
I get the insufficient resource problem with all video mplayers under kde4. When i switch to another de everything works normally.

I'm assuming this is a graphics issue as kde4 is running with composite enabled. Going to test it by disabling plasma and see what happens.

UPDATE: Disabling effects in KDE4 got video working again.

---

