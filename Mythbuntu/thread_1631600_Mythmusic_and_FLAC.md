---
title: "Mythmusic and FLAC"
date: 2010-11-26
forum: Mythbuntu
---

### Post by GuiGuy on 2010-11-26
Other players, such as rhythmbox, on the same box play .flac files OK, mythmusic won't.

According to what I'm reading about mythbuntu (lucid/ mythtv 0.23) mythmusic should play them, but doesn't.

So, what are the prerequisites for playing flac music files in MythMusic?

Thanks

---

### Post by alien878 on 2010-11-28
Strange... I've used flac exclusively for several years without problem with myth (Initially, I started with myth for a jukebox-only solution when my CD player broke).  What does your backend/frontend log say?

---

### Post by bcg30506 on 2010-12-20
I am having an issue too with mythmusic and FLAC files.  They play but sound horrible.  It is very quiet with a loud hiss over it.  My frontend log only says:

```
2010-12-20 17:31:20.438 AO: Using resampler. From: 44100 to 48000
2010-12-20 17:31:20.438 Opening audio device 'default'. ch 2(2) sr 48000 (reenc 0)
2010-12-20 17:31:20.438 Opening ALSA audio device 'default'.
2010-12-20 17:31:20.478 Mixer unable to find control Master 1
2010-12-20 17:31:20.478 mixer unable to find control Master 1
2010-12-20 17:31:20.478 Mixer unable to find control Master 1
2010-12-20 17:31:20.479 mixer unable to find control Master 1
2010-12-20 17:31:20.530 AO: Using resampler. From: 44100 to 48000
2010-12-20 17:31:20.530 Opening audio device 'default'. ch 2(2) sr 48000 (reenc 0)
2010-12-20 17:31:20.530 Opening ALSA audio device 'default'.
2010-12-20 17:31:20.570 Mixer unable to find control Master 1
2010-12-20 17:31:20.570 mixer unable to find control Master 1
2010-12-20 17:31:20.570 Mixer unable to find control Master 1
2010-12-20 17:31:20.570 mixer unable to find control Master 1

```
The same files play perfectly and sound great on the same mythbuntu box using mplayer or even ffplay.  They are normal files created on the same box by ripping a CD using Asunder.

Bit more info:  There is no activity in the backend log.  When I run ffmpeg -i on the file, it says:
```

Stream #0.0: Audio: flac, 44100 Hz, stereo, s32

```

And mplayer reports this:
```


Audio only file format detected.
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, s32le, 808.4 kbit/28.64% (ratio: 101046->352800)
Selected audio codec: [ffflac] afm: ffmpeg (FFmpeg FLAC audio)
==========================================================================
AO: [alsa] 48000Hz 2ch s32le (4 bytes per sample)
Video: no video
Starting playback...

```

---

### Post by alien878 on 2010-12-21
It looks like you have set the "default" device in the mythmusic setup and this uses what is used for the rest of mythtv.  I suspect you have the mixer enabled in mythtv and this is causing problems.

I would recommend you set the output device directly in mythmusic setup.  Ex. ALSA:hdmi, ALSA:spdif, ALSA:plughw:0,1 or similar.  What you actually use depends on the devices available.  "aplay -l" and "aplay -L" are a good way to see what you have available.  The device you specified in mythtv setup might also be good (if it isn't "default").  This should by-pass the mythtv mixer.

Alternatively, you might try disabling the mixer in mythtv.

---

### Post by joho500 on 2010-12-21
You might consider upgrading to 0.24. It handles audio completely different and it works better. You can now scan for available audio devices in the audio setup page. It works out of the box. No need for difficult searching for the right settings/devices that was needed before.

Cheers,
Joost

---

### Post by thatguruguy on 2010-12-21
> **joho500 said:**
> You might consider upgrading to 0.24. It handles audio completely different and it works better. You can now scan for available audio devices in the audio setup page. It works out of the box. No need for difficult searching for the right settings/devices that was needed before.

Cheers,
Joost

this.

---

### Post by bcg30506 on 2010-12-21
Thanks for the replies.  I am not interested in upgrading to 0.24 yet as I've read about too many other issues and for the most part, I have a nice stable system with a good WAF.

Currently in music setup, my audio device is ALSA:default as it is in General settings for mythfrontend.  All music files play and sound fine with that setting except these FLAC files.  If I convert them to MP3, they sound fine.  If I play the FLAC files with mplayer, they sound fine.  So it is only FLAC files within mythmusic causing the issue.

aplay outputs:
```
$ aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=NVidia
    HDA NVidia, ALC1200 Analog
    Default Audio Device
front:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Digital
    IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
Forgot to also mention that it's a simple setup using the analog outputs to a 2-channel stereo.  Nothing fancy.

---

