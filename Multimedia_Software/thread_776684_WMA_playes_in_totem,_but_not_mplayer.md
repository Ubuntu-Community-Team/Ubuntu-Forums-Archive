---
title: "WMA playes in totem, but not mplayer"
date: 2008-04-30
forum: Multimedia Software
---

### Post by Phantom784 on 2008-04-30
I am trying to play a WMA file in mplayer (to encode it over to mp3, actually).  However, when I do so, i get the following output:
```

francis@uranium:~$ mplayer 08_Who_Am_I_-_The_Trial.wma 
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 3600+ (Family: 15, Model: 107, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing 08_Who_Am_I_-_The_Trial.wma.
libavformat file format detected.
[mp3 @ 0x8804c54]Could not find codec parameters (Audio: mp2, 40 kb/s)
LAVF_header: av_find_stream_info() failed


Exiting... (End of file)

```

The same file plays just fine in totem.  I have w32codecs installed, and I don't see why it would work with one program but not the other.

---

### Post by cor2y on 2008-04-30
How did you install mplayer and the w32codecs?
if via synaptic (using the medibuntu repos) then you may have to choose a different audio output library
I see its calling mp2 instead of the w32codecs.
If you just downloaded the w32codecs from the mplayer site then they have to be in /usr/lib/codecs or /usr/local/lib/codecs if mplayer was compiled without specifiying where to install it.

---

### Post by Phantom784 on 2008-04-30
I installed through synaptic (with the midibuntu repository).  How can I configure mplayer to correctly access the codecs?  Also, I checked, and it appears that the files installed by that package *are* in the /usr/lib/codecs directory.

---

### Post by cor2y on 2008-05-01
Check your mplayer ac out put.
Via the terminal type
```
 mplayer -ac help
```Look to see if wma is supported usually via
```
wma9dmo     dmo       working   Windows Media Audio 9 DMO  [wma9dmod.dll]
wmadmo      dmo       working   Windows Media Audio DMO  [wmadmod.dll]
wma9spdmo   dmo       working   Windows Media Audio 9 Speech DMO  [wmspdmod.dll]
wma9spdshow dshow     working   Windows Media Audio 9 Speech DShow  [wmavds32.ax]
```To change ac settings you have to edit it
Either via gmplayer Right click on mplayer select Preferences and go to the Codecs Demuxer tab, the default for audio out is usually libmad (make sure libmad is installed)
For editing with gedit vi etc the file is located in either /etc/mplayer/mplayer.conf ~/.mplayer/config or /usr/local/etc/mplayer/mplayer.conf
Since its the audio thats the problem check what output you have audio set up as.
For example mine is
```

##################
# audio settings #
##################

# Specify default audio driver (see -ao help for a list).
ao=pulse,alsa,

# Use SDL audio driver with the esd subdriver by default.
#ao = sdl:esd

# Specify the mixer device.
#mixer = /dev/mixer

# Resample the sound to 44100Hz with the lavcresample audio filter.
#af=lavcresample=44100

# Specify default audio codec (see -ac help for a list).
ac=mad,
```Meaning libmad is the default audio codec for audio playback.

---

### Post by Phantom784 on 2008-05-01
WMA is listed by "mplayer -ac help" and my mplayer.conf is the same as yours.  However, I recently realized that mplayer will play some wma files; it's just this one that isn't working for some reason (although it's fine in totem).

---

