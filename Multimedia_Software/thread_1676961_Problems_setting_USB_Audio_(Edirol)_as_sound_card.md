---
title: "Problems setting USB Audio (Edirol) as sound card"
date: 2011-01-28
forum: Multimedia Software
---

### Post by Michl on 2011-01-28
I am trying use an Edirol PCR-1 as the playback sound card and am having no luck.  (It works in Windoze XP without a hitch.)  I have tried everything I can find here and by googling, but nothing works.  The driver for it is snd-usb-audio and I have added the appropriate lines in /etc/modules and the alsa-base conf file.  I have set it as the default card with asoundconf, where it shows up.  It shows up with lsusb both as midi and wav.  But not matter what I do, it never shows up in aplay -l. This is on a Dell C610 laptop, which I use to test speakers, and I am stuck having to use MS for this.  There has to be a way to get it working...  Maybe someone can help.

---

### Post by Michl on 2011-01-28
Maybe someone could explain this:  why can I set it as the default sound card with asoundconfig, but after rebooting, it is not the default sound card and does not show up in aplay -l, even though asoundconfig shows it as the default card.

---

### Post by lidex on 2011-01-29
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by Michl on 2011-01-31
> **lidex said:**
> Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

Thank you so much for pointing out how to get to the Terminal! 

If you have some specific knowledge about this particular issue that might help, please ask a specific question.  Which specific files and lines  would you like to see?

---

### Post by lidex on 2011-01-31
> **Michl said:**
> Thank you so much for pointing out how to get to the Terminal! 

If you have some specific knowledge about this particular issue that might help, please ask a specific question.  Which specific files and lines  would you like to see?

The output of that script.

---

### Post by Michl on 2011-01-31
```

upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Tue Feb  1 03:43:02 UTC 2011


!!Linux Distribution
!!------------------

Ubuntu 9.04 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 9.04"


!!DMI Information
!!---------------

Manufacturer:      Dell Computer Corporation
Product Name:      Latitude C610                   
Product Version:   


!!Kernel Information
!!------------------

Kernel release:    2.6.28-19-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.18rc3
Library version:    1.0.23
Utilities version:  1.0.23


!!Loaded ALSA modules
!!-------------------

snd_usb_audio
snd_intel8x0


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No

Jack:
      Installed - Yes (/usr/bin/jackd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [PCR1           ]: USB-Audio - PCR-1
                      EDIROL PCR-1 at usb-0000:00:1d.0-1.1, full speed
 1 [I82801CAICH3   ]: ICH - Intel 82801CA-ICH3
                      Intel 82801CA-ICH3 with CS4205 at irq 5


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

00:1f.5 0401: 8086:2485 (rev 02)
	Subsystem: 1013:5959


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-usb-caiaq: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-usb-audio: index=0
snd-intel8x0: index=1


!!Loaded sound module options
!!--------------------------

!!Module: snd_usb_audio
	async_unlink : Y
	device_setup : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
	ignore_ctl_error : N
	index : 0,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	nrpacks : 8
	pid : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	vid : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1

!!Module: snd_intel8x0
	ac97_clock : 0
	ac97_quirk : <NULL>
	buggy_irq : N
	buggy_semaphore : N
	enable : N
	id : <NULL>
	index : 1
	joystick : 0
	spdif_aclink : 0
	xbox : N


!!AC97 Codec information
!!---------------------------
--startcollapse--

0-0/0: Cirrus Logic CS4205 rev 3

PCI Subsys Vendor: 0x1013
PCI Subsys Device: 0x5959

Capabilities     : -dedicated MIC PCM IN channel- -bass & treble- -simulated stereo- -loudness-
DAC resolution   : 20-bit
ADC resolution   : 18-bit
3D enhancement   : SRS 3D Stereo Enhancement

Current setup
Mic gain         : +0dB [+0dB]
POP path         : pre 3D
Sim. stereo      : off
3D enhancement   : off
Loudness         : off
Mono output      : MIX
Mic select       : Mic1
ADC/DAC loopback : off
Extended ID      : codec=0 rev=0 AMAP DSA=0 VRM VRA
Extended status  : MADC VRM VRA
PCM front DAC    : 44100Hz
PCM ADC          : 44100Hz
PCM MIC ADC      : 48000Hz
SPDIF Control    : Consumer PCM Category=0x2 Generation=1 Rate=44.1kHz Enabled

0:00 = 25ad
0:02 = 0f0f
0:04 = 0000
0:06 = 0006
0:08 = 0f0f
0:0a = 000e
0:0c = 0000
0:0e = 801f
0:10 = 0000
0:12 = 0606
0:14 = 0303
0:16 = 0000
0:18 = 0606
0:1a = 0000
0:1c = 0f0f
0:1e = 0000
0:20 = 0000
0:22 = 0000
0:24 = 0000
0:26 = 000f
0:28 = 0209
0:2a = 0209
0:2c = ac44
0:2e = 0000
0:30 = 0000
0:32 = ac44
0:34 = bb80
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
0:4c = 001f
0:4e = ffff
0:50 = 0000
0:52 = 0000
0:54 = 0000
0:56 = ffff
0:58 = 0000
0:5a = 0302
0:5c = 0000
0:5e = 0082
0:60 = 0003
0:62 = 0000
0:64 = 0000
0:66 = 0000
0:68 = 9824
0:6a = 0000
0:6c = 0000
0:6e = 8000
0:70 = 0000
0:72 = 0000
0:74 = 0000
0:76 = 0000
0:78 = 0077
0:7a = 0000
0:7c = 4352
0:7e = 595b
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116, 5 Jan 31 20:37 /dev/snd/controlC0
crw-rw----+ 1 root audio 116, 9 Jan 31 20:37 /dev/snd/controlC1
crw-rw----+ 1 root audio 116, 4 Jan 31 20:37 /dev/snd/midiC0D0
crw-rw----+ 1 root audio 116, 8 Jan 31 20:38 /dev/snd/pcmC1D0c
crw-rw----+ 1 root audio 116, 7 Jan 31 20:38 /dev/snd/pcmC1D0p
crw-rw----+ 1 root audio 116, 6 Jan 31 20:37 /dev/snd/pcmC1D1c
crw-rw----+ 1 root audio 116, 3 Jan 31 20:37 /dev/snd/seq
crw-rw----+ 1 root audio 116, 2 Jan 31 20:37 /dev/snd/timer


!!ALSA configuration files
!!------------------------

!!User specific config file (~/.asoundrc)

# ALSA library configuration file

# Include settings that are under the control of asoundconf(1).
# (To disable these settings, comment out this line.)
</home/ml/.asoundrc.asoundconf>
pcm.card0 {
    type hw
    card 0
}
ctl.card0 {
    type hw
    card 0
}



!!asoundconf-generated config file

# ALSA library configuration file managed by asoundconf(1).
#
# MANUAL CHANGES TO THIS FILE WILL BE OVERWRITTEN!
#
# Manual changes to the ALSA library configuration should be implemented
# by editing the ~/.asoundrc file, not by editing this file.
!defaults.pcm.card PCR1
defaults.ctl.card PCR1
defaults.pcm.device 0
defaults.pcm.subdevice -1
defaults.pcm.nonblock 1
defaults.pcm.ipc_key 5678293
defaults.pcm.ipc_gid audio
defaults.pcm.ipc_perm 0660
defaults.pcm.dmix.max_periods 0
defaults.pcm.dmix.rate 48000
defaults.pcm.dmix.format "unchanged"
defaults.pcm.dmix.card defaults.pcm.card
defaults.pcm.dmix.device defaults.pcm.device
defaults.pcm.dsnoop.card defaults.pcm.card
defaults.pcm.dsnoop.device defaults.pcm.device
defaults.pcm.front.card defaults.pcm.card
defaults.pcm.front.device defaults.pcm.device
defaults.pcm.rear.card defaults.pcm.card
defaults.pcm.rear.device defaults.pcm.device
defaults.pcm.center_lfe.card defaults.pcm.card
defaults.pcm.center_lfe.device defaults.pcm.device
defaults.pcm.side.card defaults.pcm.card
defaults.pcm.side.device defaults.pcm.device
defaults.pcm.surround40.card defaults.pcm.card
defaults.pcm.surround40.device defaults.pcm.device
defaults.pcm.surround41.card defaults.pcm.card
defaults.pcm.surround41.device defaults.pcm.device
defaults.pcm.surround50.card defaults.pcm.card
defaults.pcm.surround50.device defaults.pcm.device
defaults.pcm.surround51.card defaults.pcm.card
defaults.pcm.surround51.device defaults.pcm.device
defaults.pcm.surround71.card defaults.pcm.card
defaults.pcm.surround71.device defaults.pcm.device
defaults.pcm.iec958.card defaults.pcm.card
defaults.pcm.iec958.device defaults.pcm.device
defaults.pcm.modem.card defaults.pcm.card
defaults.pcm.modem.device defaults.pcm.device
defaults.pcm.file_format "raw"
defaults.pcm.file_truncate true
defaults.rawmidi.card 0
defaults.rawmidi.device 0
defaults.rawmidi.subdevice -1
defaults.hwdep.card 0
defaults.hwdep.device 0
defaults.timer.class 2
defaults.timer.sclass 0
defaults.timer.card 0
defaults.timer.device 0
defaults.timer.subdevice 0
defaults.namehint.showall off
defaults.namehint.basic on
defaults.namehint.extended off


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 1: I82801CAICH3 [Intel 82801CA-ICH3], device 0: Intel ICH [Intel 82801CA-ICH3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 1: I82801CAICH3 [Intel 82801CA-ICH3], device 0: Intel ICH [Intel 82801CA-ICH3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: I82801CAICH3 [Intel 82801CA-ICH3], device 1: Intel ICH - MIC ADC [Intel 82801CA-ICH3 - MIC ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [PCR1]

Card hw:0 'PCR1'/'EDIROL PCR-1 at usb-0000:00:1d.0-1.1, full speed'
  Mixer name	: ''
  Components	: 'USB0582:0065'
  Controls      : 0
  Simple ctrls  : 0

!!-------Mixer controls for card 1 [I82801CAICH3]

Card hw:1 'I82801CAICH3'/'Intel 82801CA-ICH3 with CS4205 at irq 5'
  Mixer name	: 'Cirrus Logic CS4205 rev 3'
  Components	: 'AC97a:4352595b'
  Controls      : 42
  Simple ctrls  : 27
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 16 [52%] [-22.50dB] [on]
  Front Right: Playback 16 [52%] [-22.50dB] [on]
Simple mixer control 'Master Mono',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 25 [81%] [-9.00dB] [on]
Simple mixer control 'Bass',0
  Capabilities: volume volume-joined penum
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 15
  Mono: 0 [0%]
Simple mixer control 'Treble',0
  Capabilities: volume volume-joined penum
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 15
  Mono: 0 [0%]
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
  Front Left: Playback 25 [81%] [3.00dB] [on]
  Front Right: Playback 25 [81%] [3.00dB] [on]
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
  Front Left: Playback 31 [100%] [12.00dB] [on] Capture [off]
  Front Right: Playback 31 [100%] [12.00dB] [on] Capture [off]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 25 [81%] [3.00dB] [on] Capture [off]
  Front Right: Playback 25 [81%] [3.00dB] [on] Capture [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pvolume-joined cvolume cvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31 Capture 0 - 15
  Mono: Playback 0 [0%] [-34.50dB] [off]
  Front Left: Capture 0 [0%] [0.00dB] [on]
  Front Right: Capture 0 [0%] [0.00dB] [on]
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
  Front Left: Playback 28 [90%] [7.50dB] [on] Capture [off]
  Front Right: Playback 28 [90%] [7.50dB] [on] Capture [off]
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
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958 Playback AC97-SPSA',0
  Capabilities: volume volume-joined penum
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 3
  Mono: 2 [67%]
Simple mixer control 'PC Speaker',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 15
  Mono: Playback 8 [53%] [-21.00dB] [on]
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
  Item0: 'Mix'
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch cswitch-joined penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 15 [100%] [22.50dB] [on]
  Front Right: Capture 15 [100%] [22.50dB] [on]
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
Simple mixer control 'Loudness (bass boost)',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Simulated Stereo Enhancement',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]


!!Alsactl output
!!-------------

--startcollapse--
state.PCR1 {
	control {
	}
}
state.I82801CAICH3 {
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
		comment.range '0 - 31'
		comment.dbmin -4650
		comment.dbmax 0
		iface MIXER
		name 'Master Playback Volume'
		value.0 16
		value.1 16
	}
	control.3 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Master Mono Playback Switch'
		value true
	}
	control.4 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 31'
		comment.dbmin -4650
		comment.dbmax 0
		iface MIXER
		name 'Master Mono Playback Volume'
		value 25
	}
	control.5 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 15'
		iface MIXER
		name 'Tone Control - Bass'
		value 0
	}
	control.6 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 15'
		iface MIXER
		name 'Tone Control - Treble'
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
		value 8
	}
	control.9 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Phone Playback Switch'
		value true
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
		value 31
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
		comment.count 1
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Mic Playback Volume'
		value 0
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
		value true
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
		value.0 31
		value.1 31
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
		value.0 25
		value.1 25
	}
	control.18 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Video Playback Switch'
		value true
	}
	control.19 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Video Playback Volume'
		value.0 28
		value.1 28
	}
	control.20 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Aux Playback Switch'
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
		name 'Aux Playback Volume'
		value.0 31
		value.1 31
	}
	control.22 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'PCM Playback Switch'
		value true
	}
	control.23 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'PCM Playback Volume'
		value.0 25
		value.1 25
	}
	control.24 {
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
	control.25 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Capture Switch'
		value true
	}
	control.26 {
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
	control.27 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Mic Capture Switch'
		value true
	}
	control.28 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 15'
		comment.dbmin 0
		comment.dbmax 2250
		iface MIXER
		name 'Mic Capture Volume'
		value 0
	}
	control.29 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 'pre 3D'
		comment.item.1 'post 3D'
		iface MIXER
		name 'PCM Out Path & Mute'
		value 'pre 3D'
	}
	control.30 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Simulated Stereo Enhancement'
		value false
	}
	control.31 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name '3D Control - Switch'
		value false
	}
	control.32 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Loudness (bass boost)'
		value false
	}
	control.33 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Mix
		comment.item.1 Mic
		iface MIXER
		name 'Mono Output Select'
		value Mix
	}
	control.34 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Mic1
		comment.item.1 Mic2
		iface MIXER
		name 'Mic Select'
		value Mic1
	}
	control.35 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 15'
		iface MIXER
		name '3D Control - Center'
		value 0
	}
	control.36 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 15'
		iface MIXER
		name '3D Control - Depth'
		value 0
	}
	control.37 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Con Mask'
		value '0fff000f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.38 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		value cf00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
	}
	control.39 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Default'
		value '0082000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.40 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Switch'
		value true
	}
	control.41 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 3'
		iface MIXER
		name 'IEC958 Playback AC97-SPSA'
		value 2
	}
	control.42 {
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
binfmt_misc
radeon
drm
bridge
stp
bnep
input_polldev
i8k
lp
orinoco_cs
orinoco
hermes_dld
hermes
pcmcia
snd_intel8x0
snd_usb_audio
snd_pcm_oss
snd_ac97_codec
snd_mixer_oss
ac97_bus
snd_pcm
snd_seq_dummy
snd_usb_lib
snd_seq_oss
snd_hwdep
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
snd_seq
snd_timer
snd_seq_device
ppdev
yenta_socket
rsrc_nonstatic
pcmcia_core
dcdbas
pcspkr
snd
psmouse
iTCO_wdt
iTCO_vendor_support
video
soundcore
snd_page_alloc
serio_raw
shpchp
output
parport_pc
parport
intel_agp
agpgart
3c59x
mii
floppy
fbcon
tileblit
font
bitblit
softcursor


!!ALSA/HDA dmesg
!!------------------

```

---

### Post by lidex on 2011-02-01
Any reason not to update your install from jaunty to something more recent, like maverick? 

```
!!ALSA Version
!!------------

Driver version:     [COLOR="Red"]1.0.18rc3[/COLOR]
Library version:    1.0.23
Utilities version:  1.0.23
```

And how did you get that configuration?

---

### Post by Michl on 2011-02-01
> **lidex said:**
> Any reason not to update your install from jaunty to something more recent, like maverick? 

The C610 is an older laptop and I had trouble installing later versions; I believe that video card in that laptop wasn't supported anymore.  I have both lucid and maverick installed on other desktops, and I could try it there just to see.  But I would like to get it to work on this laptop which I use to test audio equipment.

> 
```
!!ALSA Version
!!------------

Driver version:     [COLOR="Red"]1.0.18rc3[/COLOR]
Library version:    1.0.23
Utilities version:  1.0.23
```

And how did you get that configuration?

I don't know.  I am assuming it came with 9.04 and subsequent updates.

---

### Post by Michl on 2011-02-02
I tried the Edirol on a computer with Lucid (10.04) and Maverick (10.10) with the same results.  I am pretty sure this has nothing to do with the Alsa driver version or release.  This requires some more detailed experience and knowledge about installing USB audio and the driver snd-usb-audio.  Your approach is far too removed from this problem.

One issue that might be relevant is that there are no mixer controls installed for the PCR1 card:
> Card hw:0 'PCR1'/'EDIROL PCR-1 at usb-0000:00:1d.0-1.1, full speed'
  Mixer name	: ''
  Components	: 'USB0582:0065'
  Controls      : 0
  Simple ctrls  : 0


compared to the other card:

> Card hw:1 'I82801CAICH3'/'Intel 82801CA-ICH3 with CS4205 at irq 5'
  Mixer name	: 'Cirrus Logic CS4205 rev 3'
  Components	: 'AC97a:4352595b'
  Controls      : 42
  Simple ctrls  : 27
Simple mixer control 'Master',0


---

### Post by lidex on 2011-02-02
> **Michl said:**
> I tried the Edirol on a computer with Lucid (10.04) and Maverick (10.10) with the same results.  I am pretty sure this has nothing to do with the Alsa driver version or release.  This requires some more detailed experience and knowledge about installing USB audio and the driver snd-usb-audio.  Your approach is far too removed from this problem.

One issue that might be relevant is that there are no mixer controls installed for the PCR1 card:


compared to the other card:

Pretty sure alsa sets up the controls, but I've been wrong before. I haven't found anything to show the PCR1 is actually supported by alsa. Have you tried a different distro?
[http://ubuntuforums.org/showthread.php?t=1310368](http://ubuntuforums.org/showthread.php?t=1310368)
[http://ubuntuforums.org/showthread.php?t=1371366](http://ubuntuforums.org/showthread.php?t=1371366)
[http://www.alsa-project.org/main/index.php/Matrix:Vendor-Edirol](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Edirol)
You might get a hit over on the ubuntu studio forum, those guys are much more experienced with advanced sound devices:
[http://ubuntuforums.org/forumdisplay.php?f=335](http://ubuntuforums.org/forumdisplay.php?f=335)

---

### Post by cchhrriiss121212 on 2011-02-02
All the evidence I can find points to the conclusion that this device is not supported. The most conclusive answer I found is [here]("http://comments.gmane.org/gmane.linux.audio.users/68010"):
> I like the Edirol PCR1, but unfortunately it has a bug and doesn't work on Linux yet.

---

### Post by Michl on 2011-02-02
> **lidex said:**
> Pretty sure alsa sets up the controls, but I've been wrong before. I haven't found anything to show the PCR1 is actually supported by alsa. Have you tried a different distro?
[http://ubuntuforums.org/showthread.php?t=1310368](http://ubuntuforums.org/showthread.php?t=1310368)
[http://ubuntuforums.org/showthread.php?t=1371366](http://ubuntuforums.org/showthread.php?t=1371366)
[http://www.alsa-project.org/main/index.php/Matrix:Vendor-Edirol](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Edirol)
You might get a hit over on the ubuntu studio forum, those guys are much more experienced with advanced sound devices:
[http://ubuntuforums.org/forumdisplay.php?f=335](http://ubuntuforums.org/forumdisplay.php?f=335)

It seems that it hasn't been tested:

[http://bugtrack.alsa-project.org/main/index.php/Matrix:Vendor-Edirol](http://bugtrack.alsa-project.org/main/index.php/Matrix:Vendor-Edirol)

I'm just assuming that there has to be a way to make this work.

---

### Post by Michl on 2011-02-03
> **cchhrriiss121212 said:**
> All the evidence I can find points to the conclusion that this device is not supported. The most conclusive answer I found is [here]("http://comments.gmane.org/gmane.linux.audio.users/68010"):

I guess that's definitive for me unless someone can identify the bug.  I
have been ](*,) with this issue trying out all the suggestions I could
find and trying various permutations of these suggestions and on two distinct computers with two distinct ubuntu versions nothing makes the PCR work as a sound card.  Time to quit and load Windoze to check speaker frequency responses.

---

### Post by cchhrriiss121212 on 2011-02-03
There is not much you can do with unsupported hardware, unless you learn to code of course. Or try contacting an ALSA developer, they might tell you more info or be open to working on your device in exchange for cash.

---

