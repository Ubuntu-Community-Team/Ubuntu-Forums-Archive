---
title: "Use android phone as a USB webcam"
date: 2012-04-16
forum: Multimedia Software
---

### Post by sigmahx1 on 2012-04-16
Hi,

  I am trying to use my android phone (galaxy S II) as a USB webcam on my Dell laptop with ubuntu on it.To do so, I use the script prepare-videochat.sh available here : [https://github.com/bluezio/ipwebcam-gst](https://github.com/bluezio/ipwebcam-gst) (FYI, I also tried to install a version of droidcam that does not work last week). My problem is the following : when I launch the script on the laptop, everything works fine, a new video device is created (/dev/video2 while /dev/video0 is the (not working) droidcam and /dev/video1 is the (working) integrated webcam of the laptop) and IPwebcam is launched on the phone and broadcasts with http://<no_ip_address>:8080, but when I try to open /dev/video2 with vlc for example, it does not work. Here are some information. Do not hesitate to ask for more if required.

VLC log file when I try to open /dev/video2 :
```
sigma@193-49-212-144:~$ vlc -vvv &
[1] 2534
sigma@193-49-212-144:~$ VLC media player 1.1.9 The Luggage (revision exported)
[0x15f9120] main libvlc debug: VLC media player - 1.1.9 The Luggage
[0x15f9120] main libvlc debug: Copyright © 1996-2011 the VideoLAN team
[0x15f9120] main libvlc debug: revision exported
[0x15f9120] main libvlc debug: configured with ./configure  '--enable-static' '--build=x86_64-linux-gnu' '--config-cache' '--disable-maintainer-mode' '--disable-silent-rules' '--disable-update-check' '--enable-fast-install' '--prefix=/usr' '--docdir=/usr/share/doc/vlc-nox' '--sysconfdir=/etc' '--with-binary-version=1ubuntu1.3' '--enable-a52' '--enable-aa' '--enable-bonjour' '--enable-caca' '--enable-dca' '--enable-dirac' '--enable-dvb' '--enable-dvbpsi' '--enable-dvdnav' '--enable-faad' '--enable-flac' '--enable-fluidsynth' '--enable-freetype' '--enable-fribidi' '--enable-ggi' '--enable-gnutls' '--enable-jack' '--enable-kate' '--enable-libass' '--enable-libmpeg2' '--enable-libproxy' '--enable-libxml2' '--enable-lirc' '--enable-live555' '--enable-mad' '--enable-mkv' '--enable-mod' '--enable-mozilla' '--enable-mpc' '--enable-mtp' '--enable-mux_ogg' '--enable-ncurses' '--enable-notify' '--enable-ogg' '--enable-pulse' '--enable-qt4' '--enable-realrtsp' '--enable-schroedinger' '--enable-sdl' '--enable-shout' '--enable-skins2' '--enable-smb' '--enable-speex' '--enable-svg' '--enable-taglib' '--enable-theora' '--enable-twolame' '--enable-upnp' '--enable-vcd' '--enable-vcdx' '--enable-vorbis' '--enable-x264' '--enable-zvbi' '--with-kde-solid=/usr/share/kde4/apps/solid/actions/' '--with-mozilla-pkg=libxul' '--disable-dxva2' '--disable-gnomevfs' '--disable-goom' '--disable-osso_screensaver' '--disable-portaudio' '--disable-projectm' '--disable-sqlite' '--disable-telx' '--enable-alsa' '--enable-atmo' '--enable-dc1394' '--enable-dv' '--enable-libva' '--enable-pvr' '--enable-udev' '--enable-v4l2' '--enable-svgalib' 'build_alias=x86_64-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[0x15f9120] main libvlc debug: translation test: code is "en_GB"
[0x15f9120] main libvlc debug: checking plugin modules
[0x15f9120] main libvlc debug: loading plugins cache file /usr/lib/vlc/plugins/plugins-04081e-7e8.dat
[0x15f9120] main libvlc debug: recursively browsing `/usr/lib/vlc/plugins'
[0x15f9120] main libvlc debug: saving plugins cache /usr/lib/vlc/plugins/plugins-04081e-7e8.dat
[0x15f9120] main libvlc debug: module bank initialized (394 modules)
[0x15f9120] main libvlc debug: opening config file (/home/sigma/.config/vlc/vlcrc)
[0x15f9120] main libvlc debug: CPU has capabilities MMX MMXEXT SSE SSE2 SSE3 SSSE3 SSE4.1 FPU 
[0x15f9120] main libvlc debug: looking for memcpy module: 3 candidates
[0x15f9120] main libvlc debug: using memcpy module "memcpymmxext"
[0x1711420] main input debug: Creating an input for 'Media Library'
[0x1711420] main input debug: Input is a meta file: disabling unneeded options
[0x1711420] main input debug: using timeshift granularity of 50 MiB
[0x1711420] main input debug: using timeshift path '/tmp'
[0x1711420] main input debug: `file/xspf-open:///home/sigma/.local/share/vlc/ml.xspf' gives access `file' demux `xspf-open' path `/home/sigma/.local/share/vlc/ml.xspf'
[0x1711420] main input debug: creating demux: access='file' demux='xspf-open' path='/home/sigma/.local/share/vlc/ml.xspf'
[0x1717c70] main demux debug: looking for access_demux module: 2 candidates
[0x1717c70] main demux debug: no access_demux module matching "file" could be loaded
[0x1717c70] main demux debug: TIMER module_need() : 0.383 ms - Total 0.383 ms / 1 intvls (Avg 0.383 ms)
[0x1711420] main input debug: creating access 'file' path='/home/sigma/.local/share/vlc/ml.xspf'
[0x1727940] main access debug: looking for access module: 2 candidates
[0x1727940] filesystem access debug: opening file `/home/sigma/.local/share/vlc/ml.xspf'
[0x1727940] main access debug: using access module "filesystem"
[0x1727940] main access debug: TIMER module_need() : 0.177 ms - Total 0.177 ms / 1 intvls (Avg 0.177 ms)
[0x1719700] main stream debug: Using AStream*Stream
[0x1719700] main stream debug: pre buffering
[0x1719700] main stream debug: received first data after 0 ms
[0x1719700] main stream debug: pre-buffering done 296 bytes in 0s - 24088 KiB/s
[0x17194d0] main stream debug: looking for stream_filter module: 5 candidates
[0x17194d0] main stream debug: no stream_filter module matching "any" could be loaded
[0x17194d0] main stream debug: TIMER module_need() : 0.277 ms - Total 0.277 ms / 1 intvls (Avg 0.277 ms)
[0x17194d0] main stream debug: looking for stream_filter module: 1 candidate
[0x17194d0] main stream debug: using stream_filter module "stream_filter_record"
[0x17194d0] main stream debug: TIMER module_need() : 0.090 ms - Total 0.090 ms / 1 intvls (Avg 0.090 ms)
[0x1711420] main input debug: creating demux: access='file' demux='xspf-open' path='/home/sigma/.local/share/vlc/ml.xspf'
[0x1729280] main demux debug: looking for demux module: 1 candidate
[0x1729280] playlist demux debug: using XSPF playlist reader
[0x1729280] main demux debug: using demux module "playlist"
[0x1729280] main demux debug: TIMER module_need() : 0.130 ms - Total 0.130 ms / 1 intvls (Avg 0.130 ms)
[0x172d330] main demux meta debug: looking for meta reader module: 2 candidates
[0x172d330] lua demux meta debug: Trying Lua scripts in /home/sigma/.local/share/vlc/lua/meta/reader
[0x172d330] lua demux meta debug: Trying Lua scripts in /usr/lib/vlc/lua/meta/reader
[0x172d330] lua demux meta debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/reader/filename.luac
[0x172d330] lua demux meta debug: Trying Lua scripts in /usr/share/vlc/lua/meta/reader
[0x172d330] main demux meta debug: no meta reader module matching "any" could be loaded
[0x172d330] main demux meta debug: TIMER module_need() : 2.393 ms - Total 2.393 ms / 1 intvls (Avg 2.393 ms)
[0x1711420] main input debug: `file/xspf-open:///home/sigma/.local/share/vlc/ml.xspf' successfully opened
[0x172d330] main xml debug: looking for xml module: 2 candidates
[0x172d330] main xml debug: using xml module "xml"
[0x172d330] main xml debug: TIMER module_need() : 0.344 ms - Total 0.344 ms / 1 intvls (Avg 0.344 ms)
Warning: call to srand(1334561382)
Warning: call to rand()
[0x1729280] playlist demux debug: parsed 0 tracks successfully
[0x172d330] main xml debug: removing module "xml"
[0x1711420] main input debug: EOF reached
[0x1729280] main demux debug: removing module "playlist"
[0x17194d0] main stream debug: removing module "stream_filter_record"
[0x1727940] main access debug: removing module "filesystem"
[0x1711420] main input debug: TIMER input launching for 'Media Library' : 3.751 ms - Total 3.751 ms / 1 intvls (Avg 3.751 ms)
[0x17171f0] main interface debug: looking for interface module: 1 candidate
[0x17171f0] main interface debug: using interface module "hotkeys"
[0x17171f0] main interface debug: TIMER module_need() : 0.117 ms - Total 0.117 ms / 1 intvls (Avg 0.117 ms)
[0x1715b60] main interface debug: looking for interface module: 1 candidate
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x160b5a0] main playlist debug: Activated
[0x1715b60] main interface debug: using interface module "inhibit"
[0x1715b60] main interface debug: TIMER module_need() : 1.670 ms - Total 1.670 ms / 1 intvls (Avg 1.670 ms)
[0x1716270] main interface debug: looking for interface module: 1 candidate
[0x1716270] logger interface: using logger.
[0x1716270] logger interface warning: no log filename provided, using `vlc-log.txt'
[0x1716270] logger interface debug: opening logfile `vlc-log.txt'
[0x1716270] main interface debug: using interface module "logger"
[0x1716270] main interface debug: TIMER module_need() : 0.249 ms - Total 0.249 ms / 1 intvls (Avg 0.249 ms)
[0x1716c50] main interface debug: looking for interface module: 1 candidate
[0x1716c50] main interface debug: using interface module "signals"
[0x1716c50] main interface debug: TIMER module_need() : 0.146 ms - Total 0.146 ms / 1 intvls (Avg 0.146 ms)
[0x1716e90] main interface debug: looking for interface module: 1 candidate
[0x160b5a0] main playlist debug: rebuilding array of current - root Playlist
[0x160b5a0] main playlist debug: rebuild done - 0 items, index -1
[0x1716e90] main interface debug: using interface module "globalhotkeys"
[0x1716e90] main interface debug: TIMER module_need() : 0.705 ms - Total 0.705 ms / 1 intvls (Avg 0.705 ms)
[0x15f9120] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x1734790] main interface debug: looking for interface module: 5 candidates
Blocked: call to setlocale(6, "")
Warning: call to srand(1334807802)
Warning: call to rand()
Blocked: call to setlocale(6, "")

(process:2534): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
[0x19a02a0] main generic debug: looking for extension module: 1 candidate
[0x19a02a0] lua generic debug: Opening EXPERIMENTAL Lua Extension module
[0x19a02a0] lua generic debug: Trying Lua scripts in /home/sigma/.local/share/vlc/lua/extensions
[0x19a02a0] lua generic debug: Trying Lua scripts in /usr/lib/vlc/lua/extensions
[0x19a02a0] lua generic debug: Trying Lua playlist script /usr/lib/vlc/lua/extensions/allocine-fr.luac
[0x19a02a0] lua generic debug: Scanning Lua script /usr/lib/vlc/lua/extensions/allocine-fr.luac
[0x19a02a0] lua generic debug: Script /usr/lib/vlc/lua/extensions/allocine-fr.luac has the following capability flags: 0xc
[0x19a02a0] lua generic debug: Trying Lua scripts in /usr/share/vlc/lua/extensions
[0x19a02a0] main generic debug: using extension module "lua"
[0x19a02a0] main generic debug: TIMER module_need() : 0.582 ms - Total 0.582 ms / 1 intvls (Avg 0.582 ms)
Blocked: call to setlocale(6, "")
[0x1734790] main interface debug: using interface module "qt4"
[0x1734790] main interface debug: TIMER module_need() : 133.751 ms - Total 133.751 ms / 1 intvls (Avg 133.751 ms)
[0x1734790] qt4 interface debug: Initialization of Capture device panel
Warning: call to rand()
Warning: call to rand()
Warning: call to rand()
[0x1734790] qt4 interface warning: Input option: input-slave=alsa://
[0x1734790] qt4 interface warning: Input option: v4l2-standard=0
[0x1734790] qt4 interface warning: Input option: file-caching=300
[0x160b5a0] main playlist debug: adding item `v4l2:///dev/video2' ( v4l2:///dev/video2 )
[0x160b5a0] main playlist debug: rebuilding array of current - root Playlist
[0x160b5a0] main playlist debug: rebuild done - 1 items, index -1
[0x160b5a0] main playlist debug: processing request item v4l2:///dev/video2 node null skip 0
[0x160b5a0] main playlist debug: resyncing on v4l2:///dev/video2
[0x160b5a0] main playlist debug: v4l2:///dev/video2 is at 0
[0x160b5a0] main playlist debug: starting new item
[0x160b5a0] main playlist debug: creating new input thread
[0x1d85f80] main input debug: Creating an input for 'v4l2:///dev/video2'
[0x1d85f80] main input debug: thread (input) created at priority 10 (input/input.c:220)
[0x1734790] qt4 interface debug: Adding a new MRL to recent ones: v4l2:///dev/video2
[0x1734790] qt4 interface debug: IM: Setting an input
[0x1d85f80] main input debug: thread started
[0x1d85f80] main input debug: using timeshift granularity of 50 MiB
[0x1d85f80] main input debug: using timeshift path '/tmp'
[0x1d85f80] main input debug: `v4l2:///dev/video2' gives access `v4l2' demux `' path `/dev/video2'
[0x1d85f80] main input debug: creating demux: access='v4l2' demux='' path='/dev/video2'
[0x1b27c10] main demux debug: looking for access_demux module: 1 candidate
[0x1b27c10] v4l2 demux debug: Trying direct kernel v4l2
[0x1b27c10] v4l2 demux debug: opening device '/dev/video2'
[0x1b27c10] v4l2 demux debug: V4L2 device: Dummy video device using driver: v4l2 loopback (version: 0.5.0) on 
[0x1b27c10] v4l2 demux debug: the device has the capabilities: (X) Video Capture, ( ) Audio, ( ) Tuner, ( ) Radio
[0x1b27c10] v4l2 demux debug: supported I/O methods are: (X) Read/Write, (X) Streaming, ( ) Asynchronous
[0x1b27c10] v4l2 demux debug: video standard 0 is: NTSC  
[0x1b27c10] v4l2 demux debug: video standard 1 is: NTSC-M  
[0x1b27c10] v4l2 demux debug: video standard 2 is: NTSC-M-JP  
[0x1b27c10] v4l2 demux debug: video standard 3 is: NTSC-M-KR  
[0x1b27c10] v4l2 demux debug: video standard 4 is: NTSC-443  
[0x1b27c10] v4l2 demux debug: video standard 5 is: PAL  
[0x1b27c10] v4l2 demux debug: video standard 6 is: PAL-BG  
[0x1b27c10] v4l2 demux debug: video standard 7 is: PAL-H  
[0x1b27c10] v4l2 demux debug: video standard 8 is: PAL-I  
[0x1b27c10] v4l2 demux debug: video standard 9 is: PAL-DK  
[0x1b27c10] v4l2 demux debug: video standard 10 is: PAL-M  
[0x1b27c10] v4l2 demux debug: video standard 11 is: PAL-N  
[0x1b27c10] v4l2 demux debug: video standard 12 is: PAL-Nc  
[0x1b27c10] v4l2 demux debug: video standard 13 is: PAL-60  
[0x1b27c10] v4l2 demux debug: video standard 14 is: SECAM  
[0x1b27c10] v4l2 demux debug: video standard 15 is: SECAM-B  
[0x1b27c10] v4l2 demux debug: video standard 16 is: SECAM-G  
[0x1b27c10] v4l2 demux debug: video standard 17 is: SECAM-H  
[0x1b27c10] v4l2 demux debug: video standard 18 is: SECAM-DK  
[0x1b27c10] v4l2 demux debug: video standard 19 is: SECAM-L  
[0x1b27c10] v4l2 demux debug: video standard 20 is: SECAM-Lc  
[0x1b27c10] v4l2 demux debug: '/dev/video2' is a video device
[0x1b27c10] v4l2 demux warning: invalid input. Using the default one
[0x1b27c10] v4l2 demux error: cannot set input (Invalid argument)
[0x1b27c10] v4l2 demux debug: Trying libv4l2 wrapper
[0x1b27c10] v4l2 demux debug: opening device '/dev/video2'
libv4l2: error getting pixformat: Invalid argument
[0x1b27c10] v4l2 demux error: cannot open video device '/dev/video2' (Invalid argument)
[0x1b27c10] main demux debug: no access_demux module matching "v4l2" could be loaded
[0x1b27c10] main demux debug: TIMER module_need() : 5.376 ms - Total 5.376 ms / 1 intvls (Avg 5.376 ms)
[0x1d85f80] main input debug: creating access 'v4l2' path='/dev/video2'
[0x160b5a0] main playlist debug: no fetch required for (null) (art currently (null))
[0x1d95dd0] main access debug: looking for access module: 1 candidate
[0x1d95dd0] v4l2 access debug: Trying direct kernel v4l2
[0x1d95dd0] v4l2 access debug: opening device '/dev/video2'
[0x1d95dd0] v4l2 access debug: V4L2 device: Dummy video device using driver: v4l2 loopback (version: 0.5.0) on 
[0x1d95dd0] v4l2 access debug: the device has the capabilities: (X) Video Capture, ( ) Audio, ( ) Tuner, ( ) Radio
[0x1d95dd0] v4l2 access debug: supported I/O methods are: (X) Read/Write, (X) Streaming, ( ) Asynchronous
[0x1d95dd0] v4l2 access debug: video standard 0 is: NTSC  
[0x1d95dd0] v4l2 access debug: video standard 1 is: NTSC-M  
[0x1d95dd0] v4l2 access debug: video standard 2 is: NTSC-M-JP  
[0x1d95dd0] v4l2 access debug: video standard 3 is: NTSC-M-KR  
[0x1d95dd0] v4l2 access debug: video standard 4 is: NTSC-443  
[0x1d95dd0] v4l2 access debug: video standard 5 is: PAL  
[0x1d95dd0] v4l2 access debug: video standard 6 is: PAL-BG  
[0x1d95dd0] v4l2 access debug: video standard 7 is: PAL-H  
[0x1d95dd0] v4l2 access debug: video standard 8 is: PAL-I  
[0x1d95dd0] v4l2 access debug: video standard 9 is: PAL-DK  
[0x1d95dd0] v4l2 access debug: video standard 10 is: PAL-M  
[0x1d95dd0] v4l2 access debug: video standard 11 is: PAL-N  
[0x1d95dd0] v4l2 access debug: video standard 12 is: PAL-Nc  
[0x1d95dd0] v4l2 access debug: video standard 13 is: PAL-60  
[0x1d95dd0] v4l2 access debug: video standard 14 is: SECAM  
[0x1d95dd0] v4l2 access debug: video standard 15 is: SECAM-B  
[0x1d95dd0] v4l2 access debug: video standard 16 is: SECAM-G  
[0x1d95dd0] v4l2 access debug: video standard 17 is: SECAM-H  
[0x1d95dd0] v4l2 access debug: video standard 18 is: SECAM-DK  
[0x1d95dd0] v4l2 access debug: video standard 19 is: SECAM-L  
[0x1d95dd0] v4l2 access debug: video standard 20 is: SECAM-Lc  
[0x1d95dd0] v4l2 access debug: '/dev/video2' is a video device
[0x1d95dd0] v4l2 access warning: invalid input. Using the default one
[0x1d95dd0] v4l2 access error: cannot set input (Invalid argument)
[0x1d95dd0] v4l2 access debug: Trying libv4l2 wrapper
[0x1d95dd0] v4l2 access debug: opening device '/dev/video2'
libv4l2: error getting pixformat: Invalid argument
[0x1d95dd0] v4l2 access error: cannot open video device '/dev/video2' (Invalid argument)
[0x1d95dd0] main access debug: no access module matching "v4l2" could be loaded
[0x1d95dd0] main access debug: TIMER module_need() : 0.595 ms - Total 0.595 ms / 1 intvls (Avg 0.595 ms)
[0x1d85f80] main input error: open of `v4l2:///dev/video2' failed: (null)
[0x160b5a0] main playlist debug: finished input
[0x160b5a0] main playlist debug: dead input
[0x1d85f80] main input debug: thread ended
[0x160b5a0] main playlist debug: changing item without a request (current 0/1)
[0x160b5a0] main playlist debug: nothing to play
[0x1734790] qt4 interface debug: IM: Deleting the input
[0x15f9120] main libvlc debug: deactivating the playlist
[0x160b5a0] main playlist debug: Deactivate
[0x1d9c030] main playlist export debug: saving Media Library to file /home/sigma/.local/share/vlc/ml.xspf
[0x1d9c030] main playlist export debug: looking for playlist export module: 1 candidate
[0x1d9c030] main playlist export debug: using playlist export module "export"
[0x1d9c030] main playlist export debug: TIMER module_need() : 0.890 ms - Total 0.890 ms / 1 intvls (Avg 0.890 ms)
[0x1d9c030] main playlist export debug: removing module "export"
[0x160b5a0] main playlist debug: Deactivated
[0x15f9120] main libvlc debug: removing all services discovery tasks
[0x15f9120] main libvlc debug: removing all interfaces
[0x1734790] qt4 interface debug: requesting exit...
[0x1734790] qt4 interface debug: waiting for UI thread...
[0x1734790] qt4 interface debug: Exec finished()
[0x1734790] qt4 interface debug: Video is not needed anymore
[0x1734790] qt4 interface debug: Killing extension dialog provider
[0x1734790] qt4 interface debug: ExtensionsDialogProvider is quitting...
[0x19a02a0] lua generic debug: Deactivating all loaded extensions
[0x19a02a0] lua generic debug: All extensions are now deactivated
[0x19a02a0] main generic debug: removing module "lua"
Application asked to unregister timer 0x4e000004 which is not registered in this thread. Fix application.
[0x1734790] main interface debug: removing module "qt4"
[0x1716e90] main interface debug: removing module "globalhotkeys"
[0x1716c50] main interface debug: removing module "signals"
[0x1716270] main interface debug: removing module "logger"
[0x1d85f80] main input debug: TIMER input launching for 'v4l2:///dev/video2' : 5785.462 ms - Total 5785.462 ms / 1 intvls (Avg 5785.462 ms)
[0x1715b60] main interface debug: removing module "inhibit"
[0x17171f0] main interface debug: removing module "hotkeys"
[0x160b5a0] main playlist debug: destroying
[0x15f9120] main libvlc debug: TIMER ML Load : Total 4.341 ms / 1 intvls (Avg 4.341 ms)
[0x15f9120] main libvlc debug: TIMER Items array build : Total 0.136 ms / 2 intvls (Avg 0.068 ms)
[0x15f9120] main libvlc debug: TIMER ML Dump : Total 1.269 ms / 1 intvls (Avg 1.269 ms)
[0x15f9120] main libvlc debug: removing stats
[0x15f9120] main libvlc debug: removing module "memcpymmxext"
```

lsmod :
```
sigma@193-49-212-144:~$ lsmod
Module                  Size  Used by
v4l2loopback           28811  0 
usb_storage            53538  0 
cdc_acm                22574  0 
uas                    17996  0 
michael_mic            12612  0 
arc4                   12529  0 
rfcomm                 47694  0 
binfmt_misc            17565  1 
sco                    18187  0 
bnep                   18308  0 
l2cap                  53610  4 rfcomm,bnep
btusb                  18600  0 
bluetooth              72320  5 rfcomm,sco,bnep,l2cap,btusb
joydev                 17606  0 
nvidia              10709116  100 
rpcsec_gss_krb5        36216  0 
nfsd                  316512  2 
exportfs               12998  1 nfsd
nfs                   330417  0 
snd_hda_codec_idt      71137  1 
lockd                  85732  2 nfsd,nfs
fscache                57123  1 nfs
nfs_acl                12883  2 nfsd,nfs
auth_rpcgss            52881  3 rpcsec_gss_krb5,nfsd,nfs
sunrpc                234297  7 rpcsec_gss_krb5,nfsd,nfs,lockd,nfs_acl,auth_rpcgss
snd_hda_intel          33176  6 
snd_hda_codec         103804  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96391  4 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
lib80211_crypt_tkip    17387  0 
snd_timer              29602  2 snd_pcm,snd_seq
pcmcia                 49166  0 
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
wl                   2568244  0 
dell_wmi               12681  0 
ppdev                  17113  0 
sparse_keymap          13898  1 dell_wmi
uvcvideo               72195  0 
dell_laptop            13827  0 
snd                    67382  19 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           27846  0 
parport_pc             36959  1 
pcmcia_rsrc            18372  1 yenta_socket
dcdbas                 14438  1 dell_laptop
psmouse                73535  0 
soundcore              12680  1 snd
pcmcia_core            22569  3 pcmcia,yenta_socket,pcmcia_rsrc
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
serio_raw              13166  0 
lib80211               14991  2 lib80211_crypt_tkip,wl
droidcam_v4l           14295  0 
video                  19438  0 
videodev               82052  3 v4l2loopback,uvcvideo,droidcam_v4l
v4l2_compat_ioctl32    17078  1 videodev
lp                     17825  0 
parport                46458  3 ppdev,parport_pc,lp
usbhid                 46956  0 
hid                    91020  1 usbhid
e1000e                159143  0 
sdhci_pci              13989  0 
sdhci                  27387  1 sdhci_pci
firewire_ohci          40370  0 
firewire_core          62646  1 firewire_ohci
ahci                   25951  2 
crc_itu_t              12707  1 firewire_core
libahci                26642  1 ahci

```

  If anyone has any clue... It will be much appreciated :).

Best,

Sigma.

---

### Post by mordak13 on 2012-05-24
Does it have to be via USB?  I've been using an IP webcam app for a while from the Play Store: [https://play.google.com/store/apps/details?id=com.pas.webcam](https://play.google.com/store/apps/details?id=com.pas.webcam) I use on both my Galaxy Note using ICS and my Acer A100 tablet also running ICS.  Any web browser works to view it. Hope this helps.

---

### Post by boscharun on 2013-02-22
IP webcam uses WIFI and requires that wifi be available on PC. You could also try the [DroidCam]("http://www.skipser.com/p/2/p/android-as-webcam.html") app which connects via USB.
P.S. You need ADB as well installed to do this though.

---

