---
title: "VLC crashes and restarts X when trying to play 1080p x264 HD MKV"
date: 2010-02-05
forum: Multimedia Software
---

### Post by oracel on 2010-02-05
When I try to play a x264 1080p movie VLC will go fullscreen, freeze, and crash my X-session.

VLC has default settings all the way. If I switch to OpenGL output it will render the video, however with very low framerate and horrible quality.

Here's the stderr output from VLC when it crashes:

```

VLC media player 0.9.9a Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.9a Grishenko - (c) 1996-2009 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintainer-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=2ubuntu1' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-realrtsp' '--disable-dv' '--enable-x264' '--enable-alsa' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
 m_el[mi_level] == NULL
 arrrrrrrrrrrrrg Up cannot escape itself
[00000453] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:384000
ALSA lib setup.c:555:(add_elem) Cannot obtain info for CTL elem (MIXER,'IEC958 Playback Default',0,0,0): No such file or directory
[00000402] signals interface error: Caught Hangup signal, exiting...
E: client-conf-x11.c: XOpenDisplay() failed
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
<unknown>: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
<unknown>: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.

```

Here's the dmesg output|grep CPU:
```

[    0.010000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.010000] CPU: L2 cache: 1024K
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 0
[    0.614388] CPU0: Intel(R) Pentium(R) D CPU 2.80GHz stepping 07
[    0.010000] Initializing CPU#1
[    0.010000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.010000] CPU: L2 cache: 1024K
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 1
[    0.770318] CPU1: Intel(R) Pentium(R) D CPU 2.80GHz stepping 07
[    0.770332] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.780036] Brought up 2 CPUs

```

And dmesg|grep Intel:
```

[    0.614388] CPU0: Intel(R) Pentium(R) D CPU 2.80GHz stepping 07
[    0.770318] CPU1: Intel(R) Pentium(R) D CPU 2.80GHz stepping 07
[    0.780468] PCI: Found Intel Corporation 945G/GZ/P/PL Express Memory Controller Hub without MMCONFIG support.
[   11.741147] agpgart-intel 0000:00:00.0: Intel 945G Chipset
[   11.992146] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   13.365276] Intel ICH 0000:00:1e.2: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[   13.365389] Intel ICH 0000:00:1e.2: setting latency timer to 64

```

Glxgears gives framerates around 130 fps. glxinfo says Direct Rendering is enabled.

Any ideas?

---

