---
title: "No sound in HVR-1800"
date: 2009-02-27
forum: Mythbuntu
---

### Post by karlec on 2009-02-27
I have two capture cards, PVR500 and HVR1800, and I am using S/PDIF to my receiver.  I never had any sound issues until I decided to use S/PDIF passthrough and used the following to get going [http://ubuntuforums.org/showthread.php?t=843012]("http://ubuntuforums.org/showthread.php?t=843012") ;it still doesn't seem to be entirely stable cause when I shutdown my box I may or may not have sound altogether when it is turned back on.  
My problem is that when sound is working on my machine, the PVR500 is the only one with sound, whenever I switch to the DVB tuner I get this crackling/shrieking noise.

Can anyone offer some pointers on how to fix this?

The PVR500 is connected via composite to my directv STB, the HVR is used with an OTA antenna.

Thanks

---

### Post by newlinux on 2009-02-27
can you play the recording outside of myth, with say mplayer? This will help diagnose whether it is a system or myth problem. The commandline output from mplayer may give you some information as well.

You may also want to take a look and post your frontend logs from when you are playing back content with no sound.

---

### Post by karlec on 2009-02-27
Thanks for the reply.  I can play a dvd with Mplayer using cli.  The ATSC signals are the only ones with the sound issues.  I'll post my frontend logs later.

---

### Post by karlec on 2009-02-27
Here is my frontend logs taken while playing live TV

```
karlec@central$ tail -f /var/log/mythtv/mythfrontend.log
2009-02-27 22:08:13.886 [mpeg2video @ 0x7fec1a801e90]Warning MVs not available
2009-02-27 22:08:14.071 [mpeg2video @ 0x7fec1a801e90]ac-tex damaged at 63 0
2009-02-27 22:08:14.078 [mpeg2video @ 0x7fec1a801e90]Warning MVs not available
2009-02-27 22:08:16.527 [mpeg2video @ 0x7fec1a801e90]ac-tex damaged at 82 13
2009-02-27 22:08:43.195 TV: Attempting to change from WatchingLiveTV to None
2009-02-27 22:08:43.238 ~OpenGLVideoSync() -- begin
2009-02-27 22:08:43.238 ~OpenGLVideoSync() -- middle
2009-02-27 22:08:43.238 ~OpenGLVideoSync() -- end
2009-02-27 22:08:43.662 TV: Changing from WatchingLiveTV to None
2009-02-27 22:08:43.697 DPMS Reactivated.
2009-02-27 22:11:12.552 TV: Attempting to change from None to WatchingLiveTV
2009-02-27 22:11:12.553 Using protocol version 40
2009-02-27 22:11:14.036 NVP: Disabling Audio, params(-1,2,44100)
2009-02-27 22:11:14.059 DPMS Deactivated 
2009-02-27 22:11:14.070 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2009-02-27 22:11:14.174 OSD Theme Dimensions W: 640 H: 480
2009-02-27 22:11:14.662 TV: Changing from None to WatchingLiveTV
2009-02-27 22:11:14.663 Realtime priority would require SUID as root.
Initialize Yadif Deinterlacer. In-Pixformat = 1 Out-Pixformat=1
yadifdeint: size changed from 0 x 0 -> 720 x 576
2009-02-27 22:11:14.772 OpenGLVideoSync()
2009-02-27 22:11:14.851 Video timing method: SGI OpenGL
2009-02-27 22:11:17.306 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2009-02-27 22:11:17.944 AFD: Opened codec 0x7fec08257110, id(MPEG2VIDEO) type(Video)
2009-02-27 22:11:17.944 AFD: codec AC3 has 6 channels
2009-02-27 22:11:17.945 AFD: Opened codec 0x7fec08259a10, id(AC3) type(Audio)
2009-02-27 22:11:17.946 AFD: codec AC3 has 1 channels
2009-02-27 22:11:17.947 AFD: Opened codec 0x7fec0847d880, id(AC3) type(Audio)
2009-02-27 22:11:18.160 Opening audio device 'default'. ch 6(2) sr 48000
2009-02-27 22:11:18.160 Opening ALSA audio device 'default'.
2009-02-27 22:11:18.165 ALSA, Warning: mmap not available, attempting to fall back to slow writes.
2009-02-27 22:11:18.276 NVP: Enabling Audio
2009-02-27 22:11:18.280 Opening audio device 'default'. ch 2(2) sr 48000
2009-02-27 22:11:18.280 Opening ALSA audio device 'default'.
2009-02-27 22:11:18.284 ALSA, Warning: mmap not available, attempting to fall back to slow writes.
2009-02-27 22:11:18.539 WriteAudio: buffer underrun
2009-02-27 22:11:36.523 [mpeg2video @ 0x7fec1a801e90]skipped MB in I frame at 104 11
2009-02-27 22:11:36.526 [mpeg2video @ 0x7fec1a801e90]skipped MB in I frame at 41 24
2009-02-27 22:11:36.526 [mpeg2video @ 0x7fec1a801e90]ac-tex damaged at 98 25
2009-02-27 22:11:36.528 [mpeg2video @ 0x7fec1a801e90]skipped MB in I frame at 66 34
2009-02-27 22:11:36.530 [mpeg2video @ 0x7fec1a801e90]ac-tex damaged at 57 45
2009-02-27 22:11:36.533 [mpeg2video @ 0x7fec1a801e90]invalid mb type in I Frame at 79 56
2009-02-27 22:11:36.534 [mpeg2video @ 0x7fec1a801e90]ac-tex damaged at 95 63
2009-02-27 22:11:36.534 [mpeg2video @ 0x7fec1a801e90]ac-tex damaged at 16 64
2009-02-27 22:11:36.535 [mpeg2video @ 0x7fec1a801e90]Warning MVs not available
2009-02-27 22:11:36.562 [mpeg2video @ 0x7fec1a801e90]ac-tex damaged at 62 12
2009-02-27 22:11:36.572 [mpeg2video @ 0x7fec1a801e90]Warning MVs not available
2009-02-27 22:12:22.520 [mpeg2video @ 0x7fec1a801e90]ac-tex damaged at 34 61
2009-02-27 22:12:22.520 [mpeg2video @ 0x7fec1a801e90]slice mismatch
2009-02-27 22:12:22.520 [mpeg2video @ 0x7fec1a801e90]slice mismatch
2009-02-27 22:12:22.520 [mpeg2video @ 0x7fec1a801e90]ac-tex damaged at 15 3
2009-02-27 22:12:22.521 [mpeg2video @ 0x7fec1a801e90]invalid cbp at 17 4
2009-02-27 22:12:22.521 [mpeg2video @ 0x7fec1a801e90]invalid mb type in B Frame at 54 5
2009-02-27 22:12:22.521 [mpeg2video @ 0x7fec1a801e90]ac-tex damaged at 0 6
2009-02-27 22:12:22.521 [mpeg2video @ 0x7fec1a801e90]mb incr damaged
2009-02-27 22:12:22.521 [mpeg2video @ 0x7fec1a801e90]ac-tex damaged at 75 8
2009-02-27 22:12:22.521 [mpeg2video @ 0x7fec1a801e90]mb incr damaged
2009-02-27 22:12:22.521 [mpeg2video @ 0x7fec1a801e90]ac-tex damaged at 0 10
2009-02-27 22:12:22.521 [mpeg2video @ 0x7fec1a801e90]slice mismatch
2009-02-27 22:12:22.521 [mpeg2video @ 0x7fec1a801e90]invalid mb type in B Frame at 6 12
2009-02-27 22:12:22.522 [mpeg2video @ 0x7fec1a801e90]slice mismatch
2009-02-27 22:12:22.522 [mpeg2video @ 0x7fec1a801e90]ac-tex damaged at 29 16
2009-02-27 22:12:22.522 [mpeg2video @ 0x7fec1a801e90]mb incr damaged
2009-02-27 22:12:22.522 [mpeg2video @ 0x7fec1a801e90]invalid cbp at 26 18
2009-02-27 22:12:22.522 [mpeg2video @ 0x7fec1a801e90]mb incr damaged
2009-02-27 22:12:22.522 [mpeg2video @ 0x7fec1a801e90]ac-tex damaged at 32 20
2009-02-27 22:12:22.522 [mpeg2video @ 0x7fec1a801e90]slice mismatch
2009-02-27 22:12:22.522 [mpeg2video @ 0x7fec1a801e90]ac-tex damaged at 27 22
2009-02-27 22:12:22.522 [mpeg2video @ 0x7fec1a801e90]ac-tex damaged at 4 23
2009-02-27 22:12:22.522 [mpeg2video @ 0x7fec1a801e90]mb incr damaged
2009-02-27 22:12:22.522 [mpeg2video @ 0x7fec1a801e90]ac-tex damaged at 17 25
2009-02-27 22:12:22.522 [mpeg2video @ 0x7fec1a801e90]ac-tex damaged at 30 26
2009-02-27 22:12:22.523 [mpeg2video @ 0x7fec1a801e90]ac-tex damaged at 5 27
2009-02-27 22:12:22.523 [mpeg2video @ 0x7fec1a801e90]ac-tex damaged at 6 28
2009-02-27 22:12:22.523 [mpeg2video @ 0x7fec1a801e90]ac-tex damaged at 26 29
2009-02-27 22:12:22.523 [mpeg2video @ 0x7fec1a801e90]slice mismatch
2009-02-27 22:12:22.523 [mpeg2video @ 0x7fec1a801e90]ac-tex damaged at 3 31
2009-02-27 22:12:22.523 [mpeg2video @ 0x7fec1a801e90]invalid cbp at 13 32
2009-02-27 22:12:22.523 [mpeg2video @ 0x7fec1a801e90]ac-tex damaged at 16 33
2009-02-27 22:12:22.523 [mpeg2video @ 0x7fec1a801e90]ac-tex damaged at 5 34
2009-02-27 22:12:22.523 [mpeg2video @ 0x7fec1a801e90]invalid cbp at 17 35
2009-02-27 22:12:22.523 [mpeg2video @ 0x7fec1a801e90]ac-tex damaged at 24 36
2009-02-27 22:12:22.523 [mpeg2video @ 0x7fec1a801e90]ac-tex damaged at 13 37
2009-02-27 22:12:22.523 [mpeg2video @ 0x7fec1a801e90]ac-tex damaged at 15 44
2009-02-27 22:12:22.523 [mpeg2video @ 0x7fec1a801e90]ac-tex damaged at 68 45
2009-02-27 22:12:22.523 [mpeg2video @ 0x7fec1a801e90]ac-tex damaged at 27 47
2009-02-27 22:12:22.524 [mpeg2video @ 0x7fec1a801e90]mb incr damaged
2009-02-27 22:12:22.524 [mpeg2video @ 0x7fec1a801e90]ac-tex damaged at 25 50
2009-02-27 22:12:22.524 [mpeg2video @ 0x7fec1a801e90]ac-tex damaged at 83 51
2009-02-27 22:12:22.524 [mpeg2video @ 0x7fec1a801e90]ac-tex damaged at 13 52
2009-02-27 22:12:22.524 [mpeg2video @ 0x7fec1a801e90]mb incr damaged
2009-02-27 22:12:22.524 [mpeg2video @ 0x7fec1a801e90]mb incr damaged
2009-02-27 22:12:22.524 [mpeg2video @ 0x7fec1a801e90]ac-tex damaged at 23 58
2009-02-27 22:12:22.524 [mpeg2video @ 0x7fec1a801e90]slice mismatch
2009-02-27 22:12:22.524 [mpeg2video @ 0x7fec1a801e90]mb incr damaged
2009-02-27 22:12:22.525 [mpeg2video @ 0x7fec1a801e90]mb incr damaged
2009-02-27 22:12:22.525 [mpeg2video @ 0x7fec1a801e90]ac-tex damaged at 31 63
2009-02-27 22:12:22.525 [mpeg2video @ 0x7fec1a801e90]ac-tex damaged at 10 64
2009-02-27 22:12:22.525 [mpeg2video @ 0x7fec1a801e90]ac-tex damaged at 17 65
2009-02-27 22:12:22.526 [mpeg2video @ 0x7fec1a801e90]ac-tex damaged at 20 66
2009-02-27 22:12:22.526 [mpeg2video @ 0x7fec1a801e90]ac-tex damaged at 12 67
2009-02-27 22:12:40.363 [mpeg2video @ 0x7fec1a801e90]mb incr damaged
2009-02-27 22:12:40.368 [mpeg2video @ 0x7fec1a801e90]Warning MVs not available
2009-02-27 22:12:41.696 [mpeg2video @ 0x7fec1a801e90]ac-tex damaged at 33 19
2009-02-27 22:12:42.528 [mpeg2video @ 0x7fec1a801e90]slice mismatch
2009-02-27 22:12:42.529 [mpeg2video @ 0x7fec1a801e90]ac-tex damaged at 100 2
2009-02-27 22:12:42.529 [mpeg2video @ 0x7fec1a801e90]invalid cbp at 23 11
2009-02-27 22:12:42.530 [mpeg2video @ 0x7fec1a801e90]invalid mb type in P Frame at 14 43
2009-02-27 22:12:42.530 [mpeg2video @ 0x7fec1a801e90]ac-tex damaged at 30 46
2009-02-27 22:12:42.530 [mpeg2video @ 0x7fec1a801e90]ac-tex damaged at 81 48
2009-02-27 22:12:43.888 [mpeg2video @ 0x7fec1a801e90]00 motion_type at 4 54
2009-02-27 22:12:43.889 [mpeg2video @ 0x7fec1a801e90]slice mismatch
2009-02-27 22:12:43.980 [mpeg2video @ 0x7fec1a801e90]ac-tex damaged at 31 43
2009-02-27 22:12:43.981 [mpeg2video @ 0x7fec1a801e90]00 motion_type at 12 62
2009-02-27 22:12:43.982 [mpeg2video @ 0x7fec1a801e90]invalid mb type in P Frame at 102 66
2009-02-27 22:12:44.000 [mpeg2video @ 0x7fec1a801e90]invalid mb type in P Frame at 66 22
2009-02-27 22:12:44.000 [mpeg2video @ 0x7fec1a801e90]ac-tex damaged at 6 23
2009-02-27 22:12:44.000 [mpeg2video @ 0x7fec1a801e90]ac-tex damaged at 83 25
2009-02-27 22:12:44.136 [mpeg2video @ 0x7fec1a801e90]00 motion_type at 51 0
2009-02-27 22:12:44.136 [mpeg2video @ 0x7fec1a801e90]slice mismatch
2009-02-27 22:12:45.053 [mpeg2video @ 0x7fec1a801e90]mb incr damaged
2009-02-27 22:12:45.053 [mpeg2video @ 0x7fec1a801e90]slice mismatch
2009-02-27 22:12:45.054 [mpeg2video @ 0x7fec1a801e90]slice mismatch
2009-02-27 22:12:45.054 [mpeg2video @ 0x7fec1a801e90]slice mismatch
2009-02-27 22:12:45.054 [mpeg2video @ 0x7fec1a801e90]ac-tex damaged at 28 8
2009-02-27 22:12:45.054 [mpeg2video @ 0x7fec1a801e90]ac-tex damaged at 20 9
2009-02-27 22:12:45.054 [mpeg2video @ 0x7fec1a801e90]ac-tex damaged at 91 40
2009-02-27 22:12:45.054 [mpeg2video @ 0x7fec1a801e90]slice mismatch
2009-02-27 22:12:45.054 [mpeg2video @ 0x7fec1a801e90]invalid cbp at 71 43
2009-02-27 22:12:45.055 [mpeg2video @ 0x7fec1a801e90]ac-tex damaged at 104 46
2009-02-27 22:12:45.055 [mpeg2video @ 0x7fec1a801e90]slice mismatch
2009-02-27 22:12:45.055 [mpeg2video @ 0x7fec1a801e90]invalid cbp at 49 16
2009-02-27 22:12:45.055 [mpeg2video @ 0x7fec1a801e90]slice mismatch
2009-02-27 22:12:45.055 [mpeg2video @ 0x7fec1a801e90]ac-tex damaged at 69 22
2009-02-27 22:12:45.055 [mpeg2video @ 0x7fec1a801e90]invalid cbp at 87 29
2009-02-27 22:12:45.056 [mpeg2video @ 0x7fec1a801e90]invalid cbp at 76 30
2009-02-27 22:12:51.230 TV: Attempting to change from WatchingLiveTV to None
2009-02-27 22:12:51.308 ~OpenGLVideoSync() -- begin
2009-02-27 22:12:51.308 ~OpenGLVideoSync() -- middle
2009-02-27 22:12:51.309 ~OpenGLVideoSync() -- end
2009-02-27 22:12:51.693 TV: Changing from WatchingLiveTV to None
2009-02-27 22:12:51.734 DPMS Reactivated.
```

---

### Post by newlinux on 2009-02-27
> **karlec said:**
> Thanks for the reply.  I can play a dvd with Mplayer using cli.  The ATSC signals are the only ones with the sound issues.  I'll post my frontend logs later.

yes, but what happens when you play one of those recordings with mplayer? You need to test on the same files that are giving you problems in myth to know for sure.

---

### Post by newlinux on 2009-02-27
Just as a quick test, temporarily disable pulse and then try playing a recording... Still could be a pulseaudio configuration problem.

```

killall pulseaudio

```

---

### Post by karlec on 2009-02-28
Now there is no sound at all in Mythtv.
Logs:
```
karlec@central$ tail -f /var/log/mythtv/mythfrontend.log
2009-02-28 00:04:49.279 AFD: codec AC3 has 6 channels
2009-02-28 00:04:49.280 AFD: Opened codec 0x7febfc84e360, id(AC3) type(Audio)
2009-02-28 00:04:49.281 AFD: codec AC3 has 1 channels
2009-02-28 00:04:49.283 AFD: Opened codec 0x7febfc43a5f0, id(AC3) type(Audio)
2009-02-28 00:04:49.315 Opening audio device 'default'. ch 6(2) sr 48000
2009-02-28 00:04:49.315 Opening ALSA audio device 'default'.
ALSA lib pulse.c:272:(pulse_connect) PulseAudio: Unable to connect: Connection refused

2009-02-28 00:04:49.382 AudioOutput Error: snd_pcm_open(default): Connection refused
2009-02-28 00:04:49.382 NVP: Disabling Audio, reason is: snd_pcm_open(default): Connection refused
```

---

