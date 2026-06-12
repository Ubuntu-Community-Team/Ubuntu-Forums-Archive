---
title: "[SOLVED] Smplayer + mplayer SVN problem"
date: 2008-04-01
forum: Multimedia &amp; Video
---

### Post by chronosoft on 2008-04-01
Hi there, i recently upgraded mplayer to the latest SVN and i noticed it seems to have broken something in Smplayer...

*please note...An error that appears in mplayer after i finish/stop playing a video 'gnome_screensaver_control()'

When i try to open a video with Smplayer i get this error

/usr/local/bin/mplayer -noquiet -nofs -sub-fuzziness 1 -identify -msglevel demux=6 -slave -vo v4l2 -ao pulse -zoom -nokeepaspect -framedrop -input conf=/usr/local/share/smplayer/input.conf -stop-xscreensaver -wid 58720270 -monitorpixelaspect 1 -subfont-autoscale 1 -subfont-text-scale 5 -subcp ISO-8859-1 -subpos 100 -contrast 0 -brightness 0 -hue 0 -saturation 0 -nocache -osdlevel 0 -vf-add screenshot -channels 2 -af scaletempo /media/sda2/Anime/[Ayako]_Minami-ke_-_01_H264_[EA5EB9DE].mkv

MPlayer dev-SVN-r26303-4.1.3 (C) 2000-2008 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 3600+ (Family: 15, Model: 107, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 3DNow 3DNowEx SSE SSE2
Unknown option on the command line: -stop-xscreensaver
Error parsing option on the command line: -stop-xscreensaver

I enjoy using Smplayer very much... :) any help is much appreciated thanks ;)

---

### Post by rvm4000 on 2008-04-01
For some reason your mplayer was compiled without support for the option -stop-xscreensaver (probably a devel library missing). 

If you can't fix the problem in mplayer you can make a small change in the sources of smplayer, edit core.cpp and comment or delete these lines:
```

	if (pref->disable_screensaver) {
		proc->addArgument("-stop-xscreensaver");
	} else {
		proc->addArgument("-nostop-xscreensaver");

```

---

### Post by chronosoft on 2008-04-01
Thanks for the reply rvm4000, i've done what you said... i edited core.cpp (it was in the /src directory) and commented out

> if (pref->disable_screensaver) {
		proc->addArgument("-stop-xscreensaver");
	} else {
		proc->addArgument("-nostop-xscreensaver");

and then compiled + make installed it.I still get this message...

/usr/local/bin/mplayer -noquiet -nofs -sub-fuzziness 1 -identify -msglevel demux=6 -slave -vo v4l2 -ao pulse -zoom -nokeepaspect -framedrop -input conf=/usr/local/share/smplayer/input.conf -stop-xscreensaver -wid 27262990 -monitorpixelaspect 1 -subfont-autoscale 1 -subfont-text-scale 5 -subcp ISO-8859-1 -subpos 100 -contrast 0 -brightness 0 -hue 0 -saturation 0 -nocache -osdlevel 0 -vf-add screenshot -channels 2 -af scaletempo /media/sda2/Anime/[Ayako]_Minami-ke_-_01_H264_[EA5EB9DE].mkv

MPlayer dev-SVN-r26303-4.1.3 (C) 2000-2008 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 3600+ (Family: 15, Model: 107, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 3DNow 3DNowEx SSE SSE2
Unknown option on the command line: -stop-xscreensaver
Error parsing option on the command line: -stop-xscreensaver

How would one go about compiling mplayer with "stop-xscreensaver"?

---

### Post by chronosoft on 2008-04-01
Ah, >.< i've solved the problem... It seems the build of Mplayer SVN was at fault... i had make clean 'd it and svn update mplayer to the latest revision + compile + install. ^_^ it's fixed now thanks for the help anyway ;)

---

