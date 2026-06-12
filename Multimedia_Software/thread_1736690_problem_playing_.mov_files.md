---
title: "problem playing .mov files"
date: 2011-04-22
forum: Multimedia Software
---

### Post by sandy0594 on 2011-04-22
Hi all, I am a bit new to Linux operating system..Recently I installed Ubuntu 10.10..I installed SM player as i am bit addicted to it back in windows.But,unfortunately when I am trying to play files with .mov extension the video doesn't appear but I could hear the sound and moreover when I am trying to play the file with Movie Player,it is giving  error
[B]G streamer encountered a general stream error
[/B]
Can anyone kindly explain me why it's happening?

---

### Post by andrew.46 on 2011-04-22
Can you post a link to one of these problem files? Also are you running 64bit Ubuntu?

---

### Post by KegHead on 2011-04-22
Hi!

Have you installed restricted extras?

KegHead

---

### Post by coffeecat on 2011-04-22
Try installing VLC and see if that can cope with your mov videos. VLC is one of the best media players and there is a Windows (and Mac) version should you want it.

---

### Post by sandy0594 on 2011-04-23
Thanks for all your replies..Mine is a 32-bit O.S,One can't install too many software's.In windows SM player plays everything.So,is there anyway to get SM player working for the .mov extension..
For some file extensions SM player is giving only sound but no video and here is the case too with .mov extension..
Can someone suggest me how to make SM player working..
My filename is "**0101 - About this Course.mov**"

---

### Post by fdrake on 2011-04-23
> **sandy0594 said:**
> 
My filename is "**0101 - About this Course.mov**"

are u playing Linda.com movie? that's cool.
i think ur missing the codecs for mp4 . try [this page ]("http://ubuntuforums.org/showthread.php?t=437624")

---

### Post by andrew.46 on 2011-04-23
> **sandy0594 said:**
> Thanks for all your replies..Mine is a 32-bit O.S,One can't install too many software's.In windows SM player plays everything.So,is there anyway to get SM player working for the .mov extension..

The problem is that 'mov' is a *container* for audio and video codecs, and there are *several* that can be placed in this container. Which is why it would be nice to see the file itself or even an analysis of the problem file with software like mediainfo...

---

### Post by sandy0594 on 2011-04-23
The file is good,i played it in windows....It's a Linux video tutorial..
Someone kindly guide how to make SM player work for that

---

### Post by fdrake on 2011-04-23
on the command line type this
sudo apt-get install mplayer
<put your password and install>

then type
mplayer /home/path directory/name_of movie.mov

see if it plays .. if there is an error post the output of the terminal in here.

---

### Post by sandy0594 on 2011-04-23
Here is what i got

```

sandy@ubuntu:~$ mplayer /host/Downloads/SHELL SCRIPTING IN LINUX/VTC - UNIX SHELL SCRIPTING ADVANCED/Chapter 01 - Introduction/0101 - About this Course.mov
MPlayer 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /host/Downloads/SHELL.
File not found: '/host/Downloads/SHELL'
Failed to open /host/Downloads/SHELL.


Playing SCRIPTING.
File not found: 'SCRIPTING'
Failed to open SCRIPTING.


Playing IN.
File not found: 'IN'
Failed to open IN.


Playing LINUX/VTC.
File not found: 'LINUX/VTC'
Failed to open LINUX/VTC.


Playing -.
Reading from stdin...



```

Smplayer didn't open

---

### Post by fdrake on 2011-04-23
> **sandy0594 said:**
> Here is what i got

```

sandy@ubuntu:~$ mplayer /host/Downloads/SHELL SCRIPTING IN LINUX/VTC - UNIX SHELL SCRIPTING ADVANCED/Chapter 01 - Introduction/0101 - About this Course.mov
MPlayer 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /host/Downloads/SHELL.
File not found: '/host/Downloads/SHELL'
Failed to open /host/Downloads/SHELL.


Playing SCRIPTING.
File not found: 'SCRIPTING'
Failed to open SCRIPTING.


Playing IN.
File not found: 'IN'
Failed to open IN.


Playing LINUX/VTC.
File not found: 'LINUX/VTC'
Failed to open LINUX/VTC.


Playing -.
Reading from stdin...



```

Smplayer didn't open
ok there is a string mistake try thus copy and paste:
mplayer "/host/Downloads/SHELL SCRIPTING IN LINUX/VTC - UNIX SHELL SCRIPTING ADVANCED/Chapter 01 - Introduction/0101 - About this Course.mov"

---

### Post by sandy0594 on 2011-04-23
It's playing but no audio as i said in my first post...here are the results

```

sandy@ubuntu:~$ mplayer "/host/Downloads/SHELL SCRIPTING IN LINUX/VTC - UNIX SHELL SCRIPTING ADVANCED/Chapter 01 - Introduction/0101 - About this Course.mov"
MPlayer 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /host/Downloads/SHELL SCRIPTING IN LINUX/VTC - UNIX SHELL SCRIPTING ADVANCED/Chapter 01 - Introduction/0101 - About this Course.mov.
libavformat file format detected.
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x9a32960]max_analyze_duration reached
[lavf] stream 0: video (smc), -vid 0
[lavf] stream 1: audio (mp3), -aid 0, -alang eng
VIDEO:  [smc ]  640x480  8bpp  1.000 fps    5.1 kbps ( 0.6 kbyte/s)
Clip info:
 title: VTC Online University
 title-eng: VTC Online University
 artist: Virtual Training Company
 artist-eng: Virtual Training Company
 copyright: 1996-2004
 copyright-eng: 1996-2004
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.
[VO_3DFX] Unable to open /dev/3dfx.
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffsmc] vfm: ffmpeg (Apple Graphics (SMC) codec)
==========================================================================
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 22050 Hz, 2 ch, s16le, 32.0 kbit/4.54% (ratio: 4000->88200)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
AO: [pulse] 22050Hz 2ch s16le (2 bytes per sample)
Starting playback...
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
Movie-Aspect is undefined - no prescaling applied.
[swscaler @ 0x4f5fc0]BICUBIC scaler, from pal8 to yuv420p using MMX2
VO: [xv] 640x480 => 640x480 Planar YV12 
A:  23.6 V:  24.0 A-V: -0.447 ct: -0.018   0/  0  0%  0%  0.1% 1 0 
Exiting... (Quit)


```

---

### Post by fdrake on 2011-04-23
you are missing mp3 codecs

type this:

sudo su <enter>
<put password>
apt-get install gstreamer0.10-fluendo-mp3
<installation......>
exit
mplayer "/host/Downloads/SHELL SCRIPTING IN LINUX/VTC - UNIX SHELL SCRIPTING ADVANCED/Chapter 01 - Introduction/0101 - About this Course.mov"

if it works in mplayer it should work in smplayer tooo..

---

### Post by sandy0594 on 2011-04-23
Followed ur steps,but still no video

```

sandy@ubuntu:~$ sudo apt-get install gstreamer0.10-fluendo-mp3
[sudo] password for sandy: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libswt-cairo-gtk-3.5-jni libxmlrpc-core-c3 libxmlrpc-c3 libswt-gtk-3.5-jni
  liblog4j1.2-java libswt-mozilla-gtk-3.5-jni libcommons-cli-java
  linux-headers-2.6.35-28-generic libcommons-lang-java
  libswt-gnome-gtk-3.5-jni libswt-gtk-3.5-java java-wrappers
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  gstreamer0.10-fluendo-plugins-mp3-partner
The following NEW packages will be installed:
  gstreamer0.10-fluendo-mp3
0 upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
Need to get 96.2kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://fi.archive.ubuntu.com/ubuntu/ maverick/universe gstreamer0.10-fluendo-mp3 i386 0.10.14.debian-1 [96.2kB]
Fetched 96.2kB in 7s (12.9kB/s)                                                
(Reading database ... 182378 files and directories currently installed.)
Removing gstreamer0.10-fluendo-plugins-mp3-partner ...
Selecting previously deselected package gstreamer0.10-fluendo-mp3.
(Reading database ... 182376 files and directories currently installed.)
Unpacking gstreamer0.10-fluendo-mp3 (from .../gstreamer0.10-fluendo-mp3_0.10.14.debian-1_i386.deb) ...
Setting up gstreamer0.10-fluendo-mp3 (0.10.14.debian-1) ...
sandy@ubuntu:~$ mplayer "/host/Downloads/SHELL SCRIPTING IN LINUX/VTC - UNIX SHELL SCRIPTING ADVANCED/Chapter 01 - Introduction/0101 - About this Course.mov"
MPlayer 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /host/Downloads/SHELL SCRIPTING IN LINUX/VTC - UNIX SHELL SCRIPTING ADVANCED/Chapter 01 - Introduction/0101 - About this Course.mov.
libavformat file format detected.
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x98d4960]max_analyze_duration reached
[lavf] stream 0: video (smc), -vid 0
[lavf] stream 1: audio (mp3), -aid 0, -alang eng
VIDEO:  [smc ]  640x480  8bpp  1.000 fps    5.1 kbps ( 0.6 kbyte/s)
Clip info:
 title: VTC Online University
 title-eng: VTC Online University
 artist: Virtual Training Company
 artist-eng: Virtual Training Company
 copyright: 1996-2004
 copyright-eng: 1996-2004
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.
[VO_3DFX] Unable to open /dev/3dfx.
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffsmc] vfm: ffmpeg (Apple Graphics (SMC) codec)
==========================================================================
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 22050 Hz, 2 ch, s16le, 32.0 kbit/4.54% (ratio: 4000->88200)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
AO: [pulse] 22050Hz 2ch s16le (2 bytes per sample)
Starting playback...
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
Movie-Aspect is undefined - no prescaling applied.
[swscaler @ 0xc95fc0]BICUBIC scaler, from pal8 to yuv420p using MMX2
VO: [xv] 640x480 => 640x480 Planar YV12 
A:   7.5 V:   8.0 A-V: -0.504 ct: -0.012   0/  0  0%  0%  0.1% 0 0 
Exiting... (Quit)


```

---

### Post by fdrake on 2011-04-23
[QUOTE=sandy0594;10709526]Followed ur steps,but still no video

[CODE]
i am confused before you said there was no audio...

but is it playing the audio now ? and before didn't play the video?

---

### Post by sandy0594 on 2011-04-23
Oh! my mistake,it was video that's not playing from starting..audio is fine

---

### Post by sandy0594 on 2011-04-23
Any idea of how to sort that video issue and get my player working?

---

### Post by andrew.46 on 2011-04-23
> **sandy0594 said:**
> Any idea of how to sort that video issue and get my player working?

Perhaps try one of the following:

```

mplayer -vo xv "/host/Downloads/SHELL SCRIPTING IN LINUX/VTC - UNIX SHELL SCRIPTING ADVANCED/Chapter 01 - Introduction/0101 - About this Course.mov"
mplayer -vo x11 "/host/Downloads/SHELL SCRIPTING IN LINUX/VTC - UNIX SHELL SCRIPTING ADVANCED/Chapter 01 - Introduction/0101 - About this Course.mov"

```

---

### Post by sandy0594 on 2011-04-23
No luck with that

```

sandy@ubuntu:~$ mplayer -vo xv "/host/Downloads/SHELL SCRIPTING IN LINUX/VTC - UNIX SHELL SCRIPTING ADVANCED/Chapter 01 - Introduction/0101 - About this Course.mov"
MPlayer 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /host/Downloads/SHELL SCRIPTING IN LINUX/VTC - UNIX SHELL SCRIPTING ADVANCED/Chapter 01 - Introduction/0101 - About this Course.mov.
libavformat file format detected.
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x9b9c9e0]max_analyze_duration reached
[lavf] stream 0: video (smc), -vid 0
[lavf] stream 1: audio (mp3), -aid 0, -alang eng
VIDEO:  [smc ]  640x480  8bpp  1.000 fps    5.1 kbps ( 0.6 kbyte/s)
Clip info:
 title: VTC Online University
 title-eng: VTC Online University
 artist: Virtual Training Company
 artist-eng: Virtual Training Company
 copyright: 1996-2004
 copyright-eng: 1996-2004
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffsmc] vfm: ffmpeg (Apple Graphics (SMC) codec)
==========================================================================
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 22050 Hz, 2 ch, s16le, 32.0 kbit/4.54% (ratio: 4000->88200)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
AO: [pulse] 22050Hz 2ch s16le (2 bytes per sample)
Starting playback...
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
Movie-Aspect is undefined - no prescaling applied.
[swscaler @ 0xc50fc0]BICUBIC scaler, from pal8 to yuv420p using MMX2
VO: [xv] 640x480 => 640x480 Planar YV12 
A:   9.5 V:  10.0 A-V: -0.512 ct: -0.010   0/  0  0%  0%  0.1% 0 0 
Exiting... (Quit)
sandy@ubuntu:~$ mplayer -vo x11 "/host/Downloads/SHELL SCRIPTING IN LINUX/VTC - UNIX SHELL SCRIPTING ADVANCED/Chapter 01 - Introduction/0101 - About this Course.mov"
MPlayer 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /host/Downloads/SHELL SCRIPTING IN LINUX/VTC - UNIX SHELL SCRIPTING ADVANCED/Chapter 01 - Introduction/0101 - About this Course.mov.
libavformat file format detected.
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x8bbc9e0]max_analyze_duration reached
[lavf] stream 0: video (smc), -vid 0
[lavf] stream 1: audio (mp3), -aid 0, -alang eng
VIDEO:  [smc ]  640x480  8bpp  1.000 fps    5.1 kbps ( 0.6 kbyte/s)
Clip info:
 title: VTC Online University
 title-eng: VTC Online University
 artist: Virtual Training Company
 artist-eng: Virtual Training Company
 copyright: 1996-2004
 copyright-eng: 1996-2004
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffsmc] vfm: ffmpeg (Apple Graphics (SMC) codec)
==========================================================================
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 22050 Hz, 2 ch, s16le, 32.0 kbit/4.54% (ratio: 4000->88200)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
AO: [pulse] 22050Hz 2ch s16le (2 bytes per sample)
Starting playback...
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
Movie-Aspect is undefined - no prescaling applied.
[swscaler @ 0x6c8fc0]using unscaled pal8 -> bgra special converter
VO: [x11] 640x480 => 640x480 BGRA 
A:   9.0 V:  10.0 A-V: -0.951 ct: -0.009   0/  0  0%  0%  0.1% 0 0 
Exiting... (Quit)


```

---

### Post by fdrake on 2011-04-23
on the menubar select System>administration>Synaptic Package panager

then click setting>repositories> 
ubuntu tab > select all the options
other softawre tap > select all
uptades tab>select all
close the 2nd window,click reload.
on the search bar type mplayer. it will look like it's already installed right click on it and select reinstall

search for vlc(it's always good to have it) select it for installation.
click the "apply" button to install
once installed on the terminal try either
mplayer "/host/Downloads/SHELL SCRIPTING IN LINUX/VTC - UNIX SHELL SCRIPTING ADVANCED/Chapter 01 - Introduction/0101 - About this Course.mov"

or 
vlc "/host/Downloads/SHELL SCRIPTING IN LINUX/VTC - UNIX SHELL SCRIPTING ADVANCED/Chapter 01 - Introduction/0101 - About this Course.mov"

---

### Post by sandy0594 on 2011-04-23
Followed the steps..neither mplayer nor vlc played the file..I mean i could hear the audio but can't see video

```

sandy@ubuntu:~$ mplayer -vo xv "/host/Downloads/SHELL SCRIPTING IN LINUX/VTC - UNIX SHELL SCRIPTING ADVANCED/Chapter 01 - Introduction/0101 - About this Course.mov"
MPlayer 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /host/Downloads/SHELL SCRIPTING IN LINUX/VTC - UNIX SHELL SCRIPTING ADVANCED/Chapter 01 - Introduction/0101 - About this Course.mov.
libavformat file format detected.
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x9b9c9e0]max_analyze_duration reached
[lavf] stream 0: video (smc), -vid 0
[lavf] stream 1: audio (mp3), -aid 0, -alang eng
VIDEO:  [smc ]  640x480  8bpp  1.000 fps    5.1 kbps ( 0.6 kbyte/s)
Clip info:
 title: VTC Online University
 title-eng: VTC Online University
 artist: Virtual Training Company
 artist-eng: Virtual Training Company
 copyright: 1996-2004
 copyright-eng: 1996-2004
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffsmc] vfm: ffmpeg (Apple Graphics (SMC) codec)
==========================================================================
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 22050 Hz, 2 ch, s16le, 32.0 kbit/4.54% (ratio: 4000->88200)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
AO: [pulse] 22050Hz 2ch s16le (2 bytes per sample)
Starting playback...
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
Movie-Aspect is undefined - no prescaling applied.
[swscaler @ 0xc50fc0]BICUBIC scaler, from pal8 to yuv420p using MMX2
VO: [xv] 640x480 => 640x480 Planar YV12 
A:   9.5 V:  10.0 A-V: -0.512 ct: -0.010   0/  0  0%  0%  0.1% 0 0 
Exiting... (Quit)
sandy@ubuntu:~$ mplayer -vo x11 "/host/Downloads/SHELL SCRIPTING IN LINUX/VTC - UNIX SHELL SCRIPTING ADVANCED/Chapter 01 - Introduction/0101 - About this Course.mov"
MPlayer 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /host/Downloads/SHELL SCRIPTING IN LINUX/VTC - UNIX SHELL SCRIPTING ADVANCED/Chapter 01 - Introduction/0101 - About this Course.mov.
libavformat file format detected.
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x8bbc9e0]max_analyze_duration reached
[lavf] stream 0: video (smc), -vid 0
[lavf] stream 1: audio (mp3), -aid 0, -alang eng
VIDEO:  [smc ]  640x480  8bpp  1.000 fps    5.1 kbps ( 0.6 kbyte/s)
Clip info:
 title: VTC Online University
 title-eng: VTC Online University
 artist: Virtual Training Company
 artist-eng: Virtual Training Company
 copyright: 1996-2004
 copyright-eng: 1996-2004
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffsmc] vfm: ffmpeg (Apple Graphics (SMC) codec)
==========================================================================
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 22050 Hz, 2 ch, s16le, 32.0 kbit/4.54% (ratio: 4000->88200)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
AO: [pulse] 22050Hz 2ch s16le (2 bytes per sample)
Starting playback...
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
Movie-Aspect is undefined - no prescaling applied.
[swscaler @ 0x6c8fc0]using unscaled pal8 -> bgra special converter
VO: [x11] 640x480 => 640x480 BGRA 
A:   9.0 V:  10.0 A-V: -0.951 ct: -0.009   0/  0  0%  0%  0.1% 0 0 
Exiting... (Quit)
sandy@ubuntu:~$ mplayer "/host/Downloads/SHELL SCRIPTING IN LINUX/VTC - UNIX SHELL SCRIPTING ADVANCED/Chapter 01 - Introduction/0101 - About this Course.mov"
MPlayer 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /host/Downloads/SHELL SCRIPTING IN LINUX/VTC - UNIX SHELL SCRIPTING ADVANCED/Chapter 01 - Introduction/0101 - About this Course.mov.
libavformat file format detected.
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x9347960]max_analyze_duration reached
[lavf] stream 0: video (smc), -vid 0
[lavf] stream 1: audio (mp3), -aid 0, -alang eng
VIDEO:  [smc ]  640x480  8bpp  1.000 fps    5.1 kbps ( 0.6 kbyte/s)
Clip info:
 title: VTC Online University
 title-eng: VTC Online University
 artist: Virtual Training Company
 artist-eng: Virtual Training Company
 copyright: 1996-2004
 copyright-eng: 1996-2004
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.
[VO_3DFX] Unable to open /dev/3dfx.
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffsmc] vfm: ffmpeg (Apple Graphics (SMC) codec)
==========================================================================
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 22050 Hz, 2 ch, s16le, 32.0 kbit/4.54% (ratio: 4000->88200)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
AO: [pulse] 22050Hz 2ch s16le (2 bytes per sample)
Starting playback...
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
Movie-Aspect is undefined - no prescaling applied.
[swscaler @ 0x6b5fc0]BICUBIC scaler, from pal8 to yuv420p using MMX2
VO: [xv] 640x480 => 640x480 Planar YV12 
A:   6.6 V:   7.0 A-V: -0.432 ct: -0.014   0/  0  0%  0%  0.1% 0 0 
Exiting... (Quit)
sandy@ubuntu:~$ vlc "/host/Downloads/SHELL SCRIPTING IN LINUX/VTC - UNIX SHELL SCRIPTING ADVANCED/Chapter 01 - Introduction/0101 - About this Course.mov"
VLC media player 1.1.4 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x88ee914] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Blocked: call to setlocale(6, "")
Blocked: call to sigaction(17, 0xb67fe0d4, 0xb67fe048)
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
Warning: call to srand(1304068463)
Warning: call to rand()
Blocked: call to setlocale(6, "")

(process:4013): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
Blocked: call to setlocale(6, "")
[0x8dffc24] main subpicture error: blending YUVA to RGBP failed
[0x8dffc24] main subpicture error: blending YUVA to RGBP failed
[0x8dffc24] main subpicture error: blending YUVA to RGBP failed
[0x8dffc24] main subpicture error: blending YUVA to RGBP failed
[0x8dffc24] main subpicture error: blending YUVA to RGBP failed
[0x8dffc24] main subpicture error: blending YUVA to RGBP failed
[0x8dffc24] main subpicture error: blending YUVA to RGBP failed
[0x8dffc24] main subpicture error: blending YUVA to RGBP failed
[0x8dffc24] main subpicture error: blending YUVA to RGBP failed
[0x8dffc24] main subpicture error: blending YUVA to RGBP failed
[0x8dffc24] main subpicture error: blending YUVA to RGBP failed
[0x8dffc24] main subpicture error: blending YUVA to RGBP failed
[0x8dffc24] main subpicture error: blending YUVA to RGBP failed
[0x8dffc24] main subpicture error: blending YUVA to RGBP failed
[0x8dffc24] main subpicture error: blending YUVA to RGBP failed
[0x8dffc24] main subpicture error: blending YUVA to RGBP failed
[0x8dffc24] main subpicture error: blending YUVA to RGBP failed
[0x8dffc24] main subpicture error: blending YUVA to RGBP failed
[0x8dffc24] main subpicture error: blending YUVA to RGBP failed
[0x8dffc24] main subpicture error: blending YUVA to RGBP failed
[0x8dffc24] main subpicture error: blending YUVA to RGBP failed
[0x8dffc24] main subpicture error: blending YUVA to RGBP failed
[0x8dffc24] main subpicture error: blending YUVA to RGBP failed
[0x8dffc24] main subpicture error: blending YUVA to RGBP failed
[0x8dffc24] main subpicture error: blending YUVA to RGBP failed
[0x8dffc24] main subpicture error: blending YUVA to RGBP failed
[0x8dffc24] main subpicture error: blending YUVA to RGBP failed
[0x8dffc24] main subpicture error: blending YUVA to RGBP failed
[0x8dffc24] main subpicture error: blending YUVA to RGBP failed


```

---

### Post by sandy0594 on 2011-04-23
What's wrong with these players I don't understand.When it is playing well on windows what's wrong here  in Ubuntu 10.10?

---

### Post by andrew.46 on 2011-04-23
Hmmm.... sounds a little odd, perhaps try either one of these:

```

mplayer -vo xv **[COLOR="Red"]-demuxer mov[/COLOR]** "/host/Downloads/SHELL SCRIPTING IN LINUX/VTC - UNIX SHELL SCRIPTING ADVANCED/Chapter 01 - Introduction/0101 - About this Course.mov"
mplayer -vo x11 **[COLOR="Red"]-demuxer mov[/COLOR]** "/host/Downloads/SHELL SCRIPTING IN LINUX/VTC - UNIX SHELL SCRIPTING ADVANCED/Chapter 01 - Introduction/0101 - About this Course.mov"

```

I believe the default demuxer is now *lavf* which is troublesome with some mov files... but if this does not solve the issue I am afraid I am out of ideas :(.

---

### Post by sandy0594 on 2011-04-23
Hey,by following the above steps i can see the video.So,lastly what should i do inorder to play that file with SM player.
```

sandy@ubuntu:~$ mplayer -vo xv -demuxer mov "/host/Downloads/SHELL SCRIPTING IN LINUX/VTC - UNIX SHELL SCRIPTING ADVANCED/Chapter 01 - Introduction/0101 - About this Course.mov"
MPlayer 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /host/Downloads/SHELL SCRIPTING IN LINUX/VTC - UNIX SHELL SCRIPTING ADVANCED/Chapter 01 - Introduction/0101 - About this Course.mov.
Quicktime/MOV file format detected.
[mov] Video stream found, -vid 0
[mov] Audio stream found, -aid 1
VIDEO:  [smc ]  640x480  8bpp  1.000 fps    0.0 kbps ( 0.0 kbyte/s)
Clip info:
 title: VTC Online University
 author: Virtual Training Company
 copyright: 1996-2004
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffsmc] vfm: ffmpeg (Apple Graphics (SMC) codec)
==========================================================================
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 22050 Hz, 2 ch, s16le, 32.0 kbit/4.54% (ratio: 4000->88200)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
AO: [pulse] 22050Hz 2ch s16le (2 bytes per sample)
Starting playback...
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
Movie-Aspect is undefined - no prescaling applied.
[swscaler @ 0x433fc0]BICUBIC scaler, from pal8 to yuv420p using MMX2
VO: [xv] 640x480 => 640x480 Planar YV12 
A:  60.0 V:  -1.0 A-V: 61.013 ct:  0.100  32/ 32 ??% ??% ??,?% 0 0 

Exiting... (End of file)
sandy@ubuntu:~$ mplayer -vo x11 -demuxer mov "/host/Downloads/SHELL SCRIPTING IN LINUX/VTC - UNIX SHELL SCRIPTING ADVANCED/Chapter 01 - Introduction/0101 - About this Course.mov"
MPlayer 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /host/Downloads/SHELL SCRIPTING IN LINUX/VTC - UNIX SHELL SCRIPTING ADVANCED/Chapter 01 - Introduction/0101 - About this Course.mov.
Quicktime/MOV file format detected.
[mov] Video stream found, -vid 0
[mov] Audio stream found, -aid 1
VIDEO:  [smc ]  640x480  8bpp  1.000 fps    0.0 kbps ( 0.0 kbyte/s)
Clip info:
 title: VTC Online University
 author: Virtual Training Company
 copyright: 1996-2004
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffsmc] vfm: ffmpeg (Apple Graphics (SMC) codec)
==========================================================================
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 22050 Hz, 2 ch, s16le, 32.0 kbit/4.54% (ratio: 4000->88200)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
AO: [pulse] 22050Hz 2ch s16le (2 bytes per sample)
Starting playback...
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
Movie-Aspect is undefined - no prescaling applied.
[swscaler @ 0x490fc0]using unscaled pal8 -> bgra special converter
VO: [x11] 640x480 => 640x480 BGRA 
A:  59.9 V:  -1.0 A-V: 60.853 ct:  0.000  43/ 43 ??% ??% ??,?% 0 0 

Exiting... (End of file)


```

---

### Post by andrew.46 on 2011-04-23
> **sandy0594 said:**
> Hey,by following the above steps i can see the video.So,lastly what should i do in order to play that file with SM player.

Great news :). Firstly for the commandline player you should add the following to your $HOME/.mplayer/config:

```

[extension.mov]
demuxer=mov

```

and this will mean that whenever the commandline MPlayer runs across a .mov file it will use the mov demuxer rather than the default lavf. Have a look as well in this file and see if there is already something after *vo=.... * and consider adding your most successful setting there (from xv, x11 or others perhaps). On my own system SMPlayer appears to use this file as well and loads the correct demuxer automagically.

Hopefully you are a little less frustrated now as well and can enjoy your video :).

---

### Post by sandy0594 on 2011-04-23
Hey the file which u said is empty,it doesn't have anything except this
> # Write your default config options here!

---

### Post by andrew.46 on 2011-04-23
That is the spot :).

---

### Post by sandy0594 on 2011-04-23
Is there anything more to add?

> 
[extension.mov]
demuxer=mov



Or the above things are enough

---

### Post by andrew.46 on 2011-04-23
This should fix the mov demuxer problem, everything else should be right with the defaults. Perhaps you might thing about setting a vo=.... setting there but this might not be needed on your system. If necessary I would use:

```
vo=xv
```

unless you have a suitable nvidia graphics card...

---

### Post by sandy0594 on 2011-04-23
Thanks you,now everything is playing..I don't have external graphic card..so,i think i will stick with the defaults

---

### Post by andrew.46 on 2011-04-24
> **sandy0594 said:**
> Thanks you,now everything is playing..I don't have external graphic card..so,i think i will stick with the defaults

Excellent news, I am glad that it has all worked out :).

---

### Post by Rebooth on 2011-12-10
try to append at ~/.mplayer/config the ff:

[extension.mov]
demuxer=mov
ac=qclp


I had the same problem and it gave me a headache before. make sure you have atleast w32codecs installed from medibuntu.

---

### Post by paichkash on 2012-08-27
> **andrew.46 said:**
> Great news :). Firstly for the commandline player you should add the following to your $HOME/.mplayer/config:

```

[extension.mov]
demuxer=mov

```

and this will mean that whenever the commandline MPlayer runs across a .mov file it will use the mov demuxer rather than the default lavf. Have a look as well in this file and see if there is already something after *vo=.... * and consider adding your most successful setting there (from xv, x11 or others perhaps). On my own system SMPlayer appears to use this file as well and loads the correct demuxer automagically.

Hopefully you are a little less frustrated now as well and can enjoy your video :).


> **andrew.46 said:**
> Hmmm.... sounds a little odd, perhaps try either one of these:

```

mplayer -vo xv **[COLOR="Red"]-demuxer mov[/COLOR]** "/host/Downloads/SHELL SCRIPTING IN LINUX/VTC - UNIX SHELL SCRIPTING ADVANCED/Chapter 01 - Introduction/0101 - About this Course.mov"
mplayer -vo x11 **[COLOR="Red"]-demuxer mov[/COLOR]** "/host/Downloads/SHELL SCRIPTING IN LINUX/VTC - UNIX SHELL SCRIPTING ADVANCED/Chapter 01 - Introduction/0101 - About this Course.mov"

```

I believe the default demuxer is now *lavf* which is troublesome with some mov files... but if this does not solve the issue I am afraid I am out of ideas :(.



following these two posts i got solved my problem as well. i was also getting this issue when playing  vtc linux courses videos...

before i had ubuntu 9.10 and i could play all files flawlessly using Totem.. but now i have 10.10 and cant play with totem ... however i can play with mplayer now after following above posts... also before following the above posts i installed xine player in ubnutnu 10.10 and was able to play flawlessly..

i wish totem also plays it in 10.10 .. as i like that tooo much.. 
also vlc still only plays audio and not video of above files..

thanks

---

