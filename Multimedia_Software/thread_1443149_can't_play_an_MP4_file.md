---
title: "can't play an MP4 file"
date: 2010-03-30
forum: Multimedia Software
---

### Post by laineywolff on 2010-03-30
An on-line course of study I am taking has a video in MP4 format.  I can watch it on-ling however, when I download it I cannot watch it.

I have Mplayer which gives me the following message when I try to open the downloaded MP4 file     The dialogue box is titled "Fatal Error" the message is "Error Opening/Initializing the selected video_out (-vo) device."  When I Click on the "X" in the upper right hand corner to close the dialogue box or the "OK" bottom center of the dialogue box to close, I DO get the audio only of the presentation.

I have VLC and when I try to open the file it opens for a second or two with good audio, video looking like it's covered with deep gray liquid and the video just peeking through in bits and pieces.  After a second or two, the VLC closes on its own with no error message.  It's just stopped playing without providing me with any info.

I have Movie Player.  When I open the file with Movie Play, I get great audio and video which looks more like a series of stills, very jerky, behind a gray liquid through which I can see some colors and forms, and with bits and pieces of the screen not behind the gray.

Can I fix any of these so that I can study this video on my laptop? or
Is there some other applicatio n I need which will work with my Ubuntu 9.10 Karmic Koala for playing MP4 files?

I'm kinda a beginner... So if you need more info please let me know.

Thanks,

Lainey

---

### Post by ron999 on 2010-03-30
.........................

---

### Post by PRC09 on 2010-03-30
The following 2 links should enable you to play virtually all formats...At least that has been my experience...


[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by iNaitvad on 2010-03-30
Or, just install Ubuntu Tweak [http://ubuntu-tweak.com]("http://ubuntu-tweak.com") and install the restricted codecs, also the last version of VLC, etc... hope it helps. :p

---

### Post by andrew.46 on 2010-03-30
Hi laineywolff,

You might find that MPlayer has selected a video out device that is incompatible with your current setup. Can you try to play the file from the commandline with a few of the following:

```

mplayer -vo xv my_file.mp4
mplayer -vo gl my_file.mp4
mplayer -vo x11 my_file.mp4

```

You will of course need to substitute *my_file.mp4* with the actual name of your own file.

All the best,

Andrew

---

### Post by fixitdude on 2012-05-21
This is still happening. I have been using the below workaround for some time now hoping it would get fixed, but it's still doing it.

You want to make sure you have everything up to date and follow the "Comprehensive Multimedia & Video Howto"

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

The workaround is to download the latest ffmpeg source code and compile it and put it (the executable) in your media folder where you download stuff.

I renamed it "ffmpeg-new".

I open a terminal and CD to that directory and then run:

./ffmpeg-new -sameq -vsync 1 -async 1 -i input-filename.mp4 output-filename.mpg

Now Xine or VLC will play the file because it's a mpg file.

Hope this helps someone.

It's a pain in the butt and I don't understand why ffmpeg can decode the mp4 file but yet Xine or VLC can't. I would think they use the same set of codecs.

Edit: Forgot the link to ffmpeg compiling. Instead of installing it I move the executable to the media directory and use it there so that I don't lose it in Ubuntu updates etc...

[https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide](https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide)

---

### Post by Nutria on 2012-05-21
> **fixitdude said:**
> This is still happening. I have been using the below workaround for some time now hoping it would get fixed, but it's still doing it.

You've not given any detail.

Having installed the nvidia binary driver and libvdpau, this config file which I wrote in the Maverick days has let mplayer work with every AVI, MPEG2, MKV and MPEG4, WMV and webm that I've thrown at it:

```
use-filename-title=1
volume=50
af=volume=10
ao=pulse
vo=vdpau,xv,
vc=ffmpeg12vdpau,ffwmv3vdpau,ffvc1vdpau,ffh264vdpau,ffodivxvdpau,
nolirc=yes
nojoystick=yes
```


For example:
```
$ mplayer IPS_S1E01_Pilot.mp4
MPlayer SVN-r34707-4.6 (C) 2000-2012 MPlayer Team

Playing IPS_S1E01_Pilot.mp4.
libavformat version 54.0.0 (internal)
libavformat file format detected.
[mov,mp4,m4a,3gp,3g2,mj2 @ 0xcac860]max_analyze_duration reached
[lavf] stream 0: video (h264), -vid 0
[lavf] stream 1: audio (ac3), -aid 0, -alang eng
[lavf] stream 2: subtitle (movtext), -sid 0, -slang und
VIDEO:  [H264]  720x480  24bpp  90000.000 fps  2480.7 kbps (302.8 kbyte/s)
Clip info:
 major_brand: mp42
 minor_version: 0
 compatible_brands: mp42isomavc1
 creation_time: 2012-05-21 22:14:56
 encoder: HandBrake 4682svn 2012051601
Load subtitles in ./
==========================================================================
Forced video codec: ffmpeg12vdpau
Forced video codec: ffwmv3vdpau
Forced video codec: ffvc1vdpau
Forced video codec: ffh264vdpau
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
libavcodec version 54.0.0 (internal)
Selected video codec: [ffh264vdpau] vfm: ffmpeg (FFmpeg H.264 (VDPAU))
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 192.0 kbit/12.50% (ratio: 24000->192000)
Selected audio codec: [ffac3] afm: ffmpeg (FFmpeg AC-3)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
[VD_FFMPEG] Trying pixfmt=0.
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [vdpau] 720x480 => 854x480 H.264 VDPAU acceleration 
[VD_FFMPEG] XVMC-accelerated MPEG-2.
A:   6.1 V:   6.1 A-V: -0.000 ct:  0.000   0/  0  3%  1%  0.7% 4 0 

Exiting... (Quit)
```

---

