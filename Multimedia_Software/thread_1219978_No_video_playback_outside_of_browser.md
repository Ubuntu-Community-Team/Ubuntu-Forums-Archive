---
title: "No video playback outside of browser"
date: 2009-07-22
forum: Multimedia Software
---

### Post by jwaclawsky on 2009-07-22
I just installed 9.04 two days ago on my Dell mini 9. I appear to have a problem with playing videos. Whenever I start a video the video screen opens and then promptly shuts down. I tried different file types including flash. Yet the videos work ok within the browser - YouTube works fine for example.

Can someone give me some guidance on how to go about trouble shooting this video situation? The files I tested are .wmv, .mpg .asf and .avi (I tried different file types). All these files worked on my previous 8.04 Ubuntu system. The problem happens with both movie player and VLC media player and other players. You actually hear a snippet of the file beginning to play with VLC and then the window disappears/closes. I tried it with a DVD movie and got the same result. I opened VLC in a terminal and got the following error: 

[????????] x11 video output error: X11 request 132.19 failed with error code 11:
 BadAlloc (insufficient resources for operation)
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  132 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  81
  Current serial number in output stream:  82

BTW, ...my Skype video isn't working either, people can see me but I can't see them (it may be, and probably is, something system related)

When I ran mplayer in the terminal I got: 

jgw@jgw-netbook:~$ mplayer Videos/GrannyAirBag.wmv
MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Atom(TM) CPU N270   @ 1.60GHz (Family: 6, Model: 28, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing Videos/GrannyAirBag.wmv.
ASF file format detected.
[asfheader] Audio stream found, -aid 1
[asfheader] Video stream found, -vid 2
VIDEO:  [WMV1]  320x240  24bpp  1000.000 fps  198.0 kbps (24.2 kbyte/s)
Clip info:
 name: 
 author: 
 copyright: 
 comments: 
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffwmv1] vfm: ffmpeg (FFmpeg M$ WMV1/WMV7)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 22050 Hz, 2 ch, s16le, 20.0 kbit/2.84% (ratio: 2501->88200)
Selected audio codec: [ffwmav2] afm: ffmpeg (DivX audio v2 (FFmpeg))
==========================================================================
AO: [pulse] 22050Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 320 x 240 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 320x240 => 320x240 Planar YV12 
X11 error: BadAlloc (insufficient resources for operation)?,?% 3 0 
X11 error: BadAlloc (insufficient resources for operation)
X11 error: BadAlloc (insufficient resources for operation)
X11 error: BadAlloc (insufficient resources for operation)
X11 error: BadAlloc (insufficient resources for operation)
X11 error: BadAlloc (insufficient resources for operation)
X11 error: BadAlloc (insufficient resources for operation)0.5% 3 0 
X11 error: BadAlloc (insufficient resources for operation)
X11 error: BadAlloc (insufficient resources for operation)0.8% 3 0 
X11 error: BadAlloc (insufficient resources for operation)0.7% 3 0 
X11 error: BadAlloc (insufficient resources for operation)1.0% 3 0 
X11 error: BadAlloc (insufficient resources for operation)0.9% 3 0 
X11 error: BadAlloc (insufficient resources for operation)1.1% 3 0 
X11 error: BadAlloc (insufficient resources for operation)1.0% 3 0 
X11 error: BadAlloc (insufficient resources for operation)1.0% 3 0 
X11 error: BadAlloc (insufficient resources for operation)1.0% 3 0 
X11 error: BadAlloc (insufficient resources for operation)1.0% 3 0 
X11 error: BadAlloc (insufficient resources for operation)0.9% 3 0 
X11 error: BadAlloc (insufficient resources for operation)0.9% 3 0 
X11 error: BadAlloc (insufficient resources for operation)1.0% 3 0 
X11 error: BadAlloc (insufficient resources for operation)0.9% 3 0 
X11 error: BadAlloc (insufficient resources for operation)0.8% 3 0 
X11 error: BadAlloc (insufficient resources for operation)
X11 error: BadAlloc (insufficient resources for operation)0.9% 3 0 
X11 error: BadAlloc (insufficient resources for operation)
X11 error: BadAlloc (insufficient resources for operation)0.9% 3 0 
X11 error: BadAlloc (insufficient resources for operation)0.8% 3 0 
X11 error: BadAlloc (insufficient resources for operation)0.8% 3 0 
X11 error: BadAlloc (insufficient resources for operation)0.9% 3 0 
X11 error: BadAlloc (insufficient resources for operation)0.9% 3 0 
X11 error: BadAlloc (insufficient resources for operation)0.8% 3 0 
X11 error: BadAlloc (insufficient resources for operation)0.8% 3 0 
X11 error: BadAlloc (insufficient resources for operation)0.8% 3 0 
X11 error: BadAlloc (insufficient resources for operation)0.8% 3 0 
X11 error: BadAlloc (insufficient resources for operation)0.8% 3 0 
X11 error: BadAlloc (insufficient resources for operation)0.8% 3 0 
X11 error: BadAlloc (insufficient resources .... etc. 

The X11 errors continued while the screen was blank and the audio played.

I tried Dragon player and got the same result where the screen was blank and the audio played while error messages came out one after the other until I shut down the video. See below:

jgw@jgw-netbook:~$ dragon
dragonplayer(10117) Phonon::KdePlatformPlugin::createBackend: using backend:  "GStreamer"
Object::connect: No such signal Phonon::Gstreamer::MediaObject::availableSubtitlesChanged() in /build/buildd/phonon-4.3.1/phonon/mediacontroller.cpp:57
Object::connect: No such signal Phonon::Gstreamer::MediaObject::availableAudioChannelsChanged() in /build/buildd/phonon-4.3.1/phonon/mediacontroller.cpp:58
Object::connect: No such signal Phonon::Gstreamer::MediaObject::titleChanged(int) in /build/buildd/phonon-4.3.1/phonon/mediacontroller.cpp:59
Object::connect: No such signal Phonon::Gstreamer::MediaObject::availableTitlesChanged(int) in /build/buildd/phonon-4.3.1/phonon/mediacontroller.cpp:60
Object::connect: No such signal Phonon::Gstreamer::MediaObject::chapterChanged(int) in /build/buildd/phonon-4.3.1/phonon/mediacontroller.cpp:61
Object::connect: No such signal Phonon::Gstreamer::MediaObject::availableChaptersChanged(int) in /build/buildd/phonon-4.3.1/phonon/mediacontroller.cpp:62
Object::connect: No such signal Phonon::Gstreamer::MediaObject::angleChanged(int) in /build/buildd/phonon-4.3.1/phonon/mediacontroller.cpp:63
Object::connect: No such signal Phonon::Gstreamer::MediaObject::availableAnglesChanged(int) in /build/buildd/phonon-4.3.1/phonon/mediacontroller.cpp:64
Object::connect: No such signal Phonon::Gstreamer::MediaObject::availableSubtitlesChanged() in /build/buildd/phonon-4.3.1/phonon/mediacontroller.cpp:57
Object::connect: No such signal Phonon::Gstreamer::MediaObject::availableAudioChannelsChanged() in /build/buildd/phonon-4.3.1/phonon/mediacontroller.cpp:58
Object::connect: No such signal Phonon::Gstreamer::MediaObject::titleChanged(int) in /build/buildd/phonon-4.3.1/phonon/mediacontroller.cpp:59
Object::connect: No such signal Phonon::Gstreamer::MediaObject::availableTitlesChanged(int) in /build/buildd/phonon-4.3.1/phonon/mediacontroller.cpp:60
Object::connect: No such signal Phonon::Gstreamer::MediaObject::chapterChanged(int) in /build/buildd/phonon-4.3.1/phonon/mediacontroller.cpp:61
Object::connect: No such signal Phonon::Gstreamer::MediaObject::availableChaptersChanged(int) in /build/buildd/phonon-4.3.1/phonon/mediacontroller.cpp:62
Object::connect: No such signal Phonon::Gstreamer::MediaObject::angleChanged(int) in /build/buildd/phonon-4.3.1/phonon/mediacontroller.cpp:63
Object::connect: No such signal Phonon::Gstreamer::MediaObject::availableAnglesChanged(int) in /build/buildd/phonon-4.3.1/phonon/mediacontroller.cpp:64
dragonplayer(10117): Attempt to use QAction "aspect_ratio_menu" with KXMLGUIFactory! 
dragonplayer(10117): Attempt to use QAction "audio_channels_menu" with KXMLGUIFactory! 
dragonplayer(10117): Attempt to use QAction "subtitle_channels_menu" with KXMLGUIFactory! 
DMO dll supports VO Optimizations 0 1
DMO dll might use previous sample when requested
X Error: BadAlloc (insufficient resources for operation) 11
  Extension:    132 (Uknown extension)
  Minor opcode: 19 (Unknown request)
  Resource id:  0x4800002
X Error: BadAlloc (insufficient resources for operation) 11
  Extension:    132 (Uknown extension)
  Minor opcode: 19 (Unknown request)
  Resource id:  0x4800002
X Error: BadAlloc (insufficient resources for operation) 11
  Extension:    132 (Uknown extension)
  Minor opcode: 19 (Unknown request)
  Resource id:  0x4800002
X Error: BadAlloc (insufficient resources for operation) 11
  Extension:    132 (Uknown extension)
  Minor opcode: 19 (Unknown request)
  Resource id:  0x4800002
X Error: BadAlloc (insufficient resources for operation) 11
  Extension:    132 (Uknown extension)
  Minor opcode: 19 (Unknown request)
  Resource id:  0x4800002
X Error: BadAlloc (insufficient resources for operation) 11
  Extension:    132 (Uknown extension)
  Minor opcode: 19 (Unknown request)
  Resource id:  0x4800002
X Error: BadAlloc (insufficient resources for operation) 11
  Extension:    132 (Uknown extension)
  Minor opcode: 19 (Unknown request)
  Resource id:  0x4800002
X Error: BadAlloc (insufficient resources for operation) 11
  Extension:    132 (Uknown extension)
  Minor opcode: 19 (Unknown request)
  Resource id:  0x4800002
X Error: BadAlloc (insufficient resources for operation) 11
  Extension:    132 (Uknown extension)
  ....etc. 


 All these videos worked the other day under my 8.04 system. Any help would be appreciated. Many Thanks!

---

### Post by igorzwx on 2009-07-22
** 	[COLOR=#980101][B][ubuntu]**[/COLOR] mplayer playback problems  [/B]
[http://ubuntuforums.org/showthread.php?t=1219202](http://ubuntuforums.org/showthread.php?t=1219202)

---

### Post by binbash on 2009-07-22
VO: [xv] 320x240 => 320x240 Planar YV12 

change video output to X11 instead of xv from your video players preference

---

### Post by jwaclawsky on 2009-07-22
> **igorzwx said:**
> ** 	[COLOR=#980101][B][ubuntu]**[/COLOR] mplayer playback problems  [/B]
[http://ubuntuforums.org/showthread.php?t=1219202](http://ubuntuforums.org/showthread.php?t=1219202)

I don't think that is my problem because all video playback sees this insufficient resources message "X11" (what ever that is) I did everything at the link at [http://shibuvarkala.blogspot.com/2009/04/howto-make-ubuntu-904-jaunty-jackalope.html](http://shibuvarkala.blogspot.com/2009/04/howto-make-ubuntu-904-jaunty-jackalope.html) and I still have the sane problem

---

### Post by jwaclawsky on 2009-07-22
> **binbash said:**
> VO: [xv] 320x240 => 320x240 Planar YV12 

change video output to X11 instead of xv from your video players preference

How do I do this in VLC? ...for example. I don't see this in VLC. I am using VLC media player 0.9.9a Grishenko?

---

### Post by jwaclawsky on 2009-07-22
Ok, I found the VLC location to change the output to X11 and I was able to play my videos but the output was not very high quality. I was able to run at full screen mode if I wanted in 8.04 but now they are choppy with the screen being painted on larger sized windows (and full screen) on playback. I can't seem to find any similar control to get mplayer working. I suspect by using X11 output in VLC I am just compensating for a problem/configuration issue and I might be bypassing a bigger system problem since all my video players are effected and they all worked well (on 8.04) before at full screen. Does anyone have any suggestions?

---

### Post by xc3RnbFO8P on 2009-07-24
If you are using Compiz, try in Settings> Preferences>Compiz Config Settings Manager, under general tab, uncheck **Unredirect Fullscreen**.

---

### Post by jwaclawsky on 2009-07-24
I went to the Compiz Config Settings Manager, and under the general tab, and will uncheck the value to see if it helps any. I seem to have gotten most of my problems resolved. Mplayer still doesn't work, however. Maybe this will help. Thanks

---

### Post by banato on 2009-07-24
This might help if you have an Intel graphics card:

[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

---

