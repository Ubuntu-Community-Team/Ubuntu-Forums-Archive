---
title: "mplayer xv doesn't work - karmic"
date: 2009-11-01
forum: Multimedia Software
---

### Post by linuxrockz on 2009-11-01
Hi everybody I have recently clean installed karmic koala. Eveything seems to be fine except the video playback in mplayer and vlc, in jaunty it worked like a charm. I am posting the various outputs that may help you to diagnose my problem. 

mplayer output

```
MPlayer SVN-r29237-4.4.1 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing sha.flv.
libavformat file format detected.
[lavf] Video stream found, -vid 0
[lavf] Audio stream found, -aid 1
VIDEO:  [FLV1]  320x240  0bpp  30.000 fps  270.6 kbps (33.0 kbyte/s)
[VO_XV] It seems there is no Xvideo support for your video card available.
[VO_XV] Run 'xvinfo' to verify its Xv support and read
[VO_XV] DOCS/HTML/en/video.html#xv!
[VO_XV] See 'mplayer -vo help' for other (non-xv) video out drivers.
[VO_XV] Try -vo x11.
Error opening/initializing the selected video_out (-vo) device.
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 22050 Hz, 2 ch, s16le, 64.0 kbit/9.07% (ratio: 8000->88200)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
[pulse] working around probably broken pause functionality,
        see http://www.pulseaudio.org/ticket/440
AO: [pulse] 22050Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
```

Output of lspci

```
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
```

Output of xvinfo
```
X-Video Extension version 2.2
screen #0
 no adaptors present
```

VLC also doesnt play any video:( 

Audio works fine and totem xine is able to play videos.

Please help.

---

### Post by linuxrockz on 2009-11-01
Got VLC working with this command

vlc --reset-config --reset-plugins-cache

But no luck with mplayer please help

---

### Post by Rochendil on 2009-11-21
Hello guys,

I have VLC, mplayer and smplayer working now. Actually it was quite simple. I have opened VLC and I went to "preferences" - "video" and in the "output" dropbox I chose "OpenGL video output". Et voilá

In mplayer and smplayer it's exactly the same thing. When you open the preferences menu, you go to "video" and then change the "xv" option to "gl" and it will work. At least it did for me.



Long live Linux!

Cheers

---

