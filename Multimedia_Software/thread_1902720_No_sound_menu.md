---
title: "No sound menu"
date: 2011-12-31
forum: Multimedia Software
---

### Post by ProntoAnthony on 2011-12-31
Although sound was working, lately I've noticed my Sound Menu is missing and no sound device is found in System Settings > Sound.

Strangely (to me) youtube videos still have sound. Anyone know what's wrong?

I ran this command:

wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh

The output:


upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Sat Dec 31 17:13:08 UTC 2011


!!Linux Distribution
!!------------------

Ubuntu 11.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 11.10"


!!DMI Information
!!---------------

Manufacturer:      Dell Inc.
Product Name:      Inspiron 6000                   
Product Version:   


!!Kernel Information
!!------------------

Kernel release:    3.0.0-14-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         i686
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.24
Library version:    1.0.24.1
Utilities version:  1.0.24.2


!!Loaded ALSA modules
!!-------------------

snd_intel8x0


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - No

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [ICH6           ]: ICH4 - Intel ICH6
                      Intel ICH6 with STAC9752,53 at irq 16


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

00:1e.2 0401: 8086:266e (rev 03)
	Subsystem: 1028:0188


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

0-0/0: SigmaTel STAC9752,53

PCI Subsys Vendor: 0x1028
PCI Subsys Device: 0x0188

Flags: 0
Revision         : 0x30
Compat. Class    : 0x12
Subsys. Vendor ID: 0xffff
Subsys. ID       : 0xffff

Capabilities     : -headphone out-
DAC resolution   : 20-bit
ADC resolution   : 20-bit
3D enhancement   : SigmaTel 3D Enhancement

Current setup
Mic gain         : +0dB [+0dB]
POP path         : pre 3D
Sim. stereo      : off
3D enhancement   : off
Loudness         : off
Mono output      : MIX
Mic select       : Mic1
ADC/DAC loopback : off
Extended ID      : codec=0 rev=2 AMAP DSA=0 VRA
Extended status  : VRA
PCM front DAC    : 48000Hz
PCM ADC          : 48000Hz

                    Gain     Inverted  Buffer delay  Location
Master Out       :   0.0 dBV    -       0/fs         Rear I/O Panel
AUX Out          :   0.0 dBV    -       0/fs         Rear I/O Panel
Mic 1            :   0.0 dBV    -       0/fs         Rear I/O Panel
Mic 2            :   0.0 dBV    -       0/fs         Rear I/O Panel
Line In          :   0.0 dBV    -       0/fs         Rear I/O Panel
Mono Out         :   0.0 dBV    -       0/fs         Rear I/O Panel

0:00 = 6a90
0:02 = 0303
0:04 = 0303
0:06 = 0000
0:08 = 0000
0:0a = 801e
0:0c = 801f
0:0e = 801f
0:10 = 9f1f
0:12 = 0606
0:14 = 9f1f
0:16 = 9f1f
0:18 = 0808
0:1a = 0000
0:1c = 8f0f
0:1e = 0000
0:20 = 0000
0:22 = 0000
0:24 = 0000
0:26 = 030c
0:28 = 0a01
0:2a = 0001
0:2c = bb80
0:2e = 0000
0:30 = 0000
0:32 = bb80
0:34 = 0000
0:36 = 0000
0:38 = 0000
0:3a = 0000
0:3c = 0000
0:3e = 0100
0:40 = 0000
0:42 = 0000
0:44 = 0000
0:46 = 0000
0:48 = 0000
0:4a = 0000
0:4c = 0003
0:4e = ffff
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
0:64 = 0000
0:66 = 0000
0:68 = 0000
0:6a = 0000
0:6c = 0030
0:6e = 1000
0:70 = 0000
0:72 = 0000
0:74 = 0800
0:76 = 0000
0:78 = 0000
0:7a = 0000
0:7c = 8384
0:7e = 7652
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116,  8 Dec 31 07:09 /dev/snd/controlC0
crw-rw----+ 1 root audio 116,  7 Dec 31 07:10 /dev/snd/pcmC0D0c
crw-rw----+ 1 root audio 116,  6 Dec 31 07:56 /dev/snd/pcmC0D0p
crw-rw----+ 1 root audio 116,  5 Dec 31 07:10 /dev/snd/pcmC0D1c
crw-rw----+ 1 root audio 116,  4 Dec 31 07:10 /dev/snd/pcmC0D2c
crw-rw----+ 1 root audio 116,  3 Dec 31 07:10 /dev/snd/pcmC0D3c
crw-rw----+ 1 root audio 116,  2 Dec 31 07:10 /dev/snd/pcmC0D4p
crw-rw----+ 1 root audio 116,  1 Dec 31 07:09 /dev/snd/seq
crw-rw----+ 1 root audio 116, 33 Dec 31 07:09 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Dec 31 07:09 .
drwxr-xr-x 3 root root 240 Dec 31 07:09 ..
lrwxrwxrwx 1 root root  12 Dec 31 07:09 pci-0000:00:1e.2 -> ../controlC0


!!Aplay/Arecord output
!!------------

APLAY

Failed to stat runtime directory /home/anthony/.pulse/d9e4786759c311f91c60775400000007-runtime: Invalid argument
**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

Failed to stat runtime directory /home/anthony/.pulse/d9e4786759c311f91c60775400000007-runtime: Invalid argument
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

Card hw:0 'ICH6'/'Intel ICH6 with STAC9752,53 at irq 16'
  Mixer name	: 'SigmaTel STAC9752,53'
  Components	: 'AC97a:83847652'
  Controls      : 30
  Simple ctrls  : 20
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 28 [90%] [-4.50dB] [on]
  Front Right: Playback 28 [90%] [-4.50dB] [on]
Simple mixer control 'Master Mono',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [0.00dB] [on]
Simple mixer control '3D Control - Center',0
  Capabilities: volume volume-joined penum
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 15
  Mono: 0 [0%]
Simple mixer control '3D Control - Depth',0
  Capabilities: volume volume-joined penum
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 15
  Mono: 0 [0%]
Simple mixer control '3D Control - Switch',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 23 [74%] [0.00dB] [on]
  Front Right: Playback 23 [74%] [0.00dB] [on]
Simple mixer control 'PCM Out Path & Mute',0
  Capabilities: enum
  Items: 'pre 3D' 'post 3D'
  Item0: 'pre 3D'
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [-34.50dB] [off] Capture [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off] Capture [off]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive penum
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
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [-34.50dB] [off] Capture [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off] Capture [off]
Simple mixer control 'Phone',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-34.50dB] [off]
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Beep',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 15
  Mono: Playback 0 [0%] [-45.00dB] [off]
Simple mixer control 'Aux',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [-34.50dB] [off] Capture [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off] Capture [off]
Simple mixer control 'Mono Output Select',0
  Capabilities: enum
  Items: 'Mix' 'Mic'
  Item0: 'Mix'
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch cswitch-joined penum
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


!!Alsactl output
!!-------------

--startcollapse--
state.ICH6 {
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
		value.0 28
		value.1 28
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 31'
			dbmin -4650
			dbmax 0
			dbvalue.0 -450
			dbvalue.1 -450
		}
	}
	control.5 {
		iface MIXER
		name 'Master Mono Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.6 {
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
	control.7 {
		iface MIXER
		name 'Beep Playback Switch'
		value false
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.8 {
		iface MIXER
		name 'Beep Playback Volume'
		value 0
		comment {
			access 'read write'
			type INTEGER
			count 1
			range '0 - 15'
			dbmin -4500
			dbmax 0
			dbvalue.0 -4500
		}
	}
	control.9 {
		iface MIXER
		name 'Phone Playback Switch'
		value false
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.10 {
		iface MIXER
		name 'Phone Playback Volume'
		value 0
		comment {
			access 'read write'
			type INTEGER
			count 1
			range '0 - 31'
			dbmin -3450
			dbmax 1200
			dbvalue.0 -3450
		}
	}
	control.11 {
		iface MIXER
		name 'Mic Playback Switch'
		value false
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.12 {
		iface MIXER
		name 'Mic Playback Volume'
		value 0
		comment {
			access 'read write'
			type INTEGER
			count 1
			range '0 - 31'
			dbmin -3450
			dbmax 1200
			dbvalue.0 -3450
		}
	}
	control.13 {
		iface MIXER
		name 'Mic Boost (+20dB)'
		value false
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.14 {
		iface MIXER
		name 'Line Playback Switch'
		value false
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.15 {
		iface MIXER
		name 'Line Playback Volume'
		value.0 0
		value.1 0
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 31'
			dbmin -3450
			dbmax 1200
			dbvalue.0 -3450
			dbvalue.1 -3450
		}
	}
	control.16 {
		iface MIXER
		name 'CD Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.17 {
		iface MIXER
		name 'CD Playback Volume'
		value.0 25
		value.1 25
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 31'
			dbmin -3450
			dbmax 1200
			dbvalue.0 300
			dbvalue.1 300
		}
	}
	control.18 {
		iface MIXER
		name 'Video Playback Switch'
		value false
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.19 {
		iface MIXER
		name 'Video Playback Volume'
		value.0 0
		value.1 0
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 31'
			dbmin -3450
			dbmax 1200
			dbvalue.0 -3450
			dbvalue.1 -3450
		}
	}
	control.20 {
		iface MIXER
		name 'Aux Playback Switch'
		value false
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.21 {
		iface MIXER
		name 'Aux Playback Volume'
		value.0 0
		value.1 0
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 31'
			dbmin -3450
			dbmax 1200
			dbvalue.0 -3450
			dbvalue.1 -3450
		}
	}
	control.22 {
		iface MIXER
		name 'PCM Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.23 {
		iface MIXER
		name 'PCM Playback Volume'
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
	control.24 {
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
	control.25 {
		iface MIXER
		name 'Capture Switch'
		value false
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.26 {
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
	control.27 {
		iface MIXER
		name 'PCM Out Path & Mute'
		value 'pre 3D'
		comment {
			access 'read write'
			type ENUMERATED
			count 1
			item.0 'pre 3D'
			item.1 'post 3D'
		}
	}
	control.28 {
		iface MIXER
		name '3D Control - Switch'
		value false
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.29 {
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
		name '3D Control - Center'
		value 0
		comment {
			access 'read write'
			type INTEGER
			count 1
			range '0 - 15'
		}
	}
	control.32 {
		iface MIXER
		name '3D Control - Depth'
		value 0
		comment {
			access 'read write'
			type INTEGER
			count 1
			range '0 - 15'
		}
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
rfcomm
bnep
bluetooth
pci_stub
vboxpci
vboxnetadp
vboxnetflt
vboxdrv
michael_mic
arc4
lib80211_crypt_tkip
lib80211_crypt_ccmp
parport_pc
ppdev
joydev
psmouse
ipw2200
libipw
serio_raw
dell_laptop
dcdbas
pcmcia
i915
cfg80211
lib80211
yenta_socket
pcmcia_rsrc
pcmcia_core
drm_kms_helper
drm
i2c_algo_bit
video
binfmt_misc
snd_intel8x0
snd_ac97_codec
ac97_bus
snd_pcm
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
snd_seq
snd_timer
snd_seq_device
snd
soundcore
snd_page_alloc
lp
parport
firewire_ohci
sdhci_pci
firewire_core
crc_itu_t
sdhci
usbhid
hid


!!ALSA/HDA dmesg
!!------------------

---

### Post by MoreOrLess on 2011-12-31
Your pulseaudio isn't running (youtube/flash doesn't use pulseaudio by default, which is why it's still working). Try resetting your pulse configuration files and logging out/in:
```
rm -rf ~/.pulse*
```

If that doesn't work, get a verbose pulse log: [https://wiki.ubuntu.com/PulseAudio/Log](https://wiki.ubuntu.com/PulseAudio/Log)

---

### Post by ProntoAnthony on 2011-12-31
That did it!

Thank you.

---

