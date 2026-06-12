---
title: "Sound is not working"
date: 2014-02-21
forum: Multimedia Software
---

### Post by Brian_Daniels on 2014-02-21
Hello,
a few weeks ago i installed xubuntu 12.04 onto an 'old' computer (Dell Dimension 2400) for my mom to use. nobody ever plugged in speakers while/after we set it up because they weren't important at the time. anyway she wanted to watch a movie today - being a good son, i plugged some speakers in and realized they aren't working after trying out alsamixer, all that (and no, it's not the speakers, either). the whole OS runs quite smoothly on the machine but I can't seem to figure out what the problem is with the sound not working. If anybody could help with this issue it would be greatly appreciated. mumsie wants her movies.

thanks in advance,
brian.

---

### Post by Yellow Pasque on 2014-02-22
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by Brian_Daniels on 2014-02-22
```
upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.62
!!################################


!!Script ran on: Sat Feb 22 22:49:28 UTC 2014




!!Linux Distribution
!!------------------


Ubuntu 12.04.4 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 12.04.4 LTS" NAME="Ubuntu" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu precise (12.04.4 LTS)"




!!DMI Information
!!---------------


Manufacturer:      Dell Computer Corporation
Product Name:      Dimension 2400               
Product Version:   
Firmware Version:  A00




!!Kernel Information
!!------------------


Kernel release:    3.2.0-59-generic-pae
Operating System:  GNU/Linux
Architecture:      i686
Processor:         i686
SMP Enabled:       Yes




!!ALSA Version
!!------------


Driver version:     1.0.24
Library version:    1.0.25
Utilities version:  1.0.25




!!Loaded ALSA modules
!!-------------------


snd_intel8x0




!!Sound Servers on this system
!!----------------------------


Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes




!!Soundcards recognised by ALSA
!!-----------------------------


 0 [I82801DBICH4   ]: ICH4 - Intel 82801DB-ICH4
                      Intel 82801DB-ICH4 with AD1981B at irq 17




!!PCI Soundcards installed in the system
!!--------------------------------------


00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)




!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!-------------------------------------------------------


00:1f.5 0401: 8086:24c5 (rev 01)
	Subsystem: 1028:0160




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
snd-hda-intel: model=generic




!!Loaded sound module options
!!---------------------------


!!Module: snd_intel8x0
	ac97_clock : 0
	ac97_quirk : (null)
	buggy_irq : N
	buggy_semaphore : N
	enable : N
	id : (null)
	index : -1
	inside_vm : Y
	joystick : 0
	spdif_aclink : 0
	xbox : N




!!AC97 Codec information
!!----------------------
--startcollapse--


0-0/0: Analog Devices AD1981B


PCI Subsys Vendor: 0x1028
PCI Subsys Device: 0x0160


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
Extended ID      : codec=0 rev=1 AMAP DSA=0 VRA
Extended status  : VRA
PCM front DAC    : 44100Hz
PCM ADC          : 44100Hz






AD18XX configuration
Unchained        : 0x1000,0x0000,0x0000
Chained          : 0x0000,0x0000,0x0000


0:00 = 0090
0:02 = 0000
0:04 = 0000
0:06 = 801f
0:08 = 0000
0:0a = 0000
0:0c = 8008
0:0e = 8008
0:10 = 8888
0:12 = 8888
0:14 = 0000
0:16 = 8888
0:18 = 0000
0:1a = 0000
0:1c = 8f8f
0:1e = 0000
0:20 = 0000
0:22 = 0000
0:24 = 0000
0:26 = 000f
0:28 = 0601
0:2a = 0031
0:2c = ac44
0:2e = 0000
0:30 = 0000
0:32 = ac44
0:34 = 0000
0:36 = 0000
0:38 = 0000
0:3a = 2000
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
0:72 = 0000
0:74 = 1001
0:76 = 2010
0:78 = 0000
0:7a = 0000
0:7c = 4144
0:7e = 5374
--endcollapse--




!!ALSA Device nodes
!!-----------------


crw-rw---T+ 1 root audio 116,  8 Feb 21 21:20 /dev/snd/controlC0
crw-rw---T+ 1 root audio 116,  7 Feb 22 16:43 /dev/snd/pcmC0D0c
crw-rw---T+ 1 root audio 116,  6 Feb 22 16:43 /dev/snd/pcmC0D0p
crw-rw---T+ 1 root audio 116,  5 Feb 21 21:20 /dev/snd/pcmC0D1c
crw-rw---T+ 1 root audio 116,  4 Feb 21 21:20 /dev/snd/pcmC0D2c
crw-rw---T+ 1 root audio 116,  3 Feb 21 21:20 /dev/snd/pcmC0D3c
crw-rw---T+ 1 root audio 116,  2 Feb 21 21:20 /dev/snd/pcmC0D4p
crw-rw---T+ 1 root audio 116,  1 Feb 21 21:20 /dev/snd/seq
crw-rw---T+ 1 root audio 116, 33 Feb 21 21:20 /dev/snd/timer


/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Feb 21 21:20 .
drwxr-xr-x 3 root root 240 Feb 21 21:20 ..
lrwxrwxrwx 1 root root  12 Feb 21 21:20 pci-0000:00:1f.5 -> ../controlC0




!!Aplay/Arecord output
!!--------------------


APLAY


**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


ARECORD


**** List of CAPTURE Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 1: Intel ICH - MIC ADC [Intel 82801DB-ICH4 - MIC ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 2: Intel ICH - MIC2 ADC [Intel 82801DB-ICH4 - MIC2 ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 3: Intel ICH - ADC2 [Intel 82801DB-ICH4 - ADC2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


!!Amixer output
!!-------------


!!-------Mixer controls for card 0 [I82801DBICH4]


Card hw:0 'I82801DBICH4'/'Intel 82801DB-ICH4 with AD1981B at irq 17'
  Mixer name	: 'Analog Devices AD1981B'
  Components	: 'AC97a:41445374'
  Controls      : 26
  Simple ctrls  : 18
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Master Mono',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-46.50dB] [off]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [12.00dB] [on]
  Front Right: Playback 31 [100%] [12.00dB] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 23 [74%] [0.00dB] [off] Capture [off]
  Front Right: Playback 23 [74%] [0.00dB] [off] Capture [off]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 23 [74%] [0.00dB] [off] Capture [off]
  Front Right: Playback 23 [74%] [0.00dB] [off] Capture [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 23 [74%] [0.00dB] [off]
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
  Mono: Playback 23 [74%] [0.00dB] [off]
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Aux',0
  Capabilities: pvolume pswitch cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 23 [74%] [0.00dB] [off] Capture [off]
  Front Right: Playback 23 [74%] [0.00dB] [off] Capture [off]
Simple mixer control 'Mono Output Select',0
  Capabilities: enum
  Items: 'Mix' 'Mic'
  Item0: 'Mix'
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 15 [100%] [22.50dB] [off]
  Front Right: Capture 15 [100%] [22.50dB] [off]
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
!!--------------


--startcollapse--
state.I82801DBICH4 {
	control.1 {
		iface MIXER
		name 'Master Playback Switch'
		value.0 true
		value.1 true
		comment {
			access 'read write'
			type BOOLEAN
			count 2
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
		name 'Headphone Playback Switch'
		value.0 true
		value.1 true
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.4 {
		iface MIXER
		name 'Headphone Playback Volume'
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
	control.5 {
		iface MIXER
		name 'Master Mono Playback Switch'
		value false
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.6 {
		iface MIXER
		name 'Master Mono Playback Volume'
		value 0
		comment {
			access 'read write'
			type INTEGER
			count 1
			range '0 - 31'
			dbmin -4650
			dbmax 0
			dbvalue.0 -4650
		}
	}
	control.7 {
		iface MIXER
		name 'Phone Playback Switch'
		value false
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.8 {
		iface MIXER
		name 'Phone Playback Volume'
		value 23
		comment {
			access 'read write'
			type INTEGER
			count 1
			range '0 - 31'
			dbmin -3450
			dbmax 1200
			dbvalue.0 0
		}
	}
	control.9 {
		iface MIXER
		name 'Mic Playback Switch'
		value false
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.10 {
		iface MIXER
		name 'Mic Playback Volume'
		value 23
		comment {
			access 'read write'
			type INTEGER
			count 1
			range '0 - 31'
			dbmin -3450
			dbmax 1200
			dbvalue.0 0
		}
	}
	control.11 {
		iface MIXER
		name 'Mic Boost (+20dB)'
		value false
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.12 {
		iface MIXER
		name 'Line Playback Switch'
		value.0 false
		value.1 false
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.13 {
		iface MIXER
		name 'Line Playback Volume'
		value.0 23
		value.1 23
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 31'
			dbmin -3450
			dbmax 1200
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.14 {
		iface MIXER
		name 'CD Playback Switch'
		value.0 false
		value.1 false
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.15 {
		iface MIXER
		name 'CD Playback Volume'
		value.0 23
		value.1 23
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 31'
			dbmin -3450
			dbmax 1200
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.16 {
		iface MIXER
		name 'Aux Playback Switch'
		value.0 false
		value.1 false
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.17 {
		iface MIXER
		name 'Aux Playback Volume'
		value.0 23
		value.1 23
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 31'
			dbmin -3450
			dbmax 1200
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.18 {
		iface MIXER
		name 'PCM Playback Switch'
		value.0 true
		value.1 true
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.19 {
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
	control.20 {
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
	control.21 {
		iface MIXER
		name 'Capture Switch'
		value.0 false
		value.1 false
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.22 {
		iface MIXER
		name 'Capture Volume'
		value.0 15
		value.1 15
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 15'
			dbmin 0
			dbmax 2250
			dbvalue.0 2250
			dbvalue.1 2250
		}
	}
	control.23 {
		iface MIXER
		name 'Mono Output Select'
		value Mix
		comment {
			access 'read write'
			type ENUMERATED
			count 1
			item.0 Mix
			item.1 Mic
		}
	}
	control.24 {
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
	control.25 {
		iface MIXER
		name 'Stereo Mic'
		value false
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.26 {
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
--endcollapse--




!!All Loaded Modules
!!------------------


Module
snd_intel8x0
snd_ac97_codec
ac97_bus
snd_pcm
dcdbas
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
dm_multipath
snd_seq
snd_timer
snd_seq_device
snd
psmouse
serio_raw
soundcore
snd_page_alloc
shpchp
rfcomm
bnep
parport_pc
bluetooth
ppdev
lp
parport
mac_hid
i915
b44
ssb
drm_kms_helper
drm
i2c_algo_bit
video
floppy
zram




!!ALSA/HDA dmesg
!!--------------







```

---

### Post by Yellow Pasque on 2014-02-22
1. Try headphones. It may just be the amp (EAPD) not working correctly
2. Try a newer kernel (for example, install lts-saucy kernel) or try a LiveUSB of Xubuntu 13.10/14.04 if you don't want to interfere with your current install.

---

