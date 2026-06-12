---
title: "lavcopts error"
date: 2007-11-15
forum: Multimedia Production
---

### Post by qjuanjo on 2007-11-15
why

 mencoder -oac lavc -ovc lavc -subcp latin1 -of mpeg -mpegopts format=dvd -vf scale=352:288,harddup -srate 48000 -af lavcresample=48000 -lavcopts threads=2:vcodec=mpeg2video:vrc_buf_size=1835:vrc_maxrate=9800:vbitrate= 850:keyint=15:acodec=ac3:abitrate=224:aspect=16/9 -ofps 30000/1001 -sub rbt.srt -subfont-text-scale 4 -subpos 99 -o salida.mpg smallville.s07e02.hdtv.xvid-2hd.avi 
MEncoder 2:1.0~rc1-0ubuntu13 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ (Family: 15, Model: 43, Stepping: 1)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Error parsing option on the command line: -lavcopts

Exiting... (error parsing command line)



Thanks

---

### Post by sonofusion82 on 2007-11-29
> **qjuanjo said:**
> why

 mencoder -oac lavc -ovc lavc -subcp latin1 -of mpeg -mpegopts format=dvd -vf scale=352:288,harddup -srate 48000 -af lavcresample=48000 -lavcopts threads=2:vcodec=mpeg2video:vrc_buf_size=1835:[COLOR="blue"]vrc_ maxrate=9800[/COLOR]:[COLOR="Blue"]vbitrate= 850[/COLOR]:keyint=15:acodec=ac3:abitrate=224:aspect=16/9 -ofps 30000/1001 -sub rbt.srt -subfont-text-scale 4 -subpos 99 -o salida.mpg smallville.s07e02.hdtv.xvid-2hd.avi 
MEncoder 2:1.0~rc1-0ubuntu13 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ (Family: 15, Model: 43, Stepping: 1)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Error parsing option on the command line: -lavcopts

Exiting... (error parsing command line)



Thanks
there are a couple of extra spaces.
try

mencoder -oac lavc -ovc lavc -subcp latin1 -of mpeg -mpegopts format=dvd -vf scale=352:288,harddup -srate 48000 -af lavcresample=48000 -lavcopts threads=2:vcodec=mpeg2video:vrc_buf_size=1835:vrc_maxrate=9800:vbitrate=850:keyint=15:acodec=ac3:abitrate=224:aspect=16/9 -ofps 30000/1001 -sub rbt.srt -subfont-text-scale 4 -subpos 99 -o outfile.mpg infile.avi

---

