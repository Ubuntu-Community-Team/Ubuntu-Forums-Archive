---
title: "getting coaxial digital audio output working in 12.04 with realtek alc850 rev 0"
date: 2014-03-10
forum: Multimedia Software
---

### Post by pyrates on 2014-03-10
I have a 64-bit minimal install of ubuntu 12.04 installed.  I've got alsa installed, but not pulse.  I followed the instructions here for installing the daily version of alsa kernel drivers:

[https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

I have ran alsamixer and unmuted all 3 iec958 and left the one with volume control at 0.

I added this to /etc/modprobe.d/alsa-base.conf

```
options snd-hda-intel model=6stack-dig
```

And then reloaded alsa:

# sudo reload alsa

This is the output with aplay -l

```
# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

And this is the output with aplay -L

```
# aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=CK804
    NVidia CK804, NVidia CK804
    Default Audio Device
sysdefault:CARD=CK804
    NVidia CK804, NVidia CK804
    Default Audio Device
front:CARD=CK804,DEV=0
    NVidia CK804, NVidia CK804
    Front speakers
surround40:CARD=CK804,DEV=0
    NVidia CK804, NVidia CK804
    4.0 Surround output to Front and Rear speakers
surround41:CARD=CK804,DEV=0
    NVidia CK804, NVidia CK804
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=CK804,DEV=0
    NVidia CK804, NVidia CK804
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=CK804,DEV=0
    NVidia CK804, NVidia CK804
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=CK804,DEV=0
    NVidia CK804, NVidia CK804
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=CK804,DEV=0
    NVidia CK804, NVidia CK804 - IEC958
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=CK804,DEV=0
    NVidia CK804, NVidia CK804
    Direct sample mixing device
dmix:CARD=CK804,DEV=2
    NVidia CK804, NVidia CK804 - IEC958
    Direct sample mixing device
dsnoop:CARD=CK804,DEV=0
    NVidia CK804, NVidia CK804
    Direct sample snooping device
dsnoop:CARD=CK804,DEV=2
    NVidia CK804, NVidia CK804 - IEC958
    Direct sample snooping device
hw:CARD=CK804,DEV=0
    NVidia CK804, NVidia CK804
    Direct hardware device without any conversions
hw:CARD=CK804,DEV=2
    NVidia CK804, NVidia CK804 - IEC958
    Direct hardware device without any conversions
plughw:CARD=CK804,DEV=0
    NVidia CK804, NVidia CK804
    Hardware device with all software conversions
plughw:CARD=CK804,DEV=2
    NVidia CK804, NVidia CK804 - IEC958
    Hardware device with all software conversions
```

But when I run this command to test the speaker output, there is no audio:

# speaker-test -D iec958 -c 2 -t wav

here is the output from ./alsa-info.sh --stdout

```

upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.63
!!################################

!!Script ran on: Mon Mar 10 07:24:20 UTC 2014


!!Linux Distribution
!!------------------

Ubuntu 12.04.4 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 12.04.4 LTS" NAME="Ubuntu" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu precise (12.04.4 LTS)"


!!DMI Information
!!---------------

Manufacturer:      System manufacturer
Product Name:      System Product Name
Product Version:   System Version
Firmware Version:  ASUS A8N-SLI Premium ACPI BIOS Revision 1303


!!Kernel Information
!!------------------

Kernel release:    3.2.0-60-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         x86_64
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.25
Library version:    1.0.25
Utilities version:  1.0.25


!!Loaded ALSA modules
!!-------------------

snd_intel8x0
snd_mpu401


!!Sound Servers on this system
!!----------------------------

No sound servers found.


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [CK804          ]: NFORCE - NVidia CK804
                      NVidia CK804 with ALC850 at irq 22
 1 [UART           ]: MPU-401 UART - MPU-401 UART
                      MPU-401 UART at 0x330, irq 10


!!PCI Soundcards installed in the system
!!--------------------------------------

00:04.0 Multimedia audio controller: NVIDIA Corporation CK804 AC'97 Audio Controller (rev a2)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!-------------------------------------------------------

00:04.0 0401: 10de:0059 (rev a2)
	Subsystem: 1043:812a


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
snd-hda-intel: model=6stack-dig


!!Loaded sound module options
!!---------------------------

!!Module: snd_intel8x0
	ac97_clock : 0
	ac97_quirk : (null)
	buggy_irq : Y
	buggy_semaphore : N
	enable : N
	id : (null)
	index : -1
	inside_vm : Y
	joystick : 0
	spdif_aclink : 0
	xbox : N

!!Module: snd_mpu401
	enable : Y,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N
	id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	index : -2,-2,-2,-2,-2,-2,-2,-2,-2,-2,-2,-2,-2,-2,-2,-2,-2,-2,-2,-2,-2,-2,-2,-2,-2,-2,-2,-2,-2,-2,-2,-2
	irq : 10,65535,65535,65535,65535,65535,65535,65535,65535,65535,65535,65535,65535,65535,65535,65535,65535,65535,65535,65535,65535,65535,65535,65535,65535,65535,65535,65535,65535,65535,65535,65535
	pnp : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	port : 816,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1
	uart_enter : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y


!!AC97 Codec information
!!----------------------
--startcollapse--

0-0/0: Realtek ALC850 rev 0

PCI Subsys Vendor: 0x1043
PCI Subsys Device: 0x812a

Flags: 80020
Revision         : 0x00
Compat. Class    : 0x00
Subsys. Vendor ID: 0xffff
Subsys. ID       : 0xffff

Capabilities     :
DAC resolution   : 16-bit
ADC resolution   : 16-bit
3D enhancement   : No 3D Stereo Enhancement

Current setup
Mic gain         : +20dB [+20dB]
POP path         : pre 3D
Sim. stereo      : off
3D enhancement   : off
Loudness         : off
Mono output      : Mic
Mic select       : Mic1
ADC/DAC loopback : off
Double rate slots: 7/8
Extended ID      : codec=0 rev=2 LDAC SDAC CDAC DSA=0 SPDIF DRA
Extended status  : SPCV LDAC SDAC CDAC SPDIF=3/4 SPDIF
SPDIF Control    : Consumer PCM Copyright Category=0x2 Generation=1 Rate=48kHz

0:00 = 0000
0:02 = 0000
0:04 = 0000
0:06 = 0000
0:08 = 0000
0:0a = 0000
0:0c = 0000
0:0e = 0040
0:10 = 0000
0:12 = 0000
0:14 = 0000
0:16 = 0000
0:18 = 0000
0:1a = 0000
0:1c = 0808
0:1e = 0000
0:20 = 0600
0:22 = 0000
0:24 = 0000
0:26 = 000f
0:28 = 09c6
0:2a = 05c4
0:2c = bb80
0:2e = bb80
0:30 = bb80
0:32 = bb80
0:34 = 0000
0:36 = 0000
0:38 = 0000
0:3a = 2820
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
0:5c = 0000
0:5e = 0000
0:60 = 0000
0:62 = 0000
0:64 = 0808
0:66 = 0808
0:68 = 0a0a
0:6a = 8401
0:6c = 0000
0:6e = 0017
0:70 = c5a0
0:72 = 00c0
0:74 = 8388
0:76 = 2ad0
0:78 = 108e
0:7a = 10e2
0:7c = 414c
0:7e = 4790
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw---T+ 1 root audio 116,  6 Mar 10 00:08 /dev/snd/controlC0
crw-rw---T+ 1 root audio 116,  8 Mar 10 00:08 /dev/snd/controlC1
crw-rw---T+ 1 root audio 116,  7 Mar 10 00:08 /dev/snd/midiC1D0
crw-rw---T+ 1 root audio 116,  5 Mar 10 00:08 /dev/snd/pcmC0D0c
crw-rw---T+ 1 root audio 116,  4 Mar 10 00:08 /dev/snd/pcmC0D0p
crw-rw---T+ 1 root audio 116,  3 Mar 10 00:08 /dev/snd/pcmC0D1c
crw-rw---T+ 1 root audio 116,  2 Mar 10 00:09 /dev/snd/pcmC0D2p
crw-rw---T+ 1 root audio 116,  1 Mar 10 00:08 /dev/snd/seq
crw-rw---T+ 1 root audio 116, 33 Mar 10 00:08 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Mar 10 00:08 .
drwxr-xr-x 3 root root 240 Mar 10 00:08 ..
lrwxrwxrwx 1 root root  12 Mar 10 00:08 pci-0000:00:04.0 -> ../controlC0


!!Aplay/Arecord output
!!--------------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 1: Intel ICH - MIC ADC [NVidia CK804 - MIC ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [CK804]

Card hw:0 'CK804'/'NVidia CK804 with ALC850 at irq 22'
  Mixer name	: 'Realtek ALC850 rev 0'
  Components	: 'AC97a:414c4790'
  Controls      : 42
  Simple ctrls  : 27
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Master Mono',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [12.00dB] [on]
  Front Right: Playback 31 [100%] [12.00dB] [on]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Surround Jack Mode',0
  Capabilities: enum
  Items: 'Shared' 'Independent'
  Item0: 'Shared'
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 31 [100%] [12.00dB] [on] Capture [off]
  Front Right: Playback 31 [100%] [12.00dB] [on] Capture [off]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 31 [100%] [12.00dB] [on] Capture [off]
  Front Right: Playback 31 [100%] [12.00dB] [on] Capture [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [12.00dB] [on]
  Front Left: Capture [on]
  Front Right: Capture [on]
Simple mixer control 'Mic Boost (+20dB)',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Mic Front Input',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
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
  Mono: Playback 31 [100%] [12.00dB] [on]
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined cswitch cswitch-joined penum
  Playback channels: Mono
  Capture channels: Mono
  Mono: Playback [on] Capture [off]
Simple mixer control 'IEC958 Playback AC97-SPSA',0
  Capabilities: volume volume-joined penum
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 3
  Mono: 0 [0%]
Simple mixer control 'IEC958 Playback Source',0
  Capabilities: enum
  Items: 'PCM' 'Analog In' 'IEC958 In'
  Item0: 'PCM'
Simple mixer control 'Beep',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 15
  Mono: Playback 15 [100%] [0.00dB] [on]
Simple mixer control 'Aux',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 31 [100%] [12.00dB] [on] Capture [off]
  Front Right: Playback 31 [100%] [12.00dB] [on] Capture [off]
Simple mixer control 'Mono Output Select',0
  Capabilities: enum
  Items: 'Mix' 'Mic'
  Item0: 'Mic'
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch cswitch-joined penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 8 [53%] [12.00dB] [on]
  Front Right: Capture 8 [53%] [12.00dB] [on]
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
Simple mixer control 'Channel Mode',0
  Capabilities: enum
  Items: '2ch' '4ch' '6ch' '8ch'
  Item0: '6ch'
Simple mixer control 'Duplicate Front',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'External Amplifier',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]

!!-------Mixer controls for card 1 [UART]

Card hw:1 'UART'/'MPU-401 UART at 0x330, irq 10'
  Mixer name	: ''
  Components	: ''
  Controls      : 0
  Simple ctrls  : 0


!!Alsactl output
!!--------------

--startcollapse--
state.CK804 {
	control.1 {
		iface MIXER
		name 'Master Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.2 {
		iface MIXER
		name 'Master Playback Volume'
		value.0 31
		value.1 31
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 31'
			dbmin -4650
			dbmax 0
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.3 {
		iface MIXER
		name 'Center Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.4 {
		iface MIXER
		name 'Center Playback Volume'
		value 31
		comment {
			access 'read write'
			type INTEGER
			count 1
			range '0 - 31'
			dbmin -4650
			dbmax 0
			dbvalue.0 0
		}
	}
	control.5 {
		iface MIXER
		name 'LFE Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.6 {
		iface MIXER
		name 'LFE Playback Volume'
		value 31
		comment {
			access 'read write'
			type INTEGER
			count 1
			range '0 - 31'
			dbmin -4650
			dbmax 0
			dbvalue.0 0
		}
	}
	control.7 {
		iface MIXER
		name 'Surround Playback Switch'
		value.0 true
		value.1 true
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.8 {
		iface MIXER
		name 'Surround Playback Volume'
		value.0 31
		value.1 31
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 31'
			dbmin -4650
			dbmax 0
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.9 {
		iface MIXER
		name 'Master Mono Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.10 {
		iface MIXER
		name 'Master Mono Playback Volume'
		value 31
		comment {
			access 'read write'
			type INTEGER
			count 1
			range '0 - 31'
			dbmin -4650
			dbmax 0
			dbvalue.0 0
		}
	}
	control.11 {
		iface MIXER
		name 'Beep Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.12 {
		iface MIXER
		name 'Beep Playback Volume'
		value 15
		comment {
			access 'read write'
			type INTEGER
			count 1
			range '0 - 15'
			dbmin -4500
			dbmax 0
			dbvalue.0 0
		}
	}
	control.13 {
		iface MIXER
		name 'Phone Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.14 {
		iface MIXER
		name 'Phone Playback Volume'
		value 31
		comment {
			access 'read write'
			type INTEGER
			count 1
			range '0 - 31'
			dbmin -3450
			dbmax 1200
			dbvalue.0 1200
		}
	}
	control.15 {
		iface MIXER
		name 'Mic Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.16 {
		iface MIXER
		name 'Mic Playback Volume'
		value 31
		comment {
			access 'read write'
			type INTEGER
			count 1
			range '0 - 31'
			dbmin -3450
			dbmax 1200
			dbvalue.0 1200
		}
	}
	control.17 {
		iface MIXER
		name 'Mic Boost (+20dB)'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.18 {
		iface MIXER
		name 'Line Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.19 {
		iface MIXER
		name 'Line Playback Volume'
		value.0 31
		value.1 31
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 31'
			dbmin -3450
			dbmax 1200
			dbvalue.0 1200
			dbvalue.1 1200
		}
	}
	control.20 {
		iface MIXER
		name 'CD Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.21 {
		iface MIXER
		name 'CD Playback Volume'
		value.0 31
		value.1 31
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 31'
			dbmin -3450
			dbmax 1200
			dbvalue.0 1200
			dbvalue.1 1200
		}
	}
	control.22 {
		iface MIXER
		name 'Aux Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.23 {
		iface MIXER
		name 'Aux Playback Volume'
		value.0 31
		value.1 31
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 31'
			dbmin -3450
			dbmax 1200
			dbvalue.0 1200
			dbvalue.1 1200
		}
	}
	control.24 {
		iface MIXER
		name 'PCM Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.25 {
		iface MIXER
		name 'PCM Playback Volume'
		value.0 31
		value.1 31
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 31'
			dbmin -3450
			dbmax 1200
			dbvalue.0 1200
			dbvalue.1 1200
		}
	}
	control.26 {
		iface MIXER
		name 'Capture Source'
		value.0 Mic
		value.1 Mic
		comment {
			access 'read write'
			type ENUMERATED
			count 2
			item.0 Mic
			item.1 CD
			item.2 Video
			item.3 Aux
			item.4 Line
			item.5 Mix
			item.6 'Mix Mono'
			item.7 Phone
		}
	}
	control.27 {
		iface MIXER
		name 'Capture Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.28 {
		iface MIXER
		name 'Capture Volume'
		value.0 8
		value.1 8
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 15'
			dbmin 0
			dbmax 2250
			dbvalue.0 1200
			dbvalue.1 1200
		}
	}
	control.29 {
		iface MIXER
		name 'Mono Output Select'
		value Mic
		comment {
			access 'read write'
			type ENUMERATED
			count 1
			item.0 Mix
			item.1 Mic
		}
	}
	control.30 {
		iface MIXER
		name 'Mic Select'
		value Mic1
		comment {
			access 'read write'
			type ENUMERATED
			count 1
			item.0 Mic1
			item.1 Mic2
		}
	}
	control.31 {
		iface MIXER
		name 'IEC958 Playback Con Mask'
		value '0fff000f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.32 {
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		value cf00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.33 {
		iface MIXER
		name 'IEC958 Playback Default'
		value '0482000200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access 'read write'
			type IEC958
			count 1
		}
	}
	control.34 {
		iface MIXER
		name 'IEC958 Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.35 {
		iface MIXER
		name 'IEC958 Playback AC97-SPSA'
		value 0
		comment {
			access 'read write'
			type INTEGER
			count 1
			range '0 - 3'
		}
	}
	control.36 {
		iface MIXER
		name 'Duplicate Front'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.37 {
		iface MIXER
		name 'Mic Front Input Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.38 {
		iface MIXER
		name 'Surround Jack Mode'
		value Shared
		comment {
			access 'read write'
			type ENUMERATED
			count 1
			item.0 Shared
			item.1 Independent
		}
	}
	control.39 {
		iface MIXER
		name 'Channel Mode'
		value '6ch'
		comment {
			access 'read write'
			type ENUMERATED
			count 1
			item.0 '2ch'
			item.1 '4ch'
			item.2 '6ch'
			item.3 '8ch'
		}
	}
	control.40 {
		iface MIXER
		name 'IEC958 Capture Switch'
		value false
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.41 {
		iface MIXER
		name 'IEC958 Playback Source'
		value PCM
		comment {
			access 'read write'
			type ENUMERATED
			count 1
			item.0 PCM
			item.1 'Analog In'
			item.2 'IEC958 In'
		}
	}
	control.42 {
		iface MIXER
		name 'External Amplifier'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
}
state.UART {
	control {
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
snd_mpu401
snd_mpu401_uart
snd_rawmidi
snd_intel8x0
snd_ac97_codec
ac97_bus
snd_pcm
snd_seq
snd_timer
snd_seq_device
snd
soundcore
snd_page_alloc
vesafb
nvidia
ppdev
serio_raw
edac_core
k8temp
edac_mce_amd
ir_lirc_codec
lirc_dev
ir_mce_kbd_decoder
ir_sony_decoder
ir_jvc_decoder
ir_rc6_decoder
ir_rc5_decoder
rc_rc6_mce
ir_nec_decoder
mceusb
rc_core
rfcomm
ns558
gameport
bnep
bluetooth
parport_pc
asus_atk0110
mac_hid
i2c_nforce2
hwmon_vid
lp
parport
firewire_ohci
skge
firewire_core
crc_itu_t
pata_amd
sata_nv
forcedeth


!!ALSA/HDA dmesg
!!--------------

[   12.117839]  (Note that use of the override may cause unknown side effects.)
[   12.224321] snd_intel8x0 0000:00:04.0: enabling device (0000 -> 0003)
[   12.224480] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 22
[   12.224486] snd_intel8x0 0000:00:04.0: PCI INT A -> Link[APCJ] -> GSI 22 (level, low) -> IRQ 22
[   12.224514] snd_intel8x0 0000:00:04.0: setting latency timer to 64
[   12.236141] mceusb 2-3:1.0: Registered Philips eHome Infrared Transceiver with mce emulator interface version 1
--
[  109.916733] nvidia 0000:02:00.0: irq 44 for MSI/MSI-X
[  111.155084] snd_intel8x0 0000:00:04.0: PCI INT A disabled
[  111.190047] mpu401 00:09: disabled
[  111.258120] snd_intel8x0 0000:00:04.0: PCI INT A -> Link[APCJ] -> GSI 22 (level, low) -> IRQ 22
[  111.258153] snd_intel8x0 0000:00:04.0: setting latency timer to 64
[  111.580026] intel8x0_measure_ac97_clock: measured 54740 usecs (2688 samples)

```

This worked when I was running Ubuntu 8.04.  In Ubuntu 8.04, I used a script named AlsaUpgrade-1.0.x-rev-1.16.sh, that updated the version of alsa to 1.0.19.

---

### Post by Yellow Pasque on 2014-03-10
> **pyrates said:**
> I followed the instructions here for installing the daily version of alsa kernel drivers:
[https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

I added this to /etc/modprobe.d/alsa-base.conf
```
options snd-hda-intel model=6stack-dig
```

You don't have an HDA-compliant sound codec, so none of that is applicable to you.  The ALC850 is an older AC97 codec and it uses snd-intel-8x0 module.

My suggestion would be to try the lts-saucy (3.11.x) kernel. There's no sense in chasing an issue that's already been solved upstream.

---

### Post by pyrates on 2014-03-10
So according to this:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

I can upgrade the linux kernel version to the one in saucy, which you says has it fixed.  I will try that, thanks.

---

### Post by Yellow Pasque on 2014-03-10
No, I didn't say it was fixed (sorry if it caused false hope). I said it's possibly fixed ;)

---

### Post by pyrates on 2014-03-10
yeah that didn't fix it, damnit.

---

### Post by Yellow Pasque on 2014-03-11
Try adding this to /etc/modprobe.d/alsa-base.conf:
```
options snd-intel-8x0 spdif_aclink=1
```
Then run:
```
sudo alsa force-reload
```
Sound?

---

### Post by pyrates on 2014-03-12
Well I installed the 32-bit version and I've got analog audio output.  Installed mplayer and this command works:

mplayer -vo null -ao alsa:default -ac hwac3 video.mkv

But only when my receiver is set to stereo and not pro logic/dolby digital, even though all 6 speakers light up.  Then it's just silence.

This does not work though:

mplayer -vo null -ao alsa:iec958 -ac hwac3 video.mkv

---

### Post by pyrates on 2014-03-13
I also had to downgrade to xbmc 11.0.  Some issues with 12.3:

1.  The ac3 pass through doesn't work
2.  Doesn't seem to decode 5.1 aac when ac3 pass through is enabled
3.  It won't let me select a custom audio device, which for me I need to set the audio pass through to default for it to work.  The device iec958 does not work.
I thought I found a way to set it in the file advancedsettings.xml, but that didn't seem to work.

I remember xbmc had an option for enabling ac3 transcoding on the fly, where did it go?  I may have to switch back to 10.1 to get it back to see if that has it.

---

### Post by pyrates on 2014-03-14
> **Temüjin said:**
> Try adding this to /etc/modprobe.d/alsa-base.conf:
```
options snd-intel-8x0 spdif_aclink=1
```
Then run:
```
sudo alsa force-reload
```
Sound?

nope, that did not work.  I still gotta set it to default for it to work.

---

### Post by pyrates on 2014-03-14
Ok here's what I got working so far:

1.  Passing ac3 and dts to receiver works
2.  I got alsa to upmix analog audio to 5.1 that is then transcoded to ac3.  Here's how I did that:

```

# apt-get install ladspa-sdk blop swh-plugins tap-plugins cmt libasound2-plugins
# cd /tmp
# apt-get source libasound2-plugins
# apt-get build-dep libasound2-plugins
# apt-get install libavcodec-dev
# cd alsa-plugins-*
# ./configure
# libtoolize --force --copy; aclocal; autoconf; automake; make
# cd a52/.libs
# cp libasound_module_pcm_a52.la libasound_module_pcm_a52.so /usr/lib/i386-linux-gnu/alsa-lib/

```

/etc/asound.conf:

```

# http://alsa.opensrc.org/SurroundSound
# http://alsa.opensrc.org/Low-pass_filter_for_subwoofer_channel_%28HOWTO%29
# Arch Linux:  pacman -S ladspa blop swh-plugins libsamplerate tap-plugins cmt
# speaker-test -D upmix_20to51 -c 2 -t wav
# listplugins
# analyseplugin cmt
# http://plugin.org.uk/ladspa-swh/docs/ladspa-swh.html
pcm.lowpass_21to21 {
    type ladspa
    slave.pcm "upmix_21to51"
    path "/usr/lib/ladspa"
    channels 3
    plugins {
      0 {
         id 1098  # Identity (Audio) (1098/identity_audio)
         policy duplicate
         input.bindings.0 "Input";
         output.bindings.0 "Output";
      }

      1 {
         id 1052  # High-pass filter
         policy none
         input.bindings.0 "Input";
         output.bindings.0 "Output";
         input {
            controls [ 100 ]
         }
      }

      2 {
         id 1052  # High-pass filter
         policy none
         input.bindings.1 "Input";
         output.bindings.1 "Output";
         input {
            controls [ 100 ]
         }
      }

      3 {
         id 1051  # Low-pass filter
         policy none
         input.bindings.2 "Input";
         output.bindings.2 "Output";
         input {
            controls [ 100 ]
         }
      }

   }
}


pcm.upmix_20to51 {
   type plug
   slave.pcm "lowpass_21to21"
   slave.channels 3
   ttable {
      0.0     1       # left channel
      1.1     1       # right channel
      0.2     0.5     # mix left and right ...
      1.2     0.5     # ... channel for subwoofer
   }
}


pcm.upmix_21to51 {
   type plug
   slave.pcm "a52encoder"
   slave.channels 6
   ttable {
      0.0     1       # front left
      1.1     1       # front right
      0.2     1       # rear left
      1.3     1       # rear right

      # Front left/right to center.
      0.4     0.5
      1.4     0.5

      # Subwoofer, more powerful to compensate for bass-removal from other speakers.
      # Would normally be 1.
      2.5     2
    }
}

pcm.a52encoder
{
   type a52
   slavepcm "hw:0,0"
   channels 6
   rate 48000
   bitrate 640
}

```

But if the audio is 5.1 originally and not ac3 or dts, it up converts the 2 channels where you can barely hear anything.  Anyone know how I can check with alsa the number of channels in the audio and only up convert it to 5.1 if it's stereo, otherwise just send it straight to the ac3 encoder without any up converting.

---

### Post by pyrates on 2014-03-15
> May have found the solution.  I'm running xbmc and it has its own asound.conf.  So I'm gonna try editing that directly.  I hope it works out.

Ok that did not work.

---

### Post by pyrates on 2014-03-18
Ok it seems the fix to this is installing the 32-bit version.  You can set this as solved.

The 64-bit version does not work with this audio chipset it seems.

---

### Post by pyrates on 2014-03-20
Also the centre speaker cable was loose, so that fixed the problem with the centre speaker.

---

