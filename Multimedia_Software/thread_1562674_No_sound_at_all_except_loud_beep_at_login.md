---
title: "No sound at all except loud beep at login"
date: 2010-08-27
forum: Multimedia Software
---

### Post by Mariane on 2010-08-27
I tried to follow the instruction here:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
But I failed at step 3 because there is no dropdown box on the linked page.

One test command I found online returns errors:
cat /dev/sndstat
Sound Driver:3.8.1a-980706 (ALSA v1.0.20 emulation code)
Kernel: Linux mary 2.6.30-bpo.2-686 #1 SMP Fri Dec 11 18:12:58 UTC 2009 i686
Config options: 0
Installed drivers: 
Type 10: ALSA emulation
Card config: 
HDA Intel at 0xf3300000 irq 22
Audio devices: NOT ENABLED IN CONFIG
Synth devices: NOT ENABLED IN CONFIG
Midi devices: NOT ENABLED IN CONFIG
Timers:
7: system timer
Mixers: NOT ENABLED IN CONFIG

Mariane

---

### Post by lidex on 2010-08-28
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Enter your user password when prompted. Choose the upload option and provide a link for the output.

---

### Post by Mariane on 2010-08-28
Here is the output. I started to clean it because it is too long 
but then I decided that I might remove some relevant stuff by mistake. 
I do apologize for the length of this post. 

upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.59
!!################################


!!DMI Information
!!---------------

Manufacturer:      Dell Inc.
Product Name:      Vostro 1520


!!Kernel Information
!!------------------

Kernel release:    2.6.30-bpo.2-686
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.20
Library version:    1.0.16
Utilities version:  1.0.16


!!Loaded ALSA modules
!!-------------------

snd_hda_intel


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - No

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No

aRts:
      Installed - Yes (/usr/bin/artsd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf3300000 irq 22


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:293e (rev 03)
	Subsystem: 1028:02bc


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-pcsp: index=-2
snd-hda-intel: model=dell-s14
snd-hda-intel: index=0


!!Loaded sound module options
!!--------------------------

!!Module: snd_hda_intel
	bdl_pos_adj : 1,-1,-1,-1,-1,-1,-1,-1
	enable : Y,Y,Y,Y,Y,Y,Y,Y
	enable_msi : 0
	id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
	index : 0,-1,-1,-1,-1,-1,-1,-1
	model : dell-s14,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
	position_fix : 0,0,0,0,0,0,0,0
	power_save : 0
	power_save_controller : Y
	probe_mask : -1,-1,-1,-1,-1,-1,-1,-1
	probe_only : N,N,N,N,N,N,N,N
	single_cmd : N


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: IDT 92HD81B1C5
Address: 0
Function Id: 0x1
Vendor Id: 0x111d76d5
Subsystem Id: 0x102802bc
Revision Id: 0x100302
No Modem Function Group found
Default PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
Default Amp-Out caps: ofs=0x7f, nsteps=0x7f, stepsize=0x02, mute=1
GPIO: io=3, o=0, i=0, unsolicited=1, wake=1
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[2]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Power-Map: 0x00
Node 0x0a [Pin Complex] wcaps 0x400583: Stereo Amp-In
  Amp-In caps: N/A
  Amp-In vals:  [0x00 0x00]
  Pincap 0x0001173c: IN OUT HP EAPD Detect
    Vref caps: HIZ 50 GRD 80
  EAPD 0x2: EAPD
  Pin Default 0x02214030: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Green
    DefAssociation = 0x3, Sequence = 0x0
  Pin-ctls: 0x00: VREF_HIZ
  Unsolicited: tag=02, enabled=1
  Power: setting=D0, actual=D0
  Connection: 3
     0x13 0x14* 0x1c
Node 0x0b [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x0001001c: OUT HP EAPD Detect
  EAPD 0x2: EAPD
  Pin Default 0x02211010: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Black
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=01, enabled=1
  Power: setting=D0, actual=D0
  Connection: 3
     0x13 0x14* 0x1c
Node 0x0c [Pin Complex] wcaps 0x400583: Stereo Amp-In
  Amp-In caps: N/A
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00011734: IN OUT EAPD Detect
    Vref caps: HIZ 50 GRD 80
  EAPD 0x2: EAPD
  Pin Default 0x02a19020: [Jack] Mic at Ext Front
    Conn = 1/8, Color = Pink
    DefAssociation = 0x2, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=03, enabled=1
  Power: setting=D0, actual=D0
  Connection: 3
     0x13* 0x14 0x1c
Node 0x0d [Pin Complex] wcaps 0x400501: Stereo
  Pincap 0x00010050: OUT EAPD Balanced
  EAPD 0x2: EAPD
  Pin Default 0x01014050: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Green
    DefAssociation = 0x5, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Power: setting=D0, actual=D0
  Connection: 3
     0x13* 0x14 0x1c
Node 0x0e [Pin Complex] wcaps 0x400583: Stereo Amp-In
  Amp-In caps: N/A
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00010034: IN OUT EAPD Detect
  EAPD 0x2: EAPD
  Pin Default 0x40f000f0: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 3
     0x13* 0x14 0x1c
Node 0x0f [Pin Complex] wcaps 0x400583: Stereo Amp-In
  Amp-In caps: N/A
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00010034: IN OUT EAPD Detect
  EAPD 0x2: EAPD
  Pin Default 0x01819040: [Jack] Line In at Ext Rear
    Conn = 1/8, Color = Pink
    DefAssociation = 0x4, Sequence = 0x0
  Pin-ctls: 0x20: IN
  Unsolicited: tag=04, enabled=1
  Power: setting=D0, actual=D0
  Connection: 3
     0x13 0x14 0x1c*
Node 0x10 [Pin Complex] wcaps 0x400500: Mono
  Pincap 0x00000010: OUT
  Pin Default 0x40f000f0: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00:
  Power: setting=D0, actual=D0
  Connection: 1
     0x1a
Node 0x11 [Pin Complex] wcaps 0x400483: Stereo Amp-In
  Amp-In caps: N/A
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00000024: IN Detect
  Pin Default 0x90a60160: [Fixed] Mic at Int N/A
    Conn = Digital, Color = Unknown
    DefAssociation = 0x6, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
Node 0x12 [Vendor Defined Widget] wcaps 0xf00503: Stereo Amp-In
  Amp-In caps: N/A
  Amp-In vals:  [0x00 0x00]
  Power: setting=D0, actual=D0
  Connection: 1
     0x20
Node 0x13 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out R/L
  Amp-Out caps: N/A
  Amp-Out vals:  [0x73 0x73]
  Converter: stream=0, channel=0
  Power: setting=D0, actual=D0
  Delay: 13 samples
Node 0x14 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out R/L
  Amp-Out caps: N/A
  Amp-Out vals:  [0xff 0xff]
  Converter: stream=0, channel=0
  Power: setting=D0, actual=D0
  Delay: 13 samples
Node 0x15 [Audio Input] wcaps 0x1d0541: Stereo
  Converter: stream=0, channel=0
  SDI-Select: 0
  Power: setting=D0, actual=D0
  Delay: 13 samples
  Connection: 1
     0x17
  Processing caps: benign=0, ncoeff=0
Node 0x16 [Audio Input] wcaps 0x1d0541: Stereo
  Converter: stream=0, channel=0
  SDI-Select: 0
  Power: setting=D0, actual=D0
  Delay: 13 samples
  Connection: 1
     0x18
  Processing caps: benign=0, ncoeff=0
Node 0x17 [Audio Selector] wcaps 0x300d0d: Stereo Amp-Out R/L
  Amp-Out caps: ofs=0x00, nsteps=0x0f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x80 0x80]
  Power: setting=D0, actual=D0
  Connection: 7
     0x0c* 0x0e 0x0f 0x1b 0x11 0x12 0x0a
Node 0x18 [Audio Selector] wcaps 0x300d0d: Stereo Amp-Out R/L
  Amp-Out caps: ofs=0x00, nsteps=0x0f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x80 0x80]
  Power: setting=D0, actual=D0
  Connection: 7
     0x0c* 0x0e 0x0f 0x1b 0x11 0x12 0x0a
Node 0x19 [Audio Selector] wcaps 0x300501: Stereo
  Power: setting=D0, actual=D0
  Connection: 3
     0x13* 0x14 0x1c
Node 0x1a [Audio Mixer] wcaps 0x200500: Mono
  Power: setting=D0, actual=D0
  Connection: 1
     0x19
Node 0x1b [Audio Mixer] wcaps 0x20050b: Stereo Amp-In
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97]
  Power: setting=D0, actual=D0
  Connection: 6
     0x0c 0x0e 0x0f 0x13 0x14 0x0a
Node 0x1c [Audio Selector] wcaps 0x30050d: Stereo Amp-Out
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x9f 0x9f]
  Power: setting=D0, actual=D0
  Connection: 1
     0x1b
Node 0x1d [Audio Output] wcaps 0x4061d: Stereo Digital Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Power: setting=D0, actual=D0
  Delay: 4 samples
Node 0x1e [Audio Output] wcaps 0x4061d: Stereo Digital Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Power: setting=D0, actual=D0
  Delay: 4 samples
Node 0x1f [Pin Complex] wcaps 0x400781: Stereo Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x40f000f0: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 1
     0x1d
Node 0x20 [Pin Complex] wcaps 0x400781: Stereo Digital
  Pincap 0x00000034: IN OUT Detect
  Pin Default 0x40f000f0: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 1
     0x1e
Node 0x21 [Beep Generator Widget] wcaps 0x70000c: Mono Amp-Out
  Amp-Out caps: ofs=0x03, nsteps=0x03, stepsize=0x17, mute=1
  Amp-Out vals:  [0x00]
Node 0x22 [Vendor Defined Widget] wcaps 0xf00000: Mono
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw---- 1 root audio 116,  0 Aug 28 00:47 /dev/snd/controlC0
crw-rw---- 1 root audio 116,  4 Aug 28 00:47 /dev/snd/hwC0D0
crw-rw---- 1 root audio 116, 24 Aug 28 00:47 /dev/snd/pcmC0D0c
crw-rw---- 1 root audio 116, 16 Aug 28 00:57 /dev/snd/pcmC0D0p
crw-rw---- 1 root audio 116, 33 Aug 28 00:43 /dev/snd/timer


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [Intel]

Card hw:0 'Intel'/'HDA Intel at 0xf3300000 irq 22'
  Mixer name	: 'IDT 92HD81B1C5'
  Components	: 'HDA:111d76d5,102802bc,00100302'
  Controls      : 27
  Simple ctrls  : 17
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [off]
  Front Right: Playback 64 [100%] [0.00dB] [off]
Simple mixer control 'Headphone as Line Out',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 52 [81%] [-9.00dB] [on]
  Front Right: Playback 52 [81%] [-9.00dB] [on]
Simple mixer control 'Front Mic',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 23 [74%] [0.00dB] [off]
  Front Right: Capture 23 [74%] [0.00dB] [off]
Simple mixer control 'Line In',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 23 [74%] [0.00dB] [off]
  Front Right: Capture 23 [74%] [0.00dB] [off]
Simple mixer control 'Mono Mux',0
  Capabilities: enum
  Items: 'DAC0' 'DAC1' 'Mixer'
  Item0: 'DAC0'
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 0 [0%] [0.00dB] [off]
  Front Right: Capture 0 [0%] [0.00dB] [off]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 0 [0%] [0.00dB] [off]
  Front Right: Capture 0 [0%] [0.00dB] [off]
Simple mixer control 'Amp',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 3
  Front Left: Capture 0 [0%] [0.00dB]
  Front Right: Capture 0 [0%] [0.00dB]
Simple mixer control 'DAC0',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 23 [74%] [0.00dB] [off]
  Front Right: Capture 23 [74%] [0.00dB] [off]
Simple mixer control 'DAC1',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 23 [74%] [0.00dB] [off]
  Front Right: Capture 23 [74%] [0.00dB] [off]
Simple mixer control 'Digital',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 120
  Front Left: Capture 60 [50%] [0.00dB]
  Front Right: Capture 60 [50%] [0.00dB]
Simple mixer control 'Digital Input Source',0
  Capabilities: enum
  Items: 'Analog Inputs' 'Digital Mic 1' 'Digital Mic 2'
  Item0: 'Analog Inputs'
Simple mixer control 'Digital Input Source',1
  Capabilities: enum
  Items: 'Analog Inputs' 'Digital Mic 1' 'Digital Mic 2'
  Item0: 'Analog Inputs'
Simple mixer control 'PC Beep',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 3
  Mono: Playback 1 [33%] [-12.00dB] [on]


!!Alsactl output
!!-------------

--startcollapse--
state.Intel {
	control.1 {
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
	control.2 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Capture Switch'
		value.0 false
		value.1 false
	}
	control.3 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 15'
		comment.dbmin 0
		comment.dbmax 2250
		iface MIXER
		name 'Capture Volume'
		index 1
		value.0 0
		value.1 0
	}
	control.4 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Capture Switch'
		index 1
		value.0 false
		value.1 false
	}
	control.5 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'DAC0 Capture Volume'
		value.0 23
		value.1 23
	}
	control.6 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'DAC0 Capture Switch'
		value.0 false
		value.1 false
	}
	control.7 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'DAC1 Capture Volume'
		value.0 23
		value.1 23
	}
	control.8 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'DAC1 Capture Switch'
		value.0 false
		value.1 false
	}
	control.9 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Front Mic Capture Volume'
		value.0 23
		value.1 23
	}
	control.10 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Front Mic Capture Switch'
		value.0 false
		value.1 false
	}
	control.11 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Line In Capture Volume'
		value.0 23
		value.1 23
	}
	control.12 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Line In Capture Switch'
		value.0 false
		value.1 false
	}
	control.13 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 64'
		comment.dbmin -4800
		comment.dbmax 0
		iface MIXER
		name 'Front Playback Volume'
		value.0 52
		value.1 52
	}
	control.14 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Front Playback Switch'
		value.0 true
		value.1 true
	}
	control.15 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Headphone as Line Out Switch'
		value false
	}
	control.16 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'PC Beep Playback Switch'
		value true
	}
	control.17 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 3'
		comment.dbmin -1800
		comment.dbmax 0
		iface MIXER
		name 'PC Beep Playback Volume'
		value 1
	}
	control.18 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 64'
		comment.dbmin -4800
		comment.dbmax 0
		iface MIXER
		name 'Headphone Playback Volume'
		value.0 64
		value.1 64
	}
	control.19 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Headphone Playback Switch'
		value.0 false
		value.1 false
	}
	control.20 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 DAC0
		comment.item.1 DAC1
		comment.item.2 Mixer
		iface MIXER
		name 'Mono Mux'
		value DAC0
	}
	control.21 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 3'
		comment.dbmin 0
		comment.dbmax 3000
		iface MIXER
		name 'Amp Capture Volume'
		value.0 0
		value.1 0
	}
	control.22 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 'Analog Inputs'
		comment.item.1 'Digital Mic 1'
		comment.item.2 'Digital Mic 2'
		iface MIXER
		name 'Digital Input Source'
		value 'Analog Inputs'
	}
	control.23 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 'Analog Inputs'
		comment.item.1 'Digital Mic 1'
		comment.item.2 'Digital Mic 2'
		iface MIXER
		name 'Digital Input Source'
		index 1
		value 'Analog Inputs'
	}
	control.24 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 64'
		comment.dbmin -4800
		comment.dbmax 0
		iface MIXER
		name 'Master Playback Volume'
		value 64
	}
	control.25 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Master Playback Switch'
		value true
	}
	control.26 {
		comment.access 'read write user'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 255'
		comment.tlv '0000000100000008ffffec1400000014'
		comment.dbmin -5100
		comment.dbmax 0
		iface MIXER
		name 'PCM Playback Volume'
		value.0 255
		value.1 255
	}
	control.27 {
		comment.access 'read write user'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 120'
		comment.tlv '0000000100000008fffff44800000032'
		comment.dbmin -3000
		comment.dbmax 3000
		iface MIXER
		name 'Digital Capture Volume'
		value.0 60
		value.1 60
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
snd_pcm_oss
snd_mixer_oss
snd_hda_intel
binfmt_misc
rfcomm
l2cap
bluetooth
deflate
zlib_deflate
ctr
twofish
twofish_common
camellia
serpent
blowfish
cast5
des_generic
cbc
aes_i586
aes_generic
xcbc
rmd160
sha256_generic
sha1_generic
hmac
crypto_null
af_key
ppdev
parport_pc
lp
parport
acpi_cpufreq
cpufreq_stats
cpufreq_userspace
cpufreq_conservative
cpufreq_powersave
firewire_sbp2
loop
snd_hda_codec_idt
snd_hda_codec
arc4
snd_hwdep
ecb
joydev
snd_pcm
iwlagn
iwlcore
uvcvideo
dell_laptop
rfkill
mac80211
videodev
psmouse
dcdbas
v4l1_compat
i2c_i801
snd_timer
serio_raw
i2c_core
pcspkr
cfg80211
evdev
video
output
ac
battery
snd
button
soundcore
processor
snd_page_alloc
intel_agp
agpgart
ext3
jbd
mbcache
sg
sr_mod
cdrom
sd_mod
crc_t10dif
usbhid
hid
ahci
libata
scsi_mod
firewire_ohci
firewire_core
crc_itu_t
r8169
mii
sdhci_pci
sdhci
mmc_core
led_class
ehci_hcd
uhci_hcd
usbcore
thermal
fan
thermal_sys


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x0a 0x90170110
0x0b 0x0221101f
0x0c 0x02a11020
0x0d 0x400000f0
0x0e 0x400000f1
0x0f 0x400000f2
0x10 0x400000f3
0x11 0x90a60160
0x1f 0x400000f4
0x20 0x400000f5

/sys/class/sound/hwC0D0/driver_pin_configs:
0x0a 0x02214030
0x0b 0x02211010
0x0c 0x02a19020
0x0d 0x01014050
0x0e 0x40f000f0
0x0f 0x01819040
0x10 0x40f000f0
0x11 0x90a60160
0x1f 0x40f000f0
0x20 0x40f000f0

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:


!!ALSA/HDA dmesg
!!------------------

[    7.600726] phy0: Selected rate control algorithm 'iwl-agn-rs'
[    7.641291] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    7.641325] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    7.765547] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input11
[    7.773508] input: HDA Intel Line In at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/input/input12
[    7.773552] input: HDA Intel Mic at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/input/input13
[    7.773595] input: HDA Intel Line Out at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/input/input14
[    7.773636] input: HDA Intel HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/input/input15
[    7.773677] input: HDA Intel HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/input/input16
[    8.001009] Clocksource tsc unstable (delta = -65960118 ns)
--
[   49.665718] Bluetooth: RFCOMM ver 1.11
[  191.317583] HDA Intel 0000:00:1b.0: PCI INT A disabled
[  234.754011] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[  234.754043] HDA Intel 0000:00:1b.0: setting latency timer to 64
[  234.825589] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input17
[  234.845624] input: HDA Intel Line In at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/input/input18
[  234.845774] input: HDA Intel Mic at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/input/input19
[  234.845904] input: HDA Intel Line Out at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/input/input20
[  234.846030] input: HDA Intel HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/input/input21
[  234.846152] input: HDA Intel HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/input/input22
[  703.416031] CE: hpet increasing min_delta_ns to 15000 nsec

---

### Post by lidex on 2010-08-29
With text blocks like that you have to use the code tags - the "#" in the toolbar.

You are running Jaunty, correct? What kind of kernel is that?

Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 kdesudo kate /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=dell-s14 
```
Save. Close. Reboot. 
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.

---

