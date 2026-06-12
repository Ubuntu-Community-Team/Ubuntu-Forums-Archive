---
title: "MEncoder help needed"
date: 2008-12-30
forum: Multimedia Software
---

### Post by crazyfuturamanoob on 2008-12-30
I got an avi video I made with mencoder, from 3 jpegs. No sound, framerate=10.

And this command should make it PSP-compatible:
```

mencoder -ofps 30000/1001 -af lavcresample=24000 -vf harddup -of lavf \
    -oac lavc -ovc lavc -lavcopts aglobal=1:vglobal=1:vcodec=mpeg4:acodec=aac \
    -lavfopts format=psp \
    input.avi -o output.avi
```

But he says:
```

MEncoder 2:1.0~rc2-0ubuntu13 (C) 2000-2007 MPlayer Team
CPU: AMD Turion(tm) 64 X2 Mobile Technology TL-60 (Family: 15, Model: 104, Stepping: 2)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 0  data: 0x0 - 0x218a
AVI file format detected.
[aviheader] Video stream found, -vid 0
AVI: No audio stream found -> no sound.
VIDEO:  [FMP4]  480x272  24bpp  10.000 fps  117.2 kbps (14.3 kbyte/s)
[V] filefmt:3  fourcc:0x34504D46  size:480x272  fps:10.00  ftime:=0.1000
** MUXER_LAVF *****************************************************************
REMEMBER: MEncoder's libavformat muxing is presently broken and can generate
INCORRECT files in the presence of B frames. Moreover, due to bugs MPlayer
will play these INCORRECT files as if nothing were wrong!
*******************************************************************************
OK, exit
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
Opening video filter: [harddup]
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
VDec: vo config request - 480 x 272 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.76:1 - prescaling to correct movie aspect.
videocodec: libavcodec (480x272 fourcc=34504d46 [FMP4])
New_Face failed. Maybe the font path is wrong.
Please supply the text font file (~/.mplayer/subfont.ttf).
subtitle font: load_sub_face failed.
VIDEO CODEC ID: 13
Writing header...
[psp @ 0x86f0c54]PSP mode need one video and one audio stream
Floating point exception

```

Google says that's a bug. How to do make it to work on PSP?

I also tried PSP Video 9 with wine but doesn't work.

---

### Post by Cracauer on 2008-12-30
It obviously wants an audio stream, whether that's a bug or not.

Why don't you give it a bunch of zeros for an audio stream?

---

### Post by crazyfuturamanoob on 2008-12-30
> **Cracauer said:**
> It obviously wants an audio stream, whether that's a bug or not.

Why don't you give it a bunch of zeros for an audio stream?

How? I don't know anything about video editing.

---

### Post by crazyfuturamanoob on 2008-12-31
Ok it just wants an audio stream.

But how to disable audio completely from that conversion operation?

Like ignoring audio, not complaining about audio, no audio at all?

---

### Post by Cracauer on 2008-12-31
> **crazyfuturamanoob said:**
> Ok it just wants an audio stream.

But how to disable audio completely from that conversion operation?

Like ignoring audio, not complaining about audio, no audio at all?

You'd have to hack up the source code and hope that whoever said that it's a bug to require audio was wrong.

I'd present an empty audio file and just be done with it.

---

### Post by wolfen69 on 2008-12-31
for my PSP, nothing is easier than [Handbrake]("http://handbrake.fr/?article=download"). 1 click to convert videos. on the right of the app you will see "presets". select psp. to install handbrake, just click. super easy. also works for ipods and other devices.

---

### Post by crazyfuturamanoob on 2009-01-01
> **wolfen69 said:**
> for my PSP, nothing is easier than [Handbrake]("http://handbrake.fr/?article=download"). 1 click to convert videos. on the right of the app you will see "presets". select psp. to install handbrake, just click. super easy. also works for ipods and other devices.

I downloaded Ubuntu 32bit GUI .deb package, installed it, but launcher in Apps->Sound&Video->HandBrake didn't work.
So I looked up the command that launcher executes, and tried it in console to get error messages:
```

arho@ohra-laptop:~$ ghb
ghb: error while loading shared libraries: libxcb-render-util.so.0: cannot open shared object file: No such file or directory

```
And when I look up for that package in synaptic, I see there's libxcb-render0 installed, along with every other xcb package.

But that's just for GUI rendering. I downloaded CLI version too. Didn't work either:
```

$HandBrakeCLI -t "Stuck Pixel Fixer" -Z psp -i ~/PSP/stuckpixelfixer/rgb.avi -o ~/PSP/stuckpixelfixer/psp.avi
HandBrake 0.9.3 (2008112300) - http://handbrake.fr/
2 CPUs detected
Opening /home/arho/PSP/stuckpixelfixer/rgb.avi...
Input #0, avi, from '/home/arho/PSP/stuckpixelfixer/rgb.avi':
  Duration: 00:00:00.30, start: 0.000000, bitrate: 228 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 480x272 [PAR 1:1 DAR 30:17], 10.00 tb(r)
No title found.
HandBrake has exited.

```
I set the preset with -Z and title with -t and he says "No title found."!

...

Is it just me, or why nothing works in Ubuntu without serious troubleshooting?

---

