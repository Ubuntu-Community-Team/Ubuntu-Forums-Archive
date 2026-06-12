---
title: "audio reality check"
date: 2010-02-21
forum: Mythbuntu
---

### Post by wilma92010 on 2010-02-21
I upgraded from 9.04 to 9.10 mostly to correct a few nagging problems.   One thing is that I wanted to switch from analog audio to digital to fix very low level sound that seemed to downmix everything to a single output (no actual stereo sound).

I successfully configured digital audio from OTA sources from my WinTV HVR-1600 with the help of stuff posted here.  Sounds great with the correct separation and reasonable levels.  

However, I did lose sound from my videos.

After playing around a bit with the settings, I can get analog audio on my videos and digital sound from OTA TV and Recordings (Note: I did this mainly by deleting the asound.conf from /etc I created on recommendation from a posting here).   Of course, this requires me to change modes on my audio receiver, not a big deal, but I would think that everything would go through digital.  

Maybe, though, the current setup is correct.  They are from different sources (TV comes from ATSC digital input), for example, and perhaps the videos output is considered "analog" and so the setup is working as intended.

Does this make sense?   If not, any ideas on how to make everything play through digital?    The logs don't show any errors or other anomalies.

Thanks,

Wilma

---

### Post by Neon Dusk on 2010-02-21
Is you digital output a spdif connection?

How are the audio tracks different from you OTA recordings and videos? A quick way to test would be to run ffmpeg -i filename (it will complain about missing output file but should show useful info)

---

### Post by wilma92010 on 2010-02-21
Yes, the output if S/PDIF.   

The audio output device is ALSA:default 
The passthrough device is ALSA:iec958:{ AES0 0x02 }

The AC3 and DTS passthrough is enabled and so forth.

Here is the output from the ffmpeg -i....  (first is the video and second is the recording)

Input #0, mpeg, from 'somevideo.mpeg':
  Duration: 00:26:34.40, start: 0.666622, bitrate: 1393 kb/s
    Stream #0.0[0x1e0]: Video: mpeg1video, yuv420p, 352x288 [PAR 178:163 DAR 1958:1467], 1150 kb/s, 25 tbr, 90k tbn, 25 tbc
    Stream #0.1[0x1c0]: Audio: mp2, 44100 Hz, stereo, s16, 224 kb/s
At least one output file must be specified


Input #0, mpegts, from '1041_20100220200000.mpg':
  Duration: 03:29:56.15, start: 51293.604444, bitrate: 13643 kb/s
  Program 1
    Stream #0.0[0x31]: Video: mpeg2video, yuv420p, 1920x1080 [PAR 1:1 DAR 16:9], 65000 kb/s, 29.97 tbr, 90k tbn, 59.94 tbc
    Stream #0.1[0x34](eng): Audio: ac3, 48000 Hz, 5.1, s16, 384 kb/s
    Stream #0.2[0x35](spa): Audio: ac3, 48000 Hz, stereo, s16, 192 kb/s
At least one output file must be specified


I see that the video is encoded with mp2 as opposed to ac3, so I wonder whether that has something to do with it.   Not sure where that gets configured, if within mythtv or in ubuntu.

Thanks for any help.

Wilma

---

### Post by Neon Dusk on 2010-02-21
I've seen this in mythmusic where the music track was 44.1KHz but the soundcard didn't support outputting a digital signal at 44.1KHz

To fix it you could try creating an /etc/asound.conf file containing
```

pcm.!default {
     type plug
     slave.pcm "spdif"
  }

```

Then setting
Audio output device: ALSA:default  
Passthrough output device: Default

and restart the system

---

### Post by wilma92010 on 2010-02-21
Thanks!   That did the trick.   All sound now is digital.

Wilma

---

