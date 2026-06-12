---
title: "Mic issue"
date: 2011-06-08
forum: Multimedia Software
---

### Post by gauche on 2011-06-08
My computer has two audio jacks. One of them is for headphones and the other is for a microphone. I have a microphone that I tested on other computers and it only works if it's plugged into a line-in jack. Is there a way to make my microphone work?

---

### Post by lincoln32 on 2011-06-08
well yes it should but a. what version do you have b. look in the sound Preferences under input and turn up mike and see if there is a front/rear mike option:)

---

### Post by gauche on 2011-06-08
I'm using 10.10. I unmuted the mic and turned it all the way up but it still doesn't work.

---

### Post by lincoln32 on 2011-06-08
what was the device listed under sound input?

---

### Post by lincoln32 on 2011-06-08
only other thing to check is under the hardware tab check the profile setting the mike may be turned off there or set to speaker only
I recommend a simple setting that has a analog stereo input
other that that you may need someone better than me to test hardware error
or drive issue:confused:

---

### Post by gauche on 2011-06-08
it says internal audio analog stereo

---

### Post by gauche on 2011-06-08
can anybody help?

---

### Post by gauche on 2011-06-08
alsa-info

!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Wed Jun  8 16:49:11 UTC 2011


!!Linux Distribution
!!------------------

Ubuntu 10.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.10"


!!DMI Information
!!---------------

Manufacturer:      Dell Inc.
Product Name:      Vostro 1015                     
Product Version:   


!!Kernel Information
!!------------------

Kernel release:    2.6.35-28-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.24
Library version:    1.0.23
Utilities version:  1.0.23


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
                      HDA Intel at 0xf6afc000 irq 48


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

	Subsystem: 1028:0402
	Control: I/O- Mem  BusMaster  SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
--
	Subsystem: 1028:0402
	Control: I/O  Mem  BusMaster  SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx 
--
	Subsystem: 1028:0402
	Control: I/O  Mem  BusMaster  SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
--
	Subsystem: 1028:0402
	Control: I/O  Mem- BusMaster  SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
--
	Subsystem: 1028:0402
	Control: I/O  Mem- BusMaster  SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
--
	Subsystem: 1028:0402
	Control: I/O  Mem- BusMaster  SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
--
	Subsystem: 1028:0402
	Control: I/O- Mem  BusMaster  SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR  FastB2B- DisINTx-
--
00:1b.0 0403: 8086:293e (rev 03)
	Subsystem: 1028:0402
	Control: I/O- Mem  BusMaster  SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR  FastB2B- DisINTx 
--
	Subsystem: 1028:0402
	Control: I/O  Mem- BusMaster  SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
--
	Subsystem: 1028:0402
	Control: I/O  Mem- BusMaster  SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
--
	Subsystem: 1028:0402
	Control: I/O  Mem- BusMaster  SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
--
	Subsystem: 1028:0402
	Control: I/O- Mem  BusMaster  SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR  FastB2B- DisINTx-
--
	Subsystem: 1028:0402
	Control: I/O  Mem  BusMaster  SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR  FastB2B- DisINTx-
--
	Subsystem: 1028:0402
	Control: I/O  Mem  BusMaster  SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx 
--
	Subsystem: 1028:0402
	Control: I/O  Mem  BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR  FastB2B- DisINTx-
--
	Subsystem: 1028:0402
	Control: I/O  Mem  BusMaster  SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR  FastB2B- DisINTx 
--
	Subsystem: 1028:0402
	Control: I/O- Mem  BusMaster  SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR  FastB2B- DisINTx-
--
	Subsystem: 1028:0402
	Control: I/O- Mem  BusMaster  SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR  FastB2B- DisINTx-
--
	Subsystem: 1028:0402
	Control: I/O- Mem  BusMaster  SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR  FastB2B- DisINTx-


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
	beep_mode : 1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	enable_msi : -1
	id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	model : auto,(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	patch : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	position_fix : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	power_save : 0
	power_save_controller : Y
	probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	single_cmd : N


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: Conexant CX20585
Address: 0
AFG Function Id: 0x1 (unsol 1)
MFG Function Id: 0x2 (unsol 1)
Vendor Id: 0x14f15069
Subsystem Id: 0x10280402
Revision Id: 0x100302
Modem Function Group: 0x2
Default PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=4, o=0, i=0, unsolicited=1, wake=0
  IO[0]: enable=1, dir=1, wake=0, sticky=0, data=1, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[2]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[3]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Node 0x10 [Audio Output] wcaps 0xc1d: Stereo Amp-Out R/L
  Control: name="Speaker Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Speaker Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Device: name="CONEXANT Analog", type="Audio", device=0
  Amp-Out caps: ofs=0x4a, nsteps=0x4a, stepsize=0x03, mute=1
  Amp-Out vals:  [0x4a 0x4a]
  Converter: stream=5, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
Node 0x11 [Audio Output] wcaps 0xc1d: Stereo Amp-Out R/L
  Control: name="Headphone Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Headphone Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x4a, nsteps=0x4a, stepsize=0x03, mute=1
  Amp-Out vals:  [0x4a 0x4a]
  Converter: stream=5, channel=0
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
  Control: name="Beep Playback Volume", index=0, device=0
    ControlAmp: chs=1, dir=Out, idx=0, ofs=0
  Control: name="Beep Playback Switch", index=0, device=0
    ControlAmp: chs=1, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x07, nsteps=0x07, stepsize=0x0f, mute=0
  Amp-Out vals:  [0x00]
Node 0x14 [Audio Input] wcaps 0x100d1b: Stereo Amp-In R/L
  Control: name="Mic Capture Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Mic Capture Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Internal Mic Capture Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Control: name="Internal Mic Capture Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Device: name="CONEXANT Analog", type="Audio", device=0
  Amp-In caps: ofs=0x4a, nsteps=0x50, stepsize=0x03, mute=1
  Amp-In vals:  [0x50 0x50] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Converter: stream=1, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 4
     0x17* 0x18 0x23 0x24
Node 0x15 [Audio Input] wcaps 0x100d1b: Stereo Amp-In R/L
  Amp-In caps: ofs=0x4a, nsteps=0x50, stepsize=0x03, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
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
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
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
  Control: name="Mic Boost Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x00, nsteps=0x04, stepsize=0x27, mute=0
  Amp-Out vals:  [0x04 0x04]
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 4
     0x1a* 0x1b 0x1d 0x1e
Node 0x18 [Audio Selector] wcaps 0x30050d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x04, stepsize=0x27, mute=0
  Amp-Out vals:  [0x00 0x00]
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 4
     0x1a* 0x1b 0x1d 0x1e
Node 0x19 [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x0000001c: OUT HP Detect
  Pin Default 0x042140f0: [Jack] HP Out at Ext Right
    Conn = 1/8, Color = Green
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0xc0: OUT HP
  Unsolicited: tag=37, enabled=1
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 2
     0x10 0x11*
Node 0x1a [Pin Complex] wcaps 0x400481: Stereo
  Pincap 0x00001324: IN Detect
    Vref caps: HIZ 50 80
  Pin Default 0x04a190f0: [Jack] Mic at Ext Right
    Conn = 1/8, Color = Pink
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=38, enabled=1
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
Node 0x1b [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x00011334: IN OUT EAPD Detect
    Vref caps: HIZ 50 80
  EAPD 0x2: EAPD
  Pin Default 0x400001f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00: VREF_HIZ
  Unsolicited: tag=00, enabled=0
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
  Pin-ctls: 0x00:
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
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
Node 0x1f [Pin Complex] wcaps 0x400501: Stereo
  Pincap 0x00000010: OUT
  Pin Default 0x921701f0: [Fixed] Speaker at Int Front
    Conn = Analog, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 2
     0x10* 0x11
Node 0x20 [Pin Complex] wcaps 0x400781: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x400001f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
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
  Pincap 0x00000010: OUT
  Pin Default 0x400001f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 1
     0x21
Node 0x23 [Pin Complex] wcaps 0x40040b: Stereo Amp-In
  Control: name="Internal Mic Boost Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x04, stepsize=0x2f, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00000020: IN
  Pin Default 0x95a601f0: [Fixed] Mic at Int Top
    Conn = Digital, Color = Unknown
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
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----  1 root audio 116,  5 Jun  8 12:34 /dev/snd/controlC0
crw-rw----  1 root audio 116,  4 Jun  8 12:34 /dev/snd/hwC0D0
crw-rw----  1 root audio 116,  3 Jun  8 12:35 /dev/snd/pcmC0D0c
crw-rw----  1 root audio 116,  2 Jun  8 12:35 /dev/snd/pcmC0D0p
crw-rw----  1 root audio 116,  1 Jun  8 12:34 /dev/snd/seq
crw-rw----  1 root audio 116, 33 Jun  8 12:34 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Jun  8 12:34 .
drwxr-xr-x 3 root root 180 Jun  8 12:34 ..
lrwxrwxrwx 1 root root  12 Jun  8 12:34 pci-0000:00:1b.0 -> ../controlC0


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [Intel]

Card hw:0 'Intel'/'HDA Intel at 0xf6afc000 irq 48'
  Mixer name	: 'Conexant CX20585'
  Components	: 'HDA:14f15069,10280402,00100302'
  Controls      : 16
  Simple ctrls  : 10
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 74
  Mono: Playback 74 [100%] [0.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 74
  Mono:
  Front Left: Playback 74 [100%] [0.00dB] [on]
  Front Right: Playback 74 [100%] [0.00dB] [on]
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 74
  Mono:
  Front Left: Playback 74 [100%] [0.00dB] [on]
  Front Right: Playback 74 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Mic',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 80
  Front Left: Capture 80 [100%] [6.00dB] [on]
  Front Right: Capture 80 [100%] [6.00dB] [on]
Simple mixer control 'Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 4
  Front Left: 4 [100%] [40.00dB]
  Front Right: 4 [100%] [40.00dB]
Simple mixer control 'Beep',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 7
  Mono: Playback 7 [100%] [0.00dB] [on]
Simple mixer control 'Auto-Mute Mode',0
  Capabilities: enum
  Items: 'Disabled' 'Enabled'
  Item0: 'Enabled'
Simple mixer control 'Internal Mic',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 80
  Front Left: Capture 0 [0%] [-74.00dB] [off]
  Front Right: Capture 0 [0%] [-74.00dB] [off]
Simple mixer control 'Internal Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 4
  Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB]


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
		name 'Speaker Playback Volume'
		value.0 74
		value.1 74
	}
	control.2 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Speaker Playback Switch'
		value.0 true
		value.1 true
	}
	control.3 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 74'
		comment.dbmin -7400
		comment.dbmax 0
		iface MIXER
		name 'Headphone Playback Volume'
		value.0 74
		value.1 74
	}
	control.4 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Headphone Playback Switch'
		value.0 true
		value.1 true
	}
	control.5 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Disabled
		comment.item.1 Enabled
		iface MIXER
		name 'Auto-Mute Mode'
		value Enabled
	}
	control.6 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 4'
		comment.dbmin 0
		comment.dbmax 4000
		iface MIXER
		name 'Mic Boost Volume'
		value.0 4
		value.1 4
	}
	control.7 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 80'
		comment.dbmin -7400
		comment.dbmax 600
		iface MIXER
		name 'Mic Capture Volume'
		value.0 80
		value.1 80
	}
	control.8 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Mic Capture Switch'
		value.0 true
		value.1 true
	}
	control.9 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 4'
		comment.dbmin 0
		comment.dbmax 4800
		iface MIXER
		name 'Internal Mic Boost Volume'
		value.0 0
		value.1 0
	}
	control.10 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 80'
		comment.dbmin -7400
		comment.dbmax 600
		iface MIXER
		name 'Internal Mic Capture Volume'
		value.0 0
		value.1 0
	}
	control.11 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Internal Mic Capture Switch'
		value.0 false
		value.1 false
	}
	control.12 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 74'
		comment.dbmin -7400
		comment.dbmax 0
		iface MIXER
		name 'Master Playback Volume'
		value 74
	}
	control.13 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Master Playback Switch'
		value true
	}
	control.14 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 7'
		comment.dbmin -2800
		comment.dbmax 0
		iface MIXER
		name 'Beep Playback Volume'
		value 7
	}
	control.15 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Beep Playback Switch'
		value true
	}
	control.16 {
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
binfmt_misc
sco
bnep
l2cap
parport_pc
ppdev
snd_hda_codec_conexant
snd_hda_intel
snd_hda_codec
snd_hwdep
snd_pcm
arc4
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
i915
ath9k
snd_seq
snd_timer
ath9k_common
ath9k_hw
snd_seq_device
drm_kms_helper
uvcvideo
ath
mac80211
videodev
v4l1_compat
v4l2_compat_ioctl32
dell_wmi
cfg80211
dell_laptop
dcdbas
btusb
snd
bluetooth
drm
psmouse
soundcore
serio_raw
intel_agp
snd_page_alloc
i2c_algo_bit
video
output
lp
parport
ahci
sdhci_pci
sdhci
libahci
led_class
firewire_ohci
firewire_core
crc_itu_t
r8169
mii


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x19 0x042140f0
0x1a 0x04a190f0
0x1b 0x400001f0
0x1c 0x400001f0
0x1d 0x400001f0
0x1e 0x400001f0
0x1f 0x921701f0
0x20 0x400001f0
0x22 0x400001f0
0x23 0x95a601f0

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:


!!ALSA/HDA dmesg
!!------------------

[   20.799451] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   20.799501] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   20.799560]   alloc irq_desc for 48 on node -1
[   20.799562]   alloc kstat_irqs on node -1
[   20.799577] HDA Intel 0000:00:1b.0: irq 48 for MSI/MSI-X
[   20.799609] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   20.799614] ALSA hda_intel.c:2617: chipset global capabilities = 0x4401
[   20.799637] ALSA hda_intel.c:1090: Clearing TCSEL
[   20.860045] Skipping EDID probe due to cached edid
[   20.872565] ALSA hda_intel.c:944: codec_mask = 0x1
[   20.872678] ALSA hda_intel.c:1391: codec #0 probed OK
[   20.899444] ALSA hda_codec.c:3828: hda_codec: model 'auto' is selected
[   20.899448] hda_codec: CX20585: BIOS auto-probing.
[   20.899455] ALSA hda_codec.c:4768: autoconfig: line_outs=1 (0x1f/0x0/0x0/0x0/0x0) type:speaker
[   20.899460] ALSA hda_codec.c:4772:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   20.899463] ALSA hda_codec.c:4776:    hp_outs=1 (0x19/0x0/0x0/0x0/0x0)
[   20.899466] ALSA hda_codec.c:4777:    mono: mono_out=0x0
[   20.899468] ALSA hda_codec.c:4781:    inputs:
[   20.899471] ALSA hda_codec.c:4785:  Mic=0x1a
[   20.899474] ALSA hda_codec.c:4785:  Internal Mic=0x23
[   20.899477] ALSA hda_codec.c:4787: 
[   20.899961] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input7
[   20.900984] ALSA hda_codec.c:2236: Cannot find slave Front Playback Volume, skipped
[   20.900987] ALSA hda_codec.c:2236: Cannot find slave Surround Playback Volume, skipped
[   20.900990] ALSA hda_codec.c:2236: Cannot find slave CLFE Playback Volume, skipped
[   20.900996] ALSA hda_codec.c:2236: Cannot find slave Front Playback Switch, skipped
[   20.900999] ALSA hda_codec.c:2236: Cannot find slave Surround Playback Switch, skipped
[   20.901002] ALSA hda_codec.c:2236: Cannot find slave CLFE Playback Switch, skipped
[   21.228814] input: PS/2 Generic Mouse as /devices/platform/i8042/serio1/input/input8
--
[   22.410876] Skipping EDID probe due to cached edid
[   22.611186] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.611191] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.611334] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.611337] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.611566] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.611570] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.611838] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.611841] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.611983] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.611986] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.612119] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.612122] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.612309] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.612312] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.612636] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.612639] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.612789] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.612792] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.612928] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.612932] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.613121] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.613125] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.613393] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.613396] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.613570] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.613573] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.613711] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.613714] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.613902] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.613905] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.614169] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.614172] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.614312] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.614315] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.614449] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.614452] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.614639] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.614642] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.614909] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.614912] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.617934] ALSA hda_intel.c:1731: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   22.617947] ALSA hda_codec.c:1297: hda_codec_setup_stream: NID=0x10, stream=0x5, channel=0, format=0x4011
[   22.618066] ALSA hda_codec.c:1297: hda_codec_setup_stream: NID=0x11, stream=0x5, channel=0, format=0x4011
[   22.642969] ALSA hda_intel.c:1731: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   22.642982] ALSA hda_codec.c:1297: hda_codec_setup_stream: NID=0x10, stream=0x5, channel=0, format=0x4011
[   22.642986] ALSA hda_codec.c:1297: hda_codec_setup_stream: NID=0x11, stream=0x5, channel=0, format=0x4011
[   22.644568] ALSA hda_intel.c:1731: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   22.644582] ALSA hda_codec.c:1297: hda_codec_setup_stream: NID=0x14, stream=0x1, channel=0, format=0x4011
[   22.644746] ALSA hda_intel.c:1731: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   22.644754] ALSA hda_codec.c:1297: hda_codec_setup_stream: NID=0x14, stream=0x1, channel=0, format=0x4011
[   22.645458] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.645463] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.645481] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.645484] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.645845] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.645849] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.646161] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.646164] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.646601] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.646605] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.647120] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.647124] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.647457] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.647460] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.647794] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.647798] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.648225] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.648229] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.648805] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.648810] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.649196] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.649199] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.649534] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.649537] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.649962] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.649966] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.650458] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.650461] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.650796] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.650800] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.651118] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.651121] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.651541] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.651545] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.652070] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.652074] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.652396] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.652399] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.652781] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.652784] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.653164] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.653168] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.653635] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.653639] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.653940] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.653943] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.654201] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.654204] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.654478] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.654481] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.654775] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.654778] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.655050] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.655053] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.655351] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.655355] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.655663] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.655667] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.655997] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.656000] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.656309] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.656313] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.656644] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.656647] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.656971] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.656974] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.657292] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.657295] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.657600] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.657604] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.657902] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.657906] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.658220] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.658223] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.658537] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.658566] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.658879] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.658883] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.659175] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.659179] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.659492] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.659496] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.659804] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.659807] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.660115] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.660119] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.660416] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.660420] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.660760] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.660765] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.661052] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.661056] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.661346] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.661350] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.661629] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.661633] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.661941] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.661945] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.662269] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.662272] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.664044] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.664048] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.664374] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.664377] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.664678] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.664681] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.664964] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.664968] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.665244] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.665247] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.665510] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.665513] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.665789] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.665793] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.666086] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.666090] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.666388] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.666392] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.666729] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.666733] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.667055] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.667059] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.667375] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.667379] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.667757] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.667762] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.668097] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.668100] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.668514] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.668518] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.669026] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.669029] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.669334] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.669337] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.669632] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.669636] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.670019] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.670022] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.670489] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.670492] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.670811] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.670815] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.671109] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.671112] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.671519] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.671523] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.672067] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.672071] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.672457] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.672461] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.673333] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.673338] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.673800] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.673804] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.674331] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.674335] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.674782] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.674786] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.675137] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.675140] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.675578] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.675581] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.676103] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.676107] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.676445] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.676448] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.676769] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.676773] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.677155] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.677158] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.677625] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.677628] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.677934] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.677937] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.678702] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.678706] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.679103] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.679107] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.679578] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.679582] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.679880] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.679884] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.680186] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.680190] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.680573] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.680577] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.681056] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.681059] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.681362] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.681366] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.681685] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.681688] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.682072] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.682076] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.682682] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.682686] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.682999] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.683002] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.683302] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.683306] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.683746] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.683751] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.684257] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   22.684261] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   22.689658] ALSA hda_intel.c:1731: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   22.689669] ALSA hda_codec.c:1297: hda_codec_setup_stream: NID=0x14, stream=0x1, channel=0, format=0x4011
[   22.689684] ALSA hda_intel.c:1731: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   22.689691] ALSA hda_codec.c:1297: hda_codec_setup_stream: NID=0x14, stream=0x1, channel=0, format=0x4011
[   22.691471] ALSA hda_intel.c:1731: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[   22.691483] ALSA hda_codec.c:1297: hda_codec_setup_stream: NID=0x10, stream=0x5, channel=0, format=0x4011
[   22.691486] ALSA hda_codec.c:1297: hda_codec_setup_stream: NID=0x11, stream=0x5, channel=0, format=0x4011
[   22.691501] ALSA hda_intel.c:1731: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[   22.691509] ALSA hda_codec.c:1297: hda_codec_setup_stream: NID=0x10, stream=0x5, channel=0, format=0x4011
[   22.691513] ALSA hda_codec.c:1297: hda_codec_setup_stream: NID=0x11, stream=0x5, channel=0, format=0x4011
[   22.697746] hda-intel: Invalid position buffer, using LPIB read method instead.
[   22.698400] ALSA hda_intel.c:1731: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[   22.698410] ALSA hda_codec.c:1297: hda_codec_setup_stream: NID=0x14, stream=0x1, channel=0, format=0x4011
[   22.698426] ALSA hda_intel.c:1731: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[   22.698433] ALSA hda_codec.c:1297: hda_codec_setup_stream: NID=0x14, stream=0x1, channel=0, format=0x4011
[   22.707367] hda-intel: Invalid position buffer, using LPIB read method instead.
[   22.856247] EXT4-fs (loop0): re-mounted. Opts: errors=remount-ro,commit=0
[   22.882445] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[   28.852901] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   28.852905] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   28.852927] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   28.852930] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.392617] Skipping EDID probe due to cached edid
--
[   30.510078] Skipping EDID probe due to cached edid
[   30.618762] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.618767] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.619004] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.619007] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.619302] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.619305] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.619644] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.619648] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.619861] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.619865] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.620065] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.620068] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.620323] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.620327] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.620678] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.620682] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.620885] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.620889] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.621083] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.621086] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.621331] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.621334] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.621665] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.621669] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.621885] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.621888] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.622090] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.622094] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.622349] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.622353] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.622784] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.622787] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.623002] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.623005] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.623199] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.623203] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.623447] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.623451] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.623781] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.623785] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.626958] ALSA hda_intel.c:1731: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   30.626971] ALSA hda_codec.c:1297: hda_codec_setup_stream: NID=0x10, stream=0x5, channel=0, format=0x4011
[   30.626975] ALSA hda_codec.c:1297: hda_codec_setup_stream: NID=0x11, stream=0x5, channel=0, format=0x4011
[   30.626990] ALSA hda_intel.c:1731: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   30.626998] ALSA hda_codec.c:1297: hda_codec_setup_stream: NID=0x10, stream=0x5, channel=0, format=0x4011
[   30.627001] ALSA hda_codec.c:1297: hda_codec_setup_stream: NID=0x11, stream=0x5, channel=0, format=0x4011
[   30.628515] ALSA hda_intel.c:1731: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   30.628525] ALSA hda_codec.c:1297: hda_codec_setup_stream: NID=0x14, stream=0x1, channel=0, format=0x4011
[   30.628559] ALSA hda_intel.c:1731: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   30.628566] ALSA hda_codec.c:1297: hda_codec_setup_stream: NID=0x14, stream=0x1, channel=0, format=0x4011
[   30.629348] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.629351] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.629400] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.629403] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.629830] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.629834] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.630251] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.630255] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.630767] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.630771] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.631362] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.631366] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.631791] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.631794] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.632204] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.632208] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.632827] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.632831] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.633421] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.633424] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.633838] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.633841] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.634276] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.634279] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.634831] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.634835] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.635451] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.635455] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.635892] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.635896] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.636302] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.636306] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.636832] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.636836] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.637450] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.637454] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.637901] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.637905] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.638355] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.638359] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.638921] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.638925] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.639590] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.639594] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.640059] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.640063] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.642638] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.642644] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.643243] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.643246] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.643642] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.643645] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.644048] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.644051] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.644449] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.644453] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.644889] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.644893] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.645316] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.645320] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.645736] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.645740] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.646132] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.646136] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.646529] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.646532] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.646953] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.646957] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.647351] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.647355] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.647746] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.647749] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.648182] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.648186] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.648626] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.648630] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.649014] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.649018] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.649397] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.649400] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.649793] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.649797] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.650193] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.650197] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.650593] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.650596] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.650991] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.650995] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.651418] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.651421] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.651818] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.651821] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.652208] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.652211] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.652693] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.652697] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.653102] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.653105] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.653487] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.653491] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.653870] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.653874] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.654243] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.654246] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.654653] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.654656] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.655054] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.655057] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.655439] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.655443] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.655843] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.655847] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.656244] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.656248] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.656685] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.656688] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.657091] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.657095] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.657479] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.657483] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.657894] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.657898] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.658284] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.658288] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.658718] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.658722] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.659123] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.659126] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.659643] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.659647] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.670999] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.671004] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.671510] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.671514] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.671973] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.671977] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.672637] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.672641] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.673268] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.673271] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.673711] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.673715] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.674133] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.674137] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.674656] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.674660] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.675244] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.675247] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.675666] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.675670] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.676091] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.676095] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.676617] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.676620] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.677216] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.677219] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.677650] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.677654] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.678068] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.678072] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.678590] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.678594] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.679212] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.679215] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.679659] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.679663] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.680095] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.680099] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.680655] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.680660] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.681294] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.681298] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.681757] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.681761] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.682198] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.682202] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.682772] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.682775] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.683370] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.683373] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.683800] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.683803] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.684239] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.684242] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.684807] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.684811] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.685448] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.685452] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.685911] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.685915] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.686335] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.686339] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.686874] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.686878] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.687463] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.687466] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.687910] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.687914] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.688348] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.688351] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.688908] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.688911] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.689510] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   30.689513] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   30.696506] ALSA hda_intel.c:1731: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   30.696517] ALSA hda_codec.c:1297: hda_codec_setup_stream: NID=0x14, stream=0x1, channel=0, format=0x4011
[   30.696551] ALSA hda_intel.c:1731: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   30.696559] ALSA hda_codec.c:1297: hda_codec_setup_stream: NID=0x14, stream=0x1, channel=0, format=0x4011
[   30.698801] ALSA hda_intel.c:1731: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[   30.698812] ALSA hda_codec.c:1297: hda_codec_setup_stream: NID=0x10, stream=0x5, channel=0, format=0x4011
[   30.698817] ALSA hda_codec.c:1297: hda_codec_setup_stream: NID=0x11, stream=0x5, channel=0, format=0x4011
[   30.698832] ALSA hda_intel.c:1731: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[   30.698840] ALSA hda_codec.c:1297: hda_codec_setup_stream: NID=0x10, stream=0x5, channel=0, format=0x4011
[   30.698843] ALSA hda_codec.c:1297: hda_codec_setup_stream: NID=0x11, stream=0x5, channel=0, format=0x4011
[   30.713786] ALSA hda_intel.c:1731: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[   30.713797] ALSA hda_codec.c:1297: hda_codec_setup_stream: NID=0x14, stream=0x1, channel=0, format=0x4011
[   30.713813] ALSA hda_intel.c:1731: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[   30.713822] ALSA hda_codec.c:1297: hda_codec_setup_stream: NID=0x14, stream=0x1, channel=0, format=0x4011
[   31.710648] Skipping EDID probe due to cached edid
--
[   33.740069] Skipping EDID probe due to cached edid
[   35.834153] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   35.834158] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   35.834185] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   35.834188] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   36.170090] Skipping EDID probe due to cached edid
--
[   48.790253] CE: hpet increased min_delta_ns to 7500 nsec
[   62.925578] ALSA hda_intel.c:1731: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[   62.925590] ALSA hda_codec.c:1297: hda_codec_setup_stream: NID=0x14, stream=0x1, channel=0, format=0x4011
[   62.925606] ALSA hda_intel.c:1731: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[   62.925613] ALSA hda_codec.c:1297: hda_codec_setup_stream: NID=0x14, stream=0x1, channel=0, format=0x4011
[   74.595224] ALSA hda_intel.c:1731: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[   74.595236] ALSA hda_codec.c:1297: hda_codec_setup_stream: NID=0x10, stream=0x5, channel=0, format=0x4011
[   74.595241] ALSA hda_codec.c:1297: hda_codec_setup_stream: NID=0x11, stream=0x5, channel=0, format=0x4011
[   74.595256] ALSA hda_intel.c:1731: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[   74.595264] ALSA hda_codec.c:1297: hda_codec_setup_stream: NID=0x10, stream=0x5, channel=0, format=0x4011
[   74.595267] ALSA hda_codec.c:1297: hda_codec_setup_stream: NID=0x11, stream=0x5, channel=0, format=0x4011
[   89.546467] ALSA hda_intel.c:1731: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[   89.546480] ALSA hda_codec.c:1297: hda_codec_setup_stream: NID=0x14, stream=0x1, channel=0, format=0x4011
[   89.546495] ALSA hda_intel.c:1731: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[   89.546502] ALSA hda_codec.c:1297: hda_codec_setup_stream: NID=0x14, stream=0x1, channel=0, format=0x4011
[   89.697657] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   89.697665] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[   89.697693] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x10
[   89.697698] ALSA hda_codec.c:1360: hda_codec_cleanup_stream: NID=0x11
[  155.395050] lo: Disabled Privacy Extensions

---

### Post by gauche on 2011-06-08
Can someone give me a link to any site or anywhere where that I might get help please?

---

