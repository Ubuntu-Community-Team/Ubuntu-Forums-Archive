---
title: "Converting RMVB To AVI Using Mencoder"
date: 2009-04-01
forum: Multimedia Software
---

### Post by unplugged23 on 2009-04-01
Hey there,

I was just having some problems with mencoder, mainly due yo my lack of experience, and was hoping someone could help. I was following this format ```
mencoder in.rmvb -oac mp3lame -lameopts preset=128 -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=1200 -ofps 25 -of avi -o out.avi
``` from [http://www.fedoraforum.org/forum/showthread.php?t=104161]("http://www.fedoraforum.org/forum/showthread.php?t=104161") I just copied and pasted that into terminal not knowing what else to do (I have mplayer mencoder, and am pretty sure i have all of the needed codecs) and got ```
MEncoder 2:1.0~rc2-0ubuntu17 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 2.80GHz (Family: 15, Model: 2, Stepping: 9)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
File not found: 'in.rmvb'
Failed to open in.rmvb.
Cannot open file/device.

``` as an output. I dont know what to do, can someone please help?

---

### Post by andrew.46 on 2009-04-01
Hi,

I suspect you do not have the right path for your input file:

```
mencoder in.rmvb
```

Make sure you open your terminal window in the right directory, or navigate to the file. You may find as well that these files are not the easiest to convert.

All the best,

Andrew

---

### Post by andrew.46 on 2009-04-02
Hi again,

I felt a little guilty about dismissing my old friend MEncoder quite so quickly on so many occasions lately so I have done a little work on converting rmvb to avi using MEncoder,

A couple of points to start with:

[LIST=1]
[*]MEncoder's basic container format is avi. It can encode to other containers but avi will always be the safest.
[*]To get the best results you really need [the latest svn MPlayer]("http://ubuntuforums.org/showthread.php?t=1024592").
[*]Work on MEncoder has stalled a little and often better and easier solutions can be found by using FFmpeg.
[/LIST]

I used a sample file from the MPlayer 'samples' site so if anybody wishes to improve on my syntax feel free.

```
wget http://samples.mplayerhq.hu/real/AC-cook/cook_5.1/samplerv.rmvb
```

I have modified unplugged23's syntax a little and extended it somewhat:

```

mencoder samplerv.rmvb \
    -oac mp3lame -lameopts preset=standard \
    -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=1200:mbd=2:trell:v4mv \
    -ffourcc XVID  -mc 0 -noskip -o out.avi

```

which is as fancy as you would really want to get with this little clip :-). So for those new to MEncoder:

[LIST=1]
[*]**mencoder samplerv.rmvb** : This is the name of the input file
[*]**-oac mp3lame** : Audio output will be encoded by lame.
[*]**-lameopts preset=standard** : Options passed to the lame encoder. This encodes to between 128k. and 192k.
[*]**-ovc lavc** : Video output will be encoded by the static libavcodec libraries imported from FFmpeg. 
[*]**-lavcopts** : These are the options passed to libavcodec
[*]**vcodec=mpeg4:vbitrate=1200** : Encode to mpeg4 with a bitrate of 1200k
[*]**mbd=2:trell:v4mv** : Standard encoding options for mpeg4. Makes the encoding a little slower, a little bigger but much better quality.
[*]**-ffourcc XVID** : By default this file will announce itself as FMP4, this changes it to XVID and avoids confusing some devices.
[*]**-mc 0 -noskip** : Guards against A/V sync issues, strange framedrops etc.
[*]**-o out.avi** : Sadly avi is the native format for MEncoder. '-of avi' is not necessary as MEncoder picks this 1. by default 2. by file suffix.
[/LIST]

Well that is about it, certainly makes a reasonable transcode from the original rmvb file. Can anybody suggest better syntax using MEncoder?

All the best,

Andrew

---

