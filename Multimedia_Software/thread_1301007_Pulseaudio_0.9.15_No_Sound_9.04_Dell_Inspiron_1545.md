---
title: "Pulseaudio 0.9.15 No Sound 9.04 Dell Inspiron 1545"
date: 2009-10-25
forum: Multimedia Software
---

### Post by Accidus on 2009-10-25
My sound output used to work well, but not capture. I tried to set up capture, and messed up something along the way, so even output no longer works. 

If I open the volume control while a program is playing a sound, I can see the program's output stream, and the volumeters move as if the sound is playing, but it is not.

The default output sink is the correct one, and alsamixer is not muted.

I've followed the various troubleshooting posts (e.g.: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578) and [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) and [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure) ) without success. I've also asked on #pulseaudio@freenode, without success.

My ALSA information is:
```

!!################################
!!ALSA Information Script v 0.4.58
!!################################

!!Script ran on: Sat Oct 24 18:10:52 UTC 2009


!!Linux Distribution
!!------------------

Ubuntu 9.04 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 9.04"


!!DMI Information
!!---------------

Manufacturer:      Dell Inc.
Product Name:      Inspiron 1545                   


!!Kernel Information
!!------------------

Kernel release:    2.6.28-16-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.18rc3
Library version:    1.0.19
Utilities version:  1.0.18


!!Loaded ALSA modules
!!-------------------

snd_hda_intel


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

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf6afc000 irq 21


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:293e (rev 03)
	Subsystem: 1028:02aa


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
snd-hda-intel: model=dell-bios


!!Loaded sound module options
!!--------------------------

!!Module: snd_hda_intel
	bdl_pos_adj : 1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	enable_msi : 0
	id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
	index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	model : dell-bios,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
	position_fix : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	power_save : 0
	power_save_controller : Y
	probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	single_cmd : N


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: IDT 92HD71B7X
Address: 0
Vendor Id: 0x111d76b2
Subsystem Id: 0x102802aa
Revision Id: 0x100302
No Modem Function Group found
Default PCM:
    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
Default Amp-Out caps: ofs=0x7f, nsteps=0x7f, stepsize=0x02, mute=1
GPIO: io=8, o=0, i=0, unsolicited=1, wake=1
  IO[0]: enable=1, dir=1, wake=0, sticky=0, data=1
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0
  IO[2]: enable=0, dir=0, wake=0, sticky=0, data=0
  IO[3]: enable=0, dir=0, wake=0, sticky=0, data=0
  IO[4]: enable=0, dir=0, wake=0, sticky=0, data=0
  IO[5]: enable=0, dir=0, wake=0, sticky=0, data=0
  IO[6]: enable=0, dir=0, wake=0, sticky=0, data=0
  IO[7]: enable=0, dir=0, wake=0, sticky=0, data=0
Node 0x0a [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x0000001c: OUT HP Detect
  Pin Default 0x0421101f: [Jack] HP Out at Ext Right
    Conn = 1/8, Color = Black
    DefAssociation = 0x1, Sequence = 0xf
  Pin-ctls: 0xc0: OUT HP
  Unsolicited: tag=30, enabled=1
  Connection: 3
     0x10 0x11* 0x17
Node 0x0b [Pin Complex] wcaps 0x400081: Stereo
  Pincap 0x00001724: IN Detect
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x04a11221: [Jack] Mic at Ext Right
    Conn = 1/8, Color = Black
    DefAssociation = 0x2, Sequence = 0x1
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
Node 0x0c [Pin Complex] wcaps 0x400081: Stereo
  Pincap 0x00001724: IN Detect
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x90a70330: [Fixed] Mic at Int N/A
    Conn = Analog, Color = Unknown
    DefAssociation = 0x3, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
Node 0x0d [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x00000014: OUT Detect
  Pin Default 0x90170110: [Fixed] Speaker at Int N/A
    Conn = Analog, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 3
     0x10* 0x11 0x17
Node 0x0e [Pin Complex] wcaps 0x400081: Stereo
  Pincap 0x00001724: IN Detect
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x40f000f0: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00: VREF_HIZ
  Unsolicited: tag=00, enabled=0
Node 0x0f [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x00000014: OUT Detect
  Pin Default 0x40f000f0: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Connection: 3
     0x10 0x11 0x17*
Node 0x10 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out R/L
  Amp-Out caps: N/A
  Amp-Out vals:  [0x7f 0x7f]
  Converter: stream=0, channel=0
  Power: setting=D0, actual=D0
  Delay: 13 samples
Node 0x11 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out R/L
  Amp-Out caps: N/A
  Amp-Out vals:  [0x7f 0x7f]
  Converter: stream=0, channel=0
  Power: setting=D0, actual=D0
  Delay: 13 samples
Node 0x12 [Audio Input] wcaps 0x1d0541: Stereo
  Converter: stream=0, channel=0
  SDI-Select: 0
  Power: setting=D3, actual=D3
  Delay: 13 samples
  Connection: 1
     0x1c
  Processing caps: benign=0, ncoeff=0
Node 0x13 [Audio Input] wcaps 0x1d0541: Stereo
  Converter: stream=0, channel=0
  SDI-Select: 0
  Power: setting=D3, actual=D3
  Delay: 13 samples
  Connection: 1
     0x1d
  Processing caps: benign=0, ncoeff=0
Node 0x14 [Pin Complex] wcaps 0x400100: Mono
  Pincap 0x00000010: OUT
  Pin Default 0x40f000f0: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00:
  Connection: 1
     0x16
Node 0x15 [Audio Selector] wcaps 0x300101: Stereo
  Connection: 3
     0x10* 0x11 0x17
Node 0x16 [Audio Mixer] wcaps 0x200100: Mono
  Connection: 1
     0x15
Node 0x17 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97]
  Connection: 5
     0x10 0x11 0x27 0x1a 0x1b
Node 0x18 [Pin Complex] wcaps 0x40000d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x00000020: IN
  Pin Default 0x90a000f0: [Fixed] Mic at Int N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x20: IN
Node 0x19 [Pin Complex] wcaps 0x40000d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x00000020: IN
  Pin Default 0x40f000f0: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00:
Node 0x1a [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 3
     0x0b* 0x0c 0x0e
Node 0x1b [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 3
     0x0b* 0x0c 0x0e
Node 0x1c [Audio Selector] wcaps 0x30090d: Stereo Amp-Out R/L
  Amp-Out caps: ofs=0x00, nsteps=0x0f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x8f 0x8f]
  Connection: 4
     0x1a* 0x17 0x18 0x19
Node 0x1d [Audio Selector] wcaps 0x30090d: Stereo Amp-Out R/L
  Amp-Out caps: ofs=0x00, nsteps=0x0f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x80 0x80]
  Connection: 4
     0x1b* 0x17 0x18 0x19
Node 0x1e [Pin Complex] wcaps 0x400301: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x044413b0: [Jack] SPDIF Out at Ext Right
    Conn = RCA, Color = Black
    DefAssociation = 0xb, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Connection: 1
     0x24
Node 0x1f [Pin Complex] wcaps 0x400701: Stereo Digital
  Pincap 0x00010010: OUT EAPD
  EAPD 0x0:
  Pin Default 0x044413b0: [Jack] SPDIF Out at Ext Right
    Conn = RCA, Color = Black
    DefAssociation = 0xb, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Power: setting=D0, actual=D0
  Connection: 2
     0x24* 0x25
Node 0x20 [Pin Complex] wcaps 0x400301: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x40f000f6: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x6
  Pin-ctls: 0x00:
  Connection: 1
     0x25
Node 0x21 [Audio Output] wcaps 0x40211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Delay: 4 samples
Node 0x22 [Audio Output] wcaps 0x40211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Delay: 4 samples
Node 0x23 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x24 [Audio Selector] wcaps 0x300101: Stereo
  Connection: 3
     0x21* 0x1c 0x1d
Node 0x25 [Audio Selector] wcaps 0x300101: Stereo
  Connection: 3
     0x22* 0x1c 0x1d
Node 0x26 [Beep Generator Widget] wcaps 0x70000c: Mono Amp-Out
  Amp-Out caps: ofs=0x03, nsteps=0x03, stepsize=0x17, mute=1
  Amp-Out vals:  [0x00]
Node 0x27 [Pin Complex] wcaps 0x400000: Mono
  Pincap 0x00000020: IN
  Pin Default 0x40f000f7: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x7
  Pin-ctls: 0x00:
Node 0x28 [Volume Knob Widget] wcaps 0x600000: Mono
  Volume-Knob: delta=1, steps=127, direct=1, val=127
  Connection: 2
     0x10* 0x11
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----  1 root audio 116, 7 Oct 24 18:30 /dev/snd/controlC0
crw-rw----  1 root audio 116, 6 Oct 24 18:31 /dev/snd/pcmC0D0c
crw-rw----  1 root audio 116, 5 Oct 24 18:37 /dev/snd/pcmC0D0p
crw-rw----  1 root audio 116, 4 Oct 24 18:31 /dev/snd/pcmC0D1p
crw-rw----  1 root audio 116, 3 Oct 24 18:30 /dev/snd/seq
crw-rw----  1 root audio 116, 2 Oct 24 18:30 /dev/snd/timer


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
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

Card hw:0 'Intel'/'HDA Intel at 0xf6afc000 irq 21'
  Mixer name	: 'IDT 92HD71B7X'
  Components	: 'HDA:111d76b2,102802aa,00100302'
  Controls      : 31
  Simple ctrls  : 19
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 127
  Mono: Playback 127 [100%] [0.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 127
  Mono:
  Front Left: Playback 127 [100%] [0.00dB] [on]
  Front Right: Playback 127 [100%] [0.00dB] [on]
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
  Limits: Playback 0 - 127
  Mono:
  Front Left: Playback 127 [100%] [0.00dB] [on]
  Front Right: Playback 127 [100%] [0.00dB] [on]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 15 [100%] [22.50dB] [off]
  Front Right: Capture 15 [100%] [22.50dB] [off]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 0 [0%] [0.00dB] [off]
  Front Right: Capture 0 [0%] [0.00dB] [off]
Simple mixer control 'Analog Loopback',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Analog Loopback',1
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
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
Simple mixer control 'Digital Input Source',0
  Capabilities: enum
  Items: 'Analog Inputs' 'Mixer' 'Digital Mic 1'
  Item0: 'Analog Inputs'
Simple mixer control 'Import0 Mux',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 23 [74%] [0.00dB] [off]
  Front Right: Capture 23 [74%] [0.00dB] [off]
Simple mixer control 'Import1 Mux',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 23 [74%] [0.00dB] [off]
  Front Right: Capture 23 [74%] [0.00dB] [off]
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Mic' 'Front Mic'
  Item0: 'Mic'
Simple mixer control 'Input Source',1
  Capabilities: cenum
  Items: 'Mic' 'Front Mic'
  Item0: 'Mic'
Simple mixer control 'Mux',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 3
  Front Left: Capture 0 [0%] [0.00dB]
  Front Right: Capture 0 [0%] [0.00dB]
Simple mixer control 'Mux',1
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 3
  Front Left: Capture 0 [0%] [0.00dB]
  Front Right: Capture 0 [0%] [0.00dB]


!!Alsactl output
!!-------------

--startcollapse--
state.Intel {
	control.1 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Mic
		comment.item.1 'Front Mic'
		iface MIXER
		name 'Input Source'
		value Mic
	}
	control.2 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Mic
		comment.item.1 'Front Mic'
		iface MIXER
		name 'Input Source'
		index 1
		value Mic
	}
	control.3 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Analog Loopback'
		value true
	}
	control.4 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Analog Loopback'
		index 1
		value true
	}
	control.5 {
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
	control.6 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Capture Switch'
		value.0 false
		value.1 false
	}
	control.7 {
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
	control.8 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Capture Switch'
		index 1
		value.0 false
		value.1 false
	}
	control.9 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Import0 Mux Capture Switch'
		value.0 false
		value.1 false
	}
	control.10 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Import0 Mux Capture Volume'
		value.0 23
		value.1 23
	}
	control.11 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Import1 Mux Capture Switch'
		value.0 false
		value.1 false
	}
	control.12 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Import1 Mux Capture Volume'
		value.0 23
		value.1 23
	}
	control.13 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'DAC0 Capture Switch'
		value.0 false
		value.1 false
	}
	control.14 {
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
	control.15 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'DAC1 Capture Switch'
		value.0 false
		value.1 false
	}
	control.16 {
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
	control.17 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 127'
		comment.dbmin -9525
		comment.dbmax 0
		iface MIXER
		name 'Front Playback Volume'
		value.0 127
		value.1 127
	}
	control.18 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Front Playback Switch'
		value.0 true
		value.1 true
	}
	control.19 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 127'
		comment.dbmin -9525
		comment.dbmax 0
		iface MIXER
		name 'Headphone Playback Volume'
		value.0 127
		value.1 127
	}
	control.20 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Headphone Playback Switch'
		value.0 true
		value.1 true
	}
	control.21 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 3'
		comment.dbmin 0
		comment.dbmax 3000
		iface MIXER
		name 'Mux Capture Volume'
		value.0 0
		value.1 0
	}
	control.22 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 3'
		comment.dbmin 0
		comment.dbmax 3000
		iface MIXER
		name 'Mux Capture Volume'
		index 1
		value.0 0
		value.1 0
	}
	control.23 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 'Analog Inputs'
		comment.item.1 Mixer
		comment.item.2 'Digital Mic 1'
		iface MIXER
		name 'Digital Input Source'
		value 'Analog Inputs'
	}
	control.24 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Con Mask'
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.25 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.26 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Default'
		value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.27 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Switch'
		value false
	}
	control.28 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Default PCM Playback Switch'
		value true
	}
	control.29 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		comment.dbmin -9525
		comment.dbmax 0
		iface MIXER
		name 'Master Playback Volume'
		value 127
	}
	control.30 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Master Playback Switch'
		value true
	}
	control.31 {
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
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
michael_mic
arc4
ecb
binfmt_misc
i915
drm
ppdev
bridge
stp
bnep
input_polldev
lp
parport
snd_hda_intel
snd_pcm_oss
snd_mixer_oss
snd_pcm
snd_seq_dummy
snd_seq_oss
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
snd_seq
snd_timer
snd_seq_device
snd
soundcore
psmouse
iTCO_wdt
ieee80211_crypt_tkip
snd_page_alloc
dcdbas
pcspkr
serio_raw
iTCO_vendor_support
video
wl
ieee80211_crypt
joydev
output
intel_agp
agpgart
hid_microsoft
usbhid
usb_storage
sky2
fbcon
tileblit
font
bitblit
softcursor


!!ALSA/HDA dmesg
!!------------------

[   12.932933] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   13.258681] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   13.258778] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   13.573469] lp: driver loaded but no devices found

```

Here is the log generated by restarting pulseaudio -vvvvvv, and then trying to play a sound using Totem:
```

D: main.c: Started as real root: no, suid root: yes
I: main.c: We're in the group 'pulse-rt', allowing high-priority scheduling.
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
I: core-util.c: Successfully gained nice level -11.
D: main.c: Can realtime: yes, can high-priority: yes
I: main.c: Giving up CAP_NICE
D: main.c: Can realtime: no, can high-priority: no
I: main.c: This is PulseAudio 0.9.15
D: main.c: Compilation host: i486-pc-linux-gnu
D: main.c: Compilation CFLAGS: -g -O2 -g -Wall -O3 -Wall -W -Wextra -pipe -Wno-long-long -Winline -Wvla -Wno-overlength-strings -Wunsafe-loop-optimizations -Wundef -Wformat=2 -Wlogical-op -Wsign-compare -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wold-style-definition -Wpointer-arith -Winit-self -Wdeclaration-after-statement -Wfloat-equal -Wmissing-prototypes -Wstrict-prototypes -Wredundant-decls -Wmissing-declarations -Wmissing-noreturn -Wshadow -Wendif-labels -Wcast-align -Wstrict-aliasing=2 -Wwrite-strings -Wno-unused-parameter -ffast-math -Wp,-D_FORTIFY_SOURCE=2 -fno-common -fdiagnostics-show-option
D: main.c: Running on host: Linux i686 2.6.28-16-generic #55-Ubuntu SMP Tue Oct 20 19:48:24 UTC 2009
D: main.c: Found 2 CPUs.
I: main.c: Page size is 4096 bytes
D: main.c: Compiled with Valgrind support: no
D: main.c: Running in valgrind mode: no
D: main.c: Optimized build: yes
D: main.c: All asserts enabled.
I: main.c: Machine ID is 4e7b4aaa28fdc4c2497f9afa4949474d.
I: main.c: Session ID is 4e7b4aaa28fdc4c2497f9afa4949474d-1256410527.356582-320609535.
I: main.c: Using runtime directory /home/accidus/.pulse/4e7b4aaa28fdc4c2497f9afa4949474d:runtime.
I: main.c: Using state directory /home/accidus/.pulse.
I: main.c: Running in system mode: no
I: main.c: Fresh high-resolution timers available! Bon appetit!
D: rtclock.c: Timer slack is set to 50 us.
D: memblock.c: Using shared memory pool with 1024 slots of size 64.0 KiB each, total size is 64.0 MiB, maximum usable slot size is 65496
I: module.c: Loaded "module-suspend-on-idle" (index: #0; argument: "").
I: module-device-restore.c: Sucessfully opened database file '/home/accidus/.pulse/4e7b4aaa28fdc4c2497f9afa4949474d:device-volumes.i486-pc-linux-gnu.gdbm'.
I: module.c: Loaded "module-device-restore" (index: #1; argument: "").
I: module-stream-restore.c: Sucessfully opened database file '/home/accidus/.pulse/4e7b4aaa28fdc4c2497f9afa4949474d:stream-volumes.i486-pc-linux-gnu.gdbm'.
I: module.c: Loaded "module-stream-restore" (index: #2; argument: "").
I: module-card-restore.c: Sucessfully opened database file '/home/accidus/.pulse/4e7b4aaa28fdc4c2497f9afa4949474d:card-database.i486-pc-linux-gnu.gdbm'.
I: module.c: Loaded "module-card-restore" (index: #3; argument: "").
I: module.c: Loaded "module-augment-properties" (index: #4; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9.15/modules/module-hal-detect.so': success
D: dbus-util.c: Successfully connected to D-Bus system bus 908b3e94becf5af61d0f0a064ae34d86 as :1.232
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_sequencer
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_timer
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_8086_293e_sound_card_0_alsa_playback_1
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_8086_293e_sound_card_0_alsa_playback_0
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_8086_293e_sound_card_0_alsa_capture_0
D: module-hal-detect.c: Loading module-alsa-card with arguments 'device_id=0 name=pci_8086_293e_sound_card_0 card_name=alsa_card.pci_8086_293e_sound_card_0 tsched=0'
D: dbus-util.c: Successfully connected to D-Bus session bus 2f815fec6a532992f92884ff4ae34da0 as :1.231
D: reserve-wrap.c: Successfully acquired reservation lock on device 'Audio0'
D: alsa-util.c: Checking for playback on analog-mono (hw)
D: alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels() failed: Invalid argument
D: alsa-util.c: Trying hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels() failed: Invalid argument
D: alsa-util.c: Trying plug:hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels() failed: Invalid argument
D: alsa-util.c: Trying plug:hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels() failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Invalid argument
D: alsa-util.c: Checking for playback on analog-stereo (front)
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open front:0
D: alsa-util.c: Checking for capture on analog-mono (hw)
D: alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels() failed: Invalid argument
D: alsa-util.c: Trying hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels() failed: Invalid argument
D: alsa-util.c: Trying plug:hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels() failed: Invalid argument
D: alsa-util.c: Trying plug:hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels() failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Invalid argument
D: alsa-util.c: Checking for capture on analog-stereo (front)
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open front:0
I: module-alsa-card.c: Found profile 'Output Analog Stereo + Input Analog Stereo'
D: alsa-util.c: Checking for capture on iec958-stereo (iec958)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D1c failed
I: alsa-util.c: Error opening PCM device iec958:0: No such file or directory
D: alsa-util.c: Checking for capture on hdmi-stereo (hdmi)
D: alsa-util.c: Trying hdmi:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D3c failed
I: alsa-util.c: Error opening PCM device hdmi:0: No such file or directory
D: alsa-util.c: Checking for capture on analog-surround-40 (surround40)
D: alsa-util.c: Trying surround40:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround40:0
D: alsa-util.c: snd_pcm_hw_params_set_channels() failed: Invalid argument
D: alsa-util.c: Trying surround40:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround40:0
D: alsa-util.c: snd_pcm_hw_params_set_channels() failed: Invalid argument
D: alsa-util.c: Trying plug:surround40:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround40:0
D: alsa-util.c: snd_pcm_hw_params_set_channels() failed: Invalid argument
D: alsa-util.c: Trying plug:surround40:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround40:0
D: alsa-util.c: snd_pcm_hw_params_set_channels() failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround40:0: Invalid argument
D: alsa-util.c: Checking for capture on iec958-ac3-surround-40 (a52)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: alsa-util.c: Checking for capture on analog-surround-41 (surround41)
D: alsa-util.c: Trying surround41:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround41:0
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying surround41:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround41:0
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying plug:surround41:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround41:0
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying plug:surround41:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround41:0
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround41:0: Invalid argument
D: alsa-util.c: Checking for capture on analog-surround-50 (surround50)
D: alsa-util.c: Trying surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround50:0
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying surround50:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround50:0
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying plug:surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround50:0
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying plug:surround50:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround50:0
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround50:0: Invalid argument
D: alsa-util.c: Checking for capture on analog-surround-51 (surround51)
D: alsa-util.c: Trying surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround51:0
D: alsa-util.c: snd_pcm_hw_params_set_channels() failed: Invalid argument
D: alsa-util.c: Trying surround51:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround51:0
D: alsa-util.c: snd_pcm_hw_params_set_channels() failed: Invalid argument
D: alsa-util.c: Trying plug:surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround51:0
D: alsa-util.c: snd_pcm_hw_params_set_channels() failed: Invalid argument
D: alsa-util.c: Trying plug:surround51:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround51:0
D: alsa-util.c: snd_pcm_hw_params_set_channels() failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround51:0: Invalid argument
D: alsa-util.c: Checking for capture on iec958-ac3-surround-51 (a52)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: alsa-util.c: Checking for capture on analog-surround-71 (surround71)
D: alsa-util.c: Trying surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround71:0
D: alsa-util.c: snd_pcm_hw_params_set_channels() failed: Invalid argument
D: alsa-util.c: Trying surround71:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround71:0
D: alsa-util.c: snd_pcm_hw_params_set_channels() failed: Invalid argument
D: alsa-util.c: Trying plug:surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround71:0
D: alsa-util.c: snd_pcm_hw_params_set_channels() failed: Invalid argument
D: alsa-util.c: Trying plug:surround71:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround71:0
D: alsa-util.c: snd_pcm_hw_params_set_channels() failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround71:0: Invalid argument
I: module-alsa-card.c: Found profile 'Output Analog Stereo'
D: alsa-util.c: Checking for playback on iec958-stereo (iec958)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open iec958:0
D: alsa-util.c: Checking for capture on analog-mono (hw)
D: alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels() failed: Invalid argument
D: alsa-util.c: Trying hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels() failed: Invalid argument
D: alsa-util.c: Trying plug:hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels() failed: Invalid argument
D: alsa-util.c: Trying plug:hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels() failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Invalid argument
D: alsa-util.c: Checking for capture on analog-stereo (front)
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open front:0
I: module-alsa-card.c: Found profile 'Output Digital Stereo (IEC958) + Input Analog Stereo'
D: alsa-util.c: Checking for capture on iec958-stereo (iec958)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D1c failed
I: alsa-util.c: Error opening PCM device iec958:0: No such file or directory
D: alsa-util.c: Checking for capture on hdmi-stereo (hdmi)
D: alsa-util.c: Trying hdmi:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D3c failed
I: alsa-util.c: Error opening PCM device hdmi:0: No such file or directory
D: alsa-util.c: Checking for capture on analog-surround-40 (surround40)
D: alsa-util.c: Trying surround40:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround40:0
D: alsa-util.c: snd_pcm_hw_params_set_channels() failed: Invalid argument
D: alsa-util.c: Trying surround40:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround40:0
D: alsa-util.c: snd_pcm_hw_params_set_channels() failed: Invalid argument
D: alsa-util.c: Trying plug:surround40:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround40:0
D: alsa-util.c: snd_pcm_hw_params_set_channels() failed: Invalid argument
D: alsa-util.c: Trying plug:surround40:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround40:0
D: alsa-util.c: snd_pcm_hw_params_set_channels() failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround40:0: Invalid argument
D: alsa-util.c: Checking for capture on iec958-ac3-surround-40 (a52)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: alsa-util.c: Checking for capture on analog-surround-41 (surround41)
D: alsa-util.c: Trying surround41:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround41:0
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying surround41:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround41:0
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying plug:surround41:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround41:0
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying plug:surround41:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround41:0
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround41:0: Invalid argument
D: alsa-util.c: Checking for capture on analog-surround-50 (surround50)
D: alsa-util.c: Trying surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround50:0
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying surround50:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround50:0
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying plug:surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround50:0
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying plug:surround50:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround50:0
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround50:0: Invalid argument
D: alsa-util.c: Checking for capture on analog-surround-51 (surround51)
D: alsa-util.c: Trying surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround51:0
D: alsa-util.c: snd_pcm_hw_params_set_channels() failed: Invalid argument
D: alsa-util.c: Trying surround51:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround51:0
D: alsa-util.c: snd_pcm_hw_params_set_channels() failed: Invalid argument
D: alsa-util.c: Trying plug:surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround51:0
D: alsa-util.c: snd_pcm_hw_params_set_channels() failed: Invalid argument
D: alsa-util.c: Trying plug:surround51:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround51:0
D: alsa-util.c: snd_pcm_hw_params_set_channels() failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround51:0: Invalid argument
D: alsa-util.c: Checking for capture on iec958-ac3-surround-51 (a52)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: alsa-util.c: Checking for capture on analog-surround-71 (surround71)
D: alsa-util.c: Trying surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround71:0
D: alsa-util.c: snd_pcm_hw_params_set_channels() failed: Invalid argument
D: alsa-util.c: Trying surround71:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround71:0
D: alsa-util.c: snd_pcm_hw_params_set_channels() failed: Invalid argument
D: alsa-util.c: Trying plug:surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround71:0
D: alsa-util.c: snd_pcm_hw_params_set_channels() failed: Invalid argument
D: alsa-util.c: Trying plug:surround71:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround71:0
D: alsa-util.c: snd_pcm_hw_params_set_channels() failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround71:0: Invalid argument
I: module-alsa-card.c: Found profile 'Output Digital Stereo (IEC958)'
D: alsa-util.c: Checking for playback on hdmi-stereo (hdmi)
D: alsa-util.c: Trying hdmi:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D3p failed
I: alsa-util.c: Error opening PCM device hdmi:0: No such file or directory
D: alsa-util.c: Checking for playback on analog-surround-40 (surround40)
D: alsa-util.c: Trying surround40:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround40:0
D: alsa-util.c: snd_pcm_hw_params_set_channels() failed: Invalid argument
D: alsa-util.c: Trying surround40:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround40:0
D: alsa-util.c: snd_pcm_hw_params_set_channels() failed: Invalid argument
D: alsa-util.c: Trying plug:surround40:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround40:0
D: alsa-util.c: snd_pcm_hw_params_set_channels() failed: Invalid argument
D: alsa-util.c: Trying plug:surround40:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround40:0
D: alsa-util.c: snd_pcm_hw_params_set_channels() failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround40:0: Invalid argument
D: alsa-util.c: Checking for playback on iec958-ac3-surround-40 (a52)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: alsa-util.c: Checking for playback on analog-surround-41 (surround41)
D: alsa-util.c: Trying surround41:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround41:0
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying surround41:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround41:0
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying plug:surround41:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround41:0
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying plug:surround41:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround41:0
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround41:0: Invalid argument
D: alsa-util.c: Checking for playback on analog-surround-50 (surround50)
D: alsa-util.c: Trying surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround50:0
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying surround50:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround50:0
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying plug:surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround50:0
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying plug:surround50:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround50:0
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround50:0: Invalid argument
D: alsa-util.c: Checking for playback on analog-surround-51 (surround51)
D: alsa-util.c: Trying surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround51:0
D: alsa-util.c: snd_pcm_hw_params_set_channels() failed: Invalid argument
D: alsa-util.c: Trying surround51:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround51:0
D: alsa-util.c: snd_pcm_hw_params_set_channels() failed: Invalid argument
D: alsa-util.c: Trying plug:surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround51:0
D: alsa-util.c: snd_pcm_hw_params_set_channels() failed: Invalid argument
D: alsa-util.c: Trying plug:surround51:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround51:0
D: alsa-util.c: snd_pcm_hw_params_set_channels() failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround51:0: Invalid argument
D: alsa-util.c: Checking for playback on iec958-ac3-surround-51 (a52)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: alsa-util.c: Checking for playback on analog-surround-71 (surround71)
D: alsa-util.c: Trying surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround71:0
D: alsa-util.c: snd_pcm_hw_params_set_channels() failed: Invalid argument
D: alsa-util.c: Trying surround71:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround71:0
D: alsa-util.c: snd_pcm_hw_params_set_channels() failed: Invalid argument
D: alsa-util.c: Trying plug:surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround71:0
D: alsa-util.c: snd_pcm_hw_params_set_channels() failed: Invalid argument
D: alsa-util.c: Trying plug:surround71:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround71:0
D: alsa-util.c: snd_pcm_hw_params_set_channels() failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround71:0: Invalid argument
D: alsa-util.c: Checking for capture on analog-mono (hw)
D: alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels() failed: Invalid argument
D: alsa-util.c: Trying hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels() failed: Invalid argument
D: alsa-util.c: Trying plug:hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels() failed: Invalid argument
D: alsa-util.c: Trying plug:hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels() failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Invalid argument
D: alsa-util.c: Checking for capture on analog-stereo (front)
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open front:0
I: module-alsa-card.c: Found profile 'Input Analog Stereo'
D: alsa-util.c: Checking for capture on iec958-stereo (iec958)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D1c failed
I: alsa-util.c: Error opening PCM device iec958:0: No such file or directory
D: alsa-util.c: Checking for capture on hdmi-stereo (hdmi)
D: alsa-util.c: Trying hdmi:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D3c failed
I: alsa-util.c: Error opening PCM device hdmi:0: No such file or directory
D: alsa-util.c: Checking for capture on analog-surround-40 (surround40)
D: alsa-util.c: Trying surround40:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround40:0
D: alsa-util.c: snd_pcm_hw_params_set_channels() failed: Invalid argument
D: alsa-util.c: Trying surround40:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround40:0
D: alsa-util.c: snd_pcm_hw_params_set_channels() failed: Invalid argument
D: alsa-util.c: Trying plug:surround40:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround40:0
D: alsa-util.c: snd_pcm_hw_params_set_channels() failed: Invalid argument
D: alsa-util.c: Trying plug:surround40:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround40:0
D: alsa-util.c: snd_pcm_hw_params_set_channels() failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround40:0: Invalid argument
D: alsa-util.c: Checking for capture on iec958-ac3-surround-40 (a52)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: alsa-util.c: Checking for capture on analog-surround-41 (surround41)
D: alsa-util.c: Trying surround41:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround41:0
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying surround41:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround41:0
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying plug:surround41:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround41:0
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying plug:surround41:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround41:0
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround41:0: Invalid argument
D: alsa-util.c: Checking for capture on analog-surround-50 (surround50)
D: alsa-util.c: Trying surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround50:0
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying surround50:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround50:0
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying plug:surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround50:0
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying plug:surround50:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround50:0
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround50:0: Invalid argument
D: alsa-util.c: Checking for capture on analog-surround-51 (surround51)
D: alsa-util.c: Trying surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround51:0
D: alsa-util.c: snd_pcm_hw_params_set_channels() failed: Invalid argument
D: alsa-util.c: Trying surround51:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround51:0
D: alsa-util.c: snd_pcm_hw_params_set_channels() failed: Invalid argument
D: alsa-util.c: Trying plug:surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround51:0
D: alsa-util.c: snd_pcm_hw_params_set_channels() failed: Invalid argument
D: alsa-util.c: Trying plug:surround51:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround51:0
D: alsa-util.c: snd_pcm_hw_params_set_channels() failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround51:0: Invalid argument
D: alsa-util.c: Checking for capture on iec958-ac3-surround-51 (a52)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: alsa-util.c: Checking for capture on analog-surround-71 (surround71)
D: alsa-util.c: Trying surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround71:0
D: alsa-util.c: snd_pcm_hw_params_set_channels() failed: Invalid argument
D: alsa-util.c: Trying surround71:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround71:0
D: alsa-util.c: snd_pcm_hw_params_set_channels() failed: Invalid argument
D: alsa-util.c: Trying plug:surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround71:0
D: alsa-util.c: snd_pcm_hw_params_set_channels() failed: Invalid argument
D: alsa-util.c: Trying plug:surround71:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround71:0
D: alsa-util.c: snd_pcm_hw_params_set_channels() failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround71:0: Invalid argument
I: module-card-restore.c: Restoring profile for card alsa_card.pci_8086_293e_sound_card_0.
I: card.c: Created 0 "alsa_card.pci_8086_293e_sound_card_0"
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open front:0
I: alsa-sink.c: Successfully opened device front:0.
I: alsa-sink.c: Selected configuration 'Analog Stereo' (analog-stereo).
I: alsa-sink.c: Successfully enabled mmap() mode.
I: (alsa-lib)control.c: Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Master".
I: module-device-restore.c: Restoring volume for sink alsa_output.pci_8086_293e_sound_card_0.
I: module-device-restore.c: Restoring mute state for sink alsa_output.pci_8086_293e_sound_card_0.
I: sink.c: Created sink 0 "alsa_output.pci_8086_293e_sound_card_0" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: sink.c:     alsa.resolution_bits = "16"
I: sink.c:     alsa.mixer_element = "Master"
I: sink.c:     device.api = "alsa"
I: sink.c:     device.class = "sound"
I: sink.c:     alsa.class = "generic"
I: sink.c:     alsa.subclass = "generic-mix"
I: sink.c:     alsa.name = "STAC92xx Analog"
I: sink.c:     alsa.id = "STAC92xx Analog"
I: sink.c:     alsa.subdevice = "0"
I: sink.c:     alsa.subdevice_name = "subdevice #0"
I: sink.c:     alsa.device = "0"
I: sink.c:     alsa.card = "0"
I: sink.c:     alsa.card_name = "HDA Intel"
I: sink.c:     alsa.long_card_name = "HDA Intel at 0xf6afc000 irq 21"
I: sink.c:     alsa.driver_name = "snd_hda_intel"
I: sink.c:     device.bus_path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
I: sink.c:     hal.udi = "/org/freedesktop/Hal/devices/pci_8086_293e_sound_card_0"
I: sink.c:     hal.product = "HDA Intel Sound Card"
I: sink.c:     hal.card_id = "HDA Intel"
I: sink.c:     device.string = "front:0"
I: sink.c:     device.buffering.buffer_size = "14080"
I: sink.c:     device.buffering.fragment_size = "1408"
I: sink.c:     device.access_mode = "mmap"
I: sink.c:     device.profile.name = "analog-stereo"
I: sink.c:     device.profile.description = "Analog Stereo"
I: sink.c:     device.description = "HDA Intel"
I: sink.c:     device.icon_name = "audio-card"
I: module-device-restore.c: Restoring volume for source alsa_output.pci_8086_293e_sound_card_0.monitor.
I: module-device-restore.c: Restoring mute state for source alsa_output.pci_8086_293e_sound_card_0.monitor.
I: source.c: Created source 0 "alsa_output.pci_8086_293e_sound_card_0.monitor" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: source.c:     device.description = "Monitor of HDA Intel"
I: source.c:     device.class = "monitor"
I: source.c:     alsa.card = "0"
I: source.c:     alsa.card_name = "HDA Intel"
I: source.c:     alsa.long_card_name = "HDA Intel at 0xf6afc000 irq 21"
I: source.c:     alsa.driver_name = "snd_hda_intel"
I: source.c:     device.bus_path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
I: source.c:     hal.udi = "/org/freedesktop/Hal/devices/pci_8086_293e_sound_card_0"
I: source.c:     hal.product = "HDA Intel Sound Card"
I: source.c:     hal.card_id = "HDA Intel"
I: source.c:     device.string = "0"
I: source.c:     device.icon_name = "audio-card"
I: alsa-sink.c: Using 10 fragments of size 1408 bytes, buffer time is 79.82ms
D: alsa-sink.c: hwbuf_unused=0
D: alsa-sink.c: setting avail_min=1
I: alsa-sink.c: Volume ranges from 0 to 127.
I: alsa-sink.c: Volume ranges from -95.25 dB to 0.00 dB.
I: alsa-sink.c: No particular base volume set, fixing to 0 dB
I: alsa-util.c: ALSA device lacks independant volume controls for each channel.
I: alsa-sink.c: Using hardware volume control. Hardware dB scale supported.
D: alsa-util.c: snd_pcm_dump():
D: alsa-util.c: Soft volume PCM
D: alsa-util.c: Control: PCM Playback Volume
D: alsa-util.c: min_dB: -51
D: alsa-util.c: max_dB: 0
D: alsa-util.c: resolution: 256
D: alsa-util.c: Its setup is:
D: alsa-util.c:   stream       : PLAYBACK
D: alsa-util.c:   access       : MMAP_INTERLEAVED
D: alsa-util.c:   format       : S16_LE
D: alsa-util.c:   subformat    : STD
D: alsa-util.c:   channels     : 2
D: alsa-util.c:   rate         : 44100
D: alsa-util.c:   exact rate   : 44100 (44100/1)
D: alsa-util.c:   msbits       : 16
D: alsa-util.c:   buffer_size  : 3520
D: alsa-util.c:   period_size  : 352
D: alsa-util.c:   period_time  : 7981
D: alsa-util.c:   tstamp_mode  : ENABLE
D: alsa-util.c:   period_step  : 1
D: alsa-util.c:   avail_min    : 352
D: alsa-util.c:   period_event : 0
D: alsa-util.c:   start_threshold  : -1
D: alsa-util.c:   stop_threshold   : 1845493760
D: alsa-util.c:   silence_threshold: 0
D: alsa-util.c:   silence_size : 0
D: alsa-util.c:   boundary     : 1845493760
D: alsa-util.c: Slave: Hardware PCM card 0 'HDA Intel' device 0 subdevice 0
D: alsa-util.c: Its setup is:
D: alsa-util.c:   stream       : PLAYBACK
D: alsa-util.c:   access       : MMAP_INTERLEAVED
D: alsa-util.c:   format       : S16_LE
D: alsa-util.c:   subformat    : STD
D: alsa-util.c:   channels     : 2
D: alsa-util.c:   rate         : 44100
D: alsa-util.c:   exact rate   : 44100 (44100/1)
D: alsa-util.c:   msbits       : 16
D: alsa-util.c:   buffer_size  : 3520
D: alsa-util.c:   period_size  : 352
D: alsa-util.c:   period_time  : 7981
D: alsa-util.c:   tstamp_mode  : ENABLE
D: alsa-util.c:   period_step  : 1
D: alsa-util.c:   avail_min    : 352
D: alsa-util.c:   period_event : 0
D: alsa-util.c:   start_threshold  : -1
D: alsa-util.c:   stop_threshold   : 1845493760
D: alsa-util.c:   silence_threshold: 0
D: alsa-util.c:   silence_size : 0
D: alsa-util.c:   boundary     : 1845493760
D: alsa-sink.c: Requested volume: 0:  89% 1:  89%
D: alsa-sink.c: Got hardware volume: 0:  90% 1:  90%
D: alsa-sink.c: Calculated software volume: 0:  99% 1:  99%
D: alsa-sink.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+29
I: alsa-sink.c: Starting playback.
D: module-suspend-on-idle.c: Sink alsa_output.pci_8086_293e_sound_card_0 becomes idle.
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open front:0
I: alsa-source.c: Successfully opened device front:0.
I: alsa-source.c: Selected configuration 'Analog Stereo' (analog-stereo).
I: alsa-source.c: Successfully enabled mmap() mode.
I: alsa-sink.c: Underrun!
I: (alsa-lib)control.c: Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Capture".
I: module-device-restore.c: Restoring volume for source alsa_input.pci_8086_293e_sound_card_0.
I: module-device-restore.c: Restoring mute state for source alsa_input.pci_8086_293e_sound_card_0.
I: source.c: Created source 1 "alsa_input.pci_8086_293e_sound_card_0" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: source.c:     alsa.resolution_bits = "16"
I: source.c:     alsa.mixer_element = "Capture"
I: source.c:     device.api = "alsa"
I: source.c:     device.class = "sound"
I: source.c:     alsa.class = "generic"
I: source.c:     alsa.subclass = "generic-mix"
I: source.c:     alsa.name = "STAC92xx Analog"
I: source.c:     alsa.id = "STAC92xx Analog"
I: source.c:     alsa.subdevice = "0"
I: source.c:     alsa.subdevice_name = "subdevice #0"
I: source.c:     alsa.device = "0"
I: source.c:     alsa.card = "0"
I: source.c:     alsa.card_name = "HDA Intel"
I: source.c:     alsa.long_card_name = "HDA Intel at 0xf6afc000 irq 21"
I: source.c:     alsa.driver_name = "snd_hda_intel"
I: source.c:     device.bus_path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
I: source.c:     hal.udi = "/org/freedesktop/Hal/devices/pci_8086_293e_sound_card_0"
I: source.c:     hal.product = "HDA Intel Sound Card"
I: source.c:     hal.card_id = "HDA Intel"
I: source.c:     device.string = "front:0"
I: source.c:     device.buffering.buffer_size = "14080"
I: source.c:     device.buffering.fragment_size = "1408"
I: source.c:     device.access_mode = "mmap"
I: source.c:     device.profile.name = "analog-stereo"
I: source.c:     device.profile.description = "Analog Stereo"
I: source.c:     device.description = "HDA Intel"
I: source.c:     device.icon_name = "audio-card"
I: alsa-source.c: Using 10 fragments of size 1408 bytes, buffer time is 79.82ms
D: alsa-source.c: hwbuf_unused=0
D: alsa-source.c: setting avail_min=1
I: alsa-source.c: Volume ranges from 0 to 15.
I: alsa-source.c: Volume ranges from 0.00 dB to 22.50 dB.
I: alsa-source.c: Fixing base volume to -22.50 dB
I: alsa-util.c: All 2 channels can be mapped to mixer channels.
I: alsa-source.c: Using hardware volume control. Hardware dB scale supported.
D: alsa-util.c: snd_pcm_dump():
D: alsa-util.c: Soft volume PCM
D: alsa-util.c: Control: PCM Playback Volume
D: alsa-util.c: min_dB: -51
D: alsa-util.c: max_dB: 0
D: alsa-util.c: resolution: 256
D: alsa-util.c: Its setup is:
D: alsa-util.c:   stream       : CAPTURE
D: alsa-util.c:   access       : MMAP_INTERLEAVED
D: alsa-util.c:   format       : S16_LE
D: alsa-util.c:   subformat    : STD
D: alsa-util.c:   channels     : 2
D: alsa-util.c:   rate         : 44100
D: alsa-util.c:   exact rate   : 44100 (44100/1)
D: alsa-util.c:   msbits       : 16
D: alsa-util.c:   buffer_size  : 3520
D: alsa-util.c:   period_size  : 352
D: alsa-util.c:   period_time  : 7981
D: alsa-util.c:   tstamp_mode  : ENABLE
D: alsa-util.c:   period_step  : 1
D: alsa-util.c:   avail_min    : 352
D: alsa-util.c:   period_event : 0
D: alsa-util.c:   start_threshold  : -1
D: alsa-util.c:   stop_threshold   : 1845493760
D: alsa-util.c:   silence_threshold: 0
D: alsa-util.c:   silence_size : 0
D: alsa-util.c:   boundary     : 1845493760
D: alsa-util.c: Slave: Hardware PCM card 0 'HDA Intel' device 0 subdevice 0
D: alsa-util.c: Its setup is:
D: alsa-util.c:   stream       : CAPTURE
D: alsa-util.c:   access       : MMAP_INTERLEAVED
D: alsa-util.c:   format       : S16_LE
D: alsa-util.c:   subformat    : STD
D: alsa-util.c:   channels     : 2
D: alsa-util.c:   rate         : 44100
D: alsa-util.c:   exact rate   : 44100 (44100/1)
D: alsa-util.c:   msbits       : 16
D: alsa-util.c:   buffer_size  : 3520
D: alsa-util.c:   period_size  : 352
D: alsa-util.c:   period_time  : 7981
D: alsa-util.c:   tstamp_mode  : ENABLE
D: alsa-util.c:   period_step  : 1
D: alsa-util.c:   avail_min    : 352
D: alsa-util.c:   period_event : 0
D: alsa-util.c:   start_threshold  : -1
D: alsa-util.c:   stop_threshold   : 1845493760
D: alsa-util.c:   silence_threshold: 0
D: alsa-util.c:   silence_size : 0
D: alsa-util.c:   boundary     : 1845493760
D: alsa-source.c: Requested volume: 0: 100% 1: 100%
D: alsa-source.c: Got hardware volume: 0: 100% 1: 100%
D: alsa-source.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+28
D: alsa-source.c: Calculated software volume: 0: 100% 1: 100%
D: module-suspend-on-idle.c: Source alsa_input.pci_8086_293e_sound_card_0 becomes idle.
I: module.c: Loaded "module-alsa-card" (index: #5; argument: "device_id=0 name=pci_8086_293e_sound_card_0 card_name=alsa_card.pci_8086_293e_sound_card_0 tsched=0").
D: module-hal-detect.c: Loaded device /org/freedesktop/Hal/devices/pci_8086_293e_sound_card_0_alsa_control__1
I: module-hal-detect.c: Loaded 1 modules.
I: module.c: Loaded "module-hal-detect" (index: #6; argument: "tsched=0").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9.15/modules/module-bluetooth-discover.so': success
D: module-hal-detect.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
D: bluetooth-util.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
I: module.c: Loaded "module-bluetooth-discover" (index: #7; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9.15/modules/module-esound-protocol-unix.so': success
I: module.c: Loaded "module-esound-protocol-unix" (index: #8; argument: "").
I: module.c: Loaded "module-native-protocol-unix" (index: #9; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9.15/modules/module-gconf.so': success
I: module.c: Loaded "module-gconf" (index: #10; argument: "").
I: module-default-device-restore.c: Restored default sink 'alsa_output.pci_8086_293e_sound_card_0'.
D: core-subscribe.c: Dropped redundant event due to change event.
I: module-default-device-restore.c: Restored default source 'alsa_input.pci_8086_293e_sound_card_0'.
I: module.c: Loaded "module-default-device-restore" (index: #11; argument: "").
I: module.c: Loaded "module-rescue-streams" (index: #12; argument: "").
I: module.c: Loaded "module-always-sink" (index: #13; argument: "").
I: client.c: Created 0 "ConsoleKit Session /org/freedesktop/ConsoleKit/Session3"
D: module-console-kit.c: Added new session /org/freedesktop/ConsoleKit/Session3
I: module.c: Loaded "module-console-kit" (index: #14; argument: "").
I: module.c: Loaded "module-position-event-sounds" (index: #15; argument: "").
I: module.c: Loaded "module-cork-music-on-phone" (index: #16; argument: "").
D: main.c: Got org.pulseaudio.Server!
I: main.c: Daemon startup complete.
I: client.c: Created 1 "Native client (UNIX socket client)"
D: protocol-native.c: Protocol version: remote 15, local 15
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
D: protocol-native.c: SHM possible: yes
D: protocol-native.c: Negotiated SHM: yes
D: module-augment-properties.c: Looking for .desktop file for totem-gstreamer
I: client.c: Freed 1 "Totem Movie Player"
I: protocol-native.c: Connection died.
I: module-suspend-on-idle.c: Sink alsa_output.pci_8086_293e_sound_card_0 idle for too long, suspending ...
I: alsa-sink.c: Device suspended...
I: module-suspend-on-idle.c: Source alsa_input.pci_8086_293e_sound_card_0 idle for too long, suspending ...
I: alsa-source.c: Device suspended...
I: client.c: Created 2 "Native client (UNIX socket client)"
D: protocol-native.c: Protocol version: remote 15, local 15
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
D: protocol-native.c: SHM possible: yes
D: protocol-native.c: Negotiated SHM: yes
D: module-augment-properties.c: Looking for .desktop file for totem-gstreamer
I: module-stream-restore.c: Restoring volume for sink input sink-input-by-media-role:video.
I: module-stream-restore.c: Restoring mute state for sink input sink-input-by-media-role:video.
D: reserve-wrap.c: Successfully acquired reservation lock on device 'Audio0'
I: alsa-sink.c: Trying resume...
D: alsa-sink.c: hwbuf_unused=0
D: alsa-sink.c: setting avail_min=1
I: alsa-sink.c: Resumed successfully...
I: alsa-sink.c: Starting playback.
D: module-suspend-on-idle.c: Sink alsa_output.pci_8086_293e_sound_card_0 becomes idle.
D: module-suspend-on-idle.c: Sink alsa_output.pci_8086_293e_sound_card_0 becomes busy.
D: memblockq.c: memblockq requested: maxlength=33554432, tlength=0, base=4, prebuf=0, minreq=1 maxrewind=0
D: memblockq.c: memblockq sanitized: maxlength=33554432, tlength=33554432, base=4, prebuf=0, minreq=4 maxrewind=0
I: sink-input.c: Created input 0 "Playback Stream" on alsa_output.pci_8086_293e_sound_card_0 with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: protocol-native.c: Requested tlength=200.00 ms, minreq=10.00 ms
D: protocol-native.c: Adjust latency mode enabled, configuring sink latency to half of overall latency.
D: memblockq.c: memblockq requested: maxlength=70560, tlength=21204, base=4, prebuf=19444, minreq=1764 maxrewind=0
D: memblockq.c: memblockq sanitized: maxlength=70560, tlength=21204, base=4, prebuf=19444, minreq=1764 maxrewind=0
I: protocol-native.c: Final latency 200.02 ms = 100.20 ms + 2*10.00 ms + 79.82 ms
D: alsa-sink.c: Requested volume: 0:  99% 1:  99%
D: alsa-sink.c: Got hardware volume: 0: 100% 1: 100%
D: alsa-sink.c: Calculated software volume: 0:  99% 1:  99%
D: core-subscribe.c: Dropped redundant event due to change event.
D: alsa-sink.c: Requested to rewind 14080 bytes.
D: alsa-sink.c: Limited to 10552 bytes.
D: alsa-sink.c: before: 2638
D: alsa-sink.c: after: 2638
D: alsa-sink.c: Rewound 10552 bytes.
D: sink.c: Processing rewind...
D: sink-input.c: Have to rewind 10552 bytes on render memblockq.
D: source.c: Processing rewind...
D: sink-input.c: Requesting rewind due to uncorking
D: alsa-sink.c: Requested to rewind 14080 bytes.
D: alsa-sink.c: Limited to 10552 bytes.
D: alsa-sink.c: before: 2638
D: alsa-sink.c: after: 2638
D: alsa-sink.c: Rewound 10552 bytes.
D: sink.c: Processing rewind...
D: source.c: Processing rewind...
D: module-suspend-on-idle.c: Sink alsa_output.pci_8086_293e_sound_card_0 becomes busy.
D: protocol-native.c: Requesting rewind due to end of underrun.
D: protocol-native.c: Requesting rewind due to end of underrun.
E: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
E: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
E: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
D: alsa-sink.c: Requested volume: 0:  89% 1:  89%
D: alsa-sink.c: Got hardware volume: 0:  90% 1:  90%
D: alsa-sink.c: Calculated software volume: 0:  99% 1:  99%
D: alsa-sink.c: Requested to rewind 14080 bytes.
D: alsa-sink.c: Limited to 10552 bytes.
D: alsa-sink.c: before: 2638
D: alsa-sink.c: after: 2638
D: alsa-sink.c: Rewound 10552 bytes.
D: sink.c: Processing rewind...
D: source.c: Processing rewind...
D: module-suspend-on-idle.c: Sink alsa_output.pci_8086_293e_sound_card_0 becomes idle.
D: module-suspend-on-idle.c: Sink alsa_output.pci_8086_293e_sound_card_0 becomes idle.
D: core-subscribe.c: Dropped redundant event due to change event.
D: core.c: Hmm, no streams around, trying to vacuum.
I: sink-input.c: Freeing input 0 "Playback Stream"
I: protocol-native.c: Connection died.
I: client.c: Freed 2 "Totem Movie Player"
I: module-suspend-on-idle.c: Sink alsa_output.pci_8086_293e_sound_card_0 idle for too long, suspending ...
I: alsa-sink.c: Device suspended...

```

Finally, a listing of my sound devices:
```

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

If additional information is required, just ask.

---

### Post by AutoStatic on 2009-10-26
Hello Accidus, you could try adding this line to your */etc/modprobe.d/alsa-base.conf* file instead of the *model=dell-bios* entry:
```
options snd-hda-intel enable_msi=1
```

But it worked before so it's probably PulseAudio related. What you could try also is to rename your .pulse directory in your home directory.

---

### Post by Accidus on 2009-10-26
Thanks. I tried both solutions (including restarting and checking that alsamixer isn't muted), but they didn't work.

---

### Post by AutoStatic on 2009-10-26
But do you have no sound at all or no sound with PulseAudio?

---

### Post by Accidus on 2009-10-26
No sound at all, even if I try changing the various playback options in sound preferences.

---

### Post by AutoStatic on 2009-10-26
Then it's not PulseAudio but something else. How does your */etc/modprobe.d/alsa-base.conf* look right now? And is it possible to install the package *alsamixergui* with Synaptic and post a screenshot of *alsamixergui*?

---

### Post by Accidus on 2009-10-26
Of course. Attached is the required screenshot. Contents of /etc/modprobe.d/alsa-base.conf:
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
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2

#dell amendment to make mic and headphone jacks work
options snd-hda-intel enable_msi=1

```

---

### Post by AutoStatic on 2009-10-26
Thanks! Your alsa-base.conf looks good. alsamixergui unfortunately doesn't show the settings I'd like to see. Could you open a terminal and start it from there with the command **alsamixergui -c1** and post a screenshot from those settings?

---

### Post by Accidus on 2009-10-26
Thanks. See attachment. The only difference was that I had to type -c0 and not -c1.

---

### Post by Ulysses361 on 2009-10-27
@Accidus: your first ALSA issue is this:

!!ALSA Version
!!------------

Driver version:     1.0.18rc3
Library version:    1.0.19
Utilities version:  1.0.18


Your ALSA driver version is not the same version as your ALSA library version. 

In order to upgrade the ALSA driver, library and utilites to the same new version (version 1.0.21), please execute step 1 and then send us the full output from step 3 and step 4 in this procedure:

[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

---

### Post by Ulysses361 on 2009-10-27
Please make sure to reboot your pc after step 1 and before step 3 and step 4

---

### Post by Accidus on 2009-10-27
Great! Now sound and mic work (even with Skype). So the problem was incompatible versions of driver, utils and lib.

Now onwards to setup the camera.

The log information you asked for:

Pastebin contents:
```

   1. ################################
   2. ALSA Information Script v 0.4.58
   3. ################################
   4.  
   5. Script ran on: Tue Oct 27 11:23:52 UTC 2009
   6.  
   7.  
   8. Linux Distribution
   9. ------------------
  10.  
  11. Ubuntu 9.04 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 9.04"
  12.  
  13.  
  14. DMI Information
  15. ---------------
  16.  
  17. Manufacturer:      Dell Inc.
  18. Product Name:      Inspiron 1545                  
  19.  
  20.  
  21. Kernel Information
  22. ------------------
  23.  
  24. Kernel release:    2.6.28-16-generic
  25. Operating System:  GNU/Linux
  26. Architecture:      i686
  27. Processor:         unknown
  28. SMP Enabled:       Yes
  29.  
  30.  
  31. ALSA Version
  32. ------------
  33.  
  34. Driver version:     1.0.21
  35. Library version:    1.0.21a
  36. Utilities version:  1.0.21
  37.  
  38.  
  39. Loaded ALSA modules
  40. -------------------
  41.  
  42. snd_hda_intel
  43.  
  44.  
  45. Sound Servers on this system
  46. ----------------------------
  47.  
  48. Pulseaudio:
  49.      Installed - Yes (/usr/bin/pulseaudio)
  50.      Running - Yes
  51.  
  52. ESound Daemon:
  53.      Installed - Yes (/usr/bin/esd)
  54.      Running - No
  55.  
  56.  
  57. Soundcards recognised by ALSA
  58. -----------------------------
  59.  
  60. 0 [Intel          ]: HDA-Intel - HDA Intel
  61.                      HDA Intel at 0xf6afc000 irq 2297
  62.  
  63.  
  64. PCI Soundcards installed in the system
  65. --------------------------------------
  66.  
  67. 00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
  68.  
  69.  
  70. Advanced information - PCI Vendor/Device/Susbsystem ID's
  71. --------------------------------------------------------
  72.  
  73. 00:1b.0 0403: 8086:293e (rev 03)
  74.         Subsystem: 1028:02aa
  75.  
  76.  
  77. Modprobe options (Sound related)
  78. --------------------------------
  79.  
  80. snd-atiixp-modem: index=-2
  81. snd-intel8x0m: index=-2
  82. snd-via82xx-modem: index=-2
  83. snd-usb-audio: index=-2
  84. snd-usb-us122l: index=-2
  85. snd-usb-usx2y: index=-2
  86. snd-usb-caiaq: index=-2
  87. snd-cmipci: mpu_port=0x330 fm_port=0x388
  88. snd-pcsp: index=-2
  89. snd-hda-intel: enable_msi=1
  90.  
  91.  
  92. Loaded sound module options
  93. --------------------------
  94.  
  95. Module: snd_hda_intel
  96.         bdl_pos_adj : 1,-1,-1,-1,-1,-1,-1,-1
  97.         enable : Y,Y,Y,Y,Y,Y,Y,Y
  98.         enable_msi : 1
  99.         id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
 100.         index : -1,-1,-1,-1,-1,-1,-1,-1
 101.         model : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
 102.         patch : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
 103.         position_fix : 0,0,0,0,0,0,0,0
 104.         power_save : 0
 105.         power_save_controller : Y
 106.         probe_mask : -1,-1,-1,-1,-1,-1,-1,-1
 107.         probe_only : N,N,N,N,N,N,N,N
 108.         single_cmd : N
 109.  
 110.  
 111. HDA-Intel Codec information
 112. ---------------------------
 113. (following section hidden - click to display)

   1.  
   2. Codec: IDT 92HD71B7X
   3. Address: 0
   4. Function Id: 0x1
   5. Vendor Id: 0x111d76b2
   6. Subsystem Id: 0x102802aa
   7. Revision Id: 0x100302
   8. No Modem Function Group found
   9. Default PCM:
  10.    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
  11.    bits [0xe]: 16 20 24
  12.    formats [0x1]: PCM
  13. Default Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  14. Default Amp-Out caps: ofs=0x7f, nsteps=0x7f, stepsize=0x02, mute=1
  15. GPIO: io=8, o=0, i=0, unsolicited=1, wake=1
  16.  IO[0]: enable=1, dir=1, wake=0, sticky=0, data=1, unsol=0
  17.  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  18.  IO[2]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  19.  IO[3]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  20.  IO[4]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  21.  IO[5]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  22.  IO[6]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  23.  IO[7]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  24. Power-Map: 0x00
  25. Analog Loopback: 0x00
  26. Node 0x0a [Pin Complex] wcaps 0x400181: Stereo
  27.  Pincap 0x0000001c: OUT HP Detect
  28.  Pin Default 0x0421101f: [Jack] HP Out at Ext Right
  29.    Conn = 1/8, Color = Black
  30.    DefAssociation = 0x1, Sequence = 0xf
  31.  Pin-ctls: 0xc0: OUT HP
  32.  Unsolicited: tag=01, enabled=1
  33.  Connection: 3
  34.     0x10 0x11* 0x17
  35. Node 0x0b [Pin Complex] wcaps 0x400081: Stereo
  36.  Pincap 0x00001724: IN Detect
  37.    Vref caps: HIZ 50 GRD 80
  38.  Pin Default 0x04a11221: [Jack] Mic at Ext Right
  39.    Conn = 1/8, Color = Black
  40.    DefAssociation = 0x2, Sequence = 0x1
  41.  Pin-ctls: 0x24: IN VREF_80
  42.  Unsolicited: tag=02, enabled=1
  43. Node 0x0c [Pin Complex] wcaps 0x400081: Stereo
  44.  Pincap 0x00001724: IN Detect
  45.    Vref caps: HIZ 50 GRD 80
  46.  Pin Default 0x90a70330: [Fixed] Mic at Int N/A
  47.    Conn = Analog, Color = Unknown
  48.    DefAssociation = 0x3, Sequence = 0x0
  49.    Misc = NO_PRESENCE
  50.  Pin-ctls: 0x24: IN VREF_80
  51.  Unsolicited: tag=00, enabled=0
  52. Node 0x0d [Pin Complex] wcaps 0x400181: Stereo
  53.  Pincap 0x00000014: OUT Detect
  54.  Pin Default 0x90170110: [Fixed] Speaker at Int N/A
  55.    Conn = Analog, Color = Unknown
  56.    DefAssociation = 0x1, Sequence = 0x0
  57.    Misc = NO_PRESENCE
  58.  Pin-ctls: 0x00:
  59.  Unsolicited: tag=00, enabled=0
  60.  Connection: 3
  61.     0x10* 0x11 0x17
  62. Node 0x0e [Pin Complex] wcaps 0x400081: Stereo
  63.  Pincap 0x00001724: IN Detect
  64.    Vref caps: HIZ 50 GRD 80
  65.  Pin Default 0x40f000f0: [N/A] Other at Ext N/A
  66.    Conn = Unknown, Color = Unknown
  67.    DefAssociation = 0xf, Sequence = 0x0
  68.  Pin-ctls: 0x00: VREF_HIZ
  69.  Unsolicited: tag=00, enabled=0
  70. Node 0x0f [Pin Complex] wcaps 0x400181: Stereo
  71.  Pincap 0x00000014: OUT Detect
  72.  Pin Default 0x40f000f0: [N/A] Other at Ext N/A
  73.    Conn = Unknown, Color = Unknown
  74.    DefAssociation = 0xf, Sequence = 0x0
  75.  Pin-ctls: 0x00:
  76.  Unsolicited: tag=00, enabled=0
  77.  Connection: 3
  78.     0x10* 0x11 0x17
  79. Node 0x10 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out R/L
  80.  Amp-Out caps: N/A
  81.  Amp-Out vals:  [0x5a 0x5a]
  82.  Converter: stream=0, channel=0
  83.  Power: setting=D0, actual=D0
  84.  Delay: 13 samples
  85. Node 0x11 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out R/L
  86.  Amp-Out caps: N/A
  87.  Amp-Out vals:  [0x65 0x65]
  88.  Converter: stream=0, channel=0
  89.  Power: setting=D0, actual=D0
  90.  Delay: 13 samples
  91. Node 0x12 [Audio Input] wcaps 0x1d0541: Stereo
  92.  Converter: stream=0, channel=0
  93.  SDI-Select: 0
  94.  Power: setting=D3, actual=D3
  95.  Delay: 13 samples
  96.  Connection: 1
  97.     0x1c
  98.  Processing caps: benign=0, ncoeff=0
  99. Node 0x13 [Audio Input] wcaps 0x1d0541: Stereo
 100.  Converter: stream=0, channel=0
 101.  SDI-Select: 0
 102.  Power: setting=D3, actual=D3
 103.  Delay: 13 samples
 104.  Connection: 1
 105.     0x1d
 106.  Processing caps: benign=0, ncoeff=0
 107. Node 0x14 [Pin Complex] wcaps 0x400100: Mono
 108.  Pincap 0x00000010: OUT
 109.  Pin Default 0x40f000f0: [N/A] Other at Ext N/A
 110.    Conn = Unknown, Color = Unknown
 111.    DefAssociation = 0xf, Sequence = 0x0
 112.  Pin-ctls: 0x00:
 113.  Connection: 1
 114.     0x16
 115. Node 0x15 [Audio Selector] wcaps 0x300101: Stereo
 116.  Connection: 3
 117.     0x10* 0x11 0x17
 118. Node 0x16 [Audio Mixer] wcaps 0x200100: Mono
 119.  Connection: 1
 120.     0x15
 121. Node 0x17 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
 122.  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
 123.  Amp-In vals:  [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97]
 124.  Connection: 5
 125.     0x10 0x11 0x27 0x1a 0x1b
 126. Node 0x18 [Pin Complex] wcaps 0x40000d: Stereo Amp-Out
 127.  Amp-Out caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
 128.  Amp-Out vals:  [0x00 0x00]
 129.  Pincap 0x00000020: IN
 130.  Pin Default 0x90a000f0: [Fixed] Mic at Int N/A
 131.    Conn = Unknown, Color = Unknown
 132.    DefAssociation = 0xf, Sequence = 0x0
 133.  Pin-ctls: 0x20: IN
 134. Node 0x19 [Pin Complex] wcaps 0x40000d: Stereo Amp-Out
 135.  Amp-Out caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
 136.  Amp-Out vals:  [0x00 0x00]
 137.  Pincap 0x00000020: IN
 138.  Pin Default 0x40f000f0: [N/A] Other at Ext N/A
 139.    Conn = Unknown, Color = Unknown
 140.    DefAssociation = 0xf, Sequence = 0x0
 141.  Pin-ctls: 0x00:
 142. Node 0x1a [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
 143.  Amp-Out caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
 144.  Amp-Out vals:  [0x03 0x03]
 145.  Connection: 3
 146.     0x0b* 0x0c 0x0e
 147. Node 0x1b [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
 148.  Amp-Out caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
 149.  Amp-Out vals:  [0x03 0x03]
 150.  Connection: 3
 151.     0x0b* 0x0c 0x0e
 152. Node 0x1c [Audio Selector] wcaps 0x30090d: Stereo Amp-Out R/L
 153.  Amp-Out caps: ofs=0x00, nsteps=0x0f, stepsize=0x05, mute=1
 154.  Amp-Out vals:  [0x08 0x08]
 155.  Connection: 4
 156.     0x1a* 0x17 0x18 0x19
 157. Node 0x1d [Audio Selector] wcaps 0x30090d: Stereo Amp-Out R/L
 158.  Amp-Out caps: ofs=0x00, nsteps=0x0f, stepsize=0x05, mute=1
 159.  Amp-Out vals:  [0x8f 0x8f]
 160.  Connection: 4
 161.     0x1b* 0x17 0x18 0x19
 162. Node 0x1e [Pin Complex] wcaps 0x400301: Stereo Digital
 163.  Pincap 0x00000010: OUT
 164.  Pin Default 0x044413b0: [Jack] SPDIF Out at Ext Right
 165.    Conn = RCA, Color = Black
 166.    DefAssociation = 0xb, Sequence = 0x0
 167.    Misc = NO_PRESENCE
 168.  Pin-ctls: 0x40: OUT
 169.  Connection: 1
 170.     0x24
 171. Node 0x1f [Pin Complex] wcaps 0x400701: Stereo Digital
 172.  Pincap 0x00010010: OUT EAPD
 173.  EAPD 0x0:
 174.  Pin Default 0x044413b0: [Jack] SPDIF Out at Ext Right
 175.    Conn = RCA, Color = Black
 176.    DefAssociation = 0xb, Sequence = 0x0
 177.    Misc = NO_PRESENCE
 178.  Pin-ctls: 0x00:
 179.  Power: setting=D0, actual=D0
 180.  Connection: 2
 181.     0x24* 0x25
 182. Node 0x20 [Pin Complex] wcaps 0x400301: Stereo Digital
 183.  Pincap 0x00000010: OUT
 184.  Pin Default 0x40f000f6: [N/A] Other at Ext N/A
 185.    Conn = Unknown, Color = Unknown
 186.    DefAssociation = 0xf, Sequence = 0x6
 187.  Pin-ctls: 0x00:
 188.  Connection: 1
 189.     0x25
 190. Node 0x21 [Audio Output] wcaps 0x40211: Stereo Digital
 191.  Converter: stream=0, channel=0
 192.  Digital:
 193.  Digital category: 0x0
 194.  PCM:
 195.    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
 196.    bits [0xe]: 16 20 24
 197.    formats [0x5]: PCM AC3
 198.  Delay: 4 samples
 199. Node 0x22 [Audio Output] wcaps 0x40211: Stereo Digital
 200.  Converter: stream=0, channel=0
 201.  Digital:
 202.  Digital category: 0x0
 203.  PCM:
 204.    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
 205.    bits [0xe]: 16 20 24
 206.    formats [0x5]: PCM AC3
 207.  Delay: 4 samples
 208. Node 0x23 [Vendor Defined Widget] wcaps 0xf00000: Mono
 209. Node 0x24 [Audio Selector] wcaps 0x300101: Stereo
 210.  Connection: 3
 211.     0x21* 0x1c 0x1d
 212. Node 0x25 [Audio Selector] wcaps 0x300101: Stereo
 213.  Connection: 3
 214.     0x22* 0x1c 0x1d
 215. Node 0x26 [Beep Generator Widget] wcaps 0x70000c: Mono Amp-Out
 216.  Amp-Out caps: ofs=0x03, nsteps=0x03, stepsize=0x17, mute=1
 217.  Amp-Out vals:  [0x00]
 218. Node 0x27 [Pin Complex] wcaps 0x400000: Mono
 219.  Pincap 0x00000020: IN
 220.  Pin Default 0x40f000f7: [N/A] Other at Ext N/A
 221.    Conn = Unknown, Color = Unknown
 222.    DefAssociation = 0xf, Sequence = 0x7
 223.  Pin-ctls: 0x00:
 224. Node 0x28 [Volume Knob Widget] wcaps 0x600000: Mono
 225.  Volume-Knob: delta=1, steps=127, direct=1, val=127
 226.  Connection: 2
 227.     0x10 0x11
 228. (end collapsed section)

   1.  
   2.  
   3. ALSA Device nodes
   4. -----------------
   5.  
   6. crw-rw----  1 root audio 116,  0 Oct 27 11:12 /dev/snd/controlC0
   7. crw-rw----  1 root audio 116,  4 Oct 27 11:12 /dev/snd/hwC0D0
   8. crw-rw----  1 root audio 116, 24 Oct 27 11:19 /dev/snd/pcmC0D0c
   9. crw-rw----  1 root audio 116, 16 Oct 27 11:19 /dev/snd/pcmC0D0p
  10. crw-rw----  1 root audio 116, 17 Oct 27 11:12 /dev/snd/pcmC0D1p
  11. crw-rw----  1 root audio 116,  1 Oct 27 11:12 /dev/snd/seq
  12. crw-rw----  1 root audio 116, 33 Oct 27 11:12 /dev/snd/timer
  13.  
  14.  
  15. Aplay/Arecord output
  16. ------------
  17.  
  18. APLAY
  19.  
  20. **** List of PLAYBACK Hardware Devices ****
  21. card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  22.  Subdevices: 1/1
  23.  Subdevice #0: subdevice #0
  24. card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  25.  Subdevices: 1/1
  26.  Subdevice #0: subdevice #0
  27.  
  28. ARECORD
  29.  
  30. **** List of CAPTURE Hardware Devices ****
  31. card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  32.  Subdevices: 2/2
  33.  Subdevice #0: subdevice #0
  34.  Subdevice #1: subdevice #1
  35.  
  36. Amixer output
  37. -------------
  38.  
  39. -------Mixer controls for card 0 [Intel]
  40.  
  41. Card hw:0 'Intel'/'HDA Intel at 0xf6afc000 irq 2297'
  42.  Mixer name        : 'IDT 92HD71B7X'
  43.  Components        : 'HDA:111d76b2,102802aa,00100302'
  44.  Controls      : 24
  45.  Simple ctrls  : 15
  46. Simple mixer control 'Master',0
  47.  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  48.  Playback channels: Mono
  49.  Limits: Playback 0 - 64
  50.  Mono: Playback 54 [84%] [-7.50dB] [on]
  51. Simple mixer control 'Headphone',0
  52.  Capabilities: pvolume pswitch
  53.  Playback channels: Front Left - Front Right
  54.  Limits: Playback 0 - 64
  55.  Mono:
  56.  Front Left: Playback 48 [75%] [-12.00dB] [on]
  57.  Front Right: Playback 48 [75%] [-12.00dB] [on]
  58. Simple mixer control 'Speaker',0
  59.  Capabilities: pvolume pswitch
  60.  Playback channels: Front Left - Front Right
  61.  Limits: Playback 0 - 64
  62.  Mono:
  63.  Front Left: Playback 37 [58%] [-20.25dB] [on]
  64.  Front Right: Playback 37 [58%] [-20.25dB] [on]
  65. Simple mixer control 'PCM',0
  66.  Capabilities: pvolume
  67.  Playback channels: Front Left - Front Right
  68.  Limits: Playback 0 - 255
  69.  Mono:
  70.  Front Left: Playback 255 [100%] [0.00dB]
  71.  Front Right: Playback 255 [100%] [0.00dB]
  72. Simple mixer control 'Mic Jack Mode',0
  73.  Capabilities: enum
  74.  Items: 'Mic In' 'Line In'
  75.  Item0: 'Mic In'
  76. Simple mixer control 'IEC958',0
  77.  Capabilities: pswitch pswitch-joined
  78.  Playback channels: Mono
  79.  Mono: Playback [off]
  80. Simple mixer control 'IEC958 Default PCM',0
  81.  Capabilities: pswitch pswitch-joined
  82.  Playback channels: Mono
  83.  Mono: Playback [on]
  84. Simple mixer control 'Capture',0
  85.  Capabilities: cvolume cswitch
  86.  Capture channels: Front Left - Front Right
  87.  Limits: Capture 0 - 15
  88.  Front Left: Capture 8 [53%] [12.00dB] [on]
  89.  Front Right: Capture 8 [53%] [12.00dB] [on]
  90. Simple mixer control 'Capture',1
  91.  Capabilities: cvolume cswitch
  92.  Capture channels: Front Left - Front Right
  93.  Limits: Capture 0 - 15
  94.  Front Left: Capture 15 [100%] [22.50dB] [off]
  95.  Front Right: Capture 15 [100%] [22.50dB] [off]
  96. Simple mixer control 'Digital',0
  97.  Capabilities: cvolume
  98.  Capture channels: Front Left - Front Right
  99.  Limits: Capture 0 - 120
 100.  Front Left: Capture 60 [50%] [0.00dB]
 101.  Front Right: Capture 60 [50%] [0.00dB]
 102. Simple mixer control 'Input Source',0
 103.  Capabilities: cenum
 104.  Items: 'Mic' 'Front Mic' 'Digital Mic'
 105.  Item0: 'Mic'
 106. Simple mixer control 'Input Source',1
 107.  Capabilities: cenum
 108.  Items: 'Mic' 'Front Mic' 'Digital Mic'
 109.  Item0: 'Mic'
 110. Simple mixer control 'Mux',0
 111.  Capabilities: cvolume
 112.  Capture channels: Front Left - Front Right
 113.  Limits: Capture 0 - 3
 114.  Front Left: Capture 3 [100%] [30.00dB]
 115.  Front Right: Capture 3 [100%] [30.00dB]
 116. Simple mixer control 'Mux',1
 117.  Capabilities: cvolume
 118.  Capture channels: Front Left - Front Right
 119.  Limits: Capture 0 - 3
 120.  Front Left: Capture 3 [100%] [30.00dB]
 121.  Front Right: Capture 3 [100%] [30.00dB]
 122. Simple mixer control 'PC Beep',0
 123.  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
 124.  Playback channels: Mono
 125.  Limits: Playback 0 - 3
 126.  Mono: Playback 0 [0%] [-18.00dB] [off]
 127.  
 128.  
 129. Alsactl output
 130. -------------
 131.  
 132. (following section hidden - click to display)

   1. state.Intel {
   2.         control.1 {
   3.                 comment.access 'read write'
   4.                 comment.type INTEGER
   5.                 comment.count 2
   6.                 comment.range '0 - 64'
   7.                 comment.dbmin -4800
   8.                 comment.dbmax 0
   9.                 iface MIXER
  10.                 name 'Speaker Playback Volume'
  11.                 value.0 37
  12.                 value.1 37
  13.         }
  14.         control.2 {
  15.                 comment.access 'read write'
  16.                 comment.type BOOLEAN
  17.                 comment.count 2
  18.                 iface MIXER
  19.                 name 'Speaker Playback Switch'
  20.                 value.0 true
  21.                 value.1 true
  22.         }
  23.         control.3 {
  24.                 comment.access 'read write'
  25.                 comment.type ENUMERATED
  26.                 comment.count 1
  27.                 comment.item.0 'Mic In'
  28.                 comment.item.1 'Line In'
  29.                 iface MIXER
  30.                 name 'Mic Jack Mode'
  31.                 value 'Mic In'
  32.         }
  33.         control.4 {
  34.                 comment.access 'read write'
  35.                 comment.type BOOLEAN
  36.                 comment.count 1
  37.                 iface MIXER
  38.                 name 'PC Beep Playback Switch'
  39.                 value false
  40.         }
  41.         control.5 {
  42.                 comment.access 'read write'
  43.                 comment.type INTEGER
  44.                 comment.count 1
  45.                 comment.range '0 - 3'
  46.                 comment.dbmin -1800
  47.                 comment.dbmax 0
  48.                 iface MIXER
  49.                 name 'PC Beep Playback Volume'
  50.                 value 0
  51.         }
  52.         control.6 {
  53.                 comment.access 'read write'
  54.                 comment.type INTEGER
  55.                 comment.count 2
  56.                 comment.range '0 - 64'
  57.                 comment.dbmin -4800
  58.                 comment.dbmax 0
  59.                 iface MIXER
  60.                 name 'Headphone Playback Volume'
  61.                 value.0 48
  62.                 value.1 48
  63.         }
  64.         control.7 {
  65.                 comment.access 'read write'
  66.                 comment.type BOOLEAN
  67.                 comment.count 2
  68.                 iface MIXER
  69.                 name 'Headphone Playback Switch'
  70.                 value.0 true
  71.                 value.1 true
  72.         }
  73.         control.8 {
  74.                 comment.access 'read write'
  75.                 comment.type INTEGER
  76.                 comment.count 2
  77.                 comment.range '0 - 15'
  78.                 comment.dbmin 0
  79.                 comment.dbmax 2250
  80.                 iface MIXER
  81.                 name 'Capture Volume'
  82.                 value.0 8
  83.                 value.1 8
  84.         }
  85.         control.9 {
  86.                 comment.access 'read write'
  87.                 comment.type BOOLEAN
  88.                 comment.count 2
  89.                 iface MIXER
  90.                 name 'Capture Switch'
  91.                 value.0 true
  92.                 value.1 true
  93.         }
  94.         control.10 {
  95.                 comment.access 'read write'
  96.                 comment.type INTEGER
  97.                 comment.count 2
  98.                 comment.range '0 - 15'
  99.                 comment.dbmin 0
 100.                 comment.dbmax 2250
 101.                 iface MIXER
 102.                 name 'Capture Volume'
 103.                 index 1
 104.                 value.0 15
 105.                 value.1 15
 106.         }
 107.         control.11 {
 108.                 comment.access 'read write'
 109.                 comment.type BOOLEAN
 110.                 comment.count 2
 111.                 iface MIXER
 112.                 name 'Capture Switch'
 113.                 index 1
 114.                 value.0 false
 115.                 value.1 false
 116.         }
 117.         control.12 {
 118.                 comment.access 'read write'
 119.                 comment.type INTEGER
 120.                 comment.count 2
 121.                 comment.range '0 - 3'
 122.                 comment.dbmin 0
 123.                 comment.dbmax 3000
 124.                 iface MIXER
 125.                 name 'Mux Capture Volume'
 126.                 value.0 3
 127.                 value.1 3
 128.         }
 129.         control.13 {
 130.                 comment.access 'read write'
 131.                 comment.type INTEGER
 132.                 comment.count 2
 133.                 comment.range '0 - 3'
 134.                 comment.dbmin 0
 135.                 comment.dbmax 3000
 136.                 iface MIXER
 137.                 name 'Mux Capture Volume'
 138.                 index 1
 139.                 value.0 3
 140.                 value.1 3
 141.         }
 142.         control.14 {
 143.                 comment.access 'read write'
 144.                 comment.type ENUMERATED
 145.                 comment.count 1
 146.                 comment.item.0 Mic
 147.                 comment.item.1 'Front Mic'
 148.                 comment.item.2 'Digital Mic'
 149.                 iface MIXER
 150.                 name 'Input Source'
 151.                 value Mic
 152.         }
 153.         control.15 {
 154.                 comment.access 'read write'
 155.                 comment.type ENUMERATED
 156.                 comment.count 1
 157.                 comment.item.0 Mic
 158.                 comment.item.1 'Front Mic'
 159.                 comment.item.2 'Digital Mic'
 160.                 iface MIXER
 161.                 name 'Input Source'
 162.                 index 1
 163.                 value Mic
 164.         }
 165.         control.16 {
 166.                 comment.access read
 167.                 comment.type IEC958
 168.                 comment.count 1
 169.                 iface MIXER
 170.                 name 'IEC958 Playback Con Mask'
 171.                 value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
 172.         }
 173.         control.17 {
 174.                 comment.access read
 175.                 comment.type IEC958
 176.                 comment.count 1
 177.                 iface MIXER
 178.                 name 'IEC958 Playback Pro Mask'
 179.                 value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
 180.         }
 181.         control.18 {
 182.                 comment.access 'read write'
 183.                 comment.type IEC958
 184.                 comment.count 1
 185.                 iface MIXER
 186.                 name 'IEC958 Playback Default'
 187.                 value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
 188.         }
 189.         control.19 {
 190.                 comment.access 'read write'
 191.                 comment.type BOOLEAN
 192.                 comment.count 1
 193.                 iface MIXER
 194.                 name 'IEC958 Playback Switch'
 195.                 value false
 196.         }
 197.         control.20 {
 198.                 comment.access 'read write'
 199.                 comment.type BOOLEAN
 200.                 comment.count 1
 201.                 iface MIXER
 202.                 name 'IEC958 Default PCM Playback Switch'
 203.                 value true
 204.         }
 205.         control.21 {
 206.                 comment.access 'read write'
 207.                 comment.type INTEGER
 208.                 comment.count 1
 209.                 comment.range '0 - 64'
 210.                 comment.dbmin -4800
 211.                 comment.dbmax 0
 212.                 iface MIXER
 213.                 name 'Master Playback Volume'
 214.                 value 54
 215.         }
 216.         control.22 {
 217.                 comment.access 'read write'
 218.                 comment.type BOOLEAN
 219.                 comment.count 1
 220.                 iface MIXER
 221.                 name 'Master Playback Switch'
 222.                 value true
 223.         }
 224.         control.23 {
 225.                 comment.access 'read write user'
 226.                 comment.type INTEGER
 227.                 comment.count 2
 228.                 comment.range '0 - 255'
 229.                 comment.tlv '0000000100000008ffffec1400000014'
 230.                 comment.dbmin -5100
 231.                 comment.dbmax 0
 232.                 iface MIXER
 233.                 name 'PCM Playback Volume'
 234.                 value.0 255
 235.                 value.1 255
 236.         }
 237.         control.24 {
 238.                 comment.access 'read write user'
 239.                 comment.type INTEGER
 240.                 comment.count 2
 241.                 comment.range '0 - 120'
 242.                 comment.tlv '0000000100000008fffff44800000032'
 243.                 comment.dbmin -3000
 244.                 comment.dbmax 3000
 245.                 iface MIXER
 246.                 name 'Digital Capture Volume'
 247.                 value.0 60
 248.                 value.1 60
 249.         }
 250. }
 251. (end collapsed section)

   1.  
   2.  
   3. All Loaded Modules
   4. ------------------
   5.  
   6. Module
   7. binfmt_misc
   8. i915
   9. drm
  10. ppdev
  11. bridge
  12. stp
  13. bnep
  14. input_polldev
  15. lp
  16. parport
  17. snd_hda_codec_idt
  18. snd_hda_intel
  19. snd_hda_codec
  20. snd_hwdep
  21. snd_pcm_oss
  22. snd_mixer_oss
  23. snd_pcm
  24. snd_seq_dummy
  25. snd_seq_oss
  26. snd_seq_midi
  27. snd_rawmidi
  28. snd_seq_midi_event
  29. snd_seq
  30. snd_timer
  31. snd_seq_device
  32. joydev
  33. snd
  34. hid_microsoft
  35. ieee80211_crypt_tkip
  36. intel_agp
  37. usbhid
  38. pcspkr
  39. soundcore
  40. psmouse
  41. video
  42. dcdbas
  43. wl
  44. agpgart
  45. iTCO_wdt
  46. iTCO_vendor_support
  47. serio_raw
  48. output
  49. ieee80211_crypt
  50. snd_page_alloc
  51. usb_storage
  52. sky2
  53. fbcon
  54. tileblit
  55. font
  56. bitblit
  57. softcursor
  58.  
  59.  
  60. Sysfs Files
  61. -----------
  62.  
  63. /sys/class/sound/hwC0D0/init_pin_configs:
  64. 0x0a 0x0221101f
  65. 0x0b 0x02a11020
  66. 0x0c 0x95a70130
  67. 0x0d 0x90171110
  68. 0x0e 0x40f000f8
  69. 0x0f 0x40f000f2
  70. 0x14 0x40f000f3
  71. 0x18 0x40f000fa
  72. 0x19 0x40f000f4
  73. 0x1e 0x40f000f9
  74. 0x1f 0x40f000f5
  75. 0x20 0x40f000f6
  76. 0x27 0x40f000f7
  77.  
  78. /sys/class/sound/hwC0D0/driver_pin_configs:
  79. 0x0a 0x0421101f
  80. 0x0b 0x04a11221
  81. 0x0c 0x90a70330
  82. 0x0d 0x90170110
  83. 0x0e 0x40f000f0
  84. 0x0f 0x40f000f0
  85. 0x14 0x40f000f0
  86. 0x18 0x90a000f0
  87. 0x19 0x40f000f0
  88. 0x1e 0x044413b0
  89. 0x1f 0x044413b0
  90.  
  91. /sys/class/sound/hwC0D0/user_pin_configs:
  92.  
  93. /sys/class/sound/hwC0D0/init_verbs:
  94.  
  95.  
  96. ALSA/HDA dmesg
  97. ------------------
  98.  
  99. [   12.914589] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio2/input/input12
 100. [   13.097328] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
 101. [   13.097450] HDA Intel 0000:00:1b.0: irq 2297 for MSI/MSI-X
 102. [   13.097490] HDA Intel 0000:00:1b.0: setting latency timer to 64
 103. [   13.176941] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input13
 104. [   13.193105] input: HDA Intel Mic at Ext Right Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
 105. [   13.196227] input: HDA Intel HP Out at Ext Right Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15
 106. [   13.457894] lp: driver loaded but no devices found

```

Terminal logging:
```

Script started on Tue 27 Oct 2009 11:23:24 GMT
accidus@accidus-laptop:~$
accidus@accidus-laptop:~$ wget -O alsa-info.sh http://212.20.107.51/alsa-info.sh

--2009-10-27 11:23:38--  http://212.20.107.51/alsa-info.sh

Connecting to 212.20.107.51:80... connected.

HTTP request sent, awaiting response... 302 Found

Location: http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh [following]

--2009-10-27 11:23:38--  http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh

Resolving git.alsa-project.org... 212.20.107.51

Reusing existing connection to 212.20.107.51:80.

HTTP request sent, awaiting response... 200 OK

Length: unspecified [text/plain]

Saving to: `alsa-info.sh'




    [<=>                                                     ] 0           --.-K/s              
    [ <=>                                                    ] 26,584      --.-K/s   in 0.1s    



2009-10-27 11:23:38 (231 KB/s) - `alsa-info.sh' saved [26584]



accidus@accidus-laptop:~$
accidus@accidus-laptop:~$ bash alsa-info.sh --pastebin 

ALSA Information Script v 0.4.58

--------------------------------



This script visits the following commands/files to collect diagnostic

information about your ALSA installation and sound related hardware.



  dmesg

  lspci

  lsmod

  aplay

  amixer

  alsactl

  /proc/asound/

  /sys/class/sound/

  ~/.asoundrc (etc.)



See 'alsa-info.sh --help' for command line options.



Automatically upload ALSA information to pastebin? [y/N] : y

Uploading information to www.pastebin.ca ...  Done!



Your ALSA information is located at [31mhttp://pastebin.ca/xxxxxxx


Please inform the person helping you.



accidus@accidus-laptop:~$ cat /proc/asound/cards;  sudo aptitude install gnome-alsamixer asoundconf-gtk 
 alsa-utils flashplugin-nonfree-extrasound;  asoundconf list;  aplay -l;  sudo lshw -C sound;  ls 
 -lart /dev/snd;  cat /dev/sndstat; lspci -nn;  sudo which alsactl;  lsmod | grep snd 

 0 [Intel          ]: HDA-Intel - HDA Intel

                      HDA Intel at 0xf6afc000 irq 2297

[sudo] password for accidus: 




Reading package lists... Done



Building dependency tree... Done

Reading state information... Done



Reading extended state information... Done
Initialising package states... Done


Writing extended state information... Done


The following NEW packages will be installed:

  asoundconf-gtk flashplugin-nonfree-extrasound 

0 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.

Need to get 14.6kB of archives. After unpacking 135kB will be used.


Writing extended state information... Done




0% [Working]
            
Get:1 http://archive.ubuntu.com jaunty/universe asoundconf-gtk 1.6-0ubuntu1 [6444B]


            
17% [1 asoundconf-gtk 2582/6444B 40%]
                                     
Get:2 http://archive.ubuntu.com jaunty/multiverse flashplugin-nonfree-extrasound 0.0.svn2431-3 [8160B]


                                     
55% [2 flashplugin-nonfree-extrasound 1617/8160B 19%]
                                                     
100% [Working]
              
Fetched 14.6kB in 0s (144kB/s)


[###/                ] Collecting changes [0] - Stage 1/5                                       

                                                                                                
Committing to: /etc/

added asound.state


[###-                ] Collecting changes [1] - Stage 1/5                                       

                                                                                                
added init.d/alsasound

added modprobe.d/50-sound.conf


[###########\        ] Running pre_commit hooks - Stage 3/5                                     

                                                                                                
Committed revision 243.

Selecting previously deselected package asoundconf-gtk.

(Reading database ... 276653 files and directories currently installed.)

Unpacking asoundconf-gtk (from .../asoundconf-gtk_1.6-0ubuntu1_all.deb) ...

Selecting previously deselected package flashplugin-nonfree-extrasound.

Unpacking flashplugin-nonfree-extrasound (from .../flashplugin-nonfree-extrasound_0.0.svn2431-3_i386.deb) ...

Processing triggers for man-db ...

Setting up asoundconf-gtk (1.6-0ubuntu1) ...

Setting up flashplugin-nonfree-extrasound (0.0.svn2431-3) ...


Reading package lists...  Done



Building dependency tree... Done

Reading state information... Done


Reading extended state information... Done
Initialising package states... Done


Writing extended state information... Done




Names of available sound cards:

Intel

**** List of PLAYBACK Hardware Devices ****

card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]

  Subdevices: 1/1

  Subdevice #0: subdevice #0

card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]

  Subdevices: 1/1

  Subdevice #0: subdevice #0



DMI

   
SMP

   
PA-RISC

       
device-tree

           
SPD

   
memory

      
/proc/cpuinfo

             
CPUID

     
PCI (sysfs)

           
ISA PnP

       
PCMCIA

      
PCMCIA

      
kernel device tree (sysfs)

                          
USB

   
IDE

   
SCSI

    
Network interfaces

                  
Framebuffer devices

                   
Display

       
CPUFreq

       
ABI

   

  *-multimedia

       description: Audio device

       product: 82801I (ICH9 Family) HD Audio Controller

       vendor: Intel Corporation

       physical id: 1b

       bus info: pci@0000:00:1b.0

       version: 03

       width: 64 bits

       clock: 33MHz

       capabilities: pm msi pciexpress bus_master cap_list

       configuration: driver=HDA Intel latency=0 module=snd_hda_intel

[00mtotal 0

crw-rw----+  1 root audio 116, 33 2009-10-27 11:12 [40;33;01mtimer[00m

crw-rw----+  1 root audio 116,  1 2009-10-27 11:12 [40;33;01mseq[00m

crw-rw----+  1 root audio 116,  4 2009-10-27 11:12 [40;33;01mhwC0D0[00m

crw-rw----+  1 root audio 116,  0 2009-10-27 11:12 [40;33;01mcontrolC0[00m

drwxr-xr-x   2 root root      180 2009-10-27 11:12 [01;34m.[00m

crw-rw----+  1 root audio 116, 17 2009-10-27 11:12 [40;33;01mpcmC0D1p[00m

crw-rw----+  1 root audio 116, 16 2009-10-27 11:19 [40;33;01mpcmC0D0p[00m

crw-rw----+  1 root audio 116, 24 2009-10-27 11:19 [40;33;01mpcmC0D0c[00m

drwxr-xr-x  16 root root     4460 2009-10-27 11:25 [01;34m..[00m

[mSound Driver:3.8.1a-980706 (ALSA v1.0.21 emulation code)

Kernel: Linux accidus-laptop 2.6.28-16-generic #55-Ubuntu SMP Tue Oct 20 19:48:24 UTC 2009 i686

Config options: 0



Installed drivers: 

Type 10: ALSA emulation



Card config: 

HDA Intel at 0xf6afc000 irq 2297



Audio devices:

0: STAC92xx Analog (DUPLEX)



Synth devices: NOT ENABLED IN CONFIG



Midi devices: NOT ENABLED IN CONFIG



Timers:

7: system timer



Mixers:

0: IDT 92HD71B7X

00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)

00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)

00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 07)

00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)

00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)

00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)

00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)

00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)

00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)

00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)

00:1c.2 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 [8086:2944] (rev 03)

00:1c.4 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 [8086:2948] (rev 03)

00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)

00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)

00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)

00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)

00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)

00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03)

00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)

09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 13)

0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)

/usr/sbin/alsactl

snd_hda_codec_idt      65160  1 

snd_hda_intel          35712  2 

snd_hda_codec          87168  2 snd_hda_codec_idt,snd_hda_intel

snd_hwdep              15364  1 snd_hda_codec

snd_pcm_oss            45984  0 

snd_mixer_oss          22912  1 snd_pcm_oss

snd_pcm                83716  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss

snd_seq_dummy          10884  0 

snd_seq_oss            36224  0 

snd_seq_midi           14496  0 

snd_rawmidi            29984  1 snd_seq_midi

snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi

snd_seq                57584  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event

snd_timer              29192  2 snd_pcm,snd_seq

snd_seq_device         15372  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq

snd                    67236  18 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

soundcore              15200  1 snd

snd_page_alloc         17032  2 snd_hda_intel,snd_pcm

accidus@accidus-laptop:~$
accidus@accidus-laptop:~$ exit

exit


Script done on Tue 27 Oct 2009 11:25:59 GMT

```

Thanks a lot!

---

