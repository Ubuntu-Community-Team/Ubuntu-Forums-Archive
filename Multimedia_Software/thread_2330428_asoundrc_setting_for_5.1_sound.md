---
title: "asoundrc setting for 5.1 sound"
date: 2016-07-11
forum: Multimedia Software
---

### Post by ajperezpulido on 2016-07-11
Hi, I would like to remap my 5.1 speakers in alsa from the .asoundrc, but I don't know well how it works. I have seen something like this in another old thread, but it doesn't work for me:
```
[COLOR=#000000][FONT=Ubuntu Mono]pcm.swap51 {[/FONT][/COLOR][COLOR=#000000]   @args.0 SLAVE
   @args.SLAVE {
               type string
               default "surround51"
   }
   type route
   slave {
         pcm $SLAVE
         channels 6
   }
   ttable {
     0.0= 1
     1.4= 1
     2.5= 1
     3.2= 1
     4.1= 1
     5.3= 1
   }
}

[/COLOR]
[COLOR=#000000][/COLOR]
```

This is my output for aplay -L:

```
[FONT=monospace][COLOR=#000000]null[/COLOR]
    Discard all samples (playback) or generate zero samples (capture)
pulse
    PulseAudio Sound Server
default:CARD=ALSA
    bcm2835 ALSA, bcm2835 ALSA
    Default Audio Device
sysdefault:CARD=ALSA
    bcm2835 ALSA, bcm2835 ALSA
    Default Audio Device
dmix:CARD=ALSA,DEV=0
    bcm2835 ALSA, bcm2835 ALSA
    Direct sample mixing device
dmix:CARD=ALSA,DEV=1
    bcm2835 ALSA, bcm2835 IEC958/HDMI
    Direct sample mixing device
dsnoop:CARD=ALSA,DEV=0
    bcm2835 ALSA, bcm2835 ALSA
    Direct sample snooping device
dsnoop:CARD=ALSA,DEV=1
    bcm2835 ALSA, bcm2835 IEC958/HDMI
    Direct sample snooping device
hw:CARD=ALSA,DEV=0
    bcm2835 ALSA, bcm2835 ALSA
    Direct hardware device without any conversions
hw:CARD=ALSA,DEV=1
    bcm2835 ALSA, bcm2835 IEC958/HDMI
    Direct hardware device without any conversions
plughw:CARD=ALSA,DEV=0
    bcm2835 ALSA, bcm2835 ALSA
    Hardware device with all software conversions
plughw:CARD=ALSA,DEV=1
    bcm2835 ALSA, bcm2835 IEC958/HDMI
    Hardware device with all software conversions
default:CARD=Device
    USB Sound Device, USB Audio
    Default Audio Device
sysdefault:CARD=Device
    USB Sound Device, USB Audio
    Default Audio Device
front:CARD=Device,DEV=0
    USB Sound Device, USB Audio
    Front speakers
surround21:CARD=Device,DEV=0
    USB Sound Device, USB Audio
    2.1 Surround output to Front and Subwoofer speakers
surround40:CARD=Device,DEV=0
    USB Sound Device, USB Audio
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Device,DEV=0
    USB Sound Device, USB Audio
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Device,DEV=0
    USB Sound Device, USB Audio
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Device,DEV=0
    USB Sound Device, USB Audio
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Device,DEV=0
    USB Sound Device, USB Audio
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Device,DEV=0
    USB Sound Device, USB Audio
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=Device,DEV=0
    USB Sound Device, USB Audio
    Direct sample mixing device
dsnoop:CARD=Device,DEV=0
    USB Sound Device, USB Audio
    Direct sample snooping device
hw:CARD=Device,DEV=0
    USB Sound Device, USB Audio
    Direct hardware device without any conversions
plughw:CARD=Device,DEV=0
    USB Sound Device, USB Audio
    Hardware device with all software conversions

[/FONT]
```

The only thing I need is swapping lfe and center channel. Please, can you help me? Thanks.

---

