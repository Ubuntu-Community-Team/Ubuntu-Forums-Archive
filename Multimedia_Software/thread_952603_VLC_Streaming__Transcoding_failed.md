---
title: "VLC Streaming / Transcoding failed"
date: 2008-10-19
forum: Multimedia Software
---

### Post by jserrachinha on 2008-10-19
My error:

VLC Streaming / Transcoding failed: VLC could not find encoder "MPEG-2 Video".

I'm using ubuntu 8.10 full updated with allmost medibuntu packages installed. I can play the movie, only i can't streaming.
my command: vlc --intf wxwin --extraintf=http
output: VLC media player 0.9.4 Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.4 Grishenko - (c) 1996-2008 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=x86_64-linux-gnu' '--enable-maintaner-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=1ubuntu3' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-arts' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-x264' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-alsa' '--enable-dv' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=x86_64-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000405] main interface: creating httpd


Thanks in advance,
Joao

:confused:

---

### Post by Wiki_Poster on 2008-11-01
I've got the same problem.

---

### Post by mocho on 2008-11-17
I have exactly the same problem, tired from searching a solution and nothing.

even made a transition from debian to ubuntu hoping that this could be solved, but problem persists.

if you did find a solution please post it.s

regards

---

### Post by aashay on 2008-12-23
bump
Same problem. Trying to encode for rockbox

---

### Post by mocho on 2008-12-23
you need to install Medibuntu non-free codecs

---

### Post by desy83 on 2008-12-23
sorry for crashing this thread could someone please tell me where to post new threads as i have been trying to post this thread below for about an hour?                                                                                                                               I have downloaded gtm- 0.4.12 i tried to install it by system- administration-synaptic package manager i got into the section to add/ remove packages but i don't have a clue how to transfer them. Please could someone help?:confused:

---

### Post by karigrandi on 2009-01-12
> **jserrachinha said:**
> My error:

VLC Streaming / Transcoding failed: VLC could not find encoder "MPEG-2 Video".

I was getting this same error, found a solution and then later on started getting the same error again after some updates by the package manager.

There seems to be quite many dead ends on the net on this particular problem. Finally I found the easy solution for this:

```
apt-get install libavcodec-unstripped-51
```

source:
[https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/281872](https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/281872)

---

