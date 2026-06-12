---
title: "Cannot Play DVDs"
date: 2009-07-23
forum: Multimedia Software
---

### Post by ve4cib on 2009-07-23
Classic problem: I want to watch an encrypted DVD using Linux.  And of course I'm running into problems (again).

Before you point me to the obvious, I have already installed Ubuntu-Restricted-Extras and libdvdcss.

The problem I'm running into is that none of my media players will play the DVD properly: (I'm trying to watch the Watchmen Director's Cut DVD)

1- VLC: The DVD's main menu loads just fine.  But when I go to play the actual movie the video is scrambled (or non-existant), and the audio is garbled.  I get this output when I run VLC from the command-line:

```
VLC media player 1.0.0 Goldeneye
[0x1f69888] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: DVD Title: WATCHMEN_DIRECTORS_CUT
libdvdnav: DVD Serial Number: 3AB68C1A
libdvdnav: DVD Title (Alternative): WATCHMEN_DIRECTORS_CUT
libdvdnav: Unable to find map file '/home/ve4cib/.dvdnav/WATCHMEN_DIRECTORS_CUT.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
libdvdnav: Suspected RCE Region Protection!!!
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
[0x7fa690001368] main input error: ES_OUT_RESET_PCR called

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0000a65a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0000f706
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x0001b592
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x00037149
libdvdread: Elapsed time 0
libdvdread: Found 3 VTS's
libdvdread: Elapsed time 0
[0x7fa690001368] main input error: ES_OUT_RESET_PCR called
[0x2815908] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[0x7fa690001368] main input error: ES_OUT_RESET_PCR called
[0x7fa690001368] main input error: ES_OUT_RESET_PCR called
[0x25a8d88] libmpeg2 decoder error: invalid picture encountered
[0x2818048] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:384000
QPainter::begin: Paint device returned engine == 0, type: 1
[0x25a8d88] libmpeg2 decoder error: invalid picture encountered
[0x25a8d88] libmpeg2 decoder error: invalid picture encountered
[0x25a8d88] libmpeg2 decoder error: invalid picture encountered
[0x25a8d88] libmpeg2 decoder error: invalid picture encountered
[0x25a8d88] libmpeg2 decoder error: invalid picture encountered
[0x25a8d88] libmpeg2 decoder error: invalid picture encountered
[0x25a8d88] libmpeg2 decoder error: invalid picture encountered
[0x25a8d88] libmpeg2 decoder error: invalid picture encountered
[0x25a8d88] libmpeg2 decoder error: invalid picture encountered
[0x25a8d88] libmpeg2 decoder error: invalid picture encountered
[0x25a8d88] libmpeg2 decoder error: invalid picture encountered
[0x25a8d88] libmpeg2 decoder error: invalid picture encountered
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[0x25a8d88] libmpeg2 decoder error: invalid picture encountered
[0x25a8d88] libmpeg2 decoder error: invalid picture encountered
[0x25a8d88] libmpeg2 decoder error: invalid picture encountered
[0x25a8d88] libmpeg2 decoder error: invalid picture encountered
[0x25a8d88] libmpeg2 decoder error: invalid picture encountered
...
```

I've done a bit of Google-hunting, but haven't come up with anything terribly useful about that error yet.  Any thoughts?

2- SMplayer: No video, scrambled/skipping audio.  No output to the command-line.

3- GMplayer and Mplayer: No video, no audio.  I get this output to the command-line:

```

MPlayer SVN-r29139-4.3.3 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvd://1.
libdvdread: Using libdvdcss version 1.2.10 for DVD access
There are 10 titles on this DVD.
There are 1 angles in this DVD title.

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0000a65a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0000f706
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x0001b592
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x00037149
libdvdread: Elapsed time 0
libdvdread: Found 3 VTS's
libdvdread: Elapsed time 0
audio stream: 0 format: ac3 (5.1) language: en aid: 128.
audio stream: 1 format: ac3 (5.1) language: fr aid: 129.
number of audio channels on disk: 2.
subtitle ( sid ): 1 language: en
subtitle ( sid ): 3 language: fr
subtitle ( sid ): 5 language: es
number of subtitles on disk: 3
MPEG-PS file format detected.
VIDEO:  MPEG1  720x480  (aspect 3)  29.970 fps  7500.0 kbps (937.5 kbyte/s)
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 480 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Unsupported PixelFormat -1
Selected video codec: [ffmpeg1] vfm: ffmpeg (FFmpeg MPEG-1)
==========================================================================
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
a52: CRC check failed!  
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 384.0 kbit/25.00% (ratio: 48000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
[pulse] working around probably broken pause functionality,
        see http://www.pulseaudio.org/ticket/440
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
a52: error at resampling
[mpeg1video @ 0xd5ee60]sequence header damaged
[mpeg1video @ 0xd5ee60]sequence header damaged
a52: CRC check failed!  0.035 ct:  0.000   1/  1 ??% ??% ??,?% 0 0              
a52: error at resampling
a52: CRC check failed!  0.145 ct:  0.003   2/  2 ??% ??% ??,?% 0 0              
a52: error at resampling
a52: CRC check failed!  0.349 ct:  0.007   3/  3 ??% ??% ??,?% 0 0              
a52: error at resampling
[mpeg1video @ 0xd5ee60]inter matrix damaged
[mpeg1video @ 0xd5ee60]Missing picture start code
[mpeg1video @ 0xd5ee60]Missing picture start code
[mpeg1video @ 0xd5ee60]Missing picture start code
[mpeg1video @ 0xd5ee60]Missing picture start code
[mpeg1video @ 0xd5ee60]Missing picture start code
[mpeg1video @ 0xd5ee60]Missing picture start code
[mpeg1video @ 0xd5ee60]Missing picture start code
[mpeg1video @ 0xd5ee60]Missing picture start code
[mpeg1video @ 0xd5ee60]Missing picture start code
[mpeg1video @ 0xd5ee60]Missing picture start code
[mpeg1video @ 0xd5ee60]Missing picture start code
a52: CRC check failed!  0.608 ct:  0.010   4/  4 ??% ??% ??,?% 0 0              
a52: error at resampling
a52: CRC check failed!  
a52: error at resampling
a52: CRC check failed!  
a52: error at resampling
[mpeg1video @ 0xd5ee60]inter matrix damaged1/ 10 ??% ??% ??,?% 1 0              
[mpeg1video @ 0xd5ee60]Missing picture start code
a52: CRC check failed!  0.422 ct:  0.033  12/ 11 ??% ??% ??,?% 1 0              
a52: error at resampling
A:   1.4 V:   1.2 A-V:  0.174 ct:  0.040  15/ 13 ??% ??% ??,?% 1 0              
demux_mpg: 24000/1001fps progressive NTSC content detected, switching framerate.
a52: CRC check failed!  0.152 ct:  0.048  18/ 15 118%  0%  2.7% 1 0             
a52: error at resampling
a52: CRC check failed!  0.254 ct:  0.056  20/ 17 103%  0%  2.5% 1 0             
a52: error at resampling
[mpeg1video @ 0xd5ee60]inter matrix damaged
[mpeg1video @ 0xd5ee60]Missing picture start code
a52: CRC check failed!  0.246 ct:  0.060  21/ 18 101%  0%  2.4% 1 0             
a52: error at resampling
a52: CRC check failed!  0.117 ct:  0.064  22/ 19 95%  0%  2.3% 1 0              
a52: CRC check failed!  0.390 ct:  0.077  25/ 22 82%  0%  2.2% 1 0              
a52: error at resampling
[mpeg1video @ 0xd5ee60]inter matrix damaged7/ 24 75%  0%  2.1% 1 0              
[mpeg1video @ 0xd5ee60]Missing picture start code
[mpeg1video @ 0xd5ee60]Missing picture start code
[mpeg1video @ 0xd5ee60]Missing picture start code
[mpeg1video @ 0xd5ee60]Missing picture start code
...
```

4- Totem (xine): I get a message box saying that I am trying to play an encrypted DVD without libdvdcss installed (despite the fact that it is installed).

5- Totem (gstreamer): Nothing happens.  I can't even hit play, because Totem claims the movie is 0:00.00 long.  Output:

```
/var/lib/python-support/python2.6/gdata/tlslite/utils/cryptomath.py:9: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha
** Message: no file info
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: DVD Title: WATCHMEN_DIRECTORS_CUT
libdvdnav: DVD Serial Number: 3AB68C1A
libdvdnav: DVD Title (Alternative): WATCHMEN_DIRECTORS_CUT
libdvdnav: Unable to find map file '/home/ve4cib/.dvdnav/WATCHMEN_DIRECTORS_CUT.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
libdvdnav: Suspected RCE Region Protection!!!

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0000a65a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0000f706
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x0001b592
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x00037149
libdvdread: Elapsed time 0
libdvdread: Found 3 VTS's
libdvdread: Elapsed time 0
Preparing SPU change, phys 0 forced 1
Preparing audio change, phys 0
NAV packet discont: cur_end_ts 99:99:99.999999999 !=  vobu_start_ptm: 0:00:00.045500000 base 0:00:00.000000000
seek completed. New start TS 0:00:00.045500000 pos 0:00:00.000000000 (offset 0:00:00.045500000)
Pushing stream event
Pushing clut event
Pushing spu_select event
Subpicture physical ID change to 0, forced 1
Pushing audio_select event
Audio physical ID change to 128
Discont packet
Pushing highlight event with TS 99:99:99.999999999
demux: got segment update 0 start 45500000 stop -1 time 0
sending new segment: update 0 rate 1 format 3, start: 10000000000, stop: -1, time: 0 scr_adjust: 895905(0:00:09.954500000)
First audio after flush has TS 0:00:10.192000000

(totem:19040): GLib-GObject-WARNING **: IA__g_object_get_valist: object class `GstPlayBin' has no property named `current-subpicture'

```


So that's that.  I've tried every media player I could think of, and since none of them work I've concluded that there's either a problem with my drive (though I can burn and read burned DVDs and CDs just fine).

I thought that maybe it was a problem with the drive's region, so I installed regionset and set the drive to use Region 1 (I'm in Canada), but that didn't help.

Looking into it further I came across a few posts suggesting that enabling DMA would fix it.  DMA was already enabled, so that's not the answer either.

Does anyone have any ideas or suggestions or alternate methods I should try?  Thanks a lot!

(By the way, I'm running Jaunty x86_64, from a clean install in case that makes a difference)



UPDATE:

On a whim I just tried watching an older DVD (A Scanner Darkly) and it plays just fine.  So does Watchmen just have some newfangled encryption that my version of libdvdcss can't handle?  Or is it more likely a bad disc?  I'm even more confused now...

---

### Post by philcamlin on 2009-07-23
my guess is your missing codecs

---

### Post by ve4cib on 2009-07-23
What codecs would I be missing?  And if I'm missing some why would A Scanner Darkly play without any problems and Watchmen just chokes?

---

### Post by philcamlin on 2009-07-23
go into synaptic and see if you have both GStreamer codecs 

search under all available apps athe top tab

are both videos different fomats?

avi mov mp4 etc...

---

### Post by mc4man on 2009-07-23
> So does Watchmen just have some newfangled encryption that my version of libdvdcss can't handle

I've only seen 2 dvd's that couldn't be played on linux, this wouldn't be another one. (probably has no structure protection at all.

What your version probably does have is a digital copy on the disk, maybe your players are trying to play it. (or something else
Plus there seems to possibly be a pulse error
From mplayer

> Selected video codec: [ffmpeg1] vfm: ffmpeg (FFmpeg [COLOR="Blue"]MPEG-1)[/COLOR]
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
a52: error at resampling
[[COLOR="Blue"]mpeg1video[/COLOR] @ 0xd5ee60]sequence header damaged
[[COLOR="Blue"]mpeg1video[/COLOR] @ 0xd5ee60]sequence header damaged
a52: CRC check failed!  0.035 ct:  0.000   1/  1 ??% ??% ??,?% 0 0              
a52: error at resampling
ect. ect

Vlc starts out fine, the red can be ignored, blue is same issue as above, ( except vlc is using proper decoder for dvd movies - libmpeg2

> QPainter::begin: Paint device returned engine == 0, type: 1
[COLOR="Red"][0x7fa690001368] main input error: ES_OUT_RESET_PCR called
[0x7fa690001368] main input error: ES_OUT_RESET_PCR called[/COLOR]
[COLOR="Blue"][0x25a8d88] libmpeg2 decoder error: invalid picture encountered[/COLOR]
[0x2818048] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:384000
QPainter::begin: Paint device returned engine == 0, type: 1
[COLOR="Blue"][0x25a8d88] libmpeg2 decoder error: invalid picture encountered[/COLOR]
ect..

totem-xine needs libxine1-ffmpeg installed, if not installed then install, and see what it does.

totem-gstreamer seems confused also (usually is anyway with dvd's, but not to this extent

dvd movies are mpeg2, not mpeg1

---

### Post by igorzwx on 2009-07-23
I have been able to play DVD since 2006 with Ubuntu.
You need some restrictes, css, and xine plugs for this.

The easiest way is this:
[http://shibuvarkala.blogspot.com/2009/04/howto-make-ubuntu-904-jaunty-jackalope.html](http://shibuvarkala.blogspot.com/2009/04/howto-make-ubuntu-904-jaunty-jackalope.html)

and you can play DVDs in VLC

---

