---
title: "VDPAU and MPlayer"
date: 2011-11-02
forum: Multimedia Software
---

### Post by stingran on 2011-11-02
HELLO all

i am trying to play this command but i don't see any video output.
**mplayer -vo vdpau -vc ffh264vdpau ./filename.mkv**

the video is indeed playing in the terminal (i can also hear the sound of it) but not in a mplayer window.
i am using Ubuntu 11.04 with all updates installed (i do not install 11.10 for purpose).
i have installed the vdpau-va-driver using this:
[B]apt-get install vdpau-va-driver
[/B]
the result of the first mplayer command is below:

[B]MPlayer 1.0rc4-4.5.2 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/essilorapp/app/video/screensaver/optifog.webm.
[mkv] Track ID 1: video (V_VP8), -vid 0
[mkv] Track ID 2: audio (A_VORBIS), -aid 0, -alang und
[mkv] Will play video track 1.
Matroska file format detected.
VIDEO:  [VP80]  1920x1080  24bpp  25.000 fps    0.0 kbps ( 0.0 kbyte/s)
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1
Error opening/initializing the selected video_out (-vo) device.
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, s16le, 0.0 kbit/0.00% (ratio: 0->176400)
Selected audio codec: [ffvorbis] afm: ffmpeg (FFmpeg Vorbis)
==========================================================================
AO: [pulse] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:  18.3 (18.3) of 18.8 (18.7)  1.1% [/B]

can someone tell me where i am doing wrong? what do i miss??!
if i just run this command:

**mplayer -fs ./filename.mkv**

than the video is playing, but not very smooth. 
i don't know what the "fs" stand for, i just picked it up from another thread...

i am using a Foxconn AMD E350 + ATI Radeon HD 6300 (integrated) - it's a nettop PC.
i have installed the ATI driver and it seems to be working, but still the videos are not smooth.

thank you for your quick help... :)

---

### Post by nothingspecial on 2011-11-02
Hi,

Welcome to the forums :)

When you have a question, rather than replying to a thread that is almost 2 years old, make a thread of your own.......

.....which I have done for you.

---

### Post by BicyclerBoy on 2011-11-02
VDPAU is an open std published & used by nVidia to allow video decode etc in h/w.
Only nVidia are using this API.

VA-API is an open source std that hopes to be able to support all h/w.

The vdpau-va library is to allow VA-API to access VDPAU h/w.
This allows programs to support only one video decode interface & (attempt) to work on all h/w (nVidia-VDPAU, AMD-XvBA, intel-VAAPI/DRM)

You are assuming the opposite.
You do not have VDPAU h/w only XvBA.

You must use VAAPI support of mplayer/vlc.
You need to install the VAAPI support for AMD XvBA.
VAAPI is a subset of features & performance of direct VDPAU.

check out:
"splitted desktop systems"
VAAPI or VA-API
XvBA

---

