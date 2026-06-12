---
title: "Xvid green line + rgb out of sync"
date: 2008-04-28
forum: Multimedia Software
---

### Post by Necromantis on 2008-04-28
Hello all,

I just reinstalled Ubuntu and upgraded it to 8.04 which works great. 
I can't see the difference between 8.04 and 7.10 tbh :pp

Anyway, some video I made recently on Windows using Gordian Knot - latest Xvid codec don't work too well on Ubuntu.

I get a single thick green line in a form of a 'r' on the left of the picture and the RGB is separated on the picture. Obviously this works on windows so I'm not sure where the problem could be?

I have install all the Xvid / Divx codecs I could put my hand on (obviously) + I installed the ubuntu synaptic restricted drivers.

Old Xvid films work no problem - only the one I've done more recently seem to have this problem.

Anyone with a clue ? or even better a fix ? ;)
Thanks

---

### Post by riptreeper on 2008-05-05
I have this same problem in Hardy when trying to play .avi files. They work just fine in Vista with DivX. Could that have something to do with it? 

Thanks in advance. 

Specs in sig.

---

### Post by isaidi on 2008-05-05
I have been having the exact same problem.

Try using VLC, it worked for me.. but i still don't understand why mplayer and totem wouldn't play the same xvid file with out the thick vertical green line on left ? I noticed mplayer was detecting Divx video codec, so i forced xvid using (mplayer -vc xvid) but i still get the thick green line on the left.. and blurry RGB..

oh well.. VLC works for now... but can anyone explain this ?

---

### Post by riptreeper on 2008-05-08
What is VLC and where can I get it? Thanks

---

### Post by isaidi on 2008-05-10
vlc is another popular movie player offered in linux (also windows) that seems to exceed my expectations and play almost anything that fails on all other players.

use the add/remove to install or in terminal

>  sudo apt-get install vlc

[http://www.videolan.org/vlc/](http://www.videolan.org/vlc/)

I did another install of ubuntu and noticed that I only get the thick green line after I install restricted nvidia drivers.. only with certain movies. VLC manages to play them fine however.
My Vid card is nvidia 8400GS

I did some reading on this a while back. i believe this has to do with Xorg extension called X-Video ? i guess I need to tweak my xorg.conf... any tips from anyone? i was hoping i wouldn't delve into xorg tweaking.. everything else works fine in my ubuntu..

---

### Post by Necromantis on 2008-05-19
> **isaidi said:**
> I have been having the exact same problem.

Try using VLC, it worked for me.. but i still don't understand why mplayer and totem wouldn't play the same xvid file with out the thick vertical green line on left ? I noticed mplayer was detecting Divx video codec, so i forced xvid using (mplayer -vc xvid) but i still get the thick green line on the left.. and blurry RGB..

oh well.. VLC works for now... but can anyone explain this ?

Thanks :) this works for me too.

---

### Post by cor2y on 2008-05-19
you don't need vlc you can either replace totem-gstreamer with totem-xine
```
sudo apt-get install totem-xine;sudo update-alternatives --config totem
```
Select totem-xine instead of totem-gstreamer
or
Recompile the gstreamer-ffmpeg plugin,
[http://ubuntuforums.org/showthread.php?t=799065](http://ubuntuforums.org/showthread.php?t=799065)
Theres a problem with how the plugin (the version of ffmpeg used while stable is probably too old) is rendering mpeg4 video ,it neeeds to be updated and that won't happen probably until the next version of ubuntu.

---

### Post by isaidi on 2008-06-01
thanks cor2y, 
usimg totem-xine is just avoiding the problem, as is using VLC. Or disabling xv in gstreamer-properties, like some other threads recomended.
some threads also recommended using xvattr to adjust xv settings, but that didn't work for me, as one of the color layers seems to be shifted to the right, which creates the green line and the blur. See attached screenshots.

I think the problem lies specifically with using xv video output for certain codecs and only while using nvidia drivers.
I have the same problem with my mythbuntu install also, which doesn't have gstreamer installed.

i have several video files of the same problem. but not all of them.
Here is tcprobe of one of them (also screen shot attached):
```

$ tcprobe -i file.ave
[tcprobe] RIFF data, AVI video
[avilib] V: 23.976 fps, codec=DX50, frames=163073, width=664, height=274
[avilib] A: 48000 Hz, format=0x55, bits=0, channels=2, bitrate=112 kbps,
[avilib]    163062 chunks, 95221056 bytes, CBR
[tcprobe] summary for file.avi, (*) = not default, 0 = not detected
import frame size: -g 664x274 [720x576] (*)
       frame rate: -f 23.976 [25.000] frc=1 (*)
      audio track: -a 0 [0] -e 48000,0,2 [48000,16,2] -n 0x55 [0x2000] (*)
                   bitrate=112 kbps
           length: 163073 frames, frame_time=41 msec, duration=1:53:21.509

```



mplayer output when planing file
```

$> mplayer file.avi 
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 4400+ (Family: 15, Model: 107, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

file.avi.
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [DX50]  664x274  12bpp  23.976 fps  743.2 kbps (90.7 kbyte/s)
Clip info:
 Software: VirtualDubMod 1.5.10.1 (build 2366/release)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
[VO_XV] Could not grab port 280.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 112.0 kbit/7.29% (ratio: 14000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [pulse] Failed to connect to server: Connection refused
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 664 x 274 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 2.42:1 - prescaling to correct movie aspect.
VO: [xv] 664x274 => 664x274 Planar YV12 


```

I tried  running the file with different video output devices:

X11 with SHM extension (video works fine but no scaling )
```

mplayer -vo x11  <file-name>

```

opengl video out works fine (with scaling)
```

mplayer -vo gl <filename>

```
```

mplayer -vo gl2 <filename>

```

this must be a bug when playing back a video with the following present:
  1.)  FFmpeg MPEG-4 (DX50) codec video
  2.) using xv output in nvidia xorg drivers

help? ideas? anyone ?

---

### Post by Necromantis on 2008-06-02
Would the problem not be with the people developing mmplayer?

Nvidia driver + Xvid 1.1 codec = green line on mmplayer

Nvidia driver + Xvid 1.1 codec = No green line on VLC

---

### Post by quantumstitch on 2008-07-26
I just noticed this today after installing xgl-xserver. Some XVID avi's had this problem others didn't. I just removed xgl and libglitz and fixed it. Just a little more information for others.

```

sudo apt-get remove xserver-xgl libglitz-glx1 libglitz1

```

This wasn't a problem using restricted drivers for me.

---

### Post by Jimorie on 2008-10-26
I have this problem and none of the fixes in this thread have worked for me.

Any news?

---

### Post by FuturePilot on 2008-10-31
I've got the same problem. Nvidia GeForce 8400. Nothing I've tried works except using a Xine based player. :confused:

---

### Post by vinnie1 on 2008-11-11
Hi

New install 8.10

Everything was ok untill the other day when this problem started.

Is anybody working on a fix ??

I have tried vlc, but thats not working either.


HELP

---

### Post by vinnie1 on 2008-11-11
I have found a work around, in mplayer at least.

In mplayer preferences, go to the video tab and change the driver.

I chose gl2 from the list and that seems to work.


 Hope this helps someone

---

### Post by QuaxEros on 2009-01-10
Thanks Vinnie1 !!!

For me your solution worked fine.
The GL2 driver in MPlayer solved the green line and the rgb offset.
The GL driver gave me a better image though especially when there is a lot of movement (panning or moving shot).

Btw... SMPlayer is a great frontend to MPlayer. All the advanced options i was missing are there.

VLC had the same green line and rgb offset but when using the openGL output driver VLC crashed.
The X11 driver got rid of the problem though.


_______________________________________________________________________
Dell XPS M1530 / GeForce 8600M GT / NVidia Driver 177.82 / Kubuntu 8.10

---

