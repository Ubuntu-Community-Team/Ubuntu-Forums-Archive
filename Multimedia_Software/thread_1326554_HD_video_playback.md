---
title: "HD video playback"
date: 2009-11-14
forum: Multimedia Software
---

### Post by dbzkid on 2009-11-14
I am trying to view HD video on my Ubuntu 9.10 its at 1080p H264 and, I downloaded the gstreamer codecs but when I try to play with totem it starts to skip frames and video/audio go out of sync. So anyone have this problem? My computer is intel core 2 quad 2.4 ghz 4 gb ram. im pretty sure it has enough power to handle it, just wondering why it skipps like that. I also tried vlc and it did the same.

---

### Post by xc3RnbFO8P on 2009-11-14
What kind of graphics card you have?

---

### Post by dbzkid on 2009-11-14
Nvidia GT 8800, I have no idea why it wont play correctly my 720p movies play smoothly and use up only 20% cpu power when encoded in H264. I also tried it on windows on vlc and kmplayer it did the same but when I used WMP it worked and played perfectly at 1080p.

---

### Post by xc3RnbFO8P on 2009-11-14
Check in Synaptic Package Manager if you got **nvidia-185-libvdpau** installed.

---

### Post by dbzkid on 2009-11-14
Yep got that installed, It seems strange to me, it should work, it for some reason get choppy, I am going to try different video's and see if that is the case.
Tested 300 at 1080p same problem, when a lot is going on in the screen it starts to get choppy cpu overall goes to 30-35% but I went to system monitor and saw that cpu 1 and 2 went to 100% while other cpu's stayed much lower.

---

### Post by fooman on 2009-11-14
try using xine...search for xine-ui in synaptic,  or in a terminal:

```
sudo apt-get install xine-ui
```

after installing,  open xine and go to settings > setup > video

set "video driver to use" to vdpau

hope that helps.

---

### Post by dbzkid on 2009-11-14
Could it be that there isn't enough bandwidth with my VGA cable? it is connected to a 17 inch monitor.

---

### Post by HappyFeet on 2009-11-14
> **dbzkid said:**
> Could it be that there isn't enough bandwidth with my VGA cable? it is connected to a 17 inch monitor.

Yes, that is it. You need at least a dvi connection to make use of the bandwidth.

---

### Post by dbzkid on 2009-11-15
Hrmm... Ill try that, just i find it strange because I was able to play it on WMP which i found strange... this has become a weird problem

---

### Post by fooman on 2009-11-15
> **dbzkid said:**
> Hrmm... Ill try that, just i find it strange because I was able to play it on WMP which i found strange... this has become a weird problem

so obviously it is not the cable or monitor that is causing the problem.

i have an 8800gt and a 22" samsung monitor hooked up via hdmi. i am using the nvidia-185 drivers and the nvidia-185-libvdpau package is also installed. 

if i play a 1080p clip using totem or vlc (niether one supports vdpau afaik)....the video is choppy and cpu usage jumps up to 75% + on both cores of my dual-core amd 4200.  

if i play the same file using smplayer or xine (both are configured to use the vdpau driver)...it is silky smooth and cpu usage stays at or below 15%.

also plays perfecly via s-video cable to my older crt television.

---

### Post by dbzkid on 2009-11-15
> **fooman said:**
> so obviously it is not the cable or monitor that is causing the problem.

i have an 8800gt and a 22" samsung monitor hooked up via hdmi. i am using the nvidia-185 drivers and the nvidia-185-libvdpau package is also installed. 

if i play a 1080p clip using totem or vlc (niether one supports vdpau afaik)....the video is choppy and cpu usage jumps up to 75% + on both cores of my dual-core amd 4200.  

if i play the same file using smplayer or xine (both are configured to use the vdpau driver)...it is silky smooth and cpu usage stays at or below 15%.

also plays perfecly via s-video cable to my older crt television.

Unfortunatly I tried it with Smplayer and still get jerking, I really wish I knew what causes this, im on version 9.10 ubuntu. I just dont understand what does this because Im trying everything, anyone have anymore sudgestions? also I tried to see if it was because of my HD speed, ive tried on diffrent hd's and same result.

Thanks Everyone for your help so far.

---

### Post by SLEEPER_V on 2009-11-15
I have the same problem, but I am running an ati radeon 4770 vid card.

---

### Post by fooman on 2009-11-15
> **dbzkid said:**
> Unfortunatly I tried it with Smplayer and still get jerking, I really wish I knew what causes this, im on version 9.10 ubuntu. I just dont understand what does this because Im trying everything, anyone have anymore sudgestions? also I tried to see if it was because of my HD speed, ive tried on diffrent hd's and same result.

Thanks Everyone for your help so far.

with smplayer and xine....you need to go into settings and make sure the driver is set to vdpau

in smplayer,  go to options > preferences > video tab > output driver

find vdpau in the list.  if it is not in the list....you may have to find another version of smplayer (there are repositories out there for this).  

have you tried xine (xine-ui from synaptic)?  same thing...you must configure it to use vdpau.  the version from the repos should be able to handle 1080p if using the vdpau driver.

---

### Post by dbzkid on 2009-11-16
I configured Smplayer to do so and it still is jerky, but for xine under the video tab where you can select the drivers it dosnt say vdpau. In smplayer there is a vdpau and i select that restart smplayer and it still starts to jerk.

---

### Post by rvm4000 on 2009-11-16
What does the mplayer log say? (Options -> View logs)

Maybe mplayer couldn't use vdpau for some reason and it's using another driver.

---

### Post by dbzkid on 2009-11-16
```
/usr/bin/mplayer -noquiet -nofs -nomouseinput -lavdopts threads=8 -sub-fuzziness 1 -identify -slave -vo vdpau -ao alsa -nokeepaspect -framedrop -nodr -double -input conf=/usr/share/smplayer/input.conf -stop-xscreensaver -wid 65011727 -monitorpixelaspect 1 -*** -embeddedfonts -***-line-spacing 0 -***-font-scale 1 -***-styles /home/kevin/.config/smplayer/styles.*** -fontconfig -font Arial -subfont-autoscale 0 -subfont-osd-scale 20 -subfont-text-scale 20 -subcp ISO-8859-1 -vid 0 -aid 0 -subpos 100 -volume 100 -cache 3000 -osdlevel 0 -vf-add screenshot -slices -channels 2 -af scaletempo,equalizer=0:0:0:0:0:0:0:0:0:0 -softvol -softvol-max 110 /media/Local Disk 1/Video/Series/Planet Earth [1080p]/Planet Earth 01 From Pole to Pole [1080p].mkv

MPlayer SVN-r29237-4.4.1 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
Terminal type `unknown' is not defined.

Playing /media/Local Disk 1/Video/Series/Planet Earth [1080p]/Planet Earth 01 From Pole to Pole [1080p].mkv.

Cache fill:  0.00% (0 bytes)   
ID_VIDEO_ID=0
[mkv] Track ID 1: video (V_MPEG4/ISO/AVC), -vid 0
ID_AUDIO_ID=0
ID_AID_0_NAME=English (AC3)
ID_AID_0_LANG=eng
[mkv] Track ID 2: audio (A_AC3) "English (AC3)", -aid 0, -alang eng
ID_SUBTITLE_ID=0
ID_SID_0_LANG=eng
[mkv] Track ID 3: subtitles (S_TEXT/***), -sid 0, -slang eng
[mkv] Will play video track 1.
Matroska file format detected.
VIDEO:  [avc1]  1920x1080  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
ID_FILENAME=/media/Local Disk 1/Video/Series/Planet Earth [1080p]/Planet Earth 01 From Pole to Pole [1080p].mkv
ID_DEMUXER=mkv
ID_VIDEO_FORMAT=avc1
ID_VIDEO_BITRATE=0
ID_VIDEO_WIDTH=1920
ID_VIDEO_HEIGHT=1080
ID_VIDEO_FPS=23.976
ID_VIDEO_ASPECT=1.7778
ID_AUDIO_FORMAT=8192
ID_AUDIO_BITRATE=0
ID_AUDIO_RATE=48000
ID_AUDIO_NCH=6
ID_LENGTH=3200.66
ID_SEEKABLE=1
ID_CHAPTERS=0
Couldn't open video filter '***'.
***: cannot add video filter
Opening video filter: [screenshot]
[***] Init
[***] Updating font cache.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
ID_VIDEO_CODEC=ffh264
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 448.0 kbit/29.17% (ratio: 56000->192000)
ID_AUDIO_BITRATE=448000
ID_AUDIO_RATE=48000
ID_AUDIO_NCH=2
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
AO: [alsa] 48000Hz 2ch floatle (4 bytes per sample)
ID_AUDIO_CODEC=a52
[Mixer] No hardware mixing, inserting volume filter.
Starting playback...
VDec: vo config request - 1920 x 1080 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
ID_VIDEO_ASPECT=1.7778
[swscaler @ 0xb5f38240]No accelerated colorspace conversion found.
[swscaler @ 0xb5f38240]using unscaled yuv420p -> rgb24 special converter
VO: [vdpau] 1920x1080 => 1920x1080 Planar YV12 
[ASPECT] Warning: No suitable new res found!

```

Apparently it uses Vfm codec rather than the vdpau.

---

### Post by xzero1 on 2009-11-16
> **SLEEPER_V said:**
> I have the same problem, but I am running an ati radeon 4770 vid card.

I have this card. You can have UVD2 full hardware video acceleration under mplayer in Karmic. It is beta but it works pretty well. See my posts in this thread [http://ubuntuforums.org/showthread.php?t=1320668](http://ubuntuforums.org/showthread.php?t=1320668)

Note that hw accelerated video only works under mplayer or other specific players compiled for that purpose.

---

### Post by xenogia on 2009-11-16
Add this to your repositories

[https://launchpad.net/~rvm/+archive/testing](https://launchpad.net/~rvm/+archive/testing)

This has the latest mplayer and smplayer builds with vdpau built in.

Works great for me

---

### Post by rvm4000 on 2009-11-16
> **dbzkid said:**
> Apparently it uses Vfm codec rather than the vdpau.

Yes, it's using ffh264 instead of ffh264vdpau. I suggest you to update smplayer ([https://launchpad.net/~rvm/+archive/testing](https://launchpad.net/~rvm/+archive/testing)) or pass "**-vc ffh264vdpau,ffmpeg12vdpau,ffwmv3vdpau,ffvc1vdpau,**" to mplayer (Preferences -> Advanced)

---

### Post by dbzkid on 2009-11-16
> **rvm4000 said:**
> Yes, it's using ffh264 instead of ffh264vdpau. I suggest you to update smplayer ([https://launchpad.net/~rvm/+archive/testing](https://launchpad.net/~rvm/+archive/testing)) or pass "**-vc ffh264vdpau,ffmpeg12vdpau,ffwmv3vdpau,ffvc1vdpau,**" to mplayer (Preferences -> Advanced)

Thank you Soo much It works perfectly and uses up 9% cpu :p

---

