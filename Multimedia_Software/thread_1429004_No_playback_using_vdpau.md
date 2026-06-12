---
title: "No playback using vdpau"
date: 2010-03-13
forum: Multimedia Software
---

### Post by cchhrriiss121212 on 2010-03-13
When playing 720p video I get out of sync audio and occasional glitches, so I tried to enable vdpau playback using this guide:[http://ubuntuforums.org/showthread.php?t=1037625&page=15](http://ubuntuforums.org/showthread.php?t=1037625&page=15)

I have a 9600gt with driver version 190 installed. I get no video with vdpau, and this output form the terminal:

```
[mkv] Track ID 1: video (V_MPEG4/ISO/AVC), -vid 0
[mkv] Track ID 2: audio (A_AC3), -aid 0, -alang und
[mkv] Will play video track 1.
Matroska file format detected.
VIDEO:  [avc1]  1280x720  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
NVIDIA: could not open the device file /dev/nvidiactl (Permission denied).
[vdpau] Error when calling vdp_device_create_x11: 1
Error opening/initializing the selected video_out (-vo) device.
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 448.0 kbit/29.17% (ratio: 56000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
[pulse] working around probably broken pause functionality,
        see http://www.pulseaudio.org/ticket/440
E: context.c: waitpid(): No child processes
AO: [pulse] Init failed: Internal error
Failed to initialize audio driver 'pulse'
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
```It gives a permission error but I am a part of the video group. Using sudo to play the file also gives this:
Forced video codec: ffh264vdpau
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Cannot find codec 'h264_vdpau' in libavcodec...
VDecoder init failed :(
Cannot find codec matching selected -vo and video format 0x31637661.
Read DOCS/HTML/en/codecs.html!

Could anyone help? All similar posts I have seen on here are unresolved. I have also tried to compile mplayer with multi-threading which does not seem to be a solution.

---

### Post by cchhrriiss121212 on 2010-03-15
Anyone?

---

### Post by AdrianVeidt on 2010-03-15
Add yourself to the "video" group, sir. This is done by the nvidia driver packaging scripts when the driver is installed, but for whatever reason it sometimes fails.

---

### Post by cchhrriiss121212 on 2010-03-15
I'm using crunchbang which does not have a video group by default. I made one and added my self to it but no change.

---

### Post by cchhrriiss121212 on 2010-03-20
I have now tried reinstalling everything but the root partition. This is probably a simple fix but I just don't know what it is.

---

### Post by cchhrriiss121212 on 2010-03-26
Seems to be working for me now. For anyone else here is what I had to do:

Install libavcodec-unstripped-52 and libavutil-unstripped-49 which will replace other versions.
Install libfaad2 after downgrading libfaad0 (force 2.61 from menu).
Updating the nvidia ppa, and installing latest versions of mplayer and libvdpau.
Using chmod 777 on nvidiactl and nvidia0 in /dev.
Disable post processing and multi threading.
Add this into smplayer preferences>advanced>options for mplayer>options:
-vc ffmpeg12vdpau,ffh264vdpau,ffwmv3vdpau,ffvc1vdpau,

---

