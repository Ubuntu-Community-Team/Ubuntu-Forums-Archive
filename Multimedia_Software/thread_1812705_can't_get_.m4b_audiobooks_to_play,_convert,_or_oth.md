---
title: "can't get .m4b audiobooks to play, convert, or otherwise respond"
date: 2011-07-26
forum: Multimedia Software
---

### Post by ronwell on 2011-07-26
Hello! So I recently acquired a batch of audiobooks in the .m4b format, and I can't seem to do anything with them.  They won't play in VLC, Banshee, or Rhythmbox, and they won't convert with Audio Converter or dbPowerAmp (running through WINE).  Can anyone advise me on a way to make these things work?  I don't care about preserving the chapter/bookmarking properties of the .m4b format, I just wanna get the damn things to play. I'm running Natty.

thanks so much,

sam

---

### Post by andrew.46 on 2011-07-27
I don't know a great deal about m4b files, although I see they can be encumbered with drm so this might be a problem. MPlayer can play the sample I found:

```

wget http://samples.mplayerhq.hu/ipod/MAKE_2005-08-01.m4b

```

It plays from the commandline as follows:

```

andrew@skamandros~/Desktop$ **[COLOR="Red"]mplayer MAKE_2005-08-01.m4b [/COLOR]**
MPlayer SVN-r33883-4.5.3 (C) 2000-2011 MPlayer Team

Playing MAKE_2005-08-01.m4b.
libavformat file format detected.
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x90d81d0] max_analyze_duration 5000000 reached at 5015510
[lavf] stream 0: audio (aac), -aid 0, -alang eng
[lavf] stream 1: subtitle (movtext), -sid 0, -slang eng
[lavf] stream 2: video (tiff), -vid 0
[lavf] stream 3: subtitle (movtext), -sid 1, -slang eng
VIDEO:  [tiff]  167x166  24bpp  22050.000 fps  126.8 kbps (15.5 kbyte/s)
Clip info:
 major_brand: M4A 
 minor_version: 0
 compatible_brands: M4A mp42isom
 creation_time: 2005-08-01 07:26:16
 title: MAKE_2005-08-01
 artist: MAKE Magazine
 composer: MAKE Magazine - Phillip Torrone
 album: Interview with Janus Wireless
 grouping: MAKE Magazine enhanced podcast
 genre: Podcast
 date: 2005
 comment: Interview with Janus wireless and their 5 Wi-Fi card packet capturing Linux box. This is a special enhanced podcast (this file plays images and links in iTunes and on iPod color devices).
Load subtitles in ./
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [fftiff] vfm: ffmpeg (FFmpeg TIFF)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 22050 Hz, 1 ch, s16le, 32.0 kbit/9.08% (ratio: 4004->44100)
Selected audio codec: [ffaac] afm: ffmpeg (FFmpeg AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
AO: [oss] 22050Hz 1ch s16le (2 bytes per sample)
Starting playback...
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
Movie-Aspect is 0.75:1 - prescaling to correct movie aspect.
[swscaler @ 0x898e5c0]BICUBIC scaler, from rgb24 to yuv420p using MMX2
VO: [xv] 168x166 => 168x223 Planar YV12 
A:   0.1 V:   0.0 A-V:  0.083 ct:  0.000   0/  0 ??% ??% ??,?% 0 0 
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 168x166 => 221x166 Planar YV12 
A:  11.8 V:  17.0 A-V: -5.162 ct:  0.000   0/  0  0%  0%  0.1% 0 0 

Exiting... (Quit)

```

So MPlayer might be worth a go perhaps. Can you post one of the difficult files somewhere?

---

