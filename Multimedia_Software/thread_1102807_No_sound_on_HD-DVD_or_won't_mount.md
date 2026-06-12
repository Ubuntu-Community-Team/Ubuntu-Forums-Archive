---
title: "No sound on HD-DVD or won't mount"
date: 2009-03-22
forum: Multimedia Software
---

### Post by 3rdalbum on 2009-03-22
I've just bought two HD-DVDs to use with my LG Blu-ray/HD-DVD drive. Superman 2 "The Richard Donner Cut" and Knocked Up. (they were cheap)

I've got several Blu-rays to rip and play using dumphd and an SVN copy of Mplayer, but I'm having trouble with these two discs.

Superman 2 will rip and the video will play, but there is no sound. Pressing the # key in Mplayer to change sound tracks doesn't work. This is the output:

```
MPlayer dev-SVN-r28239-4.3.2 (C) 2000-2008 MPlayer Team                      
CPU: Intel(R) Core(TM)2 Duo CPU     E6850  @ 3.00GHz (Family: 6, Model: 15, Stepping: 11)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1                              
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2                                  

Playing feature.EVO.
MPEG-PS file format detected.
Searching for VC1 sequence header... found
VIDEO:  VC-1  1920x1080, 29.970 fps, header len: 36
==========================================================================
Requested video codec family [wmvvc1dmo] (vfm=dmo) not available.         
Enable it at compilation.                                                 
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family          
Selected video codec: [ffvc1] vfm: ffmpeg (FFmpeg WVC1)                   
==========================================================================
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52                  
Using SSE optimized IMDCT transform                                       

Too many video packets in the buffer: (4096 in 8249122 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.   
A52 sync failed                                                         
ADecoder init failed :(                                                 
ADecoder init failed :(                                                 
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders        

Too many video packets in the buffer: (4096 in 8249122 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.   
Unknown/missing audio format -> no sound                                
ADecoder init failed :(                                                 
Opening audio decoder: [hwac3] AC3/DTS pass-through S/PDIF
No accelerated IMDCT transform found

Too many video packets in the buffer: (4096 in 8249122 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
AC3/DTS sync failed
ADecoder init failed :(
ADecoder init failed :(
Cannot find codec for audio format 0x2000.
Read DOCS/HTML/en/codecs.html!
Audio: no sound
Starting playback...
VDec: vo config request - 1920 x 1080 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [x11] 1920x1080 => 1920x1080 Planar YV12
[ASPECT] Warning: No suitable new res found!
[swscaler @ 0xc17840]using unscaled yuv420p -> rgb32 special converter
New_Face failed. Maybe the font path is wrong.
Please supply the text font file (~/.mplayer/subfont.ttf).
subtitle font: load_sub_face failed.
New_Face failed. Maybe the font path is wrong.
Please supply the text font file (~/.mplayer/subfont.ttf).
subtitle font: load_sub_face failed.

```

The message seems to be "no sound" rather than "can't understand this sound track". When I used dumphd, only the "Video" checkbox was enabled and ticked. The "Audio" checkbox was disabled.

Okay, so that's Superman 2. I'm having bigger troubles with Knocked Up - it simply won't mount. I get a "permission denied" message from Dolphin whenever I mount the disc, which is really strange. Nautilus just shows an empty folder.

I'm using Intrepid with all updates applied, including those from Proposed. I have the libav*-unstripped libraries installed from the Ubuntu repository. My SVN copy of Mplayer was built in January, I think, and compiled with everything as far as I remember.

---

