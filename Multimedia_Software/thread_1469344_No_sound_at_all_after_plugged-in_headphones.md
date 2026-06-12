---
title: "No sound at all after plugged-in headphones"
date: 2010-05-02
forum: Multimedia Software
---

### Post by vtdr on 2010-05-02
Hi to everyone,
I always had fine audio output, but when I plugged in a set of headphones (using the jack on the side of my laptop) last night, I experienced no sound at all, not on the headphones nor on the speakers. The real issue is that I miss sound after plugging out the headphones... since I didn't modify nothing...

I checked several solutions on the net and in this forum, but neither one seems to be right for my problem.

Ubuntu 9.10 on Toshiba P30-128 laptop.

Thank you in advance for your attention.

---

### Post by lidex on 2010-05-02
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

### Post by vtdr on 2010-05-03
Hi lidex,

thank you very much for your reply. Below you'll see what you have requested. Also, I can tell you that now headphones work, but speakers do not. I made headphones working by tweaking with PulseAudio Device Chooser...

I' am sorry for my repost delay, but I come from Italy and 9 hours ago I was sleeping...

```
uname -a

Linux cris-laptop 2.6.31-21-generic #59-Ubuntu SMP Wed Mar 24 07:28:56 UTC 2010 i686 GNU/Linux

aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Modem [ATI IXP Modem], device 0: ATI IXP MC97 [ATI IXP MC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

cat /proc/asound/version

Advanced Linux Sound Architecture Driver Version 1.0.20.

head -n 1 /proc/asound/card*/codec#*

head: cannot open `/proc/asound/card*/codec#*' for reading: No such file or directory

```

Toshiba P30-128 laptop 

That's all lidex...

vtdr

---

### Post by vtdr on 2010-05-03
Hi lidex,

this is an extension of my previous post...

```
head -n 1 /proc/asound/card0/codec97#0/ac97#0-0

0-0/0: Realtek ALC250 rev 2
```

vtdr

---

### Post by vtdr on 2010-05-05
Hi lidex,

did you find any solution?

Thanks,

vtdr

---

### Post by lidex on 2010-05-06
Sorry, was pulled out of town with no notice for two days. Do this for me. Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Provide a link for the output or post it here using code tags.

---

### Post by vtdr on 2010-05-06
Hi lidex!
Thank you for your replies.
> Sorry, was pulled out of town with no notice for two days. Do this for me. Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
Code:
sudo bash utils_alsa-info.sh
Enter your user password when prompted. Provide a link for the output or post it here using code tags.

This is the output:

```
upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.59
!!################################

!!Script ran on: Thu May  6 07:48:52 UTC 2010


!!Linux Distribution
!!------------------

Ubuntu 9.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 9.10"


!!DMI Information
!!---------------

Manufacturer:      TOSHIBA
Product Name:      Satellite P30


!!Kernel Information
!!------------------

Kernel release:    2.6.31-21-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.20
Library version:    1.0.20
Utilities version:  1.0.20


!!Loaded ALSA modules
!!-------------------

snd_atiixp
snd_atiixp_modem


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

 0 [IXP            ]: ATIIXP - ATI IXP
                      ATI IXP rev 1 with ALC250 at 0xe8004400, irq 17
 1 [Modem          ]: ATIIXP-MODEM - ATI IXP Modem
                      ATI IXP Modem rev 1 at 0xe8004800, irq 17


!!PCI Soundcards installed in the system
!!--------------------------------------

00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller (rev 01)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:14.5 0401: 1002:4341 (rev 01)
	Subsystem: 1179:ff01


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-usb-caiaq: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-hda-intel: power_save=10 power_save_controller=N


!!Loaded sound module options
!!--------------------------

!!Module: snd_atiixp
	ac97_clock : 48000
	ac97_codec : -1
	ac97_quirk : <NULL>
	enable : N
	id : <NULL>
	index : -1
	spdif_aclink : Y

!!Module: snd_atiixp_modem
	ac97_clock : 48000
	enable : N
	id : <NULL>
	index : -2


!!AC97 Codec information
!!---------------------------
--startcollapse--

0-0/0: Realtek ALC250 rev 2

PCI Subsys Vendor: 0x1179
PCI Subsys Device: 0xff01

Flags: 0
Revision         : 0x00
Compat. Class    : 0x00
Subsys. Vendor ID: 0xffff
Subsys. ID       : 0xffff

Capabilities     : -headphone out-
DAC resolution   : 20-bit
ADC resolution   : 18-bit
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
Double rate slots: 10/11
Extended ID      : codec=0 rev=2 AMAP DSA=0 SPDIF DRA VRA
Extended status  : SPDIF=3/4 VRA
PCM front DAC    : 44100Hz
PCM ADC          : 44100Hz
SPDIF Control    : Consumer PCM Category=0x2 Generation=1 Rate=48kHz

                    Gain     Inverted  Buffer delay  Location
Master Out       :   0.0 dBV    -      23/fs         Rear I/O Panel
AUX Out          :   0.0 dBV    -      23/fs         Rear I/O Panel
Center/LFE Out   :   0.0 dBV    -      23/fs         Rear I/O Panel
SPDIF Out        :   0.0 dBV    -      23/fs         Rear I/O Panel
Phone In         :   0.0 dBV    -      23/fs         Rear I/O Panel
Mic 1            :   0.0 dBV    -      23/fs         Rear I/O Panel
Mic 2            :   0.0 dBV    -      23/fs         Rear I/O Panel
Line In          :   0.0 dBV    -      23/fs         Rear I/O Panel
CD In            :   0.0 dBV    -      23/fs         Rear I/O Panel
Video In         :   0.0 dBV    -      23/fs         Rear I/O Panel
Aux In           :   0.0 dBV    -      23/fs         Rear I/O Panel
Mono Out         :   0.0 dBV    -      23/fs         Rear I/O Panel

0:00 = 0190
0:02 = 0000
0:04 = 0000
0:06 = 801f
0:08 = 0000
0:0a = 0000
0:0c = 801f
0:0e = 831f
0:10 = 9f1f
0:12 = 0000
0:14 = 0000
0:16 = 9f1f
0:18 = 0101
0:1a = 0303
0:1c = 8f0f
0:1e = 0000
0:20 = 0000
0:22 = 0000
0:24 = 0000
0:26 = 800f
0:28 = 0a07
0:2a = 0001
0:2c = ac44
0:2e = 0000
0:30 = 0000
0:32 = ac44
0:34 = bb80
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
0:5c = 0000
0:5e = 0000
0:60 = 0000
0:62 = 0000
0:64 = 0000
0:66 = 0000
0:68 = 0aea
0:6a = 4400
0:6c = 4601
0:6e = 0015
0:70 = 0008
0:72 = 0000
0:74 = 0100
0:76 = 0304
0:78 = 0c03
0:7a = 6002
0:7c = 414c
0:7e = 4752
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116, 9 May  5 12:21 /dev/snd/controlC0
crw-rw----+ 1 root audio 116, 6 May  5 12:21 /dev/snd/controlC1
crw-rw----+ 1 root audio 116, 8 May  5 23:56 /dev/snd/pcmC0D0c
crw-rw----+ 1 root audio 116, 7 May  5 23:31 /dev/snd/pcmC0D0p
crw-rw----+ 1 root audio 116, 5 May  5 12:21 /dev/snd/pcmC1D0c
crw-rw----+ 1 root audio 116, 4 May  5 12:21 /dev/snd/pcmC1D0p
crw-rw----+ 1 root audio 116, 3 May  5 12:21 /dev/snd/seq
crw-rw----+ 1 root audio 116, 2 May  5 12:21 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  80 May  5 12:21 .
drwxr-xr-x 3 root root 220 May  5 12:21 ..
lrwxrwxrwx 1 root root  12 May  5 12:21 pci-0000:00:14.5 -> ../controlC0
lrwxrwxrwx 1 root root  12 May  5 12:21 pci-0000:00:14.6 -> ../controlC1


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Modem [ATI IXP Modem], device 0: ATI IXP MC97 [ATI IXP MC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Modem [ATI IXP Modem], device 0: ATI IXP MC97 [ATI IXP MC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [IXP]

Card hw:0 'IXP'/'ATI IXP rev 1 with ALC250 at 0xe8004400, irq 17'
  Mixer name	: 'Realtek ALC250 rev 2'
  Components	: 'AC97a:414c4752'
  Controls      : 33
  Simple ctrls  : 21
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 63
  Mono:
  Front Left: Playback 63 [100%] [0.00dB] [on]
  Front Right: Playback 63 [100%] [0.00dB] [on]
Simple mixer control 'Master Mono',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-46.50dB] [off]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 63
  Mono:
  Front Left: Playback 63 [100%] [0.00dB] [on]
  Front Right: Playback 63 [100%] [0.00dB] [on]
Simple mixer control '3D Control - Switch',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 30 [97%] [10.50dB] [on]
  Front Right: Playback 30 [97%] [10.50dB] [on]
Simple mixer control 'PCM Out Path & Mute',0
  Capabilities: enum
  Items: 'pre 3D' 'post 3D'
  Item0: 'pre 3D'
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [-34.50dB] [off] Capture [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off] Capture [off]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 31 [100%] [12.00dB] [on] Capture [off]
  Front Right: Playback 31 [100%] [12.00dB] [on] Capture [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [-34.50dB] [off] Capture [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off] Capture [off]
Simple mixer control 'Mic Boost (+20dB)',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Mic Select',0
  Capabilities: enum
  Items: 'Mic1' 'Mic2'
  Item0: 'Mic1'
Simple mixer control 'Video',0
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Phone',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-34.50dB] [off]
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 Playback AC97-SPSA',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 3
  Mono: 0 [0%]
Simple mixer control 'PC Speaker',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 15
  Mono: Playback 15 [100%] [0.00dB] [on]
Simple mixer control 'Aux',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [-34.50dB] [off] Capture [on]
  Front Right: Playback 0 [0%] [-34.50dB] [off] Capture [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch cswitch-joined
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 15 [100%] [22.50dB] [off]
  Front Right: Capture 15 [100%] [22.50dB] [off]
Simple mixer control 'Mix',0
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Mix Mono',0
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'External Amplifier',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]

!!-------Mixer controls for card 1 [Modem]

Card hw:1 'Modem'/'ATI IXP Modem rev 1 at 0xe8004800, irq 17'
  Mixer name	: 'Silicon Laboratory Si3036,8 rev 7'
  Components	: 'AC97m:53494c27'
  Controls      : 3
  Simple ctrls  : 3
Simple mixer control 'Caller ID',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Modem Speaker',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%]
  Front Right: 0 [0%]
Simple mixer control 'Off-hook',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]


!!Alsactl output
!!-------------

--startcollapse--
state.IXP {
	control.1 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Master Playback Switch'
		value true
	}
	control.2 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 63'
		comment.dbmin -9450
		comment.dbmax 0
		iface MIXER
		name 'Master Playback Volume'
		value.0 63
		value.1 63
	}
	control.3 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Headphone Playback Switch'
		value true
	}
	control.4 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 63'
		comment.dbmin -9450
		comment.dbmax 0
		iface MIXER
		name 'Headphone Playback Volume'
		value.0 63
		value.1 63
	}
	control.5 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Master Mono Playback Switch'
		value false
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
		name 'PC Speaker Playback Switch'
		value true
	}
	control.8 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 15'
		comment.dbmin -4500
		comment.dbmax 0
		iface MIXER
		name 'PC Speaker Playback Volume'
		value 15
	}
	control.9 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Phone Playback Switch'
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
		name 'Phone Playback Volume'
		value 0
	}
	control.11 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Mic Playback Switch'
		value false
	}
	control.12 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Mic Playback Volume'
		value.0 0
		value.1 0
	}
	control.13 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Mic Boost (+20dB)'
		value false
	}
	control.14 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Line Playback Switch'
		value false
	}
	control.15 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Line Playback Volume'
		value.0 0
		value.1 0
	}
	control.16 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'CD Playback Switch'
		value true
	}
	control.17 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'CD Playback Volume'
		value.0 31
		value.1 31
	}
	control.18 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Aux Playback Switch'
		value false
	}
	control.19 {
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
	control.20 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'PCM Playback Switch'
		value true
	}
	control.21 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'PCM Playback Volume'
		value.0 30
		value.1 30
	}
	control.22 {
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
		value.0 Aux
		value.1 Aux
	}
	control.23 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Capture Switch'
		value false
	}
	control.24 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 15'
		comment.dbmin 0
		comment.dbmax 2250
		iface MIXER
		name 'Capture Volume'
		value.0 15
		value.1 15
	}
	control.25 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 'pre 3D'
		comment.item.1 'post 3D'
		iface MIXER
		name 'PCM Out Path & Mute'
		value 'pre 3D'
	}
	control.26 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name '3D Control - Switch'
		value false
	}
	control.27 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Mic1
		comment.item.1 Mic2
		iface MIXER
		name 'Mic Select'
		value Mic1
	}
	control.28 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Con Mask'
		value '0fff000f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.29 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		value cf00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
	}
	control.30 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Default'
		value '0082000200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.31 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Switch'
		value false
	}
	control.32 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 3'
		iface MIXER
		name 'IEC958 Playback AC97-SPSA'
		value 0
	}
	control.33 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'External Amplifier'
		value false
	}
}
state.Modem {
	control.1 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Off-hook Switch'
		value false
	}
	control.2 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Caller ID Switch'
		value false
	}
	control.3 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 3'
		iface MIXER
		name 'Modem Speaker Volume'
		value.0 0
		value.1 0
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
binfmt_misc
ppdev
bridge
stp
bnep
vboxnetadp
vboxnetflt
vboxdrv
arc4
ecb
joydev
snd_atiixp
snd_seq_dummy
pcmcia
snd_seq_oss
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
snd_atiixp_modem
snd_ac97_codec
ac97_bus
snd_pcm_oss
snd_mixer_oss
snd_seq
snd_pcm
iptable_filter
psmouse
serio_raw
ip_tables
x_tables
btusb
ath5k
mac80211
ath
yenta_socket
rsrc_nonstatic
pcmcia_core
sdhci_pci
sdhci
led_class
cfg80211
i2c_piix4
snd_seq_device
snd_timer
snd
soundcore
snd_page_alloc
shpchp
lp
parport
dm_raid45
xor
8139too
ohci1394
radeon
8139cp
mii
video
output
ieee1394
usb_storage
ttm
drm
i2c_algo_bit
ati_agp
agpgart


!!ALSA/HDA dmesg
!!------------------



```

That's all, feel free to punish me if I went wrong...
vtdr

---

### Post by lidex on 2010-05-06
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-atiixp ac97-quirk=swap-hp 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press F6 to select the correct soundcard.
Press F3 to show playback levels. F4 selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default.

---

### Post by vtdr on 2010-05-06
> Re: No sound at all after plugged-in headphones
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
Code:
 gksudo gedit /etc/modprobe.d/alsa-base.conf
Insert this line at the bottom:
Code:
 options snd-atiixp ac97-quirk=swap-hp
Save. Close. Reboot. Check your levels in alsamixer.
Code:
 alsamixer
Press F6 to select the correct soundcard.
Press F3 to show playback levels. F4 selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default.

```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Power down HDA controllers after 10 idle seconds
options snd-hda-intel power_save=10 power_save_controller=N
options snd-atiixp ac97-quirk=swap-hp
```

Nothing has changed... headphones work greatly and internal speakers don't... Here it is what I get:

[ATTACH]155667[/ATTACH]

[ATTACH]155668[/ATTACH]

[ATTACH]155669[/ATTACH]

[ATTACH]155670[/ATTACH]

[ATTACH]155671[/ATTACH]

Couldn't it be that when I inserted Headphones jack, I could have break any sort of "hardware mechanism" ? 

vtdr

---

### Post by lidex on 2010-05-06
I kinda doubt it. I think I got my symbols mixed up. OK, edit that line to look like this:
```
options snd-atiixp ac97_quirk=swap_hp
```
Don't forget to reboot. BTW, which slider controls the HP volume?

In your alsamixer, showing playback, there are elements off to the right, what are they?

---

### Post by vtdr on 2010-05-06
> I kinda doubt it. I think I got my symbols mixed up. OK, edit that line to look like this:
Code:
options snd-atiixp ac97_quirk=swap_hp
Don't forget to reboot. BTW, which slider controls the HP volume?

In your alsamixer, showing playback, there are elements off to the right, what are they?

Nothing...

```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Power down HDA controllers after 10 idle seconds
options snd-hda-intel power_save=10 power_save_controller=N
options snd-atiixp ac97_quirk=swap_hp
```

Here they are elements off to the right in playback alsamixer

[ATTACH]155675[/ATTACH]

PCM slider controls HP volume, it's the 4th from the left, playback alsamixer, visible in Sound_3.jpg

I' am very sorry, but now I have to leave you, my job is calling... I will be back here in about six hours.

**For now I thank you very much** 

See you soon,
vtdr

---

### Post by lidex on 2010-05-06
Here's the fun part. I'll need you to upgrade alsa. follow the alsa-upgrade-script link in my sig.

---

### Post by vtdr on 2010-05-06
Well, now I will try...

---

### Post by vtdr on 2010-05-06
Hi lidex, 
after your last advice:

> Here's the fun part. I'll need you to upgrade alsa. follow the alsa-upgrade-script link in my sig.

I had followed this guide:

```
Short Alsa-Upgrade script install instructions:

1. download the script and save it somewhere
2. cd <your-download-dir>
3. tar xvf AlsaUpgrade-1.0.22.1-2.tar
4. sudo ./AlsaUpgrade-1.0.22.1-2.sh -d
5. sudo ./AlsaUpgrade-1.0.22.1-2.sh -c
6. sudo ./AlsaUpgrade-1.0.22.1-2.sh -i
7. sudo shutdown -r 0

Looging: I recommend to log all the upgrade steps, e.g. 

script -a -c "./AlsaUpgrade-1.0.22.1-2.sh -d" /tmp/Alsa_1.0.22.1_upgrade_download.log 
```

Now I have no sound, you can take a look at this image:
[ATTACH]155729[/ATTACH]

I' ll post log files in the next posts.

I want to inform you that after the last operation, HP don't run anymore...

vtdr

---

### Post by vtdr on 2010-05-06
Log file number one:

```
Script started on Thu 06 May 2010 09:41:31 PM CEST
[H[2J
--Thu May  6 21:41:31 CEST 2010----Alsa-Upgrade-Script-1.0.22.1-1 ----------------- 
-
- You'll be upgraded from 1.0.20. to 1.0.22.1
- Run -h option for further help and to look up the workflows
-
-
-
- 
- DISCLAIMER: Use this script at your own risk. I do not take any 
-             responsability for any problems caused by running 
-             this script. 
-
- In any case I strongly advise you to make a backup first!
--------------------------------------------------------------------------------------
-
-
- Do you want to prepare the environment and download 1.0.22.1 [y/n]: y
[H[2J
--------------------------------------------------------------------------------------
-  Packages will be downloaded
--------------------------------------------------------------------------------------

--------------------------------------------------------------------------------------
-  Working on following Alsa packages...
--------------------------------------------------------------------------------------
Driver: alsa-driver-1.0.22.1
Library: alsa-lib-1.0.22
Plugins: alsa-plugins-1.0.22
Utils: alsa-utils-1.0.22
Firmware: alsa-firmware-1.0.20
OSS: alsa-oss-1.0.17
Installing tools: alsa-tools-1.0.22

--------------------------------------------------------------------------------------
-  Installing packages required to build ALSA...
--------------------------------------------------------------------------------------


0% [Working]
            
Hit http://ppa.launchpad.net karmic Release.gpg

            
3% [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting f
                                                                               
Ign http://ppa.launchpad.net karmic/main Translation-en_US

6% [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting f
                                                                               
Hit http://packages.medibuntu.org karmic Release.gpg

10% [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting 
                                                                               
Ign http://packages.medibuntu.org karmic/free Translation-en_US

13% [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting 
                                                                               
Get:1 http://dl.google.com stable Release.gpg [189B]

88% [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting 
                                                                               
Ign http://dl.google.com stable/main Translation-en_US

89% [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting 
                                                                               
Hit http://it.archive.ubuntu.com karmic Release.gpg

89% [Waiting for headers] [Connecting to it.archive.ubuntu.com (193.206.139.34)
                                                                               
Hit http://archive.ubuntu.com karmic Release.gpg

89% [Connecting to it.archive.ubuntu.com (193.206.139.34)] [Waiting for headers
                                                                               
Ign http://packages.medibuntu.org karmic/non-free Translation-en_US

89% [Waiting for headers] [Connecting to it.archive.ubuntu.com (193.206.139.34)
                                                                               
Hit http://security.ubuntu.com karmic-security Release.gpg

89% [Waiting for headers] [Connecting to it.archive.ubuntu.com (193.206.139.34)
                                                                               
Ign http://security.ubuntu.com karmic-security/main Translation-en_US

90% [Waiting for headers] [Connecting to it.archive.ubuntu.com (193.206.139.34)
                                                                               
Hit http://archive.canonical.com karmic Release.gpg

90% [Waiting for headers] [Connecting to it.archive.ubuntu.com (193.206.139.34)
                                                                               
Ign http://archive.canonical.com karmic/partner Translation-en_US

90% [Waiting for headers] [Connecting to it.archive.ubuntu.com (193.206.139.34)
                                                                               
Hit http://ppa.launchpad.net karmic Release

90% [Waiting for headers] [Connecting to it.archive.ubuntu.com (193.206.139.34)
                                                                               
Hit http://packages.medibuntu.org karmic Release

90% [Waiting for headers] [Connecting to it.archive.ubuntu.com (193.206.139.34)
90% [Release gpgv 65970] [Waiting for headers] [Connecting to it.archive.ubuntu
90% [Waiting for headers] [Connecting to it.archive.ubuntu.com (193.206.139.34)
90% [Release gpgv 9237] [Waiting for headers] [Connecting to it.archive.ubuntu.
90% [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting 
                                                                               
Get:2 http://dl.google.com stable Release [2,540B]

50% [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting 
99% [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting 
99% [2 Release gpgv 2540] [Waiting for headers] [Waiting for headers] [Waiting 
99% [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting 
                                                                               
Hit http://archive.ubuntu.com karmic Release

99% [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting 
99% [Release gpgv 65940] [Waiting for headers] [Waiting for headers] [Waiting f
                                                                               
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_US

                                                                               
Ign http://security.ubuntu.com karmic-security/universe Translation-en_US

                                                                               
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_US

99% [Release gpgv 65940] [Waiting for headers] [Waiting for headers] [Waiting f
                                                                               
Hit http://security.ubuntu.com karmic-security Release

99% [Release gpgv 65940] [Waiting for headers] [Waiting for headers] [Waiting f
99% [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting 
                                                                               
Hit http://archive.canonical.com karmic Release

99% [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting 
99% [Release gpgv 44056] [Waiting for headers] [Waiting for headers] [Waiting f
                                                                               
Hit http://ppa.launchpad.net karmic/main Packages

99% [Release gpgv 44056] [Waiting for headers] [Waiting for headers] [Waiting f
99% [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting 
99% [Release gpgv 9347] [Waiting for headers] [Waiting for headers] [Waiting fo
99% [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting 
                                                                               
Ign http://it.archive.ubuntu.com karmic/main Translation-en_US

99% [Waiting for headers] [Connecting to it.archive.ubuntu.com (193.206.139.34)
                                                                               
Hit http://packages.medibuntu.org karmic/free Packages

99% [Waiting for headers] [Connecting to it.archive.ubuntu.com (193.206.139.34)
                                                                               
Hit http://download.virtualbox.org karmic Release.gpg

                                                                               
Ign http://download.virtualbox.org karmic/non-free Translation-en_US

99% [Waiting for headers] [Connecting to it.archive.ubuntu.com (193.206.139.34)
                                                                               
Get:3 http://dl.google.com stable/main Packages [892B]

75% [Waiting for headers] [Connecting to it.archive.ubuntu.com (193.206.139.34)
99% [Waiting for headers] [Connecting to it.archive.ubuntu.com (193.206.139.34)
                                                                               
Hit http://archive.ubuntu.com karmic/main Sources

99% [Connecting to it.archive.ubuntu.com (193.206.139.34)] [Waiting for headers
99% [3 Packages bzip2 0] [Waiting for headers] [Connecting to it.archive.ubuntu
99% [Waiting for headers] [Connecting to it.archive.ubuntu.com (193.206.139.34)
                                                                               
Hit http://security.ubuntu.com karmic-security/main Packages

99% [Waiting for headers] [Connecting to it.archive.ubuntu.com (193.206.139.34)
                                                                               
Hit http://archive.canonical.com karmic/partner Packages

99% [Waiting for headers] [Connecting to it.archive.ubuntu.com (193.206.139.34)
                                                                               
Hit http://packages.medibuntu.org karmic/non-free Packages

99% [Waiting for headers] [Connecting to it.archive.ubuntu.com (193.206.139.34)
                                                                               
Hit http://archive.ubuntu.com karmic/restricted Sources

99% [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting 
                                                                               
Hit http://security.ubuntu.com karmic-security/restricted Packages

99% [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting 
                                                                               
Hit http://security.ubuntu.com karmic-security/restricted Sources

                                                                               
Hit http://security.ubuntu.com karmic-security/main Sources

99% [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting 
                                                                               
Hit http://security.ubuntu.com karmic-security/multiverse Sources

99% [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting 
                                                                               
Hit http://archive.canonical.com karmic/partner Sources

                                                                               
99% [Waiting for headers] [Waiting for headers] [Waiting for headers]
                                                                     
Ign http://it.archive.ubuntu.com karmic/restricted Translation-en_US

                                                                     
99% [Connecting to it.archive.ubuntu.com (193.206.139.34)] [Waiting for headers
                                                                               
Hit http://download.virtualbox.org karmic Release

99% [Connecting to it.archive.ubuntu.com (193.206.139.34)] [Waiting for headers
99% [Release gpgv 3454] [Connecting to it.archive.ubuntu.com (193.206.139.34)] 
99% [Connecting to it.archive.ubuntu.com (193.206.139.34)] [Waiting for headers
                                                                               
Hit http://security.ubuntu.com karmic-security/universe Sources

                                                                               
Hit http://security.ubuntu.com karmic-security/universe Packages

                                                                               
Hit http://security.ubuntu.com karmic-security/multiverse Packages

99% [Connecting to it.archive.ubuntu.com (193.206.139.34)] [Waiting for headers
                                                                               
Ign http://it.archive.ubuntu.com karmic/universe Translation-en_US

99% [Connecting to it.archive.ubuntu.com (193.206.139.34)] [Waiting for headers
                                                                               
Hit http://download.virtualbox.org karmic/non-free Packages

                                                                               
99% [Waiting for headers]
                         
Ign http://it.archive.ubuntu.com karmic/multiverse Translation-en_US

                         
99% [Connecting to it.archive.ubuntu.com (193.206.139.34)]
                                                          
Hit http://it.archive.ubuntu.com karmic-updates Release.gpg

99% [Connecting to it.archive.ubuntu.com (193.206.139.34)]
                                                          
Ign http://it.archive.ubuntu.com karmic-updates/main Translation-en_US

99% [Connecting to it.archive.ubuntu.com (193.206.139.34)]
                                                          
Ign http://it.archive.ubuntu.com karmic-updates/restricted Translation-en_US

99% [Connecting to it.archive.ubuntu.com (193.206.139.34)]
                                                          
Ign http://it.archive.ubuntu.com karmic-updates/universe Translation-en_US

99% [Connecting to it.archive.ubuntu.com (193.206.139.34)]
                                                          
Ign http://it.archive.ubuntu.com karmic-updates/multiverse Translation-en_US

99% [Connecting to it.archive.ubuntu.com (193.206.139.34)]
                                                          
Hit http://it.archive.ubuntu.com karmic Release

99% [Connecting to it.archive.ubuntu.com (193.206.139.34)]
                                                          
99% [Release gpgv 65940] [Connecting to it.archive.ubuntu.com (193.206.139.34)]
                                                                               
99% [Connecting to it.archive.ubuntu.com (193.206.139.34)]
                                                          
Hit http://it.archive.ubuntu.com karmic-updates Release

                                                          
99% [Working]
             
99% [Release gpgv 44054] [Connecting to it.archive.ubuntu.com (193.206.139.34)]
                                                                               
99% [Connecting to it.archive.ubuntu.com (193.206.139.34)]
                                                          
Hit http://it.archive.ubuntu.com karmic/main Packages

99% [Connecting to it.archive.ubuntu.com (193.206.139.34)]
                                                          
99% [Waiting for headers]
99% [Waiting for headers]
                         
Hit http://it.archive.ubuntu.com karmic/restricted Packages

                         
99% [Connecting to it.archive.ubuntu.com (193.206.139.34)]
                                                          
99% [Waiting for headers]
99% [Waiting for headers]
                         
Hit http://it.archive.ubuntu.com karmic/restricted Sources

                         
99% [Connecting to it.archive.ubuntu.com (193.206.139.34)]
                                                          
Hit http://it.archive.ubuntu.com karmic/main Sources

99% [Connecting to it.archive.ubuntu.com (193.206.139.34)]
                                                          
Hit http://it.archive.ubuntu.com karmic/multiverse Sources

99% [Connecting to it.archive.ubuntu.com (193.206.139.34)]
                                                          
Hit http://it.archive.ubuntu.com karmic/universe Sources

99% [Connecting to it.archive.ubuntu.com (193.206.139.34)]
                                                          
Hit http://it.archive.ubuntu.com karmic/universe Packages

99% [Connecting to it.archive.ubuntu.com (193.206.139.34)]
                                                          
Hit http://it.archive.ubuntu.com karmic/multiverse Packages

99% [Connecting to it.archive.ubuntu.com (193.206.139.34)]
                                                          
Hit http://it.archive.ubuntu.com karmic-updates/main Packages

99% [Connecting to it.archive.ubuntu.com (193.206.139.34)]
                                                          
Hit http://it.archive.ubuntu.com karmic-updates/restricted Packages

99% [Connecting to it.archive.ubuntu.com (193.206.139.34)]
                                                          
Hit http://it.archive.ubuntu.com karmic-updates/restricted Sources

99% [Connecting to it.archive.ubuntu.com (193.206.139.34)]
                                                          
Hit http://it.archive.ubuntu.com karmic-updates/main Sources

99% [Connecting to it.archive.ubuntu.com (193.206.139.34)]
                                                          
Hit http://it.archive.ubuntu.com karmic-updates/multiverse Sources

                                                          
99% [Connecting to it.archive.ubuntu.com (193.206.139.34)]            601B/s 0s
                                                                               
Hit http://it.archive.ubuntu.com karmic-updates/universe Sources

99% [Connecting to it.archive.ubuntu.com (193.206.139.34)]            601B/s 0s
                                                                               
Hit http://it.archive.ubuntu.com karmic-updates/universe Packages

99% [Connecting to it.archive.ubuntu.com (193.206.139.34)]            601B/s 0s
                                                                               
Hit http://it.archive.ubuntu.com karmic-updates/multiverse Packages

100% [Working]                                                        601B/s 0s
                                                                               
Fetched 3,621B in 6s (562B/s)

Reading package lists... 0%

Reading package lists... 0%

Reading package lists... 6%

Reading package lists... Done


--------------------------------------------------------------------------------------
-  Upgrading installed packages first!
--------------------------------------------------------------------------------------

Reading package lists... 0%

Reading package lists... 100%

Reading package lists... Done


Building dependency tree... 0%

Building dependency tree... 0%

Building dependency tree... 50%

Building dependency tree... 50%

Building dependency tree       


Reading state information... 0%

Reading state information... 0%

Reading state information... Done

0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

--------------------------------------------------------------------------------------
-  Installing Alsa dev packages
--------------------------------------------------------------------------------------

--------------------------------------------------------------------------------------
-  Package linux-sound-base will be installed
--------------------------------------------------------------------------------------

Reading package lists... 0%

Reading package lists... 100%

Reading package lists... Done


Building dependency tree... 0%

Building dependency tree... 0%

Building dependency tree... 50%

Building dependency tree... 50%

Building dependency tree       


Reading state information... 0%

Reading state information... 0%

Reading state information... Done

linux-sound-base is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

--------------------------------------------------------------------------------------
-  Package alsa-base will be installed
--------------------------------------------------------------------------------------

Reading package lists... 0%

Reading package lists... 100%

Reading package lists... Done


Building dependency tree... 0%

Building dependency tree... 0%

Building dependency tree... 50%

Building dependency tree... 50%

Building dependency tree       


Reading state information... 0%

Reading state information... 0%

Reading state information... Done

alsa-base is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

--------------------------------------------------------------------------------------
-  Package alsa-utils will be installed
--------------------------------------------------------------------------------------

Reading package lists... 0%

Reading package lists... 100%

Reading package lists... Done


Building dependency tree... 0%

Building dependency tree... 0%

Building dependency tree... 50%

Building dependency tree... 50%

Building dependency tree       


Reading state information... 0%

Reading state information... 0%

Reading state information... Done

alsa-utils is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

--------------------------------------------------------------------------------------
-  Package libasound2 will be installed
--------------------------------------------------------------------------------------

Reading package lists... 0%

Reading package lists... 100%

Reading package lists... Done


Building dependency tree... 0%

Building dependency tree... 0%

Building dependency tree... 50%

Building dependency tree... 50%

Building dependency tree       


Reading state information... 0%

Reading state information... 0%

Reading state information... Done

libasound2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

--------------------------------------------------------------------------------------
-  Package alsa-firmware will be installed
--------------------------------------------------------------------------------------

Reading package lists... 0%

Reading package lists... 100%

Reading package lists... Done


Building dependency tree... 0%

Building dependency tree... 0%

Building dependency tree... 50%

Building dependency tree... 50%

Building dependency tree       


Reading state information... 0%

Reading state information... 0%

Reading state information... Done

The following NEW packages will be installed:
  alsa-firmware
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 3,310kB of archives.
After this operation, 8,176kB of additional disk space will be used.


0% [Working]
            
Get:1 http://packages.medibuntu.org karmic/non-free alsa-firmware 1.0.17-0medibuntu2.9.10.1 [3,310kB]

            
0% [1 alsa-firmware 1272/3,310kB 0%]
                                    
9% [1 alsa-firmware 305112/3,310kB 9%]
                                      
18% [1 alsa-firmware 617592/3,310kB 18%]
                                        
33% [1 alsa-firmware 1099992/3,310kB 33%]
45% [1 alsa-firmware 1521912/3,310kB 45%]
56% [1 alsa-firmware 1854552/3,310kB 56%]
68% [1 alsa-firmware 2275032/3,310kB 68%]
81% [1 alsa-firmware 2688312/3,310kB 81%]
94% [1 alsa-firmware 3120312/3,310kB 94%]
                                         
100% [Working]
              
Fetched 3,310kB in 4s (751kB/s)
Selecting previously deselected package alsa-firmware.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 180787 files and directories currently installed.)
Unpacking alsa-firmware (from .../alsa-firmware_1.0.17-0medibuntu2.9.10.1_i386.deb) ...
Setting up alsa-firmware (1.0.17-0medibuntu2.9.10.1) ...

--------------------------------------------------------------------------------------
-  Package alsa-firmware-loaders will be installed
--------------------------------------------------------------------------------------

Reading package lists... 0%

Reading package lists... 0%

Reading package lists... 6%

Reading package lists... Done


Building dependency tree... 0%

Building dependency tree... 0%

Building dependency tree... 50%

Building dependency tree... 50%

Building dependency tree... 54%

Building dependency tree       


Reading state information... 0%

Reading state information... 0%

Reading state information... Done

alsa-firmware-loaders is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

--------------------------------------------------------------------------------------
-  Package alsa-oss will be installed
--------------------------------------------------------------------------------------

Reading package lists... 0%

Reading package lists... 100%

Reading package lists... Done


Building dependency tree... 0%

Building dependency tree... 0%

Building dependency tree... 50%

Building dependency tree... 50%

Building dependency tree       


Reading state information... 0%

Reading state information... 0%

Reading state information... Done

alsa-oss is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

--------------------------------------------------------------------------------------
-  Package alsa-tools will be installed
--------------------------------------------------------------------------------------

Reading package lists... 0%

Reading package lists... 100%

Reading package lists... Done


Building dependency tree... 0%

Building dependency tree... 0%

Building dependency tree... 50%

Building dependency tree... 50%

Building dependency tree       


Reading state information... 0%

Reading state information... 0%

Reading state information... Done

alsa-tools is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

--------------------------------------------------------------------------------------
-  Package alsa-tools-gui will be installed
--------------------------------------------------------------------------------------

Reading package lists... 0%

Reading package lists... 100%

Reading package lists... Done


Building dependency tree... 0%

Building dependency tree... 0%

Building dependency tree... 50%

Building dependency tree... 50%

Building dependency tree       


Reading state information... 0%

Reading state information... 0%

Reading state information... Done

alsa-tools-gui is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

--------------------------------------------------------------------------------------
-  Package libasound2-dev will be installed
--------------------------------------------------------------------------------------

Reading package lists... 0%

Reading package lists... 100%

Reading package lists... Done


Building dependency tree... 0%

Building dependency tree... 0%

Building dependency tree... 50%

Building dependency tree... 50%

Building dependency tree       


Reading state information... 0%

Reading state information... 0%

Reading state information... Done

libasound2-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

--------------------------------------------------------------------------------------
-  Package libasound2-plugins will be installed
--------------------------------------------------------------------------------------

Reading package lists... 0%

Reading package lists... 100%

Reading package lists... Done


Building dependency tree... 0%

Building dependency tree... 0%

Building dependency tree... 50%

Building dependency tree... 50%

Building dependency tree       


Reading state information... 0%

Reading state information... 0%

Reading state information... Done

libasound2-plugins is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

--------------------------------------------------------------------------------------
-  Package aconnectgui will be installed
--------------------------------------------------------------------------------------

Reading package lists... 0%

Reading package lists... 100%

Reading package lists... Done


Building dependency tree... 0%

Building dependency tree... 0%

Building dependency tree... 50%

Building dependency tree... 50%

Building dependency tree       


Reading state information... 0%

Reading state information... 0%

Reading state information... Done

aconnectgui is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

--------------------------------------------------------------------------------------
-  Package alsa-source will be installed
--------------------------------------------------------------------------------------

Reading package lists... 0%

Reading package lists... 100%

Reading package lists... Done


Building dependency tree... 0%

Building dependency tree... 0%

Building dependency tree... 50%

Building dependency tree... 50%

Building dependency tree       


Reading state information... 0%

Reading state information... 0%

Reading state information... Done

alsa-source is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

--------------------------------------------------------------------------------------
-  Installing dependencies
--------------------------------------------------------------------------------------

Reading package lists... 0%

Reading package lists... 100%

Reading package lists... Done


Building dependency tree... 0%

Building dependency tree... 0%

Building dependency tree... 50%

Building dependency tree... 50%

Building dependency tree       


Reading state information... 0%

Reading state information... 0%

Reading state information... Done

bzip2 is already the newest version.
build-essential is already the newest version.
module-assistant is already the newest version.
libsysfs-dev is already the newest version.
libncurses5-dev is already the newest version.
libncursesw5-dev is already the newest version.
gettext is already the newest version.
python-dev is already the newest version.
xmlto is already the newest version.
libpulse0 is already the newest version.
libpulse-dev is already the newest version.
libspeex-dev is already the newest version.
libavcodec-dev is already the newest version.
libavformat-dev is already the newest version.
libavutil-dev is already the newest version.
libavutil-dev set to manually installed.
libmpeg4ip-dev is already the newest version.
liba52-0.7.4-dev is already the newest version.
libsamplerate0-dev is already the newest version.
linux-headers-2.6.31-21-generic is already the newest version.
libfltk1.1-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

--------------------------------------------------------------------------------------
-  Downloading and extracting ALSA packages...
--------------------------------------------------------------------------------------
--2010-05-06 21:42:03--  ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.22.1.tar.bz2
           => `alsa-driver-1.0.22.1.tar.bz2'
Resolving ftp.alsa-project.org... 212.20.107.51
Connecting to ftp.alsa-project.org|212.20.107.51|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/driver ... done.
==> SIZE alsa-driver-1.0.22.1.tar.bz2 ... 3218678
==> PASV ... done.    ==> RETR alsa-driver-1.0.22.1.tar.bz2 ... done.
Length: 3218678 (3.1M)


 0% [                                       ] 0           --.-K/s              
 0% [                                       ] 10,080      45.0K/s              
 1% [                                       ] 33,120      74.6K/s              
 2% [>                                      ] 93,600       140K/s              
 6% [=>                                     ] 195,168      219K/s              
 8% [==>                                    ] 272,160      243K/s              
10% [===>                                   ] 331,200      246K/s              
12% [===>                                   ] 390,240      247K/s              
14% [====>                                  ] 462,240      257K/s              
16% [=====>                                 ] 544,320      268K/s              
19% [======>                                ] 639,360      286K/s              
21% [=======>                               ] 702,720      287K/s              
24% [========>                              ] 784,800      293K/s              
26% [=========>                             ] 866,880      298K/s              
29% [==========>                            ] 951,840      304K/s  eta 7s      
32% [===========>                           ] 1,038,240    309K/s  eta 7s      
35% [============>                          ] 1,128,960    316K/s  eta 7s      
37% [=============>                         ] 1,198,080    335K/s  eta 7s      
39% [==============>                        ] 1,268,640    349K/s  eta 7s      
42% [===============>                       ] 1,356,480    354K/s  eta 6s      
45% [================>                      ] 1,463,040    364K/s  eta 6s      
48% [==================>                    ] 1,573,920    361K/s  eta 6s      
51% [===================>                   ] 1,667,520    376K/s  eta 6s      
54% [====================>                  ] 1,759,680    386K/s  eta 6s      
57% [=====================>                 ] 1,856,160    392K/s  eta 4s      
60% [======================>                ] 1,955,520    391K/s  eta 4s      
63% [=======================>               ] 2,059,200    401K/s  eta 4s      
67% [=========================>             ] 2,167,200    406K/s  eta 4s      
70% [==========================>            ] 2,270,880    412K/s  eta 4s      
73% [===========================>           ] 2,380,320    421K/s  eta 2s      
77% [=============================>         ] 2,491,200    427K/s  eta 2s      
79% [==============================>        ] 2,560,864    421K/s  eta 2s      
82% [==============================>        ] 2,640,960    414K/s  eta 2s      
83% [===============================>       ] 2,697,120    406K/s  eta 2s      
85% [================================>      ] 2,760,480    407K/s  eta 1s      
87% [================================>      ] 2,802,240    391K/s  eta 1s      
88% [=================================>     ] 2,864,160    379K/s  eta 1s      
90% [==================================>    ] 2,918,880    370K/s  eta 1s      
92% [===================================>   ] 2,977,920    358K/s  eta 1s      
94% [===================================>   ] 3,038,400    346K/s  eta 1s      
96% [====================================>  ] 3,096,000    340K/s  eta 1s      
98% [=====================================> ] 3,155,040    328K/s  eta 1s      
99% [=====================================> ] 3,212,640    317K/s  eta 1s      
99% [=====================================> ] 3,215,520    275K/s  eta 0s      
100%[======================================>] 3,218,678    253K/s  eta 0s      
100%[======================================>] 3,218,678    253K/s   in 9.9s    

2010-05-06 21:42:15 (318 KB/s) - `alsa-driver-1.0.22.1.tar.bz2' saved [3218678]

--2010-05-06 21:42:17--  ftp://ftp.alsa-project.org/pub/firmware/alsa-firmware-1.0.20.tar.bz2
           => `alsa-firmware-1.0.20.tar.bz2'
Resolving ftp.alsa-project.org... 212.20.107.51
Connecting to ftp.alsa-project.org|212.20.107.51|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/firmware ... done.
==> SIZE alsa-firmware-1.0.20.tar.bz2 ... 3750774
==> PASV ... done.    ==> RETR alsa-firmware-1.0.20.tar.bz2 ... done.
Length: 3750774 (3.6M)


 0% [                                       ] 0           --.-K/s              
 0% [                                       ] 10,080      45.8K/s              
 0% [                                       ] 33,120      75.2K/s              
 2% [                                       ] 93,600       141K/s              
 5% [=>                                     ] 195,168      220K/s              
 7% [=>                                     ] 270,720      241K/s              
 8% [==>                                    ] 332,640      247K/s              
10% [===>                                   ] 387,360      247K/s              
12% [===>                                   ] 472,320      262K/s              
15% [====>                                  ] 573,120      279K/s              
18% [======>                                ] 675,360      292K/s              
20% [======>                                ] 756,000      298K/s              
22% [=======>                               ] 839,520      304K/s              
24% [========>                              ] 924,480      309K/s              
26% [=========>                             ] 1,010,880    314K/s  eta 9s      
29% [==========>                            ] 1,118,880    322K/s  eta 9s      
32% [===========>                           ] 1,228,320    330K/s  eta 9s      
35% [============>                          ] 1,337,760    369K/s  eta 9s      
38% [=============>                         ] 1,432,800    377K/s  eta 9s      
40% [==============>                        ] 1,520,640    386K/s  eta 6s      
43% [===============>                       ] 1,618,560    382K/s  eta 6s      
45% [================>                      ] 1,717,920    397K/s  eta 6s      
48% [=================>                     ] 1,818,720    404K/s  eta 6s      
51% [===================>                   ] 1,923,840    413K/s  eta 6s      
53% [===================>                   ] 1,992,064    402K/s  eta 5s      
55% [====================>                  ] 2,070,720    393K/s  eta 5s      
56% [=====================>                 ] 2,119,680    386K/s  eta 5s      
57% [=====================>                 ] 2,165,760    381K/s  eta 5s      
59% [======================>                ] 2,221,920    368K/s  eta 5s      
60% [======================>                ] 2,279,520    362K/s  eta 4s      
62% [=======================>               ] 2,341,440    349K/s  eta 4s      
64% [=======================>               ] 2,401,920    344K/s  eta 4s      
65% [========================>              ] 2,475,360    335K/s  eta 4s      
67% [=========================>             ] 2,531,520    322K/s  eta 4s      
69% [=========================>             ] 2,592,000    310K/s  eta 3s      
70% [==========================>            ] 2,651,040    305K/s  eta 3s      
72% [===========================>           ] 2,721,600    299K/s  eta 3s      
74% [============================>          ] 2,796,480    295K/s  eta 3s      
76% [============================>          ] 2,861,280    288K/s  eta 3s      
78% [=============================>         ] 2,942,464    273K/s  eta 2s      
80% [==============================>        ] 3,008,160    280K/s  eta 2s      
81% [==============================>        ] 3,044,160    261K/s  eta 2s      
82% [===============================>       ] 3,083,040    257K/s  eta 2s      
83% [===============================>       ] 3,114,720    258K/s  eta 2s      
84% [===============================>       ] 3,156,480    250K/s  eta 2s      
85% [================================>      ] 3,199,680    251K/s  eta 2s      
86% [================================>      ] 3,245,760    245K/s  eta 2s      
87% [=================================>     ] 3,299,040    245K/s  eta 2s      
89% [=================================>     ] 3,353,760    240K/s  eta 2s      
90% [==================================>    ] 3,401,280    240K/s  eta 1s      
92% [==================================>    ] 3,458,880    237K/s  eta 1s      
94% [===================================>   ] 3,526,560    240K/s  eta 1s      
95% [====================================>  ] 3,591,360    240K/s  eta 1s      
97% [====================================>  ] 3,651,840    234K/s  eta 1s      
98% [=====================================> ] 3,710,880    235K/s  eta 0s      
100%[======================================>] 3,750,774    235K/s   in 12s     

2010-05-06 21:42:31 (297 KB/s) - `alsa-firmware-1.0.20.tar.bz2' saved [3750774]

--2010-05-06 21:42:33--  ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.22.tar.bz2
           => `alsa-lib-1.0.22.tar.bz2'
Resolving ftp.alsa-project.org... 212.20.107.51
Connecting to ftp.alsa-project.org|212.20.107.51|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/lib ... done.
==> SIZE alsa-lib-1.0.22.tar.bz2 ... 808534
==> PASV ... done.    ==> RETR alsa-lib-1.0.22.tar.bz2 ... done.
Length: 808534 (790K)


 0% [                                       ] 0           --.-K/s              
 1% [                                       ] 10,080      45.6K/s              
 4% [>                                      ] 33,120      75.1K/s              
11% [===>                                   ] 93,600       141K/s              
24% [========>                              ] 195,168      218K/s              
33% [===========>                           ] 267,840      240K/s              
44% [================>                      ] 357,184      263K/s              
52% [===================>                   ] 420,544      266K/s              
60% [======================>                ] 488,224      271K/s              
69% [==========================>            ] 561,664      280K/s              
80% [==============================>        ] 650,944      287K/s              
89% [=================================>     ] 724,384      289K/s              
95% [====================================>  ] 769,024      281K/s              
99% [=====================================> ] 803,584      268K/s              
99% [=====================================> ] 807,904      251K/s  eta 0s      
100%[======================================>] 808,534      243K/s   in 3.3s    

2010-05-06 21:42:38 (243 KB/s) - `alsa-lib-1.0.22.tar.bz2' saved [808534]

--2010-05-06 21:42:39--  ftp://ftp.alsa-project.org/pub/plugins/alsa-plugins-1.0.22.tar.bz2
           => `alsa-plugins-1.0.22.tar.bz2'
Resolving ftp.alsa-project.org... 212.20.107.51
Connecting to ftp.alsa-project.org|212.20.107.51|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/plugins ... done.
==> SIZE alsa-plugins-1.0.22.tar.bz2 ... 326266
==> PASV ... done.    ==> RETR alsa-plugins-1.0.22.tar.bz2 ... done.
Length: 326266 (319K)


 0% [                                       ] 0           --.-K/s              
 3% [>                                      ] 10,080      45.7K/s              
10% [==>                                    ] 33,120      74.9K/s              
28% [==========>                            ] 93,600       140K/s              
59% [======================>                ] 195,168      219K/s              
83% [===============================>       ] 272,160      244K/s              
100%[======================================>] 326,266      273K/s   in 1.2s    

2010-05-06 21:42:42 (273 KB/s) - `alsa-plugins-1.0.22.tar.bz2' saved [326266]

alsa-plugins-1.0.22/
alsa-plugins-1.0.22/depcomp
alsa-plugins-1.0.22/usb_stream/
alsa-plugins-1.0.22/usb_stream/Makefile.in
alsa-plugins-1.0.22/usb_stream/pcm_usb_stream.c
alsa-plugins-1.0.22/usb_stream/Makefile.am
alsa-plugins-1.0.22/usb_stream/usb_stream.h
alsa-plugins-1.0.22/ltconfig
alsa-plugins-1.0.22/COPYING.GPL
alsa-plugins-1.0.22/ltmain.sh
alsa-plugins-1.0.22/acinclude.m4
alsa-plugins-1.0.22/configure.in
alsa-plugins-1.0.22/jack/
alsa-plugins-1.0.22/jack/Makefile.in
alsa-plugins-1.0.22/jack/pcm_jack.c
alsa-plugins-1.0.22/jack/Makefile.am
alsa-plugins-1.0.22/oss/
alsa-plugins-1.0.22/oss/pcm_oss.c
alsa-plugins-1.0.22/oss/Makefile.in
alsa-plugins-1.0.22/oss/ctl_oss.c
alsa-plugins-1.0.22/oss/Makefile.am
alsa-plugins-1.0.22/pulse/
alsa-plugins-1.0.22/pulse/pulse.c
alsa-plugins-1.0.22/pulse/Makefile.in
alsa-plugins-1.0.22/pulse/ctl_pulse.c
alsa-plugins-1.0.22/pulse/conf_pulse.c
alsa-plugins-1.0.22/pulse/pcm_pulse.c
alsa-plugins-1.0.22/pulse/Makefile.am
alsa-plugins-1.0.22/pulse/pulse.h
alsa-plugins-1.0.22/maemo/
alsa-plugins-1.0.22/maemo/types.h
alsa-plugins-1.0.22/maemo/reporting.h
alsa-plugins-1.0.22/maemo/dsp-protocol.c
alsa-plugins-1.0.22/maemo/dsp-protocol.h
alsa-plugins-1.0.22/maemo/Makefile.in
alsa-plugins-1.0.22/maemo/Makefile.am
alsa-plugins-1.0.22/maemo/constants.h
alsa-plugins-1.0.22/maemo/dsp-ctl.c
alsa-plugins-1.0.22/maemo/debug.h
alsa-plugins-1.0.22/maemo/alsa-dsp.c
alsa-plugins-1.0.22/maemo/list.h
alsa-plugins-1.0.22/arcam-av/
alsa-plugins-1.0.22/arcam-av/Makefile.in
alsa-plugins-1.0.22/arcam-av/arcam_av.h
alsa-plugins-1.0.22/arcam-av/Makefile.am
alsa-plugins-1.0.22/arcam-av/ctl_arcam_av.c
alsa-plugins-1.0.22/arcam-av/arcam_av.c
alsa-plugins-1.0.22/mix/
alsa-plugins-1.0.22/mix/pcm_upmix.c
alsa-plugins-1.0.22/mix/Makefile.in
alsa-plugins-1.0.22/mix/Makefile.am
alsa-plugins-1.0.22/mix/pcm_vdownmix.c
alsa-plugins-1.0.22/configure
alsa-plugins-1.0.22/Makefile.in
alsa-plugins-1.0.22/rate-lavc/
alsa-plugins-1.0.22/rate-lavc/gcd.h
alsa-plugins-1.0.22/rate-lavc/Makefile.in
alsa-plugins-1.0.22/rate-lavc/rate_lavcrate.c
alsa-plugins-1.0.22/rate-lavc/Makefile.am
alsa-plugins-1.0.22/version
alsa-plugins-1.0.22/rate/
alsa-plugins-1.0.22/rate/Makefile.in
alsa-plugins-1.0.22/rate/Makefile.am
alsa-plugins-1.0.22/rate/rate_samplerate.c
alsa-plugins-1.0.22/doc/
alsa-plugins-1.0.22/doc/lavcrate.txt
alsa-plugins-1.0.22/doc/upmix.txt
alsa-plugins-1.0.22/doc/README-jack
alsa-plugins-1.0.22/doc/speexrate.txt
alsa-plugins-1.0.22/doc/a52.txt
alsa-plugins-1.0.22/doc/Makefile.in
alsa-plugins-1.0.22/doc/README-pcm-oss
alsa-plugins-1.0.22/doc/README-pulse
alsa-plugins-1.0.22/doc/README-maemo
alsa-plugins-1.0.22/doc/samplerate.txt
alsa-plugins-1.0.22/doc/Makefile.am
alsa-plugins-1.0.22/doc/speexdsp.txt
alsa-plugins-1.0.22/doc/README-arcam-av
alsa-plugins-1.0.22/doc/vdownmix.txt
alsa-plugins-1.0.22/config.guess
alsa-plugins-1.0.22/m4/
alsa-plugins-1.0.22/m4/attributes.m4
alsa-plugins-1.0.22/speex/
alsa-plugins-1.0.22/speex/pcm_speex.c
alsa-plugins-1.0.22/speex/Makefile.in
alsa-plugins-1.0.22/speex/Makefile.am
alsa-plugins-1.0.22/gitcompile
alsa-plugins-1.0.22/Makefile.am
alsa-plugins-1.0.22/a52/
alsa-plugins-1.0.22/a52/Makefile.in
alsa-plugins-1.0.22/a52/Makefile.am
alsa-plugins-1.0.22/a52/pcm_a52.c
alsa-plugins-1.0.22/config.h.in
alsa-plugins-1.0.22/aclocal.m4
alsa-plugins-1.0.22/COPYING
alsa-plugins-1.0.22/missing
alsa-plugins-1.0.22/install-sh
alsa-plugins-1.0.22/pph/
alsa-plugins-1.0.22/pph/Makefile.in
alsa-plugins-1.0.22/pph/fixed_generic.h
alsa-plugins-1.0.22/pph/speex_resampler.h
alsa-plugins-1.0.22/pph/Makefile.am
alsa-plugins-1.0.22/pph/rate_speexrate.c
alsa-plugins-1.0.22/pph/arch.h
alsa-plugins-1.0.22/pph/resample.c
alsa-plugins-1.0.22/config.sub
--2010-05-06 21:42:42--  ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.22.tar.bz2
           => `alsa-utils-1.0.22.tar.bz2'
Resolving ftp.alsa-project.org... 212.20.107.51
Connecting to ftp.alsa-project.org|212.20.107.51|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/utils ... done.
==> SIZE alsa-utils-1.0.22.tar.bz2 ... 1075216
==> PASV ... done.    ==> RETR alsa-utils-1.0.22.tar.bz2 ... done.
Length: 1075216 (1.0M)


 0% [                                       ] 0           --.-K/s              
 0% [                                       ] 10,080      45.9K/s              
 3% [>                                      ] 33,120      75.0K/s              
 8% [==>                                    ] 93,600       141K/s              
18% [======>                                ] 195,168      220K/s              
25% [========>                              ] 273,600      246K/s              
32% [===========>                           ] 344,160      261K/s              
35% [============>                          ] 384,480      249K/s              
42% [===============>                       ] 462,240      260K/s              
50% [==================>                    ] 545,760      271K/s              
59% [======================>                ] 642,240      283K/s              
68% [=========================>             ] 740,160      293K/s              
78% [=============================>         ] 839,520      303K/s              
85% [================================>      ] 914,400      305K/s              
92% [===================================>   ] 995,040      309K/s  eta 0s      
98% [=====================================> ] 1,061,280    303K/s  eta 0s      
100%[======================================>] 1,075,216    296K/s   in 3.6s    

2010-05-06 21:42:47 (296 KB/s) - `alsa-utils-1.0.22.tar.bz2' saved [1075216]

--2010-05-06 21:42:48--  ftp://ftp.alsa-project.org/pub/tools/alsa-tools-1.0.22.tar.bz2
           => `alsa-tools-1.0.22.tar.bz2'
Resolving ftp.alsa-project.org... 212.20.107.51
Connecting to ftp.alsa-project.org|212.20.107.51|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/tools ... done.
==> SIZE alsa-tools-1.0.22.tar.bz2 ... 1555768
==> PASV ... done.    ==> RETR alsa-tools-1.0.22.tar.bz2 ... done.
Length: 1555768 (1.5M)


 0% [                                       ] 0           --.-K/s              
 0% [                                       ] 10,080      45.6K/s              
 2% [                                       ] 33,120      75.5K/s              
 6% [=>                                     ] 93,600       141K/s              
12% [===>                                   ] 195,168      219K/s              
17% [=====>                                 ] 270,720      244K/s              
23% [========>                              ] 360,000      273K/s              
27% [=========>                             ] 429,120      282K/s              
30% [===========>                           ] 479,520      278K/s              
35% [=============>                         ] 558,720      285K/s              
40% [==============>                        ] 635,040      290K/s              
46% [=================>                     ] 730,080      298K/s              
48% [=================>                     ] 747,904      277K/s              
55% [====================>                  ] 856,800      290K/s              
56% [=====================>                 ] 885,600      279K/s  eta 2s      
58% [=====================>                 ] 911,520      268K/s  eta 2s      
60% [======================>                ] 944,640      260K/s  eta 2s      
62% [=======================>               ] 976,320      254K/s  eta 2s      
65% [========================>              ] 1,013,760    248K/s  eta 2s      
67% [=========================>             ] 1,046,880    262K/s  eta 2s      
69% [==========================>            ] 1,085,760    253K/s  eta 2s      
72% [===========================>           ] 1,130,400    248K/s  eta 2s      
75% [============================>          ] 1,167,840    219K/s  eta 2s      
77% [=============================>         ] 1,206,720    215K/s  eta 2s      
80% [==============================>        ] 1,251,360    210K/s  eta 1s      
83% [===============================>       ] 1,297,440    202K/s  eta 1s      
86% [================================>      ] 1,350,720    196K/s  eta 1s      
89% [=================================>     ] 1,395,360    194K/s  eta 1s      
92% [===================================>   ] 1,441,440    191K/s  eta 1s      
96% [====================================>  ] 1,497,600    174K/s  eta 0s      
99% [=====================================> ] 1,546,560    180K/s  eta 0s      
100%[======================================>] 1,555,768    182K/s   in 6.6s    

2010-05-06 21:42:56 (229 KB/s) - `alsa-tools-1.0.22.tar.bz2' saved [1555768]

--2010-05-06 21:42:57--  ftp://ftp.alsa-project.org/pub/oss-lib/alsa-oss-1.0.17.tar.bz2
           => `alsa-oss-1.0.17.tar.bz2'
Resolving ftp.alsa-project.org... 212.20.107.51
Connecting to ftp.alsa-project.org|212.20.107.51|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/oss-lib ... done.
==> SIZE alsa-oss-1.0.17.tar.bz2 ... 248726
==> PASV ... done.    ==> RETR alsa-oss-1.0.17.tar.bz2 ... done.
Length: 248726 (243K)


 0% [                                       ] 0           --.-K/s              
 4% [>                                      ] 10,080      45.8K/s              
13% [====>                                  ] 33,120      75.6K/s              
34% [============>                          ] 84,960       129K/s              
68% [=========================>             ] 171,360      195K/s              
100%[======================================>] 248,726      234K/s   in 1.0s    

2010-05-06 21:42:59 (234 KB/s) - `alsa-oss-1.0.17.tar.bz2' saved [248726]

alsa-oss-1.0.17/
alsa-oss-1.0.17/depcomp
alsa-oss-1.0.17/compile
alsa-oss-1.0.17/ltmain.sh
alsa-oss-1.0.17/configure.in
alsa-oss-1.0.17/oss-redir/
alsa-oss-1.0.17/oss-redir/Makefile.in
alsa-oss-1.0.17/oss-redir/oss-redir.h
alsa-oss-1.0.17/oss-redir/README
alsa-oss-1.0.17/oss-redir/Makefile.am
alsa-oss-1.0.17/oss-redir/oss-redir.c
alsa-oss-1.0.17/configure
alsa-oss-1.0.17/Makefile.in
alsa-oss-1.0.17/test/
alsa-oss-1.0.17/test/Makefile.in
alsa-oss-1.0.17/test/testaoss.in
alsa-oss-1.0.17/test/osstest.c
alsa-oss-1.0.17/test/lmixer.cc
alsa-oss-1.0.17/test/mixctl.h
alsa-oss-1.0.17/test/Makefile.am
alsa-oss-1.0.17/config.guess
alsa-oss-1.0.17/alsa/
alsa-oss-1.0.17/alsa/alsa-local.h
alsa-oss-1.0.17/alsa/pcm.c
alsa-oss-1.0.17/alsa/Makefile.in
alsa-oss-1.0.17/alsa/testaoss.in
alsa-oss-1.0.17/alsa/mixer.c
alsa-oss-1.0.17/alsa/aoss.in
alsa-oss-1.0.17/alsa/alsa-oss-emul.h
alsa-oss-1.0.17/alsa/Makefile.am
alsa-oss-1.0.17/alsa/aoss.1
alsa-oss-1.0.17/alsa/aoss.old.in
alsa-oss-1.0.17/alsa/stdioemu.c
alsa-oss-1.0.17/alsa/alsa-oss.c
alsa-oss-1.0.17/Makefile.am
alsa-oss-1.0.17/aclocal.m4
alsa-oss-1.0.17/COPYING
alsa-oss-1.0.17/missing
alsa-oss-1.0.17/install-sh
alsa-oss-1.0.17/config.sub

--------------------------------------------------------------------------------------
-  Alsa packages sucessfully downloaded - run compilation -c next
--------------------------------------------------------------------------------------

Script done on Thu 06 May 2010 09:43:00 PM CEST
```

---

### Post by vtdr on 2010-05-06
Hi lidex,

I am going to go bed... thank you for your attention and see you tomorrow!

vtdr

---

### Post by lidex on 2010-05-06
Did it finish? Let's see these again:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```

---

### Post by vtdr on 2010-05-06
```
~$ uname -a
Linux cris-laptop 2.6.31-21-generic #59-Ubuntu SMP Wed Mar 24 07:28:56 UTC 2010 i686 GNU/Linux

~$ aplay -l
aplay: device_list:223: no soundcards found...

~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.22.1.
Compiled on May  6 2010 for kernel 2.6.31-21-generic (SMP).

~$ head -n 1 /proc/asound/cards
--- no soundcards ---


```

Thank you very much lidex, now I just have to go, my wife is going angry... see you tomorrow...

vtdr

---

### Post by lidex on 2010-05-06
> **vtdr said:**
> ```
~$ uname -a
Linux cris-laptop 2.6.31-21-generic #59-Ubuntu SMP Wed Mar 24 07:28:56 UTC 2010 i686 GNU/Linux

~$ aplay -l
aplay: device_list:223: no soundcards found...

~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.22.1.
Compiled on May  6 2010 for kernel 2.6.31-21-generic (SMP).

~$ head -n 1 /proc/asound/cards
--- no soundcards ---


```

Thank you very much lidex, now I just have to go, my wife is going angry... see you tomorrow...

vtdr

Sorry fella... tell her I said hello.

Next todo:
Update your kernel:
```
sudo apt-get update
sudo apt-get upgrade
```
Now reboot so we can work with the latest kernel and do the alsa upgrade script again.

---

### Post by vtdr on 2010-05-07
Hi lidex,

I'm going to work, I'll be back here in about 12 hours...

vtdr

---

### Post by vtdr on 2010-05-07
Hi lidex!
I did this: 

> Next todo:
Update your kernel:
Code:
sudo apt-get update
sudo apt-get upgrade
Now reboot so we can work with the latest kernel and do the alsa upgrade script again.

Now something has changed, alsamixer has different columns and recognizes my sound card, but no sound at all... I think I need you to better configure it... Here it is what you asked me before:

```
uname -a
Linux cris-laptop 2.6.31-21-generic #59-Ubuntu SMP Wed Mar 24 07:28:56 UTC 2010 i686 GNU/Linux

~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: Modem [ATI IXP Modem], device 0: ATI IXP MC97 [ATI IXP MC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.22.1.
Compiled on May  7 2010 for kernel 2.6.31-21-generic (SMP).

~$ head -n 1 /proc/asound/cards
 0 [IXP            ]: ATIIXP - ATI IXP

~$ head -n 1 /proc/asound/card0/codec97#0/ac97#0-0
0-0/0: Realtek ALC250 rev 2


```

And alsamixer:

[ATTACH]155938[/ATTACH]

[ATTACH]155939[/ATTACH]

I'm waiting for your piece of knowledge...!

vtdr

---

### Post by vtdr on 2010-05-07
Oh no... In my country is 00:35 am... I'm sorry, but I have to go to bed...

Thank you fella and see you tomorrow morning!

vtdr

---

### Post by lidex on 2010-05-07
In alsamixer, when you see MM, that means the element is muted. Select the element and press M to unmute. Also try gnome-alsamixer and enable items in 'Edit>Soundcard Properties'.

---

### Post by vtdr on 2010-05-08
All items in gnome-alsamixer enabled, I played with the sliders in alsamixer but nothing has changed: no sound... Now, headphones are muted too and they don't show themselves in 'Sound Preferences>Output>Connector' ...

---

### Post by vtdr on 2010-05-08
This should help your job: I removed 'options snd-atiixp ac97_quirk=swap_hp' from 'alsa-base.conf', rebooted, HP work...
Take a look at this image:
[ATTACH]155997[/ATTACH]
'Master' & 'PCM' sliders control HP volume and mute them, 'Headphones' slider does nothing but if I mute it, HP mute themselves.

---

### Post by lidex on 2010-05-08
I should have told you to remove that once found it didn't help. My mistake. You should maybe try it as:
```
options snd-atiixp ac97_quirk=none
```

---

### Post by vtdr on 2010-05-08
> I should have told you to remove that once found it didn't help. My mistake. You should maybe try it as:
Code:
options snd-atiixp ac97_quirk=none
__________________

Now HP play when 'Sound Preferences>Output>Connector>Analog Output / Amplifier' is selected too and not only when 'Sound Preferences>Output>Connector>Analog Headphones / Amplifier' is selected...

In alsamixer, the situation is this:

 > 'Master' & 'PCM' sliders control HP volume and mute them, 'Headphones' slider does nothing but if I mute it, HP mute themselves.

I just tried minutes ago with Skype, microphone works great...

These damned internal speakers don't run only...!](*,)

---

### Post by lidex on 2010-05-08
Try this one then:
```
options snd-atiixp ac97_quirk=default
```

Look in gnome-alsamixer for jack sense options

---

### Post by vtdr on 2010-05-08
> Try this one then:
Code:
options snd-atiixp ac97_quirk=default
Look in gnome-alsamixer for jack sense options

Take a look at:

[ATTACH]156001[/ATTACH]

> 'Master' & 'PCM' sliders control HP volume and mute them, 'Headphones' slider does nothing but if I mute it, HP mute themselves

That's all...

---

### Post by vtdr on 2010-05-08
Wow!!! Suddenly the sound has returned!!!
Now I try to reboot, just to be sure before marking thread as 'SOLVED'...

Stay tuned...

---

### Post by vtdr on 2010-05-08
Yes!!!
It'all right! HP works, I unplug them and internal speakers work, microphone work...:p:p:p

lidex, you are a genius...

THANK YOU, THANK YOU, THANK YOU VERY MUCH!!!

Best personal regards,

vtdr

---

### Post by lidex on 2010-05-08
You're welcome!

---

### Post by nsznaj on 2012-02-18
Hi I had this same problem, though i can't follow the steps they had done here to solve my sound.....

could anyone help me get through it?

---

### Post by PirateChef on 2012-03-30
Yep, me too. I'm not sure if mine is exactly the same problem: plugging in my headphones causes the sound to mute. I can un-mute it from the control panel, but it also cuts out again if the volume is too loud! (Can't test internal speakers because I don't have any.)
I'll post back if I discover anything useful.

> **nsznaj said:**
> Hi I had this same problem, though i can't follow the steps they had done here to solve my sound.....

could anyone help me get through it?

---

