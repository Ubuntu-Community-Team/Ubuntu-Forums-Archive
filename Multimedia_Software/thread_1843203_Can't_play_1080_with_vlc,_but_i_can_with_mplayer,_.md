---
title: "Can't play 1080 with vlc, but i can with mplayer, why?"
date: 2011-09-13
forum: Multimedia Software
---

### Post by juanmol on 2011-09-13
Hi, i don't know why before i can play smoothly 1080 h264 mkv videos and now i can't. It's the same computer dual core atom and ion2, but i had to reinstall it for other non-relacionated problems. I don't remenber what i did to play these files, but now i can't. I've try whith the same videos and play very bad, choopy . Works if i use mplayer, but i really need vlc. Info:

$ vainfo
libva: libva version 0.32.0
Xlib: extension "XFree86-DRI" missing on display ":0.0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/dri/nvidia_drv_video.so
libva: va_openDriver() returns 0
vainfo: VA API version: 0.32
vainfo: Driver version: Splitted-Desktop Systems VDPAU backend for VA-API - 0.7.3
vainfo: Supported profile and entrypoints
VAProfileMPEG2Simple : VAEntrypointVLD
VAProfileMPEG2Main : VAEntrypointVLD
VAProfileMPEG4Simple : VAEntrypointVLD
VAProfileMPEG4AdvancedSimple : VAEntrypointVLD
VAProfileH264Main : VAEntrypointVLD
VAProfileH264High : VAEntrypointVLD
VAProfileVC1Simple : VAEntrypointVLD
VAProfileVC1Main : VAEntrypointVLD
VAProfileVC1Advanced : VAEntrypointVLD

$ vlc --version
VLC media player 1.1.9 The Luggage (revision exported)
Version de VLC 1.1.9 The Luggage (exported)
Compilado por buildd en vernadsky.buildd (Jul 21 2011 11:32:22)
Compilador: gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu4)

$ uname -a
Linux mediacenter 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:05:14 UTC 2011 i686 i686 i386 GNU/Linux


I've activated all options to have accelerated video, what can i do?

$mplayer -vo vdpau -vc ffh264vdpau path/to/file
fine, 6% of CPU and xorg at 4%

$vlc path/to/file
jumps, vlc at 120% and xorg at 80%

Y really need VLC,i'm in love with the web interface to control it with my android. Please help me.

---

