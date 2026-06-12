---
title: "Streaming &quot;LiveTV&quot;"
date: 2007-12-21
forum: Mythbuntu
---

### Post by Stereotypical Rage on 2007-12-21
Good Evening everyone,

I seem to be having a great deal of difficulty getting a mythTV recording to stream via VLC (would like to stream to friends on the Internet)

```
[00000001] main libvlc debug: VLC media player - version 0.9.0-svn Grishenko - (c) 1996-2007 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--mandir=/share/man' '--host=i486-linux-gnu' '--build=i486-linux-gnu' '--enable-maintaner-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-arts' '--enable-jack' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-wxwidgets' '--with-wx-config=wx-config' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-debug' '--enable-twolame' '--enable-x264' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-x264' '--enable-alsa' '--enable-dv' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-glide' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'host_alias=i486-linux-gnu'
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[00000001] main libvlc debug: translation test: code is "C"
[00000350] inhibit interface error: Failed to connect to the D-Bus session daemon: dbus-launch failed to autolaunch D-Bus session: Autolaunch error: X11 initialization failed.

[00000350] main interface error: no suitable interface module
[00000001] main libvlc error: interface "inhibit,none" initialization failed
[00000352] main interface: creating httpd
[00000360] access_output_http private error: cannot add stream /
[00000359] stream_out_standard private error: no suitable sout access module for `mmsh/asfh://(null)'
[00000357] stream_out_transcode private error: cannot create chain
[00000356] main stream output error: stream chain failed for `transcode{vcodec=DIV3,acodec=MPGA,vb=500,ab=128,scale=1}:std{access=mmsh,mux=ogg,url=:8001}'
[00000355] main input error: cannot start stream output instance, aborting
```

I don't understand what certain errors are mainly these lines....

```
[00000360] access_output_http private error: cannot add stream /
[00000359] stream_out_standard private error: no suitable sout access module for `mmsh/asfh://(null)'
```

If there is anyone out there that can point me in the right direction, that would be greatly appreciated.

---

