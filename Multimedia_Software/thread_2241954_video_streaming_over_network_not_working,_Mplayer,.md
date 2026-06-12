---
title: "video streaming over network not working, Mplayer, Netcat"
date: 2014-08-29
forum: Multimedia Software
---

### Post by msousa on 2014-08-29
Hi

I'm trying to view video from my raspberry pi camera over a network connection. I was able to do this a few months ago (around Feb-March) but it does not seem to work now.

The command I run from the pi is:
```
pi@raspberrypi ~ $ raspivid -t 999999 -o - | nc 10.42.0.1 5001
```

The command I run on my Ubuntu 12.04 laptop is:
```
raspberry_pi/camera$ nc.traditional -l -p 5001 | mplayer -fps 31 -cache 1024 -
```

I then let it sit for awhile and then ^C it on the Ubuntu laptop. The output from mplayer is shown below. When I ^C, it also briefly shows the camera output on the sreen (very briefly) and goes away.
```
raspberry_pi/camera$ nc.traditional -l -p 5001 | mplayer -fps 31 -cache 1024 -
MPlayer svn r34540 (Ubuntu), built with gcc-4.6 (C) 2000-2012 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing -.
Reading from stdin...
Cache fill:  0.39% (4096 bytes)   ^C

MPlayer interrupted by signal 2 in module: enable_cache

MPlayer interrupted by signal 2 in module: enable_cache
Cache fill:  0.39% (4096 bytes)   

libavformat version 53.21.1 (external)
Mismatching header version 53.19.0
libavformat file format detected.
[h264 @ 0x7f24abb1f3c0]error while decoding MB 66 28, bytestream (-8)
[h264 @ 0x7f24abb1f3c0]concealing 4783 DC, 4783 AC, 4783 MV errors
[h264 @ 0x7f24ac3a3940]Estimating duration from bitrate, this may be inaccurate
[lavf] stream 0: video (h264), -vid 0
VIDEO:  [H264]  1920x1080  0bpp  25.000 fps    0.0 kbps ( 0.0 kbyte/s)
Load subtitles in ./
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1
[VO_XV] It seems there is no Xvideo support for your video card available.
[VO_XV] Run 'xvinfo' to verify its Xv support and read
[VO_XV] DOCS/HTML/en/video.html#xv!
[VO_XV] See 'mplayer -vo help' for other (non-xv) video out drivers.
[VO_XV] Try -vo x11.
X11 error: BadRequest (invalid request code or no such operation)
X11 error: BadRequest (invalid request code or no such operation)
X11 error: BadRequest (invalid request code or no such operation)
[gl] no GLX support present
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
libavcodec version 53.35.0 (external)
Mismatching header version 53.32.2
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
Audio: no sound
FPS forced to be 31.000  (ftime: 0.032).
Starting playback...
Unsupported PixelFormat 61
Unsupported PixelFormat 53
Unsupported PixelFormat 81
[h264 @ 0x7f24abb1f3c0]error while decoding MB 66 28, bytestream (-8)
[h264 @ 0x7f24abb1f3c0]concealing 4783 DC, 4783 AC, 4783 MV errors
Movie-Aspect is undefined - no prescaling applied.
VO: [x11] 1920x1080 => 1920x1080 Planar YV12 
[swscaler @ 0x7f24ac5f8120]using unscaled yuv420p -> bgra special converter
V:   0.0   1/  1 ??% ??% ??,?% 0 0 0% 

Exiting... (Quit)
raspberry_pi/camera$ 
```

Any help with this would be appreciated.

Thanks...

---

### Post by msousa on 2014-08-29
A couple of updates I've discovered. I am able to create a video from the camera and copy it over to the Ubuntu laptop and view it with mplayer2. I redirect the stderr to a file and here's some of the output:

```
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
[h264 @ 0x7f52a6055940]Estimating duration from bitrate, this may be inaccurate
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1
[VO_XV] It seems there is no Xvideo support for your video card available.
[VO_XV] Run 'xvinfo' to verify its Xv support and read
[VO_XV] DOCS/HTML/en/video.html#xv!
[VO_XV] See 'mplayer -vo help' for other (non-xv) video out drivers.
[VO_XV] Try -vo x11.
X11 error: BadRequest (invalid request code or no such operation)
X11 error: BadRequest (invalid request code or no such operation)
X11 error: BadRequest (invalid request code or no such operation)
[gl] no GLX support present
Colorspace details not fully supported by selected vo.
No pts value from demuxer to use for frame!
Video pts after filters MISSING

No pts value from demuxer to use for frame!
Video pts after filters MISSING

No pts value from demuxer to use for frame!
Video pts after filters MISSING


```
The two lines that repeat go on for quite a long time.

Here's mplayer2 running along with its output:
```
mike@mike-Aspire-7535:~/electronics/raspberry_pi$ mplayer vid.h264 2> mplayer2.txt
MPlayer2 UNKNOWN (C) 2000-2011 MPlayer Team

Playing vid.h264.
Detected file format: raw H.264 video format (libavformat)
[lavf] stream 0: video (h264), -vid 0
VIDEO:  [H264]  1920x1080  0bpp  25.000 fps    0.0 kbps ( 0.0 kbyte/s)
Load subtitles in .
[ass] auto-open
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Asking decoder to use 2 threads if supported.
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
Audio: no sound
Starting playback...
V:   0.0   0/  0 ??% ??% ??,?% 0 0 
Movie-Aspect is undefined - no prescaling applied.
VO: [x11] 1920x1080 => 1920x1080 Planar YV12 
[swscaler @ 0x7f52a5d63120]using unscaled yuv420p -> bgra special converter
V:-9223372036854775808.0   0/  0 ??% ??% ??,?% 0 0 


Exiting... (End of file)


```
The video is about 5 seconds long, hence the end of file.

It still does not work when trying to view the video over the network, as originally stated above. Anything especially look out-of-whack?

Thanks...

---

### Post by msousa on 2014-08-30
Alright, I think I found something. I switched out one of the usb cables  and the pi camera worked and I was able to view its video on my laptop  again. I did this for both of them and both worked.

Must be a power  thing due to the usb cables wearing out? What is life expectancy for  them? I have been removing them frequently to power up/down the pi's. I  may have to rethink that process.

---

