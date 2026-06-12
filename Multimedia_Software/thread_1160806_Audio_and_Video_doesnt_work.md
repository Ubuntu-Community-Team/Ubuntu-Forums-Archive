---
title: "Audio and Video doesnt work"
date: 2009-05-16
forum: Multimedia Software
---

### Post by razzle82 on 2009-05-16
I upgraded to Ubuntu 9.04 two days ago, now i can't play any video or audio files. Every time I try to open up any video files VLC Player opens up and closes down same with mplayer for audio files.

how can i fix this ?

thank you

---

### Post by cotcot on 2009-05-16
start mplayer or vlc from terminal to get error messages. Maybe that gives you a tip.
I do not know the format of the video and audio. Supposing they are mpeg or mp3 like it might have something to do with the versions of mplayer or ffmpeg (not including proprietary formats). Have a look [[COLOR="Blue"]here[/COLOR]]("https://help.ubuntu.com/community/RestrictedFormats/") and [[COLOR="Blue"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=786095") for more info. You could check if you have gstreamer 'bad' and 'ugly'.

---

### Post by razzle82 on 2009-05-16
I tried that  but didnt work. The media players still open up and close, sometimes i get sound from the same file and sometimes i dont. what is there which i should be looking at.

---

### Post by cotcot on 2009-05-17
I can only guess for the moment. I think that you are missing some (video) codecs to allow playback.
Have you started play video from terminal ?
For instance : 
```
mplayer /pathtoavideo/video
```

---

### Post by razzle82 on 2009-05-17
> faraz@faraz-desktop:~$ mplayer /pathtovideo/video
MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 2.80GHz (Family: 15, Model: 2, Stepping: 9)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /pathtovideo/video.
File not found: '/pathtovideo/video'
Failed to open /pathtovideo/video.


Exiting... (End of file)
faraz@faraz-desktop:~$ mplayer /pathtovideo/video/Office.Space[1999]DVDRip.AC3[Eng].avi
MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 2.80GHz (Family: 15, Model: 2, Stepping: 9)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /pathtovideo/video/Office.Space[1999]DVDRip.AC3[Eng].avi.
File not found: '/pathtovideo/video/Office.Space[1999]DVDRip.AC3[Eng].avi'
Failed to open /pathtovideo/video/Office.Space[1999]DVDRip.AC3[Eng].avi.


Exiting... (End of file)
faraz@faraz-desktop:~$ mplayer /pathtovideo/video/media/disk/Office.Space[1999]DVDRip.AC3[Eng].avi
MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 2.80GHz (Family: 15, Model: 2, Stepping: 9)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /pathtovideo/video/media/disk/Office.Space[1999]DVDRip.AC3[Eng].avi.
File not found: '/pathtovideo/video/media/disk/Office.Space[1999]DVDRip.AC3[Eng].avi'
Failed to open /pathtovideo/video/media/disk/Office.Space[1999]DVDRip.AC3[Eng].avi.


Exiting... (End of file)
faraz@faraz-desktop:~$ 


This is what i got when i tried directly through the terminal, should i just downgrade to 8.10 until there is a fix for this ?

---

### Post by cotcot on 2009-05-17
Do not downgrade for the moment.
Please replace 'pathtovideo' in my instruction to the real path where your video is and replace 'video' with the real name of your video.

---

### Post by razzle82 on 2009-05-18
I tried that approach but that didnt work either. When i watch stuff on youtube that works though.
am i doing something wrong

---

### Post by asiancowboy on 2009-05-21
I'm having similar problems.  I can play from the terminal and get sound, but no video.  here's the output from the terminal, for which i get sound only.


ben@ben-laptop:~$ mplayer /home/ben/Videos/Cars.avi
MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) M processor 1.60GHz (Family: 6, Model: 13, Stepping: 8)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/ben/Videos/Cars.avi.
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [XVID]  528x256  24bpp  25.000 fps  748.8 kbps (91.4 kbyte/s)
Clip info:
 Software: VirtualDubMod 1.5.10.2 (build 2540/release)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 528 x 256 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.88:1 - prescaling to correct movie aspect.
VO: [xv] 528x256 => 528x280 Planar YV12 
X11 error: BadAlloc (insufficient resources for operation)?,?% 2 0 
X11 error: BadAlloc (insufficient resources for operation)6.0% 2 0 
X11 error: BadAlloc (insufficient resources for operation)5.8% 2 0 
X11 error: BadAlloc (insufficient resources for operation)5.7% 2 0 
X11 error: BadAlloc (insufficient resources for operation)5.6% 2 0 
X11 error: BadAlloc (insufficient resources for operation)5.4% 2 0 
X11 error: BadAlloc (insufficient resources for operation)5.3% 2 0 
X11 error: BadAlloc (insufficient resources for operation)5.2% 2 0 
X11 error: BadAlloc (insufficient resources for operation)5.0% 2 0 
X11 error: BadAlloc (insufficient resources for operation)5.0% 2 0 
X11 error: BadAlloc (insufficient resources for operation)4.6% 2 0 
X11 error: BadAlloc (insufficient resources for operation)
X11 error: BadAlloc (insufficient resources for operation)
X11 error: BadAlloc (insufficient resources for operation)
X11 error: BadAlloc (insufficient resources for operation)
X11 error: BadAlloc (insufficient resources for operation)4.5% 2 0 
X11 error: BadAlloc (insufficient resources for operation)4.5% 2 0 
GNOME screensaver enabled

Exiting... (Quit)



I see a lot of things the make me think something isn't installed properly or not set right, but I don't know exactly what or how to fix it.  I would appreciate any help or explanations people can offer me.

---

### Post by thoddler on 2009-05-21
How typical!
It seems that asiancowboy have the exact same problem as I do, and when i finally find a thread, noone has answered yet ;)

I have tried to open an ordinary .avi-file using totem, mplayer and vlc. All with negative result. When trying to play with vlc through terminal, I get this:

```
 
x11 video output error: X11 request 132.19 failed with error code 11:
 BadAlloc (insufficient resources for operation)
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  132 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  81
  Current serial number in output stream:  82

```

I would appreciate it if anyone could point us in the right direction.


-thomas

---

### Post by razzle82 on 2009-05-31
was anyone able to find a solution for these ??

---

