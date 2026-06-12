---
title: "Can't get NetJack to work"
date: 2013-10-03
forum: Multimedia Software
---

### Post by bazilio1 on 2013-10-03
If I run jackd and use it locally it works, but when I try to use netjack to connect master and slave I am not gettings sound and no errors is printed out. I even tried running netjack master and slave on same host.

Here is how I run jackd locally and sound works:

**console1**
```

tarantula!baz% jackd -r -dalsa -S                                                                                                                                                              <15:37>
jackd 0.122.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

Cannot create thread 1 Operation not permitted
JACK compiled with System V SHM support.
loading driver ..
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|16bit
control device hw:0
configuring for 48000Hz, period = 1024 frames (21.3 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 16bit integer little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 16bit integer little-endian
ALSA: use 2 periods for playback

```

**console2**
```
tarantula!baz% mplayer -vo null -ao jack,port=system:playback_1 dtp.mp4                                                                                                                        <15:38>
MPlayer2 UNKNOWN (C) 2000-2012 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dtp.mp4.
Cache fill:  0.00% (0 bytes)   

Detected file format: QuickTime/MPEG-4/Motion JPEG 2000 format (libavformat)
[lavf] stream 0: video (h264), -vid 0
[lavf] stream 1: audio (aac), -aid 0, -alang eng
VIDEO:  [H264]  1920x1080  24bpp  1000.000 fps  7412.2 kbps (904.8 kbyte/s)
Clip info:
 major_brand: isom
 minor_version: 512
 compatible_brands: isomiso2avc1mp41
 encoder: Lavf55.12.102
Load subtitles in .
[ass] auto-open
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Asking decoder to use 4 threads if supported.
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 8000 Hz, 1 ch, s16le, 24.1 kbit/18.82% (ratio: 3011->16000)
Selected audio codec: [ffaac] afm: ffmpeg (FFmpeg AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
AO: [jack] 48000Hz 1ch floatle (4 bytes per sample)
Starting playback...
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [null] 1920x1080 => 1920x1080 Planar YV12 
Colorspace details not fully supported by selected vo.
A:  14.7 V:  14.6 A-V: -0.000 ct: -0.067   0/  0  0%  2%  0.5% 0 0 0% 


Exiting... (End of file)

```


And whe I try to run netjack I am not getting any sound:
**console1**
```
tarantula!baz% jackd -n master1 -r -dalsa -S                                                                                                                                                   <15:39>
jackd 0.122.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

Cannot create thread 1 Operation not permitted
JACK compiled with System V SHM support.
loading driver ..
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|16bit
control device hw:0
configuring for 48000Hz, period = 1024 frames (21.3 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 16bit little-endian
ALSA: use 2 periods for playback

```

**console2**
```
tarantula!baz% jackd -r -dnet -I0 -O0                                                                                                                                                          <15:40>
jackd 0.122.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

Cannot create thread 1 Operation not permitted
JACK compiled with System V SHM support.
loading driver ..
creating net driver ... net_pcm|48000|1024|3000|2|2|transport_sync:1
AutoConfig Override !!!
MTU is set to 1400 bytes
netjack: period   : up: 1024 / dn: 1024
netjack: framerate: 48000
netjack: audio    : cap: 2 / pbk: 2)
netjack: midi     : cap: 0 / pbk: 0)
netjack: buffsize : rx: 8248)
netxruns amount: 21ms

```

**console3**
```
tarantula!baz% jack_netsource -H 127.0.0.1 -s master1 -I0 -O0                                                                                                                                  <15:40>
Connected :-)
netjack: at frame 000046 -> total netxruns 1  (2%) queue time= 84855

```

**console4**
```
tarantula!baz% jack_lsp                                                                                                                                                                        <15:41>
system:capture_1
system:capture_2
system:playback_1
system:playback_2
0 ~
tarantula!baz% mplayer -vo null -ao jack,port=system:playback_1 dtp.mp4                                                                                                                        <15:41>
MPlayer2 UNKNOWN (C) 2000-2012 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dtp.mp4.
Cache fill:  0.00% (0 bytes)   

Detected file format: QuickTime/MPEG-4/Motion JPEG 2000 format (libavformat)
[lavf] stream 0: video (h264), -vid 0
[lavf] stream 1: audio (aac), -aid 0, -alang eng
VIDEO:  [H264]  1920x1080  24bpp  1000.000 fps  7412.2 kbps (904.8 kbyte/s)
Clip info:
 major_brand: isom
 minor_version: 512
 compatible_brands: isomiso2avc1mp41
 encoder: Lavf55.12.102
Load subtitles in .
[ass] auto-open
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Asking decoder to use 4 threads if supported.
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 8000 Hz, 1 ch, s16le, 24.1 kbit/18.82% (ratio: 3011->16000)
Selected audio codec: [ffaac] afm: ffmpeg (FFmpeg AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
AO: [jack] 48000Hz 1ch floatle (4 bytes per sample)
Starting playback...
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [null] 1920x1080 => 1920x1080 Planar YV12 
Colorspace details not fully supported by selected vo.
A:  14.7 V:  14.6 A-V: -0.001 ct: -0.067   0/  0  0%  2%  0.5% 0 0 0% 


Exiting... (End of file)
0 ~

```

---

