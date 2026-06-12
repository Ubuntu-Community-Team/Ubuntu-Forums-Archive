---
title: "Burning DVDs"
date: 2007-05-08
forum: Multimedia &amp; Video
---

### Post by brizzlepop on 2007-05-08
Helloo.. I'm having issues burning with Feisty.  I used to be able to do it in Windows with a program that came with my burner, but now I have no idea! 

I used Tovid and I got two directories AUDIO_TS and VIDEO_TS.  Then I used k3b to burn a video DVD.  The burn was successful and I did not run into any errors.  However, when I tried to play it, I got a message that said to check the TV.   Does anybody have any idea why it will not play?

---

### Post by jiminycricket on 2007-05-08
can you play the dvd through mplayer in the command line?

 mplayer dvd://1

---

### Post by brizzlepop on 2007-05-08
Thanks for the response.  It played, however I also got this:

```

MPlayer 2:1.0~rc1-0ubuntu9 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Celeron(R) M processor         1.40GHz (Family: 6, Model: 13, Stepping: 8)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvd://1.
There are 1 titles on this DVD.
There are 7 chapters in this DVD title.
There are 1 angles in this DVD title.
audio stream: 0 format: ac3 (stereo) language: unknown aid: 128.
number of audio channels on disk: 1.
number of subtitles on disk: 0
MPEG-PS file format detected.
VIDEO:  MPEG2  720x480  (aspect 3)  29.970 fps  7840.0 kbps (980.0 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 480 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 224.0 kbit/14.58% (ratio: 28000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 720x480 => 854x480 Planar YV12 
A:   9.5 V:   9.5 A-V:  0.018 ct:  0.047 280/280 12%  3%  1.5% 11 0 
Exiting... (Quit)

```

---

### Post by brizzlepop on 2007-05-08
Also I just found that there's a "...avi.enc.mpg" file of the video on my desktop that isn't inside the video_ts folder.. should I do anything to this?  Just today I burned with k3b an ISO I had torrented and it went fine and played on my DVD player.  Why won't the other one work?

---

### Post by plainjane on 2007-05-09
Don't know if this will help at all, but I ran into the same problems.  I use Todisc, which also makes an Audio and a Video file.  The only way I could get it to run in a stand alone player was to use DVDShrink run through Wine to burn. Even using Shrink I could only get it to play in one of my DVD players, but will play fine in all my computers, including Windows.  Hope this helps!  Little off topic, but what did you use to convert the avi in Windows?

---

### Post by brizzlepop on 2007-05-10
Thank you!  I will try that.  In Windows, I used a program that came with my burner that did everything for me.  It was called Pro something.. I don't remember

---

