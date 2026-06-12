---
title: "Help with Microphone on Thinkpad Edge on Maverick -- sort of urgent..."
date: 2010-10-30
forum: Multimedia Software
---

### Post by mercmobily on 2010-10-30
Hi people,

I have a Thinkpad edge. I am travelling right now, and will be for the next 2 weeks, and just discovered that my thinkpad's internam microphone won't work. Plugging in an external one won't work either.

This means that I won't be able to communicate with friends & family for 2 weeks... any help to patch this problem will be IMMENSELY welcome.

Symptoms are strange: I can go to Sound Preferences, select Analog Stereo Duplex as hardware, click on "Input", change the input volume, mute it, unmute it... everything works fine. However, if I tap against the mike, the input level bit doesn't move at all. Needless to say, nothing sees it.

Here is the output of the ALSA Information script... which looks like greek to me! Help...


!!################################
!!ALSA Information Script v 0.4.59
!!################################

!!Script ran on: Sat Oct 30 13:28:44 UTC 2010


!!Linux Distribution
!!------------------

Ubuntu 10.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.10"


!!DMI Information
!!---------------

Manufacturer:      LENOVO
Product Name:      01963HM


!!Kernel Information
!!------------------

Kernel release:    2.6.35-22-generic
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

snd_hda_intel
thinkpad_acpi


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
                      HDA Intel at 0xf0800000 irq 47
29 [ThinkPadEC     ]: ThinkPad EC - ThinkPad Console Audio Control
                      ThinkPad Console Audio Control at EC reg 0x30, fw 6YHT20WW-1.165000


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:293e (rev 03)
	Subsystem: 17aa:21b4


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

!!Module: snd_hda_intel
	bdl_pos_adj : 1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	beep_mode : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	enable_msi : -1
	id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	model : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	patch : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	position_fix : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	power_save : 0
	power_save_controller : Y
	probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	single_cmd : N

!!Module: thinkpad_acpi
	brightness_enable : 2
	brightness_mode : 2
	dbg_bluetoothemul : 0
	dbg_uwbemul : 0
	dbg_wlswemul : 0
	dbg_wwanemul : 0
	enable : Y
	experimental : 0
	fan_control : N
	force_load : N
	hotkey_report_mode : 0
	id : ThinkPadEC
	index : -536870912
	volume_capabilities : 0
	volume_control : N
	volume_mode : 3


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: Conexant CX20582 (Pebble)
Address: 0
Function Id: 0x1
Vendor Id: 0x14f15066
Subsystem Id: 0x17aa21b4
Revision Id: 0x100300
No Modem Function Group found
Default PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=4, o=0, i=0, unsolicited=1, wake=0
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[2]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[3]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Node 0x10 [Audio Output] wcaps 0xc1d: Stereo Amp-Out R/L
  Control: name="Master Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Device: name="CONEXANT Analog", type="Audio", device=0
  Amp-Out caps: ofs=0x4a, nsteps=0x4a, stepsize=0x03, mute=1
  Amp-Out vals:  [0x47 0x47]
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
Node 0x11 [Audio Output] wcaps 0xc1d: Stereo Amp-Out R/L
  Amp-Out caps: ofs=0x4a, nsteps=0x4a, stepsize=0x03, mute=1
  Amp-Out vals:  [0x3c 0x3c]
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
Node 0x12 [Audio Output] wcaps 0x611: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
Node 0x13 [Beep Generator Widget] wcaps 0x70000c: Mono Amp-Out
  Amp-Out caps: ofs=0x07, nsteps=0x07, stepsize=0x0f, mute=0
  Amp-Out vals:  [0x00]
Node 0x14 [Audio Input] wcaps 0x100d1b: Stereo Amp-In R/L
  Device: name="CONEXANT Analog", type="Audio", device=0
  Amp-In caps: ofs=0x4a, nsteps=0x50, stepsize=0x03, mute=1
  Amp-In vals:  [0x4a 0x4a] [0x80 0x80] [0x4a 0x4a] [0x80 0x80]
  Converter: stream=1, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 4
     0x17 0x18 0x23* 0x24
Node 0x15 [Audio Input] wcaps 0x100d1b: Stereo Amp-In R/L
  Amp-In caps: ofs=0x4a, nsteps=0x50, stepsize=0x03, mute=1
  Amp-In vals:  [0x4a 0x4a] [0x4a 0x4a] [0x4a 0x4a] [0x4a 0x4a]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 4
     0x17* 0x18 0x23 0x24
Node 0x16 [Audio Input] wcaps 0x100d1b: Stereo Amp-In R/L
  Amp-In caps: ofs=0x4a, nsteps=0x50, stepsize=0x03, mute=1
  Amp-In vals:  [0x4a 0x4a] [0x4a 0x4a] [0x4a 0x4a] [0x4a 0x4a]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 4
     0x17* 0x18 0x23 0x24
Node 0x17 [Audio Selector] wcaps 0x30050d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x04, stepsize=0x27, mute=0
  Amp-Out vals:  [0x03 0x03]
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 4
     0x1a 0x1b* 0x1d 0x1e
Node 0x18 [Audio Selector] wcaps 0x30050d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x04, stepsize=0x27, mute=0
  Amp-Out vals:  [0x00 0x00]
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 4
     0x1a* 0x1b 0x1d 0x1e
Node 0x19 [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x0000001c: OUT HP Detect
  Pin Default 0x042110f0: [Jack] HP Out at Ext Right
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=37, enabled=1
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 2
     0x10* 0x11
Node 0x1a [Pin Complex] wcaps 0x400481: Stereo
  Pincap 0x00001324: IN Detect
    Vref caps: HIZ 50 80
  Pin Default 0x95a701f0: [Fixed] Mic at Int Top
    Conn = Analog, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
Node 0x1b [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x00011334: IN OUT EAPD Detect
    Vref caps: HIZ 50 80
  EAPD 0x2: EAPD
  Pin Default 0x04a110f0: [Jack] Mic at Ext Right
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00: VREF_HIZ
  Unsolicited: tag=38, enabled=1
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 2
     0x10* 0x11
Node 0x1c [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x00000014: OUT Detect
  Pin Default 0x400001f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 2
     0x10* 0x11
Node 0x1d [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x00010034: IN OUT EAPD Detect
  EAPD 0x2: EAPD
  Pin Default 0x400001f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 2
     0x10* 0x11
Node 0x1e [Pin Complex] wcaps 0x400481: Stereo
  Pincap 0x00000024: IN Detect
  Pin Default 0x400001f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
Node 0x1f [Pin Complex] wcaps 0x400501: Stereo
  Pincap 0x00000010: OUT
  Pin Default 0x921701f0: [Fixed] Speaker at Int Front
    Conn = Analog, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 2
     0x10* 0x11
Node 0x20 [Pin Complex] wcaps 0x400781: Stereo Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x400001f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 1
     0x12
Node 0x21 [Audio Output] wcaps 0x611: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
Node 0x22 [Pin Complex] wcaps 0x400781: Stereo Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x400001f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 1
     0x21
Node 0x23 [Pin Complex] wcaps 0x40040b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x04, stepsize=0x2f, mute=0
  Amp-In vals:  [0x03 0x03]
  Pincap 0x00000020: IN
  Pin Default 0x400001f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
Node 0x24 [Audio Mixer] wcaps 0x20050b: Stereo Amp-In
  Amp-In caps: ofs=0x4a, nsteps=0x4a, stepsize=0x03, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 2
     0x10 0x11
Node 0x25 [Vendor Defined Widget] wcaps 0xf00000: Mono
Codec: Intel Cantiga HDMI
Address: 1
Function Id: 0x1
Vendor Id: 0x80862802
Subsystem Id: 0x80860101
Revision Id: 0x100000
No Modem Function Group found
Default PCM:
    rates [0x0]:
    bits [0x0]:
    formats [0x0]:
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x02 [Audio Output] wcaps 0x6211: 8-Channels Digital
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Device: name="INTEL HDMI 0", type="HDMI", device=3
  Converter: stream=8, channel=0
  Digital: Enabled GenLevel
  Digital category: 0x2
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0x1e]: 16 20 24 32
    formats [0x5]: PCM AC3
Node 0x03 [Pin Complex] wcaps 0x40739d: 8-Channels Digital Amp-Out CP
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x00000094: OUT Detect HDMI
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=03, enabled=1
  Connection: 1
     0x02
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116, 10 Oct 30 15:13 /dev/snd/controlC0
crw-rw----+ 1 root audio 116,  4 Oct 30 15:13 /dev/snd/controlC29
crw-rw----+ 1 root audio 116,  9 Oct 30 15:13 /dev/snd/hwC0D0
crw-rw----+ 1 root audio 116,  8 Oct 30 15:13 /dev/snd/hwC0D1
crw-rw----+ 1 root audio 116,  7 Oct 30 15:13 /dev/snd/pcmC0D0c
crw-rw----+ 1 root audio 116,  6 Oct 30 15:13 /dev/snd/pcmC0D0p
crw-rw----+ 1 root audio 116,  5 Oct 30 15:13 /dev/snd/pcmC0D3p
crw-rw----+ 1 root audio 116,  3 Oct 30 15:13 /dev/snd/seq
crw-rw----+ 1 root audio 116,  2 Oct 30 15:13 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  80 Oct 30 15:13 .
drwxr-xr-x 3 root root 240 Oct 30 15:13 ..
lrwxrwxrwx 1 root root  12 Oct 30 15:13 pci-0000:00:1b.0 -> ../controlC0
lrwxrwxrwx 1 root root  13 Oct 30 15:13 platform-thinkpad_acpi -> ../controlC29


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI 0 [INTEL HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [Intel]

Card hw:0 'Intel'/'HDA Intel at 0xf0800000 irq 47'
  Mixer name	: 'Intel Cantiga HDMI'
  Components	: 'HDA:14f15066,17aa21b4,00100300 HDA:80862802,80860101,00100000'
  Controls      : 11
  Simple ctrls  : 6
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 74
  Mono:
  Front Left: Playback 71 [96%] [-3.00dB] [on]
  Front Right: Playback 71 [96%] [-3.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 254 [100%] [0.20dB]
  Front Right: Playback 254 [100%] [0.20dB]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 80
  Front Left: Capture 74 [92%] [0.00dB] [on]
  Front Right: Capture 74 [92%] [0.00dB] [on]
Simple mixer control 'Analog Mic Boost',0
  Capabilities: cenum
  Items: '0dB' '10dB' '20dB' '30dB' '40dB'
  Item0: '30dB'
Simple mixer control 'Digital',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 120
  Front Left: Capture 74 [62%] [7.00dB]
  Front Right: Capture 74 [62%] [7.00dB]

!!-------Mixer controls for card 29 [ThinkPadEC]

Card hw:29 'ThinkPadEC'/'ThinkPad Console Audio Control at EC reg 0x30, fw 6YHT20WW-1.165000'
  Mixer name	: 'ThinkPad EC 6YHT20WW-1.165000'
  Components	: ''
  Controls      : 1
  Simple ctrls  : 1
Simple mixer control 'Console',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]


!!Alsactl output
!!-------------

--startcollapse--
state.Intel {
	control.1 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 74'
		comment.dbmin -7400
		comment.dbmax 0
		iface MIXER
		name 'Master Playback Volume'
		value.0 71
		value.1 71
	}
	control.2 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Master Playback Switch'
		value true
	}
	control.3 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 '0dB'
		comment.item.1 '10dB'
		comment.item.2 '20dB'
		comment.item.3 '30dB'
		comment.item.4 '40dB'
		iface MIXER
		name 'Analog Mic Boost Capture Enum'
		value '30dB'
	}
	control.4 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 80'
		comment.dbmin -7400
		comment.dbmax 600
		iface MIXER
		name 'Capture Volume'
		value.0 74
		value.1 74
	}
	control.5 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Capture Switch'
		value.0 true
		value.1 true
	}
	control.6 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Con Mask'
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.7 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.8 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Default'
		value '0482000200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.9 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Switch'
		value true
	}
	control.10 {
		comment.access 'read write user'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 255'
		comment.tlv '0000000100000008ffffec1400000014'
		comment.dbmin -5100
		comment.dbmax 0
		iface MIXER
		name 'PCM Playback Volume'
		value.0 254
		value.1 254
	}
	control.11 {
		comment.access 'read write user'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 120'
		comment.tlv '0000000100000008fffff44800000032'
		comment.dbmin -3000
		comment.dbmax 3000
		iface MIXER
		name 'Digital Capture Volume'
		value.0 74
		value.1 74
	}
}
state.ThinkPadEC {
	control.1 {
		comment.access read
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Console Playback Switch'
		value true
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
rfcomm
binfmt_misc
sco
bnep
l2cap
parport_pc
ppdev
joydev
iptable_nat
nf_nat
nf_conntrack_ipv4
arc4
nf_conntrack
nf_defrag_ipv4
iptable_mangle
iptable_filter
ip_tables
x_tables
snd_hda_codec_intelhdmi
snd_hda_codec_conexant
i915
snd_hda_intel
snd_hda_codec
iwlagn
snd_hwdep
snd_pcm
drm_kms_helper
snd_seq_midi
drm
snd_rawmidi
iwlcore
snd_seq_midi_event
thinkpad_acpi
mac80211
snd_seq
btusb
uvcvideo
snd_timer
snd_seq_device
cfg80211
bluetooth
videodev
intel_agp
snd
v4l1_compat
psmouse
snd_page_alloc
soundcore
led_class
serio_raw
i2c_algo_bit
agpgart
nvram
video
output
lp
parport
usb_storage
ahci
libahci
r8169
mii


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x19 0x042110f0
0x1a 0x95a701f0
0x1b 0x04a110f0
0x1c 0x400001f0
0x1d 0x400001f0
0x1e 0x400001f0
0x1f 0x921701f0
0x20 0x400001f0
0x22 0x400001f0
0x23 0x400001f0

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:

/sys/class/sound/hwC0D1/init_pin_configs:
0x03 0x18560010

/sys/class/sound/hwC0D1/driver_pin_configs:

/sys/class/sound/hwC0D1/user_pin_configs:

/sys/class/sound/hwC0D1/init_verbs:


!!ALSA/HDA dmesg
!!------------------

[   15.054208]   alloc kstat_irqs on node -1
[   15.054218] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   15.054293]   alloc irq_desc for 47 on node -1
[   15.054296]   alloc kstat_irqs on node -1
[   15.054310] HDA Intel 0000:00:1b.0: irq 47 for MSI/MSI-X
[   15.054355] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   15.138774] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16

---

### Post by amsterdamharu on 2010-10-30
On every machine I installed I had to do the following:

Check the output of the following command and post it here:
```
cat /proc/asound/card0/codec#* | grep Codec
```Open a file named:
/usr/share/doc/alsa-base/driver/HD-Audio-Models.txt.gz
or 
/usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz

In this file (open with file roller) there is a text file and that text file contains all the models. For me the output of the command is:
Realtek ALC662 rev1
And looking for ALC662 I can find:
```
ALC662/663
==========
  3stack-dig    3-stack (2-channel) with SPDIF
  3stack-6ch     3-stack (6-channel)
  3stack-6ch-dig 3-stack (6-channel) with SPDIF
  6stack-dig     6-stack with SPDIF
  lenovo-101e     Lenovo laptop
  eeepc-p701    ASUS Eeepc P701
  eeepc-ep20    ASUS Eeepc EP20
  ecs        ECS/Foxconn mobo
  m51va        ASUS M51VA
  g71v        ASUS G71V
  h13        ASUS H13
  g50v        ASUS G50V
  asus-mode1    ASUS
  asus-mode2    ASUS
  asus-mode3    ASUS
  asus-mode4    ASUS
  asus-mode5    ASUS
  asus-mode6    ASUS
  auto        auto-config reading BIOS (default)
```I find the one that is closest to what I have (or just try the top one if that doesn't work the next one but make sure to reboot a couple of times so change it once a day).
Then open a text file using the following command:
```
sudo nano /etc/modprobe.d/alsa-base.conf
```Or if that file doesn't exist use:
```
sudo nano /etc/modprobe.d/alsa-base
```Add the following line at the end of the file:
```
options snd-hda-intel model=MODEL
```Where MODEL is (for example) 3stack-dig (as the first in the list in the example above).
Now reboot and see if it works. Make sure nothing is muted in sound preferences (the icon of a loudspeaker in your panel).

Hope this helps

---

### Post by mercmobily on 2010-10-30
Big THANK YOU for your help!

This is what I am getting:


merc@merc-laptop:/mnt/disk/home/merc$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Conexant CX20582 (Pebble)
Codec: Intel Cantiga HDMI
merc@merc-laptop:/mnt/disk/home/merc$ 


Of Conexant, I have the following in the HD-Audio-Models.txt.gz file:


Conexant 5045
=============
  laptop-hpsense    Laptop with HP sense (old model laptop)
  laptop-micsense   Laptop with Mic sense (old model fujitsu)
  laptop-hpmicsense Laptop with HP and Mic senses
  benq		Benq R55E
  laptop-hp530	HP 530 laptop

Conexant 5047
=============
  laptop	Basic Laptop config 
  laptop-hp	Laptop config for some HP models (subdevice 30A5)
  laptop-eapd	Laptop config with EAPD support

Conexant 5051
=============
  laptop	Basic Laptop config (default)
  hp		HP Spartan laptop
  hp-dv6736	HP dv6736
  hp-f700	HP Compaq Presario F700
  lenovo-x200	Lenovo X200 laptop
  toshiba	Toshiba Satellite M300

Conexant 5066
=============
  laptop	Basic Laptop config (default)
  dell-laptop	Dell laptops
  olpc-xo-1_5	OLPC XO 1.5
  ideapad       Lenovo IdeaPad U150


It's not looking very promising... which one would you pick? :(

Merc.

---

### Post by mercmobily on 2010-10-30
Hi,

(plus, is there a way for me to unload/reload all of the ALSA driver modules without rebooting...?) It looks like I have a lot of tests to run and...)

Merc.

---

### Post by mercmobily on 2010-10-30
Hey...
IT WORKED! IT WORKED!

 ** thank you **

I just gave it a shot and I added:

# ADDED BY MERC
options snd-hda-intel model=laptop

Thank you SO MUCH for this...

Now, how do I make sure that this gets fixed? Will a bug report to Launchpad find its way upstream? Or...?
And, is this a more generalised bug of recognising the right option to give? (I have no idea how the whole auto-detection is happening here...)

I just can't live with the thought of many people out there stuck in Thailand (or wherever, really) with no way to communicate.

Bye,

Merc.

---

### Post by amsterdamharu on 2010-10-30
I am using 9.10 (actually I use mint but the version I use is based on 9.10).

Opening the following file /usr/share/doc/alsa-base/driver/HD-Audio-Models.txt.gz gives me:

```
Conexant 5045
=============
  laptop-hpsense    Laptop with HP sense (old model laptop)
  laptop-micsense   Laptop with Mic sense (old model fujitsu)
  laptop-hpmicsense Laptop with HP and Mic senses
  benq        Benq R55E
  test        for testing/debugging purpose, almost all controls
        can be adjusted.  Appearing only when compiled with
        $CONFIG_SND_DEBUG=y

Conexant 5047
=============
  laptop    Basic Laptop config 
  laptop-hp    Laptop config for some HP models (subdevice 30A5)
  laptop-eapd    Laptop config with EAPD support
  test        for testing/debugging purpose, almost all controls
        can be adjusted.  Appearing only when compiled with
        $CONFIG_SND_DEBUG=y

Conexant 5051
=============
  laptop    Basic Laptop config (default)
  hp        HP Spartan laptop
  hp-dv6736    HP dv6736
  lenovo-x200    Lenovo X200 laptop
```

The thinkpad is an IBM (now called lenovo) is it? You could try:
```
options snd-hda-intel model=laptop
```
or
```
options snd-hda-intel model=lenovo-x200
```

I don't know why but for some reason rebooting did not solve it. One time I just left it and after rebooting several times it suddenly worked so my advice is just leave it there and reboot a couple of times (make sure the mic is not muted). If it still does not work then try another model.

---

### Post by amsterdamharu on 2010-10-30
Oh, sorry. I did not see your last posts.

Good thing it's working now, enjoy Thailand it's a great place.

As for the bug report; I am not sure, I always thought everyone had to do that as I had to do this on 5 different installs. This is an irritating thing in ubuntu distro's (or maybe linux in general) but it gives you some satisfaction when it's working. I am sure if someone can fix this altogether it would have been fixed.

You can try a bug report. If you need info on the 2 computers I own I can give it to you to add to the report.

---

### Post by angliski on 2010-10-30
This is the output I got when I ran the command in terminal. Sorry, but I'm not very experienced at doing things on Linux. I haven't been able to find alsa and in skype, (where I first noticed that I had no working mic, I am told in options that it is using pulse audio on local server.

You said to open some files using file roller. What is this as I don't seem to have it. I can hear sounds Ok, but nothing happens when I talk. My machine is an Acer Aspire 5520 with a Realtek ALC268 
I hpe someone can help as otherwise a beautiful love affair with my girlfriend is going to screw up.

Chhers

Steve
steve@steve:~$ cat /proc/asound/card0/codec#*
Codec: Realtek ALC268
Address: 0
Function Id: 0x1
Vendor Id: 0x10ec0268
Subsystem Id: 0x10250126
Revision Id: 0x100003
No Modem Function Group found
Default PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=4, o=0, i=0, unsolicited=1, wake=0
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[2]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[3]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Node 0x02 [Audio Output] wcaps 0x1d: Stereo Amp-Out
  Device: name="ALC268 Analog", type="Audio", device=0
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x40 0x40]
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x03 [Audio Output] wcaps 0x1d: Stereo Amp-Out
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x40 0x40]
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x04 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x05 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x06 [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0x1e]: 16 20 24 32
    formats [0x1]: PCM
Node 0x07 [Audio Input] wcaps 0x100111: Stereo
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0x6]: 16 20
    formats [0x1]: PCM
  Connection: 1
     0x24
Node 0x08 [Audio Input] wcaps 0x100111: Stereo
  Device: name="ALC268 Analog", type="Audio", device=0
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0x6]: 16 20
    formats [0x1]: PCM
  Connection: 1
     0x23
Node 0x09 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0a [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0b [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0c [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0d [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0e [Audio Mixer] wcaps 0x20010a: Mono Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00]
  Connection: 1
     0x02
Node 0x0f [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80]
  Connection: 2
     0x02 0x1d
Node 0x10 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80]
  Connection: 3
     0x03 0x1d 0x02
Node 0x11 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x12 [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
Node 0x13 [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
Node 0x14 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Control: name="Master Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0001003c: IN OUT HP EAPD Detect
  EAPD 0x2: EAPD
  Pin Default 0x0221101f: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Black
    DefAssociation = 0x1, Sequence = 0xf
  Pin-ctls: 0xc0: OUT HP
  Unsolicited: tag=04, enabled=1
  Connection: 1
     0x0f
Node 0x15 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0001003c: IN OUT HP EAPD Detect
  EAPD 0x2: EAPD
  Pin Default 0x99130110: [Fixed] Speaker at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x10
Node 0x16 [Pin Complex] wcaps 0x40010c: Mono Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80]
  Pincap 0x00000010: OUT
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x0e
Node 0x17 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x18 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Control: name="Mic Boost", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x02, stepsize=0x4f, mute=0
  Amp-In vals:  [0x02 0x02]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00003734: IN OUT Detect
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x02a19840: [Jack] Mic at Ext Front
    Conn = 1/8, Color = Pink
    DefAssociation = 0x4, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x02
Node 0x19 [Pin Complex] wcaps 0x40008b: Stereo Amp-In
  Control: name="Internal Mic Boost", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x02, stepsize=0x4f, mute=0
  Amp-In vals:  [0x02 0x02]
  Pincap 0x00003724: IN Detect
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x99a30941: [Fixed] Mic at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0x4, Sequence = 0x1
    Misc = NO_PRESENCE
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
Node 0x1a [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Control: name="Line In Boost", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x02, stepsize=0x4f, mute=0
  Amp-In vals:  [0x02 0x02]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00003734: IN OUT Detect
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x0281304e: [Jack] Line In at Ext Front
    Conn = 1/8, Color = Blue
    DefAssociation = 0x4, Sequence = 0xe
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x02
Node 0x1b [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x1c [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
Node 0x1d [Pin Complex] wcaps 0x400000: Mono
  Control: name="Beep Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Pincap 0x00000020: IN
  Pin Default 0x4017952d: [N/A] Speaker at Ext N/A
    Conn = Analog, Color = Pink
    DefAssociation = 0x2, Sequence = 0xd
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
Node 0x1e [Pin Complex] wcaps 0x400380: Mono Digital
  Pincap 0x00000010: OUT
  Pin Default 0x02451130: [Jack] SPDIF Out at Ext Front
    Conn = Optical, Color = Black
    DefAssociation = 0x3, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x06
Node 0x1f [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x20 [Vendor Defined Widget] wcaps 0xf00040: Mono
  Processing caps: benign=0, ncoeff=10
Node 0x21 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x22 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x23 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Control: name="Capture Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Capture Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Input Source", index=0, device=0
  Amp-Out caps: ofs=0x0b, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x1e 0x1e]
  Connection: 7
     0x18* 0x19 0x1a 0x1c 0x14 0x15 0x12
Node 0x24 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x0b, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x00 0x00]
  Connection: 7
     0x18* 0x19 0x1a 0x1c 0x14 0x15 0x13
Codec: Conexant ID 2c06
Address: 1
Function Id: 0x2
Vendor Id: 0x14f12c06
Subsystem Id: 0x10250126
Revision Id: 0x100000
Modem Function Group: 0x2
steve@steve:~$

---

### Post by amsterdamharu on 2010-10-31
File roller is where a .gz file will open in if you double click on it. The choices for model you have are these:
```
ALC267/268
==========
  quanta-il1    Quanta IL1 mini-notebook
  3stack    3-stack model
  toshiba    Toshiba A205
  acer        Acer laptops
  acer-dmic    Acer laptops with digital-mic
  acer-aspire    Acer Aspire One
  dell        Dell OEM laptops (Vostro 1200)
  zepto        Zepto laptops
  test        for testing/debugging purpose, almost all controls can
        adjusted.  Appearing only when compiled with
        $CONFIG_SND_DEBUG=y
  auto        auto-config reading BIOS (default)
```

So you could try to add the line:
```
options snd-hda-intel model=acer-aspire
```
And if that doesn't work you can try a more generic type like
```
options snd-hda-intel model=3stack
```

---

### Post by lidex on 2010-10-31
> **amsterdamharu said:**
> File roller is where a .gz file will open in if you double click on it. The choices for model you have are these:
```
ALC267/268
==========
  quanta-il1    Quanta IL1 mini-notebook
  3stack    3-stack model
  toshiba    Toshiba A205
  acer        Acer laptops
  acer-dmic    Acer laptops with digital-mic
  acer-aspire    Acer Aspire One
  dell        Dell OEM laptops (Vostro 1200)
  zepto        Zepto laptops
  test        for testing/debugging purpose, almost all controls can
        adjusted.  Appearing only when compiled with
        $CONFIG_SND_DEBUG=y
  auto        auto-config reading BIOS (default)
```

So you could try to add the line:
```
options snd-hda-intel model=acer-aspire
```
And if that doesn't work you can try a more generic type like
```
options snd-hda-intel model=3stack
```

To make sure this gets fixed upstream return your install to default (remove any alsa-base.conf options) and do this. Try running this command in a terminal for 10.04 or later:
```
ubuntu-bug audio
```
Reference the Ubuntu-Bug Audio link in my sig.
Follow up and post a bug report. Also post relevant info of how you got it to work. Thanks for your help!

---

### Post by sjonnie85 on 2010-11-09
**WORKED FOR ME!**

## Thinkpad Edge 13 intel version. ##

What I did:
```
sudo nano /etc/modprobe.d/alsa-base.conf
```
Add the following line and save.
```
options snd-hda-intel model=laptop
```

Reboot, testcall worked in skype!

---

### Post by ahnise on 2010-11-29
I have a Thinkpad edge 11" And interestingly this fix is not working for me at all. In all my research I have a choice between using:

**options snd-hda-intel model="olpc-xo-1_5"**
   per: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/587388](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/587388)
   This will get the headphone jack working (with auto switching     off of external speakers when headphone inserted) The EXTERNAL microphone will also work. INTERNAL mic will NOT work.

**options snd-hda-intel model=laptop**
I have not tested everything but:
1) Headphone jack does not turn off external speakers
2) Internal Mic does NOT work (did not text external yet)

If did anyone actually see the internal mic ever working on the thinkpad edge ?

---

### Post by af3556 on 2010-12-02
"Out of the box" Ubuntu 10.10 on a Thinkpad Edge 13 0196CTO:
[LIST]
[*]the builtin/onboard microphone does not work
[*]an external smartphone headphone/mic plugged in to the combo jack does work (both mic and headphones)
[*]builtin speakers work fine
[*]audio output switches back and forth between speakers and external headphones when the mic/phones are plugged in/out
[/LIST]

I tried using 'options snd-hda-intel model=laptop' in /etc/modprobe.d/alsa-base.conf, which after rebooting enabled the internal microphone, however disabled the switching between the internal mic+speakers and the external jack (i.e. plugging in the external mic/phones had no effect, audio in & out was still from the builtin devices)

I've raised [bug 683487]("https://bugs.launchpad.net/bugs/683487").

---

