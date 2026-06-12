---
title: "USB Headset is not working"
date: 2010-02-21
forum: Multimedia Software
---

### Post by vipin.balakrishnan on 2010-02-21
Hi All,

   Please help me on this issue. I  have asked to so many people in the forums to get a help on this nobody is giving a correct solution for this. Please help me on this.

 My problem is  USB Headset is not working properly in Ubuntu 8.04LTS. As soon as when I connect  USB Headset I can here Ubuntu Login Sound in USB Headset, But when try to play songs using any of the player like exaile or Rhythmbox not getting any sound. Instead I get sound in my speakers.

as soon as when I connect USB Headset I get in my System log  like this

```

Feb 21 17:33:56 Vipinb-desktop kernel: [16300.334584] usb 1-2: new full speed USB device using uhci_hcd and address 7
Feb 21 17:33:56 Vipinb-desktop kernel: [16300.537533] usb 1-2: configuration #1 chosen from 1 choice
Feb 21 17:33:56 Vipinb-desktop pulseaudio[10072]: alsa-util.c: Device front:2 doesn't support 44100 Hz, changed to 32000 Hz.
Feb 21 17:33:57 Vipinb-desktop pulseaudio[10072]: alsa-util.c: Device front:2 doesn't support 44100 Hz, changed to 32000 Hz.

```

While disconnecting USB Headset I will be getting System Log Like this

```

Feb 21 17:37:47 Vipinb-desktop kernel: [16532.047865] usb 1-2: USB disconnect, address 7

```

After Connecting the USB Headset Detail Config of my System

```


!!################################
!!ALSA Information Script v 0.4.59
!!################################

!!Script ran on: Sun Feb 21 12:14:07 UTC 2010


!!Linux Distribution
!!------------------

Ubuntu 8.04.4 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 8.04.4 LTS"


!!DMI Information
!!---------------

Manufacturer:                                      
Product Name:                                      


!!Kernel Information
!!------------------

Kernel release:    2.6.24-27-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.16
Library version:    1.0.16
Utilities version:  1.0.16


!!Loaded ALSA modules
!!-------------------

snd_ca0106
saa7134_alsa
snd_usb_audio


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [CA0106         ]: CA0106 - CA0106
                      Audigy SE [SB0570] at 0x1040 irq 19
 1 [SAA7134        ]: SAA7134 - SAA7134
                      saa7134[0] at 0xe3001000 irq 22
 2 [Headset        ]: USB-Audio - Logitech USB Headset
                      Logitech Logitech USB Headset at usb-0000:00:1d.0-2, full speed


!!PCI Soundcards installed in the system
!!--------------------------------------

05:01.0 Multimedia controller: Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder (rev 01)
05:03.0 Multimedia audio controller: Creative Labs SB Audigy LS


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

01:00.0 0300: 10de:0402 (rev a1) (prog-if 00 [VGA controller])
    Subsystem: 1682:2286
--
05:03.0 0401: 1102:0007
    Subsystem: 1102:100a


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-usx2y: index=-2
snd-usb-caiaq: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-usx2y: index=-2
snd-usb-caiaq: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388


!!Loaded sound module options
!!--------------------------

!!Module: snd_ca0106
    enable : Y,Y,Y,Y,Y,Y,Y,Y
    id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
    index : -1,-1,-1,-1,-1,-1,-1,-1
    subsystem : 0,0,0,0,0,0,0,0

!!Module: saa7134_alsa
    debug : 0
    enable : 1,1,1,1,1,1,1,1
    index : -2,-1,-1,-1,-1,-1,-1,-1

!!Module: snd_usb_audio
    async_unlink : Y
    device_setup : 0,0,0,0,0,0,0,0
    enable : Y,Y,Y,Y,Y,Y,Y,Y
    id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
    index : -2,-1,-1,-1,-1,-1,-1,-1
    nrpacks : 8
    pid : -1,-1,-1,-1,-1,-1,-1,-1
    vid : -1,-1,-1,-1,-1,-1,-1,-1


!!ALSA Device nodes
!!-----------------

crw-rw----  1 root audio 116,  0 Feb 21 13:02 /dev/snd/controlC0
crw-rw----  1 root audio 116, 32 Feb 21 13:02 /dev/snd/controlC1
crw-rw----  1 root audio 116, 64 Feb 21 17:39 /dev/snd/controlC2
crw-rw----  1 root audio 116,  8 Feb 21 13:02 /dev/snd/midiC0D0
crw-rw----  1 root audio 116, 24 Feb 21 17:14 /dev/snd/pcmC0D0c
crw-rw----  1 root audio 116, 16 Feb 21 17:40 /dev/snd/pcmC0D0p
crw-rw----  1 root audio 116, 25 Feb 21 13:02 /dev/snd/pcmC0D1c
crw-rw----  1 root audio 116, 17 Feb 21 17:40 /dev/snd/pcmC0D1p
crw-rw----  1 root audio 116, 26 Feb 21 13:02 /dev/snd/pcmC0D2c
crw-rw----  1 root audio 116, 18 Feb 21 13:02 /dev/snd/pcmC0D2p
crw-rw----  1 root audio 116, 27 Feb 21 13:02 /dev/snd/pcmC0D3c
crw-rw----  1 root audio 116, 19 Feb 21 13:02 /dev/snd/pcmC0D3p
crw-rw----  1 root audio 116, 56 Feb 21 16:31 /dev/snd/pcmC1D0c
crw-rw----  1 root audio 116, 88 Feb 21 17:39 /dev/snd/pcmC2D0c
crw-rw----  1 root audio 116, 80 Feb 21 17:39 /dev/snd/pcmC2D0p
crw-rw----  1 root audio 116,  1 Feb 21 13:02 /dev/snd/seq
crw-rw----  1 root audio 116, 33 Feb 21 13:02 /dev/snd/timer


!!ALSA configuration files
!!------------------------

!!System wide config file (/etc/asound.conf)

pcm.pulse {
    type pulse
}

ctl.pulse {
    type pulse
}

pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}



!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Headset [Logitech USB Headset], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: SAA7134 [SAA7134], device 0: SAA7134 PCM [SAA7134 PCM]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Headset [Logitech USB Headset], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [CA0106]

Card hw:0 'CA0106'/'Audigy SE [SB0570] at 0x1040 irq 19'
  Mixer name    : ''
  Components    : ''
  Controls      : 29
  Simple ctrls  : 17
Simple mixer control 'Line in',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 255
  Front Left: Capture 137 [54%] [-35.00dB]
  Front Right: Capture 137 [54%] [-35.00dB]
Simple mixer control 'Mic',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 255
  Front Left: Capture 137 [54%] [-35.00dB]
  Front Right: Capture 133 [52%] [-37.00dB]
Simple mixer control 'Phone',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 255
  Front Left: Capture 137 [54%] [-35.00dB]
  Front Right: Capture 137 [54%] [-35.00dB]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 Center/LFE',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 137 [54%] [-17.50dB]
  Front Right: Playback 137 [54%] [-17.50dB]
Simple mixer control 'IEC958 Front',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 137 [54%] [-17.50dB]
  Front Right: Playback 133 [52%] [-18.50dB]
Simple mixer control 'IEC958 Rear',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 137 [54%] [-17.50dB]
  Front Right: Playback 137 [54%] [-17.50dB]
Simple mixer control 'IEC958 Unknown',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 137 [54%] [-17.50dB]
  Front Right: Playback 137 [54%] [-17.50dB]
Simple mixer control 'Aux',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 255
  Front Left: Capture 0 [0%] [-99999.99dB]
  Front Right: Capture 0 [0%] [-99999.99dB]
Simple mixer control 'Analog Center/LFE',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 137 [54%] [-17.50dB] [on]
  Front Right: Playback 137 [54%] [-17.50dB] [on]
Simple mixer control 'Analog Front',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 137 [54%] [-17.50dB] [on]
  Front Right: Playback 137 [54%] [-17.50dB] [on]
Simple mixer control 'Analog Rear',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 137 [54%] [-17.50dB] [on]
  Front Right: Playback 137 [54%] [-17.50dB] [on]
Simple mixer control 'Analog Side',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 137 [54%] [-17.50dB] [on]
  Front Right: Playback 137 [54%] [-17.50dB] [on]
Simple mixer control 'Analog Source',0
  Capabilities: cenum
  Items: 'Phone' 'Mic' 'Line in' 'Aux'
  Item0: 'Line in'
Simple mixer control 'CAPTURE feedback',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 137 [54%] [-17.50dB]
  Front Right: Playback 137 [54%] [-17.50dB]
Simple mixer control 'Digital Source',0
  Capabilities: cenum
  Items: 'IEC958 out' 'i2s mixer out' 'IEC958 in' 'i2s in' 'AC97 in' 'SRC out'
  Item0: 'i2s in'
Simple mixer control 'Shared Mic/Line in',0
  Capabilities: cenum
  Items: 'Line in' 'Mic in'
  Item0: 'Line in'

!!-------Mixer controls for card 1 [SAA7134]

Card hw:1 'SAA7134'/'saa7134[0] at 0xe3001000 irq 22'
  Mixer name    : 'SAA7134 Mixer'
  Components    : ''
  Controls      : 6
  Simple ctrls  : 3
Simple mixer control 'Line',1
  Capabilities: volume cswitch
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 20
  Front Left: 18 [90%] Capture [on]
  Front Right: 18 [90%] Capture [on]
Simple mixer control 'Line',2
  Capabilities: volume cswitch
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 20
  Front Left: 18 [90%] Capture [on]
  Front Right: 18 [90%] Capture [on]
Simple mixer control 'Video',0
  Capabilities: volume cswitch
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 20
  Front Left: 20 [100%] Capture [on]
  Front Right: 20 [100%] Capture [on]

!!-------Mixer controls for card 2 [Headset]

Card hw:2 'Headset'/'Logitech Logitech USB Headset at usb-0000:00:1d.0-2, full speed'
  Mixer name    : 'USB Mixer'
  Components    : 'USB046d:0a14'
  Controls      : 4
  Simple ctrls  : 2
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 30
  Mono:
  Front Left: Playback 30 [100%] [0.00dB] [on]
  Front Right: Playback 30 [100%] [0.00dB] [on]
Simple mixer control 'Mic',0
  Capabilities: cvolume cswitch cswitch-joined
  Capture channels: Mono
  Limits: Capture 0 - 40
  Mono: Capture 0 [0%] [0.00dB] [off]


!!Alsactl output
!!-------------

--startcollapse--
state.CA0106 {
    control.1 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 255'
        comment.dbmin -5175
        comment.dbmax 1200
        iface MIXER
        name 'Analog Front Playback Volume'
        value.0 137
        value.1 137
    }
    control.2 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 255'
        comment.dbmin -5175
        comment.dbmax 1200
        iface MIXER
        name 'Analog Rear Playback Volume'
        value.0 137
        value.1 137
    }
    control.3 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 255'
        comment.dbmin -5175
        comment.dbmax 1200
        iface MIXER
        name 'Analog Center/LFE Playback Volume'
        value.0 137
        value.1 137
    }
    control.4 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 255'
        comment.dbmin -5175
        comment.dbmax 1200
        iface MIXER
        name 'Analog Side Playback Volume'
        value.0 137
        value.1 137
    }
    control.5 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 255'
        comment.dbmin -5175
        comment.dbmax 1200
        iface MIXER
        name 'IEC958 Front Playback Volume'
        value.0 137
        value.1 133
    }
    control.6 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 255'
        comment.dbmin -5175
        comment.dbmax 1200
        iface MIXER
        name 'IEC958 Rear Playback Volume'
        value.0 137
        value.1 137
    }
    control.7 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 255'
        comment.dbmin -5175
        comment.dbmax 1200
        iface MIXER
        name 'IEC958 Center/LFE Playback Volume'
        value.0 137
        value.1 137
    }
    control.8 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 255'
        comment.dbmin -5175
        comment.dbmax 1200
        iface MIXER
        name 'IEC958 Unknown Playback Volume'
        value.0 137
        value.1 137
    }
    control.9 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 255'
        comment.dbmin -5175
        comment.dbmax 1200
        iface MIXER
        name 'CAPTURE feedback Playback Volume'
        value.0 137
        value.1 137
    }
    control.10 {
        comment.access read
        comment.type IEC958
        comment.count 1
        iface PCM
        name 'IEC958 Playback Mask'
        value ffffffff00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
    }
    control.11 {
        comment.access read
        comment.type IEC958
        comment.count 1
        iface PCM
        name 'IEC958 Playback Mask'
        index 1
        value ffffffff00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
    }
    control.12 {
        comment.access read
        comment.type IEC958
        comment.count 1
        iface PCM
        name 'IEC958 Playback Mask'
        index 2
        value ffffffff00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
    }
    control.13 {
        comment.access read
        comment.type IEC958
        comment.count 1
        iface PCM
        name 'IEC958 Playback Mask'
        index 3
        value ffffffff00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
    }
    control.14 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Switch'
        value false
    }
    control.15 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 1
        comment.item.0 'IEC958 out'
        comment.item.1 'i2s mixer out'
        comment.item.2 'IEC958 in'
        comment.item.3 'i2s in'
        comment.item.4 'AC97 in'
        comment.item.5 'SRC out'
        iface MIXER
        name 'Digital Source Capture Enum'
        value 'i2s in'
    }
    control.16 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 1
        comment.item.0 Phone
        comment.item.1 Mic
        comment.item.2 'Line in'
        comment.item.3 Aux
        iface MIXER
        name 'Analog Source Capture Enum'
        value 'Line in'
    }
    control.17 {
        comment.access 'read write'
        comment.type IEC958
        comment.count 1
        iface PCM
        name 'IEC958 Playback Default'
        value '0492100200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.18 {
        comment.access 'read write'
        comment.type IEC958
        comment.count 1
        iface PCM
        name 'IEC958 Playback Default'
        index 1
        value '0492100200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.19 {
        comment.access 'read write'
        comment.type IEC958
        comment.count 1
        iface PCM
        name 'IEC958 Playback Default'
        index 2
        value '0492100200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.20 {
        comment.access 'read write'
        comment.type IEC958
        comment.count 1
        iface PCM
        name 'IEC958 Playback Default'
        index 3
        value '0492100200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.21 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 255'
        comment.dbmin -10350
        comment.dbmax 2400
        iface MIXER
        name 'Phone Capture Volume'
        value.0 137
        value.1 137
    }
    control.22 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 255'
        comment.dbmin -10350
        comment.dbmax 2400
        iface MIXER
        name 'Mic Capture Volume'
        value.0 137
        value.1 133
    }
    control.23 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 255'
        comment.dbmin -10350
        comment.dbmax 2400
        iface MIXER
        name 'Line in Capture Volume'
        value.0 137
        value.1 137
    }
    control.24 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 255'
        comment.dbmin -10350
        comment.dbmax 2400
        iface MIXER
        name 'Aux Capture Volume'
        value.0 0
        value.1 0
    }
    control.25 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 1
        comment.item.0 'Line in'
        comment.item.1 'Mic in'
        iface MIXER
        name 'Shared Mic/Line in Capture Switch'
        value 'Line in'
    }
    control.26 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Analog Front Playback Switch'
        value true
    }
    control.27 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Analog Rear Playback Switch'
        value true
    }
    control.28 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Analog Center/LFE Playback Switch'
        value true
    }
    control.29 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Analog Side Playback Switch'
        value true
    }
}
state.SAA7134 {
    control.1 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 20'
        iface MIXER
        name 'Video Volume'
        value.0 20
        value.1 20
    }
    control.2 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Video Capture Switch'
        value.0 true
        value.1 true
    }
    control.3 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 20'
        iface MIXER
        name 'Line Volume'
        index 1
        value.0 18
        value.1 18
    }
    control.4 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Line Capture Switch'
        index 1
        value.0 true
        value.1 true
    }
    control.5 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 20'
        iface MIXER
        name 'Line Volume'
        index 2
        value.0 18
        value.1 18
    }
    control.6 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Line Capture Switch'
        index 2
        value.0 true
        value.1 true
    }
}
state.Headset {
    control.1 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'PCM Playback Switch'
        value true
    }
    control.2 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 30'
        comment.dbmin -3000
        comment.dbmax 0
        iface MIXER
        name 'PCM Playback Volume'
        value.0 30
        value.1 30
    }
    control.3 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Mic Capture Switch'
        value false
    }
    control.4 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 40'
        comment.dbmin 0
        comment.dbmax 4000
        iface MIXER
        name 'Mic Capture Volume'
        value 0
    }
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
snd_usb_audio
snd_usb_lib
snd_hwdep
binfmt_misc
af_packet
rfcomm
l2cap
bluetooth
vboxnetadp
vboxnetflt
vboxdrv
ppdev
ipv6
acpi_cpufreq
cpufreq_ondemand
cpufreq_stats
freq_table
cpufreq_conservative
cpufreq_userspace
cpufreq_powersave
dock
container
sbs
sbshc
video
output
battery
iptable_filter
ip_tables
x_tables
ac
lm85
hwmon_vid
i2c_i801
lp
snd_ca0106
saa7134_alsa
snd_ac97_codec
snd_pcm_oss
snd_mixer_oss
snd_pcm
snd_seq_dummy
snd_seq_oss
snd_seq_midi
snd_rawmidi
tuner
tea5767
tda8290
tuner_simple
mt20xx
tea5761
snd_seq_midi_event
snd_seq
saa7134
snd_timer
snd_seq_device
nvidia
compat_ioctl32
videobuf_dma_sg
videobuf_core
ir_kbd_i2c
serio_raw
snd
ir_common
button
i2c_core
soundcore
videodev
psmouse
ac97_bus
v4l2_common
v4l1_compat
snd_page_alloc
intel_agp
agpgart
iTCO_wdt
iTCO_vendor_support
evdev
parport_pc
parport
shpchp
pci_hotplug
pcspkr
ext3
jbd
mbcache
sg
usbhid
hid
sr_mod
cdrom
sd_mod
ata_generic
ata_piix
pata_acpi
ehci_hcd
e100
mii
libata
scsi_mod
uhci_hcd
usbcore
thermal
processor
fan
fbcon
tileblit
font
bitblit
softcursor
fuse


!!ALSA/HDA dmesg
!!------------------

[   39.820280] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
[   40.020091] saa7134 ALSA driver for DMA sound loaded
[   40.020129] saa7134[0]/alsa: saa7134[0] at 0xe3001000 irq 22 registered as card -2


```

---

### Post by vipin.balakrishnan on 2010-02-21
Hi 

 Very much Feeling bad about the support given here. Nobody is knowing about the question I asked

Just thinking should I go with ubuntu or not. Because from past 4 month I'm askng about the same problem nobody is there to help me

---

