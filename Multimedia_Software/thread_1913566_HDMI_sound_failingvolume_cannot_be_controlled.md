---
title: "HDMI sound failing/volume cannot be controlled"
date: 2012-01-22
forum: Multimedia Software
---

### Post by faustool on 2012-01-22
Hi,

I've been dealing with this for days, but I couldn't find a solution anywhere.

I have a simple setup at home:
Dell Vostro 3500 laptop -> hdmi out to HDTV LG 32LV5500 -> optical out to Home Theater LG HT503SH.

After some work on it, I could manage to have audio 5.1 out with VLC configuring:
[INDENT]Output Module: ALSA audio output
Checked: Use S/PDIF when available 
Selected: HDA Intel: HDMI (hw:0,3)
[/INDENT]
I can also play 5.1 from aplay with the command line: 
```
aplay -D plughw:CARD=Intel,DEV=3 Norrlanda.wav
```

The problem is that, while playing, the sound constantly fails, getting mute for half a second, then I get small chunks of sizzle sound. After this, it gets fine again until the half second mute and next chunks of sizzles, being it a loop for the duration of the media.

One of the possible reasons I've read about is the volume being too high. Indeed, when reproducing with S/PDIF option on in VLC, the sound is much higher.

However, I can't decrease the volume! I can't even mute from VLC. Clicking the mute button has no effect.

When opening alsamixer, the S/PDIF item appears, but has no bar on top of it. Changing the PCM bar doesn't affect the output.

Someone might say: why don't you stick with pulseaudio? 

Then I will have a different problem. Pulseaudio indeed shows me, in the Sound Settings, under Hardware tab, a list of items I could choose, including: "Digital Surround 5.1 (HDMI) Output". 
However, if I go to Test Speakers, none of Center, Rear Right, Rear Left and Subwoofer works. They don't sound anything out, just Front Left and Front Right. From VLC, if I choose pulseaudio or Default, I can hear only the background sound from the media (horses, cups on the table, steps, music), but no voice. It is actually very funny :)

With so much information, you might be asking: What does he really want? I just want to watch my media in 5.1, with good sound. How can I?

I don't know if there's anything else I can tell to get help.

I'm running Ubuntu 11.10 and here goes a list of command outputs you may ask me:

```

uname -r
3.0.0-15-generic

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: HDMI 0 [HDMI 0]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

aplay -L
default
    Playback/recording through the PulseAudio sound server
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
hdmi:CARD=Intel,DEV=0
    HDA Intel, HDMI 0
    HDMI Audio Output
dmix:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    Direct sample mixing device
dmix:CARD=Intel,DEV=3
    HDA Intel, HDMI 0
    Direct sample mixing device
dsnoop:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    Direct sample snooping device
dsnoop:CARD=Intel,DEV=3
    HDA Intel, HDMI 0
    Direct sample snooping device
hw:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    Direct hardware device without any conversions
hw:CARD=Intel,DEV=3
    HDA Intel, HDMI 0
    Direct hardware device without any conversions
plughw:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    Hardware device with all software conversions
plughw:CARD=Intel,DEV=3
    HDA Intel, HDMI 0
    Hardware device with all software conversions

cat /proc/asound/card0/codec#* | grep Codec
Codec: IDT 92HD81B1X5
Codec: Intel IbexPeak HDMI

aplay -v -D plughw:CARD=Intel,DEV=3 SURROUNDTEST_011212.wav 
Playing WAVE 'SURROUNDTEST_011212.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo
Plug PCM: Hardware PCM card 0 'HDA Intel' device 3 subdevice 0
Its setup is:
  stream       : PLAYBACK
  access       : RW_INTERLEAVED
  format       : S16_LE
  subformat    : STD
  channels     : 2
  rate         : 44100
  exact rate   : 44100 (44100/1)
  msbits       : 16
  buffer_size  : 22016
  period_size  : 5504
  period_time  : 124807
  tstamp_mode  : NONE
  period_step  : 1
  avail_min    : 5504
  period_event : 0
  start_threshold  : 22016
  stop_threshold   : 22016
  silence_threshold: 0
  silence_size : 0
  boundary     : 6196953087261802496
  appl_ptr     : 0
  hw_ptr       : 0


```

Above, aplay shows 2 channels only, but the audio is perfectly correct.

---

