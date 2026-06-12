---
title: "can't hear this link"
date: 2010-01-06
forum: Multimedia Software
---

### Post by yuripo on 2010-01-06
hi everybody. i have ubuntu,9.10,64-bit.

i am trying to see the flowing lecture on the web but i mate few problems:

1. in Firefox i can see the stream media but i can't hear it, Mozilla is searching for codecs and this is the message that i get:
"No packages with the requested plugins found
The requested plugins are:
audio/x-asf-unknown decoder"

in Google chrome i even can't see the stream... 

with mplayer i can see the stream but can't hear it.
i am getting the following in mplayer:
```
mplayer mms://karish.bgu.ac.il/bgu-academic/Marachot_Sifra10.wmv
MPlayer UNKNOWN-4.4.1 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing mms://karish.bgu.ac.il/bgu-academic/Marachot_Sifra10.wmv.
STREAM_ASF, URL: mms://karish.bgu.ac.il/bgu-academic/Marachot_Sifra10.wmv
Resolving karish.bgu.ac.il for AF_INET6...
Couldn't resolve name for AF_INET6: karish.bgu.ac.il
Resolving karish.bgu.ac.il for AF_INET...
Connecting to server karish.bgu.ac.il[132.72.23.89]: 1755...
Connected
unknown object
unknown object
unknown object
file object, packet length = 5950 (5950)
unknown object
stream object, stream ID: 1
stream object, stream ID: 2
unknown object
data object
mmst packet_length = 5950
Cache size set to 64 KBytes
Cache fill: 12.50% (8192 bytes)   
ASF file format detected.
[asfheader] Audio stream found, -aid 1
[asfheader] Video stream found, -vid 2
VIDEO:  [WMV2]  720x576  24bpp  1000.000 fps  460.0 kbps (56.2 kbyte/s)
Clip info:
 author: Student Association & Dean of Students - Ben Gurion University of the Negev, Israel
 copyright: Student Association & Dean of Students - Ben Gurion University of the Negev, Israel
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.
[VO_3DFX] Unable to open /dev/3dfx.
[VO_XV] Could not grab port 85.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffwmv2] vfm: ffmpeg (FFmpeg WMV2/WMV8)
==========================================================================
==========================================================================
Requested audio codec family [acelp] (afm=dshow) not available.
Enable it at compilation.
Cannot find codec for audio format 0x130.
Read DOCS/HTML/en/codecs.html!
Audio: no sound
Starting playback...
VDec: vo config request - 720 x 576 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 720x576 => 720x576 Planar YV12 
V:   5.3   8/  8 ??% ??% ??,?% 0 0 12% 

```

with vlc i also can see but can't hear, that what i get:
```
vlc mms://karish.bgu.ac.il/bgu-academic/Marachot_Sifra10.wmv
VLC media player 1.0.2 Goldeneye
[0x16ea3e8] main interface error: no interface module matched "globalhotkeys,none"
[0x16ea3e8] main interface error: no suitable interface module
[0x15d5888] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x15d5888] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x16ec1d8] access_mms access: selecting stream[0x1] audio (18 kb/s)
[0x16ec1d8] access_mms access: selecting stream[0x2] video (456 kb/s)
[0x16ec1d8] access_mms access: connection successful
[0x1a5bca8] main decoder error: no suitable decoder module for fourcc `undf'.
VLC probably does not support this sound or video format.
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[0x16ec1d8] access_mms access error: failed to send command

```

please help me

thank you

---

### Post by mc4man on 2010-01-06
> i have ubuntu,9.10,64-bit.

That's going to be a bit of an issue, the audio decoder needed is available in 32 bit (w32codecs ), but not in 64 bit.

>  copyright: Student Association & Dean of Students - Ben Gurion University of the Negev, Israel
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffwmv2] vfm: ffmpeg (FFmpeg WMV2/WMV8)

[COLOR="Blue"]Opening audio decoder: [dshow] Win32/DirectShow decoders[/COLOR]
AUDIO: 16000 Hz, 1 ch, s16le, 16.0 kbit/6.25% (ratio: 2000->32000)
Selected audio codec: [COLOR="Blue"][acelp] afm: dshow (ACELP.net Sipro Lab Audio)[/COLOR]
AO: [pulse] 16000Hz 6ch s16le (2 bytes per sample)
Starting playback...



edit
It is possible to run a windows version of mplayer thru wine in a 64 bit install or build and install a 32 bit mplayer ( former is easy, later is a bit of work

---

