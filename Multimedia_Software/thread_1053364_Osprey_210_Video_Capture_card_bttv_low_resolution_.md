---
title: "Osprey 210 Video Capture card bttv low resolution input stream"
date: 2009-01-28
forum: Multimedia Software
---

### Post by chaos51 on 2009-01-28
Problem:
I have an Osprey 210 Video Capture Card which should be capable of capturing resolutions up to NTSC (720x480)/PAL (720x576).
I currently only seem to be able to get 320x240 so this is my problem I need to figure out.  I want to get at least 640x480.

The Osprey card is a bt878a chipset.  

The intent is to use ffmpeg, ffmpeg2theora, or Real Producer 11.1 to capture Video and encode it to various formats, we want a target resolution of 640x480.

Trying this both on an recently updated 8.10 and also 8.04.
Installed and updated 8.10 today (01/28/2009) and also build ffmpeg from svn trunk today.

System Specs:
- Shuttle XPC
- Quad Core
- 4Gb Ram
- 250 GB HD
- ATI FIREGL v3400
- Osprey 210 Video Capture Card

Setup:
Video Source - Philips DVP5982 DVD Player Composite Video Out to Composite Video In on Osprey.
Audio Source - Philips DVP5982 DVD Player Stereo RCA Out to 1/8 headphone jack to Line In on Shuttle

Software Used for Testing:
VLC - using Capture Device setting with:
video4linux2
NTSC
Video Device: /dev/video0
Audio Device: /dev/dsp

The stream is only 320x240 when looking at the media info.

Using 
ffmpeg -f oss -i /dev/dsp -f video4linux2 -i /dev/video0 test.mpg
FFmpeg version SVN-r16847, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-libmp3lame --enable-libfaad --enable-libxvid --enable-libfaac --enable-gpl --enable-libvorbis --enable-libfaadbin --enable-swscale --enable-libgsm --enable-libamr-nb --enable-libamr-wb --enable-pthreads --enable-libdc1394 --enable-postproc --enable-nonfree --enable-libspeex --enable-libtheora --enable-libx264 --prefix=/usr
  libavutil     49.14. 0 / 49.14. 0
  libavcodec    52.11. 0 / 52.11. 0
  libavformat   52.25. 0 / 52.25. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libswscale     0. 6. 1 /  0. 6. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Jan 28 2009 16:54:28, gcc: 4.3.2
Input #0, oss, from '/dev/dsp':
  Duration: N/A, start: 1233179795.156734, bitrate: N/A
    Stream #0.0: Audio: pcm_s16le, 44100 Hz, mono, s16, 705 kb/s
[video4linux2 @ 0x96a0050]Wrong size (0x0)
/dev/video0: Error while opening file

Using:
ffmpeg -f oss -i /dev/dsp -s 640x480 -f video4linux2 -i /dev/video0 test.mpg
gets output but I'm not convinced that it's actually getting 640x480 raw video from the card.  I think that it is resampling 320x240 to 640x480 which means pretty poor results.

(note I was not specifying a video/audio codec just for testing -s, I am aware that this default yeilds mpeg1 video with mp2 audio)

I also have noticed bad interlacing (horizontal lines in the video), I've tried using -deinterlace and other options with ffmpeg and vlc but I still seem to get them.

Any help would be greatly appreciated.
thanks,

---

### Post by chaos51 on 2009-01-29
Some more information/problems:
I apparently can't record audio now either (using 8.10, I can with 8.04).  I've tried all sorts of combinations of the audio mixer settings and trying either the Line-In for the onboard audio and the Osprey Brooktree bt878 audio input.

At least with ffmpeg I have to specify -f oss which I'm assuming uses the OSS mixer settings but the only Recording volume control I have in the Gnome Volume Control for this is Digital-1 which is not the LineIn.  

My Gnome Volume control mixer shows:
HDA Intel (Alsa Mixer)
Brooktree bt878 (Alsa Mixer)
RealTek ALC888 (OSS mixer)
Playback: ALSA PCM on from:0 (ALC888 Analog) via DMA (PulseAudio Mixer)
Capture: ALSA PCM on hw:1 (Bt87x Digital) via DMA (PulseAudio Mixer)
Capture: Monitor Source of ALSA PCM on front:0 (ALC888 Analog) via DMA (PulseAudio Mixer)
Capture: ALSA PCM on front:0 (ALC888) Analog via DMA (PulseAudio Mixer)

---

### Post by chaos51 on 2009-01-29
I think I might have been misunderstanding some things here:
1. It looks like the bttv driver and ffmpeg will allow me to capture are higher resolutions as seen when I tried the following (see bold output):

 ffmpeg -f oss -ab 64k -ac 2 -i /dev/dsp -s 1024x768 -tvstd ntsc -f video4linux2 -i /dev/video0  -s 640x480  -ab 64k -ac 2 -b 400k -async 2 test3.mpg

FFmpeg version SVN-r16847, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-libmp3lame --enable-libfaad --enable-libxvid --enable-libfaac --enable-gpl --enable-libvorbis --enable-libfaadbin --enable-swscale --enable-libgsm --enable-libamr-nb --enable-libamr-wb --enable-pthreads --enable-libdc1394 --enable-postproc --enable-nonfree --enable-libspeex --enable-libtheora --enable-libx264 --prefix=/usr
  libavutil     49.14. 0 / 49.14. 0
  libavcodec    52.11. 0 / 52.11. 0
  libavformat   52.25. 0 / 52.25. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libswscale     0. 6. 1 /  0. 6. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Jan 28 2009 16:54:28, gcc: 4.3.2
Input #0, oss, from '/dev/dsp':
  Duration: N/A, start: 1233257085.180198, bitrate: N/A
    Stream #0.0: Audio: pcm_s16le, 44100 Hz, stereo, s16, 1411 kb/s
[B][video4linux2 @ 0x9f8a070][4]Capabilities: 5000015
[video4linux2 @ 0x9f8a070]The V4L2 driver changed the video from 1024x768 to 768x480[/B]
Input #1, video4linux2, from '/dev/video0':
  Duration: N/A, start: 1233257085.306262, bitrate: -2147483 kb/s
    Stream #1.0: Video: rawvideo, yuv420p, 768x480, -2147483 kb/s, 1000000.00 tb(r)
Output #0, mpeg, to 'test3.mpg':
    Stream #0.0: Video: mpeg1video, yuv420p, 640x480, q=2-31, 400 kb/s, 60.00 tb(c)
    Stream #0.1: Audio: mp2, 44100 Hz, stereo, s16, 64 kb/s
Stream mapping:
  Stream #1.0 -> #0.0
  Stream #0.0 -> #0.1
Press [q] to stop encoding
frame= 1940 fps= 61 q=31.0 Lsize=    2236kB time=32.31 bitrate= 566.9kbits/s    
video:1963kB audio:252kB global headers:0kB muxing overhead 0.945678%

So from the above in bold, I am inferring that since ffmpeg dropped the resolution to something lower that 1024x768 and higher than 320x240, ffmpeg can indeed capture at 640x480. 

Incidentally, starting tvtime also confirms that that capture card can get higher than 320x240.  I guess my problem started in assuming that VLC would show me the max resolution that was possible instead of dropping in down to 320x240.  Live and learn I guess.  Now I guess I have to continue to tweak my ffmpeg settings to get the quality/size I'm looking for (this could take a really long time).

I think I also figured out the audio problem by comparing what I had in 8.04 with 8.10.

It looks like the HDA Intel (Alsa mixer) defaults to taking capture input from the mic (and not line-in).  In the preferences of the HDA Intel I added checkmarks for the Input Source: Options and then in the Options tab I was able to select "Line"

---

### Post by chaos51 on 2009-02-03
I should also add that it looks like I can make vlc work with 640x480 by 
installing ivtv-utils and then running:
v4l2-ctl --set-fmt-video=width=640,height=480
before starting vlc

---

### Post by kuldeepiitk on 2010-05-12
Hi,

    I am trying to setup Osprey 210 on my Ubuntu 9.10 machine. Could you please help me out on this? I didn't find drivers for Osprey 210 anywhere. When I tried contacting Viewcast, they pointed me to [http://linuxtv.org](http://linuxtv.org). But there also I didn't find any answer. Please help.

Thanks in advance,
Kuldeep

---

