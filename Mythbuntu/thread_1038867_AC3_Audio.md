---
title: "AC3 Audio"
date: 2009-01-14
forum: Mythbuntu
---

### Post by dad311 on 2009-01-14
Just finished building my Mythbuntu box and everything seems to be working execpt AC3 audio on AVI files.  If I play a DVD I recieve AC3 audio, but no AC3 sound on avi files.  I know the ripped avi files have AC3 audio encoded in them, Ive played them before on a dlink dsm-520.

 
Can someone point me in the right direction?

---

### Post by utar on 2009-01-14
Have you tried playing the files through mplayer / vlc?

If the audio works here it may well be down to the internal mythtv player.  In my expereince this can be a bit "fussy" about what it will play.

---

### Post by dad311 on 2009-01-14
Ive tried mplayer and vlc, neither give me AC3 audio.

---

### Post by andrew.46 on 2009-01-14
Hi,

From the command you can test if this is available:

```
andrew@skamandros:~$ **[COLOR="Red"]mplayer -ac help | grep -i aac[/COLOR]**

faad        faad      working   FAAD AAC (MPEG-2/MPEG-4 Audio) decoder  [libfaad2]
ffaac       ffmpeg    working   FFmpeg AAC (MPEG-2/MPEG-4 Audio) decoder  [aac]

```

If you are using an Ubuntu MPlayer perhaps the aac decoders have been removed.

Andrew

---

### Post by dad311 on 2009-01-14
Looks like I missing something.  How do I get the Ac3 codec???

thx



mplayer -ac help | grep -i aac
faad        faad      working   FAAD AAC (MPEG-2/MPEG-4 Audio) decoder  [libfaad2]

---

### Post by andrew.46 on 2009-01-14
Hi,

Seems a little odd as faad *is* an aac decoder. I tried an aac file with firstly ffaac:

```
andrew@skamandros~/Desktop$ **[COLOR="Red"]mplayer -ac ffaac test.aac[/COLOR]** 
MPlayer dev-SVN-r28288-4.2.4 (C) 2000-2009 MPlayer Team
CPU: Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz (Family: 6, Model: 15, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2

Playing test.aac.
libavformat file format detected.
[lavf] Audio stream found, -aid 0
==========================================================================
Forced audio codec: ffaac
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, s16le, 114.7 kbit/8.13% (ratio: 14341->176400)
Selected audio codec: [ffaac] afm: ffmpeg (FFmpeg AAC (MPEG-2/MPEG-4 Audio) decoder)
==========================================================================
AO: [oss] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:  21.5 (21.5) of 1461.7 (24:21.6)  2.2% 
```

and then faad:

```
andrew@skamandros~/Desktop$ **[COLOR="Red"]mplayer -ac faad test.aac [/COLOR]**
MPlayer dev-SVN-r28288-4.2.4 (C) 2000-2009 MPlayer Team
CPU: Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz (Family: 6, Model: 15, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2

Playing test.aac.
libavformat file format detected.
[lavf] Audio stream found, -aid 0
==========================================================================
Forced audio codec: faad
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
Unsupported LATM configuration: 7 programs/ 61 subframes, 4 layers, allstreams: 0
Unsupported LATM configuration: 3 programs/ 40 subframes, 4 layers, allstreams: 0
AUDIO: 44100 Hz, 2 ch, s16le, 114.7 kbit/8.13% (ratio: 14341->176400)
Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio) decoder)
==========================================================================
AO: [oss] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:  12.6 (12.6) of 1461.7 (24:21.6)  0.7% 
```

With I believe better performance from ffaac but the difference on my minimal audio hardware was not that great. Perhaps this functionality is not available in the rc versions of MPlayer?

There are 3 solid alternatives for you here:

[LIST=1]
[*]Compile your own svn MPlayer against a full set of codecs. There is a guide for this [on the forums somewhere]("http://ubuntuforums.org/showthread.php?t=1024592"), and this eliminates all of the patching / removal / manipulating that has been done to MPlayer by too many hands.
[*]Run through Nathan's [Comprehensive Multimedia & Video Howto]("http://ubuntuforums.org/showthread.php?t=766683") which eliminates all the insane compiling / svn commands etc that seem so foreign to most Ubuntu users. This might perhaps be your best option?
[*]Visit the [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") pages and use their version of [MPlayer]("http://packages.medibuntu.org/intrepid/mplayer.html")
[/LIST]

It depends on what you would like to do. As I run the guide for the svn MPlayer I am naturally a little biased but the more Ubuntu-centric method can be seen with Nathan's encyclopaedic guide.

All the best,

Andrew

---

### Post by dad311 on 2009-01-18
Well, after compiling mplayer from source I now show:
faad        faad      working   FAAD AAC (MPEG-2/MPEG-4 Audio) decoder  [libfaad2]
ffaac       ffmpeg    working   FFmpeg AAC (MPEG-2/MPEG-4 Audio) decoder  [aac]


However, I still do not get AC3 audio while playing AVI files.

Also, Ive seem to have lost remote control function(play,stop,exit) while playing movies in mplayer.


Does anyone here have mplayer playing AC3 audio to an external audio receiver?

---

### Post by andrew.46 on 2009-01-18
Hi dad311,

> **dad311 said:**
> However, I still do not get AC3 audio while playing AVI files.

Seems odd. Can you post one of these files somewhere or even just the results of:

```
$ mplayer -identify -frames 0 **[COLOR="Red"]<myfile.avi>[/COLOR]** 
```

> Also, Ive seem to have lost remote control function(play,stop,exit) while playing movies in mplayer.

You will need to compile against liblircclient-dev.

Andrew

---

### Post by dad311 on 2009-01-18
> **andrew.46 said:**
> Hi dad311,



Seems odd. Can you post one of these files somewhere or even just the results of:

```
$ mplayer -identify -frames 0 **[COLOR="Red"]<myfile.avi>[/COLOR]** 
```



You will need to compile against liblircclient-dev.

Andrew


Here is my file:

darrell@darrell-mythtv:/media/disk/Video$ mplayer -identify -frames 0
The_Duchess.avi
MPlayer dev-SVN-r28340-4.3.2 (C) 2000-2009 MPlayer Team
CPU: AMD Athlon(tm) 64 Processor 3000+ (Family: 15, Model: 31, Stepping:
0)
CPUflags: MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 3DNow 3DNowEx SSE SSE2

Playing The_Duchess.avi.
AVI file format detected.
ID_VIDEO_ID=0
[aviheader] Video stream found, -vid 0
ID_AUDIO_ID=1
[aviheader] Audio stream found, -aid 1
VIDEO: [DX50] 718x368 24bpp 23.976 fps 1500.1 kbps (183.1 kbyte/s)
ID_FILENAME=The_Duchess.avi
ID_DEMUXER=avi
ID_VIDEO_FORMAT=DX50
ID_VIDEO_BITRATE=1500056
ID_VIDEO_WIDTH=718
ID_VIDEO_HEIGHT=368
ID_VIDEO_FPS=23.976
ID_VIDEO_ASPECT=2.3108
ID_AUDIO_FORMAT=8192
ID_AUDIO_BITRATE=448000
ID_AUDIO_RATE=0
ID_AUDIO_NCH=0
ID_LENGTH=6600.55
ID_SEEKABLE=1
ID_CHAPTERS=0
Xlib: extension "XFree86-VidModeExtension" missing on display ":1.0".
Xlib: extension "XVideo" missing on display ":1.0".
[VO_XV] Sorry, Xv not supported by this X11 version/driver
[VO_XV] ******** Try with -vo x11 or -vo sdl *********
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
ID_VIDEO_CODEC=ffodivx
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 448.0 kbit/29.17% (ratio: 56000->192000)
ID_AUDIO_BITRATE=448000
ID_AUDIO_RATE=48000
ID_AUDIO_NCH=2
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
AO: [oss] 48000Hz 2ch s16le (2 bytes per sample)
ID_AUDIO_CODEC=a52
Starting playback...



Also, how do I "compile against liblircclient-dev"

Thanks.

---

### Post by andrew.46 on 2009-01-18
Hi dad311,

> **dad311 said:**
> ```
ID_AUDIO_FORMAT=8192
```

I believe this is Dolby AC-3 Audio, and a pretty standard part of most DVDs. The correct decoder for such sound files is being opened by MPlayer:

```
Opening audio decoder: [liba52] AC3 decoding with liba52
```

The name 'AC3/A52' used by Dolby is a bit unfortunate as it has no relation to aac audio files as is commonly understood, consequently the chase for an aac audio decoder was a little spurious. My apologies for this misreading on my part. Now liba52 comes as part of the MPlayer source code so you cannot go wrong there and it states quite clearly:

> liba52 provides a low-level interface to decoding audio frames encoded
using ATSC standard A/52 aka AC-3.

But obviously you cannot hear the sound although the lack of error messages is a little odd. There are 2 choices I guess, you could post to the MPlayer-users and ask the experts, or just simply try and manipulate your audio out device:

```
AO: [oss] 48000Hz 2ch s16le (2 bytes per sample)
```

Try, for example, the following from the commandline:

```
$ mplayer -ao alsa **[COLOR="Red"]<my_movie.avi>[/COLOR]**
```

Obviously replace **[COLOR="Red"]<my_movie.avi>[/COLOR]** with the name of your movie file and don't use the brackets. r perhaps try an alternative decoder:

> Also, how do I "compile against liblircclient-dev"

Simply install liblircclient-dev:

```
$ sudo apt-get install liblircclient-dev
```

and repeat the actual compile process for MPlayer (./configure make etc) and MPlayer will pick up the new library.

Hope this helps a little? 

Andrew

PS I am writing out 100 time: AC3 not AAC :-)

---

### Post by joho500 on 2009-01-19
> **dad311 said:**
> Ive tried mplayer and vlc, neither give me AC3 audio.
Did you select S/PDIF passthrough in vlc?

Gr, Joost

---

### Post by august495 on 2009-01-19
I went round and roud with this also. I am using spdif out, and to resolve this I had to use this command for vlc:

```
vlc --alsadev iec958
```

---

### Post by theophile on 2009-01-19
Why are we talking about AAC? I thought the OP was about AC3?

Are you trying to do AC3 passthrough to a receiver or AC3 decoding to an analog surround speaker configuration?

On my system, AC3 playback in mplayer is achieved thus:

mplayer foo.avi -ao alsa:device=spdif -ac hwac3

Show us the output of 'aplay -L' as well as your /etc/asound.conf (if you have one).

---

### Post by andrew.46 on 2009-01-19
Hi theophile,

> **theophile said:**
> Why are we talking about AAC? I thought the OP was about AC3?

Because I was tired and misread the question and made such a noob mistake that I was hoping would it just go away :(. And perhaps the earth might open up and swallow me and nobody would ever notice I made such a horrible mistake .......

Andrew

---

### Post by theophile on 2009-01-19
lol, okay. :-) At first I thought this might be a thread about trying to play 6-channel AAC files over SPDIF (still can't get that to work) and I thought I had missed something. Carry on...

---

### Post by dad311 on 2009-01-19
> **theophile said:**
> Why are we talking about AAC? I thought the OP was about AC3?

Are you trying to do AC3 passthrough to a receiver or AC3 decoding to an analog surround speaker configuration?

On my system, AC3 playback in mplayer is achieved thus:

mplayer foo.avi -ao alsa:device=spdif -ac hwac3

Show us the output of 'aplay -L' as well as your /etc/asound.conf (if you have one).


mplayer foo.avi -ao alsa:device=spdif -ac hwac3

Returns no sound

darrell@darrell-mythtv:/media/disk/Video$ mplayer BadBoys.avi -ao also:device=spdf -ac hwac3
MPlayer dev-SVN-r28341-4.3.2 (C) 2000-2009 MPlayer Team
CPU: AMD Athlon(tm) 64 Processor 3000+ (Family: 15, Model: 31, Stepping: 0)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 3DNow 3DNowEx SSE SSE2

Playing BadBoys.avi.
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [DX50]  708x462  24bpp  23.976 fps  1500.1 kbps (183.1 kbyte/s)
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Forced audio codec: hwac3
Opening audio decoder: [hwac3] AC3/DTS pass-through S/PDIF
No accelerated IMDCT transform found
hwac3: switched to AC3, 192000 bps, 48000 Hz
AUDIO: 48000 Hz, 2 ch, ac3, 192.0 kbit/12.50% (ratio: 24000->192000)
Selected audio codec: [hwac3] afm: hwac3 (AC3 through S/PDIF)
==========================================================================
No such audio driver 'also'
Could not open/initialize audio device -> no sound.
Audio: no sound
Starting playback...
VDec: vo config request - 708 x 462 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.81:1 - prescaling to correct movie aspect.
VO: [xv] 708x462 => 836x462 Planar YV12 
V:  71.2 1709/1709  6%  0%  0.0% 0 0

---

### Post by dad311 on 2009-01-19
> **theophile said:**
> Why are we talking about AAC? I thought the OP was about AC3?

Are you trying to do AC3 passthrough to a receiver or AC3 decoding to an analog surround speaker configuration?

On my system, AC3 playback in mplayer is achieved thus:

mplayer foo.avi -ao alsa:device=spdif -ac hwac3

Show us the output of 'aplay -L' as well as your /etc/asound.conf (if you have one).

darrell@darrell-mythtv:/media/disk/Video$ aplay -L
default:CARD=CK804
    NVidia CK804, NVidia CK804
    Default Audio Device
front:CARD=CK804,DEV=0
    NVidia CK804, NVidia CK804
    Front speakers
surround40:CARD=CK804,DEV=0
    NVidia CK804, NVidia CK804
    4.0 Surround output to Front and Rear speakers
surround41:CARD=CK804,DEV=0
    NVidia CK804, NVidia CK804
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=CK804,DEV=0
    NVidia CK804, NVidia CK804
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=CK804,DEV=0
    NVidia CK804, NVidia CK804
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=CK804,DEV=0
    NVidia CK804, NVidia CK804
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
null
    Discard all samples (playback) or generate zero samples (capture)

---

### Post by dad311 on 2009-01-19
> **august495 said:**
> I went round and roud with this also. I am using spdif out, and to resolve this I had to use this command for vlc:

```
vlc --alsadev iec958
```

Does this look correct? I dont get any sound when the movie plays.

darrell@darrell-mythtv:/media/disk/Video$ vlc --alsadev iec958  BadBoys.avi
VLC media player 0.9.4 Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.4 Grishenko - (c) 1996-2008 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintaner-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=1ubuntu3' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-arts' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-x264' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-alsa' '--enable-dv' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[00000453] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1

---

### Post by theophile on 2009-01-20
Your aplay results don't even show a digital-out device. It's usually called "iec958" or similar. For example, see [this page](http://alsa.opensrc.org/index.php/DigitalOut) which shows you how to set up AC3 passthrough. There is an example device listing for the same chipset you have which shows an iec958 device.

---

### Post by dad311 on 2009-01-20
> **theophile said:**
> Your aplay results don't even show a digital-out device. It's usually called "iec958" or similar. For example, see [this page](http://alsa.opensrc.org/index.php/DigitalOut) which shows you how to set up AC3 passthrough. There is an example device listing for the same chipset you have which shows an iec958 device.

aplay -l shows a iec958 device.  Is this enough or do I need a iec958 listed in aplay -L as well?  thx



darrell@darrell-mythtv:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
darrell@darrell-mythtv:~$

---

### Post by dad311 on 2009-01-30
Well after replacing the MB and following the directions eariler in this post, Im now able to play avi files with AC3 audio.

I know have a new question.



In Mythbuntu, my DVDs play AC3 audio. My AVI files (with AC3 audio) play AC3 audio.  However, my AVI files (without AC3 audio) have no sound.

How can I get ALL my audio to play via the SPDIF interface?  Can someone point me in the right direction?  

thx

---

