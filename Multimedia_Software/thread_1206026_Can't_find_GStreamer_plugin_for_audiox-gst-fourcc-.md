---
title: "Can't find GStreamer plugin for audio/x-gst-fourcc-ac-3 decoder"
date: 2009-07-06
forum: Multimedia Software
---

### Post by wiley.q.hacker on 2009-07-06
Hi:

I have file with video encoded in AVC, and audio encoded in AC-3. The container is MPEG-4 (.mp4). The details are as follows:
[INDENT] [FONT=Courier New]General
Complete name                    : C:\Documents and Settings\wiley\My Documents\wedding.mp4
Format                           : MPEG-4
Format profile                   : Base Media / Version 2
Codec ID                         : mp42
File size                        : 1.56 GiB
Duration                         : 1h 54mn
Overall bit rate                 : 1 951 Kbps
Encoded date                     : UTC 2009-04-05 10:14:06
Tagged date                      : UTC 2009-04-05 18:36:37
Writing application              : HandBrake 0.9.3 2008112300

Video
ID                               : 1
Format                           : AVC
Format/Info                      : Advanced Video Codec
Format profile                   : Main@L3.0
Format settings, CABAC           : Yes
Format settings, ReFrames        : 2 frames
Codec ID                         : avc1
Codec ID/Info                    : Advanced Video Coding
Duration                         : 1h 54mn
Bit rate mode                    : Variable
Bit rate                         : 1 500 Kbps
Width                            : 854 pixels
Height                           : 480 pixels
Display aspect ratio             : 16/9
Frame rate mode                  : Variable
Frame rate                       : 23.976 fps
Minimum frame rate               : 19.958 fps
Maximum frame rate               : 350.365 fps
Resolution                       : 24 bits
Colorimetry                      : 4:2:0
Scan type                        : Progressive
Bits/(Pixel*Frame)               : 0.153
Stream size                      : 1.20 GiB (77%)
Writing library                  : x264 core 65
Encoding settings                : cabac=1 / ref=2 / deblock=1:0:0 / analyse=0x1:0x111 / me=umh / subme=6 / psy_rd=1.0:0.0 / mixed_ref=0 / me_range=16 / chroma_me=1 / trellis=0 / 8x8dct=0 / cqm=0 / deadzone=21,11 / chroma_qp_offset=-2 / threads=1 / nr=0 / decimate=1 / mbaff=0 / bframes=2 / b_pyramid=0 / b_adapt=1 / b_bias=0 / direct=1 / wpredb=0 / keyint=240 / keyint_min=24 / scenecut=40 / rc=2pass / bitrate=1500 / ratetol=1.0 / qcomp=0.60 / qpmin=10 / qpmax=51 / qpstep=4 / cplxblur=20.0 / qblur=0.5 / ip_ratio=1.40 / pb_ratio=1.30 / aq=1:1.00
Encoded date                     : UTC 2009-04-05 10:14:06
Tagged date                      : UTC 2009-04-05 18:36:37

Audio
ID                               : 2
Format                           : AC-3
Format/Info                      : Audio Coding 3
Codec ID                         : ac-3
Duration                         : 1h 54mn
Bit rate mode                    : Constant
Bit rate                         : 448 Kbps
Channel(s)                       : 6 channels
Channel positions                : Front: L C R, Surround: L R, LFE
Sampling rate                    : 48.0 KHz
Resolution                       : 16 bits
Stream size                      : 368 MiB (23%)
Language                         : English
Encoded date                     : UTC 2009-04-05 10:14:06
Tagged date                      : UTC 2009-04-05 18:36:35
[/FONT][/INDENT]I'm running on Ubuntu 9.04 and trying to play this under Totem, without much success. The video plays just fine. However, for the audio, Totem tries to look for a plugin for audio/x-gst-fourcc-ac-3 decoder, and can't find it.I've installed pretty much everything I can from the Canonical repositories, as well as from Medibuntu. Here's the relevant package list.
[INDENT] [FONT=Courier New]gstreamer0.10-ffmpeg
gstreamer0.10-pitfdll
gstreamer0.10-schroedinger
gstreamer0.10-tools
gstreamer0.10-pulseaudio
gstreamer0.10-alsa
gstreamer0.10-plugins-base
gstreamer0.10-gnomevfs
gstreamer0.10-plugins-good
gstreamer0.10-x
gstreamer0.10-plugins-base-apps
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse
gnome-codec-install
bluez-gstreamer
gnome-media
libgstreamer0.10-0
libgstreamer-plugins-base0.10-0
gnome-app-install
pidgin
ubuntu-restricted-extras
pulseaudio

libavutil-unstripped-49
libpostproc51
libswscale0
libavcodec-unstripped-52
libavformat52

w32codecs
non-free-codecs
[/FONT][/INDENT]Can someone please help identify what's missing?

Thanks in advance.
-- 
Wiley

---

### Post by wiley.q.hacker on 2009-07-06
Sorry, forgot to mention a few other packages that are also installed:
[INDENT][FONT=Courier New]faac
faad
libfaac0
libfaad0
libmp4v2-0
[/FONT][/INDENT]Still no luck.
-- 
Wiley

---

### Post by tibguyak on 2009-10-01
Hi,
 I had the same issue and when I started searching, yours was the only post which mentioned the issue but no one responding to it! So I decided to post the resolution which I resoved with a workaround. 

Background:-
After upgrading 8.10 to 9.04, I found that totem player (and all media players) which was existing before upgrade were not able to get some libs. for MPEG-4 videos

Workaround:-
 The workaround I am doing is to Install VLC media player.(Go to Synaptic Package Manager and search for VLC and mark for installation. )


All the best.
Cheers,
Abraham

---

### Post by cor2y on 2009-10-01
If you run into a problem with Totem or any other GStreamer based application not being able to play ac3 audio via internal soundcard (no idea about passthrough) - check your sound settings. I've been pulling out my hair for about an hour before I figured out that GStreamer won't playback ac3 when it is set to use ALSA for audio output. Switch  to Pulse or ESD under Preferences -> Sound -> Music And Movies to have a little bit less linux-oddities to worry about. 



I dont know if that will help but its the only explanation i can come up with.
Just tried it myself on my system with alsa enabled no audio for AC-3 switching back to pulse gave me playback

Edit 
I just checked your lists of installed plugins i dont see liba52 (for AC-3 decoding) installed, is that installed also.
If the solution doesnt work have you tried using totem-xine instead of totem-gstreamer to see if its a bug in gstreamer's plugins?

---

