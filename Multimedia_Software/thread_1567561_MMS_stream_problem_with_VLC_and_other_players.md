---
title: "MMS stream problem with VLC and other players"
date: 2010-09-04
forum: Multimedia Software
---

### Post by Virus666 on 2010-09-04
Hi all,

I am aware of many post about MMS streams but I still cannot find any solution for my problem. Here is the problem:

As some of you know that 2010 FIBA World Championship is ongoing and I am aiming to watch some matches on TV. However, the Internet stream of the official broadcaster in Turkey cannot be played by VLC and other media players.

**mms://85.111.3.55/ntv**

Logs:

```
rifat@rea-pc:~$ vlc -vvv mms://85.111.3.55/ntv
VLC media player 1.0.6 Goldeneye
[0x83be668] main libvlc debug: VLC media player - version 1.0.6 Goldeneye - (c) 1996-2010 the VideoLAN team
[0x83be668] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--config-cache' '--disable-maintainer-mode' '--disable-update-check' '--enable-fast-install' '--enable-release' '--prefix=/usr' '--with-binary-version=1ubuntu1.2' '--disable-atmo' '--disable-fluidsynth' '--disable-gnomevfs' '--disable-kate' '--disable-mtp' '--enable-x264' '--disable-zvbi' '--enable-a52' '--enable-aa' '--enable-bonjour' '--enable-caca' '--enable-dca' '--enable-dvb' '--enable-dvbpsi' '--enable-dvdnav' '--enable-faad' '--enable-flac' '--enable-freetype' '--enable-fribidi' '--enable-ggi' '--enable-gnutls' '--enable-jack' '--enable-libass' '--enable-libmpeg2' '--enable-lirc' '--enable-live555' '--enable-mad' '--enable-mkv' '--enable-mod' '--enable-mozilla' '--enable-mpc' '--enable-ncurses' '--enable-notify' '--enable-ogg' '--enable-pulse' '--enable-qt4' '--enable-realrtsp' '--enable-sdl' '--enable-shout' '--enable-skins2' '--enable-smb' '--enable-speex' '--enable-svg' '--enable-taglib' '--enable-telx' '--enable-theora' '--enable-twolame' '--enable-vcd' '--enable-vcdx' '--enable-vorbis' '--with-mozilla-pkg=libxul' '--enable-alsa' '--enable-dv' '--enable-pvr' '--enable-v4l' '--enable-v4l2' '--enable-svgalib' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[0x83be668] main libvlc debug: translation test: code is "C"
[0x83be668] main libvlc debug: checking plugin modules
[0x83be668] main libvlc debug: loading plugins cache file /home/rifat/.cache/vlc/plugins-04041e.dat
[0x83be668] main libvlc debug: recursively browsing `/usr/lib/vlc'
[0x83be668] main libvlc debug: module bank initialized (380 modules)
[0x83be668] main libvlc debug: opening config file (/home/rifat/.config/vlc/vlcrc)
[0x83be668] main libvlc debug: CPU has capabilities 486 586 MMX MMXEXT FPU 
[0x83be668] main libvlc debug: looking for memcpy module: 3 candidates
[0x83be668] main libvlc debug: using memcpy module "memcpymmxext"
[0x845eb78] main input debug: Creating an input for 'Medya Kitapl&#305;&#287;&#305;'
[0x845eb78] main input debug: Input is a meta file: disabling unneeded options
[0x845eb78] main input debug: using timeshift granularity of 50 MBytes
[0x845eb78] main input debug: using timeshift path '/tmp'
[0x845eb78] main input debug: `file/xspf-open:///home/rifat/.local/share/vlc/ml.xspf' gives access `file' demux `xspf-open' path `/home/rifat/.local/share/vlc/ml.xspf'
[0x845eb78] main input debug: creating demux: access='file' demux='xspf-open' path='/home/rifat/.local/share/vlc/ml.xspf'
[0x8462790] main demux debug: looking for access_demux module: 1 candidate
[0x8462790] main demux warning: no access_demux module matching "file" could be loaded
[0x8462790] main demux debug: TIMER module_need() : 0,621 ms - Total 0,621 ms / 1 intvls (Avg 0,621 ms)
[0x845eb78] main input debug: creating access 'file' path='/home/rifat/.local/share/vlc/ml.xspf'
[0x8464520] main access debug: looking for access module: 3 candidates
[0x8464520] access_file access debug: opening file `/home/rifat/.local/share/vlc/ml.xspf'
[0x8464520] main access debug: using access module "access_file"
[0x8464520] main access debug: TIMER module_need() : 0,602 ms - Total 0,602 ms / 1 intvls (Avg 0,602 ms)
[0x8472c28] main stream debug: Using AStream*Stream
[0x8472c28] main stream debug: pre buffering
[0x8472c28] main stream debug: received first data after 0 ms
[0x8472c28] main stream debug: pre-buffering done 301 bytes in 0s - 13997 kbytes/s
[0x8463c48] main stream debug: looking for stream_filter module: 5 candidates
[0x8463c48] main stream debug: TIMER module_need() : 0,505 ms - Total 0,505 ms / 1 intvls (Avg 0,505 ms)
[0x8463c48] main stream debug: looking for stream_filter module: 1 candidate
[0x8463c48] main stream debug: using stream_filter module "stream_filter_record"
[0x8463c48] main stream debug: TIMER module_need() : 0,172 ms - Total 0,172 ms / 1 intvls (Avg 0,172 ms)
[0x845eb78] main input debug: creating demux: access='file' demux='xspf-open' path='/home/rifat/.local/share/vlc/ml.xspf'
[0x8474f40] main demux debug: looking for demux module: 1 candidate
[0x8474f40] playlist demux debug: using XSPF playlist reader
[0x8474f40] main demux debug: using demux module "playlist"
[0x8474f40] main demux debug: TIMER module_need() : 0,336 ms - Total 0,336 ms / 1 intvls (Avg 0,336 ms)
[0x845eb78] main input debug: `file/xspf-open:///home/rifat/.local/share/vlc/ml.xspf' successfully opened
[0x84742d8] main xml debug: looking for xml module: 2 candidates
[0x84742d8] main xml debug: using xml module "xml"
[0x84742d8] main xml debug: TIMER module_need() : 0,516 ms - Total 0,516 ms / 1 intvls (Avg 0,516 ms)
[0x8474f40] playlist demux debug: parsed 0 tracks successfully
[0x84742d8] main xml debug: removing module "xml"
[0x845eb78] main input debug: EOF reached
[0x8474f40] main demux debug: removing module "playlist"
[0x8463c48] main stream debug: removing module "stream_filter_record"
[0x8464520] main access debug: removing module "access_file"
[0x845eb78] main input debug: TIMER input launching for 'Medya Kitapl&#305;&#287;&#305;' : 6,109 ms - Total 6,109 ms / 1 intvls (Avg 6,109 ms)
[0x845da48] main playlist debug: Activated
[0x845da48] main playlist debug: rebuilding array of current - root Oynatma Listesi
[0x845da48] main playlist debug: rebuild done - 0 items, index -1
[0x8464520] main interface debug: looking for interface module: 1 candidate
[0x8464520] main interface debug: using interface module "hotkeys"
[0x8464520] main interface debug: TIMER module_need() : 0,372 ms - Total 0,372 ms / 1 intvls (Avg 0,372 ms)
[0x8464520] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)
[0x8464520] main interface debug: thread started
[0x8475658] main interface debug: looking for interface module: 1 candidate
[0x8475658] main interface debug: using interface module "inhibit"
[0x8475658] main interface debug: TIMER module_need() : 2,064 ms - Total 2,064 ms / 1 intvls (Avg 2,064 ms)
[0x8475658] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)
[0x8475658] main interface debug: thread started
[0xb7400960] main interface debug: looking for interface module: 1 candidate
[0xb7400960] main interface debug: using interface module "screensaver"
[0xb7400960] main interface debug: TIMER module_need() : 0,279 ms - Total 0,279 ms / 1 intvls (Avg 0,279 ms)
[0xb7400960] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)
[0xb7400960] main interface debug: thread started
[0x845da48] main playlist debug: adding item `mms://85.111.3.55/ntv' ( mms://85.111.3.55/ntv )
[0x8475cc8] main interface debug: looking for interface module: 1 candidate
[0x8475cc8] main interface debug: using interface module "signals"
[0x8475cc8] main interface debug: TIMER module_need() : 0,241 ms - Total 0,241 ms / 1 intvls (Avg 0,241 ms)
[0x8475cc8] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)
[0x8475cc8] main interface debug: thread started
[0x8475cc8] main interface debug: thread ended
[0x8461e40] main interface debug: looking for interface module: 1 candidate
[0x8461e40] main interface debug: using interface module "globalhotkeys"
[0x8461e40] main interface debug: TIMER module_need() : 14,381 ms - Total 14,381 ms / 1 intvls (Avg 14,381 ms)
[0x8461e40] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)
[0x83be668] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x8478f70] main interface debug: looking for interface module: 4 candidates
[0x8461e40] main interface debug: thread started
[0x8461e40] main interface debug: thread ended
[0x8478f70] main interface debug: using interface module "qt4"
[0x8478f70] main interface debug: TIMER module_need() : 269,900 ms - Total 269,900 ms / 1 intvls (Avg 269,900 ms)
[0x8478f70] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)
[0x8478f70] main interface debug: thread started
[0x845da48] main playlist debug: rebuilding array of current - root Oynatma Listesi
[0x845da48] main playlist debug: rebuild done - 1 items, index -1
[0x845da48] main playlist debug: processing request item null node Oynatma Listesi skip 0
[0x8478f70] main interface debug: thread ended
[0x845da48] main playlist debug: starting new item
[0x845da48] main playlist debug: creating new input thread
[0xb7401320] main input debug: Creating an input for 'mms://85.111.3.55/ntv'
[0x8478f70] qt4 interface debug: Error while initializing qt-specific localization
[0xb7401320] main input debug: thread (input) created at priority 10 (input/input.c:230)
[0x8478f70] qt4 interface debug: IM: Setting an input
[0xb7401320] main input debug: thread started
[0x8478f70] qt4 interface debug: Updating the geometry
[0x8478f70] qt4 interface debug: Updating the geometry
[0xb7401320] main input debug: using timeshift granularity of 50 MBytes
[0xb7401320] main input debug: using timeshift path '/tmp'
[0xb7401320] main input debug: `mms://85.111.3.55/ntv' gives access `mms' demux `' path `85.111.3.55/ntv'
[0xb7401320] main input debug: creating demux: access='mms' demux='' path='85.111.3.55/ntv'
[0x8742300] main demux debug: looking for access_demux module: 0 candidates
[0x8742300] main demux debug: no access_demux module matched "mms"
[0x8742300] main demux debug: TIMER module_need() : 0,115 ms - Total 0,115 ms / 1 intvls (Avg 0,115 ms)
[0xb7401320] main input debug: creating access 'mms' path='85.111.3.55/ntv'
[0x8742300] main access debug: looking for access module: 1 candidate
[0x8742300] access_mms access debug: waiting for connection...
[0x8742300] main access debug: net: connecting to 85.111.3.55 port 1755
[0x8742300] main access debug: connection: Operation now in progress
[0x8742300] main access warning: connection timed out
[0x8742300] access_mms access error: failed to open a connection (tcp)
[0x8742300] access_mms access debug: waiting for connection...
[0x8742300] main access debug: net: connecting to 85.111.3.55 port 1755
[0x8742300] main access debug: connection: Operation now in progress
[0x8742300] main access warning: connection timed out
[0x8742300] access_mms access error: failed to open a connection (tcp)
[0x8742300] access_mms access error: cannot connect to server
[0x8742300] main access debug: net: connecting to 85.111.3.55 port 80
[0x8742300] main access debug: connection: Operation now in progress
[0x8742300] main access debug: connection succeeded (socket = 21)
[0x8742300] access_mms access error: error: HTTP/1.1 404 Not Found
[0x8742300] main access warning: no access module matching "mms" could be loaded
[0x8742300] main access debug: TIMER module_need() : 10286,268 ms - Total 10286,268 ms / 1 intvls (Avg 10286,268 ms)
[0x8742300] main access debug: waitpipe: object killed
[0xb7401320] main input error: open of `mms://85.111.3.55/ntv' failed: (null)
[0xb7401320] main input debug: thread ended
[0x845da48] main playlist debug: dead input
[0x845da48] main playlist debug: changing item without a request (current 0/1)
[0x845da48] main playlist debug: nothing to play
[0x8478f70] qt4 interface debug: IM: Deleting the input
[0x8478f70] qt4 interface debug: Updating the geometry
[0x8478f70] qt4 interface debug: Updating the geometry
[0xb7401320] main input debug: TIMER input launching for 'mms://85.111.3.55/ntv' : 10526,490 ms - Total 10526,490 ms / 1 intvls (Avg 10526,490 ms)
``````
rifat@rea-pc:~$ vlc -v mms://85.111.3.55/ntv
VLC media player 1.0.6 Goldeneye
[0x8d4f728] main demux warning: no access_demux module matching "file" could be loaded
[0x8cab668] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x9039ae0] main access warning: connection timed out
[0x9039ae0] access_mms access error: failed to open a connection (tcp)
[0x9039ae0] main access warning: connection timed out
[0x9039ae0] access_mms access error: failed to open a connection (tcp)
[0x9039ae0] access_mms access error: cannot connect to server
[0x9039ae0] access_mms access error: error: HTTP/1.1 404 Not Found
[0x9039ae0] main access warning: no access module matching "mms" could be loaded
[0x8d6d3c0] main input error: open of `mms://85.111.3.55/ntv' failed: (null)
``````
rifat@rea-pc:~$ mplayer -v mms://85.111.3.55/ntv
MPlayer SVN-r31042-Ubuntu-RVM (C) 2000-2010 MPlayer Team
CPU vendor name: GenuineIntel  max cpuid level: 10
CPU: Intel(R) Core(TM)2 CPU         T5600  @ 1.83GHz (Family: 6, Model: 15, Stepping: 6)
extended cpuid-level: 8
extended cache-info: 134242368
Detected cache-line size is 64 bytes
Testing OS support for SSE... yes.
Tests of OS support for SSE passed.
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNowExt: 0 SSE: 1 SSE2: 1 SSSE3: 1
Compiled with runtime CPU detection.
get_path('codecs.conf') -> '/home/rifat/.mplayer/codecs.conf'
Reading /home/rifat/.mplayer/codecs.conf: Can't open '/home/rifat/.mplayer/codecs.conf': No such file or directory
Reading /etc/mplayer/codecs.conf: Can't open '/etc/mplayer/codecs.conf': No such file or directory
Using built-in default codecs.conf.
Configuration: --enable-runtime-cpudetection --target=i586-linux --prefix=/usr --confdir=/etc/mplayer --mandir=/usr/share/man --codecsdir=/usr/lib/win32 --disable-libdvdcss-internal --enable-xvmc --enable-menu --cc=gcc-4.3 --enable-gui --enable-mencoder
CommandLine: '-v' 'mms://85.111.3.55/ntv'
init_freetype
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
get_path('fonts') -> '/home/rifat/.mplayer/fonts'
Using nanosleep() timing
get_path('input.conf') -> '/home/rifat/.mplayer/input.conf'
Can't open input config file /home/rifat/.mplayer/input.conf: No such file or directory
Parsing input config file /etc/mplayer/input.conf
Input config file /etc/mplayer/input.conf parsed: 91 binds
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
get_path('ntv.conf') -> '/home/rifat/.mplayer/ntv.conf'

Playing mms://85.111.3.55/ntv.
get_path('sub/') -> '/home/rifat/.mplayer/sub/'
Filename for url is now mms://85.111.3.55/ntv
Filename for url is now mms://85.111.3.55/ntv
STREAM_ASF, URL: mms://85.111.3.55/ntv
Trying ASF/UDP...
  ===> ASF/UDP failed
Trying ASF/TCP...
Resolving 85.111.3.55 for AF_INET6...
Couldn't resolve name for AF_INET6: 85.111.3.55
Connecting to server 85.111.3.55[85.111.3.55]: 1755...
connect error: Connection refused
  ===> ASF/TCP failed
Trying ASF/HTTP...
Resolving 85.111.3.55 for AF_INET6...
Couldn't resolve name for AF_INET6: 85.111.3.55
Connecting to server 85.111.3.55[85.111.3.55]: 80...
Server returned 404:Not Found
Failed to parse header.
  ===> ASF/HTTP failed
Failed, exiting.
Filename for url is now mms://85.111.3.55/ntv
Filename for url is now mms://85.111.3.55/ntv
STREAM_HTTP(2), URL: mms://85.111.3.55/ntv
Resolving 85.111.3.55 for AF_INET6...
Couldn't resolve name for AF_INET6: 85.111.3.55
Connecting to server 85.111.3.55[85.111.3.55]: 80...
--- HTTP DEBUG HEADER --- START ---
protocol:           [HTTP/1.1]
http minor version: [1]
uri:                [(null)]
method:             [(null)]
status code:        [404]
reason phrase:      [Not Found]
body size:          [0]
Fields:
 0 - Server: Microsoft-IIS/7.0
 1 - Date: Sat, 04 Sep 2010 03:10:39 GMT
 2 - Connection: close
 3 - Content-Length: 0
--- HTTP DEBUG HEADER --- END ---
Server returned 404: Not Found
No stream found to handle url mms://85.111.3.55/ntv

vo: x11 uninit called but X11 not initialized..

Exiting... (End of file)
``````
rifat@rea-pc:~$ gnome-mplayer -vvv mms://85.111.3.55/ntv
GNOME MPlayer 0.9.9.2
vo = (null) ao = (null)
Running with GIO support
Master Playback is 1
Master Range is 0 to 65536 
Master Current Volume 37356, multiplier = 0,001526
Scaled Volume is 57,000732
Using volume of 57,00
opening mms://85.111.3.55/ntv
is block 0
is character 0
is reg 0
is dir 0
playlist 0
embedded in window id 0x0
playlist detection = 0
adding mms://85.111.3.55/ntv to playlist (cancel = 0)
Using match: type='signal',interface='com.gnome.mplayer'
Using match: type='signal',interface='org.gnome.SettingsDaemon'
Using match: type='signal',interface='org.gnome.SettingsDaemon.MediaKeys'
Proxy connections and Command connected
playing - mms://85.111.3.55/ntv
is playlist 0
media size = 0 x 0
mplayer -quiet -slave -identify -volume 57 -mixer-channel Master -framedrop -noconsolecontrols -noidle -osdlevel 0 -nomouseinput -cache 32 -wid 0x3a00064 -ss 0 -*** -noembeddedfonts -***-font-scale 1,00 -***-color ffffff00 -channels 2 -vf-add screenshot -dvd-device /dev/dvd -af-add export=/tmp/mplayer-af_exportdgqmoo:512 mms://85.111.3.55/ntv 
current size = 0 x 0 
Spawn succeeded for filename mms://85.111.3.55/ntv
MPlayer SVN-r31042-Ubuntu-RVM (C) 2000-2010 MPlayer Team
ERROR: mplayer: could not connect to socket

ERROR: mplayer: No such file or directory
Playing mms://85.111.3.55/ntv.
ERROR: Failed to open LIRC support. You will not be able to use your remote control.
STREAM_ASF, URL: mms://85.111.3.55/ntv
ERROR: Couldn't resolve name for AF_INET6: 85.111.3.55
Resolving 85.111.3.55 for AF_INET6...
Connecting to server 85.111.3.55[85.111.3.55]: 1755...
Resolving 85.111.3.55 for AF_INET6...
ERROR: connect error: Connection refused
Connecting to server 85.111.3.55[85.111.3.55]: 80...
ERROR: Couldn't resolve name for AF_INET6: 85.111.3.55
Resolving 85.111.3.55 for AF_INET6...
ERROR: Server returned 404:Not Found
Connecting to server 85.111.3.55[85.111.3.55]: 80...
ERROR: Failed to parse header.
ERROR: Failed, exiting.

ERROR: Couldn't resolve name for AF_INET6: 85.111.3.55
ERROR: Server returned 404: Not Found

ERROR: No stream found to handle url mms://85.111.3.55/ntv
Exiting... (End of file)
Thread completing
playing - mmshttp://85.111.3.55/ntv
is playlist 0
media size = 316 x 17
mplayer -quiet -slave -identify -volume 57 -mixer-channel Master -framedrop -noconsolecontrols -noidle -osdlevel 0 -nomouseinput -cache 32 -wid 0x3a00064 -ss 0 -*** -noembeddedfonts -***-font-scale 1,00 -***-color ffffff00 -channels 2 -vf-add screenshot -dvd-device /dev/dvd -af-add export=/tmp/mplayer-af_exporthjwiti:512 mmshttp://85.111.3.55/ntv 
current size = 316 x 17 
Spawn succeeded for filename mmshttp://85.111.3.55/ntv
MPlayer SVN-r31042-Ubuntu-RVM (C) 2000-2010 MPlayer Team
ERROR: mplayer: could not connect to socket

ERROR: mplayer: No such file or directory
Playing mmshttp://85.111.3.55/ntv.
ERROR: Failed to open LIRC support. You will not be able to use your remote control.
STREAM_ASF, URL: mmshttp://85.111.3.55/ntv
Resolving 85.111.3.55 for AF_INET6...
ERROR: Couldn't resolve name for AF_INET6: 85.111.3.55
Connecting to server 85.111.3.55[85.111.3.55]: 80...
ERROR: Server returned 404:Not Found

ERROR: Failed to parse header.
ERROR: Failed, exiting.

ERROR: No stream found to handle url mmshttp://85.111.3.55/ntv
Exiting... (End of file)
Thread completing
playing - http://85.111.3.55/ntv
is playlist 0
media size = 316 x 25
mplayer -quiet -slave -identify -volume 57 -mixer-channel Master -framedrop -noconsolecontrols -noidle -osdlevel 0 -nomouseinput -cache 32 -wid 0x3a00064 -ss 0 -*** -noembeddedfonts -***-font-scale 1,00 -***-color ffffff00 -channels 2 -vf-add screenshot -dvd-device /dev/dvd -af-add export=/tmp/mplayer-af_exportluavfx:512 http://85.111.3.55/ntv 
Spawn succeeded for filename http://85.111.3.55/ntv
current size = 316 x 25 
MPlayer SVN-r31042-Ubuntu-RVM (C) 2000-2010 MPlayer Team
ERROR: mplayer: could not connect to socket
ERROR: mplayer: No such file or directory

ERROR: Failed to open LIRC support. You will not be able to use your remote control.
Playing http://85.111.3.55/ntv.
Resolving 85.111.3.55 for AF_INET6...
ERROR: Couldn't resolve name for AF_INET6: 85.111.3.55
Connecting to server 85.111.3.55[85.111.3.55]: 80...
ERROR: Server returned 404: Not Found
STREAM_ASF, URL: http://85.111.3.55/ntv
Resolving 85.111.3.55 for AF_INET6...
ERROR: Couldn't resolve name for AF_INET6: 85.111.3.55
Connecting to server 85.111.3.55[85.111.3.55]: 80...
Resolving 85.111.3.55 for AF_INET6...
ERROR: Server returned 404:Not Found
Connecting to server 85.111.3.55[85.111.3.55]: 80...
ERROR: Failed to parse header.

ERROR: Failed, exiting.

ERROR: Couldn't resolve name for AF_INET6: 85.111.3.55
Exiting... (End of file)
Thread completing
playing - http://85.111.3.55/ntv
is playlist 1
media size = 316 x 29
mplayer -quiet -slave -identify -volume 57 -mixer-channel Master -framedrop -noconsolecontrols -noidle -osdlevel 0 -nomouseinput -cache 32 -wid 0x3a00064 -ss 0 -*** -noembeddedfonts -***-font-scale 1,00 -***-color ffffff00 -channels 2 -vf-add screenshot -dvd-device /dev/dvd -af-add export=/tmp/mplayer-af_exportptpyan:512 -playlist http://85.111.3.55/ntv 
Spawn succeeded for filename http://85.111.3.55/ntv
current size = 316 x 29 
shutting down threadquery for mms://85.111.3.55/ntv since threaddata->done is TRUE
Resolving 85.111.3.55 for AF_INET6...
ERROR: Couldn't resolve name for AF_INET6: 85.111.3.55
Connecting to server 85.111.3.55[85.111.3.55]: 80...
STREAM_ASF, URL: http://85.111.3.55/ntv
ERROR: Server returned 404: Not Found
Resolving 85.111.3.55 for AF_INET6...
ERROR: Couldn't resolve name for AF_INET6: 85.111.3.55
Connecting to server 85.111.3.55[85.111.3.55]: 80...
ERROR: Server returned 404:Not Found
Resolving 85.111.3.55 for AF_INET6...
ERROR: Failed to parse header.
Connecting to server 85.111.3.55[85.111.3.55]: 80...
ERROR: Failed, exiting.
MPlayer SVN-r31042-Ubuntu-RVM (C) 2000-2010 MPlayer Team
ERROR: Couldn't resolve name for AF_INET6: 85.111.3.55
ID_EXIT=NONE
ERROR: Server returned 404: Not Found
Thread completing
shutting down threadquery for mmshttp://85.111.3.55/ntv since threaddata->done is TRUE
shutting down threadquery for http://85.111.3.55/ntv since threaddata->done is TRUE
shutting down threadquery for http://85.111.3.55/ntv since threaddata->done is TRUE
``````
rifat@rea-pc:~$ gnome-mplayer -v mms://85.111.3.55/ntv
GNOME MPlayer 0.9.9.2
vo = (null) ao = (null)
Running with GIO support
Master Playback is 1
Master Range is 0 to 65536 
Master Current Volume 37356, multiplier = 0,001526
Scaled Volume is 57,000732
Using volume of 57,00
opening mms://85.111.3.55/ntv
is block 0
is character 0
is reg 0
is dir 0
playlist 0
embedded in window id 0x0
playlist detection = 0
adding mms://85.111.3.55/ntv to playlist (cancel = 0)
Using match: type='signal',interface='com.gnome.mplayer'
Using match: type='signal',interface='org.gnome.SettingsDaemon'
Using match: type='signal',interface='org.gnome.SettingsDaemon.MediaKeys'
Proxy connections and Command connected
playing - mms://85.111.3.55/ntv
is playlist 0
media size = 0 x 0
mplayer -quiet -slave -identify -volume 57 -mixer-channel Master -framedrop -noconsolecontrols -noidle -osdlevel 0 -nomouseinput -cache 32 -wid 0x3a00064 -ss 0 -*** -noembeddedfonts -***-font-scale 1,00 -***-color ffffff00 -channels 2 -vf-add screenshot -dvd-device /dev/dvd -af-add export=/tmp/mplayer-af_exportlwinvc:512 mms://85.111.3.55/ntv 
Spawn succeeded for filename mms://85.111.3.55/ntv
current size = 0 x 0 
MPlayer SVN-r31042-Ubuntu-RVM (C) 2000-2010 MPlayer Team
ERROR: mplayer: could not connect to socket

ERROR: mplayer: No such file or directory
Playing mms://85.111.3.55/ntv.
ERROR: Failed to open LIRC support. You will not be able to use your remote control.
STREAM_ASF, URL: mms://85.111.3.55/ntv
ERROR: Couldn't resolve name for AF_INET6: 85.111.3.55
Resolving 85.111.3.55 for AF_INET6...
Connecting to server 85.111.3.55[85.111.3.55]: 1755...
Resolving 85.111.3.55 for AF_INET6...
ERROR: connect error: Connection refused
Connecting to server 85.111.3.55[85.111.3.55]: 80...
ERROR: Couldn't resolve name for AF_INET6: 85.111.3.55
Resolving 85.111.3.55 for AF_INET6...
ERROR: Server returned 404:Not Found
Connecting to server 85.111.3.55[85.111.3.55]: 80...
ERROR: Failed to parse header.
ERROR: Failed, exiting.

ERROR: Couldn't resolve name for AF_INET6: 85.111.3.55

ERROR: Server returned 404: Not Found
Exiting... (End of file)
Thread completing
playing - mmshttp://85.111.3.55/ntv
is playlist 0
media size = 316 x 17
mplayer -quiet -slave -identify -volume 57 -mixer-channel Master -framedrop -noconsolecontrols -noidle -osdlevel 0 -nomouseinput -cache 32 -wid 0x3a00064 -ss 0 -*** -noembeddedfonts -***-font-scale 1,00 -***-color ffffff00 -channels 2 -vf-add screenshot -dvd-device /dev/dvd -af-add export=/tmp/mplayer-af_exportktrome:512 mmshttp://85.111.3.55/ntv 
current size = 316 x 17 
Spawn succeeded for filename mmshttp://85.111.3.55/ntv
MPlayer SVN-r31042-Ubuntu-RVM (C) 2000-2010 MPlayer Team
ERROR: mplayer: could not connect to socket
ERROR: mplayer: No such file or directory
ERROR: Failed to open LIRC support. You will not be able to use your remote control.

Playing mmshttp://85.111.3.55/ntv.
STREAM_ASF, URL: mmshttp://85.111.3.55/ntv
Resolving 85.111.3.55 for AF_INET6...
ERROR: Couldn't resolve name for AF_INET6: 85.111.3.55
Connecting to server 85.111.3.55[85.111.3.55]: 80...

ERROR: Server returned 404:Not Found

ERROR: Failed to parse header.
Thread completing
playing - http://85.111.3.55/ntv
is playlist 0
media size = 316 x 25
mplayer -quiet -slave -identify -volume 57 -mixer-channel Master -framedrop -noconsolecontrols -noidle -osdlevel 0 -nomouseinput -cache 32 -wid 0x3a00064 -ss 0 -*** -noembeddedfonts -***-font-scale 1,00 -***-color ffffff00 -channels 2 -vf-add screenshot -dvd-device /dev/dvd -af-add export=/tmp/mplayer-af_exportiymngg:512 http://85.111.3.55/ntv 
current size = 372 x 28 
Spawn succeeded for filename http://85.111.3.55/ntv
MPlayer SVN-r31042-Ubuntu-RVM (C) 2000-2010 MPlayer Team
ERROR: mplayer: could not connect to socket
ERROR: mplayer: No such file or directory
ERROR: Failed to open LIRC support. You will not be able to use your remote control.

Playing http://85.111.3.55/ntv.
Resolving 85.111.3.55 for AF_INET6...
ERROR: Couldn't resolve name for AF_INET6: 85.111.3.55
Connecting to server 85.111.3.55[85.111.3.55]: 80...
ERROR: Server returned 404: Not Found
STREAM_ASF, URL: http://85.111.3.55/ntv
Resolving 85.111.3.55 for AF_INET6...
ERROR: Couldn't resolve name for AF_INET6: 85.111.3.55
Connecting to server 85.111.3.55[85.111.3.55]: 80...
ERROR: Server returned 404:Not Found
Resolving 85.111.3.55 for AF_INET6...
ERROR: Failed to parse header.
Connecting to server 85.111.3.55[85.111.3.55]: 80...
ERROR: Failed, exiting.
ERROR: Couldn't resolve name for AF_INET6: 85.111.3.55
ERROR: Server returned 404: Not Found

ERROR: No stream found to handle url http://85.111.3.55/ntv

Exiting... (End of file)
Thread completing
playing - http://85.111.3.55/ntv
is playlist 1
media size = 372 x 14
mplayer -quiet -slave -identify -volume 57 -mixer-channel Master -framedrop -noconsolecontrols -noidle -osdlevel 0 -nomouseinput -cache 32 -wid 0x3a00064 -ss 0 -*** -noembeddedfonts -***-font-scale 1,00 -***-color ffffff00 -channels 2 -vf-add screenshot -dvd-device /dev/dvd -af-add export=/tmp/mplayer-af_exportkwytui:512 -playlist http://85.111.3.55/ntv 
Spawn succeeded for filename http://85.111.3.55/ntv
current size = 316 x 22 
Resolving 85.111.3.55 for AF_INET6...
Connecting to server 85.111.3.55[85.111.3.55]: 80...
ERROR: Couldn't resolve name for AF_INET6: 85.111.3.55
shutting down threadquery for mms://85.111.3.55/ntv since threaddata->done is TRUE
ERROR: Server returned 404: Not Found
STREAM_ASF, URL: http://85.111.3.55/ntv
Resolving 85.111.3.55 for AF_INET6...
ERROR: Couldn't resolve name for AF_INET6: 85.111.3.55
Connecting to server 85.111.3.55[85.111.3.55]: 80...
ERROR: Server returned 404:Not Found
ERROR: Failed to parse header.
Resolving 85.111.3.55 for AF_INET6...
ERROR: Failed, exiting.
Connecting to server 85.111.3.55[85.111.3.55]: 80...
ERROR: Couldn't resolve name for AF_INET6: 85.111.3.55
ERROR: Server returned 404: Not Found
ERROR: No stream found to handle url http://85.111.3.55/ntv
MPlayer SVN-r31042-Ubuntu-RVM (C) 2000-2010 MPlayer Team
ERROR: Error while opening playlist file http://85.111.3.55/ntv: Operation now in progress
ERROR: Error parsing option on the command line: -playlist
ID_EXIT=NONE
Thread completing
shutting down threadquery for mmshttp://85.111.3.55/ntv since threaddata->done is TRUE
shutting down threadquery for http://85.111.3.55/ntv since threaddata->done is TRUE
shutting down threadquery for http://85.111.3.55/ntv since threaddata->done is TRUE

```On the other hand, that MMS stream can be played by Winamp and WMP under Windows. Besides, official MMS stream of the state TV can be played by VLC under Ubuntu and gives that kind of log:

**mms://95.0.159.138/TV1**

```
rifat@rea-pc:~$ vlc -vvv mms://95.0.159.138/TV1
VLC media player 1.0.6 Goldeneye
[0x8de1668] main libvlc debug: VLC media player - version 1.0.6 Goldeneye - (c) 1996-2010 the VideoLAN team
[0x8de1668] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--config-cache' '--disable-maintainer-mode' '--disable-update-check' '--enable-fast-install' '--enable-release' '--prefix=/usr' '--with-binary-version=1ubuntu1.2' '--disable-atmo' '--disable-fluidsynth' '--disable-gnomevfs' '--disable-kate' '--disable-mtp' '--enable-x264' '--disable-zvbi' '--enable-a52' '--enable-aa' '--enable-bonjour' '--enable-caca' '--enable-dca' '--enable-dvb' '--enable-dvbpsi' '--enable-dvdnav' '--enable-faad' '--enable-flac' '--enable-freetype' '--enable-fribidi' '--enable-ggi' '--enable-gnutls' '--enable-jack' '--enable-libass' '--enable-libmpeg2' '--enable-lirc' '--enable-live555' '--enable-mad' '--enable-mkv' '--enable-mod' '--enable-mozilla' '--enable-mpc' '--enable-ncurses' '--enable-notify' '--enable-ogg' '--enable-pulse' '--enable-qt4' '--enable-realrtsp' '--enable-sdl' '--enable-shout' '--enable-skins2' '--enable-smb' '--enable-speex' '--enable-svg' '--enable-taglib' '--enable-telx' '--enable-theora' '--enable-twolame' '--enable-vcd' '--enable-vcdx' '--enable-vorbis' '--with-mozilla-pkg=libxul' '--enable-alsa' '--enable-dv' '--enable-pvr' '--enable-v4l' '--enable-v4l2' '--enable-svgalib' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[0x8de1668] main libvlc debug: translation test: code is "C"
[0x8de1668] main libvlc debug: checking plugin modules
[0x8de1668] main libvlc debug: loading plugins cache file /home/rifat/.cache/vlc/plugins-04041e.dat
[0x8de1668] main libvlc debug: recursively browsing `/usr/lib/vlc'
[0x8de1668] main libvlc debug: module bank initialized (380 modules)
[0x8de1668] main libvlc debug: opening config file (/home/rifat/.config/vlc/vlcrc)
[0x8de1668] main libvlc debug: CPU has capabilities 486 586 MMX MMXEXT FPU 
[0x8de1668] main libvlc debug: looking for memcpy module: 3 candidates
[0x8de1668] main libvlc debug: using memcpy module "memcpymmxext"
[0x8e81b78] main input debug: Creating an input for 'Medya Kitapl&#305;&#287;&#305;'
[0x8e81b78] main input debug: Input is a meta file: disabling unneeded options
[0x8e81b78] main input debug: using timeshift granularity of 50 MBytes
[0x8e81b78] main input debug: using timeshift path '/tmp'
[0x8e81b78] main input debug: `file/xspf-open:///home/rifat/.local/share/vlc/ml.xspf' gives access `file' demux `xspf-open' path `/home/rifat/.local/share/vlc/ml.xspf'
[0x8e81b78] main input debug: creating demux: access='file' demux='xspf-open' path='/home/rifat/.local/share/vlc/ml.xspf'
[0x8e85790] main demux debug: looking for access_demux module: 1 candidate
[0x8e85790] main demux warning: no access_demux module matching "file" could be loaded
[0x8e85790] main demux debug: TIMER module_need() : 0,639 ms - Total 0,639 ms / 1 intvls (Avg 0,639 ms)
[0x8e81b78] main input debug: creating access 'file' path='/home/rifat/.local/share/vlc/ml.xspf'
[0x8e87520] main access debug: looking for access module: 3 candidates
[0x8e87520] access_file access debug: opening file `/home/rifat/.local/share/vlc/ml.xspf'
[0x8e87520] main access debug: using access module "access_file"
[0x8e87520] main access debug: TIMER module_need() : 0,600 ms - Total 0,600 ms / 1 intvls (Avg 0,600 ms)
[0x8e95c28] main stream debug: Using AStream*Stream
[0x8e95c28] main stream debug: pre buffering
[0x8e95c28] main stream debug: received first data after 0 ms
[0x8e95c28] main stream debug: pre-buffering done 301 bytes in 0s - 13997 kbytes/s
[0x8e86c48] main stream debug: looking for stream_filter module: 5 candidates
[0x8e86c48] main stream debug: TIMER module_need() : 0,510 ms - Total 0,510 ms / 1 intvls (Avg 0,510 ms)
[0x8e86c48] main stream debug: looking for stream_filter module: 1 candidate
[0x8e86c48] main stream debug: using stream_filter module "stream_filter_record"
[0x8e86c48] main stream debug: TIMER module_need() : 0,172 ms - Total 0,172 ms / 1 intvls (Avg 0,172 ms)
[0x8e81b78] main input debug: creating demux: access='file' demux='xspf-open' path='/home/rifat/.local/share/vlc/ml.xspf'
[0x8e97f40] main demux debug: looking for demux module: 1 candidate
[0x8e97f40] playlist demux debug: using XSPF playlist reader
[0x8e97f40] main demux debug: using demux module "playlist"
[0x8e97f40] main demux debug: TIMER module_need() : 0,339 ms - Total 0,339 ms / 1 intvls (Avg 0,339 ms)
[0x8e81b78] main input debug: `file/xspf-open:///home/rifat/.local/share/vlc/ml.xspf' successfully opened
[0x8e972d8] main xml debug: looking for xml module: 2 candidates
[0x8e972d8] main xml debug: using xml module "xml"
[0x8e972d8] main xml debug: TIMER module_need() : 0,516 ms - Total 0,516 ms / 1 intvls (Avg 0,516 ms)
[0x8e97f40] playlist demux debug: parsed 0 tracks successfully
[0x8e972d8] main xml debug: removing module "xml"
[0x8e81b78] main input debug: EOF reached
[0x8e97f40] main demux debug: removing module "playlist"
[0x8e86c48] main stream debug: removing module "stream_filter_record"
[0x8e87520] main access debug: removing module "access_file"
[0x8e81b78] main input debug: TIMER input launching for 'Medya Kitapl&#305;&#287;&#305;' : 6,447 ms - Total 6,447 ms / 1 intvls (Avg 6,447 ms)
[0x8e80a48] main playlist debug: Activated
[0x8e80a48] main playlist debug: rebuilding array of current - root Oynatma Listesi
[0x8e80a48] main playlist debug: rebuild done - 0 items, index -1
[0x8e87520] main interface debug: looking for interface module: 1 candidate
[0x8e87520] main interface debug: using interface module "hotkeys"
[0x8e87520] main interface debug: TIMER module_need() : 0,356 ms - Total 0,356 ms / 1 intvls (Avg 0,356 ms)
[0x8e87520] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)
[0x8e87520] main interface debug: thread started
[0x8e824d0] main interface debug: looking for interface module: 1 candidate
[0x8e824d0] main interface debug: using interface module "inhibit"
[0x8e824d0] main interface debug: TIMER module_need() : 2,291 ms - Total 2,291 ms / 1 intvls (Avg 2,291 ms)
[0x8e824d0] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)
[0x8e824d0] main interface debug: thread started
[0x8e86630] main interface debug: looking for interface module: 1 candidate
[0x8e86630] main interface debug: using interface module "screensaver"
[0x8e86630] main interface debug: TIMER module_need() : 0,277 ms - Total 0,277 ms / 1 intvls (Avg 0,277 ms)
[0x8e86630] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)
[0x8e86630] main interface debug: thread started
[0x8e80a48] main playlist debug: adding item `mms://95.0.159.138/TV1' ( mms://95.0.159.138/TV1 )
[0x8de1a68] main interface debug: looking for interface module: 1 candidate
[0x8de1a68] main interface debug: using interface module "signals"
[0x8de1a68] main interface debug: TIMER module_need() : 0,248 ms - Total 0,248 ms / 1 intvls (Avg 0,248 ms)
[0x8de1a68] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)
[0x8de1a68] main interface debug: thread started
[0x8de1a68] main interface debug: thread ended
[0x8e99260] main interface debug: looking for interface module: 1 candidate
[0x8e99260] main interface debug: using interface module "globalhotkeys"
[0x8e99260] main interface debug: TIMER module_need() : 18,605 ms - Total 18,605 ms / 1 intvls (Avg 18,605 ms)
[0x8e99260] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)
[0x8de1668] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x8e9c610] main interface debug: looking for interface module: 4 candidates
[0x8e99260] main interface debug: thread started
[0x8e99260] main interface debug: thread ended
[0x8e9c610] main interface debug: using interface module "qt4"
[0x8e9c610] main interface debug: TIMER module_need() : 283,980 ms - Total 283,980 ms / 1 intvls (Avg 283,980 ms)
[0x8e9c610] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)
[0x8e9c610] qt4 interface debug: Error while initializing qt-specific localization
[0x8e9c610] main interface debug: thread started
[0x8e9c610] main interface debug: thread ended
[0x8e80a48] main playlist debug: rebuilding array of current - root Oynatma Listesi
[0x8e80a48] main playlist debug: rebuild done - 1 items, index -1
[0x8e80a48] main playlist debug: processing request item null node Oynatma Listesi skip 0
[0x8e80a48] main playlist debug: starting new item
[0x8e80a48] main playlist debug: creating new input thread
[0xb7301000] main input debug: Creating an input for 'mms://95.0.159.138/TV1'
[0xb7301000] main input debug: thread (input) created at priority 10 (input/input.c:230)
[0xb7301000] main input debug: thread started
[0xb7301000] main input debug: using timeshift granularity of 50 MBytes
[0xb7301000] main input debug: using timeshift path '/tmp'
[0xb7301000] main input debug: `mms://95.0.159.138/TV1' gives access `mms' demux `' path `95.0.159.138/TV1'
[0xb7301000] main input debug: creating demux: access='mms' demux='' path='95.0.159.138/TV1'
[0x916b3f0] main demux debug: looking for access_demux module: 0 candidates
[0x916b3f0] main demux debug: no access_demux module matched "mms"
[0x916b3f0] main demux debug: TIMER module_need() : 0,119 ms - Total 0,119 ms / 1 intvls (Avg 0,119 ms)
[0xb7301000] main input debug: creating access 'mms' path='95.0.159.138/TV1'
[0x916b388] main access debug: looking for access module: 1 candidate
[0x916b388] access_mms access debug: waiting for connection...
[0x916b388] main access debug: net: connecting to 95.0.159.138 port 1755
[0x916b388] main access debug: connection: Operation now in progress
[0x916b388] main access debug: connection succeeded (socket = 21)
[0x916b388] access_mms access debug: connection(tcp) with "95.0.159.138:1755" successful
[0x916b388] access_mms access debug: generated guid: babac001-3757-cf5d-9e53e40b22b1b478
[0x916b388] access_mms access debug: recv command start_sequence:0x00000001 command_id:0xb00bface length:128 len8:16 sequence 0x00000000 len8_II:14 dir_comm:0x00040001
[0x916b388] access_mms access debug: 0x01 --> server_version:"9.01.01.5001" tool_version:"" update_player_url:"" encryption_type:"NTLM"
[0x916b388] access_mms access debug: recv command start_sequence:0x00000001 command_id:0xb00bface length:80 len8:10 sequence 0x00000001 len8_II:8 dir_comm:0x00040002
[0x916b388] access_mms access debug: recv command start_sequence:0x4a000001 command_id:0xb00bface length:136 len8:17 sequence 0x00000002 len8_II:15 dir_comm:0x00040006
[0x916b388] access_mms access debug: media file name/path accepted
[0x916b388] access_mms access debug: answer 0x06 flags:0x02000000 media_length:0s packet_length:1444 packet_count:0 max_bit_rate:356884 header_size:5281
[0x916b388] access_mms access debug: reading header
[0x916b388] access_mms access debug: recv command start_sequence:0x00000001 command_id:0xb00bface length:40 len8:5 sequence 0x00000003 len8_II:3 dir_comm:0x00040011
[0x8e9c610] qt4 interface debug: IM: Setting an input
[0x8e9c610] qt4 interface debug: Updating the geometry
[0x8e9c610] qt4 interface debug: Updating the geometry
[0x916b388] access_mms access debug: header incomplete (1436/5281), reading more
[0x916b388] access_mms access debug: header incomplete (2872/5281), reading more
[0x916b388] access_mms access debug: header incomplete (4308/5281), reading more
[0x916b388] access_mms access debug: header complete(5281)
[0x916b388] access_mms access: selecting stream[0x1] audio (50 kb/s)
[0x916b388] access_mms access: selecting stream[0x2] video (298 kb/s)
[0x916b388] access_mms access debug: recv command start_sequence:0x4a000001 command_id:0xb00bface length:32 len8:4 sequence 0x00000004 len8_II:2 dir_comm:0x00040021
[0x916b388] access_mms access: connection successful
[0x916b388] access_mms access debug: connected to 95.0.159.138:1755
[0x916b388] access_mms access debug: recv command start_sequence:0x4a000001 command_id:0xb00bface length:56 len8:7 sequence 0x00000005 len8_II:5 dir_comm:0x00040005
[0x916b388] access_mms access debug: streaming started
[0x916b388] main access debug: using access module "access_mms"
[0x916b388] main access debug: TIMER module_need() : 237,505 ms - Total 237,505 ms / 1 intvls (Avg 237,505 ms)
[0x916cdd0] main stream debug: Using AStream*Block
[0x916cdd0] main stream debug: pre buffering
[0x916cdd0] main stream debug: received first data after 0 ms
[0x916cdd0] main stream debug: prebuffering done 5281 bytes in 0s - 64465 kbytes/s
[0x916d070] main stream debug: looking for stream_filter module: 5 candidates
[0x916d070] main stream debug: TIMER module_need() : 0,199 ms - Total 0,199 ms / 1 intvls (Avg 0,199 ms)
[0x916d008] main stream debug: looking for stream_filter module: 1 candidate
[0x916d008] main stream debug: using stream_filter module "stream_filter_record"
[0x916d008] main stream debug: TIMER module_need() : 0,106 ms - Total 0,106 ms / 1 intvls (Avg 0,106 ms)
[0xb7301000] main input debug: creating demux: access='mms' demux='' path='95.0.159.138/TV1'
[0x916d138] main demux debug: looking for demux module: 51 candidates
[0x916d008] asf stream debug: found object guid: 0x75b22630-0x668e-0x11cf-0xa6d900aa0062ce6c size:5231
[0x916d008] asf stream debug: read "header object" subobj:7, reserved1:1, reserved2:2
[0x916d008] asf stream debug: found object guid: 0x7bf875ce-0x468d-0x11d1-0x8d82006097c9a2b2 size:38
[0x916d008] asf stream debug: read "stream bitrate properties object"
[0x916d008] asf stream debug:   - stream=1 bitrate=51596
[0x916d008] asf stream debug:   - stream=2 bitrate=305288
[0x916d008] asf stream debug: found object guid: 0x8cabdca1-0xa947-0x11cf-0x8ee400c00c205365 size:104
[0x916d008] asf stream debug: read "file properties object" file_id:0xfe75dc54-0xf228-0x4f3f-0xaf7bcdedbfe73bd5 file_size:5281 creation_date:129275260398430000 data_packets_count:4294967295 play_duration:0 send_duration:0 preroll:5000 flags:9 min_data_packet_size:1444  max_data_packet_size:1444 max_bitrate:356884
[0x916d008] asf stream debug: found object guid: 0x5fbf03b5-0xa92e-0x11cf-0x8ee300c00c205365 size:4405
[0x916d008] asf stream debug: read "header extension object" reserved1:0xabd3d211-0xa9ba-0x11cf-0x8ee600c00c205365 reserved2:6 header_extension_size:4359
[0x916d008] asf stream debug: found object guid: 0x7c4346a9-0xefe0-0x4bfc-0xb229393ede415c85 size:39
[0x916d008] asf stream debug: read "language list object" 1 entries
[0x916d008] asf stream debug:   - 'en-us'
[0x916d008] asf stream debug: found object guid: 0x14e6a5cb-0xc672-0x4332-0x8399a96952065b5a size:88
[0x916d008] asf stream debug: read "extended stream properties object":
[0x916d008] asf stream debug:   - start=0 end=0
[0x916d008] asf stream debug:   - data bitrate=48024 buffer=5000 initial fullness=0
[0x916d008] asf stream debug:   - alternate data bitrate=48024 buffer=5000 initial fullness=0
[0x916d008] asf stream debug:   - maximum object size=1115
[0x916d008] asf stream debug:   - flags=0x0
[0x916d008] asf stream debug:   - stream number=1 language=0
[0x916d008] asf stream debug:   - average time per frame=0
[0x916d008] asf stream debug:   - stream name count=0
[0x916d008] asf stream debug:   - payload extension system count=0
[0x916d008] asf stream debug: found object guid: 0x14e6a5cb-0xc672-0x4332-0x8399a96952065b5a size:132
[0x916d008] asf stream debug: read "extended stream properties object":
[0x916d008] asf stream debug:   - start=0 end=0
[0x916d008] asf stream debug:   - data bitrate=291000 buffer=5000 initial fullness=0
[0x916d008] asf stream debug:   - alternate data bitrate=291000 buffer=5000 initial fullness=0
[0x916d008] asf stream debug:   - maximum object size=0
[0x916d008] asf stream debug:   - flags=0x0
[0x916d008] asf stream debug:   - stream number=2 language=0
[0x916d008] asf stream debug:   - average time per frame=400000
[0x916d008] asf stream debug:   - stream name count=0
[0x916d008] asf stream debug:   - payload extension system count=2
[0x916d008] asf stream debug: found object guid: 0x26f18b5d-0x4584-0x47ec-0x9f5f0e651f0452c9 size:26
[0x916d008] asf stream warning: unknown asf object (not loaded)
[0x916d008] asf stream debug: found object guid: 0xc5f8cbea-0x5baf-0x4877-0x8467aa8c44fa4cca size:224
[0x916d008] asf stream debug: read "metadata object" 4 entries
[0x916d008] asf stream debug:   - IsVBR=0
[0x916d008] asf stream debug:   - DeviceConformanceTemplate=L2
[0x916d008] asf stream debug:   - IsVBR=0
[0x916d008] asf stream debug:   - DeviceConformanceTemplate=MP@ML
[0x916d008] asf stream debug: found object guid: 0x1806d474-0xcadf-0x4509-0xa4ba9aabcb96aae8 size:3850
[0x916d008] asf stream warning: unknown asf object (not loaded)
[0x916d008] asf stream debug: found object guid: 0xb7dc0791-0xa9b7-0x11cf-0x8ee600c00c205365 size:114
[0x916d008] asf stream debug: read "stream Properties object" stream_type:0xf8699e40-0x5b4d-0x11cf-0xa8fd00805f5c442b error_correction_type:0xbfc3cd50-0x618f-0x11cf-0x8bb200aa00b4e220 time_offset:0 type_specific_data_length:28 error_correction_data_length:8 flags:0x1 stream_number:1
[0x916d008] asf stream debug: found object guid: 0xb7dc0791-0xa9b7-0x11cf-0x8ee600c00c205365 size:134
[0x916d008] asf stream debug: read "stream Properties object" stream_type:0xbc19efc0-0x5b4d-0x11cf-0xa8fd00805f5c442b error_correction_type:0x20fb5700-0x5b55-0x11cf-0xa8fd00805f5c442b time_offset:0 type_specific_data_length:56 error_correction_data_length:0 flags:0x2 stream_number:2
[0x916d008] asf stream debug: found object guid: 0xd2d0a440-0xe307-0x11d2-0x97f000a0c95ea850 size:166
[0x916d008] asf stream debug: read "extended content description object"
[0x916d008] asf stream debug:   - 'WMFSDKVersion' = '11.0.5721.5145'
[0x916d008] asf stream debug:   - 'WMFSDKNeeded' = '0.0.0.0000'
[0x916d008] asf stream debug:   - 'IsVBR' = 'false'
[0x916d008] asf stream debug: found object guid: 0x86d15240-0x311d-0x11d0-0xa3a400a0c90348f6 size:240
[0x916d008] asf stream debug: read "codec list object" reserved_guid:0x86d15241-0x311d-0x11d0-0xa3a400a0c90348f6 codec_entries_count:2
[0x916d008] asf stream debug:   - codec[0] audio name:"Windows Media Audio 9.2" description:" 48 kbps, 44 kHz, mono (A/V) 1-pass CBR" information_length:2
[0x916d008] asf stream debug:   - codec[1] video name:"Windows Media Video 9" description:"" information_length:4
[0x916d008] asf stream debug: found object guid: 0x75b22636-0x668e-0x11cf-0xa6d900aa0062ce6c size:50
[0x916d008] asf stream debug: read "data object" file_id:0xfe75dc54-0xf228-0x4f3f-0xaf7bcdedbfe73bd5 total data packet:0 reserved:257
[0x916d008] asf stream debug: + 'Unknown' GUID 0x0-0x0-0x0-0x0000000000000000 size:0pos:0
[0x916d008] asf stream debug:      + 'Header' GUID 0x75b22630-0x668e-0x11cf-0xa6d900aa0062ce6c size:5231pos:0
[0x916d008] asf stream debug:      |    + 'Stream Bitrate Properties' GUID 0x7bf875ce-0x468d-0x11d1-0x8d82006097c9a2b2 size:38pos:30
[0x916d008] asf stream debug:      |    + 'File Properties' GUID 0x8cabdca1-0xa947-0x11cf-0x8ee400c00c205365 size:104pos:68
[0x916d008] asf stream debug:      |    + 'Header Extension' GUID 0x5fbf03b5-0xa92e-0x11cf-0x8ee300c00c205365 size:4405pos:172
[0x916d008] asf stream debug:      |    |    + 'Language List' GUID 0x7c4346a9-0xefe0-0x4bfc-0xb229393ede415c85 size:39pos:218
[0x916d008] asf stream debug:      |    |    + 'Extended Stream Properties' GUID 0x14e6a5cb-0xc672-0x4332-0x8399a96952065b5a size:88pos:257
[0x916d008] asf stream debug:      |    |    + 'Extended Stream Properties' GUID 0x14e6a5cb-0xc672-0x4332-0x8399a96952065b5a size:132pos:345
[0x916d008] asf stream debug:      |    |    + 'Unknown' GUID 0x26f18b5d-0x4584-0x47ec-0x9f5f0e651f0452c9 size:26pos:477
[0x916d008] asf stream debug:      |    |    + 'Metadata' GUID 0xc5f8cbea-0x5baf-0x4877-0x8467aa8c44fa4cca size:224pos:503
[0x916d008] asf stream debug:      |    |    + 'Padding' GUID 0x1806d474-0xcadf-0x4509-0xa4ba9aabcb96aae8 size:3850pos:727
[0x916d008] asf stream debug:      |    + 'Stream Properties' GUID 0xb7dc0791-0xa9b7-0x11cf-0x8ee600c00c205365 size:114pos:4577
[0x916d008] asf stream debug:      |    + 'Stream Properties' GUID 0xb7dc0791-0xa9b7-0x11cf-0x8ee600c00c205365 size:134pos:4691
[0x916d008] asf stream debug:      |    + 'Extended content description' GUID 0xd2d0a440-0xe307-0x11d2-0x97f000a0c95ea850 size:166pos:4825
[0x916d008] asf stream debug:      |    + 'Codec List' GUID 0x86d15240-0x311d-0x11d0-0xa3a400a0c90348f6 size:240pos:4991
[0x916d008] asf stream debug:      + 'Data' GUID 0x75b22636-0x668e-0x11cf-0xa6d900aa0062ce6c size:50pos:5231
[0x916d138] asf demux debug: found 2 streams
[0xb7301000] main input debug: selecting program id=0
[0x916d138] asf demux debug: added new audio stream(codec:0x161,ID:1)
[0x916d138] asf demux debug: added new video stream(ID:2)
[0x916cdd0] main stream warning: 0 bytes need to be skipped (access non seekable)
[0x916d138] main demux debug: using demux module "asf"
[0x916d138] main demux debug: TIMER module_need() : 28,358 ms - Total 28,358 ms / 1 intvls (Avg 28,358 ms)
[0xb73016f0] main decoder debug: looking for decoder module: 31 candidates
[0xb73016f0] avcodec decoder debug: libavcodec initialized (interface 0x341401)
[0xb73016f0] avcodec decoder debug: ffmpeg codec (Windows Media Audio 2) started
[0xb73016f0] avcodec decoder debug: Using 192000 bytes output buffer
[0xb73016f0] main decoder debug: using decoder module "avcodec"
[0xb73016f0] main decoder debug: TIMER module_need() : 36,821 ms - Total 36,821 ms / 1 intvls (Avg 36,821 ms)
[0xb73016f0] main decoder debug: thread (decoder) created at priority 5 (input/decoder.c:315)
[0xb73016f0] main decoder debug: thread started
[0x917a6c8] main decoder debug: looking for decoder module: 31 candidates
[0x917a6c8] avcodec decoder debug: libavcodec already initialized
[0x917a6c8] avcodec decoder debug: ffmpeg codec (Windows Media Video 3) started
[0x917a6c8] main decoder debug: using decoder module "avcodec"
[0x917a6c8] main decoder debug: TIMER module_need() : 12,758 ms - Total 12,758 ms / 1 intvls (Avg 12,758 ms)
[0x917a6c8] main decoder debug: thread (decoder) created at priority 0 (input/decoder.c:315)
[0x917a6c8] main decoder debug: thread started
[0x916b388] access_mms access warning: unimplemented query in control
[0xb7301000] main input debug: `mms://95.0.159.138/TV1' successfully opened
[0xb7301000] main input debug: Buffering 0%
[0xb7301000] main input debug: no usable vout present, spawning one
[0x91bdd90] main spu text debug: looking for text renderer module: 2 candidates
[0xb7301000] main input debug: Buffering 1%
[0xb7301000] main input debug: Buffering 2%
[0x929daf0] main generic debug: thread (fontlist builder) created at priority 0 (freetype.c:480)
[0x91bdd90] freetype spu text debug: using fontsize: 2
[0x91bdd90] main spu text debug: using text renderer module "freetype"
[0x91bdd90] main spu text debug: TIMER module_need() : 1,868 ms - Total 1,868 ms / 1 intvls (Avg 1,868 ms)
[0x9290ee8] main scale debug: looking for video filter2 module: 17 candidates
[0x9290ee8] swscale scale debug: 32x32 chroma: YUVA -> 16x16 chroma: YUVA with scaling using Bicubic (good quality)
[0x9290ee8] main scale debug: using video filter2 module "swscale"
[0x9290ee8] main scale debug: TIMER module_need() : 2,177 ms - Total 2,177 ms / 1 intvls (Avg 2,177 ms)
[0x929e840] main scale debug: looking for video filter2 module: 17 candidates
[0xb7301000] main input debug: Buffering 2%
[0x929e840] yuvp scale debug: YUVP to YUVA converter
[0x929e840] main scale debug: using video filter2 module "yuvp"
[0x929e840] main scale debug: TIMER module_need() : 2,552 ms - Total 2,552 ms / 1 intvls (Avg 2,552 ms)
[0x929daf0] main generic debug: thread started
[0x929daf0] freetype generic debug: Building font database...
[0x929daf0] freetype generic debug: Finished building font database.
[0x929daf0] freetype generic debug: Took 595 microseconds
[0x929daf0] main generic debug: thread ended
[0xb7301000] main input debug: Buffering 4%
[0xb73016f0] avcodec decoder warning: Physical channel configuration not set : guessing
[0x928d908] main video output debug: window size: 384x288
[0x928d908] main video output debug: looking for video output module: 7 candidates
[0xb7301000] main input debug: Buffering -23%
[0xb7301000] main input debug: Buffering -17%
[0x928d908] xvideo video output debug: adaptor 0, port 361, format 0x32315659 (YV12) planar
[0x9361de0] main window debug: looking for xwindow module: 3 candidates
[0x9361de0] qt4 window debug: requesting video...
[0xb7301000] main input debug: Buffering -13%
[0x8e9c610] qt4 interface debug: Updating the geometry
[0x8e9c610] qt4 interface debug: Updating the geometry
[0x8e9c610] qt4 interface debug: Updating the geometry
[0x8e9c610] qt4 interface debug: Updating the geometry
[0x8e9c610] qt4 interface debug: Updating the geometry
[0x8e9c610] qt4 interface debug: Updating the geometry
[0x8e9c610] qt4 interface debug: Updating the geometry
[0x8e9c610] qt4 interface debug: Updating the geometry
[0x8e9c610] qt4 interface debug: Updating the geometry
[0x8e9c610] qt4 interface debug: Updating the geometry
[0x8e9c610] qt4 interface debug: Video was requested -1, -1
[0x8e9c610] qt4 interface debug: Video is resizing to: 384 288
[0x8e9c610] qt4 interface debug: Updating the geometry
[0x9361de0] main window debug: using xwindow module "qt4"
[0x9361de0] main window debug: TIMER module_need() : 160,261 ms - Total 160,261 ms / 1 intvls (Avg 160,261 ms)
[0x928d908] xvideo video output debug: XShm video extension v1.1 (without pixmaps, opcode: 143)
[0x928d908] xvideo video output debug: Window manager supports NetWM
[0x928d908] xvideo video output debug: Window manager supports _NET_WM_STATE_FULLSCREEN
[0x928d908] xvideo video output debug: Window manager supports _NET_WM_STATE_ABOVE
[0x928d908] xvideo video output debug: Window manager supports _NET_WM_STATE_BELOW
[0x928d908] main video output debug: using video output module "xvideo"
[0x928d908] main video output debug: TIMER module_need() : 260,794 ms - Total 260,794 ms / 1 intvls (Avg 260,794 ms)
[0x928d908] main video output debug: Deinterlacing available
[0x928d908] main video output debug: got 16 direct buffer(s)
[0x928d908] main video output debug: pic render sz 384x288, of (0,0), vsz 384x288, 4cc I420, ar 4:3, sar 1:1, msk r0x0 g0x0 b0x0
[0x928d908] main video output debug: pic in sz 384x288, of (0,0), vsz 384x288, 4cc I420, ar 4:3, sar 1:1, msk r0x0 g0x0 b0x0
[0x928d908] main video output debug: pic out sz 384x288, of (0,0), vsz 384x288, 4cc I420, ar 4:3, sar 1:1, msk r0x0 g0x0 b0x0
[0x928d908] main video output debug: direct render, mapping render pictures 0-14 to system pictures 1-15
[0x917a6c8] main decoder debug: End of video preroll
[0x917a6c8] main decoder debug: Received first picture
[0xb7301000] main input debug: creating aout
[0x9363040] main audio output debug: looking for audio output module: 4 candidates
[0x9363040] pulse audio output: No. of Audio Channels: 1
[0x928d908] main video output debug: Post-processing available
[0x9363040] pulse audio output debug: Pulse mainloop started
[0x9363040] pulse audio output debug: Pulse stream connected
[0x9363040] pulse audio output debug: Pulse initialized successfully
[0x9363040] pulse audio output debug: Buffer metrics: maxlength=70560, tlength=21168, prebuf=17640, minreq=3528
[0x9363040] pulse audio output debug: Using sample spec 'float32le 1ch 44100Hz', channel map 'mono'.
[0x9363040] pulse audio output debug: Connected to device alsa_output.pci-0000_00_1b.0.analog-stereo (0, not suspended).
[0x9363040] main audio output debug: using audio output module "pulse"
[0x9363040] main audio output debug: TIMER module_need() : 92,644 ms - Total 92,644 ms / 1 intvls (Avg 92,644 ms)
[0x9363040] main audio output debug: output 'fl32' 44100 Hz Mono frame=1 samples/4 bytes
[0x9363040] main audio output debug: mixer 'fl32' 44100 Hz Mono frame=1 samples/4 bytes
[0x9363040] main audio output debug: no need for any filter
[0x9363040] main audio output debug: looking for audio mixer module: 3 candidates
[0x9363040] main audio output debug: using audio mixer module "float32_mixer"
[0x9363040] main audio output debug: TIMER module_need() : 0,839 ms - Total 0,839 ms / 1 intvls (Avg 0,839 ms)
[0x9363040] main audio output debug: input 's16l' 44100 Hz Mono frame=1 samples/2 bytes
[0x9371760] main audio filter debug: looking for audio filter module: 1 candidate
[0x9371760] scaletempo audio filter warning: bad input or output format
[0x9371760] scaletempo audio filter warning: input and output formats are not similar
[0x9371760] main audio filter warning: no audio filter module matching "scaletempo" could be loaded
[0x9371760] main audio filter debug: TIMER module_need() : 1,006 ms - Total 1,006 ms / 1 intvls (Avg 1,006 ms)
[0x9371760] main audio filter debug: looking for audio filter module: 1 candidate
[0x9371760] scaletempo audio filter debug: format: 44100 rate, 1 nch, 4 bps, fl32
[0x9371760] scaletempo audio filter debug: params: 30 stride, 0,200 overlap, 14 search
[0x9371760] scaletempo audio filter debug: 1,000 scale, 1323,000 stride_in, 1323 stride_out, 1059 standing, 264 overlap, 617 search, 2204 queue, fl32 mode
[0x9371760] main audio filter debug: using audio filter module "scaletempo"
[0x9371760] main audio filter debug: TIMER module_need() : 0,411 ms - Total 0,411 ms / 1 intvls (Avg 0,411 ms)
[0x9363040] main audio output debug: filter(s) 's16l'->'fl32' 44100 Hz->44100 Hz Mono->Mono
[0x936cb60] main audio output debug: looking for audio filter module: 24 candidates
[0x936cb60] main audio output debug: using audio filter module "converter_float"
[0x936cb60] main audio output debug: TIMER module_need() : 2,404 ms - Total 2,404 ms / 1 intvls (Avg 2,404 ms)
[0x9363040] main audio output debug: found a filter for the whole conversion
[0x9363040] main audio output debug: filter(s) 'fl32'->'fl32' 44100 Hz->44100 Hz Mono->Mono
[0x93ae860] main audio output debug: looking for audio filter module: 24 candidates
[0x93ae860] main audio output debug: using audio filter module "trivial_channel_mixer"
[0x93ae860] main audio output debug: TIMER module_need() : 0,424 ms - Total 0,424 ms / 1 intvls (Avg 0,424 ms)
[0x9363040] main audio output debug: found a filter for the whole conversion
[0x9363040] main audio output debug: filter(s) 'fl32'->'fl32' 48510 Hz->44100 Hz Mono->Mono
[0x936f628] main audio output debug: looking for audio filter module: 24 candidates
[0x936f628] main audio output debug: using audio filter module "bandlimited_resampler"
[0x936f628] main audio output debug: TIMER module_need() : 0,251 ms - Total 0,251 ms / 1 intvls (Avg 0,251 ms)
[0x9363040] main audio output debug: found a filter for the whole conversion
[0xb73016f0] main decoder debug: End of audio preroll
[0x928d908] qt4 video output debug: Qt: Entering Fullscreen
QPainter::begin: Paint device returned engine == 0, type: 1
[0xb7301000] main input debug: Buffering -6%
[0xb7301000] main input debug: Buffering 0%
[0xb7301000] main input debug: Buffering 5%
[0xb7301000] main input debug: Buffering 12%
[0xb7301000] main input debug: Buffering 18%
[0xb7301000] main input debug: Buffering 24%
[0xb7301000] main input debug: Buffering 30%
[0xb7301000] main input debug: Buffering 36%
[0xb7301000] main input debug: Buffering 42%
[0xb7301000] main input debug: Buffering 48%
[0xb7301000] main input debug: Buffering 55%
[0xb7301000] main input debug: Buffering 61%
[0x91bdd90] freetype spu text debug: using fontsize: 18
[0xb7309108] main blend debug: looking for video blending module: 1 candidate
[0xb7309108] blend blend debug: chroma: YUVA -> I420
[0xb7309108] main blend debug: using video blending module "blend"
[0xb7309108] main blend debug: TIMER module_need() : 1,072 ms - Total 1,072 ms / 1 intvls (Avg 1,072 ms)
[0xb7301000] main input debug: Buffering 65%
[0xb7301000] main input debug: Buffering 72%
[0xb7301000] main input debug: Buffering 76%
[0xb7301000] main input debug: Buffering 82%
[0xb7301000] main input debug: Buffering 90%
[0xb7301000] main input debug: Buffering 96%
[0xb7301000] main input debug: Stream buffering done (3090 ms in 4064 ms)
[0xb7301000] main input debug: Decoder buffering done in 0 ms
[0x9363040] main audio output warning: PTS is out of range (708095), dropping buffer
[0x9363040] main audio output warning: PTS is out of range (615280), dropping buffer
[0x9363040] main audio output warning: PTS is out of range (522195), dropping buffer
[0x9363040] main audio output warning: PTS is out of range (429350), dropping buffer
[0x9363040] main audio output warning: PTS is out of range (383261), dropping buffer
[0x9363040] main audio output warning: PTS is out of range (290532), dropping buffer
[0x9363040] main audio output warning: PTS is out of range (197988), dropping buffer
[0x9363040] main audio output warning: PTS is out of range (105222), dropping buffer
[0x9363040] main audio output warning: PTS is out of range (12599), dropping buffer
[0x9363040] pulse audio output debug: Pulse stream started
[0x9363040] main audio output warning: output date isn't PTS date, requesting resampling (44988)
[0x9363040] main audio output warning: buffer is 45024 late, triggering upsampling
``````
rifat@rea-pc:~$ vlc -v mms://95.0.159.138/TV1
VLC media player 1.0.6 Goldeneye
[0x9a86728] main demux warning: no access_demux module matching "file" could be loaded
[0x99e2668] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x9d69a40] access_mms access: selecting stream[0x1] audio (50 kb/s)
[0x9d69a40] access_mms access: selecting stream[0x2] video (298 kb/s)
[0x9d69a40] access_mms access: connection successful
[0x9d7cb58] asf stream warning: unknown asf object (not loaded)
[0x9d7cb58] asf stream warning: unknown asf object (not loaded)
[0x9d73320] main stream warning: 0 bytes need to be skipped (access non seekable)
[0x9d69a40] access_mms access warning: unimplemented query in control
[0x9d89000] avcodec decoder warning: Physical channel configuration not set : guessing
[0xb741edb8] pulse audio output: No. of Audio Channels: 1
[0x9e6bd08] scaletempo audio filter warning: bad input or output format
[0x9e6bd08] scaletempo audio filter warning: input and output formats are not similar
[0x9e6bd08] main audio filter warning: no audio filter module matching "scaletempo" could be loaded
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[0xb741edb8] main audio output warning: PTS is out of range (-9943), dropping buffer
[0xb741edb8] main audio output warning: buffer is 46682 in advance, triggering downsampling

```So, two different MMS stream and one of them can be played and the other does not. It seems that it is a codec problem; however all the packages of GStreamer are installed in the system.

Any suggestion?...

Thank you...

---

### Post by Virus666 on 2010-09-04
Bump... Any idea?

---

### Post by mc4man on 2010-09-04
> It seems that it is a codec problem
It's not a codec issue, so I wouldn't waste time there.
It's more of an access problem, that station is requiring wmp.
Whether you can find a way around not too sure, possibly a browser ext. or user-agent string. (semi-doubtful

Otherwise use windows and or ask the station to open up the stream to all users ( after all it is a national station..

---

### Post by Virus666 on 2010-09-07
I almost solved this problem by using **WMP 10** via **Wine 1.3.1** in **PlayOnLinux**. Thanks all...

---

