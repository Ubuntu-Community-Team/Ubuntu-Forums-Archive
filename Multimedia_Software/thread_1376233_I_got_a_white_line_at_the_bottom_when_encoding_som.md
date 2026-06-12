---
title: "I got a white line at the bottom when encoding some videos with handbrake!!"
date: 2010-01-08
forum: Multimedia Software
---

### Post by Wanas on 2010-01-08
When I try to encode some HD videos I got a white line at the bottom (see the screenshots), its only some types of HD videos have this problem with handbreak other videos is working fine.

Here is the details of the video that I want to encode:
Resolution:1280 x 1080
Aspect ratio:1.7778
Format:0x10000002
Bitrate:65000 kbps
Frames per second:29.970
Selected codec:ffmpeg2

Here is the screenshots:
[http://img710.imageshack.us/img710/1816](http://img710.imageshack.us/img710/1816) ... break1.png
[http://img192.imageshack.us/img192/5363](http://img192.imageshack.us/img192/5363) ... break2.png

Here is my computer details:
OS: Ubuntu 9.10
CPU: core 2 due 3 GHZ
Video Driver: Nvidia 6200 LE
Ram: 3 GB

here is the handbrake log
> [06:37:29] gtkgui: HandBrake 0.9.4 (2009112300) - Linux i686 - [http://handbrake.fr](http://handbrake.fr)
[06:37:30] hb_init: checking cpu count
[06:37:30] hb_init: starting libhb thread
[06:37:30] hb_init: checking cpu count
[06:37:30] hb_init: starting libhb thread
libdvdread: Encrypted DVD support unavailable.
[06:37:36] hb_scan: path=/media/Secondary/My Downloads/Jdownloader/Nelly Furtado - Glastonbury Music Festival (UK 19.06.2004) HD-1080i.mpg, title_index=0
[06:37:36] scan: trying to open with libdvdread
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Encrypted DVD support unavailable.
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: failed to read VIDEO_TS.IFO
[06:37:36] dvd: not a dvd - trying as a stream/file instead
[06:37:36] file is MPEG DVD Program Stream
[06:37:37] add_audio_to_title: added AC3 audio stream 0x80bd
[06:37:37] scan: decoding previews for title 1
[06:37:37] scan: audio 0x80bd: AC-3, rate=48000Hz, bitrate=384000 Unknown (AC3) (5.1 ch)
[06:37:38] scan: 10 previews, 1280x1088, 29.970 fps, autocrop = 0/0/0/0, aspect 1.76:1, PAR 3:2
[06:37:38] Title is likely interlaced or telecined (8 out of 10 previews). You should do something about that.
[06:37:38] scan: title (0) job->width:1280, job->height:720
[06:37:38] libhb: scan thread found 1 valid title(s)
libdvdread: Encrypted DVD support unavailable.
[06:44:53] hb_scan: path=/media/Secondary/My Downloads/Jdownloader/Nelly Furtado - Glastonbury Music Festival (UK 19.06.2004) HD-1080i.mpg, title_index=1
[06:44:53] scan: trying to open with libdvdread
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Encrypted DVD support unavailable.
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: failed to read VIDEO_TS.IFO
[06:44:53] dvd: not a dvd - trying as a stream/file instead
[06:44:53] file is MPEG DVD Program Stream
[06:44:53] add_audio_to_title: added AC3 audio stream 0x80bd
[06:44:53] scan: decoding previews for title 1
[06:44:53] scan: audio 0x80bd: AC-3, rate=48000Hz, bitrate=384000 Unknown (AC3) (5.1 ch)
[06:44:54] scan: 10 previews, 1280x1088, 29.970 fps, autocrop = 0/0/0/0, aspect 1.76:1, PAR 3:2
[06:44:54] Title is likely interlaced or telecined (8 out of 10 previews). You should do something about that.
[06:44:54] scan: title (0) job->width:1280, job->height:720
[06:44:54] libhb: scan thread found 1 valid title(s)
[06:44:56] gtkgui: Modified Preset: Regular->Normal
[06:44:56] 1 job(s) to process
[06:44:56] starting job
[06:44:56] job configuration:
[06:44:56]  * source
[06:44:56]    + /media/Secondary/My Downloads/Jdownloader/Nelly Furtado - Glastonbury Music Festival (UK 19.06.2004) HD-1080i.mpg
[06:44:56]    + title 1, chapter(s) 1 to 1
[06:44:56]  * destination
[06:44:56]    + /home/wanas/Videos/Nelly Furtado - Glastonbury Music Festival (UK 19.06.2004) HD-1080i.mkv
[06:44:56]    + container: Matroska (.mkv)
[06:44:56]  * video track
[06:44:56]    + decoder: mpeg2
[06:44:56]      + bitrate 65000 kbps
[06:44:56]    + frame rate: same as source (around 29.970 fps)
[06:44:56]    + loose anamorphic
[06:44:56]      + modulus: 2
[06:44:56]      + storage dimensions: 1280 * 1088 -> 720 * 612, crop 0/0/0/0
[06:44:56]      + pixel aspect ratio: 3 / 2
[06:44:56]      + display dimensions: 1080 * 612
[06:44:56]    + encoder: x264
[06:44:56]      + options: ref=2:bframes=2:subme=6:mixed-refs=0:weightb=0:8x8dct=0:trellis=0
[06:44:56]      + bitrate: 6244 kbps, pass: 0
[06:44:56]  * audio track 0
[06:44:56]    + decoder: Unknown (AC3) (5.1 ch) (track 1, id 80bd)
[06:44:56]      + bitrate: 384 kbps, samplerate: 48000 Hz
[06:44:56]    + AC3 passthrough
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Encrypted DVD support unavailable.
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: failed to read VIDEO_TS.IFO
[06:44:56] dvd: not a dvd - trying as a stream/file instead
[06:44:56] reader: first SCR 44 id 224 DTS 14997
[06:44:56] mpeg2: "" (1) at frame 0 time 3003
[06:44:56] encx264: keyint-min: 30, keyint-max: 300
[06:44:56] encx264: encoding with stored aspect 3/2
x264 [info]: using SAR=3/2
x264 [info]: using cpu capabilities: MMX2 SSE2 SSE3 Cache64
x264 [info]: profile Main, level 3.1
No accelerated IMDCT transform found
[06:44:57] sync: expecting 15158 video frames
[ac3 @ 0xb57062b0]No channel layout specified. The encoder will guess the layout, but it might be incorrect.
[06:44:57] sync: first pts is 3003
[07:36:56] reader: done. 0 scr changes
[07:37:03] sync: got 15274 frames, 15158 expected
[07:37:03] work: average encoding speed for job is 4.886315 fps
[07:37:16] mux: track 0, 15274 frames, 405722512 bytes, 6367.91 kbps, fifo 64
[07:37:16] mux: track 1, 15929 frames, 24466944 bytes, 384.01 kbps, fifo 128
[07:37:16] mpeg2 done: 15275 frames
[07:37:16] render: lost time: 0 (0 frames)
[07:37:16] render: gained time: 0 (0 frames) (0 not accounted for)
x264 [info]: frame I:195   Avg QP:15.72  size: 70247  PSNR Mean Y:46.99 U:50.11 V:50.36 Avg:47.82 Global:47.48
x264 [info]: frame P:9501  Avg QP:17.79  size: 31753  PSNR Mean Y:44.42 U:47.98 V:48.22 Avg:45.33 Global:44.69
x264 [info]: frame B:5578  Avg QP:20.32  size: 16198  PSNR Mean Y:41.54 U:46.13 V:46.85 Avg:42.63 Global:41.89
x264 [info]: consecutive B-frames: 28.6% 63.7%  7.7%
x264 [info]: mb I  I16..4: 12.9%  0.0% 87.1%
x264 [info]: mb P  I16..4:  3.2%  0.0% 12.8%  P16..4: 44.6% 25.3% 11.4%  0.0%  0.0%    skip: 2.7%
x264 [info]: mb B  I16..4: 10.1%  0.0%  4.4%  B16..8: 34.0%  6.0%  5.8%  direct:22.6%  skip:17.0%  L0:24.7% L1:35.4% BI:39.9%
x264 [info]: final ratefactor: 16.16
x264 [info]: coded y,uvDC,uvAC intra: 76.7% 86.5% 69.6% inter: 47.4% 39.9% 11.5%
x264 [info]: i16 v,h,dc,p: 27% 26% 28% 19%
x264 [info]: i4 v,h,dc,ddl,ddr,vr,hd,vl,hu: 29% 14% 16%  6%  7%  9%  6%  8%  5%
x264 [info]: Weighted P-Frames: Y:4.6%
x264 [info]: ref P L0: 60.9% 17.7% 21.4%
x264 [info]: SSIM Mean Y:0.9855289
x264 [info]: PSNR Mean Y:43.399 U:47.334 V:47.744 Avg:44.374 Global:43.471 kb/s:6368.87
[07:37:16] libhb: work result = 0

PS: I tried to post it here: [http://forum.handbrake.fr/viewtopic.php?f=13&t=14218](http://forum.handbrake.fr/viewtopic.php?f=13&t=14218)
but I found no respond

---

### Post by gsmanners on 2010-01-09
Does that line show up if you play the source file in VLC or mplayer?

---

### Post by Wanas on 2010-01-09
> **gsmanners said:**
> Does that line show up if you play the source file in VLC or mplayer?

no at all it works perfect on smplayer and vlc, it only appears after encoding !!

---

### Post by gsmanners on 2010-01-09
Well, at least your post got approved, so they may be looking into it. If you could supply a small sample that does the same thing, that would probably be even more helpful.

---

### Post by Wanas on 2010-01-09
I have them samples by the screenshots.
I hope the can help me faster.
I am trying to use this application on windows to see if this error appears there or not, but havnt tryied yet :(

---

### Post by gsmanners on 2010-01-11
Screenshots show you the problem's symptoms, but they don't really help other people replicate the actual problem so they really aren't very helpful all by themselves. A small .mpg file made from the original would be far more helpful.

Handbrake is more or less at the mercy of the ffmpeg devs because that's mainly what they use. The code is pretty much the same for the Windows client, so I wouldn't expect a different result there. I guess it can't hurt to try.

---

