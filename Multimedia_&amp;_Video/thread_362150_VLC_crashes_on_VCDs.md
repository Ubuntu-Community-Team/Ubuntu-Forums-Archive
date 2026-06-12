---
title: "VLC crashes on VCDs?"
date: 2007-02-15
forum: Multimedia &amp; Video
---

### Post by eilu on 2007-02-15
VLC crashes when I try to open a VCD, which is ironic because I got it to play VCDs with! It keeps returning 'Segmentation Fault' in terminal. Any ideas? I'm using v0.8.4

edit: i ran it with increased verbosity and this is what I get:
```
foo@bar:~$ vlc -vvvv
VLC media player 0.8.4 Janus
[00000001] main vlc debug: opening config file /home/eilu/.vlc/vlcrc
[00000001] main vlc debug: checking builtin modules
[00000001] main vlc debug: checking plugin modules
[00000001] main vlc debug: loading plugins cache file /home/eilu/.vlc/cache/plugins-04041e.dat
[00000001] main vlc debug: recursively browsing `modules'
[00000001] main vlc debug: recursively browsing `/usr/lib/vlc'
[00000001] main vlc debug: recursively browsing `plugins'
[00000001] main vlc debug: module bank initialized, found 206 modules
[00000001] main vlc debug: opening config file /home/eilu/.vlc/vlcrc
[00000001] main vlc debug: CPU has capabilities 486 586 MMX MMXEXT SSE SSE2 FPU
[00000001] main vlc debug: looking for memcpy module: 1 candidate
[00000180] main module debug: using memcpy module "memcpy"
[00000262] main playlist debug: waiting for thread completion
[00000262] main playlist debug: thread 3082001328 (playlist) created at priority 0 (src/playlist/playlist.c:183)
[00000263] main private debug: waiting for thread completion
[00000263] main private debug: thread 3073608624 (preparser) created at priority 0 (src/playlist/playlist.c:205)
[00000264] main interface debug: looking for interface module: 1 candidate
[00000124] main module debug: using interface module "hotkeys"
[00000264] main interface debug: interface initialized
[00000264] main interface debug: thread 3065215920 (interface) created at priority 0 (src/interface/interface.c:211)
[00000266] main interface debug: looking for interface module: 6 candidates
[00000171] main module debug: using interface module "screensaver"
[00000266] main interface debug: interface initialized
[00000266] main interface debug: thread 3055549360 (interface) created at priority 0 (src/interface/interface.c:211)
[00000268] main interface debug: looking for interface module: 5 candidates
[00000016] main module debug: using interface module "wxwidgets"
[00000268] main interface debug: interface initialized
[00000268] main interface debug: thread 3032005552 (manager) created at priority 0 (src/interface/interface.c:196)

(process:7353): Gdk-WARNING **: locale not supported by Xlib

(process:7353): Gdk-WARNING **: cannot set locale modifiers
[00000268] wxwidgets interface debug: Using last windows config '(-1,0,0,1280,800)(0,35,8,402,85)'
[00000268] wxwidgets interface debug: id=0 p=(35,8) s=(402,85)
[00000262] main playlist debug: adding playlist item `vcdx:///dev/cdrom' ( vcdx:///dev/cdrom )
[00000262] main playlist debug: creating new input thread
[00000271] main input debug: set input option: audio-track to 0
[00000271] main input debug: waiting for thread completion
[00000271] main input debug: thread 3008289712 (input) created at priority 0 (src/input/input.c:230)
[00000271] main input debug: `vcdx:///dev/cdrom' gives access `vcdx' demux `' path `/dev/cdrom'
[00000271] main input debug: creating demux: access='vcdx' demux='' path='/dev/cdrom'
[00000272] main demuxer debug: looking for access_demux module: 0 candidates
[00000272] main demuxer warning: no access_demux module matched "vcdx"
[00000271] main input debug: creating access 'vcdx' path='/dev/cdrom'
[00000273] main access debug: looking for access2 module: 5 candidates
Segmentation fault
```
(then it crashes)

---

