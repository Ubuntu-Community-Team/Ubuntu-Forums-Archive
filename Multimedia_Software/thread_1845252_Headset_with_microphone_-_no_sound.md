---
title: "Headset with microphone - no sound"
date: 2011-09-16
forum: Multimedia Software
---

### Post by Koala Kid on 2011-09-16
Hello,
I have a simple Logitech headset + mic, once once the plug is jacked in, it doesn't switch the sound to the headset.
On pavucontrol, when I choose manually to stream on HDMI conroller, there's no sound.

here's my alsa-info script output:
[http://www.alsa-project.org/db/?f=2e6d2fde12342cfe0e586ee954a35d786fca6ffb](http://www.alsa-project.org/db/?f=2e6d2fde12342cfe0e586ee954a35d786fca6ffb)

here's aplay -L output while streaming on HDMI:

```
default
    Playback/recording through the PulseAudio sound server
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=Live,DEV=0
    SB Live! Value [CT4670], ADC Capture/Standard PCM Playback
    Front speakers
rear:CARD=Live,DEV=0
    SB Live! Value [CT4670], ADC Capture/Standard PCM Playback
    Rear speakers
center_lfe:CARD=Live,DEV=0
    SB Live! Value [CT4670], ADC Capture/Standard PCM Playback
    Center and Subwoofer speakers
surround40:CARD=Live,DEV=0
    SB Live! Value [CT4670], ADC Capture/Standard PCM Playback
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Live,DEV=0
    SB Live! Value [CT4670], ADC Capture/Standard PCM Playback
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Live,DEV=0
    SB Live! Value [CT4670], ADC Capture/Standard PCM Playback
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Live,DEV=0
    SB Live! Value [CT4670], ADC Capture/Standard PCM Playback
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
iec958:CARD=Live,DEV=0
    SB Live! Value [CT4670], Multichannel Capture/PT Playback
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=Live,DEV=0
    SB Live! Value [CT4670], ADC Capture/Standard PCM Playback
    Direct sample mixing device
dmix:CARD=Live,DEV=2
    SB Live! Value [CT4670], Multichannel Capture/PT Playback
    Direct sample mixing device
dmix:CARD=Live,DEV=3
    SB Live! Value [CT4670], Multichannel Playback
    Direct sample mixing device
dsnoop:CARD=Live,DEV=0
    SB Live! Value [CT4670], ADC Capture/Standard PCM Playback
    Direct sample snooping device
dsnoop:CARD=Live,DEV=2
    SB Live! Value [CT4670], Multichannel Capture/PT Playback
    Direct sample snooping device
dsnoop:CARD=Live,DEV=3
    SB Live! Value [CT4670], Multichannel Playback
    Direct sample snooping device
hw:CARD=Live,DEV=0
    SB Live! Value [CT4670], ADC Capture/Standard PCM Playback
    Direct hardware device without any conversions
hw:CARD=Live,DEV=2
    SB Live! Value [CT4670], Multichannel Capture/PT Playback
    Direct hardware device without any conversions
hw:CARD=Live,DEV=3
    SB Live! Value [CT4670], Multichannel Playback
    Direct hardware device without any conversions
plughw:CARD=Live,DEV=0
    SB Live! Value [CT4670], ADC Capture/Standard PCM Playback
    Hardware device with all software conversions
plughw:CARD=Live,DEV=2
    SB Live! Value [CT4670], Multichannel Capture/PT Playback
    Hardware device with all software conversions
plughw:CARD=Live,DEV=3
    SB Live! Value [CT4670], Multichannel Playback
    Hardware device with all software conversions
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, HDMI 0
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=1
    HDA NVidia, HDMI 0
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=2
    HDA NVidia, HDMI 0
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    HDMI Audio Output
dmix:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct sample mixing device
dmix:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 0
    Direct sample mixing device
dmix:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 0
    Direct sample mixing device
dmix:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 0
    Direct sample mixing device
dsnoop:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 0
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 0
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 0
    Direct sample snooping device
hw:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
plughw:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 0
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 0
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 0
    Hardware device with all software conversions

```

thanks in advance, any help would be appreciated.

KK.

---

### Post by Koala Kid on 2011-09-18
bump

---

### Post by lidex on 2011-09-18
How is this thing setup? Is the hdmi your primary output and you're plugging the headphone into the sb live?

---

### Post by Koala Kid on 2011-09-18
I don't understand much of this. SB live is my primary, basically after I plug the headphones, nothing changes, and after I switch manually to the HDMI, there's no sound.

---

### Post by Koala Kid on 2011-09-25
bump. anyone? please?

---

### Post by lidex on 2011-09-27
Have a look here:
[http://ubuntuforums.org/showthread.php?t=161817](http://ubuntuforums.org/showthread.php?t=161817)

---

