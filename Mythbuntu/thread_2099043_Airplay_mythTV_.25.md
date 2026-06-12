---
title: "Airplay mythTV .25"
date: 2012-12-28
forum: Mythbuntu
---

### Post by diesel48 on 2012-12-28
I enabled airplay on the frontend using the wiki. [http://www.mythtv.org/wiki/AirTunes/AirPlay](http://www.mythtv.org/wiki/AirTunes/AirPlay) Playing audio from my iphone works just fine. I tried playing a video from the youtube app. It played video but no sound. I rebooted everything and tried it again. Now it says please wait and nothing happens. It still plays audio from my music app though. Anyone experiences this? Would love to be able to use the youtube or trailers app with video and sound.

---

### Post by nickrout on 2012-12-28
Logs?

---

### Post by diesel48 on 2012-12-28
which logs do I look at?

---

### Post by nickrout on 2012-12-28
/var/log/mythtv/mythfrontend.log

---

### Post by diesel48 on 2012-12-29
Here is the mythfrontend log when I play from the youtube app. The video plays again but no audio.

Dec 29 16:09:05 masterbackend mythfrontend[1892]: N CoreContext audioplayer.cpp:167 (ReinitAudio) AudioPlayer: Enabling Audio
Dec 29 16:09:05 masterbackend mythfrontend[1892]: I CoreContext avformatdecoder.cpp:2102 (ScanStreams) AFD: Opened codec 0x43c03e0, id(H264) type(Video)
Dec 29 16:09:05 masterbackend mythfrontend[1892]: I CoreContext avformatdecoder.cpp:1960 (ScanStreams) AFD: codec AAC has 2 channels
Dec 29 16:09:05 masterbackend mythfrontend[1892]: I CoreContext avformatdecoder.cpp:2102 (ScanStreams) AFD: Opened codec 0x4bd7140, id(AAC) type(Audio)
Dec 29 16:09:05 masterbackend mythfrontend[1892]: W CoreContext ringbuffer.cpp:387 (CalcReadAheadThresh) Enabling buffering optimisations for low bitrate stream.
Dec 29 16:09:05 masterbackend mythfrontend[1892]: W CoreContext ringbuffer.cpp:387 (CalcReadAheadThresh) Enabling buffering optimisations for low bitrate stream.
Dec 29 16:09:05 masterbackend mythfrontend[1892]: I CoreContext audio/audiooutputbase.cpp:697 (Reconfigure) AO: Resampling from 44 kHz to 48 kHz with quality medium
Dec 29 16:09:05 masterbackend mythfrontend[1892]: I CoreContext audio/audiooutputbase.cpp:791 (Reconfigure) AO: Opening audio device 'hdmi:CARD=NVidia,DEV=1' ch 2(2) sr 48000 sf signed 16 bit r
eenc 0
Dec 29 16:09:05 masterbackend mythfrontend[1892]: E CoreContext audio/audiooutputalsa.cpp:507 (OpenDevice) ALSA: snd_pcm_open("hdmi:CARD=NVidia,DEV=1"): Device or resource busy
Dec 29 16:09:05 masterbackend mythfrontend[1892]: E CoreContext audio/audiooutput.cpp:242 (Error) AudioOutput Error: Aborting reconfigure
Dec 29 16:09:05 masterbackend mythfrontend[1892]: N CoreContext audioplayer.cpp:161 (ReinitAudio) AudioPlayer: Disabling Audio, reason is: Aborting reconfigure
Dec 29 16:09:05 masterbackend mythfrontend[1892]: I CoreContext mythpainter_ogl.cpp:62 (ClearCache) Clearing OpenGL painter cache.

Maybe something due to AAC?

---

### Post by nickrout on 2012-12-30
Dec 29 16:09:05 masterbackend mythfrontend[1892]: E CoreContext audio/audiooutputalsa.cpp:507 (OpenDevice) ALSA: snd_pcm_open("hdmi:CARD=NVidia,DEV=1"): Device or resource busy


something else is using your chosen video device.

---

### Post by diesel48 on 2013-01-03
Not sure what was going on. I paused the youtube video before going to airplay. It works maybe 80% of the time then.

---

