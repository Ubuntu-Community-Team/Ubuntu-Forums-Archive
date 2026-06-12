---
title: "Re-encoding Movie to make File Smaller"
date: 2008-06-15
forum: Multimedia Software
---

### Post by wersdaluv on 2008-06-15
I have a 200+MB .MOV file and I want to make it smaller because I am supposed to email it. I heard that re-encoding it would be the right thing to do?

How exactly do I do that? Can anyone give me a specific mencoder or ffmpeg code?

Thanks :)

---

### Post by nunki on 2008-06-15
Give this a shot
```

mencoder <input .MOV> -ovc lavc -oac copy -o <output.avi>

```

---

### Post by wersdaluv on 2008-06-15
:~$ mencoder '/home/user/Desktop/DCIM/100PENTX/IMGP1644.MOV' -ovc lavc -oac copy -o '/home/user/Desktop/DCIM/100PENTX/file.MOV' 
MEncoder 2:1.0~rc2-0ubuntu13+medibuntu1 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Celeron(R) M processor         1.50GHz (Family: 6, Model: 13, Stepping: 8)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.

WARNING: OUTPUT FILE FORMAT IS _AVI_. See -of help.
success: format: 0  data: 0x0 - 0xcca14d4
Quicktime/MOV file format detected.
[mov] Video stream found, -vid 0
[mov] Audio stream found, -aid 1
VIDEO:  [mp4v]  320x240  24bpp  29.970 fps    0.0 kbps ( 0.0 kbyte/s)
[V] filefmt:7  fourcc:0x7634706D  size:320x240  fps:29.97  ftime:=0.0334
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
Audio format 0x736f7774 is incompatible with '-oac copy', please try '-oac pcm' instead or use '-fafmttag' to override it.

Exiting...




:(
 
What do I do now?

---

### Post by wersdaluv on 2008-06-15
Tried -oac pcma and it worked! Super thanks! I just want to reduce the size more. Hmmmm

---

