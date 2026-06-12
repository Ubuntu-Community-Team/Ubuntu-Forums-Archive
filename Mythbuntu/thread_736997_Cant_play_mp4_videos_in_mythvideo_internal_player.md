---
title: "Cant play mp4 videos in mythvideo internal player"
date: 2008-03-27
forum: Mythbuntu
---

### Post by paulyche on 2008-03-27
I can't play mp4 videos in mythvideo's internal player.

I have a set of videos encoded in mp4 for the ipod and I would like to be able to play these from mythvideo. The files are found by Myth ok, but when played the screen just goes black for a while and then returns to the mythvideo frontend.

the streams returned by ffmpeg -i <filename> are in ffmpeg -formats so I believe the file should play ok.

Any ideas?



```
ffmpeg -i video.mp4
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Dec 20 2007 21:22:28, gcc: 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'video.mp4':
  Duration: 00:23:43.4, start: 0.000000, bitrate: 363 kb/s
  Stream #0.0(eng): Video: mpeg4, yuv420p, 320x240, 30.00 fps(r)
  Stream #0.1(eng): Audio: aac, 24000 Hz, stereo
Must supply at least one output file
```

---

### Post by molson67 on 2008-03-27
I have a similar, or perhaps the same problem as you.  I have been using Handbrake in Windows XP to convert my DVDs to an mp4 format that is compatible with quicktime and Linux.  I don't know if it was because I updated something in ubuntu, (Mythbuntu 7.10) or if it is because of the Handbrake update, (0.9.2).  Some of my mp4 files play in Mplayer and some don't.  Actually they are m4v files.  Xine and VLC don't play it either.  They play no problem in windows MPlayer and windows quicktime.
Try this:
in a terminal window:
mplayer -v <filename>
this should spit out a lot of error messages.
I will post the error message I get when I can to compare.

Which software and version was used to convert to mp4?

Sorry I can't offer a solution :(

Mark

---

### Post by molson67 on 2008-03-27
I figured out a solution to my problem.  I was ripping with ac3 and aac for Apple TV compatibility.  and mplayer did not like that.  Although there are some ac3+aac files that do play.
I now am ripping from my mythtv box with Handbrake.

---

### Post by ian dobson on 2008-03-30
Hi molson67,

Any chance that you share the options your using to encode with handbrake.

I've been ripping my hair out for the last few days trying to get mythtv to use Handbrake to transcode my mpeg2 encoded recordings (PVR 500 encoder).

Regards
Ian Dobson

---

### Post by SL666 on 2009-05-20
Hi, 

I have a similar issue, I pulled some recodings off my mythbuntu box onto another ubuntu desktop, encoded them to mp4, and then when i move them back into my video directory, and try to play them on my mythbuntu box using mythvideo, and i get sound, but no video - just blank screen.

I suspect that its because the codec on my desktop is newer? but i'd prefer to confirm this before i go completely destroying my mytbuntu box. :)

The encoding box was setup using this thread

[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

the video was encoded specifically using this command

```
ffmpeg -y -i input.avi -pass 1 -vcodec libx264 -vpre fastfirstpass -b 1500k -bt 1500k -threads 0 -f mp4 -an /dev/null && ffmpeg -i input.avi -pass 2 -acodec libfaac -ab 128k -ac 2 -vcodec libx264 -vpre hq -b 1500k -bt 1500k -threads 0 -f mp4 output.mp4
```

The errors i get in the mythbunu log is

```
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
FAAD: compressed input bitrate missing, assuming 128kbit/s!
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio) decoder)
==========================================================================
AO: [pulse] Failed to connect to server: Connection refused
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
[h264 @ 0xf8dee0]warning: first frame is no keyframe
[h264 @ 0xf8dee0]warning: first frame is no keyframe
*REPEATED*
[h264 @ 0xf8dee0]warning: first frame is no keyframe
[h264 @ 0xf8dee0]pic->data[0]!=NULL in avcodec_default_get_buffer
[h264 @ 0xf8dee0]get_buffer() failed (-1 6083 6111 0x17a9000017a8)
[h264 @ 0xf8dee0]decode_slice_header error
VDec: vo config request - 1440 x 1080 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 1440x1080 => 1920x1080 Planar YV12  [fs] [zoom]
[ASPECT] Warning: No suitable new res found!
[ASPECT] Warning: No suitable new res found!
******************************
Error while decoding frame!
[h264 @ 0xf8dee0]pic->data[0]!=NULL in avcodec_default_get_buffer
[h264 @ 0xf8dee0]get_buffer() failed (-1 6083 6111 0x17a9000017a8)
[h264 @ 0xf8dee0]decode_slice_header error
[h264 @ 0xf8dee0]no frame!
******************************

```


The section between the lines of ******* is repeated as long as the video is playing.

The output of pulling the information on the mythbuntu box is 

```
ffmpeg -i hatedfamily.mp4
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3.1, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Mar 13 2009 17:52:45, gcc: 4.3.2
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'hatedfamily.mp4':
  Duration: 00:01:00.1, start: 0.000000, bitrate: 1641 kb/s
    Stream #0.0(und): Video: h264, yuv420p, 1440x1080 [PAR 0:1 DAR 0:1], 25.00 tb(r)
    Stream #0.1(und): Audio: mpeg4aac, 48000 Hz, stereo
Must supply at least one output file

```


On the box it was encoded on.

```
ffmpeg -i hatedfamily.mp4
FFmpeg version SVN-r18858, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-nonfree --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libxvid
  libavutil     50. 3. 0 / 50. 3. 0
  libavcodec    52.29. 0 / 52.29. 0
  libavformat   52.32. 0 / 52.32. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0. 7. 1 /  0. 7. 1
  built on May 17 2009 08:52:01, gcc: 4.3.3

Seems stream 0 codec frame rate differs from container frame rate: 50.00 (50/1) -> 25.00 (25/1)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'hatedfamily.mp4':
  Duration: 00:01:00.12, start: 0.000000, bitrate: 1641 kb/s
    Stream #0.0(und): Video: h264, yuv420p, 1440x1080 [PAR 4:3 DAR 16:9], 25 tbr, 25 tbn, 50 tbc
    Stream #0.1(und): Audio: aac, 48000 Hz, stereo, s16
At least one output file must be specified

```

Any help you can give would be great - the video quality with the x264 is excellent for a filesize just over 1/10th of the original.

---

### Post by SL666 on 2009-05-21
And to add a pinch of strangeness, if i encode it into a Matroska wrapper, it fricken works... 


```
MPlayer 1.0rc2-4.3.2 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 6000+ (Family: 15, Model: 67, Stepping: 3)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Terminal type `unknown' is not defined.

Playing /data/video/test/hatedfamily_deinterlace_mkv.mkv.
[mkv] Track ID 1: video (V_MPEG4/ISO/AVC), -vid 0
[mkv] Track ID 2: audio (A_AAC), -aid 0, -alang und
[mkv] Will play video track 1.
Matroska file format detected.
VIDEO:  [avc1]  1440x1080  24bpp  25.000 fps    0.0 kbps ( 0.0 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
FAAD: compressed input bitrate missing, assuming 128kbit/s!
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio) decoder)
==========================================================================
AO: [pulse] Failed to connect to server: Connection refused
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 1440 x 1080 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 1440x1080 => 1920x1080 Planar YV12  [fs] [zoom]
[ASPECT] Warning: No suitable new res found!
[ASPECT] Warning: No suitable new res found!

GNOME screensaver enabled

Exiting... (End of file)

```

---

### Post by hoffman462 on 2010-02-09
does anyone have fix, or a method to play mp4 files in mythvideo ?
Thanks!

---

### Post by blkbx on 2011-04-18
I know that this thread is a little old but I have the exact problem with playing m4v files trans-coded using handbrake. Did anyone find a solution.

---

### Post by SL666 on 2011-04-18
I switched to vlc for playing most of my HD content.. mkv, mp4 etc - set it up as the alternate player.

---

### Post by blkbx on 2011-04-18
I've tried to configure vlc but it always gives me error. Though I have read in this forum that it has issues with storage groups

---

### Post by SL666 on 2011-04-18
I had the storage group error - however my video's are all in the same location (i use lvm) so i wrote a script that i call (instead of vlc) that replaces the storage group name and passes the video file location to vlc (and sets some options)

---

