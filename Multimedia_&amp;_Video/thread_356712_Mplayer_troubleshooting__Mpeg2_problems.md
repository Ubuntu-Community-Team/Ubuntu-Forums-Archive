---
title: "Mplayer troubleshooting :: Mpeg2 problems"
date: 2007-02-08
forum: Multimedia &amp; Video
---

### Post by DrBloodmoney on 2007-02-08
I need some help troubleshooting an Mplayer issue.

I compiled Mplayer from source and installed all codecs.  It plays most everything just fine.  Mp3s, x264 video, xvid/divx, wmv are all playing fine.  However, I have some large .mpg (mpeg2) files that it won't play correctly.  The audio makes a horrific scratching noise and the video clips.  

It outputs so much of this error that I can't scroll up the terminal to see what it says when the file is getting ready to play:
```

[mp2 @ 0x8884278]Header missing skipping one byte.
```

However, it plays fine (albeit with no sound) with:
```

gmplayer xxx.mpg -nosound
```

So I'm convinced that this is an audio codec issue.  Since it's mpeg2, the audio is mpga.  I have the audio configured for ffmpeg, so it should read it.

VLC is able to play the files just fine.

Anybody with any ideas?
Also do you know how to get mplayer to log the issue?

---

### Post by DrBloodmoney on 2007-02-08
*bump*

---

### Post by halete on 2007-04-05
I have this very same problem.

Edgy user, mplayer from repos worked fine, I compiled latest version from SVN (following a howto in this forum, thanks ;)) and have the same problem you have with a large mpg and additionally some files with mpga audio (not all) have wonky sound (lots of weird noises).

This is my mplayer output for one of these files:

$ gmplayer The\ Feraless\ Avenger\ UNCUT\ -VonFrost-.avi 
MPlayer 1.0rc1-4.1.2 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) 64 Processor 3000+ (Family: 15, Model: 12, Stepping: 0)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 3DNow 3DNowEx SSE SSE2
xscreensaver_disable: Could not find XScreenSaver window.
/usr/share/fonts/truetype/freefont/FreeSans.ttf doesn't look like a bitmap font description, ignoring.
Cannot load bitmap font: /usr/share/fonts/truetype/freefont/FreeSans.ttf

Playing /media/hda4/pelis/fearless avenger/The Feraless Avenger UNCUT -VonFrost-.avi.
AVI file format detected.
VIDEO:  [DX50]  608x336  24bpp  23.976 fps  1086.8 kbps (132.7 kbyte/s)
Clip info:
 Software: FairUse Wizard - [http://fairusewizard.com](http://fairusewizard.com)
xscreensaver_disable: Could not find XScreenSaver window.
==========================================================================
Trying to force video codec driver family ffmpeg...
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Trying to force audio codec driver family ffmpeg...
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
[mp3 @ 0x881cff8]incorrect frame size
invalid new backstep 8028
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [ffmp3] afm: ffmpeg (FFmpeg MPEG layer-3 audio decoder)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
[mp3 @ 0x881cff8]incorrect frame size
invalid new backstep 732
[mp3 @ 0x881cff8]incorrect frame size
invalid new backstep 732
[mp3 @ 0x881cff8]incorrect frame size
invalid new backstep 732
[mp3 @ 0x881cff8]incorrect frame size
invalid new backstep 732
[mp3 @ 0x881cff8]incorrect frame size
invalid new backstep 732
[mp3 @ 0x881cff8]incorrect frame size
invalid new backstep 732
[mp3 @ 0x881cff8]incorrect frame size
invalid new backstep 732
[mp3 @ 0x881cff8]incorrect frame size
invalid new backstep 732

These same files work fine in VLC.

---

