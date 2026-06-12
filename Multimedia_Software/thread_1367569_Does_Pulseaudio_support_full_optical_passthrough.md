---
title: "Does Pulseaudio support full optical passthrough?"
date: 2009-12-29
forum: Multimedia Software
---

### Post by mhouck on 2009-12-29
I've been going crazy trying to figure out how to set up my newly installed 9.10 system to pass all audio through the optical out port.

I have a test ac3 file that I can play correctly with "aplay -D plughw:0,2 file.wav", so I know that it can work, but I can't figure out how to get Pulseaudio to automatically pass everything through.

I've gone into the Sound Preferences and changed the output type to IEC958, but it says "Duplex Stereo", and whatever I play is always in stereo, no surround.

I've read probably 50-100 pages of forum posts and how-tos which haven't helped at all.  Some of the things I've tried:

1.  there are some .asoundrc hacks which run 2-3 pages, but I tried simply adding:
```
pcm.!default {
        type plug
                slave {
                rate 48000
                pcm "spdif"
        }
}
```which didn't do anything at all.

2.   I tried adding "default-sample-channels = 8" to the /etc/pulse/daemon.conf.. which did nothing

3.  I tried adding "load-module module-alsa-sink device=hw:0,2" to the /etc/pulse/default.pa file... but this caused pulseaudio to crash

What am I doing wrong?  Whenever I try to follow an online guide, it's either for an earlier version of Ubuntu and says something like "This has been fixed in the latest versions, so this guide doesn't apply" or it'll say to check some box that just doesn't exist for me.

Does pulseaudio even support full passthrough?  One guide said that it didn't, another said that the newer versions do.  Do I have to do this on a program to program basis, since there's no way to default it?  Please help, I'm ready to seriously harm my computer at this point.

---

### Post by VertexPusher on 2009-12-29
Please post the output of
```
aplay -l
```and
```
aplay -L
```and
```
aplay -v -D plughw:0,2 file.wav
```(using your AC3 test file).

---

### Post by mhouck on 2009-12-30
```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CMI8768 [C-Media CMI8768], device 0: CMI8738-MC8 [C-Media PCI DAC/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8768 [C-Media CMI8768], device 1: CMI8738-MC8 [C-Media PCI 2nd DAC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8768 [C-Media CMI8768], device 2: CMI8738-MC8 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
``````
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CMI8768 [C-Media CMI8768], device 0: CMI8738-MC8 [C-Media PCI DAC/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8768 [C-Media CMI8768], device 1: CMI8738-MC8 [C-Media PCI 2nd DAC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8768 [C-Media CMI8768], device 2: CMI8738-MC8 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

``````
$ aplay -v -D plughw:0,2 Downloads/diatonis_dts_secret-universe.wav 
Playing WAVE 'Downloads/diatonis_dts_secret-universe.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo
Plug PCM: Hardware PCM card 0 'C-Media CMI8768' device 2 subdevice 0
Its setup is:
  stream       : PLAYBACK
  access       : RW_INTERLEAVED
  format       : S16_LE
  subformat    : STD
  channels     : 2
  rate         : 44100
  exact rate   : 44100 (44100/1)
  msbits       : 16
  buffer_size  : 16384
  period_size  : 4096
  period_time  : 92879
  tstamp_mode  : NONE
  period_step  : 1
  avail_min    : 4096
  period_event : 0
  start_threshold  : 16384
  stop_threshold   : 16384
  silence_threshold: 0
  silence_size : 0
  boundary     : 1073741824
  appl_ptr     : 0
  hw_ptr       : 0

```

---

### Post by VertexPusher on 2009-12-30
You entered "aplay -l" twice. The second one should be "aplay -L". This will print a list of predefined PCMs.

Anyway, try this .asoundrc for a start:
```
pcm.!default {
    type plug
    slave.pcm {
        type asym
        playback.pcm {
            type hw
            card CMI8768
            device 2
        }
        capture.pcm {
            type hw
            card CMI8768
            device 0
        }
    }
}
```
This should enable passthrough for ALSA's default PCM. Note that this means that only one application at a time can use the default PCM. No stream mixing will take place because that would defeat the whole idea of raw passthrough. If the default PCM is opened for recording, audio data will be read from device 0. This is defined in the "capture.pcm" block.

---

### Post by mhouck on 2009-12-30
Sorry, was doing it quickly and didn't check:

```

$ aplay -L
front:CARD=CMI8768,DEV=0
    C-Media CMI8768, C-Media PCI DAC/ADC
    Front speakers
rear:CARD=CMI8768,DEV=0
    C-Media CMI8768, C-Media PCI 2nd DAC
    Rear speakers
surround40:CARD=CMI8768,DEV=0
    C-Media CMI8768, C-Media PCI 2nd DAC
    4.0 Surround output to Front and Rear speakers
surround41:CARD=CMI8768,DEV=0
    C-Media CMI8768, C-Media PCI 2nd DAC
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=CMI8768,DEV=0
    C-Media CMI8768, C-Media PCI 2nd DAC
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=CMI8768,DEV=0
    C-Media CMI8768, C-Media PCI 2nd DAC
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=CMI8768,DEV=0
    C-Media CMI8768, C-Media PCI 2nd DAC
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=CMI8768,DEV=0
    C-Media CMI8768, C-Media PCI DAC/ADC
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    Playback/recording through the PulseAudio sound server
```

That .asoundrc will push everything through digital out?  So everything going through PA, once routed to ALSA, will go optical full-passthrough?

---

### Post by VertexPusher on 2009-12-30
> **mhouck said:**
> That .asoundrc will push everything through digital out?  So everything going through PA, once routed to ALSA, will go optical full-passthrough?
It depends on the application.

Most applications send audio to ALSA's default PCM (unless you tell them to use a specific PCM such as "plughw"). Normally it would go from there through PA and then back to ALSA. This output will now be routed straight through digital-out, bypassing PA. You can test this with aplay:
```
aplay -D plughw:0,2 test.wav
aplay test.wav
```
With the .asoundrc file in place, both commands should give you the same result. Audio will not be routed through PA any more, unless the application talks to PA directly, e.g. through a plugin.

---

