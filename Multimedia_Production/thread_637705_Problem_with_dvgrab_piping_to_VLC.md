---
title: "Problem with dvgrab piping to VLC"
date: 2007-12-11
forum: Multimedia Production
---

### Post by theacoustician on 2007-12-11
There seems to be a problem with dvgrab piping streams.

Here's the command line I'm using:

dvgrab -f dv2 - | vlc - -vvv :demux=rawdv --no-sub-autodetect-file

And here's the result:

VLC media player 0.8.6c Janus
<00000001> main private debug: checking builtin modules
<00000001> main private debug: checking plugin modules
<00000001> main private debug: loading plugins cache file /home/scolsen/.vlc/cache/plugins-04081e.dat
<00000001> main private debug: recursively browsing `modules'
<00000001> main private debug: recursively browsing `/usr/lib/vlc'
<00000001> main private debug: recursively browsing `plugins'
<00000001> main private debug: module bank initialized, found 223 modules
<00000001> main private debug: opening config file /home/scolsen/.vlc/vlcrc
<00000001> main private debug: CPU has capabilities 486 586 MMX MMXEXT SSE SSE2 FPU 
<00000001> main private debug: looking for memcpy module: 3 candidates
<00000001> main private debug: using memcpy module "memcpymmxext"
<00000287> main playlist debug: waiting for thread completion
<00000287> main playlist debug: thread 1082132816 (playlist) created at priority 0 (playlist/playlist.c:184)
<00000288> main private debug: waiting for thread completion
<00000288> main private debug: thread 1090525520 (preparser) created at priority 0 (playlist/playlist.c:210)
<00000289> main interface debug: looking for interface module: 1 candidate
<00000289> main interface debug: using interface module "hotkeys"
<00000289> main interface debug: thread 1098918224 (interface) created at priority 0 (interface/interface.c:231)
<00000291> main interface debug: looking for interface module: 1 candidate
<00000291> main interface debug: using interface module "screensaver"
<00000291> main interface debug: thread 1107310928 (interface) created at priority 0 (interface/interface.c:231)
<00000287> main playlist debug: adding playlist item `-' ( - )
<00000293> main interface debug: looking for interface module: 5 candidates
<00000293> main interface debug: using interface module "wxwidgets"
<00000293> main interface debug: thread 1115703632 (manager) created at priority 0 (interface/interface.c:216)
<00000293> wxwidgets interface debug: Using last windows config '(-1,0,0,1280,800)(0,56,91,720,568)(6,0,0,-1,150)'
<00000293> wxwidgets interface debug: id=0 p=(56,91) s=(720,568)
<00000293> wxwidgets interface debug: id=6 p=(0,0) s=(-1,150)
<00000287> main playlist debug: nothing requested, starting
<00000287> main playlist debug: creating new input thread
<00000296> main input debug: waiting for thread completion
<00000296> main input debug: creating statistics handler
<00000296> main input debug: thread 1124096336 (input) created at priority 0 (input/input.c:265)
<00000296> main input debug: `-' gives access `' demux `' path `-'
<00000296> main input debug: enforced demux ` rawdv'
<00000296> main input debug: creating access '' path='-'
<00000298> main access debug: looking for access2 module: 5 candidates
<00000298> vcdx access warning: Can't get file status for -:
No such file or directory
Found AV/C device with GUID 0x00008500000498e8

"": buffer underrun near: timecode 781652552:10955:01.00 date 2067.02.15 22:26:25
This error means that the frames could not be written fast enough.
Capture Started
"-001.avi":    16.16 MB 134 frames timecode 2093400400:32767:2093400984.32767 date 2067.02.15 22:26:25
Capture Stopped
Warning: 1 dropped frames.

Segmentation fault (core dumped)


This is on Ubuntu Studio 7.10 and using dvgrab 3.0 and VLC 0.8.6c. The odd thing is that this *used* to work, but I can't track down what's changed. I think it might be something with dvgrab because instead of properly piping to VLC, it seems to be interpreting the "-" as what I want to name the file. As you can see, I end up with a file called "-001.avi". Dvgrab seems to be grabbing the file properly and VLC can play the file properly after the fact, just no communication between the two in real time. Removing the "-" on the dvgrab side of the pipe doesn't seem to help any. Thoughts, ideas, or suggestions?

Thanks.

---

### Post by theacoustician on 2007-12-13
Straight from the developer :
> 
Pipe output is a known regression bug in dvgrab 3.0. Actually, its a combination of capture and pipe simultaneously that's the problem. Version 3.1 is now available and fixes the problem.

+-DRD-+
Lead Kino Developer


DVGrab 3.1 is out there now, but source only.  I'll be trying this out later today and report back.  Hopefully most can figure out how to install it on their own.  I could attempt to write a how-to if anyone needs help.  

Is there any way to let the repository maintainers know there's an update?

---

