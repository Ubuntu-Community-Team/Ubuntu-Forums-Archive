---
title: "VLC Mozilla Plugin Always Says &quot;Video is Loading...&quot;"
date: 2009-02-06
forum: Multimedia Software
---

### Post by Mr Rough on 2009-02-06
I've tried to switch to using the VLC plugin in Firefox for video to see if it's any better than Totem is. However after removing the Totem plugin and installing the VLC plugin, all WMV are a black box with the text "Video is Loading..." forever.

For a reproducible test, I found [http://home.att.net/~cherokee68/wmvtest2.html]("http://home.att.net/~cherokee68/wmvtest2.html") and this shows this issue. I've attached a screen shot of what I see.

I'm able to view AVI and MPEG files no problem. I'm also able to watch WMV files in the VLC player itself, just not through the plugin. Below is the relevent part of the about:plugins. WMV is enabled and there are no additional plugins for video.

```

audio/mpeg 	MPEG audio 	mp2,mp3,mpga,mpega 	Yes
audio/x-mpeg 	MPEG audio 	mp2,mp3,mpga,mpega 	Yes
video/mpeg 	MPEG video 	mpg,mpeg,mpe 	Yes
video/x-mpeg 	MPEG video 	mpg,mpeg,mpe 	Yes
video/mpeg-system 	MPEG video 	mpg,mpeg,mpe,vob 	Yes
video/x-mpeg-system 	MPEG video 	mpg,mpeg,mpe,vob 	Yes
video/mp4 	MPEG-4 video 	mp4,mpg4 	Yes
audio/mp4 	MPEG-4 audio 	mp4,mpg4 	Yes
application/mpeg4-iod 	MPEG-4 video 	mp4,mpg4 	Yes
application/mpeg4-muxcodetable 	MPEG-4 video 	mp4,mpg4 	Yes
video/x-msvideo 	AVI video 	avi 	Yes
video/quicktime 	QuickTime video 	mov,qt 	Yes
application/x-ogg 	Ogg stream 	ogg 	Yes
application/ogg 	Ogg stream 	ogg 	Yes
application/x-vlc-plugin 	VLC plug-in 	vlc 	Yes
video/x-ms-asf-plugin 	Windows Media Video 	asf,asx 	Yes
video/x-ms-asf 	Windows Media Video 	asf,asx 	Yes
application/x-mplayer2 	Windows Media 		Yes
video/x-ms-wmv 	Windows Media 	wmv 	Yes
video/x-ms-wvx 	Windows Media Video 	wvx 	Yes
application/x-google-vlc-plugin 	Google VLC plug-in 		Yes
audio/wav 	WAV audio 	wav 	Yes
audio/x-wav 	WAV audio 	wav 	Yes
audio/3gpp 	3GPP audio 	3gp,3gpp 	Yes
video/3gpp 	3GPP video 	3gp,3gpp 	Yes
audio/3gpp2 	3GPP2 audio 	3g2,3gpp2 	Yes
video/3gpp2 	3GPP2 video 	3g2,3gpp2 	Yes
video/divx 	DivX video 	divx 	Yes
video/flv 	FLV video 	flv 	Yes
video/x-flv 	FLV video 	flv 	Yes
video/x-matroska 	Matroska video 	mkv 	Yes
audio/x-matroska 	Matroska audio 	mka 	Yes

```

Here is a list of vlc packages:
```

$ dpkg -l | grep vlc
ii  libvlc2                                    0.9.4-1ubuntu3                          multimedia player and streamer library
ii  libvlccore0                                0.9.4-1ubuntu3                          multimedia player and streamer library
ii  mozilla-plugin-vlc                         0.9.4-1ubuntu3                          multimedia plugin for web browsers based on 
ii  vlc                                        0.9.4-1ubuntu3                          multimedia player and streamer
ii  vlc-data                                   0.9.4-1ubuntu3                          Common data for VLC
ii  vlc-nox                                    0.9.4-1ubuntu3                          multimedia player and streamer (without X su
ii  vlc-plugin-pulse                           0.9.4-1ubuntu3                          PulseAudio plugin for VLC

```

Thank you for your time. Any help is appreciated.

---

### Post by redroad55 on 2009-02-06
This guide is awesome . I've used it many times .. there are many tips here .. the only time it didn't work is when I didn't follow the directions ..Give it a try and post back ..Best to you

[http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")

---

### Post by Mr Rough on 2009-02-06
Thank you for your time. However I meant to add that I did go through that thread too :/. Unfortunatetly I already had the things installed that it was asking.

I've now ran Firefox from a gnome-terminal and there is a ton of VLC chatter but it gives this message when I load a WMV

```

*** LibVLC Exception not handled: No active input

```

This only happens on WMVs however. Everything else works fine that I've tried.

I've read that this bug may be related [https://trac.videolan.org/vlc/ticket/2062](https://trac.videolan.org/vlc/ticket/2062) and that this particular bug is resolved in 1.0.0. However I doubt that's what is causing it, or else a lot more people would be asking about this issue than I found.

Does anyone have any additional ideas? Any help is appreciated.

---

### Post by redroad55 on 2009-02-06
What do you get with> vlc -vvpost back

---

### Post by Mr Rough on 2009-02-07
Thank you for your time as well. Here is the output as it loads with vlc -vv

```

VLC media player 0.9.4 Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.4 Grishenko - (c) 1996-2008 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintaner-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=1ubuntu3' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-arts' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-x264' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-alsa' '--enable-dv' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc debug: checking builtin modules
[00000001] main libvlc debug: checking plugin modules
[00000001] main libvlc debug: loading plugins cache file /home/kirk/.cache/vlc/plugins-04041e.dat
[00000001] main libvlc debug: recursively browsing `/usr/lib/vlc'
[00000001] main libvlc debug: module bank initialized, found 272 modules
[00000001] main libvlc debug: opening config file (/home/kirk/.config/vlc/vlcrc)
[00000001] main libvlc debug: CPU has capabilities 486 586 MMX 3DNow! MMXEXT SSE SSE2 FPU 
[00000001] main libvlc debug: looking for memcpy module: 4 candidates
[00000001] main libvlc debug: using memcpy module "memcpymmxext"
[00000370] main interaction debug: thread 3081796496 (Interaction control) created at priority 0 (interface/interaction.c:382)
[00000370] main interaction debug: thread started
[00000372] main input debug: Creating an input for 'Media Library'
[00000372] main input debug: Input is a meta file: disabling unneeded options
[00000372] main input debug: `file/xspf-open:///home/kirk/.local/share/vlc/ml.xspf' gives access `file' demux `xspf-open' path `/home/kirk/.local/share/vlc/ml.xspf'
[00000372] main input debug: creating access 'file' path='/home/kirk/.local/share/vlc/ml.xspf'
[00000373] main access debug: looking for access module: 3 candidates
[00000373] access_mmap access debug: opening file /home/kirk/.local/share/vlc/ml.xspf
[00000373] main access debug: using access module "access_mmap"
[00000373] main access debug: TIMER module_Need() : 0.843 ms - Total 0.843 ms / 1 intvls (Avg 0.843 ms)
[00000377] main stream debug: Using AStream*Block
[00000377] main stream debug: pre buffering
[00000377] main stream debug: received first data for our buffer
[00000373] access_mmap access debug: at end of memory mapped file
[00000372] main input debug: creating demux: access='file' demux='xspf-open' path='/home/kirk/.local/share/vlc/ml.xspf'
[00000378] main demux debug: looking for demux module: 1 candidate
[00000378] playlist demux debug: using XSPF playlist reader
[00000378] main demux debug: using demux module "playlist"
[00000378] main demux debug: TIMER module_Need() : 0.622 ms - Total 0.622 ms / 1 intvls (Avg 0.622 ms)
[00000372] main input debug: `file/xspf-open:///home/kirk/.local/share/vlc/ml.xspf' successfully opened
[00000393] main xml debug: looking for xml module: 2 candidates
[00000393] main xml debug: using xml module "xml"
[00000393] main xml debug: TIMER module_Need() : 1.106 ms - Total 1.106 ms / 1 intvls (Avg 1.106 ms)
[00000373] access_mmap access debug: at end of memory mapped file
[00000378] playlist demux warning: invalid <playlist> attribute:"xmlns:vlc"
[00000378] playlist demux debug: parsed 0 tracks successfully
[00000393] main xml debug: removing module "xml"
[00000372] main input debug: EOF reached
[00000372] main input debug: control type=1
[00000378] main demux debug: removing module "playlist"
[00000373] main access debug: removing module "access_mmap"
[00000372] main input debug: TIMER input launching for 'Media Library' : 5.471 ms - Total 5.471 ms / 1 intvls (Avg 5.471 ms)
[00000395] main preparser debug: waiting for thread initialization
[00000395] main preparser debug: thread started
[00000395] main preparser debug: thread 3070790544 (preparser) created at priority 0 (playlist/thread.c:79)
[00000396] main fetcher debug: waiting for thread initialization
[00000396] main fetcher debug: thread started
[00000396] main fetcher debug: thread 3062397840 (fetcher) created at priority 0 (playlist/thread.c:108)
[00000371] main playlist debug: waiting for thread initialization
[00000371] main playlist debug: thread started
[00000371] main playlist debug: rebuilding array of current - root Playlist
[00000371] main playlist debug: rebuild done - 0 items, index -1
[00000371] main playlist debug: thread 3054005136 (playlist) created at priority 0 (playlist/thread.c:117)
[00000397] main interface debug: looking for interface module: 1 candidate
[00000397] main interface debug: using interface module "hotkeys"
[00000397] main interface debug: TIMER module_Need() : 0.404 ms - Total 0.404 ms / 1 intvls (Avg 0.404 ms)
[00000397] main interface debug: thread 3045612432 (interface) created at priority 0 (interface/interface.c:168)
[00000397] main interface debug: thread started
[00000399] main interface debug: looking for interface module: 1 candidate
[00000399] main interface debug: using interface module "inhibit"
[00000399] main interface debug: TIMER module_Need() : 3.724 ms - Total 3.724 ms / 1 intvls (Avg 3.724 ms)
[00000399] main interface debug: thread started
[00000399] main interface debug: thread 3037219728 (interface) created at priority 0 (interface/interface.c:168)
[00000401] main interface debug: looking for interface module: 1 candidate
[00000401] main interface debug: using interface module "screensaver"
[00000401] main interface debug: TIMER module_Need() : 0.626 ms - Total 0.626 ms / 1 intvls (Avg 0.626 ms)
[00000401] main interface debug: thread started
[00000401] main interface debug: thread 3028827024 (interface) created at priority 0 (interface/interface.c:168)
[00000403] main interface debug: looking for interface module: 22 candidates
[00000403] main interface debug: using interface module "signals"
[00000403] main interface debug: TIMER module_Need() : 0.613 ms - Total 0.613 ms / 1 intvls (Avg 0.613 ms)
[00000403] main interface debug: thread started
[00000403] main interface debug: thread 3012041616 (interface) created at priority 0 (interface/interface.c:168)
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[00000405] main interface debug: looking for interface module: 4 candidates
[00000405] main interface debug: using interface module "qt4"
[00000405] main interface debug: TIMER module_Need() : 36.378 ms - Total 36.378 ms / 1 intvls (Avg 36.378 ms)
[00000405] main interface debug: thread 2985307024 (interface) created at priority 0 (interface/interface.c:168)
[00000405] main interface debug: thread started
[00000405] qt4 interface debug: Error while initializing qt-specific localization

```

Here is the added output as I close it.
```

[00000001] main libvlc debug: removing all interfaces
[00000405] qt4 interface debug: Quitting the Qt4 Interface
[00000405] qt4 interface debug: Destroying the main interface
[00000405] qt4 interface debug: Destroying the Dialog Provider
[00000405] main interface debug: thread ended
[00000405] main interface debug: thread 2985307024 joined (interface/interface.c:188)
[00000405] main interface debug: removing module "qt4"
[00000403] main interface debug: thread ended
[00000403] main interface debug: thread 3012041616 joined (interface/interface.c:188)
[00000403] main interface debug: removing module "signals"
[00000401] main interface debug: thread ended
[00000401] main interface debug: thread 3028827024 joined (interface/interface.c:188)
[00000401] main interface debug: removing module "screensaver"
[00000399] main interface debug: thread ended
[00000399] main interface debug: thread 3037219728 joined (interface/interface.c:188)
[00000399] main interface debug: removing module "inhibit"
[00000397] main interface debug: thread ended
[00000397] main interface debug: thread 3045612432 joined (interface/interface.c:188)
[00000397] main interface debug: removing module "hotkeys"
[00000001] main libvlc debug: removing all services discovery tasks
[00000001] main libvlc debug: removing playlist
[00000371] main playlist debug: saving Media Library to file /home/kirk/.local/share/vlc/ml.xspf
[00000371] main playlist debug: looking for playlist export module: 1 candidate
[00000371] main playlist debug: using playlist export module "export"
[00000371] main playlist debug: TIMER module_Need() : 0.562 ms - Total 0.562 ms / 1 intvls (Avg 0.562 ms)
[00000371] main playlist debug: removing module "export"
[00000395] main preparser debug: thread ended
[00000395] main preparser debug: thread 3070790544 joined (playlist/engine.c:521)
[00000396] main fetcher debug: thread ended
[00000396] main fetcher debug: thread 3062397840 joined (playlist/engine.c:523)
[00000371] main playlist debug: thread ended
[00000371] main playlist debug: thread 3054005136 joined (libvlc.c:992)
[00000395] main preparser debug: Destroyed
[00000396] main fetcher debug: Destroyed
[00000371] main playlist debug: Destroyed
[00000001] main libvlc debug: removing interaction
[00000370] main interaction debug: thread ended
[00000370] main interaction debug: thread 3081796496 joined (interface/interaction.c:400)
[00000001] main libvlc debug: removing all video outputs
[00000001] main libvlc debug: TIMER ML Load : Total 7.309 ms / 1 intvls (Avg 7.309 ms)
[00000001] main libvlc debug: TIMER Items array build : Total 0.049 ms / 1 intvls (Avg 0.049 ms)
[00000001] main libvlc debug: TIMER ML Dump : Total 0.803 ms / 1 intvls (Avg 0.803 ms)
[00000001] main libvlc debug: removing stats
[00000001] main libvlc debug: removing module "memcpymmxext"
[00000001] main libvlc debug: opening config file (/home/kirk/.config/vlc/vlcrc)
[00000001] main libvlc debug: opening config file (/home/kirk/.config/vlc/vlcrc)
[00000001] main libvlc debug: writing plugins cache /home/kirk/.cache/vlc/plugins-04041e.dat

```

Any clues, or ideas on how I can further investigate? Thank you for your time.

---

### Post by redroad55 on 2009-02-07
so this is suspect : 
> [00000405] qt4 interface debug: Error while initializing qt-specific localization
also this will come in handy a list of hot keys for vlc:
[http://wiki.videolan.org/QtHotkeys]("http://wiki.videolan.org/QtHotkeys")
I need to get some sleep now but I'll look over this again in the morning and post back..Best to you

Also in your firefox browser what is the list of plugins you currently have installed

---

