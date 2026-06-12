---
title: "LiveTV mute does not mute completely (alsa?)"
date: 2011-04-25
forum: Mythbuntu
---

### Post by blinnov.com on 2011-04-25
Hi,

I have 10.10 setup with auto-builds enabled. Since I moved to auto-builds, my mixer was behaving rather odd. I had myth frontend controlling PCM channel (master does not control anything), but it looks that the frontend cannot mute the sound completely.

I had alsamixer running in terminal and I noticed that when I press "mute", the frontend lowers the volume on the PCM channel to zero, but does not mute it. In my case, perhaps due to ALSA configuration, it does not silence the sound completely - I still can hear the TV. Quiet but annoying. Also, if I lower the volume to zero in the alsamixer, the outcome is the same. However, muting the PCM channel in the alsamixer cuts the sound completely.

It definitely worked better before I installed auto-builds.

I looked for any ideas about it and found plenty of threads about PCM/Master issue but found nothing on changing mixer limits.


Here is my alsa configuration:

```

upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Mon Apr 25 13:04:37 UTC 2011


!!Linux Distribution
!!------------------

Ubuntu 10.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.10"


!!DMI Information
!!---------------

Manufacturer:      Hewlett-Packard
Product Name:      HP Compaq dc7100 SFF(DX878AV)
Product Version:    


!!Kernel Information
!!------------------

Kernel release:    2.6.35-28-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.23
Library version:    1.0.23
Utilities version:  1.0.23


!!Loaded ALSA modules
!!-------------------

snd_intel8x0


!!Sound Servers on this system
!!----------------------------

No sound servers found.


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [ICH6           ]: ICH4 - Intel ICH6
                      Intel ICH6 with AD1981B at irq 21


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

00:1e.2 0401: 8086:266e (rev 03)
    Subsystem: 103c:3006


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-caiaq: index=-2
snd-usb-ua101: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-usb-audio: index=-2


!!Loaded sound module options
!!--------------------------

!!Module: snd_intel8x0
    ac97_clock : 0
    ac97_quirk : (null)
    buggy_irq : N
    buggy_semaphore : N
    enable : N
    id : (null)
    index : -1
    joystick : 0
    spdif_aclink : 0
    xbox : N


!!AC97 Codec information
!!---------------------------
--startcollapse--

0-0/0: Analog Devices AD1981B

PCI Subsys Vendor: 0x103c
PCI Subsys Device: 0x3006

Flags: 10
Capabilities     : -headphone out-
DAC resolution   : 20-bit
ADC resolution   : 16-bit
3D enhancement   : No 3D Stereo Enhancement

Current setup
Mic gain         : +0dB [+0dB]
POP path         : pre 3D
Sim. stereo      : off
3D enhancement   : off
Loudness         : off
Mono output      : MIX
Mic select       : Mic1
ADC/DAC loopback : off
Extended ID      : codec=0 rev=1 AMAP DSA=0 SPDIF VRA
Extended status  : SPCV SPDIF=3/4 VRA
PCM front DAC    : 48000Hz
PCM ADC          : 48000Hz
SPDIF Control    : Consumer PCM Category=0x2 Generation=1 Rate=48kHz



AD18XX configuration
Unchained        : 0x1000,0x0000,0x0000
Chained          : 0x0000,0x0000,0x0000

0:00 = 0090
0:02 = 1c1c
0:04 = 0e0f
0:06 = 001f
0:08 = 0000
0:0a = 0000
0:0c = 801f
0:0e = 801f
0:10 = 9898
0:12 = 0606
0:14 = 0000
0:16 = 1f1f
0:18 = 0c0c
0:1a = 0000
0:1c = 0000
0:1e = 0000
0:20 = 0000
0:22 = 0000
0:24 = 0000
0:26 = 000f
0:28 = 0605
0:2a = 0401
0:2c = bb80
0:2e = 0000
0:30 = 0000
0:32 = bb80
0:34 = 0000
0:36 = 0000
0:38 = 0000
0:3a = 2824
0:3c = 0000
0:3e = 0000
0:40 = 0000
0:42 = 0000
0:44 = 0000
0:46 = 0000
0:48 = 0000
0:4a = 0000
0:4c = 0000
0:4e = 0000
0:50 = 0000
0:52 = 0000
0:54 = 0000
0:56 = 0000
0:58 = 0000
0:5a = 0000
0:5c = 4000
0:5e = 0000
0:60 = 8080
0:62 = 0000
0:64 = 8000
0:66 = 0000
0:68 = 0000
0:6a = 0000
0:6c = 0000
0:6e = 0000
0:70 = 0000
0:72 = 0808
0:74 = 1001
0:76 = 2010
0:78 = 0000
0:7a = 0000
0:7c = 4144
0:7e = 5374
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116, 10 Apr 25 22:02 /dev/snd/controlC0
crw-rw----+ 1 root audio 116,  9 Apr 25 22:02 /dev/snd/pcmC0D0c
crw-rw----+ 1 root audio 116,  8 Apr 25 22:09 /dev/snd/pcmC0D0p
crw-rw----+ 1 root audio 116,  7 Apr 25 22:02 /dev/snd/pcmC0D1c
crw-rw----+ 1 root audio 116,  6 Apr 25 22:02 /dev/snd/pcmC0D2c
crw-rw----+ 1 root audio 116,  5 Apr 25 22:02 /dev/snd/pcmC0D3c
crw-rw----+ 1 root audio 116,  4 Apr 25 22:02 /dev/snd/pcmC0D4p
crw-rw----+ 1 root audio 116,  3 Apr 25 22:02 /dev/snd/seq
crw-rw----+ 1 root audio 116,  2 Apr 25 22:02 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Apr 25 22:02 .
drwxr-xr-x 3 root root 240 Apr 25 22:02 ..
lrwxrwxrwx 1 root root  12 Apr 25 22:02 pci-0000:00:1e.2 -> ../controlC0


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 1: Intel ICH - MIC ADC [Intel ICH6 - MIC ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 2: Intel ICH - MIC2 ADC [Intel ICH6 - MIC2 ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 3: Intel ICH - ADC2 [Intel ICH6 - ADC2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [ICH6]

Card hw:0 'ICH6'/'Intel ICH6 with AD1981B at irq 21'
  Mixer name    : 'Analog Devices AD1981B'
  Components    : 'AC97a:41445374'
  Controls      : 34
  Simple ctrls  : 23
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 3 [10%] [-42.00dB] [on]
  Front Right: Playback 3 [10%] [-42.00dB] [on]
Simple mixer control 'Master Mono',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-46.50dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 17 [55%] [-21.00dB] [on]
  Front Right: Playback 16 [52%] [-22.50dB] [on]
Simple mixer control 'Headphone Jack Sense',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 19 [61%] [-6.00dB] [on]
  Front Right: Playback 19 [61%] [-6.00dB] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 7 [23%] [-24.00dB] [off] Capture [off]
  Front Right: Playback 7 [23%] [-24.00dB] [off] Capture [off]
Simple mixer control 'Line Jack Sense',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 25 [81%] [3.00dB] [on] Capture [off]
  Front Right: Playback 25 [81%] [3.00dB] [on] Capture [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-34.50dB] [off]
  Front Left: Capture [on]
  Front Right: Capture [on]
Simple mixer control 'Mic Boost (+20dB)',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Mic Select',0
  Capabilities: enum
  Items: 'Mic1' 'Mic2'
  Item0: 'Mic1'
Simple mixer control 'Video',0
  Capabilities: cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Phone',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-34.50dB] [off]
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 Playback AC97-SPSA',0
  Capabilities: volume volume-joined penum
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 3
  Mono: 0 [0%]
Simple mixer control 'IEC958 Playback Source',0
  Capabilities: enum
  Items: 'AC-Link' 'A/D Converter'
  Item0: 'AC-Link'
Simple mixer control 'Aux',0
  Capabilities: pvolume pswitch cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [-34.50dB] [on] Capture [off]
  Front Right: Playback 0 [0%] [-34.50dB] [on] Capture [off]
Simple mixer control 'Mono Output Select',0
  Capabilities: enum
  Items: 'Mix' 'Mic'
  Item0: 'Mix'
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 0 [0%] [0.00dB] [on]
  Front Right: Capture 0 [0%] [0.00dB] [on]
Simple mixer control 'Mix',0
  Capabilities: cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Mix Mono',0
  Capabilities: cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'External Amplifier',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Stereo Mic',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]


!!Alsactl output
!!-------------

--startcollapse--
state.ICH6 {
    control.1 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Master Playback Switch'
        value.0 true
        value.1 true
    }
    control.2 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -4650
        comment.dbmax 0
        iface MIXER
        name 'Master Playback Volume'
        value.0 3
        value.1 3
    }
    control.3 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Headphone Playback Switch'
        value.0 true
        value.1 true
    }
    control.4 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -4650
        comment.dbmax 0
        iface MIXER
        name 'Headphone Playback Volume'
        value.0 17
        value.1 16
    }
    control.5 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Master Mono Playback Switch'
        value true
    }
    control.6 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 31'
        comment.dbmin -4650
        comment.dbmax 0
        iface MIXER
        name 'Master Mono Playback Volume'
        value 0
    }
    control.7 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Phone Playback Switch'
        value false
    }
    control.8 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'Phone Playback Volume'
        value 0
    }
    control.9 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Mic Playback Switch'
        value false
    }
    control.10 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'Mic Playback Volume'
        value 0
    }
    control.11 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Mic Boost (+20dB)'
        value false
    }
    control.12 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Line Playback Switch'
        value.0 false
        value.1 false
    }
    control.13 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'Line Playback Volume'
        value.0 7
        value.1 7
    }
    control.14 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'CD Playback Switch'
        value.0 true
        value.1 true
    }
    control.15 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'CD Playback Volume'
        value.0 25
        value.1 25
    }
    control.16 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Aux Playback Switch'
        value.0 true
        value.1 true
    }
    control.17 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'Aux Playback Volume'
        value.0 0
        value.1 0
    }
    control.18 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'PCM Playback Switch'
        value.0 true
        value.1 true
    }
    control.19 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'PCM Playback Volume'
        value.0 19
        value.1 19
    }
    control.20 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 2
        comment.item.0 Mic
        comment.item.1 CD
        comment.item.2 Video
        comment.item.3 Aux
        comment.item.4 Line
        comment.item.5 Mix
        comment.item.6 'Mix Mono'
        comment.item.7 Phone
        iface MIXER
        name 'Capture Source'
        value.0 Mic
        value.1 Mic
    }
    control.21 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Capture Switch'
        value.0 true
        value.1 true
    }
    control.22 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 15'
        comment.dbmin 0
        comment.dbmax 2250
        iface MIXER
        name 'Capture Volume'
        value.0 0
        value.1 0
    }
    control.23 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 1
        comment.item.0 Mix
        comment.item.1 Mic
        iface MIXER
        name 'Mono Output Select'
        value Mix
    }
    control.24 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 1
        comment.item.0 Mic1
        comment.item.1 Mic2
        iface MIXER
        name 'Mic Select'
        value Mic1
    }
    control.25 {
        comment.access read
        comment.type IEC958
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Con Mask'
        value '0fff000f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.26 {
        comment.access read
        comment.type IEC958
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Pro Mask'
        value cf00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
    }
    control.27 {
        comment.access 'read write'
        comment.type IEC958
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Default'
        value '0082000200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.28 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Switch'
        value false
    }
    control.29 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 3'
        iface MIXER
        name 'IEC958 Playback AC97-SPSA'
        value 0
    }
    control.30 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 1
        comment.item.0 AC-Link
        comment.item.1 'A/D Converter'
        iface MIXER
        name 'IEC958 Playback Source'
        value AC-Link
    }
    control.31 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Stereo Mic'
        value false
    }
    control.32 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Headphone Jack Sense'
        value true
    }
    control.33 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Line Jack Sense'
        value false
    }
    control.34 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'External Amplifier'
        value true
    }
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
nvidia
snd_intel8x0
snd_ac97_codec
ac97_bus
snd_pcm
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
snd_seq
mt2266
snd_timer
ir_lirc_codec
snd_seq_device
lirc_dev
dvb_usb_dib0700
intel_agp
ir_sony_decoder
dib7000p
snd
soundcore
snd_page_alloc
ppdev
ir_jvc_decoder
rc_rc6_mce
ir_rc6_decoder
dib0090
agpgart
parport_pc
lp
dib7000m
ir_rc5_decoder
dib0070
psmouse
ir_nec_decoder
parport
dvb_usb
mceusb
dib8000
dvb_core
dib3000mc
ir_core
dibx000_common
joydev
serio_raw
usbhid
hid
floppy
firewire_ohci
tg3
firewire_core
crc_itu_t


!!ALSA/HDA dmesg
!!------------------





```

---

### Post by blinnov.com on 2011-04-28
Actually, the problem was solved by installing and enabling PulseAudio.
Looks like its extra layer of mixing does the trick.

I only had to specify

```

load-module module-alsa-sink control=PCM

```

in /etc/pulse/default.pa file. This was to get rid of the volume "plateau" between 20-80% in the slider. In contrary to [this FAQ]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats#Volume%20range%20anomalies"), I did not have to set ignore_dB option for module-udev-detect though. When I tried, mute was not behaving properly.

---

