---
title: "Convert Blu-Ray to DVD"
date: 2010-03-26
forum: Multimedia Software
---

### Post by pssturges on 2010-03-26
Hi,

I'm trying to make a copy of my Blu-Ray movies on DVD-R so I can play them on my DVD player. The movies have been ripped to my HDD and the HD audio extracted. So I'm left with one video stream and one audio stream (either DTS or AC3) in a single m2ts file.

I've tried to use mencoder with the same command that I use to convert DVB HD broadcasts to DVD compliant mpeg files as so:

```

mencoder -oac copy -ovc lavc -of mpeg -mpegopts format=dvd:tsaf -vf scale=720:576,harddup -lavcopts vcodec=mpeg2video:vrc_buf_size=1835:vrc_maxrate=9800:vbitrate=4500:keyint=15:vstrict=0:aspect=16/9 -ofps 25 -o newfile.mpg 00520.m2ts
```

This seems to start OK but after a few seconds it seems to just hang at "Writing header..."

```

MEncoder SVN-r28754-4.3.3 (C) 2000-2009 MPlayer Team
success: format: 0  data: 0x0 - 0xacf25000
TS file format detected.
VIDEO H264(pid=4113) AUDIO DTS(pid=4352) NO SUBS (yet)!  PROGRAM N. 1
FPS seems to be: 23.976025
[V] filefmt:29  fourcc:0x10000005  size:0x0  fps:23.976  ftime:=0.0417
==========================================================================
Opening audio decoder: [libdca] DTS decoding with libdca
Stream with high frequencies VQ coding
AUDIO: 48000 Hz, 2 ch, s16le, 1536.0 kbit/100.00% (ratio: 192000->192000)
Selected audio codec: [dts] afm: libdca (DTS-libdca)
==========================================================================
PACKET SIZE: 2048 bytes, deltascr: 43885
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
Opening video filter: [harddup]
Opening video filter: [scale w=720 h=576]
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
audiocodec: framecopy (format=2001 chans=2 rate=48000 bits=16 B/s=192000 sample-1)
Limiting audio preload to 0.4s.
Increasing audio density to 4.
Pos:   0.0s      1f ( 0%)  0.00fps Trem:   0min   0mb  A-V:0.000 [0:0]
1 duplicate frame(s)!
Writing header...

```

Is there something wrong with my mencoder command, or is there perhaps a better way of attacking this. 

I've spent a fair bit of time looking for a solution to this and there seems to very little information around. I would have thought this would be quite a common thing to try and do?


Anyhow, thanks in advance,
Phil

---

### Post by pickarooney on 2010-03-26
Why would you Blu-Ray discs if you've nothing to play them on?
Sorry for not being helpful, I'm just really curious as to why anyone would want to downgrade from blu ray to dvd.

---

### Post by pssturges on 2010-03-26
6 family members, 3 tv's, 1 bluray player, 2 dvd players. Plus extended family like to borrow movies from us also, and they don't have blu-ray.;)

---

### Post by pssturges on 2010-03-26
Well it looks like I've found a solution. Winff does a great job and once you set your job up it gives you the ffmpeg commands to do the job. Now I can put that into my script!

```

ffmpeg -i "00520.m2ts" -f dvd -target pal-dvd -aspect 16:9 -b 8000kb -mbd rd -trellis -mv0 -cmp 0 -subcmp 2 "00520.mpg"

```

---

