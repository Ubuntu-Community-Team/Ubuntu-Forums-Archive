---
title: "cannot play videos"
date: 2009-07-22
forum: Multimedia Software
---

### Post by Fayed on 2009-07-22
i need a quick help please.
i cannot play videos after i installed ubuntu 9.04
sound works well but when i try to open any video the screen opens and close again at amoment.

---

### Post by pro003 on 2009-07-22
you might install or reinstall codecs, do this in terminal:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get -f install
sudo apt-get install ubuntu-restricted-extras
sudo apt-get install mplayer
```


Open your videos with mplayer, it never failed me.

---

### Post by Fayed on 2009-07-22
i tried this code but there was an error
cannot find codec matching selected -vo and video format 0x303........
but the audio of the videos is working :D

---

### Post by automaton26 on 2009-07-22
What format videos are you trying to play, and what software are you trying to play them in ?

---

### Post by pro003 on 2009-07-22
> **Fayed said:**
> i tried this code but there was an error
cannot find codec matching selected -vo and video format 0x303........
but the audio of the videos is working :D

Ok try to open a different video, if not, try to open mplayer from applications > sound & video > mplayer movie player, and then go at the preferences > video and select Xv/X11, close and open again. 

If you can't still play video try with vlc

```
sudo apt-get install vlc
```

---

### Post by Fayed on 2009-07-22
@automaton any format and any player nothing work

@pro
i have already vlc and i tried different videos

but the strange thing is that there is no videos in the preferences

---

### Post by Fayed on 2009-07-22
please any one help me .

---

### Post by igorzwx on 2009-07-22
[http://ubuntuforums.org/showthread.php?t=1220095](http://ubuntuforums.org/showthread.php?t=1220095)

---

### Post by pro003 on 2009-07-23
> **Fayed said:**
> @automaton any format and any player nothing work

@pro
i have already vlc and i tried different videos

but the strange thing is that there is no videos in the preferences


Of course there is. Let's make sure am talkin about mplayer, not vlc. Open mplayer right click on it and select preferences, then you\ll see tab named VIDEO, there you select X11/Xv, and then try to play something. You should also try to play it in terminal and see the output of any error if there is one...

---

### Post by Fayed on 2009-07-23
sorry, yes there is .i opened it but it is already x11/xv

i got mad i don't know what is the problem !!!!

---

### Post by igorzwx on 2009-07-23
relax.

it is not so simple.
many people have such problems now.

---

### Post by xc3RnbFO8P on 2009-07-23
Jaunty 32 bit:
> sudo wget [http://www.medibuntu.org/sources.list.d/jaunty.list](http://www.medibuntu.org/sources.list.d/jaunty.list) --output-document=/etc/apt/sources.list.d/medibuntu.list 
> sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update 
> sudo apt-get install libdvdcss2 
> sudo apt-get install w32codecs 
> sudo apt-get install libdvdread4 
> sudo /usr/share/doc/libdvdread4/install-css.sh
> sudo apt-get install ubuntu-restricted-extras

---

### Post by Fayed on 2009-07-23
i'm sorry but there still no progress only i can listen the audio of the video on GNOME Mplayer

---

### Post by xc3RnbFO8P on 2009-07-23
Start Gnome Player in Terminal, and see if get some errors when you play some videos:
> totem

---

### Post by Fayed on 2009-07-23
[html]ahmedfayed@ahmedfayed-desktop:~$ totem
/var/lib/python-support/python2.6/gdata/tlslite/utils/cryptomath.py:9: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 91 error_code 11 request_code 132 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
ahmedfayed@ahmedfayed-desktop:~$[/html]
i cannot understand anything :D

---

### Post by xc3RnbFO8P on 2009-07-23
What is your computer spec, graphic card?

---

### Post by prafjessor on 2009-07-24
> **Fayed said:**
> i'm sorry but there still no progress only i can listen the audio of the video on GNOME Mplayer

Do you use Pcmanfm? When i try to open a videofile in pcmfm, i get the same problem. Video works fine when opened in Nautilus, though.

---

### Post by Fayed on 2009-07-24
i have a built in VGA& the mother board is GENX 
my computer is formed not a certain spec

---

### Post by Fayed on 2009-07-24
> **prafjessor said:**
> Do you use Pcmanfm? When i try to open a videofile in pcmfm, i get the same problem. Video works fine when opened in Nautilus, though.
i don't understand

---

### Post by xc3RnbFO8P on 2009-07-24
Show the output of:
> lspci | grep VGA

---

### Post by Fayed on 2009-07-24
> **Ringi said:**
> Show the output of:

00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)

---

### Post by faizan_comsian on 2009-07-24
best way is to go to Internet and play any video of same format which u need to do... it will refer you the best media to be installed autometicaly

---

### Post by xc3RnbFO8P on 2009-07-24
Read this:
[http://ubuntuforums.org/showthread.php?t=1130582]("http://ubuntuforums.org/showthread.php?t=1130582")

---

### Post by Fayed on 2009-07-24
i tryed kplayer

it didn't close the window and the audio only is working 

there was an error tap i pressed on it
[html]  p, li { white-space: pre-wrap; }  MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team
 CPU: Intel(R) Celeron(R) CPU 2.66GHz (Family: 15, Model: 4, Stepping: 9)
 CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
 Compiled with runtime CPU detection.
 Terminal type `unknown' is not defined.
 Playing /media/disk-1/UniMasr.com_54.wmv.
 ASF file format detected.
 ID_AUDIO_ID=1
 [asfheader] Audio stream found, -aid 1
 ID_VIDEO_ID=2
 [asfheader] Video stream found, -vid 2
 VIDEO:  [WMV3]  640x480  24bpp  1000.000 fps  1345.0 kbps (164.2 kbyte/s)
 Clip info:
  name: 3
 ID_CLIP_INFO_NAME0=name
 ID_CLIP_INFO_VALUE0=3
  author: 
 ID_CLIP_INFO_NAME1=author
 ID_CLIP_INFO_VALUE1=
  copyright: 
 ID_CLIP_INFO_NAME2=copyright
 ID_CLIP_INFO_VALUE2=
  comments: 
 ID_CLIP_INFO_NAME3=comments
 ID_CLIP_INFO_VALUE3=
 ID_CLIP_INFO_N=4
 ID_FILENAME=/media/disk-1/UniMasr.com_54.wmv
 ID_DEMUXER=asf
 ID_VIDEO_FORMAT=WMV3
 ID_VIDEO_BITRATE=1344984
 ID_VIDEO_WIDTH=640
 ID_VIDEO_HEIGHT=480
 ID_VIDEO_FPS=1000.000
 ID_VIDEO_ASPECT=0.0000
 ID_AUDIO_FORMAT=353
 ID_AUDIO_BITRATE=0
 ID_AUDIO_RATE=0
 ID_AUDIO_NCH=0
 ID_LENGTH=131.00
 xscreensaver_disable: Could not find XScreenSaver window.
 GNOME screensaver disabled
 ==========================================================================
 Opening video decoder: [dmo] DMO video codecs
 DMO dll supports VO Optimizations 0 1
 DMO dll might use previous sample when requested
 GetOutput r=0x0   size:921600  align:1
 StreamCount r=0x0  1  1
 Decoder supports the following formats: YV12 YUY2 UYVY YVYU RGB8 RGB555 RGB565 RGB24 RGB32 
 Decoder is capable of YUV output (flags 0x1b)
 VDec: vo config request - 640 x 480 (preferred colorspace: Packed YUY2)
 VDec: using Planar YV12 as output csp (no 0)
 Movie-Aspect is undefined - no prescaling applied.
 VO: [xv] 640x480 => 640x480 Planar YV12  [zoom]
 Selected video codec: [wmv9dmo] vfm: dmo (Windows Media Video 9 DMO)
 ==========================================================================
 ID_VIDEO_CODEC=wmv9dmo
 ==========================================================================
 Forced audio codec: mad
 Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
 AUDIO: 48000 Hz, 2 ch, s16le, 192.2 kbit/12.51% (ratio: 24020->192000)
 ID_AUDIO_BITRATE=192160
 ID_AUDIO_RATE=48000
 ID_AUDIO_NCH=2
 Selected audio codec: [ffwmav2] afm: ffmpeg (DivX audio v2 (FFmpeg))
 ==========================================================================
 AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
 ID_AUDIO_CODEC=ffwmav2
 Starting playback...
 ID_SIGNAL=8
 GNOME screensaver enabled
 ------------------------------------------------------------
 MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team
 CPU: Intel(R) Celeron(R) CPU 2.66GHz (Family: 15, Model: 4, Stepping: 9)
 CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
 Compiled with runtime CPU detection.
 Terminal type `unknown' is not defined.
 Playing /media/disk-1/UniMasr.com_54.wmv.
 ASF file format detected.
 ID_AUDIO_ID=1
 [asfheader] Audio stream found, -aid 1
 ID_VIDEO_ID=2
 [asfheader] Video stream found, -vid 2
 VIDEO:  [WMV3]  640x480  24bpp  1000.000 fps  1345.0 kbps (164.2 kbyte/s)
 Clip info:
  name: 3
 ID_CLIP_INFO_NAME0=name
 ID_CLIP_INFO_VALUE0=3
  author: 
 ID_CLIP_INFO_NAME1=author
 ID_CLIP_INFO_VALUE1=
  copyright: 
 ID_CLIP_INFO_NAME2=copyright
 ID_CLIP_INFO_VALUE2=
  comments: 
 ID_CLIP_INFO_NAME3=comments
 ID_CLIP_INFO_VALUE3=
 ID_CLIP_INFO_N=4
 ID_FILENAME=/media/disk-1/UniMasr.com_54.wmv
 ID_DEMUXER=asf
 ID_VIDEO_FORMAT=WMV3
 ID_VIDEO_BITRATE=1344984
 ID_VIDEO_WIDTH=640
 ID_VIDEO_HEIGHT=480
 ID_VIDEO_FPS=1000.000
 ID_VIDEO_ASPECT=0.0000
 ID_AUDIO_FORMAT=353
 ID_AUDIO_BITRATE=0
 ID_AUDIO_RATE=0
 ID_AUDIO_NCH=0
 ID_LENGTH=131.00
 xscreensaver_disable: Could not find XScreenSaver window.
 GNOME screensaver disabled
 ==========================================================================
 Opening video decoder: [dmo] DMO video codecs
 DMO dll supports VO Optimizations 0 1
 DMO dll might use previous sample when requested
 GetOutput r=0x0   size:921600  align:1
 StreamCount r=0x0  1  1
 Decoder supports the following formats: YV12 YUY2 UYVY YVYU RGB8 RGB555 RGB565 RGB24 RGB32 
 Decoder is capable of YUV output (flags 0x1b)
 VDec: vo config request - 640 x 480 (preferred colorspace: Packed YUY2)
 VDec: using Planar YV12 as output csp (no 0)
 Movie-Aspect is undefined - no prescaling applied.
 VO: [xv] 640x480 => 640x480 Planar YV12  [zoom]
 Selected video codec: [wmv9dmo] vfm: dmo (Windows Media Video 9 DMO)
 ==========================================================================
 ID_VIDEO_CODEC=wmv9dmo
 ==========================================================================
 Forced audio codec: mad
 Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
 AUDIO: 48000 Hz, 2 ch, s16le, 192.2 kbit/12.51% (ratio: 24020->192000)
 ID_AUDIO_BITRATE=192160
 ID_AUDIO_RATE=48000
 ID_AUDIO_NCH=2
 Selected audio codec: [ffwmav2] afm: ffmpeg (DivX audio v2 (FFmpeg))
 ==========================================================================
 AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
 ID_AUDIO_CODEC=ffwmav2
 Starting playback...
 [Mixer] No hardware mixing, inserting volume filter.
[/html]

---

### Post by augustinepa on 2009-07-28
> **pro003 said:**
> you might install or reinstall codecs, do this in terminal:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get -f install
sudo apt-get install ubuntu-restricted-extras
sudo apt-get install mplayer
```
Open your videos with mplayer, it never failed me.



Thank you ... It was very useful for me. Now i can play my video files with mplayer. Before playing the file i have changed the X11/xv to X11(XImage/shm). For made this change just right click on the video window select preferences -> video. then change the settings as given.

---

### Post by pro003 on 2009-07-28
> **augustinepa said:**
> Thank you ... It was very useful for me. Now i can play my video files with mplayer. Before playing the file i have changed the X11/xv to X11(XImage/shm). For made this change just right click on the video window select preferences -> video. then change the settings as given.

glad I could help you, you're welcome :)

---

