---
title: "no video output in vlc"
date: 2009-07-30
forum: Multimedia Software
---

### Post by drskartik on 2009-07-30
I have ubuntu Hardy 8.04, have installed vlc 0.9.9,
however when I play the video files there is no video output though the audio plays perfectly well.
i have tried default video output as well as open GL output.
This is the output i have on running vlc in terminal

[00000001] main libvlc debug: VLC media player - version 0.9.9a Grishenko - (c) 1996-2009 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintaner-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=1~ppa1~hardy2' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-arts' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' [CODE]'--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-x264' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-alsa' '--enable-dv' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.

where could be the problem?
thanks and regards,
Kartik

---

### Post by mc4man on 2009-07-30
First a couple of small things, maybe irrelevant

When changing versions you should remove all of the previous one. So I'd look in the home folder (show hidden files) and delete the .vlc folder.

Search vlc in synaptic and if any packages show ..0.8.6... in the version then remove them also (libvlc0 is a likely one

If changing anything in preferences your are clicking the save button? (otherwise nothing changes.

I'd also try Xv and or X11 as video outputs. 

Are you getting a video window with nothing in it or is vlc staying in player mode? (like you were playing an audio file

To produce some debugging output in the terminal start vlc with a -vv
vlc -vv

For a one time reset with debugging use this

```
vlc -vv --reset-config --reset-plugins-cache
```

If posting the debug it may be large, put in a quote box in reply (highlight text and click on the quote icon in the reply toolbar

Edit: after starting vlc with debugging try to play a video so the output reflects what happens

---

### Post by drskartik on 2009-07-30
Thanks Mc4man,
The video output has started running after perfromig the reset with debugging
regards
Kartik

---

