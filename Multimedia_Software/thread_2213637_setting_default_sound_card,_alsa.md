---
title: "setting default sound card, alsa"
date: 2014-03-27
forum: Multimedia Software
---

### Post by blm14 on 2014-03-27
Running ubuntu 12.04 64-bit. Removed pulse because I hate it, and I play some games in wine and wine prefers ALSA.

I have a USB sound card, which the system recognizes. This is the output of aplay -L:

```

~$ aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    PulseAudio Sound Server
default:CARD=PCH
    HDA Intel PCH, ID 280 Analog
    Default Audio Device
sysdefault:CARD=PCH
    HDA Intel PCH, ID 280 Analog
    Default Audio Device
front:CARD=PCH,DEV=0
    HDA Intel PCH, ID 280 Analog
    Front speakers
surround40:CARD=PCH,DEV=0
    HDA Intel PCH, ID 280 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=PCH,DEV=0
    HDA Intel PCH, ID 280 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=PCH,DEV=0
    HDA Intel PCH, ID 280 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=PCH,DEV=0
    HDA Intel PCH, ID 280 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=PCH,DEV=0
    HDA Intel PCH, ID 280 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
dmix:CARD=PCH,DEV=0
    HDA Intel PCH, ID 280 Analog
    Direct sample mixing device
dsnoop:CARD=PCH,DEV=0
    HDA Intel PCH, ID 280 Analog
    Direct sample snooping device
hw:CARD=PCH,DEV=0
    HDA Intel PCH, ID 280 Analog
    Direct hardware device without any conversions
plughw:CARD=PCH,DEV=0
    HDA Intel PCH, ID 280 Analog
    Hardware device with all software conversions
default:CARD=Device
    C-Media USB Audio Device, USB Audio
    Default Audio Device
sysdefault:CARD=Device
    C-Media USB Audio Device, USB Audio
    Default Audio Device
front:CARD=Device,DEV=0
    C-Media USB Audio Device, USB Audio
    Front speakers
surround40:CARD=Device,DEV=0
    C-Media USB Audio Device, USB Audio
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Device,DEV=0
    C-Media USB Audio Device, USB Audio
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Device,DEV=0
    C-Media USB Audio Device, USB Audio
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Device,DEV=0
    C-Media USB Audio Device, USB Audio
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Device,DEV=0
    C-Media USB Audio Device, USB Audio
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Device,DEV=0
    C-Media USB Audio Device, USB Audio
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=Device,DEV=0
    C-Media USB Audio Device, USB Audio
    Direct sample mixing device
dsnoop:CARD=Device,DEV=0
    C-Media USB Audio Device, USB Audio
    Direct sample snooping device
hw:CARD=Device,DEV=0
    C-Media USB Audio Device, USB Audio
    Direct hardware device without any conversions
plughw:CARD=Device,DEV=0
    C-Media USB Audio Device, USB Audio
    Hardware device with all software conversions
default:CARD=Creative
    HDA Creative, CA0132 Analog
    Default Audio Device
sysdefault:CARD=Creative
    HDA Creative, CA0132 Analog
    Default Audio Device
front:CARD=Creative,DEV=0
    HDA Creative, CA0132 Analog
    Front speakers
surround40:CARD=Creative,DEV=0
    HDA Creative, CA0132 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Creative,DEV=0
    HDA Creative, CA0132 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Creative,DEV=0
    HDA Creative, CA0132 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Creative,DEV=0
    HDA Creative, CA0132 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Creative,DEV=0
    HDA Creative, CA0132 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Creative,DEV=0
    HDA Creative, CA0132 Digital
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=Creative,DEV=0
    HDA Creative, CA0132 Analog
    Direct sample mixing device
dmix:CARD=Creative,DEV=1
    HDA Creative, CA0132 Digital
    Direct sample mixing device
dsnoop:CARD=Creative,DEV=0
    HDA Creative, CA0132 Analog
    Direct sample snooping device
dsnoop:CARD=Creative,DEV=1
    HDA Creative, CA0132 Digital
    Direct sample snooping device
hw:CARD=Creative,DEV=0
    HDA Creative, CA0132 Analog
    Direct hardware device without any conversions
hw:CARD=Creative,DEV=1
    HDA Creative, CA0132 Digital
    Direct hardware device without any conversions
plughw:CARD=Creative,DEV=0
    HDA Creative, CA0132 Analog
    Hardware device with all software conversions
plughw:CARD=Creative,DEV=1
    HDA Creative, CA0132 Digital
    Hardware device with all software conversions
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, HDMI 0
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=1
    HDA NVidia, HDMI 1
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=2
    HDA NVidia, HDMI 2
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 3
    HDMI Audio Output
dmix:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct sample mixing device
dmix:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 1
    Direct sample mixing device
dmix:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 2
    Direct sample mixing device
dmix:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 3
    Direct sample mixing device
dsnoop:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 1
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 2
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 3
    Direct sample snooping device
hw:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 1
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 2
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 3
    Direct hardware device without any conversions
plughw:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 1
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 2
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 3
    Hardware device with all software conversions

```

What should my asound.conf file look like if I want the default ALSA device to be "C-Media USB Audio Device, USB Audio" ?

---

### Post by blm14 on 2014-03-27
aplay -l 

```

card 0: PCH [HDA Intel PCH], device 0: ID 280 Analog [ID 280 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: Device [C-Media USB Audio Device], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Creative [HDA Creative], device 0: CA0132 Analog [CA0132 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Creative [HDA Creative], device 1: CA0132 Digital [CA0132 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 3: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 3: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 3: NVidia [HDA NVidia], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 3: NVidia [HDA NVidia], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by Yellow Pasque on 2014-03-27
Rather than messing around with asound.conf, can't you just select the device you want with winecfg command?

---

### Post by blm14 on 2014-03-28
I want to do it for the whole O/S though, not just wine. Currently, ALSA defaults to the built-in sound card which I don't want to use.

---

### Post by Yellow Pasque on 2014-03-28
Since your default sound device uses a unique driver, it should be a simple matter of editing /etc/modprobe.d/alsa-base.conf
Change the following line to index=0
```
options snd-usb-audio index=-2
```

If you want, you can also remove this comment since it will no longer apply to you:
```
# Keep snd-usb-audio from being loaded as first soundcard
```

---

