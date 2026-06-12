---
title: "VLC system font problem"
date: 2009-03-19
forum: Multimedia Software
---

### Post by global_dev on 2009-03-19
VLC seems to have installed w/o issue except for the menu/dialogue font as seen in the attached pic.

anyone have a suggestion? no other app has this issue

Ubu 9.04 
VLC 0.9.8a

When running from CLI, vlc -vvv
VLC media player 0.9.8a Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.8a Grishenko - (c) 1996-2008 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintaner-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=1ubuntu4' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-realrtsp' '--enable-x264' '--enable-alsa' '--enable-dv' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc debug: checking builtin modules
[00000001] main libvlc debug: checking plugin modules
[00000001] main libvlc debug: loading plugins cache file /home/jonathan/.cache/vlc/plugins-04041e.dat
[00000001] main libvlc debug: recursively browsing `/usr/lib/vlc'
[00000001] main libvlc debug: module bank initialized, found 273 modules
[00000001] main libvlc debug: opening config file (/home/jonathan/.config/vlc/vlcrc)
[00000001] main libvlc debug: CPU has capabilities 486 586 MMX MMXEXT SSE SSE2 FPU 
[00000001] main libvlc debug: looking for memcpy module: 3 candidates
[00000001] main libvlc debug: using memcpy module "memcpymmxext"
[00000370] main interaction debug: thread started
[00000370] main interaction debug: thread 3080829840 (Interaction control) created at priority 0 (interface/interaction.c:382)
[00000372] main input debug: Creating an input for 'Media Library'
[00000372] main input debug: Input is a meta file: disabling unneeded options
[00000372] main input debug: `file/xspf-open:///home/jonathan/.local/share/vlc/ml.xspf' gives access `file' demux `xspf-open' path `/home/jonathan/.local/share/vlc/ml.xspf'
[00000372] main input debug: creating access 'file' path='/home/jonathan/.local/share/vlc/ml.xspf'
[00000373] main access debug: looking for access module: 3 candidates
[00000373] access_file access debug: opening file `/home/jonathan/.local/share/vlc/ml.xspf'
[00000373] main access debug: using access module "access_file"
[00000373] main access debug: TIMER module_Need() : 1.196 ms - Total 1.196 ms / 1 intvls (Avg 1.196 ms)
[00000378] main stream debug: Using AStream*Stream
[00000378] main stream debug: pre-buffering...
[00000378] main stream debug: received first data for our buffer
[00000372] main input debug: creating demux: access='file' demux='xspf-open' path='/home/jonathan/.local/share/vlc/ml.xspf'
[00000379] main demux debug: looking for demux module: 1 candidate
[00000379] playlist demux debug: using XSPF playlist reader
[00000379] main demux debug: using demux module "playlist"
[00000379] main demux debug: TIMER module_Need() : 0.560 ms - Total 0.560 ms / 1 intvls (Avg 0.560 ms)
[00000372] main input debug: `file/xspf-open:///home/jonathan/.local/share/vlc/ml.xspf' successfully opened
[00000394] main xml debug: looking for xml module: 2 candidates
[00000394] main xml debug: using xml module "xml"
[00000394] main xml debug: TIMER module_Need() : 0.958 ms - Total 0.958 ms / 1 intvls (Avg 0.958 ms)
[00000379] playlist demux debug: parsed 0 tracks successfully
[00000394] main xml debug: removing module "xml"
[00000372] main input debug: EOF reached
[00000372] main input debug: control type=1
[00000379] main demux debug: removing module "playlist"
[00000373] main access debug: removing module "access_file"
[00000372] main input debug: TIMER input launching for 'Media Library' : 21.266 ms - Total 21.266 ms / 1 intvls (Avg 21.266 ms)
[00000396] main preparser debug: thread started
[00000396] main preparser debug: waiting for thread initialization
[00000396] main preparser debug: thread 3072420752 (preparser) created at priority 0 (playlist/thread.c:79)
[00000397] main fetcher debug: thread started
[00000397] main fetcher debug: waiting for thread initialization
[00000397] main fetcher debug: thread 3058285456 (fetcher) created at priority 0 (playlist/thread.c:108)
[00000371] main playlist debug: thread started
[00000371] main playlist debug: waiting for thread initialization
[00000371] main playlist debug: rebuilding array of current - root Playlist
[00000371] main playlist debug: rebuild done - 0 items, index -1
[00000371] main playlist debug: thread 3049892752 (playlist) created at priority 0 (playlist/thread.c:117)
[00000398] main interface debug: looking for interface module: 1 candidate
[00000398] main interface debug: using interface module "hotkeys"
[00000398] main interface debug: TIMER module_Need() : 0.518 ms - Total 0.518 ms / 1 intvls (Avg 0.518 ms)
[00000398] main interface debug: thread started
[00000398] main interface debug: thread 3041500048 (interface) created at priority 0 (interface/interface.c:168)
[00000400] main interface debug: looking for interface module: 1 candidate
[00000400] main interface debug: using interface module "inhibit"
[00000400] main interface debug: TIMER module_Need() : 13.238 ms - Total 13.238 ms / 1 intvls (Avg 13.238 ms)
[00000400] main interface debug: thread started
[00000400] main interface debug: thread 3033107344 (interface) created at priority 0 (interface/interface.c:168)
[00000402] main interface debug: looking for interface module: 1 candidate
[00000402] main interface debug: using interface module "screensaver"
[00000402] main interface debug: TIMER module_Need() : 0.516 ms - Total 0.516 ms / 1 intvls (Avg 0.516 ms)
[00000402] main interface debug: thread started
[00000402] main interface debug: thread 3024714640 (interface) created at priority 0 (interface/interface.c:168)
[00000404] main interface debug: looking for interface module: 22 candidates
[00000404] main interface debug: using interface module "signals"
[00000404] main interface debug: TIMER module_Need() : 0.382 ms - Total 0.382 ms / 1 intvls (Avg 0.382 ms)
[00000404] main interface debug: thread started
[00000404] main interface debug: thread 3007929232 (interface) created at priority 0 (interface/interface.c:168)
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[00000406] main interface debug: looking for interface module: 4 candidates
[00000406] main interface debug: using interface module "qt4"
[00000406] main interface debug: TIMER module_Need() : 413.335 ms - Total 413.335 ms / 1 intvls (Avg 413.335 ms)
[00000406] main interface debug: thread started
[00000406] main interface debug: thread 2985016208 (interface) created at priority 0 (interface/interface.c:168)
[00000406] qt4 interface debug: Error while initializing qt-specific localization

---

### Post by global_dev on 2009-03-19
when i interrupt the process since it looks like its hanging

^C[00000404] signals interface error: Caught Interrupt signal, exiting...
[00000404] main interface debug: thread ended
[00000001] main libvlc debug: removing all interfaces
[00000406] qt4 interface debug: Quitting the Qt4 Interface
[00000406] qt4 interface debug: Destroying the main interface
[00000406] qt4 interface debug: Destroying the Dialog Provider
[00000406] main interface debug: thread ended
[00000406] main interface debug: thread 2985016208 joined (interface/interface.c:188)
[00000406] main interface debug: removing module "qt4"
[00000404] main interface debug: thread 3007929232 joined (interface/interface.c:188)
[00000404] main interface debug: removing module "signals"
[00000402] main interface debug: thread ended
[00000402] main interface debug: thread 3024714640 joined (interface/interface.c:188)
[00000402] main interface debug: removing module "screensaver"
[00000400] main interface debug: thread ended
[00000400] main interface debug: thread 3033107344 joined (interface/interface.c:188)
[00000400] main interface debug: removing module "inhibit"
[00000398] main interface debug: thread ended
[00000398] main interface debug: thread 3041500048 joined (interface/interface.c:188)
[00000398] main interface debug: removing module "hotkeys"
[00000001] main libvlc debug: removing all services discovery tasks
[00000001] main libvlc debug: removing playlist
[00000371] main playlist debug: saving Media Library to file /home/jonathan/.local/share/vlc/ml.xspf
[00000371] main playlist debug: looking for playlist export module: 1 candidate
[00000371] main playlist debug: using playlist export module "export"
[00000371] main playlist debug: TIMER module_Need() : 0.498 ms - Total 0.498 ms / 1 intvls (Avg 0.498 ms)
[00000371] main playlist debug: removing module "export"
[00000396] main preparser debug: thread ended
[00000396] main preparser debug: thread 3072420752 joined (playlist/engine.c:521)
[00000397] main fetcher debug: thread ended
[00000397] main fetcher debug: thread 3058285456 joined (playlist/engine.c:523)
[00000371] main playlist debug: thread ended
[00000371] main playlist debug: thread 3049892752 joined (libvlc.c:993)
[00000396] main preparser debug: Destroyed
[00000397] main fetcher debug: Destroyed
[00000371] main playlist debug: Destroyed
[00000001] main libvlc debug: removing interaction
[00000370] main interaction debug: thread ended
[00000370] main interaction debug: thread 3080829840 joined (interface/interaction.c:400)
[00000001] main libvlc debug: removing all video outputs
[00000001] main libvlc debug: TIMER ML Load : Total 22.833 ms / 1 intvls (Avg 22.833 ms)
[00000001] main libvlc debug: TIMER Items array build : Total 0.031 ms / 1 intvls (Avg 0.031 ms)
[00000001] main libvlc debug: TIMER ML Dump : Total 0.699 ms / 1 intvls (Avg 0.699 ms)
[00000001] main libvlc debug: removing stats
[00000001] main libvlc debug: removing module "memcpymmxext"
[00000001] main libvlc debug: opening config file (/home/jonathan/.config/vlc/vlcrc)
[00000001] main libvlc debug: opening config file (/home/jonathan/.config/vlc/vlcrc)
[00000001] main libvlc debug: writing plugins cache /home/jonathan/.cache/vlc/plugins-04041e.dat

---

### Post by IntuitiveNipple on 2009-03-22
This affects all qt4 applications - Skype, qtconfig-qt4, etc.. The reason is that qt4 is not handling sub-pixel font rendering correctly. Changing to another font rendering method is a temporary work-around:

System > Preferences > Appearance > Fonts > Rendering = Best Shapes

Track the issue via [bug #334657 Subpixel/Lcd mode makes qt4 applications on Jaunty unreadable](https://bugs.edge.launchpad.net/ubuntu/+source/qt4-x11/+bug/334657)

---

### Post by global_dev on 2009-03-23
Perfect, thanks for the quick heads-up.

---

