---
title: "SMPlayer mkv video is not synced with the audio?"
date: 2015-04-12
forum: Multimedia Software
---

### Post by remmas-sido on 2015-04-12
Hello guys 
I've been facing a really strange problem lately. When I play mkv video in SMPlayer, I discover that the audio is more advanced than the video. Here is the media-info:
General
Unique ID                                : 253304361903526077492948485350730742335 (0xBE90A543A470820EB44B4D4BC547BA3F)
Complete name                            : XXX.XXX.XXXXXX.XXXXX.E02.140217.HDTV.x264.1080XXXXXXXXX.mkv
Format                                   : Matroska
Format version                           : Version 4 / Version 2
File size                                : 2.94 GiB
Duration                                 : 59mn 24s
Overall bit rate                         : 7 088 Kbps
Encoded date                             : UTC 2014-02-28 08:08:52
Writing application                      : mkvmerge v6.6.0 ('The Edge Of The In Between') built on Dec  1 2013 17:55:00
Writing library                          : libebml v1.3.0 + libmatroska v1.4.1


Video
ID                                       : 1
Format                                   : AVC
Format/Info                              : Advanced Video Codec
Format profile                           : High@L4.1
Format settings, CABAC                   : Yes
Format settings, ReFrames                : 4 frames
Codec ID                                 : V_MPEG4/ISO/AVC
Duration                                 : 59mn 24s
Bit rate                                 : 6 499 Kbps
Width                                    : 1 920 pixels
Height                                   : 1 080 pixels
Display aspect ratio                     : 16:9
Frame rate                               : 29.970 fps
Color space                              : YUV
Chroma subsampling                       : 4:2:0
Bit depth                                : 8 bits
Scan type                                : Progressive
Bits/(Pixel*Frame)                       : 0.105
Stream size                              : 2.70 GiB (92%)
Title                                    : &#50521;&#53372;&#54620; &#46028;&#49905;&#45376; 1080p-AyoEunji
Writing library                          : x264 core 138 r2358 9e941d1
Encoding settings                        : cabac=1 / ref=4 / deblock=1:-1:-1 / analyse=0x3:0x133 / me=umh / subme=10 / psy=1 / psy_rd=1.00:0.00 / mixed_ref=1 / me_range=24 / chroma_me=1 / trellis=2 / 8x8dct=1 / cqm=0 / deadzone=21,11 / fast_pskip=1 / chroma_qp_offset=-2 / threads=6 / lookahead_threads=1 / sliced_threads=0 / nr=0 / decimate=1 / interlaced=0 / bluray_compat=0 / constrained_intra=0 / bframes=8 / b_pyramid=2 / b_adapt=2 / b_bias=0 / direct=3 / weightb=1 / open_gop=0 / weightp=2 / keyint=300 / keyint_min=29 / scenecut=40 / intra_refresh=0 / rc_lookahead=60 / rc=crf / mbtree=1 / crf=18.0 / qcomp=0.60 / qpmin=0 / qpmax=69 / qpstep=4 / vbv_maxrate=62500 / vbv_bufsize=78125 / crf_max=0.0 / nal_hrd=none / ip_ratio=1.40 / aq=1:1.00
Language                                 : Korean
Default                                  : Yes
Forced                                   : No


Audio
ID                                       : 2
Format                                   : AC-3
Format/Info                              : Audio Coding 3
Mode extension                           : CM (complete main)
Codec ID                                 : A_AC3
Duration                                 : 59mn 24s
Bit rate mode                            : Constant
Bit rate                                 : 448 Kbps
Channel(s)                               : 2 channels
Channel positions                        : Front: L R
Sampling rate                            : 48.0 KHz
Bit depth                                : 16 bits
Compression mode                         : Lossy
Delay relative to video                  : 32ms
Stream size                              : 190 MiB (6%)
Language                                 : Korean
Default                                  : Yes
Forced                                   : No

---

### Post by SeijiSensei on 2015-04-12
SMPlayer has entries in its Audio menu to add or remove delay between the video and audio tracks.  Try to find a setting that works for this content.

Do you have this problem with every Matroska file you view, or just this one?

---

### Post by Rob Sayer on 2015-04-13
If it's just the one video it'd be hard to say it's smplayer's fault, especially since the mediainfo report strongly hints it's a dl'ed video from God knows who.

Many of these uploaded videos are not encoded properly and have problems anywhere.  Noobs have NO idea how difficult video encoding actually is.  They didn't invent those formats and options for casual users wanting to back up their dvds.  They're professional standards.

I'd also want to know what your hardware is ... can it handle HD video with a fairly high bit rate?  Is your video card set up properly in linux?  Is it properly supported?

---

### Post by remmas-sido on 2015-04-13
> **SeijiSensei said:**
> SMPlayer has entries in its Audio menu to add or remove delay between the video and audio tracks.  Try to find a setting that works for this content.

Do you have this problem with every Matroska file you view, or just this one?
Yes, I have this problem with every Matroska file I view.

---

### Post by remmas-sido on 2015-04-13
> **Rob Sayer said:**
> If it's just the one video it'd be hard to say it's smplayer's fault, especially since the mediainfo report strongly hints it's a dl'ed video from God knows who.

Many of these uploaded videos are not encoded properly and have problems anywhere.  Noobs have NO idea how difficult video encoding actually is.  They didn't invent those formats and options for casual users wanting to back up their dvds.  They're professional standards.

I'd also want to know what your hardware is ... can it handle HD video with a fairly high bit rate?  Is your video card set up properly in linux?  Is it properly supported?
Memory: 2.9 GB
Processor: Intel® Core™2 Duo CPU T6400 @ 2.00GHz × 2 
Graphics: Unknown

---

### Post by SeijiSensei on 2015-04-14
That processor with its likely companion Intel graphics adapter will have a hard time with modern 720p or better HD formats.  I'm not surprised it can't keep up with a 1080p30 video.  You can change a couple of settings in SMPlayer and see if it helps.  In Options > Preferences > Performance, try allowing frames to be dropped, and enable skipping in the loop filter.  See if any combination of those helps.

---

### Post by Rob Sayer on 2015-04-14
Also some other smplayer options:

set the cache for local files to 8192Kb

under mplayer arguments paste this in:

```
-cache-min 50
```

---

### Post by remmas-sido on 2015-04-15
> **Rob Sayer said:**
> Also some other smplayer options:

set the cache for local files to 8192Kb

under mplayer arguments paste this in:

```
-cache-min 50
```
Where can I find:
mplayer arguments

---

### Post by SeijiSensei on 2015-04-15
Options > Preferences > Advanced > Options for MPlayer/MPV.  Add it to the top box.

---

