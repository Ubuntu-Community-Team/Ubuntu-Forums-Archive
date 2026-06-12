---
title: "h264 file will not play"
date: 2009-12-08
forum: Mythbuntu
---

### Post by bcg30506 on 2009-12-08
I have an h264 encoded flv file downloaded from the web using the Firefox extension, DownloadHelper, that will not play with MythTV's internal player or even mplayer.  When I play it with ffplay it plays but the colors are inverted like a negative.  However, I can use ffmpeg to convert it to ntsc-dvd format and everything plays it fine, colors and all.  I have many other such files that do play though they are not as hi-res at this one.  Here is the start of the console from mplayer.  The last series of messages are repeated over and over before failing to play.

```
MPlayer UNKNOWN-4.3.3 (C) 2000-2009 MPlayer Team
137 audio & 297 video codecs
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick

Playing Reebok EasyTone Commercial.flv.
libavformat file format detected.
[lavf] Video stream found, -vid 0
[lavf] Audio stream found, -aid 1
VIDEO:  [H264]  854x480  0bpp  47.917 fps  1049.7 kbps (128.1 kbyte/s)
Clip info:
 duration: 30
 starttime: 0
 totalduration: 30
 width: 854
 height: 480
 videodatarate: 1025
 audiodatarate: 104
 totaldatarate: 1120
 framerate: 24
 bytelength: 4329812
 canseekontime: true
 sourcedata: BD075FA87HH
 purl: 
 pmsg: 
==========================================================================
Forced video codec: ffh264vdpau
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
[VD_FFMPEG] XVMC-accelerated MPEG-2.
Selected video codec: [ffh264vdpau] vfm: ffmpeg (FFmpeg H.264 (VDPAU))
==========================================================================
==========================================================================
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
FAAD: compressed input bitrate missing, assuming 128kbit/s!
AUDIO: 44100 Hz, 2 ch, s16le, 128.0 kbit/9.07% (ratio: 16000->176400)
Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
[VD_FFMPEG] XVMC-accelerated MPEG-2.
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [vdpau] 854x480 => 854x480 H.264 VDPAU acceleration  [fs]
[vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.
FATAL: Cannot initialize video driver.
[h264_vdpau @ 0x89c86a0]get_buffer() failed (-1 0 0 (nil))
[h264_vdpau @ 0x89c86a0]decode_slice_header error
[h264_vdpau @ 0x89c86a0]no frame!
Error while decoding frame!
[h264_vdpau @ 0x89c86a0]get_buffer() failed (-1 0 0 (nil))
[h264_vdpau @ 0x89c86a0]decode_slice_header error
[h264_vdpau @ 0x89c86a0]no frame!
Error while decoding frame!
[h264_vdpau @ 0x89c86a0]get_buffer() failed (-1 0 0 (nil))
[h264_vdpau @ 0x89c86a0]decode_slice_header error
[h264_vdpau @ 0x89c86a0]no frame!
Error while decoding frame!
[h264_vdpau @ 0x89c86a0]get_buffer() failed (-1 0 0 (nil))
[h264_vdpau @ 0x89c86a0]decode_slice_header error
[h264_vdpau @ 0x89c86a0]no frame!
Error while decoding frame!
[h264_vdpau @ 0x89c86a0]get_buffer() failed (-1 0 0 (nil))
[h264_vdpau @ 0x89c86a0]decode_slice_header error
[h264_vdpau @ 0x89c86a0]no frame!
Error while decoding frame!
[h264_vdpau @ 0x89c86a0]get_buffer() failed (-1 0 0 (nil))
[h264_vdpau @ 0x89c86a0]decode_slice_header error
[h264_vdpau @ 0x89c86a0]no frame!
Error while decoding frame!

FATAL: Could not initialize video filters (-vf) or video output (-vo).

Exiting... (End of file)

```

---

### Post by bcg30506 on 2009-12-09
I've tried all players:  mplayer, internal mythfrontend, xine, vlc, ffplay.  I know I can play H264 as I have others.  Our camcorder records in AVCHD which uses H264 in 1080p and it plays them fine.  I'm using VDPAU in mythtv and mplayer and until this one file, they've both been working great.

---

### Post by ian dobson on 2009-12-09
Hi,

Is it just this one h264 file that screws up? It could well be that the file itself isn't 100% standards conform.

I've seen enough video files that are on the internet that play OK under xxx on windows but when you look closly at the file it's not 100% conform. If your using VDPAU for playback for both MythTv and mplayer it sounds as if the VDPAU driver can't handle this file correctly.

Regards
Ian Dobson

---

### Post by bcg30506 on 2009-12-09
Seems to be just this one file thus far.  Here is the info from it when I run ffmpeg -i on the file:

```

Seems stream 0 codec frame rate differs from container frame rate: 47.89 (23943/500) -> 47.92 (575/12)
Input #0, flv, from 'Reebok EasyTone Commercial.flv':
  Duration: 00:00:30.40, start: 0.000000, bitrate: 1049 kb/s
    Stream #0.0: Video: h264, yuv420p, 854x480 [PAR 1:1 DAR 427:240], 1049 kb/s, 47.92 tbr, 1k tbn, 47.89 tbc
    Stream #0.1: Audio: aac, 44100 Hz, stereo, s16

```

Also, vlc plays it fine in OS/X, but not in Ubuntu.  Strange.  I've attached a screen shot of the media information window in VLC on the Mac.
[IMG]http://www.bradandsteph.com/Videos/streams.png[/IMG]

---

### Post by bcg30506 on 2009-12-09
The image did not attach in edit mode, so here is a new reply for it.

---

### Post by bcg30506 on 2009-12-09
Lastly, if this helps, I've uploaded the video so you may download it and see your results.  The video was obtained from YouTube in HQ mode using Firefox's DownloadHelper add-on so it should be a "standard" format.  It is 4.2MB so it is too large to attach here.

[http://www.bradandsteph.com/Videos/Reebok%20EasyTone%20Commercial.flv]("http://www.bradandsteph.com/Videos/Reebok%20EasyTone%20Commercial.flv")

---

### Post by bcg30506 on 2009-12-09
I'm sorry to keep spamming the subject, but I keep thinking of things to look at and try.  I got it to play by specifying the video codec on the mplayer command line.  Obviously, this still does not help with the Internal myth player.

The command that played it:
```
mplayer -vc ffh264 Reebok\ EasyTone\ Commercial-1.flv
```

My .mplayer/config file:
```
vo=vdpau
vc=ffh264vdpau,ffmpeg12vdpau,ffwmv3vdpau,ffvc1vdpau,
fs=true
aspect=16:9
vfm=ffmpeg
lavdopts=fast=1:skiploopfilter=all
ao=alsa
mixer-channel=Master

```

---

### Post by andrew.46 on 2009-12-10
Hi bcg,

> **bcg30506 said:**
> Lastly, if this helps, I've uploaded the video so you may download it and see your results.  The video was obtained from YouTube in HQ mode using Firefox's DownloadHelper add-on so it should be a "standard" format.  It is 4.2MB so it is too large to attach here.

[http://www.bradandsteph.com/Videos/Reebok%20EasyTone%20Commercial.flv]("http://www.bradandsteph.com/Videos/Reebok%20EasyTone%20Commercial.flv")

I can't download the file with Firefox or wget, can you check the link? **Edit:** Working now :)

On my non-vdpau MPlayer this file plays flawlessly:

```

andrew@skamandros~/Desktop$ mplayer Reebok\ EasyTone\ Commercial.flv 
MPlayer SVN-r29982-4.3.3 (C) 2000-2009 MPlayer Team

Playing Reebok EasyTone Commercial.flv.
libavformat file format detected.
[flv @ 0x8f53a70]Estimating duration from bitrate, this may be inaccurate
[lavf] Video stream found, -vid 0
[lavf] Audio stream found, -aid 1
VIDEO:  [H264]  854x480  0bpp  47.917 fps  1049.7 kbps (128.1 kbyte/s)
Clip info:
 duration: 30
 starttime: 0
 totalduration: 30
 width: 854
 height: 480
 videodatarate: 1025
 audiodatarate: 104
 totaldatarate: 1120
 framerate: 24
 bytelength: 4329812
 canseekontime: true
 sourcedata: BD075FA87HH
 purl: 
 pmsg: 
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Unsupported PixelFormat -1
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
FAAD: compressed input bitrate missing, assuming 128kbit/s!
AUDIO: 44100 Hz, 2 ch, s16le, 128.0 kbit/9.07% (ratio: 16000->176400)
Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
AO: [oss] 44100Hz 2ch s16le (2 bytes per sample)
Starting playback...
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 854x480 => 854x480 Planar YV12 
A:  30.4 V:  30.4 A-V:  0.001 ct:  0.023   0/  0 26%  2%  1.4% 5 0 

Exiting... (End of file)

```

So I guess the problem is actually with your vdpau / NVidia drivers? BTW nice looking shoes :).

Andrew

---

### Post by yhrn on 2010-02-09
Hi,

I'm facing a similar issue in standard Ubuntu Karmic (NVidia graphics). Regardless of player (Totem, MPlayer, VLC) i get inverted colors when playing any H.264 file. Did you find any solution to this?

Mattias

---

### Post by Jose Catre-Vandis on 2010-02-09
Took this command line to play the file:
```
mplayer -vo xv -vc ffh264 -vfm ffmpeg -ao alsa -lavdopts lowres=1:fast:skiploopfilter=all reebok.flv
```

so I guess its not vdpau material

---

### Post by novinick on 2011-05-24
Try adding  filter , called 'expand' 

```
 -vf expand=::::1::8  
``` Problem occurs if you are using xv video output ,
while on x11 or xshm it just works.

 documentation [http://www.mplayerhq.hu/DOCS/man/en/mplayer.1.html#VIDEO%20FILTERS](http://www.mplayerhq.hu/DOCS/man/en/mplayer.1.html#VIDEO%20FILTERS) 


>   ```
expand[=w:h:x:y:o:a:r]
```
     
Expands (not scales) movie resolution to the given value and places the unscaled original at coordinates x, y. Can be used for placing subtitles/OSD in the resulting black bands.
     
 <w>,<h>
     
 Expanded width,height (default: original width,height). Negative values for w and h are treated as offsets to the original size.
  *EXAMPLE:*
     
 expand=0:&#8722;50:0:0
     
 Adds a 50 pixel border to the bottom of the picture.
     
 <x>,<y>
     
 position of original image on the expanded image (default: center)
      
 <o>
     
 OSD/subtitle rendering
     
 0: disable (default)
1: enable
     
 <a>
     
 Expands to fit an aspect instead of a resolution (default: 0).
  *EXAMPLE:*
     
 expand=800:::::4/3
     
 Expands to 800x600, unless the source is higher resolution, in which case it expands to fill a 4/3 aspect.
 
 <r>
     
 [COLOR=DarkOrchid]Rounds up to make both width and height divisible by <r> (default: 1).[/COLOR]


I think that in some cases hardvare overlay can not display  in resolution that is not divider of eight.

 This occurs with nvidia driver while nv or nouveau also just works, i think.
 I have no info about vdpau.

---

### Post by novinick on 2011-05-25
On intel opensrc driver seems to just works too
 out/of/the/box
 with xv or textured video,without previous tweak  .

Note i am not using vdpau at this moment.

---

