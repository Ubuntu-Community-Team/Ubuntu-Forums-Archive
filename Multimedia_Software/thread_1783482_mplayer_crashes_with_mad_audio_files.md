---
title: "mplayer crashes with mad audio files"
date: 2011-06-15
forum: Multimedia Software
---

### Post by mitchd123 on 2011-06-15
I think I've isolated this to the audio codec.  If I run mplayer *.avi, then mplayer crashes, however if I run mplayer -nosound * then the movie plays without audio.

AMD64   10.10
MPlayer 1.0rc4-4.4.5
alsa for audio
w64codecs installed

I started with the standard version of mplayer with 10.10, and then upgraded to medibuntu's version...still no luck.

here's what happens when I play a file: 



mplayer: Symbol `ff_codec_wav_tags' has different size in shared object, consider re-linking
mplayer: Symbol `ff_codec_bmp_tags' has different size in shared object, consider re-linking
MPlayer 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team

Playing xvid.cd1.avi.
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [XVID]  624x352  12bpp  23.976 fps  1590.9 kbps (194.2 kbyte/s)
Clip info:
 Software: VirtualDubMod 1.5.10.2 (build 2540/release)
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
**Forced audio codec: mad**
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders


[B]MPlayer interrupted by signal 11 in module: init_audio_codec
- MPlayer crashed by bad usage of CPU/FPU/RAM.[/B]
  Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
  disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.
 [ This binary of MPlayer in Debian is currently compiled with
   '--enable-debug'; the debugging symbols are in the package
   'mplayer-dbg'.]


Be gentle, I'm not a linux expert.  Any hints?

---

