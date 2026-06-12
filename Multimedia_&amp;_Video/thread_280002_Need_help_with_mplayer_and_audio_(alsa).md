---
title: "Need help with mplayer and audio (alsa)"
date: 2006-10-18
forum: Multimedia &amp; Video
---

### Post by boast on 2006-10-18
I get the following, and have no clue how to fix it.

```
mplayer http://media1.break.com/dnet/media/2006/10 /beating_speed_monitoring_cameras.wmv
MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Intel Pentium 4/Celeron D Prescott; Xeon Nocona (Family: 15, Stepping: 3)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.


91 audio & 204 video codecs
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing http://media1.break.com/dnet/media/2006/10/beating_speed_monitoring_came ras.wmv.
STREAM_HTTP(1), URL: http://media1.break.com/dnet/media/2006/10/beating_speed_mo nitoring_cameras.wmv
Resolving media1.break.com for AF_INET6...
Couldn't resolve name for AF_INET6: media1.break.com
Resolving media1.break.com for AF_INET...
Connecting to server media1.break.com[68.142.101.68]: 80...
STREAM_ASF, URL: http://media1.break.com/dnet/media/2006/10/beating_speed_monito ring_cameras.wmv
Resolving media1.break.com for AF_INET6...
Couldn't resolve name for AF_INET6: media1.break.com
Resolving media1.break.com for AF_INET...
Connecting to server media1.break.com[68.142.101.68]: 80...
Stream not seekable!
ASF file format detected.
VIDEO:  [WMV3]  320x240  24bpp  1000.000 fps    0.0 kbps ( 0.0 kbyte/s)
Clip info:
 name: Produced by Telestream Flip Technology
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 160.0 kbit/10.42% (ratio: 20001->192000)
Selected audio codec: [ffwmav2] afm: ffmpeg (DivX audio v2 (FFmpeg))
==========================================================================
==========================================================================
Opening video decoder: [dmo] DMO video codecs
Win32 LoadLibrary failed to load: wmv9dmod.dll, /usr/lib/win32/wmv9dmod.dll, /us r/local/lib/win32/wmv9dmod.dll
IMediaObject ERROR: 0x85de2b5  could not open DMO DLL (0x0 : 0)
Failed to create DMO filter
ERROR: Could not open required DirectShow codec wmv9dmod.dll.
You need to upgrade/install the binary codecs package.
Go to http://mplayerhq.hu/homepage/dload.html
VDecoder init failed :(
Opening video decoder: [dmo] DMO video codecs
Win32 LoadLibrary failed to load: wmvdmod.dll, /usr/lib/win32/wmvdmod.dll, /usr/ local/lib/win32/wmvdmod.dll
IMediaObject ERROR: 0x85de2b5  could not open DMO DLL (0x0 : 0)
Failed to create DMO filter
ERROR: Could not open required DirectShow codec wmvdmod.dll.
You need to upgrade/install the binary codecs package.
Go to http://mplayerhq.hu/homepage/dload.html
VDecoder init failed :(
Cannot find codec matching selected -vo and video format 0x33564D57.
Read DOCS/HTML/en/codecs.html!
==========================================================================
Building audio filter chain for 48000Hz/2ch/s16le -> 0Hz/0ch/??...
alsa-init: 2 soundcard found, using: default
ALSA lib confmisc.c:672:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_card_driver return ed error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_concat returned er ror: No such device
ALSA lib confmisc.c:1072:(snd_func_refer) error evaluating name
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned err or: No such device
ALSA lib conf.c:3962:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2102:(snd_pcm_open_noupdate) Unknown PCM default
alsa-init: playback open error: No such device
[AO OSS] audio_setup: Can't open audio device /dev/dsp: No such file or director y
[AO SDL] Samplerate: 48000Hz Channels: Stereo Format s16le
ALSA lib confmisc.c:672:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_card_driver return ed error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_concat returned er ror: No such device
ALSA lib confmisc.c:1072:(snd_func_refer) error evaluating name
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned err or: No such device
ALSA lib conf.c:3962:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2102:(snd_pcm_open_noupdate) Unknown PCM default
[AO SDL] Unable to open audio: No available audio device
ALSA lib confmisc.c:672:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_card_driver return ed error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_concat returned er ror: No such device
ALSA lib confmisc.c:1072:(snd_func_refer) error evaluating name
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned err or: No such device
ALSA lib conf.c:3962:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2102:(snd_pcm_open_noupdate) Unknown PCM default
[AO ESD] esd_open_sound failed: Connection reset by peer
[AO ARTS] loading the aRts backend "/usr/lib/libartscbackend.la" failed
Could not open/initialize audio device -> no sound.
Audio: no sound
Video: no video


Exiting... (End of file)

```

Outside of mplayer/flash sound works fine.

---

### Post by taurus on 2006-10-18
From a terminal, type

```
gmplayer
```
Click the right button while the cursor is in the mplayer window and pick Preferences.  In the Audio tag, try oss and Okay.  Shut it down and start it up again and see if you hear any sound coming from a movie!!!

---

### Post by boast on 2006-10-19
Well the alsa driver works now, but the video and audio isnt synced. 

I have frame dropping enabled, but it doesn't work. The video also plays slow in fullscreen. I'm using the X11 drivers. (I have onboard video)

---

### Post by taurus on 2006-10-19
Try using xv for your video instead of x11!!!

---

### Post by boast on 2006-10-19
K, using xv (it wasn't working before). But I still can't get sync.

---

### Post by wilberfan on 2006-11-25
What fixed this for me was changing the audio setting from alsa to oss...

:-k

---

