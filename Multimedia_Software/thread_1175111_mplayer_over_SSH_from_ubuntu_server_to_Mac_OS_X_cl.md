---
title: "mplayer over SSH from ubuntu server to Mac OS X client"
date: 2009-05-31
forum: Multimedia Software
---

### Post by reg2117 on 2009-05-31
Forum Members,
   I am attempting to forward a webcam output over SSH from a ubuntu server to a MacBook running OS X. I would like to open mplayer on the Mac.

   Using the following code in the mac terminal:
```
ssh -C -X me@myip konsole
```
opens a konsole terminal from which I am able to open GUI programs, including kopete, and test the webcam and video forwarding. The video forwarding appears to be working fine for my purposes. 

When I attempt to open the webcam using mplayer on the client side (Mac):
```
mplayer tv:// -tv driver=v4l:width=352:height=288:device=/dev/video0
```
I get the following output:
```
Xlib:  extension "XFree86-VidModeExtension" missing on display "localhost:10.0".
xscreensaver_disable: Could not find XScreenSaver window.
[VO_XV] It seems there is no Xvideo support for your video card available.
[VO_XV] Run 'xvinfo' to verify its Xv support and read
[VO_XV] DOCS/HTML/en/video.html#xv!
[VO_XV] See 'mplayer -vo help' for other (non-xv) video out drivers.
[VO_XV] Try -vo x11.
Error opening/initializing the selected video_out (-vo) device.



MPlayer interrupted by signal 11 in module: free_demuxer
- MPlayer crashed by bad usage of CPU/FPU/RAM.
 Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
 disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
- MPlayer crashed. This shouldn't happen.
 It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
 gcc version. If you think it's MPlayer's fault, please read
 DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
 won't help unless you provide this information when reporting a possible bug.
```

If I run the same command on the server (linux machine) directly, the output looks like this (and mplayer opens and displays the webcam well)
```
mplayer opens and the command line output is:
==========================================================================
Opening video decoder: [raw] RAW Uncompressed Video
VDec: vo config request - 352 x 288 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 352x288 => 352x288 Planar YV12
Selected video codec: [rawyv12] vfm: raw (RAW YV12)
==========================================================================
Audio: no sound
Starting playback...
```

I have tried the -vo X11 suggestion in the error output. Also,  xvinfo returns:
```
X-Video Extension version 2.2
screen #0
 no adaptors present
```

There are related threads looking at SSH forwarding and mplayer:
[http://ubuntuforums.org/showthread.php?t=56107](http://ubuntuforums.org/showthread.php?t=56107)
[http://ubuntuforums.org/showthread.php?t=953605](http://ubuntuforums.org/showthread.php?t=953605)
From suggestions in these threads, I have tried:
```
export DISPLAY=:0
mplayer tv:// -tv driver=v4l:width=352:height=288:device=/dev/video0
```
but this seems to open an mplayer on the server side (linux machine).

I suspect the -X forwarding is the way to go and I need to set the -display options correctly. The man page is cryptic:
```
-display <name>
    Specify the hostname and display number of the X server you want to display on.

    EXAMPLE:

-display xtest.localdomain:0
```

The command (on the client side running Mac)
```
echo $DISPLAY
``` 
returns
```
/tmp/launch-CG2FOS/:0
```


**Any suggestions would be helpful.**

---

