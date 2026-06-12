---
title: "No sound in Maverick after installing Flash player"
date: 2010-10-17
forum: Multimedia Software
---

### Post by Paulgirardin on 2010-10-17
I fresh installed Maverick and had sound for buttons and Rythymbox.
After installing flash all sound is gone.I have checked most of the suggested possible causes but have not come up with the reason for this.

ALSA info:

[http://www.alsa-project.org/db/?f=7dd0f5173ab74c4b4abb33963c959632ed3a33e5](http://www.alsa-project.org/db/?f=7dd0f5173ab74c4b4abb33963c959632ed3a33e5)

```
!!################################
!!ALSA Information Script v 0.4.59
!!################################

!!Script ran on: Mon Oct 18 00:42:07 UTC 2010


!!Linux Distribution
!!------------------

Ubuntu 10.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.10"


!!DMI Information
!!---------------

Manufacturer:      System manufacturer
Product Name:      P5K SE


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

snd_ca0106
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

 0 [CA0106         ]: CA0106 - CA0106
                      Audigy SE [SB0570] at 0xec00 irq 17
 1 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfe8f8000 irq 44


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
05:01.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:293e (rev 02)
	Subsystem: 1043:829f
--
05:01.0 0401: 1102:0007
	Subsystem: 1102:100a


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

!!Module: snd_ca0106
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	subsystem : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0

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


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: Realtek ALC883
Address: 0
Function Id: 0x1
Vendor Id: 0x10ec0883
Subsystem Id: 0x1043829f
Revision Id: 0x100002
No Modem Function Group found
Default PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=2, o=0, i=0, unsolicited=1, wake=0
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Node 0x02 [Audio Output] wcaps 0x11: Stereo
  Device: name="ALC883 Analog", type="Audio", device=0
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x03 [Audio Output] wcaps 0x11: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x04 [Audio Output] wcaps 0x11: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x05 [Audio Output] wcaps 0x11: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x06 [Audio Output] wcaps 0x211: Stereo Digital
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Control: name="IEC958 Default PCM Playback Switch", index=0, device=0
  Device: name="ALC883 Digital", type="SPDIF", device=1
  Converter: stream=0, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0x1e]: 16 20 24 32
    formats [0x1]: PCM
Node 0x07 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x08 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Control: name="Capture Switch", index=0, device=0
  Control: name="Capture Volume", index=0, device=0
  Device: name="ALC883 Analog", type="Audio", device=0
  Amp-In caps: ofs=0x08, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x00 0x00]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0x6]: 16 20
    formats [0x1]: PCM
  Connection: 1
     0x23
Node 0x09 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Control: name="Capture Switch", index=1, device=0
  Control: name="Capture Volume", index=1, device=0
  Device: name="ALC883 Analog", type="Audio", device=2
  Amp-In caps: ofs=0x08, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x00 0x00]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0x6]: 16 20
    formats [0x1]: PCM
  Connection: 1
     0x22
Node 0x0a [Audio Input] wcaps 0x100391: Stereo Digital
  Converter: stream=0, channel=0
  SDI-Select: 0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0x1e]: 16 20 24 32
    formats [0x1]: PCM
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x1f
Node 0x0b [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Front Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=1, ofs=0
  Control: name="Front Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=1, ofs=0
  Control: name="Line Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Control: name="Line Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Control: name="Beep Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=5, ofs=0
  Control: name="Beep Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=5, ofs=0
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 10
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17
Node 0x0c [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Control: name="Front Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Front Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x1e 0x1e]
  Connection: 2
     0x02 0x0b
Node 0x0d [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Control: name="Surround Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Surround Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x1e 0x1e]
  Connection: 2
     0x03 0x0b
Node 0x0e [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Control: name="Center Playback Volume", index=0, device=0
    ControlAmp: chs=1, dir=Out, idx=0, ofs=0
  Control: name="LFE Playback Volume", index=0, device=0
    ControlAmp: chs=2, dir=Out, idx=0, ofs=0
  Control: name="Center Playback Switch", index=0, device=0
    ControlAmp: chs=1, dir=In, idx=2, ofs=0
  Control: name="LFE Playback Switch", index=0, device=0
    ControlAmp: chs=2, dir=In, idx=2, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x1e 0x1e]
  Connection: 2
     0x04 0x0b
Node 0x0f [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Control: name="Side Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Side Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x1e 0x1e]
  Connection: 2
     0x05 0x0b
Node 0x10 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x11 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x12 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x13 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x14 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000003e: IN OUT HP Detect Trigger
  Pin Default 0x01014010: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Green
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x15 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000003e: IN OUT HP Detect Trigger
  Pin Default 0x01011012: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0x1, Sequence = 0x2
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c 0x0d* 0x0e 0x0f 0x26
Node 0x16 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000003e: IN OUT HP Detect Trigger
  Pin Default 0x01016011: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Orange
    DefAssociation = 0x1, Sequence = 0x1
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c 0x0d 0x0e* 0x0f 0x26
Node 0x17 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000003e: IN OUT HP Detect Trigger
  Pin Default 0x01012014: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Grey
    DefAssociation = 0x1, Sequence = 0x4
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c 0x0d 0x0e 0x0f* 0x26
Node 0x18 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Control: name="Mic Boost", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000173e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x01a19840: [Jack] Mic at Ext Rear
    Conn = 1/8, Color = Pink
    DefAssociation = 0x4, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x19 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Control: name="Front Mic Boost", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000173e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x02a19c50: [Jack] Mic at Ext Front
    Conn = 1/8, Color = Pink
    DefAssociation = 0x5, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1a [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000173e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x0181304f: [Jack] Line In at Ext Rear
    Conn = 1/8, Color = Blue
    DefAssociation = 0x4, Sequence = 0xf
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1b [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Control: name="Headphone Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000173e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x02214c20: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Green
    DefAssociation = 0x2, Sequence = 0x0
  Pin-ctls: 0xc0: OUT HP VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1c [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x593301f0: [N/A] CD at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
Node 0x1d [Pin Complex] wcaps 0x400000: Mono
  Pincap 0x00000020: IN
  Pin Default 0x4015e601: [N/A] Speaker at Ext N/A
    Conn = Optical, Color = White
    DefAssociation = 0x0, Sequence = 0x1
  Pin-ctls: 0x00:
Node 0x1e [Pin Complex] wcaps 0x400300: Mono Digital
  Pincap 0x00000010: OUT
  Pin Default 0x01441130: [Jack] SPDIF Out at Ext Rear
    Conn = RCA, Color = Black
    DefAssociation = 0x3, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Connection: 1
     0x06
Node 0x1f [Pin Complex] wcaps 0x400200: Mono Digital
  Pincap 0x00000020: IN
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
Node 0x20 [Vendor Defined Widget] wcaps 0xf00040: Mono
  Processing caps: benign=0, ncoeff=17
Node 0x21 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x22 [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Control: name="Input Source", index=1, device=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Amp-Out caps: N/A
  Amp-Out vals:  [0x00 0x00]
  Connection: 11
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b
Node 0x23 [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Control: name="Input Source", index=0, device=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Amp-Out caps: N/A
  Amp-Out vals:  [0x00 0x00]
  Connection: 11
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b
Node 0x24 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x25 [Audio Output] wcaps 0x11: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x26 [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 2
     0x25 0x0b
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----  1 root audio 116, 13 Oct 18 13:26 /dev/snd/controlC0
crw-rw----  1 root audio 116, 19 Oct 18 13:26 /dev/snd/controlC1
crw-rw----  1 root audio 116, 18 Oct 18 13:26 /dev/snd/hwC1D0
crw-rw----  1 root audio 116,  4 Oct 18 13:26 /dev/snd/midiC0D0
crw-rw----  1 root audio 116, 12 Oct 18 13:27 /dev/snd/pcmC0D0c
crw-rw----  1 root audio 116, 11 Oct 18 13:27 /dev/snd/pcmC0D0p
crw-rw----  1 root audio 116, 10 Oct 18 13:26 /dev/snd/pcmC0D1c
crw-rw----  1 root audio 116,  9 Oct 18 13:27 /dev/snd/pcmC0D1p
crw-rw----  1 root audio 116,  8 Oct 18 13:26 /dev/snd/pcmC0D2c
crw-rw----  1 root audio 116,  7 Oct 18 13:27 /dev/snd/pcmC0D2p
crw-rw----  1 root audio 116,  6 Oct 18 13:26 /dev/snd/pcmC0D3c
crw-rw----  1 root audio 116,  5 Oct 18 13:27 /dev/snd/pcmC0D3p
crw-rw----  1 root audio 116, 17 Oct 18 13:36 /dev/snd/pcmC1D0c
crw-rw----  1 root audio 116, 16 Oct 18 13:41 /dev/snd/pcmC1D0p
crw-rw----  1 root audio 116, 15 Oct 18 13:27 /dev/snd/pcmC1D1p
crw-rw----  1 root audio 116, 14 Oct 18 13:26 /dev/snd/pcmC1D2c
crw-rw----  1 root audio 116,  3 Oct 18 13:26 /dev/snd/seq
crw-rw----  1 root audio 116,  2 Oct 18 13:26 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  80 Oct 18 13:26 .
drwxr-xr-x 3 root root 420 Oct 18 13:26 ..
lrwxrwxrwx 1 root root  12 Oct 18 13:26 pci-0000:00:1b.0 -> ../controlC1
lrwxrwxrwx 1 root root  12 Oct 18 13:26 pci-0000:05:01.0 -> ../controlC0


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 2: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [CA0106]

Card hw:0 'CA0106'/'Audigy SE [SB0570] at 0xec00 irq 17'
  Mixer name	: 'CA0106'
  Components	: ''
  Controls      : 35
  Simple ctrls  : 18
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 255
  Mono: Playback 204 [80%] [-12.75dB] [on]
Simple mixer control 'Line in',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 255
  Front Left: Capture 209 [82%] [1.00dB]
  Front Right: Capture 209 [82%] [1.00dB]
Simple mixer control 'Mic',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 255
  Front Left: Capture 0 [0%] [-99999.99dB]
  Front Right: Capture 0 [0%] [-99999.99dB]
Simple mixer control 'Phone',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 255
  Front Left: Capture 207 [81%] [0.00dB]
  Front Right: Capture 207 [81%] [0.00dB]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958 Center/LFE',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 207 [81%] [0.00dB]
  Front Right: Playback 207 [81%] [0.00dB]
Simple mixer control 'IEC958 Front',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 207 [81%] [0.00dB]
  Front Right: Playback 207 [81%] [0.00dB]
Simple mixer control 'IEC958 Rear',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 207 [81%] [0.00dB]
  Front Right: Playback 207 [81%] [0.00dB]
Simple mixer control 'IEC958 Unknown',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 207 [81%] [0.00dB]
  Front Right: Playback 207 [81%] [0.00dB]
Simple mixer control 'Aux',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 255
  Front Left: Capture 0 [0%] [-99999.99dB]
  Front Right: Capture 0 [0%] [-99999.99dB]
Simple mixer control 'Analog Center/LFE',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 207 [81%] [0.00dB] [on]
  Front Right: Playback 207 [81%] [0.00dB] [on]
Simple mixer control 'Analog Front',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 204 [80%] [0.75dB] [on]
  Front Right: Playback 204 [80%] [0.75dB] [on]
Simple mixer control 'Analog Rear',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 203 [80%] [-1.00dB] [on]
  Front Right: Playback 203 [80%] [-1.00dB] [on]
Simple mixer control 'Analog Side',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 207 [81%] [0.00dB] [on]
  Front Right: Playback 207 [81%] [0.00dB] [on]
Simple mixer control 'Analog Source',0
  Capabilities: cenum
  Items: 'Phone' 'Mic' 'Line in' 'Aux'
  Item0: 'Mic'
Simple mixer control 'CAPTURE feedback',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 0 [0%] [-99999.99dB]
  Front Right: Playback 0 [0%] [-99999.99dB]
Simple mixer control 'Digital Source',0
  Capabilities: cenum
  Items: 'IEC958 out' 'i2s mixer out' 'IEC958 in' 'i2s in' 'AC97 in' 'SRC out'
  Item0: 'i2s in'
Simple mixer control 'Shared Mic/Line in',0
  Capabilities: cenum
  Items: 'Line in' 'Mic in'
  Item0: 'Mic in'

!!-------Mixer controls for card 1 [Intel]

Card hw:1 'Intel'/'HDA Intel at 0xfe8f8000 irq 44'
  Mixer name	: 'Realtek ALC883'
  Components	: 'HDA:10ec0883,1043829f,00100002'
  Controls      : 35
  Simple ctrls  : 20
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 30 [97%] [-1.50dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pswitch penum
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [on]
  Front Right: Playback [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Front Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Front Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%]
  Front Right: 0 [0%]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
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
Simple mixer control 'Side',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%]
  Front Right: 0 [0%]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Beep',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 0 [0%] [-12.00dB] [on]
  Front Right: Capture 0 [0%] [-12.00dB] [on]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 0 [0%] [-12.00dB] [on]
  Front Right: Capture 0 [0%] [-12.00dB] [on]
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Mic' 'Front Mic' 'Line'
  Item0: 'Mic'
Simple mixer control 'Input Source',1
  Capabilities: cenum
  Items: 'Mic' 'Front Mic' 'Line'
  Item0: 'Mic'


!!Alsactl output
!!-------------

--startcollapse--
state.CA0106 {
	control.1 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 255'
		comment.dbmin -5175
		comment.dbmax 1200
		iface MIXER
		name 'Analog Front Playback Volume'
		value.0 204
		value.1 204
	}
	control.2 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 255'
		comment.dbmin -5175
		comment.dbmax 1200
		iface MIXER
		name 'Analog Rear Playback Volume'
		value.0 203
		value.1 203
	}
	control.3 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 255'
		comment.dbmin -5175
		comment.dbmax 1200
		iface MIXER
		name 'Analog Center/LFE Playback Volume'
		value.0 207
		value.1 207
	}
	control.4 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 255'
		comment.dbmin -5175
		comment.dbmax 1200
		iface MIXER
		name 'Analog Side Playback Volume'
		value.0 207
		value.1 207
	}
	control.5 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 255'
		comment.dbmin -5175
		comment.dbmax 1200
		iface MIXER
		name 'IEC958 Front Playback Volume'
		value.0 207
		value.1 207
	}
	control.6 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 255'
		comment.dbmin -5175
		comment.dbmax 1200
		iface MIXER
		name 'IEC958 Rear Playback Volume'
		value.0 207
		value.1 207
	}
	control.7 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 255'
		comment.dbmin -5175
		comment.dbmax 1200
		iface MIXER
		name 'IEC958 Center/LFE Playback Volume'
		value.0 207
		value.1 207
	}
	control.8 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 255'
		comment.dbmin -5175
		comment.dbmax 1200
		iface MIXER
		name 'IEC958 Unknown Playback Volume'
		value.0 207
		value.1 207
	}
	control.9 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 255'
		comment.dbmin -5175
		comment.dbmax 1200
		iface MIXER
		name 'CAPTURE feedback Playback Volume'
		value.0 0
		value.1 0
	}
	control.10 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface PCM
		name 'IEC958 Playback Mask'
		value ffffffff00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
	}
	control.11 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface PCM
		name 'IEC958 Playback Mask'
		index 1
		value ffffffff00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
	}
	control.12 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface PCM
		name 'IEC958 Playback Mask'
		index 2
		value ffffffff00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
	}
	control.13 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface PCM
		name 'IEC958 Playback Mask'
		index 3
		value ffffffff00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
	}
	control.14 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Switch'
		value true
	}
	control.15 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 'IEC958 out'
		comment.item.1 'i2s mixer out'
		comment.item.2 'IEC958 in'
		comment.item.3 'i2s in'
		comment.item.4 'AC97 in'
		comment.item.5 'SRC out'
		iface MIXER
		name 'Digital Source Capture Enum'
		value 'i2s in'
	}
	control.16 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Phone
		comment.item.1 Mic
		comment.item.2 'Line in'
		comment.item.3 Aux
		iface MIXER
		name 'Analog Source Capture Enum'
		value Mic
	}
	control.17 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface PCM
		name 'IEC958 Playback Default'
		value '0492100200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.18 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface PCM
		name 'IEC958 Playback Default'
		index 1
		value '0492100200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.19 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface PCM
		name 'IEC958 Playback Default'
		index 2
		value '0492100200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.20 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface PCM
		name 'IEC958 Playback Default'
		index 3
		value '0492100200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.21 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface PCM
		name 'IEC958 Playback PCM Stream'
		value '0492100200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.22 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface PCM
		name 'IEC958 Playback PCM Stream'
		index 1
		value '0492100200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.23 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface PCM
		name 'IEC958 Playback PCM Stream'
		index 2
		value '0492100200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.24 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface PCM
		name 'IEC958 Playback PCM Stream'
		index 3
		value '0492100200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.25 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 255'
		comment.dbmin -10350
		comment.dbmax 2400
		iface MIXER
		name 'Phone Capture Volume'
		value.0 207
		value.1 207
	}
	control.26 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 255'
		comment.dbmin -10350
		comment.dbmax 2400
		iface MIXER
		name 'Mic Capture Volume'
		value.0 0
		value.1 0
	}
	control.27 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 255'
		comment.dbmin -10350
		comment.dbmax 2400
		iface MIXER
		name 'Line in Capture Volume'
		value.0 209
		value.1 209
	}
	control.28 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 255'
		comment.dbmin -10350
		comment.dbmax 2400
		iface MIXER
		name 'Aux Capture Volume'
		value.0 0
		value.1 0
	}
	control.29 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 'Line in'
		comment.item.1 'Mic in'
		iface MIXER
		name 'Shared Mic/Line in Capture Switch'
		value 'Mic in'
	}
	control.30 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Analog Front Playback Switch'
		value true
	}
	control.31 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Analog Rear Playback Switch'
		value true
	}
	control.32 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Analog Center/LFE Playback Switch'
		value true
	}
	control.33 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Analog Side Playback Switch'
		value true
	}
	control.34 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 255'
		comment.dbmin -6375
		comment.dbmax 0
		iface MIXER
		name 'Master Playback Volume'
		value 204
	}
	control.35 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Master Playback Switch'
		value true
	}
}
state.Intel {
	control.1 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -4650
		comment.dbmax 0
		iface MIXER
		name 'Front Playback Volume'
		value.0 31
		value.1 31
	}
	control.2 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Front Playback Switch'
		value.0 true
		value.1 true
	}
	control.3 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -4650
		comment.dbmax 0
		iface MIXER
		name 'Surround Playback Volume'
		value.0 31
		value.1 31
	}
	control.4 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Surround Playback Switch'
		value.0 true
		value.1 true
	}
	control.5 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 31'
		comment.dbmin -4650
		comment.dbmax 0
		iface MIXER
		name 'Center Playback Volume'
		value 31
	}
	control.6 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 31'
		comment.dbmin -4650
		comment.dbmax 0
		iface MIXER
		name 'LFE Playback Volume'
		value 31
	}
	control.7 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Center Playback Switch'
		value true
	}
	control.8 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'LFE Playback Switch'
		value true
	}
	control.9 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -4650
		comment.dbmax 0
		iface MIXER
		name 'Side Playback Volume'
		value.0 31
		value.1 31
	}
	control.10 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Side Playback Switch'
		value.0 true
		value.1 true
	}
	control.11 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Headphone Playback Switch'
		value.0 true
		value.1 true
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
		comment.count 2
		iface MIXER
		name 'Mic Playback Switch'
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
		name 'Front Mic Playback Volume'
		value.0 0
		value.1 0
	}
	control.15 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Front Mic Playback Switch'
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
		name 'Line Playback Volume'
		value.0 0
		value.1 0
	}
	control.17 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Line Playback Switch'
		value.0 false
		value.1 false
	}
	control.18 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 3'
		comment.dbmin 0
		comment.dbmax 3000
		iface MIXER
		name 'Mic Boost'
		value.0 0
		value.1 0
	}
	control.19 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 3'
		comment.dbmin 0
		comment.dbmax 3000
		iface MIXER
		name 'Front Mic Boost'
		value.0 0
		value.1 0
	}
	control.20 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Capture Switch'
		value.0 true
		value.1 true
	}
	control.21 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Capture Switch'
		index 1
		value.0 true
		value.1 true
	}
	control.22 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -1200
		comment.dbmax 3450
		iface MIXER
		name 'Capture Volume'
		value.0 0
		value.1 0
	}
	control.23 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -1200
		comment.dbmax 3450
		iface MIXER
		name 'Capture Volume'
		index 1
		value.0 0
		value.1 0
	}
	control.24 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Mic
		comment.item.1 'Front Mic'
		comment.item.2 Line
		iface MIXER
		name 'Input Source'
		value Mic
	}
	control.25 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Mic
		comment.item.1 'Front Mic'
		comment.item.2 Line
		iface MIXER
		name 'Input Source'
		index 1
		value Mic
	}
	control.26 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Con Mask'
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.27 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.28 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Default'
		value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.29 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Switch'
		value true
	}
	control.30 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Default PCM Playback Switch'
		value true
	}
	control.31 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Beep Playback Volume'
		value.0 0
		value.1 0
	}
	control.32 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Beep Playback Switch'
		value.0 false
		value.1 false
	}
	control.33 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 31'
		comment.dbmin -4650
		comment.dbmax 0
		iface MIXER
		name 'Master Playback Volume'
		value 30
	}
	control.34 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Master Playback Switch'
		value true
	}
	control.35 {
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
parport_pc
ppdev
snd_hda_codec_realtek
snd_hda_intel
snd_hda_codec
snd_ca0106
snd_hwdep
snd_ac97_codec
ac97_bus
radeon
snd_seq_midi
snd_rawmidi
snd_pcm
snd_seq_midi_event
ttm
snd_seq
drm_kms_helper
snd_timer
snd_seq_device
joydev
snd
asus_atk0110
drm
serio_raw
lp
soundcore
parport
intel_agp
snd_page_alloc
i2c_algo_bit
agpgart
hid_microsoft
floppy
usbhid
pata_marvell
ahci
atl1
hid
libahci
mii


!!Sysfs Files
!!-----------

/sys/class/sound/hwC1D0/init_pin_configs:
0x14 0x01014010
0x15 0x01011012
0x16 0x01016011
0x17 0x01012014
0x18 0x01a19840
0x19 0x02a19c50
0x1a 0x0181304f
0x1b 0x02214c20
0x1c 0x593301f0
0x1d 0x4015e601
0x1e 0x01441130
0x1f 0x411111f0

/sys/class/sound/hwC1D0/driver_pin_configs:

/sys/class/sound/hwC1D0/user_pin_configs:

/sys/class/sound/hwC1D0/init_verbs:


!!ALSA/HDA dmesg
!!------------------

[    6.912064] [drm] initializing kernel modesetting (RV515 0x1002:0x7142).
[    6.918480] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    6.918517]   alloc irq_desc for 44 on node -1
[    6.918519]   alloc kstat_irqs on node -1
[    6.918528] HDA Intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[    6.918551] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    6.919379] [drm] register mmio base: 0xFE9E0000
--
[    6.943993] [drm]     DFP3: INTERNAL_LVTM1
[    6.972526] hda_codec: ALC883: BIOS auto-probing.
[    7.128766] [drm] fb ma
```

I hope someone can spot the problem or suggest a fix

---

### Post by Paulgirardin on 2010-10-18
I tried to run the ALSA upgrade script and failed at:

```

/usr/src/Alsa-1.0.23/alsa-driver-1.0.23/include/config1.h:175: warning: "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
./include/generated/autoconf.h:2222: note: this is the location of the previous definition
/usr/src/Alsa-1.0.23/alsa-driver-1.0.23/acore/pcm_native.c: In function &#8216;snd_pcm_hw_params&#8217;:
/usr/src/Alsa-1.0.23/alsa-driver-1.0.23/acore/pcm_native.c:489: error: implicit declaration of function &#8216;pm_qos_remove_requirement&#8217;
/usr/src/Alsa-1.0.23/alsa-driver-1.0.23/acore/pcm_native.c:492: error: implicit declaration of function &#8216;pm_qos_add_requirement&#8217;
make[3]: *** [/usr/src/Alsa-1.0.23/alsa-driver-1.0.23/acore/pcm_native.o] Error 1
make[2]: *** [/usr/src/Alsa-1.0.23/alsa-driver-1.0.23/acore] Error 2
make[1]: *** [_module_/usr/src/Alsa-1.0.23/alsa-driver-1.0.23] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make: *** [compile] Error 2

***************************************************************************
*  alsa-driver-1.0.23 make failed
***************************************************************************
paul@ubuntu:~$  sudo ./AlsaUpgrade-1.0.23-2.sh -i


**101810-18.58****Alsa-Upgrade-Script-1.0.23-2 *********************
*
* You'll be upgraded from Alsa 1.0.23. to 1.0.23
*
* Run -h option for further help and to look up the workflows
*
* Note1: Alsa won't be upgraded before you run the
*        installation option -i!! 
*        The upgrade procedure shouldn't have any effect on Alsa 
*        until then. However - see Note2
*
* Note2: Do not delete the Alsa Source Directory under /usr/src!
*        When starting the script the 2nd time with -d,
*        the Alsa source dir will be deleted automatically!
*        You won't have sound until you're done with that installation
* 
* DISCLAIMER: Use this script at your own risk. I do not take any 
*             responsibility for any problems caused by running 
*             this script. Before running this script I strongly 
*             advise you to make a backup of your system.
*             You might enter problems restoring the system to its
*             original status when running the restore function 
*             supplied by the script.  
*                            
*  
***************************************************************************


Continue to install the compiled sources of 1.0.23 [y/n]: y


***************************************************************************
*  Alsa packages (drivers/lib/util/firmware/oss) will be installed
***************************************************************************

***************************************************************************
*  Installing all packages...
***************************************************************************

***************************************************************************
*  Installing driver...
***************************************************************************
if [ -L /usr/include/sound ]; then \
		rm -f /usr/include/sound; \
		ln -sf /usr/src/Alsa-1.0.23/alsa-driver-1.0.23/include/sound /usr/include/sound; \
	else \
		rm -rf /usr/include/sound; \
		install -d -m 755 -g root -o root /usr/include/sound; \
		for f in include/sound/*.h; do \
			install -m 644 -g root -o root $f /usr/include/sound; \
		done \
	fi
find /lib/modules/2.6.35-22-generic/kernel/sound -name 'snd*.*o' | xargs rm -f
find /lib/modules/2.6.35-22-generic/kernel/sound -name 'snd*.*o.gz' | xargs rm -f
find /lib/modules/2.6.35-22-generic/kernel/sound -name 'ac97_bus.*o' | xargs rm -f
find /lib/modules/2.6.35-22-generic/kernel/sound -name 'ac97_bus.*o.gz' | xargs rm -f
make[1]: Entering directory `/usr/src/Alsa-1.0.23/alsa-driver-1.0.23/include'
make[1]: Nothing to be done for `modules_install'.
make[1]: Leaving directory `/usr/src/Alsa-1.0.23/alsa-driver-1.0.23/include'
make[1]: Entering directory `/usr/src/Alsa-1.0.23/alsa-driver-1.0.23/acore'
mkdir -p /lib/modules/2.6.35-22-generic/kernel/sound/acore
cp snd-hrtimer.ko snd-hwdep.ko snd-page-alloc.ko snd-pcm.ko snd-rawmidi.ko snd-timer.ko snd.ko /lib/modules/2.6.35-22-generic/kernel/sound/acore
cp: cannot stat `snd-hrtimer.ko': No such file or directory
cp: cannot stat `snd-hwdep.ko': No such file or directory
cp: cannot stat `snd-page-alloc.ko': No such file or directory
cp: cannot stat `snd-pcm.ko': No such file or directory
cp: cannot stat `snd-rawmidi.ko': No such file or directory
cp: cannot stat `snd-timer.ko': No such file or directory
cp: cannot stat `snd.ko': No such file or directory
make[1]: *** [modules_install] Error 1
make[1]: Leaving directory `/usr/src/Alsa-1.0.23/alsa-driver-1.0.23/acore'
make: *** [install-modules] Error 1

***************************************************************************
*  Nothing to install! Run compile -c option first
***************************************************************************

```

Now the ALSA info script outputs:

```
ALSA Information Script v 0.4.59
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

cat: /proc/asound/version: No such file or directory
grep: /proc/asound/cards: No such file or directory
cat: /proc/asound/cards: No such file or directory
cat: /proc/asound/modules: No such file or directory
ls: cannot access /dev/snd/*: No such file or directory
grep: /proc/asound/cards: No such file or directory
/sbin/alsactl: save_state:1504: No soundcards found...
cat: /tmp/alsa-info.iWezHwJd8O/alsactl.tmp: No such file or directory
Automatically upload ALSA information to www.alsa-project.org? [y/N] : y
Uploading information to www.alsa-project.org ...  Done!

Your ALSA information is located at http://www.alsa-project.org/db/?f=9fbbe4189007e384ac6d9a5abdff51cac0e51797


```

Is there any way to reinstall the items that the ALSA upgrade has deleted?

---

### Post by P4man on 2010-10-18
That seems like a nasty bug in that script, if thats what removed alsa.

Id just try try reinstalling alsa;

```
sudo apt-get install linux-sound-base alsa-base alsa-utils
```

The script tried updating it to the same version you already had, so dont bother trying that again and perhaps report the bug to the author.

---

### Post by Paulgirardin on 2010-10-18
Thanks for the reply.
I've already tried your suggestion.It doesn't restore those missing folders.

---

### Post by P4man on 2010-10-18
those '/proc/asound'folders arent folders on your harddrive. They are running processes (in linux, everything is a file). So if your soundcard isnt detected or enabled, those folders wont be there, even if alsa is installed.

Now Im not exactly an alsa expert, but can you post the output of

```
lspci
```

and

```
aplay -l
```

---

### Post by Paulgirardin on 2010-10-18
Ok, that is something I was unaware of and maybe this isn't so disastrous.



lspci:

```
paul@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IB (ICH9) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IB (ICH9) 2 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV515 PRO [Radeon X1300/X1550 Series]
01:00.1 Display controller: ATI Technologies Inc RV515 PRO [Radeon X1300/X1550 Series] (Secondary)
02:00.0 Ethernet controller: Atheros Communications L1 Gigabit Ethernet (rev b0)
03:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6121 SATA II Controller (rev b2)
05:01.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster

```


aplay -l:

```
paul@ubuntu:~$ aplay -l
aplay: device_list:235: no soundcards found...

```

I had already looked at these outputs,but nothing from the sound threads I tried helped

---

### Post by typos1 on 2010-10-18
I ve got a similar problem-no sound, but I dont know why-I had sound for over a week after upgrade to 10.10, then suddenly lost it.

I ve altered every setting but still nothing.

Maveric recognises my usb speakers and XP plays sound through them, but Maverick hasnt for 3 days! 

I m at a total loss

---

### Post by Paulgirardin on 2010-10-18
Pretty much the same story as me.I think installing Flash Player started my problems and I had the same problem with Lucid recently after a kernal update.
That prompted me to install Maverick

---

### Post by typos1 on 2010-10-18
I ve started a post but no one has replied, cant find any known bugs-I dont know what to do.

---

### Post by Paulgirardin on 2010-10-18
When I 'sudo modprobe snd-' and hit Tab then Enter I get:

'FATAL: Module snd_ not found.'

---

### Post by typos1 on 2010-10-18
Same here

---

### Post by P4man on 2010-10-18
Im hoping someone more knowledgable about alsa will come and post the proper solution, but.. its weird. You do have 2 soundcards in that system (onboard and a soundblaster audigy) and neither is initialized. Even weirder that installing flash could cause that :confused:

Anyway. Try purging alsa (thats like removing, but it also removes all configuration files):

```
 sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
```

Be careful, iirc ubuntu will also remove ubuntu-desktop. If that happens, its okay, just reinstall it before you reboot.

Then reinstall alsa (and ubuntu-desktop).  

```
sudo apt-get install linux-sound-base alsa-base alsa-utils ubuntu-desktop
```

reboot, cross fingers.

---

### Post by Paulgirardin on 2010-10-18
Yes 2 sound cards an onboard and a pci.The pci is selected in BIOS.

When I first installed Maverick I had system sounds (login,button etc) and rhythmbox worked just no sound in Flash.I attempted the fixes that gave me sound in Lucid but the ALSA upgrade script didn't like me and killed all sound.It seem I can't reload the ca0106 driver but I am not sure.

I tried the commands you suggest but they don't achieve a positive result.

---

### Post by Paulgirardin on 2010-10-18
bump

---

### Post by Paulgirardin on 2010-10-19
bumpity bump

---

### Post by typos1 on 2010-10-19
I ve only got onboard sound and I didnt install anythng and suddenly sound went after being ok with Maverick for over a week (inlcuding working sound in Flash).

When you say uninstall ububntu desktop P4man do you mean the desktop volume control or the whole OS?

---

### Post by cheetaux on 2010-10-19
I have the same exact problem.  :(

---

### Post by Paulgirardin on 2010-10-19
> **typos1 said:**
> I ve only got onboard sound and I didnt install anythng and suddenly sound went after being ok with Maverick for over a week (inlcuding working sound in Flash).

When you say uninstall ububntu desktop P4man do you mean the desktop volume control or the whole OS?

When linux-sound-base alsa-utils and alsa-base are removed sometimes ubuntu-desktop package is removed as well.The reinstall is just a precautionary step.

---

### Post by typos1 on 2010-10-19
Right so you dont mean the whole OS, just the desktop part of Home folder? So back it up before running those scripts?

---

### Post by P4man on 2010-10-19
ubuntu-desktop is a (meta)package. If you uninstall alsa, sometimes (always?) that package is automatically uninstalled as well. The commands I posted above take care of that, it will reinstall the package, note the install instructins include 'ubuntu-desktop'. I was merely explaining why that is there. 

But all this is a moot point since it apparently doesnt help.

Perhaps one of you facing this problem can post the contents of ```
/var/log/dpkg.log
```
Maybe that sheds some light on what happenend. I can only guess installing flash caused something to be uninstalled that you need, but like I said, Im no expert.

---

### Post by typos1 on 2010-10-19
My sound worked for a week then suddenly went, the OP's prob happened  after installing Flash, not sure whether the third person just had sound  suddenly go or whether it was a Flash prob and they just ended up on this  post looking for a solution.

When I post"" I get "permission denied", it doesnt ask for my password. ?

I m using AWN and I removed the volume icon and replaced it with one in AWN. Wondering whether that might have caused my prob, although I still get pulseaudio preferences and sound in places/preferences.

---

### Post by Paulgirardin on 2010-10-19
Here's dpkg.log from when I tried the ALSA upgrade:

```
2010-10-18 02:13:22 install kdelibs5-data <none> 4:4.5.1-0ubuntu7
2010-10-18 02:13:22 status half-installed kdelibs5-data 4:4.5.1-0ubuntu7
2010-10-18 02:13:23 status triggers-pending hicolor-icon-theme 0.11-1
2010-10-18 02:13:23 status half-installed kdelibs5-data 4:4.5.1-0ubuntu7
2010-10-18 02:13:23 status triggers-pending man-db 2.5.7-4
2010-10-18 02:13:23 status half-installed kdelibs5-data 4:4.5.1-0ubuntu7
2010-10-18 02:13:23 status triggers-pending shared-mime-info 0.71-3
2010-10-18 02:13:23 status half-installed kdelibs5-data 4:4.5.1-0ubuntu7
2010-10-18 02:13:24 status unpacked kdelibs5-data 4:4.5.1-0ubuntu7
2010-10-18 02:13:24 status unpacked kdelibs5-data 4:4.5.1-0ubuntu7
2010-10-18 02:13:24 install docbook-xsl <none> 1.75.2+dfsg-5
2010-10-18 02:13:24 status half-installed docbook-xsl 1.75.2+dfsg-5
2010-10-18 02:13:25 status unpacked docbook-xsl 1.75.2+dfsg-5
2010-10-18 02:13:25 status unpacked docbook-xsl 1.75.2+dfsg-5
2010-10-18 02:13:25 install docbook-xsl-doc-html <none> 1.75.2-1
2010-10-18 02:13:25 status half-installed docbook-xsl-doc-html 1.75.2-1
2010-10-18 02:13:25 status triggers-pending doc-base 0.9.5
2010-10-18 02:13:25 status half-installed docbook-xsl-doc-html 1.75.2-1
2010-10-18 02:13:26 status unpacked docbook-xsl-doc-html 1.75.2-1
2010-10-18 02:13:26 status unpacked docbook-xsl-doc-html 1.75.2-1
2010-10-18 02:13:26 install libqt4-network <none> 4:4.7.0-0ubuntu4
2010-10-18 02:13:26 status half-installed libqt4-network 4:4.7.0-0ubuntu4
2010-10-18 02:13:26 status unpacked libqt4-network 4:4.7.0-0ubuntu4
2010-10-18 02:13:26 status unpacked libqt4-network 4:4.7.0-0ubuntu4
2010-10-18 02:13:27 install libattica0 <none> 0.1.4-1
2010-10-18 02:13:27 status half-installed libattica0 0.1.4-1
2010-10-18 02:13:27 status unpacked libattica0 0.1.4-1
2010-10-18 02:13:27 status unpacked libattica0 0.1.4-1
2010-10-18 02:13:27 install libkdecore5 <none> 4:4.5.1-0ubuntu7
2010-10-18 02:13:27 status half-installed libkdecore5 4:4.5.1-0ubuntu7
2010-10-18 02:13:28 status unpacked libkdecore5 4:4.5.1-0ubuntu7
2010-10-18 02:13:28 status unpacked libkdecore5 4:4.5.1-0ubuntu7
2010-10-18 02:13:28 install libkpty4 <none> 4:4.5.1-0ubuntu7
2010-10-18 02:13:28 status half-installed libkpty4 4:4.5.1-0ubuntu7
2010-10-18 02:13:28 status unpacked libkpty4 4:4.5.1-0ubuntu7
2010-10-18 02:13:29 status unpacked libkpty4 4:4.5.1-0ubuntu7
2010-10-18 02:13:29 install libkdesu5 <none> 4:4.5.1-0ubuntu7
2010-10-18 02:13:29 status half-installed libkdesu5 4:4.5.1-0ubuntu7
2010-10-18 02:13:30 status unpacked libkdesu5 4:4.5.1-0ubuntu7
2010-10-18 02:13:30 status unpacked libkdesu5 4:4.5.1-0ubuntu7
2010-10-18 02:13:30 install libdbusmenu-qt2 <none> 0.6.4-0ubuntu1
2010-10-18 02:13:30 status half-installed libdbusmenu-qt2 0.6.4-0ubuntu1
2010-10-18 02:13:30 status unpacked libdbusmenu-qt2 0.6.4-0ubuntu1
2010-10-18 02:13:30 status unpacked libdbusmenu-qt2 0.6.4-0ubuntu1
2010-10-18 02:13:30 install libqt4-svg <none> 4:4.7.0-0ubuntu4
2010-10-18 02:13:30 status half-installed libqt4-svg 4:4.7.0-0ubuntu4
2010-10-18 02:13:31 status unpacked libqt4-svg 4:4.7.0-0ubuntu4
2010-10-18 02:13:31 status unpacked libqt4-svg 4:4.7.0-0ubuntu4
2010-10-18 02:13:31 install libkdeui5 <none> 4:4.5.1-0ubuntu7
2010-10-18 02:13:31 status half-installed libkdeui5 4:4.5.1-0ubuntu7
2010-10-18 02:13:32 status unpacked libkdeui5 4:4.5.1-0ubuntu7
2010-10-18 02:13:32 status unpacked libkdeui5 4:4.5.1-0ubuntu7
2010-10-18 02:13:32 install libkdnssd4 <none> 4:4.5.1-0ubuntu7
2010-10-18 02:13:32 status half-installed libkdnssd4 4:4.5.1-0ubuntu7
2010-10-18 02:13:33 status unpacked libkdnssd4 4:4.5.1-0ubuntu7
2010-10-18 02:13:33 status unpacked libkdnssd4 4:4.5.1-0ubuntu7
2010-10-18 02:13:33 install libclucene0ldbl <none> 0.9.21b-2
2010-10-18 02:13:33 status half-installed libclucene0ldbl 0.9.21b-2
2010-10-18 02:13:33 status unpacked libclucene0ldbl 0.9.21b-2
2010-10-18 02:13:34 status unpacked libclucene0ldbl 0.9.21b-2
2010-10-18 02:13:34 install libiodbc2 <none> 3.52.6-4
2010-10-18 02:13:34 status half-installed libiodbc2 3.52.6-4
2010-10-18 02:13:35 status unpacked libiodbc2 3.52.6-4
2010-10-18 02:13:35 status unpacked libiodbc2 3.52.6-4
2010-10-18 02:13:35 install soprano-daemon <none> 2.5.2+dfsg.1-0ubuntu1
2010-10-18 02:13:35 status half-installed soprano-daemon 2.5.2+dfsg.1-0ubuntu1
2010-10-18 02:13:35 status unpacked soprano-daemon 2.5.2+dfsg.1-0ubuntu1
2010-10-18 02:13:35 status unpacked soprano-daemon 2.5.2+dfsg.1-0ubuntu1
2010-10-18 02:13:36 install libsoprano4 <none> 2.5.2+dfsg.1-0ubuntu1
2010-10-18 02:13:36 status half-installed libsoprano4 2.5.2+dfsg.1-0ubuntu1
2010-10-18 02:13:36 status unpacked libsoprano4 2.5.2+dfsg.1-0ubuntu1
2010-10-18 02:13:36 status unpacked libsoprano4 2.5.2+dfsg.1-0ubuntu1
2010-10-18 02:13:36 install libnepomuk4 <none> 4:4.5.1-0ubuntu7
2010-10-18 02:13:36 status half-installed libnepomuk4 4:4.5.1-0ubuntu7
2010-10-18 02:13:37 status unpacked libnepomuk4 4:4.5.1-0ubuntu7
2010-10-18 02:13:37 status unpacked libnepomuk4 4:4.5.1-0ubuntu7
2010-10-18 02:13:37 install libsolid4 <none> 4:4.5.1-0ubuntu7
2010-10-18 02:13:37 status half-installed libsolid4 4:4.5.1-0ubuntu7
2010-10-18 02:13:37 status unpacked libsolid4 4:4.5.1-0ubuntu7
2010-10-18 02:13:37 status unpacked libsolid4 4:4.5.1-0ubuntu7
2010-10-18 02:13:38 install libstreams0 <none> 0.7.2-1
2010-10-18 02:13:38 status half-installed libstreams0 0.7.2-1
2010-10-18 02:13:39 status unpacked libstreams0 0.7.2-1
2010-10-18 02:13:39 status unpacked libstreams0 0.7.2-1
2010-10-18 02:13:39 install libstreamanalyzer0 <none> 0.7.2-1
2010-10-18 02:13:39 status half-installed libstreamanalyzer0 0.7.2-1
2010-10-18 02:13:39 status unpacked libstreamanalyzer0 0.7.2-1
2010-10-18 02:13:39 status unpacked libstreamanalyzer0 0.7.2-1
2010-10-18 02:13:40 install libkio5 <none> 4:4.5.1-0ubuntu7
2010-10-18 02:13:40 status half-installed libkio5 4:4.5.1-0ubuntu7
2010-10-18 02:13:40 status unpacked libkio5 4:4.5.1-0ubuntu7
2010-10-18 02:13:40 status unpacked libkio5 4:4.5.1-0ubuntu7
2010-10-18 02:13:41 install libkfile4 <none> 4:4.5.1-0ubuntu7
2010-10-18 02:13:41 status half-installed libkfile4 4:4.5.1-0ubuntu7
2010-10-18 02:13:41 status unpacked libkfile4 4:4.5.1-0ubuntu7
2010-10-18 02:13:41 status unpacked libkfile4 4:4.5.1-0ubuntu7
2010-10-18 02:13:41 install libkjsapi4 <none> 4:4.5.1-0ubuntu7
2010-10-18 02:13:41 status half-installed libkjsapi4 4:4.5.1-0ubuntu7
2010-10-18 02:13:42 status unpacked libkjsapi4 4:4.5.1-0ubuntu7
2010-10-18 02:13:42 status unpacked libkjsapi4 4:4.5.1-0ubuntu7
2010-10-18 02:13:42 install libkparts4 <none> 4:4.5.1-0ubuntu7
2010-10-18 02:13:42 status half-installed libkparts4 4:4.5.1-0ubuntu7
2010-10-18 02:13:42 status unpacked libkparts4 4:4.5.1-0ubuntu7
2010-10-18 02:13:42 status unpacked libkparts4 4:4.5.1-0ubuntu7
2010-10-18 02:13:43 install libktexteditor4 <none> 4:4.5.1-0ubuntu7
2010-10-18 02:13:43 status half-installed libktexteditor4 4:4.5.1-0ubuntu7
2010-10-18 02:13:43 status unpacked libktexteditor4 4:4.5.1-0ubuntu7
2010-10-18 02:13:43 status unpacked libktexteditor4 4:4.5.1-0ubuntu7
2010-10-18 02:13:44 install libphonon4 <none> 4:4.7.0really4.4.2-0ubuntu1
2010-10-18 02:13:44 status half-installed libphonon4 4:4.7.0really4.4.2-0ubuntu1
2010-10-18 02:13:44 status unpacked libphonon4 4:4.7.0really4.4.2-0ubuntu1
2010-10-18 02:13:44 status unpacked libphonon4 4:4.7.0really4.4.2-0ubuntu1
2010-10-18 02:13:45 install libkhtml5 <none> 4:4.5.1-0ubuntu7
2010-10-18 02:13:45 status half-installed libkhtml5 4:4.5.1-0ubuntu7
2010-10-18 02:13:45 status unpacked libkhtml5 4:4.5.1-0ubuntu7
2010-10-18 02:13:45 status unpacked libkhtml5 4:4.5.1-0ubuntu7
2010-10-18 02:13:46 install libkmediaplayer4 <none> 4:4.5.1-0ubuntu7
2010-10-18 02:13:46 status half-installed libkmediaplayer4 4:4.5.1-0ubuntu7
2010-10-18 02:13:46 status unpacked libkmediaplayer4 4:4.5.1-0ubuntu7
2010-10-18 02:13:46 status unpacked libkmediaplayer4 4:4.5.1-0ubuntu7
2010-10-18 02:13:46 install libknewstuff3-4 <none> 4:4.5.1-0ubuntu7
2010-10-18 02:13:46 status half-installed libknewstuff3-4 4:4.5.1-0ubuntu7
2010-10-18 02:13:47 status unpacked libknewstuff3-4 4:4.5.1-0ubuntu7
2010-10-18 02:13:47 status unpacked libknewstuff3-4 4:4.5.1-0ubuntu7
2010-10-18 02:13:47 install libknotifyconfig4 <none> 4:4.5.1-0ubuntu7
2010-10-18 02:13:47 status half-installed libknotifyconfig4 4:4.5.1-0ubuntu7
2010-10-18 02:13:48 status unpacked libknotifyconfig4 4:4.5.1-0ubuntu7
2010-10-18 02:13:48 status unpacked libknotifyconfig4 4:4.5.1-0ubuntu7
2010-10-18 02:13:48 install libkutils4 <none> 4:4.5.1-0ubuntu7
2010-10-18 02:13:48 status half-installed libkutils4 4:4.5.1-0ubuntu7
2010-10-18 02:13:49 status unpacked libkutils4 4:4.5.1-0ubuntu7
2010-10-18 02:13:49 status unpacked libkutils4 4:4.5.1-0ubuntu7
2010-10-18 02:13:49 install libnepomukquery4a <none> 4:4.5.1-0ubuntu7
2010-10-18 02:13:49 status half-installed libnepomukquery4a 4:4.5.1-0ubuntu7
2010-10-18 02:13:50 status unpacked libnepomukquery4a 4:4.5.1-0ubuntu7
2010-10-18 02:13:50 status unpacked libnepomukquery4a 4:4.5.1-0ubuntu7
2010-10-18 02:13:50 install libmodplug1 <none> 1:0.8.8.1-1ubuntu1
2010-10-18 02:13:50 status half-installed libmodplug1 1:0.8.8.1-1ubuntu1
2010-10-18 02:13:51 status unpacked libmodplug1 1:0.8.8.1-1ubuntu1
2010-10-18 02:13:51 status unpacked libmodplug1 1:0.8.8.1-1ubuntu1
2010-10-18 02:13:51 install libmpcdec6 <none> 2:0.1~r459-1
2010-10-18 02:13:51 status half-installed libmpcdec6 2:0.1~r459-1
2010-10-18 02:13:52 status unpacked libmpcdec6 2:0.1~r459-1
2010-10-18 02:13:52 status unpacked libmpcdec6 2:0.1~r459-1
2010-10-18 02:13:52 install libxine1-bin <none> 1.1.18.1-4ubuntu4
2010-10-18 02:13:52 status half-installed libxine1-bin 1.1.18.1-4ubuntu4
2010-10-18 02:13:52 status half-installed libxine1-bin 1.1.18.1-4ubuntu4
2010-10-18 02:13:52 status unpacked libxine1-bin 1.1.18.1-4ubuntu4
2010-10-18 02:13:53 status unpacked libxine1-bin 1.1.18.1-4ubuntu4
2010-10-18 02:13:53 install libxine1-misc-plugins <none> 1.1.18.1-4ubuntu4
2010-10-18 02:13:53 status half-installed libxine1-misc-plugins 1.1.18.1-4ubuntu4
2010-10-18 02:13:53 status unpacked libxine1-misc-plugins 1.1.18.1-4ubuntu4
2010-10-18 02:13:53 status unpacked libxine1-misc-plugins 1.1.18.1-4ubuntu4
2010-10-18 02:13:53 install tsconf <none> 1.0-7build1
2010-10-18 02:13:53 status half-installed tsconf 1.0-7build1
2010-10-18 02:13:53 status half-installed tsconf 1.0-7build1
2010-10-18 02:13:55 status unpacked tsconf 1.0-7build1
2010-10-18 02:13:55 status unpacked tsconf 1.0-7build1
2010-10-18 02:13:55 install libts-0.0-0 <none> 1.0-7build1
2010-10-18 02:13:55 status half-installed libts-0.0-0 1.0-7build1
2010-10-18 02:13:55 status unpacked libts-0.0-0 1.0-7build1
2010-10-18 02:13:55 status unpacked libts-0.0-0 1.0-7build1
2010-10-18 02:13:56 install libdirectfb-1.2-9 <none> 1.2.10.0-4ubuntu2
2010-10-18 02:13:56 status half-installed libdirectfb-1.2-9 1.2.10.0-4ubuntu2
2010-10-18 02:13:56 status unpacked libdirectfb-1.2-9 1.2.10.0-4ubuntu2
2010-10-18 02:13:56 status unpacked libdirectfb-1.2-9 1.2.10.0-4ubuntu2
2010-10-18 02:13:57 install libxcb-shape0 <none> 1.6-1
2010-10-18 02:13:57 status half-installed libxcb-shape0 1.6-1
2010-10-18 02:13:57 status unpacked libxcb-shape0 1.6-1
2010-10-18 02:13:57 status unpacked libxcb-shape0 1.6-1
2010-10-18 02:13:57 install libxcb-xv0 <none> 1.6-1
2010-10-18 02:13:57 status half-installed libxcb-xv0 1.6-1
2010-10-18 02:13:58 status unpacked libxcb-xv0 1.6-1
2010-10-18 02:13:58 status unpacked libxcb-xv0 1.6-1
2010-10-18 02:13:58 install libxine1-x <none> 1.1.18.1-4ubuntu4
2010-10-18 02:13:58 status half-installed libxine1-x 1.1.18.1-4ubuntu4
2010-10-18 02:13:58 status unpacked libxine1-x 1.1.18.1-4ubuntu4
2010-10-18 02:13:58 status unpacked libxine1-x 1.1.18.1-4ubuntu4
2010-10-18 02:13:58 install libxine1-console <none> 1.1.18.1-4ubuntu4
2010-10-18 02:13:58 status half-installed libxine1-console 1.1.18.1-4ubuntu4
2010-10-18 02:13:59 status unpacked libxine1-console 1.1.18.1-4ubuntu4
2010-10-18 02:13:59 status unpacked libxine1-console 1.1.18.1-4ubuntu4
2010-10-18 02:13:59 install libxine1 <none> 1.1.18.1-4ubuntu4
2010-10-18 02:13:59 status half-installed libxine1 1.1.18.1-4ubuntu4
2010-10-18 02:14:00 status unpacked libxine1 1.1.18.1-4ubuntu4
2010-10-18 02:14:00 status unpacked libxine1 1.1.18.1-4ubuntu4
2010-10-18 02:14:00 install phonon-backend-xine <none> 4:4.7.0really4.4.2-0ubuntu1
2010-10-18 02:14:00 status half-installed phonon-backend-xine 4:4.7.0really4.4.2-0ubuntu1
2010-10-18 02:14:01 status unpacked phonon-backend-xine 4:4.7.0really4.4.2-0ubuntu1
2010-10-18 02:14:01 status unpacked phonon-backend-xine 4:4.7.0really4.4.2-0ubuntu1
2010-10-18 02:14:01 install phonon <none> 4:4.7.0really4.4.2-0ubuntu1
2010-10-18 02:14:01 status half-installed phonon 4:4.7.0really4.4.2-0ubuntu1
2010-10-18 02:14:06 status unpacked phonon 4:4.7.0really4.4.2-0ubuntu1
2010-10-18 02:14:06 status unpacked phonon 4:4.7.0really4.4.2-0ubuntu1
2010-10-18 02:14:06 install libqtwebkit4 <none> 2.0.0-0ubuntu1
2010-10-18 02:14:06 status half-installed libqtwebkit4 2.0.0-0ubuntu1
2010-10-18 02:14:07 status unpacked libqtwebkit4 2.0.0-0ubuntu1
2010-10-18 02:14:07 status unpacked libqtwebkit4 2.0.0-0ubuntu1
2010-10-18 02:14:08 install libkdewebkit5 <none> 4:4.5.1-0ubuntu7
2010-10-18 02:14:08 status half-installed libkdewebkit5 4:4.5.1-0ubuntu7
2010-10-18 02:14:08 status unpacked libkdewebkit5 4:4.5.1-0ubuntu7
2010-10-18 02:14:08 status unpacked libkdewebkit5 4:4.5.1-0ubuntu7
2010-10-18 02:14:08 install libqca2 <none> 2.0.2-1ubuntu2
2010-10-18 02:14:08 status half-installed libqca2 2.0.2-1ubuntu2
2010-10-18 02:14:08 status half-installed libqca2 2.0.2-1ubuntu2
2010-10-18 02:14:09 status unpacked libqca2 2.0.2-1ubuntu2
2010-10-18 02:14:09 status unpacked libqca2 2.0.2-1ubuntu2
2010-10-18 02:14:09 install libqt4-opengl <none> 4:4.7.0-0ubuntu4
2010-10-18 02:14:09 status half-installed libqt4-opengl 4:4.7.0-0ubuntu4
2010-10-18 02:14:10 status unpacked libqt4-opengl 4:4.7.0-0ubuntu4
2010-10-18 02:14:10 status unpacked libqt4-opengl 4:4.7.0-0ubuntu4
2010-10-18 02:14:10 install libqt4-script <none> 4:4.7.0-0ubuntu4
2010-10-18 02:14:10 status half-installed libqt4-script 4:4.7.0-0ubuntu4
2010-10-18 02:14:10 status unpacked libqt4-script 4:4.7.0-0ubuntu4
2010-10-18 02:14:10 status unpacked libqt4-script 4:4.7.0-0ubuntu4
2010-10-18 02:14:11 install libthreadweaver4 <none> 4:4.5.1-0ubuntu7
2010-10-18 02:14:11 status half-installed libthreadweaver4 4:4.5.1-0ubuntu7
2010-10-18 02:14:11 status unpacked libthreadweaver4 4:4.5.1-0ubuntu7
2010-10-18 02:14:11 status unpacked libthreadweaver4 4:4.5.1-0ubuntu7
2010-10-18 02:14:12 install libplasma3 <none> 4:4.5.1-0ubuntu7
2010-10-18 02:14:12 status half-installed libplasma3 4:4.5.1-0ubuntu7
2010-10-18 02:14:12 status unpacked libplasma3 4:4.5.1-0ubuntu7
2010-10-18 02:14:12 status unpacked libplasma3 4:4.5.1-0ubuntu7
2010-10-18 02:14:13 install libssh-4 <none> 0.4.5-1
2010-10-18 02:14:13 status half-installed libssh-4 0.4.5-1
2010-10-18 02:14:13 status unpacked libssh-4 0.4.5-1
2010-10-18 02:14:13 status unpacked libssh-4 0.4.5-1
2010-10-18 02:14:14 install kdebase-runtime-data <none> 4:4.5.1-0ubuntu3
2010-10-18 02:14:14 status half-installed kdebase-runtime-data 4:4.5.1-0ubuntu3
2010-10-18 02:14:14 status half-installed kdebase-runtime-data 4:4.5.1-0ubuntu3
2010-10-18 02:14:14 status half-installed kdebase-runtime-data 4:4.5.1-0ubuntu3
2010-10-18 02:14:16 status unpacked kdebase-runtime-data 4:4.5.1-0ubuntu3
2010-10-18 02:14:16 status unpacked kdebase-runtime-data 4:4.5.1-0ubuntu3
2010-10-18 02:14:16 install libkatepartinterfaces4 <none> 4:4.5.1-0ubuntu7
2010-10-18 02:14:16 status half-installed libkatepartinterfaces4 4:4.5.1-0ubuntu7
2010-10-18 02:14:17 status unpacked libkatepartinterfaces4 4:4.5.1-0ubuntu7
2010-10-18 02:14:17 status unpacked libkatepartinterfaces4 4:4.5.1-0ubuntu7
2010-10-18 02:14:17 install libkjsembed4 <none> 4:4.5.1-0ubuntu7
2010-10-18 02:14:17 status half-installed libkjsembed4 4:4.5.1-0ubuntu7
2010-10-18 02:14:18 status unpacked libkjsembed4 4:4.5.1-0ubuntu7
2010-10-18 02:14:18 status unpacked libkjsembed4 4:4.5.1-0ubuntu7
2010-10-18 02:14:18 install libkntlm4 <none> 4:4.5.1-0ubuntu7
2010-10-18 02:14:18 status half-installed libkntlm4 4:4.5.1-0ubuntu7
2010-10-18 02:14:19 status unpacked libkntlm4 4:4.5.1-0ubuntu7
2010-10-18 02:14:19 status unpacked libkntlm4 4:4.5.1-0ubuntu7
2010-10-18 02:14:19 install libkrosscore4 <none> 4:4.5.1-0ubuntu7
2010-10-18 02:14:19 status half-installed libkrosscore4 4:4.5.1-0ubuntu7
2010-10-18 02:14:19 status unpacked libkrosscore4 4:4.5.1-0ubuntu7
2010-10-18 02:14:20 status unpacked libkrosscore4 4:4.5.1-0ubuntu7
2010-10-18 02:14:20 install libkrossui4 <none> 4:4.5.1-0ubuntu7
2010-10-18 02:14:20 status half-installed libkrossui4 4:4.5.1-0ubuntu7
2010-10-18 02:14:20 status unpacked libkrossui4 4:4.5.1-0ubuntu7
2010-10-18 02:14:20 status unpacked libkrossui4 4:4.5.1-0ubuntu7
2010-10-18 02:14:21 install libpolkit-qt-1-0 <none> 0.95.1-1ubuntu1
2010-10-18 02:14:21 status half-installed libpolkit-qt-1-0 0.95.1-1ubuntu1
2010-10-18 02:14:34 status unpacked libpolkit-qt-1-0 0.95.1-1ubuntu1
2010-10-18 02:14:34 status unpacked libpolkit-qt-1-0 0.95.1-1ubuntu1
2010-10-18 02:14:35 install kdoctools <none> 4:4.5.1-0ubuntu7
2010-10-18 02:14:35 status half-installed kdoctools 4:4.5.1-0ubuntu7
2010-10-18 02:14:35 status half-installed kdoctools 4:4.5.1-0ubuntu7
2010-10-18 02:14:35 status unpacked kdoctools 4:4.5.1-0ubuntu7
2010-10-18 02:14:35 status unpacked kdoctools 4:4.5.1-0ubuntu7
2010-10-18 02:14:36 install kdelibs-bin <none> 4:4.5.1-0ubuntu7
2010-10-18 02:14:36 status half-installed kdelibs-bin 4:4.5.1-0ubuntu7
2010-10-18 02:14:36 status half-installed kdelibs-bin 4:4.5.1-0ubuntu7
2010-10-18 02:14:36 status unpacked kdelibs-bin 4:4.5.1-0ubuntu7
2010-10-18 02:14:36 status unpacked kdelibs-bin 4:4.5.1-0ubuntu7
2010-10-18 02:14:36 install kdelibs5-plugins <none> 4:4.5.1-0ubuntu7
2010-10-18 02:14:36 status half-installed kdelibs5-plugins 4:4.5.1-0ubuntu7
2010-10-18 02:14:37 status unpacked kdelibs5-plugins 4:4.5.1-0ubuntu7
2010-10-18 02:14:37 status unpacked kdelibs5-plugins 4:4.5.1-0ubuntu7
2010-10-18 02:14:37 install oxygen-icon-theme <none> 4:4.5.1-0ubuntu1
2010-10-18 02:14:37 status half-installed oxygen-icon-theme 4:4.5.1-0ubuntu1
2010-10-18 02:14:37 status half-installed oxygen-icon-theme 4:4.5.1-0ubuntu1
2010-10-18 02:14:40 status unpacked oxygen-icon-theme 4:4.5.1-0ubuntu1
2010-10-18 02:14:40 status unpacked oxygen-icon-theme 4:4.5.1-0ubuntu1
2010-10-18 02:14:40 install shared-desktop-ontologies <none> 0.5-1
2010-10-18 02:14:40 status half-installed shared-desktop-ontologies 0.5-1
2010-10-18 02:14:41 status unpacked shared-desktop-ontologies 0.5-1
2010-10-18 02:14:41 status unpacked shared-desktop-ontologies 0.5-1
2010-10-18 02:14:41 install plasma-scriptengine-javascript <none> 4:4.5.1-0ubuntu3
2010-10-18 02:14:41 status half-installed plasma-scriptengine-javascript 4:4.5.1-0ubuntu3
2010-10-18 02:14:42 status unpacked plasma-scriptengine-javascript 4:4.5.1-0ubuntu3
2010-10-18 02:14:42 status unpacked plasma-scriptengine-javascript 4:4.5.1-0ubuntu3
2010-10-18 02:14:42 install kdebase-runtime <none> 4:4.5.1-0ubuntu3
2010-10-18 02:14:42 status half-installed kdebase-runtime 4:4.5.1-0ubuntu3
2010-10-18 02:14:42 status half-installed kdebase-runtime 4:4.5.1-0ubuntu3
2010-10-18 02:14:42 status triggers-pending desktop-file-utils 0.16-0ubuntu4
2010-10-18 02:14:42 status half-installed kdebase-runtime 4:4.5.1-0ubuntu3
2010-10-18 02:14:42 status triggers-pending python-gmenu 2.30.4-0ubuntu1
2010-10-18 02:14:42 status half-installed kdebase-runtime 4:4.5.1-0ubuntu3
2010-10-18 02:14:43 status unpacked kdebase-runtime 4:4.5.1-0ubuntu3
2010-10-18 02:14:43 status unpacked kdebase-runtime 4:4.5.1-0ubuntu3
2010-10-18 02:14:44 install libqt4-designer <none> 4:4.7.0-0ubuntu4
2010-10-18 02:14:44 status half-installed libqt4-designer 4:4.7.0-0ubuntu4
2010-10-18 02:14:45 status unpacked libqt4-designer 4:4.7.0-0ubuntu4
2010-10-18 02:14:45 status unpacked libqt4-designer 4:4.7.0-0ubuntu4
2010-10-18 02:14:46 install libqt4-sql <none> 4:4.7.0-0ubuntu4
2010-10-18 02:14:46 status half-installed libqt4-sql 4:4.7.0-0ubuntu4
2010-10-18 02:14:46 status unpacked libqt4-sql 4:4.7.0-0ubuntu4
2010-10-18 02:14:46 status unpacked libqt4-sql 4:4.7.0-0ubuntu4
2010-10-18 02:14:46 install libqt4-qt3support <none> 4:4.7.0-0ubuntu4
2010-10-18 02:14:46 status half-installed libqt4-qt3support 4:4.7.0-0ubuntu4
2010-10-18 02:14:47 status unpacked libqt4-qt3support 4:4.7.0-0ubuntu4
2010-10-18 02:14:47 status unpacked libqt4-qt3support 4:4.7.0-0ubuntu4
2010-10-18 02:14:47 install libkde3support4 <none> 4:4.5.1-0ubuntu7
2010-10-18 02:14:47 status half-installed libkde3support4 4:4.5.1-0ubuntu7
2010-10-18 02:14:47 status unpacked libkde3support4 4:4.5.1-0ubuntu7
2010-10-18 02:14:47 status unpacked libkde3support4 4:4.5.1-0ubuntu7
2010-10-18 02:14:48 install libkimproxy4 <none> 4:4.5.1-0ubuntu7
2010-10-18 02:14:48 status half-installed libkimproxy4 4:4.5.1-0ubuntu7
2010-10-18 02:14:48 status unpacked libkimproxy4 4:4.5.1-0ubuntu7
2010-10-18 02:14:48 status unpacked libkimproxy4 4:4.5.1-0ubuntu7
2010-10-18 02:14:49 install libknewstuff2-4 <none> 4:4.5.1-0ubuntu7
2010-10-18 02:14:49 status half-installed libknewstuff2-4 4:4.5.1-0ubuntu7
2010-10-18 02:14:49 status unpacked libknewstuff2-4 4:4.5.1-0ubuntu7
2010-10-18 02:14:49 status unpacked libknewstuff2-4 4:4.5.1-0ubuntu7
2010-10-18 02:14:50 install kdelibs5 <none> 4:4.5.1-0ubuntu7
2010-10-18 02:14:50 status half-installed kdelibs5 4:4.5.1-0ubuntu7
2010-10-18 02:14:50 status unpacked kdelibs5 4:4.5.1-0ubuntu7
2010-10-18 02:14:50 status unpacked kdelibs5 4:4.5.1-0ubuntu7
2010-10-18 02:14:51 install filelight <none> 1.9~rc3-2
2010-10-18 02:14:51 status half-installed filelight 1.9~rc3-2
2010-10-18 02:14:51 status half-installed filelight 1.9~rc3-2
2010-10-18 02:14:51 status half-installed filelight 1.9~rc3-2
2010-10-18 02:14:51 status half-installed filelight 1.9~rc3-2
2010-10-18 02:14:51 status half-installed filelight 1.9~rc3-2
2010-10-18 02:14:51 status triggers-pending menu 2.1.44ubuntu1
2010-10-18 02:14:51 status half-installed filelight 1.9~rc3-2
2010-10-18 02:14:52 status unpacked filelight 1.9~rc3-2
2010-10-18 02:14:52 status unpacked filelight 1.9~rc3-2
2010-10-18 02:14:52 install libhal-storage1 <none> 0.5.14-0ubuntu6
2010-10-18 02:14:52 status half-installed libhal-storage1 0.5.14-0ubuntu6
2010-10-18 02:14:53 status unpacked libhal-storage1 0.5.14-0ubuntu6
2010-10-18 02:14:53 status unpacked libhal-storage1 0.5.14-0ubuntu6
2010-10-18 02:14:53 install hal-info <none> 20091130-1
2010-10-18 02:14:53 status half-installed hal-info 20091130-1
2010-10-18 02:14:53 status unpacked hal-info 20091130-1
2010-10-18 02:14:53 status unpacked hal-info 20091130-1
2010-10-18 02:14:53 install hal <none> 0.5.14-0ubuntu6
2010-10-18 02:14:53 status half-installed hal 0.5.14-0ubuntu6
2010-10-18 02:14:54 status half-installed hal 0.5.14-0ubuntu6
2010-10-18 02:14:55 status unpacked hal 0.5.14-0ubuntu6
2010-10-18 02:14:55 status unpacked hal 0.5.14-0ubuntu6
2010-10-18 02:14:55 install icoutils <none> 0.29.1-0ubuntu1
2010-10-18 02:14:55 status half-installed icoutils 0.29.1-0ubuntu1
2010-10-18 02:14:55 status half-installed icoutils 0.29.1-0ubuntu1
2010-10-18 02:14:56 status unpacked icoutils 0.29.1-0ubuntu1
2010-10-18 02:14:56 status unpacked icoutils 0.29.1-0ubuntu1
2010-10-18 02:14:56 install libqapt1 <none> 1.0.3-0ubuntu2
2010-10-18 02:14:56 status half-installed libqapt1 1.0.3-0ubuntu2
2010-10-18 02:14:57 status unpacked libqapt1 1.0.3-0ubuntu2
2010-10-18 02:14:57 status unpacked libqapt1 1.0.3-0ubuntu2
2010-10-18 02:14:57 install libqapt-runtime <none> 1.0.3-0ubuntu2
2010-10-18 02:14:57 status half-installed libqapt-runtime 1.0.3-0ubuntu2
2010-10-18 02:14:57 status unpacked libqapt-runtime 1.0.3-0ubuntu2
2010-10-18 02:14:58 status unpacked libqapt-runtime 1.0.3-0ubuntu2
2010-10-18 02:14:58 install qapt-batch <none> 1.0.3-0ubuntu2
2010-10-18 02:14:58 status half-installed qapt-batch 1.0.3-0ubuntu2
2010-10-18 02:14:58 status unpacked qapt-batch 1.0.3-0ubuntu2
2010-10-18 02:14:58 status unpacked qapt-batch 1.0.3-0ubuntu2
2010-10-18 02:14:58 install kubuntu-debug-installer <none> 10.10ubuntu4
2010-10-18 02:14:58 status half-installed kubuntu-debug-installer 10.10ubuntu4
2010-10-18 02:14:59 status unpacked kubuntu-debug-installer 10.10ubuntu4
2010-10-18 02:14:59 status unpacked kubuntu-debug-installer 10.10ubuntu4
2010-10-18 02:14:59 install mysql-common <none> 5.1.49-1ubuntu8
2010-10-18 02:14:59 status half-installed mysql-common 5.1.49-1ubuntu8
2010-10-18 02:14:59 status unpacked mysql-common 5.1.49-1ubuntu8
2010-10-18 02:14:59 status unpacked mysql-common 5.1.49-1ubuntu8
2010-10-18 02:14:59 install libmysqlclient16 <none> 5.1.49-1ubuntu8
2010-10-18 02:14:59 status half-installed libmysqlclient16 5.1.49-1ubuntu8
2010-10-18 02:15:00 status unpacked libmysqlclient16 5.1.49-1ubuntu8
2010-10-18 02:15:00 status unpacked libmysqlclient16 5.1.49-1ubuntu8
2010-10-18 02:15:00 install libqt4-sql-mysql <none> 4:4.7.0-0ubuntu4
2010-10-18 02:15:00 status half-installed libqt4-sql-mysql 4:4.7.0-0ubuntu4
2010-10-18 02:15:01 status unpacked libqt4-sql-mysql 4:4.7.0-0ubuntu4
2010-10-18 02:15:01 status unpacked libqt4-sql-mysql 4:4.7.0-0ubuntu4
2010-10-18 02:15:01 install libreadline5 <none> 5.2-7build1
2010-10-18 02:15:01 status half-installed libreadline5 5.2-7build1
2010-10-18 02:15:02 status unpacked libreadline5 5.2-7build1
2010-10-18 02:15:02 status unpacked libreadline5 5.2-7build1
2010-10-18 02:15:02 install virtuoso-opensource-6.1-common <none> 6.1.2+dfsg1-1ubuntu4
2010-10-18 02:15:02 status half-installed virtuoso-opensource-6.1-common 6.1.2+dfsg1-1ubuntu4
2010-10-18 02:15:02 status half-installed virtuoso-opensource-6.1-common 6.1.2+dfsg1-1ubuntu4
2010-10-18 02:15:03 status unpacked virtuoso-opensource-6.1-common 6.1.2+dfsg1-1ubuntu4
2010-10-18 02:15:03 status unpacked virtuoso-opensource-6.1-common 6.1.2+dfsg1-1ubuntu4
2010-10-18 02:15:04 install odbcinst1debian2 <none> 2.2.14p2-1ubuntu1
2010-10-18 02:15:04 status half-installed odbcinst1debian2 2.2.14p2-1ubuntu1
2010-10-18 02:15:04 status unpacked odbcinst1debian2 2.2.14p2-1ubuntu1
2010-10-18 02:15:04 status unpacked odbcinst1debian2 2.2.14p2-1ubuntu1
2010-10-18 02:15:05 install odbcinst <none> 2.2.14p2-1ubuntu1
2010-10-18 02:15:05 status half-installed odbcinst 2.2.14p2-1ubuntu1
2010-10-18 02:15:05 status half-installed odbcinst 2.2.14p2-1ubuntu1
2010-10-18 02:15:05 status unpacked odbcinst 2.2.14p2-1ubuntu1
2010-10-18 02:15:05 status unpacked odbcinst 2.2.14p2-1ubuntu1
2010-10-18 02:15:05 install libvirtodbc0 <none> 6.1.2+dfsg1-1ubuntu4
2010-10-18 02:15:05 status half-installed libvirtodbc0 6.1.2+dfsg1-1ubuntu4
2010-10-18 02:15:06 status unpacked libvirtodbc0 6.1.2+dfsg1-1ubuntu4
2010-10-18 02:15:06 status unpacked libvirtodbc0 6.1.2+dfsg1-1ubuntu4
2010-10-18 02:15:06 install smartdimmer <none> 0.8b4-1ubuntu3
2010-10-18 02:15:06 status half-installed smartdimmer 0.8b4-1ubuntu3
2010-10-18 02:15:06 status unpacked smartdimmer 0.8b4-1ubuntu3
2010-10-18 02:15:06 status unpacked smartdimmer 0.8b4-1ubuntu3
2010-10-18 02:15:06 install ttf-dejavu <none> 2.31-1
2010-10-18 02:15:06 status half-installed ttf-dejavu 2.31-1
2010-10-18 02:15:07 status unpacked ttf-dejavu 2.31-1
2010-10-18 02:15:07 status unpacked ttf-dejavu 2.31-1
2010-10-18 02:15:07 install virtuoso-opensource-6.1-bin <none> 6.1.2+dfsg1-1ubuntu4
2010-10-18 02:15:07 status half-installed virtuoso-opensource-6.1-bin 6.1.2+dfsg1-1ubuntu4
2010-10-18 02:15:07 status half-installed virtuoso-opensource-6.1-bin 6.1.2+dfsg1-1ubuntu4
2010-10-18 02:15:07 status unpacked virtuoso-opensource-6.1-bin 6.1.2+dfsg1-1ubuntu4
2010-10-18 02:15:08 status unpacked virtuoso-opensource-6.1-bin 6.1.2+dfsg1-1ubuntu4
2010-10-18 02:15:08 install virtuoso-minimal <none> 6.1.2+dfsg1-1ubuntu4
2010-10-18 02:15:08 status half-installed virtuoso-minimal 6.1.2+dfsg1-1ubuntu4
2010-10-18 02:15:09 status unpacked virtuoso-minimal 6.1.2+dfsg1-1ubuntu4
2010-10-18 02:15:09 status unpacked virtuoso-minimal 6.1.2+dfsg1-1ubuntu4
2010-10-18 02:15:09 trigproc hicolor-icon-theme 0.11-1 0.11-1
2010-10-18 02:15:09 status half-configured hicolor-icon-theme 0.11-1
2010-10-18 02:15:09 status installed hicolor-icon-theme 0.11-1
2010-10-18 02:15:10 trigproc man-db 2.5.7-4 2.5.7-4
2010-10-18 02:15:10 status half-configured man-db 2.5.7-4
2010-10-18 02:15:11 status installed man-db 2.5.7-4
2010-10-18 02:15:11 trigproc shared-mime-info 0.71-3 0.71-3
2010-10-18 02:15:11 status half-configured shared-mime-info 0.71-3
2010-10-18 02:15:12 status installed shared-mime-info 0.71-3
2010-10-18 02:15:12 trigproc doc-base 0.9.5 0.9.5
2010-10-18 02:15:12 status half-configured doc-base 0.9.5
2010-10-18 02:15:12 status installed doc-base 0.9.5
2010-10-18 02:15:12 trigproc desktop-file-utils 0.16-0ubuntu4 0.16-0ubuntu4
2010-10-18 02:15:12 status half-configured desktop-file-utils 0.16-0ubuntu4
2010-10-18 02:15:12 status installed desktop-file-utils 0.16-0ubuntu4
2010-10-18 02:15:12 trigproc python-gmenu 2.30.4-0ubuntu1 2.30.4-0ubuntu1
2010-10-18 02:15:12 status half-configured python-gmenu 2.30.4-0ubuntu1
2010-10-18 02:15:12 status installed python-gmenu 2.30.4-0ubuntu1
2010-10-18 02:15:12 status triggers-pending python-support 1.0.9ubuntu1
2010-10-18 02:15:13 trigproc menu 2.1.44ubuntu1 2.1.44ubuntu1
2010-10-18 02:15:13 status half-configured menu 2.1.44ubuntu1
2010-10-18 02:15:13 status installed menu 2.1.44ubuntu1
2010-10-18 02:15:13 trigproc python-support 1.0.9ubuntu1 1.0.9ubuntu1
2010-10-18 02:15:13 status half-configured python-support 1.0.9ubuntu1
2010-10-18 02:15:14 status installed python-support 1.0.9ubuntu1
2010-10-18 02:15:15 startup packages configure
2010-10-18 02:15:15 configure kdelibs5-data 4:4.5.1-0ubuntu7 4:4.5.1-0ubuntu7
2010-10-18 02:15:15 status unpacked kdelibs5-data 4:4.5.1-0ubuntu7
2010-10-18 02:15:15 status unpacked kdelibs5-data 4:4.5.1-0ubuntu7
2010-10-18 02:15:15 status unpacked kdelibs5-data 4:4.5.1-0ubuntu7
2010-10-18 02:15:15 status half-configured kdelibs5-data 4:4.5.1-0ubuntu7
2010-10-18 02:15:15 status installed kdelibs5-data 4:4.5.1-0ubuntu7
2010-10-18 02:15:15 configure docbook-xsl 1.75.2+dfsg-5 1.75.2+dfsg-5
2010-10-18 02:15:15 status unpacked docbook-xsl 1.75.2+dfsg-5
2010-10-18 02:15:15 status half-configured docbook-xsl 1.75.2+dfsg-5
2010-10-18 02:15:15 status installed docbook-xsl 1.75.2+dfsg-5
2010-10-18 02:15:15 configure docbook-xsl-doc-html 1.75.2-1 1.75.2-1
2010-10-18 02:15:15 status unpacked docbook-xsl-doc-html 1.75.2-1
2010-10-18 02:15:15 status half-configured docbook-xsl-doc-html 1.75.2-1
2010-10-18 02:15:15 status installed docbook-xsl-doc-html 1.75.2-1
2010-10-18 02:15:15 configure libqt4-network 4:4.7.0-0ubuntu4 4:4.7.0-0ubuntu4
2010-10-18 02:15:15 status unpacked libqt4-network 4:4.7.0-0ubuntu4
2010-10-18 02:15:15 status half-configured libqt4-network 4:4.7.0-0ubuntu4
2010-10-18 02:15:16 status installed libqt4-network 4:4.7.0-0ubuntu4
2010-10-18 02:15:16 status triggers-pending libc-bin 2.12.1-0ubuntu6
2010-10-18 02:15:16 configure libattica0 0.1.4-1 0.1.4-1
2010-10-18 02:15:16 status unpacked libattica0 0.1.4-1
2010-10-18 02:15:16 status half-configured libattica0 0.1.4-1
2010-10-18 02:15:16 status installed libattica0 0.1.4-1
2010-10-18 02:15:16 configure libkdecore5 4:4.5.1-0ubuntu7 4:4.5.1-0ubuntu7
2010-10-18 02:15:16 status unpacked libkdecore5 4:4.5.1-0ubuntu7
2010-10-18 02:15:16 status half-configured libkdecore5 4:4.5.1-0ubuntu7
2010-10-18 02:15:16 status installed libkdecore5 4:4.5.1-0ubuntu7
2010-10-18 02:15:16 configure libkpty4 4:4.5.1-0ubuntu7 4:4.5.1-0ubuntu7
2010-10-18 02:15:16 status unpacked libkpty4 4:4.5.1-0ubuntu7
2010-10-18 02:15:16 status half-configured libkpty4 4:4.5.1-0ubuntu7
2010-10-18 02:15:16 status installed libkpty4 4:4.5.1-0ubuntu7
2010-10-18 02:15:16 configure libkdesu5 4:4.5.1-0ubuntu7 4:4.5.1-0ubuntu7
2010-10-18 02:15:16 status unpacked libkdesu5 4:4.5.1-0ubuntu7
2010-10-18 02:15:16 status half-configured libkdesu5 4:4.5.1-0ubuntu7
2010-10-18 02:15:17 status installed libkdesu5 4:4.5.1-0ubuntu7
2010-10-18 02:15:17 configure libdbusmenu-qt2 0.6.4-0ubuntu1 0.6.4-0ubuntu1
2010-10-18 02:15:17 status unpacked libdbusmenu-qt2 0.6.4-0ubuntu1
2010-10-18 02:15:17 status half-configured libdbusmenu-qt2 0.6.4-0ubuntu1
2010-10-18 02:15:17 status installed libdbusmenu-qt2 0.6.4-0ubuntu1
2010-10-18 02:15:17 configure libqt4-svg 4:4.7.0-0ubuntu4 4:4.7.0-0ubuntu4
2010-10-18 02:15:17 status unpacked libqt4-svg 4:4.7.0-0ubuntu4
2010-10-18 02:15:17 status half-configured libqt4-svg 4:4.7.0-0ubuntu4
2010-10-18 02:15:18 status installed libqt4-svg 4:4.7.0-0ubuntu4
2010-10-18 02:15:18 configure libkdeui5 4:4.5.1-0ubuntu7 4:4.5.1-0ubuntu7
2010-10-18 02:15:18 status unpacked libkdeui5 4:4.5.1-0ubuntu7
2010-10-18 02:15:18 status half-configured libkdeui5 4:4.5.1-0ubuntu7
2010-10-18 02:15:18 status installed libkdeui5 4:4.5.1-0ubuntu7
2010-10-18 02:15:18 configure libkdnssd4 4:4.5.1-0ubuntu7 4:4.5.1-0ubuntu7
2010-10-18 02:15:18 status unpacked libkdnssd4 4:4.5.1-0ubuntu7
2010-10-18 02:15:18 status half-configured libkdnssd4 4:4.5.1-0ubuntu7
2010-10-18 02:15:18 status installed libkdnssd4 4:4.5.1-0ubuntu7
2010-10-18 02:15:18 configure libclucene0ldbl 0.9.21b-2 0.9.21b-2
2010-10-18 02:15:18 status unpacked libclucene0ldbl 0.9.21b-2
2010-10-18 02:15:18 status half-configured libclucene0ldbl 0.9.21b-2
2010-10-18 02:15:19 status installed libclucene0ldbl 0.9.21b-2
2010-10-18 02:15:19 configure libiodbc2 3.52.6-4 3.52.6-4
2010-10-18 02:15:19 status unpacked libiodbc2 3.52.6-4
2010-10-18 02:15:19 status half-configured libiodbc2 3.52.6-4
2010-10-18 02:15:19 status installed libiodbc2 3.52.6-4
2010-10-18 02:15:19 configure soprano-daemon 2.5.2+dfsg.1-0ubuntu1 2.5.2+dfsg.1-0ubuntu1
2010-10-18 02:15:19 status unpacked soprano-daemon 2.5.2+dfsg.1-0ubuntu1
2010-10-18 02:15:20 status half-configured soprano-daemon 2.5.2+dfsg.1-0ubuntu1
2010-10-18 02:15:20 status installed soprano-daemon 2.5.2+dfsg.1-0ubuntu1
2010-10-18 02:15:20 configure libsoprano4 2.5.2+dfsg.1-0ubuntu1 2.5.2+dfsg.1-0ubuntu1
2010-10-18 02:15:20 status unpacked libsoprano4 2.5.2+dfsg.1-0ubuntu1
2010-10-18 02:15:20 status half-configured libsoprano4 2.5.2+dfsg.1-0ubuntu1
2010-10-18 02:15:20 status installed libsoprano4 2.5.2+dfsg.1-0ubuntu1
2010-10-18 02:15:20 configure libnepomuk4 4:4.5.1-0ubuntu7 4:4.5.1-0ubuntu7
2010-10-18 02:15:20 status unpacked libnepomuk4 4:4.5.1-0ubuntu7
2010-10-18 02:15:20 status half-configured libnepomuk4 4:4.5.1-0ubuntu7
2010-10-18 02:15:20 status installed libnepomuk4 4:4.5.1-0ubuntu7
2010-10-18 02:15:20 configure libsolid4 4:4.5.1-0ubuntu7 4:4.5.1-0ubuntu7
2010-10-18 02:15:20 status unpacked libsolid4 4:4.5.1-0ubuntu7
2010-10-18 02:15:20 status half-configured libsolid4 4:4.5.1-0ubuntu7
2010-10-18 02:15:20 status installed libsolid4 4:4.5.1-0ubuntu7
2010-10-18 02:15:21 configure libstreams0 0.7.2-1 0.7.2-1
2010-10-18 02:15:21 status unpacked libstreams0 0.7.2-1
2010-10-18 02:15:21 status half-configured libstreams0 0.7.2-1
2010-10-18 02:15:21 status installed libstreams0 0.7.2-1
2010-10-18 02:15:21 configure libstreamanalyzer0 0.7.2-1 0.7.2-1
2010-10-18 02:15:21 status unpacked libstreamanalyzer0 0.7.2-1
2010-10-18 02:15:21 status half-configured libstreamanalyzer0 0.7.2-1
2010-10-18 02:15:21 status installed libstreamanalyzer0 0.7.2-1
2010-10-18 02:15:21 configure libkio5 4:4.5.1-0ubuntu7 4:4.5.1-0ubuntu7
2010-10-18 02:15:21 status unpacked libkio5 4:4.5.1-0ubuntu7
2010-10-18 02:15:21 status half-configured libkio5 4:4.5.1-0ubuntu7
2010-10-18 02:15:21 status installed libkio5 4:4.5.1-0ubuntu7
2010-10-18 02:15:21 configure libkfile4 4:4.5.1-0ubuntu7 4:4.5.1-0ubuntu7
2010-10-18 02:15:21 status unpacked libkfile4 4:4.5.1-0ubuntu7
2010-10-18 02:15:21 status half-configured libkfile4 4:4.5.1-0ubuntu7
2010-10-18 02:15:21 status installed libkfile4 4:4.5.1-0ubuntu7
2010-10-18 02:15:21 configure libkjsapi4 4:4.5.1-0ubuntu7 4:4.5.1-0ubuntu7
2010-10-18 02:15:21 status unpacked libkjsapi4 4:4.5.1-0ubuntu7
2010-10-18 02:15:21 status half-configured libkjsapi4 4:4.5.1-0ubuntu7
2010-10-18 02:15:22 status installed libkjsapi4 4:4.5.1-0ubuntu7
2010-10-18 02:15:22 configure libkparts4 4:4.5.1-0ubuntu7 4:4.5.1-0ubuntu7
2010-10-18 02:15:22 status unpacked libkparts4 4:4.5.1-0ubuntu7
2010-10-18 02:15:22 status half-configured libkparts4 4:4.5.1-0ubuntu7
2010-10-18 02:15:22 status installed libkparts4 4:4.5.1-0ubuntu7
2010-10-18 02:15:22 configure libktexteditor4 4:4.5.1-0ubuntu7 4:4.5.1-0ubuntu7
2010-10-18 02:15:22 status unpacked libktexteditor4 4:4.5.1-0ubuntu7
2010-10-18 02:15:22 status half-configured libktexteditor4 4:4.5.1-0ubuntu7
2010-10-18 02:15:22 status installed libktexteditor4 4:4.5.1-0ubuntu7
2010-10-18 02:15:22 configure libphonon4 4:4.7.0really4.4.2-0ubuntu1 4:4.7.0really4.4.2-0ubuntu1
2010-10-18 02:15:22 status unpacked libphonon4 4:4.7.0really4.4.2-0ubuntu1
2010-10-18 02:15:22 status half-configured libphonon4 4:4.7.0really4.4.2-0ubuntu1
2010-10-18 02:15:26 status installed libphonon4 4:4.7.0really4.4.2-0ubuntu1
2010-10-18 02:15:26 configure libkhtml5 4:4.5.1-0ubuntu7 4:4.5.1-0ubuntu7
2010-10-18 02:15:26 status unpacked libkhtml5 4:4.5.1-0ubuntu7
2010-10-18 02:15:27 status half-configured libkhtml5 4:4.5.1-0ubuntu7
2010-10-18 02:15:27 status installed libkhtml5 4:4.5.1-0ubuntu7
2010-10-18 02:15:27 configure libkmediaplayer4 4:4.5.1-0ubuntu7 4:4.5.1-0ubuntu7
2010-10-18 02:15:27 status unpacked libkmediaplayer4 4:4.5.1-0ubuntu7
2010-10-18 02:15:27 status half-configured libkmediaplayer4 4:4.5.1-0ubuntu7
2010-10-18 02:15:27 status installed libkmediaplayer4 4:4.5.1-0ubuntu7
2010-10-18 02:15:28 configure libknewstuff3-4 4:4.5.1-0ubuntu7 4:4.5.1-0ubuntu7
2010-10-18 02:15:28 status unpacked libknewstuff3-4 4:4.5.1-0ubuntu7
2010-10-18 02:15:28 status half-configured libknewstuff3-4 4:4.5.1-0ubuntu7
2010-10-18 02:15:28 status installed libknewstuff3-4 4:4.5.1-0ubuntu7
2010-10-18 02:15:28 configure libknotifyconfig4 4:4.5.1-0ubuntu7 4:4.5.1-0ubuntu7
2010-10-18 02:15:28 status unpacked libknotifyconfig4 4:4.5.1-0ubuntu7
2010-10-18 02:15:28 status half-configured libknotifyconfig4 4:4.5.1-0ubuntu7
2010-10-18 02:15:28 status installed libknotifyconfig4 4:4.5.1-0ubuntu7
2010-10-18 02:15:28 configure libkutils4 4:4.5.1-0ubuntu7 4:4.5.1-0ubuntu7
2010-10-18 02:15:28 status unpacked libkutils4 4:4.5.1-0ubuntu7
2010-10-18 02:15:28 status half-configured libkutils4 4:4.5.1-0ubuntu7
2010-10-18 02:15:28 status installed libkutils4 4:4.5.1-0ubuntu7
2010-10-18 02:15:28 configure libnepomukquery4a 4:4.5.1-0ubuntu7 4:4.5.1-0ubuntu7
2010-10-18 02:15:28 status unpacked libnepomukquery4a 4:4.5.1-0ubuntu7
2010-10-18 02:15:29 status half-configured libnepomukquery4a 4:4.5.1-0ubuntu7
2010-10-18 02:15:29 status installed libnepomukquery4a 4:4.5.1-0ubuntu7
2010-10-18 02:15:29 configure libmodplug1 1:0.8.8.1-1ubuntu1 1:0.8.8.1-1ubuntu1
2010-10-18 02:15:29 status unpacked libmodplug1 1:0.8.8.1-1ubuntu1
2010-10-18 02:15:29 status half-configured libmodplug1 1:0.8.8.1-1ubuntu1
2010-10-18 02:15:29 status installed libmodplug1 1:0.8.8.1-1ubuntu1
2010-10-18 02:15:29 configure libmpcdec6 2:0.1~r459-1 2:0.1~r459-1
2010-10-18 02:15:29 status unpacked libmpcdec6 2:0.1~r459-1
2010-10-18 02:15:29 status half-configured libmpcdec6 2:0.1~r459-1
2010-10-18 02:15:29 status installed libmpcdec6 2:0.1~r459-1
2010-10-18 02:15:29 configure libxine1-bin 1.1.18.1-4ubuntu4 1.1.18.1-4ubuntu4
2010-10-18 02:15:29 status unpacked libxine1-bin 1.1.18.1-4ubuntu4
2010-10-18 02:15:30 status half-configured libxine1-bin 1.1.18.1-4ubuntu4
2010-10-18 02:15:30 status installed libxine1-bin 1.1.18.1-4ubuntu4
2010-10-18 02:15:30 configure libxine1-misc-plugins 1.1.18.1-4ubuntu4 1.1.18.1-4ubuntu4
2010-10-18 02:15:30 status unpacked libxine1-misc-plugins 1.1.18.1-4ubuntu4
2010-10-18 02:15:30 status half-configured libxine1-misc-plugins 1.1.18.1-4ubuntu4
2010-10-18 02:15:30 status installed libxine1-misc-plugins 1.1.18.1-4ubuntu4
2010-10-18 02:15:30 configure tsconf 1.0-7build1 1.0-7build1
2010-10-18 02:15:30 status unpacked tsconf 1.0-7build1
2010-10-18 02:15:30 status unpacked tsconf 1.0-7build1
2010-10-18 02:15:30 status half-configured tsconf 1.0-7build1
2010-10-18 02:15:30 status installed tsconf 1.0-7build1
2010-10-18 02:15:30 configure libts-0.0-0 1.0-7build1 1.0-7build1
2010-10-18 02:15:30 status unpacked libts-0.0-0 1.0-7build1
2010-10-18 02:15:30 status half-configured libts-0.0-0 1.0-7build1
2010-10-18 02:15:31 status installed libts-0.0-0 1.0-7build1
2010-10-18 02:15:31 configure libdirectfb-1.2-9 1.2.10.0-4ubuntu2 1.2.10.0-4ubuntu2
2010-10-18 02:15:31 status unpacked libdirectfb-1.2-9 1.2.10.0-4ubuntu2
2010-10-18 02:15:31 status half-configured libdirectfb-1.2-9 1.2.10.0-4ubuntu2
2010-10-18 02:15:31 status installed libdirectfb-1.2-9 1.2.10.0-4ubuntu2
2010-10-18 02:15:31 configure libxcb-shape0 1.6-1 1.6-1
2010-10-18 02:15:31 status unpacked libxcb-shape0 1.6-1
2010-10-18 02:15:31 status half-configured libxcb-shape0 1.6-1
2010-10-18 02:15:31 status installed libxcb-shape0 1.6-1
2010-10-18 02:15:31 configure libxcb-xv0 1.6-1 1.6-1
2010-10-18 02:15:31 status unpacked libxcb-xv0 1.6-1
2010-10-18 02:15:31 status half-configured libxcb-xv0 1.6-1
2010-10-18 02:15:31 status installed libxcb-xv0 1.6-1
2010-10-18 02:15:31 configure libxine1-x 1.1.18.1-4ubuntu4 1.1.18.1-4ubuntu4
2010-10-18 02:15:31 status unpacked libxine1-x 1.1.18.1-4ubuntu4
2010-10-18 02:15:31 status half-configured libxine1-x 1.1.18.1-4ubuntu4
2010-10-18 02:15:31 status installed libxine1-x 1.1.18.1-4ubuntu4
2010-10-18 02:15:32 configure libxine1-console 1.1.18.1-4ubuntu4 1.1.18.1-4ubuntu4
2010-10-18 02:15:32 status unpacked libxine1-console 1.1.18.1-4ubuntu4
2010-10-18 02:15:32 status half-configured libxine1-console 1.1.18.1-4ubuntu4
2010-10-18 02:15:32 status installed libxine1-console 1.1.18.1-4ubuntu4
2010-10-18 02:15:32 configure libxine1 1.1.18.1-4ubuntu4 1.1.18.1-4ubuntu4
2010-10-18 02:15:32 status unpacked libxine1 1.1.18.1-4ubuntu4
2010-10-18 02:15:32 status half-configured libxine1 1.1.18.1-4ubuntu4
2010-10-18 02:15:32 status installed libxine1 1.1.18.1-4ubuntu4
2010-10-18 02:15:32 configure phonon-backend-xine 4:4.7.0really4.4.2-0ubuntu1 4:4.7.0really4.4.2-0ubuntu1
2010-10-18 02:15:32 status unpacked phonon-backend-xine 4:4.7.0really4.4.2-0ubuntu1
2010-10-18 02:15:32 status half-configured phonon-backend-xine 4:4.7.0really4.4.2-0ubuntu1
2010-10-18 02:15:32 status installed phonon-backend-xine 4:4.7.0really4.4.2-0ubuntu1
2010-10-18 02:15:32 configure phonon 4:4.7.0really4.4.2-0ubuntu1 4:4.7.0really4.4.2-0ubuntu1
2010-10-18 02:15:32 status unpacked phonon 4:4.7.0really4.4.2-0ubuntu1
2010-10-18 02:15:32 status half-configured phonon 4:4.7.0really4.4.2-0ubuntu1
2010-10-18 02:15:33 status installed phonon 4:4.7.0really4.4.2-0ubuntu1
2010-10-18 02:15:33 configure libqtwebkit4 2.0.0-0ubuntu1 2.0.0-0ubuntu1
2010-10-18 02:15:33 status unpacked libqtwebkit4 2.0.0-0ubuntu1
2010-10-18 02:15:33 status half-configured libqtwebkit4 2.0.0-0ubuntu1
2010-10-18 02:15:33 status installed libqtwebkit4 2.0.0-0ubuntu1
2010-10-18 02:15:33 configure libkdewebkit5 4:4.5.1-0ubuntu7 4:4.5.1-0ubuntu7
2010-10-18 02:15:33 status unpacked libkdewebkit5 4:4.5.1-0ubuntu7
2010-10-18 02:15:33 status half-configured libkdewebkit5 4:4.5.1-0ubuntu7
2010-10-18 02:15:33 status installed libkdewebkit5 4:4.5.1-0ubuntu7
2010-10-18 02:15:33 configure libqca2 2.0.2-1ubuntu2 2.0.2-1ubuntu2
2010-10-18 02:15:33 status unpacked libqca2 2.0.2-1ubuntu2
2010-10-18 02:15:33 status half-configured libqca2 2.0.2-1ubuntu2
2010-10-18 02:15:33 status installed libqca2 2.0.2-1ubuntu2
2010-10-18 02:15:34 configure libqt4-opengl 4:4.7.0-0ubuntu4 4:4.7.0-0ubuntu4
2010-10-18 02:15:34 status unpacked libqt4-opengl 4:4.7.0-0ubuntu4
2010-10-18 02:15:34 status half-configured libqt4-opengl 4:4.7.0-0ubuntu4
2010-10-18 02:15:34 status installed libqt4-opengl 4:4.7.0-0ubuntu4
2010-10-18 02:15:34 configure libqt4-script 4:4.7.0-0ubuntu4 4:4.7.0-0ubuntu4
2010-10-18 02:15:34 status unpacked libqt4-script 4:4.7.0-0ubuntu4
2010-10-18 02:15:35 status half-configured libqt4-script 4:4.7.0-0ubuntu4
2010-10-18 02:15:35 status installed libqt4-script 4:4.7.0-0ubuntu4
2010-10-18 02:15:35 configure libthreadweaver4 4:4.5.1-0ubuntu7 4:4.5.1-0ubuntu7
2010-10-18 02:15:35 status unpacked libthreadweaver4 4:4.5.1-0ubuntu7
2010-10-18 02:15:35 status half-configured libthreadweaver4 4:4.5.1-0ubuntu7
2010-10-18 02:15:35 status installed libthreadweaver4 4:4.5.1-0ubuntu7
2010-10-18 02:15:35 configure libplasma3 4:4.5.1-0ubuntu7 4:4.5.1-0ubuntu7
2010-10-18 02:15:35 status unpacked libplasma3 4:4.5.1-0ubuntu7
2010-10-18 02:15:35 status half-configured libplasma3 4:4.5.1-0ubuntu7
2010-10-18 02:15:35 status installed libplasma3 4:4.5.1-0ubuntu7
2010-10-18 02:15:35 configure libssh-4 0.4.5-1 0.4.5-1
2010-10-18 02:15:35 status unpacked libssh-4 0.4.5-1
2010-10-18 02:15:35 status half-configured libssh-4 0.4.5-1
2010-10-18 02:15:35 status installed libssh-4 0.4.5-1
2010-10-18 02:15:35 configure kdebase-runtime-data 4:4.5.1-0ubuntu3 4:4.5.1-0ubuntu3
2010-10-18 02:15:35 status unpacked kdebase-runtime-data 4:4.5.1-0ubuntu3
2010-10-18 02:15:35 status unpacked kdebase-runtime-data 4:4.5.1-0ubuntu3
2010-10-18 02:15:35 status unpacked kdebase-runtime-data 4:4.5.1-0ubuntu3
2010-10-18 02:15:35 status half-configured kdebase-runtime-data 4:4.5.1-0ubuntu3
2010-10-18 02:15:36 status installed kdebase-runtime-data 4:4.5.1-0ubuntu3
2010-10-18 02:15:36 configure libkatepartinterfaces4 4:4.5.1-0ubuntu7 4:4.5.1-0ubuntu7
2010-10-18 02:15:36 status unpacked libkatepartinterfaces4 4:4.5.1-0ubuntu7
2010-10-18 02:15:36 status half-configured libkatepartinterfaces4 4:4.5.1-0ubuntu7
2010-10-18 02:15:36 status installed libkatepartinterfaces4 4:4.5.1-0ubuntu7
2010-10-18 02:15:36 configure libkjsembed4 4:4.5.1-0ubuntu7 4:4.5.1-0ubuntu7
2010-10-18 02:15:36 status unpacked libkjsembed4 4:4.5.1-0ubuntu7
2010-10-18 02:15:36 status half-configured libkjsembed4 4:4.5.1-0ubuntu7
2010-10-18 02:15:36 status installed libkjsembed4 4:4.5.1-0ubuntu7
2010-10-18 02:15:36 configure libkntlm4 4:4.5.1-0ubuntu7 4:4.5.1-0ubuntu7
2010-10-18 02:15:36 status unpacked libkntlm4 4:4.5.1-0ubuntu7
2010-10-18 02:15:36 status half-configured libkntlm4 4:4.5.1-0ubuntu7
2010-10-18 02:15:36 status installed libkntlm4 4:4.5.1-0ubuntu7
2010-10-18 02:15:36 configure libkrosscore4 4:4.5.1-0ubuntu7 4:4.5.1-0ubuntu7
2010-10-18 02:15:36 status unpacked libkrosscore4 4:4.5.1-0ubuntu7
2010-10-18 02:15:36 status half-configured libkrosscore4 4:4.5.1-0ubuntu7
2010-10-18 02:15:36 status installed libkrosscore4 4:4.5.1-0ubuntu7
2010-10-18 02:15:36 configure libkrossui4 4:4.5.1-0ubuntu7 4:4.5.1-0ubuntu7
2010-10-18 02:15:36 status unpacked libkrossui4 4:4.5.1-0ubuntu7
2010-10-18 02:15:36 status half-configured libkrossui4 4:4.5.1-0ubuntu7
2010-10-18 02:15:37 status installed libkrossui4 4:4.5.1-0ubuntu7
2010-10-18 02:15:37 configure libpolkit-qt-1-0 0.95.1-1ubuntu1 0.95.1-1ubuntu1
2010-10-18 02:15:37 status unpacked libpolkit-qt-1-0 0.95.1-1ubuntu1
2010-10-18 02:15:37 status half-configured libpolkit-qt-1-0 0.95.1-1ubuntu1
2010-10-18 02:15:37 status installed libpolkit-qt-1-0 0.95.1-1ubuntu1
2010-10-18 02:15:37 configure kdoctools 4:4.5.1-0ubuntu7 4:4.5.1-0ubuntu7
2010-10-18 02:15:37 status unpacked kdoctools 4:4.5.1-0ubuntu7
2010-10-18 02:15:37 status half-configured kdoctools 4:4.5.1-0ubuntu7
2010-10-18 02:15:37 status installed kdoctools 4:4.5.1-0ubuntu7
2010-10-18 02:15:37 configure kdelibs-bin 4:4.5.1-0ubuntu7 4:4.5.1-0ubuntu7
2010-10-18 02:15:37 status unpacked kdelibs-bin 4:4.5.1-0ubuntu7
2010-10-18 02:15:37 status half-configured kdelibs-bin 4:4.5.1-0ubuntu7
2010-10-18 02:15:37 status installed kdelibs-bin 4:4.5.1-0ubuntu7
2010-10-18 02:15:38 configure kdelibs5-plugins 4:4.5.1-0ubuntu7 4:4.5.1-0ubuntu7
2010-10-18 02:15:38 status unpacked kdelibs5-plugins 4:4.5.1-0ubuntu7
2010-10-18 02:15:38 status half-configured kdelibs5-plugins 4:4.5.1-0ubuntu7
2010-10-18 02:15:38 status installed kdelibs5-plugins 4:4.5.1-0ubuntu7
2010-10-18 02:15:38 configure oxygen-icon-theme 4:4.5.1-0ubuntu1 4:4.5.1-0ubuntu1
2010-10-18 02:15:38 status unpacked oxygen-icon-theme 4:4.5.1-0ubuntu1
2010-10-18 02:15:38 status half-configured oxygen-icon-theme 4:4.5.1-0ubuntu1
2010-10-18 02:15:38 status installed oxygen-icon-theme 4:4.5.1-0ubuntu1
2010-10-18 02:15:38 configure shared-desktop-ontologies 0.5-1 0.5-1
2010-10-18 02:15:38 status unpacked shared-desktop-ontologies 0.5-1
2010-10-18 02:15:38 status half-configured shared-desktop-ontologies 0.5-1
2010-10-18 02:15:39 status installed shared-desktop-ontologies 0.5-1
2010-10-18 02:15:39 configure plasma-scriptengine-javascript 4:4.5.1-0ubuntu3 4:4.5.1-0ubuntu3
2010-10-18 02:15:39 status unpacked plasma-scriptengine-javascript 4:4.5.1-0ubuntu3
2010-10-18 02:15:39 status half-configured plasma-scriptengine-javascript 4:4.5.1-0ubuntu3
2010-10-18 02:15:39 status installed plasma-scriptengine-javascript 4:4.5.1-0ubuntu3
2010-10-18 02:15:39 configure kdebase-runtime 4:4.5.1-0ubuntu3 4:4.5.1-0ubuntu3
2010-10-18 02:15:39 status unpacked kdebase-runtime 4:4.5.1-0ubuntu3
2010-10-18 02:15:39 status unpacked kdebase-runtime 4:4.5.1-0ubuntu3
2010-10-18 02:15:39 status half-configured kdebase-runtime 4:4.5.1-0ubuntu3
2010-10-18 02:15:39 status installed kdebase-runtime 4:4.5.1-0ubuntu3
2010-10-18 02:15:39 configure libqt4-designer 4:4.7.0-0ubuntu4 4:4.7.0-0ubuntu4
2010-10-18 02:15:39 status unpacked libqt4-designer 4:4.7.0-0ubuntu4
2010-10-18 02:15:39 status half-configured libqt4-designer 4:4.7.0-0ubuntu4
2010-10-18 02:15:39 status installed libqt4-designer 4:4.7.0-0ubuntu4
2010-10-18 02:15:39 configure libqt4-sql 4:4.7.0-0ubuntu4 4:4.7.0-0ubuntu4
2010-10-18 02:15:39 status unpacked libqt4-sql 4:4.7.0-0ubuntu4
2010-10-18 02:15:39 status half-configured libqt4-sql 4:4.7.0-0ubuntu4
2010-10-18 02:15:40 status installed libqt4-sql 4:4.7.0-0ubuntu4
2010-10-18 02:15:40 configure libqt4-qt3support 4:4.7.0-0ubuntu4 4:4.7.0-0ubuntu4
2010-10-18 02:15:40 status unpacked libqt4-qt3support 4:4.7.0-0ubuntu4
2010-10-18 02:15:40 status half-configured libqt4-qt3support 4:4.7.0-0ubuntu4
2010-10-18 02:15:40 status installed libqt4-qt3support 4:4.7.0-0ubuntu4
2010-10-18 02:15:40 configure libkde3support4 4:4.5.1-0ubuntu7 4:4.5.1-0ubuntu7
2010-10-18 02:15:40 status unpacked libkde3support4 4:4.5.1-0ubuntu7
2010-10-18 02:15:40 status half-configured libkde3support4 4:4.5.1-0ubuntu7
2010-10-18 02:15:41 status installed libkde3support4 4:4.5.1-0ubuntu7
2010-10-18 02:15:41 configure libkimproxy4 4:4.5.1-0ubuntu7 4:4.5.1-0ubuntu7
2010-10-18 02:15:41 status unpacked libkimproxy4 4:4.5.1-0ubuntu7
2010-10-18 02:15:41 status half-configured libkimproxy4 4:4.5.1-0ubuntu7
2010-10-18 02:15:41 status installed libkimproxy4 4:4.5.1-0ubuntu7
2010-10-18 02:15:41 configure libknewstuff2-4 4:4.5.1-0ubuntu7 4:4.5.1-0ubuntu7
2010-10-18 02:15:41 status unpacked libknewstuff2-4 4:4.5.1-0ubuntu7
2010-10-18 02:15:41 status half-configured libknewstuff2-4 4:4.5.1-0ubuntu7
2010-10-18 02:15:41 status installed libknewstuff2-4 4:4.5.1-0ubuntu7
2010-10-18 02:15:41 configure kdelibs5 4:4.5.1-0ubuntu7 4:4.5.1-0ubuntu7
2010-10-18 02:15:41 status unpacked kdelibs5 4:4.5.1-0ubuntu7
2010-10-18 02:15:41 status half-configured kdelibs5 4:4.5.1-0ubuntu7
2010-10-18 02:15:41 status installed kdelibs5 4:4.5.1-0ubuntu7
2010-10-18 02:15:41 configure filelight 1.9~rc3-2 1.9~rc3-2
2010-10-18 02:15:41 status unpacked filelight 1.9~rc3-2
2010-10-18 02:15:41 status half-configured filelight 1.9~rc3-2
2010-10-18 02:15:41 status installed filelight 1.9~rc3-2
2010-10-18 02:15:41 status triggers-pending menu 2.1.44ubuntu1
2010-10-18 02:15:41 status triggers-awaited menu 2.1.44ubuntu1
2010-10-18 02:15:41 configure libhal-storage1 0.5.14-0ubuntu6 0.5.14-0ubuntu6
2010-10-18 02:15:41 status unpacked libhal-storage1 0.5.14-0ubuntu6
2010-10-18 02:15:42 status half-configured libhal-storage1 0.5.14-0ubuntu6
2010-10-18 02:15:42 status installed libhal-storage1 0.5.14-0ubuntu6
2010-10-18 02:15:42 configure hal-info 20091130-1 20091130-1
2010-10-18 02:15:42 status unpacked hal-info 20091130-1
2010-10-18 02:15:42 status half-configured hal-info 20091130-1
2010-10-18 02:15:42 status installed hal-info 20091130-1
2010-10-18 02:15:43 configure hal 0.5.14-0ubuntu6 0.5.14-0ubuntu6
2010-10-18 02:15:43 status unpacked hal 0.5.14-0ubuntu6
2010-10-18 02:15:43 status unpacked hal 0.5.14-0ubuntu6
2010-10-18 02:15:43 status unpacked hal 0.5.14-0ubuntu6
2010-10-18 02:15:43 status half-configured hal 0.5.14-0ubuntu6
2010-10-18 02:15:44 status installed hal 0.5.14-0ubuntu6
2010-10-18 02:15:44 configure icoutils 0.29.1-0ubuntu1 0.29.1-0ubuntu1
2010-10-18 02:15:44 status unpacked icoutils 0.29.1-0ubuntu1
2010-10-18 02:15:44 status half-configured icoutils 0.29.1-0ubuntu1
2010-10-18 02:15:44 status installed icoutils 0.29.1-0ubuntu1
2010-10-18 02:15:44 configure libqapt1 1.0.3-0ubuntu2 1.0.3-0ubuntu2
2010-10-18 02:15:44 status unpacked libqapt1 1.0.3-0ubuntu2
2010-10-18 02:15:44 status half-configured libqapt1 1.0.3-0ubuntu2
2010-10-18 02:15:44 status installed libqapt1 1.0.3-0ubuntu2
2010-10-18 02:15:44 configure libqapt-runtime 1.0.3-0ubuntu2 1.0.3-0ubuntu2
2010-10-18 02:15:44 status unpacked libqapt-runtime 1.0.3-0ubuntu2
2010-10-18 02:15:44 status unpacked libqapt-runtime 1.0.3-0ubuntu2
2010-10-18 02:15:44 status half-configured libqapt-runtime 1.0.3-0ubuntu2
2010-10-18 02:15:45 status installed libqapt-runtime 1.0.3-0ubuntu2
2010-10-18 02:15:45 configure qapt-batch 1.0.3-0ubuntu2 1.0.3-0ubuntu2
2010-10-18 02:15:45 status unpacked qapt-batch 1.0.3-0ubuntu2
2010-10-18 02:15:45 status half-configured qapt-batch 1.0.3-0ubuntu2
2010-10-18 02:15:45 status installed qapt-batch 1.0.3-0ubuntu2
2010-10-18 02:15:45 configure kubuntu-debug-installer 10.10ubuntu4 10.10ubuntu4
2010-10-18 02:15:45 status unpacked kubuntu-debug-installer 10.10ubuntu4
2010-10-18 02:15:45 status half-configured kubuntu-debug-installer 10.10ubuntu4
2010-10-18 02:15:45 status installed kubuntu-debug-installer 10.10ubuntu4
2010-10-18 02:15:45 configure mysql-common 5.1.49-1ubuntu8 5.1.49-1ubuntu8
2010-10-18 02:15:45 status unpacked mysql-common 5.1.49-1ubuntu8
2010-10-18 02:15:45 status unpacked mysql-common 5.1.49-1ubuntu8
2010-10-18 02:15:46 status half-configured mysql-common 5.1.49-1ubuntu8
2010-10-18 02:15:46 status installed mysql-common 5.1.49-1ubuntu8
2010-10-18 02:15:46 configure libmysqlclient16 5.1.49-1ubuntu8 5.1.49-1ubuntu8
2010-10-18 02:15:46 status unpacked libmysqlclient16 5.1.49-1ubuntu8
2010-10-18 02:15:46 status half-configured libmysqlclient16 5.1.49-1ubuntu8
2010-10-18 02:15:46 status installed libmysqlclient16 5.1.49-1ubuntu8
2010-10-18 02:15:46 configure libqt4-sql-mysql 4:4.7.0-0ubuntu4 4:4.7.0-0ubuntu4
2010-10-18 02:15:46 status unpacked libqt4-sql-mysql 4:4.7.0-0ubuntu4
2010-10-18 02:15:47 status half-configured libqt4-sql-mysql 4:4.7.0-0ubuntu4
2010-10-18 02:15:47 status installed libqt4-sql-mysql 4:4.7.0-0ubuntu4
2010-10-18 02:15:47 configure libreadline5 5.2-7build1 5.2-7build1
2010-10-18 02:15:47 status unpacked libreadline5 5.2-7build1
2010-10-18 02:15:47 status half-configured libreadline5 5.2-7build1
2010-10-18 02:15:47 status installed libreadline5 5.2-7build1
2010-10-18 02:15:47 configure virtuoso-opensource-6.1-common 6.1.2+dfsg1-1ubuntu4 6.1.2+dfsg1-1ubuntu4
2010-10-18 02:15:47 status unpacked virtuoso-opensource-6.1-common 6.1.2+dfsg1-1ubuntu4
2010-10-18 02:15:47 status half-configured virtuoso-opensource-6.1-common 6.1.2+dfsg1-1ubuntu4
2010-10-18 02:15:47 status installed virtuoso-opensource-6.1-common 6.1.2+dfsg1-1ubuntu4
2010-10-18 02:15:47 configure smartdimmer 0.8b4-1ubuntu3 0.8b4-1ubuntu3
2010-10-18 02:15:47 status unpacked smartdimmer 0.8b4-1ubuntu3
2010-10-18 02:15:47 status half-configured smartdimmer 0.8b4-1ubuntu3
2010-10-18 02:15:47 status installed smartdimmer 0.8b4-1ubuntu3
2010-10-18 02:15:47 configure ttf-dejavu 2.31-1 2.31-1
2010-10-18 02:15:47 status unpacked ttf-dejavu 2.31-1
2010-10-18 02:15:47 status half-configured ttf-dejavu 2.31-1
2010-10-18 02:15:47 status installed ttf-dejavu 2.31-1
2010-10-18 02:15:47 configure virtuoso-opensource-6.1-bin 6.1.2+dfsg1-1ubuntu4 6.1.2+dfsg1-1ubuntu4
2010-10-18 02:15:47 status unpacked virtuoso-opensource-6.1-bin 6.1.2+dfsg1-1ubuntu4
2010-10-18 02:15:47 status half-configured virtuoso-opensource-6.1-bin 6.1.2+dfsg1-1ubuntu4
2010-10-18 02:15:47 status installed virtuoso-opensource-6.1-bin 6.1.2+dfsg1-1ubuntu4
2010-10-18 02:15:47 configure odbcinst 2.2.14p2-1ubuntu1 2.2.14p2-1ubuntu1
2010-10-18 02:15:47 status unpacked odbcinst 2.2.14p2-1ubuntu1
2010-10-18 02:15:48 status unpacked odbcinst 2.2.14p2-1ubuntu1
2010-10-18 02:15:48 status half-configured odbcinst 2.2.14p2-1ubuntu1
2010-10-18 02:15:48 status installed odbcinst 2.2.14p2-1ubuntu1
2010-10-18 02:15:48 configure odbcinst1debian2 2.2.14p2-1ubuntu1 2.2.14p2-1ubuntu1
2010-10-18 02:15:48 status unpacked odbcinst1debian2 2.2.14p2-1ubuntu1
2010-10-18 02:15:48 status half-configured odbcinst1debian2 2.2.14p2-1ubuntu1
2010-10-18 02:15:48 status installed odbcinst1debian2 2.2.14p2-1ubuntu1
2010-10-18 02:15:48 configure libvirtodbc0 6.1.2+dfsg1-1ubuntu4 6.1.2+dfsg1-1ubuntu4
2010-10-18 02:15:48 status unpacked libvirtodbc0 6.1.2+dfsg1-1ubuntu4
2010-10-18 02:15:48 status half-configured libvirtodbc0 6.1.2+dfsg1-1ubuntu4
2010-10-18 02:15:48 status installed libvirtodbc0 6.1.2+dfsg1-1ubuntu4
2010-10-18 02:15:49 configure virtuoso-minimal 6.1.2+dfsg1-1ubuntu4 6.1.2+dfsg1-1ubuntu4
2010-10-18 02:15:49 status unpacked virtuoso-minimal 6.1.2+dfsg1-1ubuntu4
2010-10-18 02:15:49 status half-configured virtuoso-minimal 6.1.2+dfsg1-1ubuntu4
2010-10-18 02:15:49 status installed virtuoso-minimal 6.1.2+dfsg1-1ubuntu4
2010-10-18 02:15:49 trigproc libc-bin 2.12.1-0ubuntu6 2.12.1-0ubuntu6
2010-10-18 02:15:49 status half-configured libc-bin 2.12.1-0ubuntu6
2010-10-18 02:15:49 status installed libc-bin 2.12.1-0ubuntu6
2010-10-18 02:15:49 trigproc menu 2.1.44ubuntu1 2.1.44ubuntu1
2010-10-18 02:15:49 status half-configured menu 2.1.44ubuntu1
2010-10-18 02:15:49 status installed menu 2.1.44ubuntu1
2010-10-18 08:41:09 startup archives unpack
2010-10-18 08:41:10 upgrade linux-image-2.6.35-22-generic 2.6.35-22.33 2.6.35-22.34
2010-10-18 08:41:10 status half-configured linux-image-2.6.35-22-generic 2.6.35-22.33
2010-10-18 08:41:11 status unpacked linux-image-2.6.35-22-generic 2.6.35-22.33
2010-10-18 08:41:11 status half-installed linux-image-2.6.35-22-generic 2.6.35-22.33
2010-10-18 08:41:19 status half-installed linux-image-2.6.35-22-generic 2.6.35-22.33
2010-10-18 08:41:19 status unpacked linux-image-2.6.35-22-generic 2.6.35-22.34
2010-10-18 08:41:19 status unpacked linux-image-2.6.35-22-generic 2.6.35-22.34
2010-10-18 08:41:19 upgrade libssl0.9.8 0.9.8o-1ubuntu4 0.9.8o-1ubuntu4.1
2010-10-18 08:41:19 status half-configured libssl0.9.8 0.9.8o-1ubuntu4
2010-10-18 08:41:19 status unpacked libssl0.9.8 0.9.8o-1ubuntu4
2010-10-18 08:41:19 status half-installed libssl0.9.8 0.9.8o-1ubuntu4
2010-10-18 08:41:20 status half-installed libssl0.9.8 0.9.8o-1ubuntu4
2010-10-18 08:41:20 status unpacked libssl0.9.8 0.9.8o-1ubuntu4.1
2010-10-18 08:41:20 status unpacked libssl0.9.8 0.9.8o-1ubuntu4.1
2010-10-18 08:41:21 startup packages configure
2010-10-18 08:41:21 configure libssl0.9.8 0.9.8o-1ubuntu4.1 0.9.8o-1ubuntu4.1
2010-10-18 08:41:21 status unpacked libssl0.9.8 0.9.8o-1ubuntu4.1
2010-10-18 08:41:21 status half-configured libssl0.9.8 0.9.8o-1ubuntu4.1
2010-10-18 08:41:22 status installed libssl0.9.8 0.9.8o-1ubuntu4.1
2010-10-18 08:41:22 status triggers-pending libc-bin 2.12.1-0ubuntu6
2010-10-18 08:41:22 trigproc libc-bin 2.12.1-0ubuntu6 2.12.1-0ubuntu6
2010-10-18 08:41:22 status half-configured libc-bin 2.12.1-0ubuntu6
2010-10-18 08:41:22 status installed libc-bin 2.12.1-0ubuntu6
2010-10-18 08:41:23 startup archives unpack
2010-10-18 08:41:23 upgrade libk5crypto3 1.8.1+dfsg-5 1.8.1+dfsg-5ubuntu0.1
2010-10-18 08:41:23 status half-configured libk5crypto3 1.8.1+dfsg-5
2010-10-18 08:41:23 status unpacked libk5crypto3 1.8.1+dfsg-5
2010-10-18 08:41:23 status half-installed libk5crypto3 1.8.1+dfsg-5
2010-10-18 08:41:23 status half-installed libk5crypto3 1.8.1+dfsg-5
2010-10-18 08:41:24 status unpacked libk5crypto3 1.8.1+dfsg-5ubuntu0.1
2010-10-18 08:41:24 status unpacked libk5crypto3 1.8.1+dfsg-5ubuntu0.1
2010-10-18 08:41:24 upgrade libgssapi-krb5-2 1.8.1+dfsg-5 1.8.1+dfsg-5ubuntu0.1
2010-10-18 08:41:24 status half-configured libgssapi-krb5-2 1.8.1+dfsg-5
2010-10-18 08:41:24 status unpacked libgssapi-krb5-2 1.8.1+dfsg-5
2010-10-18 08:41:24 status half-installed libgssapi-krb5-2 1.8.1+dfsg-5
2010-10-18 08:41:25 status half-installed libgssapi-krb5-2 1.8.1+dfsg-5
2010-10-18 08:41:25 status unpacked libgssapi-krb5-2 1.8.1+dfsg-5ubuntu0.1
2010-10-18 08:41:25 status unpacked libgssapi-krb5-2 1.8.1+dfsg-5ubuntu0.1
2010-10-18 08:41:26 upgrade libkrb5-3 1.8.1+dfsg-5 1.8.1+dfsg-5ubuntu0.1
2010-10-18 08:41:26 status half-configured libkrb5-3 1.8.1+dfsg-5
2010-10-18 08:41:26 status unpacked libkrb5-3 1.8.1+dfsg-5
2010-10-18 08:41:26 status half-installed libkrb5-3 1.8.1+dfsg-5
2010-10-18 08:41:26 status half-installed libkrb5-3 1.8.1+dfsg-5
2010-10-18 08:41:26 status unpacked libkrb5-3 1.8.1+dfsg-5ubuntu0.1
2010-10-18 08:41:26 status unpacked libkrb5-3 1.8.1+dfsg-5ubuntu0.1
2010-10-18 08:41:27 upgrade libkrb5support0 1.8.1+dfsg-5 1.8.1+dfsg-5ubuntu0.1
2010-10-18 08:41:27 status half-configured libkrb5support0 1.8.1+dfsg-5
2010-10-18 08:41:27 status unpacked libkrb5support0 1.8.1+dfsg-5
2010-10-18 08:41:27 status half-installed libkrb5support0 1.8.1+dfsg-5
2010-10-18 08:41:27 status half-installed libkrb5support0 1.8.1+dfsg-5
2010-10-18 08:41:27 status unpacked libkrb5support0 1.8.1+dfsg-5ubuntu0.1
2010-10-18 08:41:27 status unpacked libkrb5support0 1.8.1+dfsg-5ubuntu0.1
2010-10-18 08:41:27 upgrade libvte-common 1:0.26.0-0ubuntu1 1:0.26.0-0ubuntu2
2010-10-18 08:41:27 status half-configured libvte-common 1:0.26.0-0ubuntu1
2010-10-18 08:41:27 status unpacked libvte-common 1:0.26.0-0ubuntu1
2010-10-18 08:41:27 status half-installed libvte-common 1:0.26.0-0ubuntu1
2010-10-18 08:41:28 status half-installed libvte-common 1:0.26.0-0ubuntu1
2010-10-18 08:41:28 status unpacked libvte-common 1:0.26.0-0ubuntu2
2010-10-18 08:41:28 status unpacked libvte-common 1:0.26.0-0ubuntu2
2010-10-18 08:41:28 upgrade libvte9 1:0.26.0-0ubuntu1 1:0.26.0-0ubuntu2
2010-10-18 08:41:28 status half-configured libvte9 1:0.26.0-0ubuntu1
2010-10-18 08:41:29 status unpacked libvte9 1:0.26.0-0ubuntu1
2010-10-18 08:41:29 status half-installed libvte9 1:0.26.0-0ubuntu1
2010-10-18 08:41:29 status half-installed libvte9 1:0.26.0-0ubuntu1
2010-10-18 08:41:30 status unpacked libvte9 1:0.26.0-0ubuntu2
2010-10-18 08:41:30 status unpacked libvte9 1:0.26.0-0ubuntu2
2010-10-18 08:41:30 upgrade python-vte 1:0.26.0-0ubuntu1 1:0.26.0-0ubuntu2
2010-10-18 08:41:30 status half-configured python-vte 1:0.26.0-0ubuntu1
2010-10-18 08:41:31 status triggers-pending python-support 1.0.9ubuntu1
2010-10-18 08:41:31 status unpacked python-vte 1:0.26.0-0ubuntu1
2010-10-18 08:41:31 status half-installed python-vte 1:0.26.0-0ubuntu1
2010-10-18 08:41:31 status half-installed python-vte 1:0.26.0-0ubuntu1
2010-10-18 08:41:32 status unpacked python-vte 1:0.26.0-0ubuntu2
2010-10-18 08:41:32 status unpacked python-vte 1:0.26.0-0ubuntu2
2010-10-18 08:41:32 upgrade update-manager 1:0.142.19 1:0.142.20
2010-10-18 08:41:32 status half-configured update-manager 1:0.142.19
2010-10-18 08:41:32 status unpacked update-manager 1:0.142.19
2010-10-18 08:41:32 status half-installed update-manager 1:0.142.19
2010-10-18 08:41:32 status triggers-pending hicolor-icon-theme 0.11-1
2010-10-18 08:41:32 status half-installed update-manager 1:0.142.19
2010-10-18 08:41:32 status triggers-pending gconf2 2.31.91-0ubuntu3
2010-10-18 08:41:32 status half-installed update-manager 1:0.142.19
2010-10-18 08:41:32 status triggers-pending desktop-file-utils 0.16-0ubuntu4
2010-10-18 08:41:32 status half-installed update-manager 1:0.142.19
2010-10-18 08:41:33 status triggers-pending python-gmenu 2.30.4-0ubuntu1
2010-10-18 08:41:33 status half-installed update-manager 1:0.142.19
2010-10-18 08:41:33 status triggers-pending man-db 2.5.7-4
2010-10-18 08:41:33 status half-installed update-manager 1:0.142.19
2010-10-18 08:41:33 status half-installed update-manager 1:0.142.19
2010-10-18 08:41:34 status unpacked update-manager 1:0.142.20
2010-10-18 08:41:34 status unpacked update-manager 1:0.142.20
2010-10-18 08:41:34 upgrade update-manager-core 1:0.142.19 1:0.142.20
2010-10-18 08:41:34 status half-configured update-manager-core 1:0.142.19
2010-10-18 08:41:34 status unpacked update-manager-core 1:0.142.19
2010-10-18 08:41:34 status half-installed update-manager-core 1:0.142.19
2010-10-18 08:41:35 status half-installed update-manager-core 1:0.142.19
2010-10-18 08:41:35 status unpacked update-manager-core 1:0.142.20
2010-10-18 08:41:35 status unpacked update-manager-core 1:0.142.20
2010-10-18 08:41:36 upgrade linux-headers-2.6.35-22 2.6.35-22.33 2.6.35-22.34
2010-10-18 08:41:36 status half-configured linux-headers-2.6.35-22 2.6.35-22.33
2010-10-18 08:41:36 status unpacked linux-headers-2.6.35-22 2.6.35-22.33
2010-10-18 08:41:37 status half-installed linux-headers-2.6.35-22 2.6.35-22.33
2010-10-18 08:41:40 status half-installed linux-headers-2.6.35-22 2.6.35-22.33
2010-10-18 08:41:40 status unpacked linux-headers-2.6.35-22 2.6.35-22.34
2010-10-18 08:41:40 status unpacked linux-headers-2.6.35-22 2.6.35-22.34
2010-10-18 08:41:40 upgrade linux-headers-2.6.35-22-generic 2.6.35-22.33 2.6.35-22.34
2010-10-18 08:41:40 status half-configured linux-headers-2.6.35-22-generic 2.6.35-22.33
2010-10-18 08:41:40 status unpacked linux-headers-2.6.35-22-generic 2.6.35-22.33
2010-10-18 08:41:40 status half-installed linux-headers-2.6.35-22-generic 2.6.35-22.33
2010-10-18 08:41:43 status half-installed linux-headers-2.6.35-22-generic 2.6.35-22.33
2010-10-18 08:41:43 status unpacked linux-headers-2.6.35-22-generic 2.6.35-22.34
2010-10-18 08:41:43 status unpacked linux-headers-2.6.35-22-generic 2.6.35-22.34
2010-10-18 08:41:43 upgrade linux-libc-dev 2.6.35-1022.33 2.6.35-1022.34
2010-10-18 08:41:43 status half-configured linux-libc-dev 2.6.35-1022.33
2010-10-18 08:41:43 status unpacked linux-libc-dev 2.6.35-1022.33
2010-10-18 08:41:43 status half-installed linux-libc-dev 2.6.35-1022.33
2010-10-18 08:41:44 status half-installed linux-libc-dev 2.6.35-1022.33
2010-10-18 08:41:44 status unpacked linux-libc-dev 2.6.35-1022.34
2010-10-18 08:41:44 status unpacked linux-libc-dev 2.6.35-1022.34
2010-10-18 08:41:45 upgrade openssl 0.9.8o-1ubuntu4 0.9.8o-1ubuntu4.1
2010-10-18 08:41:45 status half-configured openssl 0.9.8o-1ubuntu4
2010-10-18 08:41:45 status unpacked openssl 0.9.8o-1ubuntu4
2010-10-18 08:41:45 status half-installed openssl 0.9.8o-1ubuntu4
2010-10-18 08:41:45 status half-installed openssl 0.9.8o-1ubuntu4
2010-10-18 08:41:45 status half-installed openssl 0.9.8o-1ubuntu4
2010-10-18 08:41:45 status unpacked openssl 0.9.8o-1ubuntu4.1
2010-10-18 08:41:46 status unpacked openssl 0.9.8o-1ubuntu4.1
2010-10-18 08:41:46 trigproc python-support 1.0.9ubuntu1 1.0.9ubuntu1
2010-10-18 08:41:46 status half-configured python-support 1.0.9ubuntu1
2010-10-18 08:41:46 status installed python-support 1.0.9ubuntu1
2010-10-18 08:41:46 trigproc hicolor-icon-theme 0.11-1 0.11-1
2010-10-18 08:41:46 status half-configured hicolor-icon-theme 0.11-1
2010-10-18 08:41:48 status installed hicolor-icon-theme 0.11-1
2010-10-18 08:41:48 trigproc gconf2 2.31.91-0ubuntu3 2.31.91-0ubuntu3
2010-10-18 08:41:48 status half-configured gconf2 2.31.91-0ubuntu3
2010-10-18 08:41:52 status installed gconf2 2.31.91-0ubuntu3
2010-10-18 08:41:52 trigproc desktop-file-utils 0.16-0ubuntu4 0.16-0ubuntu4
2010-10-18 08:41:52 status half-configured desktop-file-utils 0.16-0ubuntu4
2010-10-18 08:41:52 status installed desktop-file-utils 0.16-0ubuntu4
2010-10-18 08:41:52 trigproc python-gmenu 2.30.4-0ubuntu1 2.30.4-0ubuntu1
2010-10-18 08:41:52 status half-configured python-gmenu 2.30.4-0ubuntu1
2010-10-18 08:41:53 status installed python-gmenu 2.30.4-0ubuntu1
2010-10-18 08:41:53 status triggers-pending python-support 1.0.9ubuntu1
2010-10-18 08:41:53 trigproc man-db 2.5.7-4 2.5.7-4
2010-10-18 08:41:53 status half-configured man-db 2.5.7-4
2010-10-18 08:41:54 status installed man-db 2.5.7-4
2010-10-18 08:41:54 trigproc python-support 1.0.9ubuntu1 1.0.9ubuntu1
2010-10-18 08:41:54 status half-configured python-support 1.0.9ubuntu1
2010-10-18 08:41:54 status installed python-support 1.0.9ubuntu1
2010-10-18 08:41:55 startup packages configure
2010-10-18 08:41:55 configure linux-image-2.6.35-22-generic 2.6.35-22.34 2.6.35-22.34
2010-10-18 08:41:55 status unpacked linux-image-2.6.35-22-generic 2.6.35-22.34
2010-10-18 08:41:55 status half-configured linux-image-2.6.35-22-generic 2.6.35-22.34
2010-10-18 08:42:09 status installed linux-image-2.6.35-22-generic 2.6.35-22.34
2010-10-18 08:42:09 configure libkrb5support0 1.8.1+dfsg-5ubuntu0.1 1.8.1+dfsg-5ubuntu0.1
2010-10-18 08:42:09 status unpacked libkrb5support0 1.8.1+dfsg-5ubuntu0.1
2010-10-18 08:42:09 status half-configured libkrb5support0 1.8.1+dfsg-5ubuntu0.1
2010-10-18 08:42:09 status installed libkrb5support0 1.8.1+dfsg-5ubuntu0.1
2010-10-18 08:42:09 status triggers-pending libc-bin 2.12.1-0ubuntu6
2010-10-18 08:42:09 configure libk5crypto3 1.8.1+dfsg-5ubuntu0.1 1.8.1+dfsg-5ubuntu0.1
2010-10-18 08:42:09 status unpacked libk5crypto3 1.8.1+dfsg-5ubuntu0.1
2010-10-18 08:42:09 status half-configured libk5crypto3 1.8.1+dfsg-5ubuntu0.1
2010-10-18 08:42:09 status installed libk5crypto3 1.8.1+dfsg-5ubuntu0.1
2010-10-18 08:42:09 configure libkrb5-3 1.8.1+dfsg-5ubuntu0.1 1.8.1+dfsg-5ubuntu0.1
2010-10-18 08:42:09 status unpacked libkrb5-3 1.8.1+dfsg-5ubuntu0.1
2010-10-18 08:42:09 status half-configured libkrb5-3 1.8.1+dfsg-5ubuntu0.1
2010-10-18 08:42:09 status installed libkrb5-3 1.8.1+dfsg-5ubuntu0.1
2010-10-18 08:42:10 configure libgssapi-krb5-2 1.8.1+dfsg-5ubuntu0.1 1.8.1+dfsg-5ubuntu0.1
2010-10-18 08:42:10 status unpacked libgssapi-krb5-2 1.8.1+dfsg-5ubuntu0.1
2010-10-18 08:42:10 status half-configured libgssapi-krb5-2 1.8.1+dfsg-5ubuntu0.1
2010-10-18 08:42:10 status installed libgssapi-krb5-2 1.8.1+dfsg-5ubuntu0.1
2010-10-18 08:42:10 configure libvte-common 1:0.26.0-0ubuntu2 1:0.26.0-0ubuntu2
2010-10-18 08:42:10 status unpacked libvte-common 1:0.26.0-0ubuntu2
2010-10-18 08:42:10 status half-configured libvte-common 1:0.26.0-0ubuntu2
2010-10-18 08:42:10 status installed libvte-common 1:0.26.0-0ubuntu2
2010-10-18 08:42:10 configure libvte9 1:0.26.0-0ubuntu2 1:0.26.0-0ubuntu2
2010-10-18 08:42:10 status unpacked libvte9 1:0.26.0-0ubuntu2
2010-10-18 08:42:10 status half-configured libvte9 1:0.26.0-0ubuntu2
2010-10-18 08:42:10 status installed libvte9 1:0.26.0-0ubuntu2
2010-10-18 08:42:10 configure python-vte 1:0.26.0-0ubuntu2 1:0.26.0-0ubuntu2
2010-10-18 08:42:10 status unpacked python-vte 1:0.26.0-0ubuntu2
2010-10-18 08:42:10 status half-configured python-vte 1:0.26.0-0ubuntu2
2010-10-18 08:42:10 status installed python-vte 1:0.26.0-0ubuntu2
2010-10-18 08:42:10 status triggers-pending python-support 1.0.9ubuntu1
2010-10-18 08:42:11 configure update-manager-core 1:0.142.20 1:0.142.20
2010-10-18 08:42:11 status unpacked update-manager-core 1:0.142.20
2010-10-18 08:42:13 status unpacked update-manager-core 1:0.142.20
2010-10-18 08:42:14 status unpacked update-manager-core 1:0.142.20
2010-10-18 08:42:14 status unpacked update-manager-core 1:0.142.20
2010-10-18 08:42:14 status half-configured update-manager-core 1:0.142.20
2010-10-18 08:42:14 status installed update-manager-core 1:0.142.20
2010-10-18 08:42:14 status triggers-pending python-central 0.6.15ubuntu2
2010-10-18 08:42:14 status triggers-awaited update-manager-core 1:0.142.20
2010-10-18 08:42:14 configure linux-headers-2.6.35-22 2.6.35-22.34 2.6.35-22.34
2010-10-18 08:42:14 status unpacked linux-headers-2.6.35-22 2.6.35-22.34
2010-10-18 08:42:14 status half-configured linux-headers-2.6.35-22 2.6.35-22.34
2010-10-18 08:42:14 status installed linux-headers-2.6.35-22 2.6.35-22.34
2010-10-18 08:42:14 configure linux-headers-2.6.35-22-generic 2.6.35-22.34 2.6.35-22.34
2010-10-18 08:42:14 status unpacked linux-headers-2.6.35-22-generic 2.6.35-22.34
2010-10-18 08:42:15 status half-configured linux-headers-2.6.35-22-generic 2.6.35-22.34
2010-10-18 08:42:15 status installed linux-headers-2.6.35-22-generic 2.6.35-22.34
2010-10-18 08:42:15 configure linux-libc-dev 2.6.35-1022.34 2.6.35-1022.34
2010-10-18 08:42:15 status unpacked linux-libc-dev 2.6.35-1022.34
2010-10-18 08:42:15 status half-configured linux-libc-dev 2.6.35-1022.34
2010-10-18 08:42:15 status installed linux-libc-dev 2.6.35-1022.34
2010-10-18 08:42:15 configure openssl 0.9.8o-1ubuntu4.1 0.9.8o-1ubuntu4.1
2010-10-18 08:42:15 status unpacked openssl 0.9.8o-1ubuntu4.1
2010-10-18 08:42:15 status unpacked openssl 0.9.8o-1ubuntu4.1
2010-10-18 08:42:16 status half-configured openssl 0.9.8o-1ubuntu4.1
2010-10-18 08:42:16 status installed openssl 0.9.8o-1ubuntu4.1
2010-10-18 08:42:16 trigproc python-central 0.6.15ubuntu2 0.6.15ubuntu2
2010-10-18 08:42:16 status half-configured python-central 0.6.15ubuntu2
2010-10-18 08:42:16 status installed update-manager-core 1:0.142.20
2010-10-18 08:42:16 status installed python-central 0.6.15ubuntu2
2010-10-18 08:42:16 configure update-manager 1:0.142.20 1:0.142.20
2010-10-18 08:42:16 status unpacked update-manager 1:0.142.20
2010-10-18 08:42:16 status half-configured update-manager 1:0.142.20
2010-10-18 08:42:17 status installed update-manager 1:0.142.20
2010-10-18 08:42:17 status triggers-pending python-central 0.6.15ubuntu2
2010-10-18 08:42:17 status triggers-awaited update-manager 1:0.142.20
2010-10-18 08:42:17 trigproc libc-bin 2.12.1-0ubuntu6 2.12.1-0ubuntu6
2010-10-18 08:42:17 status half-configured libc-bin 2.12.1-0ubuntu6
2010-10-18 08:42:17 status installed libc-bin 2.12.1-0ubuntu6
2010-10-18 08:42:17 trigproc python-support 1.0.9ubuntu1 1.0.9ubuntu1
2010-10-18 08:42:17 status half-configured python-support 1.0.9ubuntu1
2010-10-18 08:42:17 status installed python-support 1.0.9ubuntu1
2010-10-18 08:42:18 trigproc python-central 0.6.15ubuntu2 0.6.15ubuntu2
2010-10-18 08:42:18 status half-configured python-central 0.6.15ubuntu2
2010-10-18 08:42:18 status installed update-manager 1:0.142.20
2010-10-18 08:42:18 status installed python-central 0.6.15ubuntu2
2010-10-18 08:42:43 startup archives unpack
2010-10-18 08:42:44 install python-compizconfig <none> 0.8.4-2ubuntu2
2010-10-18 08:42:44 status half-installed python-compizconfig 0.8.4-2ubuntu2
2010-10-18 08:42:44 status unpacked python-compizconfig 0.8.4-2ubuntu2
2010-10-18 08:42:44 status unpacked python-compizconfig 0.8.4-2ubuntu2
2010-10-18 08:42:45 install compizconfig-settings-manager <none> 0.8.2-0ubuntu1
2010-10-18 08:42:45 status half-installed compizconfig-settings-manager 0.8.2-0ubuntu1
2010-10-18 08:42:45 status triggers-pending desktop-file-utils 0.16-0ubuntu4
2010-10-18 08:42:45 status half-installed compizconfig-settings-manager 0.8.2-0ubuntu1
2010-10-18 08:42:45 status triggers-pending python-gmenu 2.30.4-0ubuntu1
2010-10-18 08:42:45 status half-installed compizconfig-settings-manager 0.8.2-0ubuntu1
2010-10-18 08:42:45 status triggers-pending hicolor-icon-theme 0.11-1
2010-10-18 08:42:45 status half-installed compizconfig-settings-manager 0.8.2-0ubuntu1
2010-10-18 08:42:46 status unpacked compizconfig-settings-manager 0.8.2-0ubuntu1
2010-10-18 08:42:46 status unpacked compizconfig-settings-manager 0.8.2-0ubuntu1
2010-10-18 08:42:46 trigproc desktop-file-utils 0.16-0ubuntu4 0.16-0ubuntu4
2010-10-18 08:42:46 status half-configured desktop-file-utils 0.16-0ubuntu4
2010-10-18 08:42:46 status installed desktop-file-utils 0.16-0ubuntu4
2010-10-18 08:42:46 trigproc python-gmenu 2.30.4-0ubuntu1 2.30.4-0ubuntu1
2010-10-18 08:42:46 status half-configured python-gmenu 2.30.4-0ubuntu1
2010-10-18 08:42:46 status installed python-gmenu 2.30.4-0ubuntu1
2010-10-18 08:42:46 status triggers-pending python-support 1.0.9ubuntu1
2010-10-18 08:42:46 trigproc hicolor-icon-theme 0.11-1 0.11-1
2010-10-18 08:42:46 status half-configured hicolor-icon-theme 0.11-1
2010-10-18 08:42:47 status installed hicolor-icon-theme 0.11-1
2010-10-18 08:42:47 trigproc python-support 1.0.9ubuntu1 1.0.9ubuntu1
2010-10-18 08:42:47 status half-configured python-support 1.0.9ubuntu1
2010-10-18 08:42:47 status installed python-support 1.0.9ubuntu1
2010-10-18 08:42:48 startup packages configure
2010-10-18 08:42:48 configure python-compizconfig 0.8.4-2ubuntu2 0.8.4-2ubuntu2
2010-10-18 08:42:48 status unpacked python-compizconfig 0.8.4-2ubuntu2
2010-10-18 08:42:48 status half-configured python-compizconfig 0.8.4-2ubuntu2
2010-10-18 08:42:48 status installed python-compizconfig 0.8.4-2ubuntu2
2010-10-18 08:42:50 status triggers-pending python-support 1.0.9ubuntu1
2010-10-18 08:42:56 configure compizconfig-settings-manager 0.8.2-0ubuntu1 0.8.2-0ubuntu1
2010-10-18 08:42:56 status unpacked compizconfig-settings-manager 0.8.2-0ubuntu1
2010-10-18 08:42:56 status half-configured compizconfig-settings-manager 0.8.2-0ubuntu1
2010-10-18 08:42:57 status installed compizconfig-settings-manager 0.8.2-0ubuntu1
2010-10-18 08:42:57 status triggers-pending python-central 0.6.15ubuntu2
2010-10-18 08:42:57 status triggers-awaited compizconfig-settings-manager 0.8.2-0ubuntu1
2010-10-18 08:42:57 trigproc python-support 1.0.9ubuntu1 1.0.9ubuntu1
2010-10-18 08:42:57 status half-configured python-support 1.0.9ubuntu1
2010-10-18 08:42:57 status installed python-support 1.0.9ubuntu1
2010-10-18 08:42:57 trigproc python-central 0.6.15ubuntu2 0.6.15ubuntu2
2010-10-18 08:42:57 status half-configured python-central 0.6.15ubuntu2
2010-10-18 08:42:57 status installed compizconfig-settings-manager 0.8.2-0ubuntu1
2010-10-18 08:42:57 status installed python-central 0.6.15ubuntu2
2010-10-18 08:44:46 startup archives install
2010-10-18 08:44:46 install ubuntu-tweak <none> 0.5.7-1~lucid1
2010-10-18 08:44:46 status half-installed ubuntu-tweak 0.5.7-1~lucid1
2010-10-18 08:44:46 status triggers-pending gconf2 2.31.91-0ubuntu3
2010-10-18 08:44:46 status half-installed ubuntu-tweak 0.5.7-1~lucid1
2010-10-18 08:44:46 status triggers-pending hicolor-icon-theme 0.11-1
2010-10-18 08:44:46 status half-installed ubuntu-tweak 0.5.7-1~lucid1
2010-10-18 08:44:46 status triggers-pending desktop-file-utils 0.16-0ubuntu4
2010-10-18 08:44:47 status half-installed ubuntu-tweak 0.5.7-1~lucid1
2010-10-18 08:44:47 status triggers-pending python-gmenu 2.30.4-0ubuntu1
2010-10-18 08:44:47 status half-installed ubuntu-tweak 0.5.7-1~lucid1
2010-10-18 08:44:47 status unpacked ubuntu-tweak 0.5.7-1~lucid1
2010-10-18 08:44:48 status unpacked ubuntu-tweak 0.5.7-1~lucid1
2010-10-18 08:44:48 configure ubuntu-tweak 0.5.7-1~lucid1 0.5.7-1~lucid1
2010-10-18 08:44:48 status unpacked ubuntu-tweak 0.5.7-1~lucid1
2010-10-18 08:44:48 status unpacked ubuntu-tweak 0.5.7-1~lucid1
2010-10-18 08:44:48 status half-configured ubuntu-tweak 0.5.7-1~lucid1
2010-10-18 08:44:48 status triggers-awaited ubuntu-tweak 0.5.7-1~lucid1
2010-10-18 08:44:48 status triggers-pending python-central 0.6.15ubuntu2
2010-10-18 08:44:48 status triggers-awaited ubuntu-tweak 0.5.7-1~lucid1
2010-10-18 08:44:48 trigproc gconf2 2.31.91-0ubuntu3 2.31.91-0ubuntu3
2010-10-18 08:44:48 status half-configured gconf2 2.31.91-0ubuntu3
2010-10-18 08:44:52 status installed gconf2 2.31.91-0ubuntu3
2010-10-18 08:44:52 trigproc hicolor-icon-theme 0.11-1 0.11-1
2010-10-18 08:44:52 status half-configured hicolor-icon-theme 0.11-1
2010-10-18 08:44:52 status installed hicolor-icon-theme 0.11-1
2010-10-18 08:44:53 trigproc desktop-file-utils 0.16-0ubuntu4 0.16-0ubuntu4
2010-10-18 08:44:53 status half-configured desktop-file-utils 0.16-0ubuntu4
2010-10-18 08:44:53 status installed desktop-file-utils 0.16-0ubuntu4
2010-10-18 08:44:53 trigproc python-gmenu 2.30.4-0ubuntu1 2.30.4-0ubuntu1
2010-10-18 08:44:53 status half-configured python-gmenu 2.30.4-0ubuntu1
2010-10-18 08:44:53 status installed python-gmenu 2.30.4-0ubuntu1
2010-10-18 08:44:53 status triggers-pending python-support 1.0.9ubuntu1
2010-10-18 08:44:53 trigproc python-central 0.6.15ubuntu2 0.6.15ubuntu2
2010-10-18 08:44:53 status half-configured python-central 0.6.15ubuntu2
2010-10-18 08:44:53 status installed ubuntu-tweak 0.5.7-1~lucid1
2010-10-18 08:44:53 status installed python-central 0.6.15ubuntu2
2010-10-18 08:44:53 trigproc python-support 1.0.9ubuntu1 1.0.9ubuntu1
2010-10-18 08:44:53 status half-configured python-support 1.0.9ubuntu1
2010-10-18 08:44:54 status installed python-support 1.0.9ubuntu1
2010-10-18 09:28:32 startup archives unpack
2010-10-18 09:28:33 install human-icon-theme <none> 0.36
2010-10-18 09:28:33 status half-installed human-icon-theme 0.36
2010-10-18 09:28:34 status unpacked human-icon-theme 0.36
2010-10-18 09:28:34 status unpacked human-icon-theme 0.36
2010-10-18 09:28:34 install breathe-icon-theme <none> 0.51.2
2010-10-18 09:28:34 status half-installed breathe-icon-theme 0.51.2
2010-10-18 09:28:36 status unpacked breathe-icon-theme 0.51.2
2010-10-18 09:28:36 status unpacked breathe-icon-theme 0.51.2
2010-10-18 09:28:36 install community-themes <none> 0.23.1
2010-10-18 09:28:36 status half-installed community-themes 0.23.1
2010-10-18 09:28:37 status unpacked community-themes 0.23.1
2010-10-18 09:28:37 status unpacked community-themes 0.23.1
2010-10-18 09:28:37 startup packages configure
2010-10-18 09:28:37 configure human-icon-theme 0.36 0.36
2010-10-18 09:28:37 status unpacked human-icon-theme 0.36
2010-10-18 09:28:37 status half-configured human-icon-theme 0.36
2010-10-18 09:28:38 status installed human-icon-theme 0.36
2010-10-18 09:28:38 configure breathe-icon-theme 0.51.2 0.51.2
2010-10-18 09:28:38 status unpacked breathe-icon-theme 0.51.2
2010-10-18 09:28:38 status half-configured breathe-icon-theme 0.51.2
2010-10-18 09:28:38 status installed breathe-icon-theme 0.51.2
2010-10-18 09:28:38 configure community-themes 0.23.1 0.23.1
2010-10-18 09:28:38 status unpacked community-themes 0.23.1
2010-10-18 09:28:38 status half-configured community-themes 0.23.1
2010-10-18 09:28:38 status installed community-themes 0.23.1
2010-10-18 09:28:44 startup archives install
2010-10-18 09:28:44 install compiz-switch <none> 0.4.3~ubuntu-1
2010-10-18 09:28:44 status half-installed compiz-switch 0.4.3~ubuntu-1
2010-10-18 09:28:44 status triggers-pending desktop-file-utils 0.16-0ubuntu4
2010-10-18 09:28:44 status half-installed compiz-switch 0.4.3~ubuntu-1
2010-10-18 09:28:44 status triggers-pending python-gmenu 2.30.4-0ubuntu1
2010-10-18 09:28:44 status half-installed compiz-switch 0.4.3~ubuntu-1
2010-10-18 09:28:45 status unpacked compiz-switch 0.4.3~ubuntu-1
2010-10-18 09:28:45 status unpacked compiz-switch 0.4.3~ubuntu-1
2010-10-18 09:28:45 configure compiz-switch 0.4.3~ubuntu-1 0.4.3~ubuntu-1
2010-10-18 09:28:45 status unpacked compiz-switch 0.4.3~ubuntu-1
2010-10-18 09:28:45 status half-configured compiz-switch 0.4.3~ubuntu-1
2010-10-18 09:28:45 status triggers-awaited compiz-switch 0.4.3~ubuntu-1
2010-10-18 09:28:45 trigproc desktop-file-utils 0.16-0ubuntu4 0.16-0ubuntu4
2010-10-18 09:28:45 status half-configured desktop-file-utils 0.16-0ubuntu4
2010-10-18 09:28:45 status installed desktop-file-utils 0.16-0ubuntu4
2010-10-18 09:28:45 trigproc python-gmenu 2.30.4-0ubuntu1 2.30.4-0ubuntu1
2010-10-18 09:28:45 status half-configured python-gmenu 2.30.4-0ubuntu1
2010-10-18 09:28:45 status installed compiz-switch 0.4.3~ubuntu-1
2010-10-18 09:28:46 status installed python-gmenu 2.30.4-0ubuntu1
2010-10-18 09:28:46 status triggers-pending python-support 1.0.9ubuntu1
2010-10-18 09:28:46 trigproc python-support 1.0.9ubuntu1 1.0.9ubuntu1
2010-10-18 09:28:46 status half-configured python-support 1.0.9ubuntu1
2010-10-18 09:28:47 status installed python-support 1.0.9ubuntu1
2010-10-18 11:24:15 startup archives unpack
2010-10-18 11:24:16 install libboost-system1.42.0 <none> 1.42.0-3ubuntu1
2010-10-18 11:24:16 status half-installed libboost-system1.42.0 1.42.0-3ubuntu1
2010-10-18 11:24:17 status unpacked libboost-system1.42.0 1.42.0-3ubuntu1
2010-10-18 11:24:17 status unpacked libboost-system1.42.0 1.42.0-3ubuntu1
2010-10-18 11:24:17 install libboost-filesystem1.42.0 <none> 1.42.0-3ubuntu1
2010-10-18 11:24:17 status half-installed libboost-filesystem1.42.0 1.42.0-3ubuntu1
2010-10-18 11:24:17 status unpacked libboost-filesystem1.42.0 1.42.0-3ubuntu1
2010-10-18 11:24:17 status unpacked libboost-filesystem1.42.0 1.42.0-3ubuntu1
2010-10-18 11:24:18 install libdbus-c++-1-0 <none> 0~20090907-1
2010-10-18 11:24:18 status half-installed libdbus-c++-1-0 0~20090907-1
2010-10-18 11:24:18 status unpacked libdbus-c++-1-0 0~20090907-1
2010-10-18 11:24:18 status unpacked libdbus-c++-1-0 0~20090907-1
2010-10-18 11:24:18 install libgconfmm-2.6-1c2 <none> 2.28.0-1
2010-10-18 11:24:18 status half-installed libgconfmm-2.6-1c2 2.28.0-1
2010-10-18 11:24:19 status unpacked libgconfmm-2.6-1c2 2.28.0-1
2010-10-18 11:24:19 status unpacked libgconfmm-2.6-1c2 2.28.0-1
2010-10-18 11:24:19 install libpanelappletmm-2.6-1c2 <none> 2.26.0-1
2010-10-18 11:24:19 status half-installed libpanelappletmm-2.6-1c2 2.26.0-1
2010-10-18 11:24:19 status unpacked libpanelappletmm-2.6-1c2 2.26.0-1
2010-10-18 11:24:19 status unpacked libpanelappletmm-2.6-1c2 2.26.0-1
2010-10-18 11:24:20 install libpcrecpp0 <none> 8.02-1
2010-10-18 11:24:20 status half-installed libpcrecpp0 8.02-1
2010-10-18 11:24:21 status unpacked libpcrecpp0 8.02-1
2010-10-18 11:24:21 status unpacked libpcrecpp0 8.02-1
2010-10-18 11:24:21 install gnote <none> 0.7.1-1.1
2010-10-18 11:24:21 status half-installed gnote 0.7.1-1.1
2010-10-18 11:24:21 status triggers-pending hicolor-icon-theme 0.11-1
2010-10-18 11:24:21 status half-installed gnote 0.7.1-1.1
2010-10-18 11:24:21 status triggers-pending desktop-file-utils 0.16-0ubuntu4
2010-10-18 11:24:21 status half-installed gnote 0.7.1-1.1
2010-10-18 11:24:21 status triggers-pending python-gmenu 2.30.4-0ubuntu1
2010-10-18 11:24:21 status half-installed gnote 0.7.1-1.1
2010-10-18 11:24:21 status triggers-pending man-db 2.5.7-4
2010-10-18 11:24:21 status half-installed gnote 0.7.1-1.1
2010-10-18 11:24:21 status triggers-pending gconf2 2.31.91-0ubuntu3
2010-10-18 11:24:22 status half-installed gnote 0.7.1-1.1
2010-10-18 11:24:22 status unpacked gnote 0.7.1-1.1
2010-10-18 11:24:22 status unpacked gnote 0.7.1-1.1
2010-10-18 11:24:22 trigproc hicolor-icon-theme 0.11-1 0.11-1
2010-10-18 11:24:22 status half-configured hicolor-icon-theme 0.11-1
2010-10-18 11:24:24 status installed hicolor-icon-theme 0.11-1
2010-10-18 11:24:24 trigproc desktop-file-utils 0.16-0ubuntu4 0.16-0ubuntu4
2010-10-18 11:24:24 status half-configured desktop-file-utils 0.16-0ubuntu4
2010-10-18 11:24:24 status installed desktop-file-utils 0.16-0ubuntu4
2010-10-18 11:24:24 trigproc python-gmenu 2.30.4-0ubuntu1 2.30.4-0ubuntu1
2010-10-18 11:24:24 status half-configured python-gmenu 2.30.4-0ubuntu1
2010-10-18 11:24:24 status installed python-gmenu 2.30.4-0ubuntu1
2010-10-18 11:24:24 status triggers-pending python-support 1.0.9ubuntu1
2010-10-18 11:24:24 trigproc man-db 2.5.7-4 2.5.7-4
2010-10-18 11:24:24 status half-configured man-db 2.5.7-4
2010-10-18 11:24:25 status installed man-db 2.5.7-4
2010-10-18 11:24:25 trigproc gconf2 2.31.91-0ubuntu3 2.31.91-0ubuntu3
2010-10-18 11:24:25 status half-configured gconf2 2.31.91-0ubuntu3
2010-10-18 11:24:30 status installed gconf2 2.31.91-0ubuntu3
2010-10-18 11:24:30 trigproc python-support 1.0.9ubuntu1 1.0.9ubuntu1
2010-10-18 11:24:30 status half-configured python-support 1.0.9ubuntu1
2010-10-18 11:24:30 status installed python-support 1.0.9ubuntu1
2010-10-18 11:24:31 startup packages configure
2010-10-18 11:24:31 configure libboost-system1.42.0 1.42.0-3ubuntu1 1.42.0-3ubuntu1
2010-10-18 11:24:31 status unpacked libboost-system1.42.0 1.42.0-3ubuntu1
2010-10-18 11:24:31 status half-configured libboost-system1.42.0 1.42.0-3ubuntu1
2010-10-18 11:24:31 status installed libboost-system1.42.0 1.42.0-3ubuntu1
2010-10-18 11:24:31 status triggers-pending libc-bin 2.12.1-0ubuntu6
2010-10-18 11:24:32 configure libboost-filesystem1.42.0 1.42.0-3ubuntu1 1.42.0-3ubuntu1
2010-10-18 11:24:32 status unpacked libboost-filesystem1.42.0 1.42.0-3ubuntu1
2010-10-18 11:24:32 status half-configured libboost-filesystem1.42.0 1.42.0-3ubuntu1
2010-10-18 11:24:32 status installed libboost-filesystem1.42.0 1.42.0-3ubuntu1
2010-10-18 11:24:32 configure libdbus-c++-1-0 0~20090907-1 0~20090907-1
2010-10-18 11:24:32 status unpacked libdbus-c++-1-0 0~20090907-1
2010-10-18 11:24:32 status half-configured libdbus-c++-1-0 0~20090907-1
2010-10-18 11:24:32 status installed libdbus-c++-1-0 0~20090907-1
2010-10-18 11:24:32 configure libgconfmm-2.6-1c2 2.28.0-1 2.28.0-1
2010-10-18 11:24:32 status unpacked libgconfmm-2.6-1c2 2.28.0-1
2010-10-18 11:24:32 status half-configured libgconfmm-2.6-1c2 2.28.0-1
2010-10-18 11:24:32 status installed libgconfmm-2.6-1c2 2.28.0-1
2010-10-18 11:24:32 configure libpanelappletmm-2.6-1c2 2.26.0-1 2.26.0-1
2010-10-18 11:24:32 status unpacked libpanelappletmm-2.6-1c2 2.26.0-1
2010-10-18 11:24:32 status half-configured libpanelappletmm-2.6-1c2 2.26.0-1
2010-10-18 11:24:32 status installed libpanelappletmm-2.6-1c2 2.26.0-1
2010-10-18 11:24:32 configure libpcrecpp0 8.02-1 8.02-1
2010-10-18 11:24:32 status unpacked libpcrecpp0 8.02-1
2010-10-18 11:24:32 status half-configured libpcrecpp0 8.02-1
2010-10-18 11:24:33 status installed libpcrecpp0 8.02-1
2010-10-18 11:24:33 configure gnote 0.7.1-1.1 0.7.1-1.1
2010-10-18 11:24:33 status unpacked gnote 0.7.1-1.1
2010-10-18 11:24:33 status half-configured gnote 0.7.1-1.1
2010-10-18 11:24:33 status installed gnote 0.7.1-1.1
2010-10-18 11:24:33 trigproc libc-bin 2.12.1-0ubuntu6 2.12.1-0ubuntu6
2010-10-18 11:24:33 status half-configured libc-bin 2.12.1-0ubuntu6
2010-10-18 11:24:33 status installed libc-bin 2.12.1-0ubuntu6
2010-10-18 11:54:04 startup packages remove
2010-10-18 11:54:04 status installed gnote 0.7.1-1.1
2010-10-18 11:54:05 remove gnote 0.7.1-1.1 0.7.1-1.1
2010-10-18 11:54:05 status half-configured gnote 0.7.1-1.1
2010-10-18 11:54:05 status half-installed gnote 0.7.1-1.1
2010-10-18 11:54:05 status triggers-pending gconf2 2.31.91-0ubuntu3
2010-10-18 11:54:05 status half-installed gnote 0.7.1-1.1
2010-10-18 11:54:05 status triggers-pending man-db 2.5.7-4
2010-10-18 11:54:05 status half-installed gnote 0.7.1-1.1
2010-10-18 11:54:05 status triggers-pending desktop-file-utils 0.16-0ubuntu4
2010-10-18 11:54:05 status half-installed gnote 0.7.1-1.1
2010-10-18 11:54:06 status triggers-pending python-gmenu 2.30.4-0ubuntu1
2010-10-18 11:54:06 status half-installed gnote 0.7.1-1.1
2010-10-18 11:54:06 status triggers-pending hicolor-icon-theme 0.11-1
2010-10-18 11:54:06 status half-installed gnote 0.7.1-1.1
2010-10-18 11:54:06 status config-files gnote 0.7.1-1.1
2010-10-18 11:54:06 status config-files gnote 0.7.1-1.1
2010-10-18 11:54:06 status config-files gnote 0.7.1-1.1
2010-10-18 11:54:06 status config-files gnote 0.7.1-1.1
2010-10-18 11:54:06 status config-files gnote 0.7.1-1.1
2010-10-18 11:54:06 status config-files gnote 0.7.1-1.1
2010-10-18 11:54:06 status config-files gnote 0.7.1-1.1
2010-10-18 11:54:06 status config-files gnote 0.7.1-1.1
2010-10-18 11:54:06 status not-installed gnote <none>
2010-10-18 11:54:06 trigproc gconf2 2.31.91-0ubuntu3 2.31.91-0ubuntu3
2010-10-18 11:54:06 status half-configured gconf2 2.31.91-0ubuntu3
2010-10-18 11:54:11 status installed gconf2 2.31.91-0ubuntu3
2010-10-18 11:54:11 trigproc man-db 2.5.7-4 2.5.7-4
2010-10-18 11:54:11 status half-configured man-db 2.5.7-4
2010-10-18 11:54:12 status installed man-db 2.5.7-4
2010-10-18 11:54:12 trigproc desktop-file-utils 0.16-0ubuntu4 0.16-0ubuntu4
2010-10-18 11:54:12 status half-configured desktop-file-utils 0.16-0ubuntu4
2010-10-18 11:54:12 status installed desktop-file-utils 0.16-0ubuntu4
2010-10-18 11:54:12 trigproc python-gmenu 2.30.4-0ubuntu1 2.30.4-0ubuntu1
2010-10-18 11:54:12 status half-configured python-gmenu 2.30.4-0ubuntu1
2010-10-18 11:54:13 status installed python-gmenu 2.30.4-0ubuntu1
2010-10-18 11:54:13 status triggers-pending python-support 1.0.9ubuntu1
2010-10-18 11:54:13 trigproc hicolor-icon-theme 0.11-1 0.11-1
2010-10-18 11:54:13 status half-configured hicolor-icon-theme 0.11-1
2010-10-18 11:54:14 status installed hicolor-icon-theme 0.11-1
2010-10-18 11:54:14 trigproc python-support 1.0.9ubuntu1 1.0.9ubuntu1
2010-10-18 11:54:14 status half-configured python-support 1.0.9ubuntu1
2010-10-18 11:54:15 status installed python-support 1.0.9ubuntu1
2010-10-18 14:35:16 startup archives unpack
2010-10-18 14:35:17 install flashplugin-nonfree-extrasound <none> 0.0.svn2431-3
2010-10-18 14:35:17 status half-installed flashplugin-nonfree-extrasound 0.0.svn2431-3
2010-10-18 14:35:17 status unpacked flashplugin-nonfree-extrasound 0.0.svn2431-3
2010-10-18 14:35:17 status unpacked flashplugin-nonfree-extrasound 0.0.svn2431-3
2010-10-18 14:35:18 startup packages configure
2010-10-18 14:35:18 configure flashplugin-nonfree-extrasound 0.0.svn2431-3 0.0.svn2431-3
2010-10-18 14:35:18 status unpacked flashplugin-nonfree-extrasound 0.0.svn2431-3
2010-10-18 14:35:18 status half-configured flashplugin-nonfree-extrasound 0.0.svn2431-3
2010-10-18 14:35:18 status installed flashplugin-nonfree-extrasound 0.0.svn2431-3
2010-10-18 14:47:07 startup packages purge
2010-10-18 14:47:07 status installed ubuntu-desktop 1.207
2010-10-18 14:47:08 remove ubuntu-desktop 1.207 1.207
2010-10-18 14:47:08 status half-configured ubuntu-desktop 1.207
2010-10-18 14:47:08 status half-installed ubuntu-desktop 1.207
2010-10-18 14:47:08 status config-files ubuntu-desktop 1.207
2010-10-18 14:47:08 status config-files ubuntu-desktop 1.207
2010-10-18 14:47:08 status config-files ubuntu-desktop 1.207
2010-10-18 14:47:08 status not-installed ubuntu-desktop <none>
2010-10-18 14:47:08 status installed alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-18 14:47:08 remove alsa-base 1.0.23+dfsg-1ubuntu4 1.0.23+dfsg-1ubuntu4
2010-10-18 14:47:08 status half-configured alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-18 14:47:08 status half-installed alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-18 14:47:08 status config-files alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-18 14:47:08 purge alsa-base 1.0.23+dfsg-1ubuntu4 1.0.23+dfsg-1ubuntu4
2010-10-18 14:47:08 status config-files alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-18 14:47:09 status config-files alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-18 14:47:09 status config-files alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-18 14:47:09 status config-files alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-18 14:47:09 status config-files alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-18 14:47:09 status not-installed alsa-base <none>
2010-10-18 14:47:09 status installed alsa-utils 1.0.23-2ubuntu3
2010-10-18 14:47:09 remove alsa-utils 1.0.23-2ubuntu3 1.0.23-2ubuntu3
2010-10-18 14:47:09 status half-configured alsa-utils 1.0.23-2ubuntu3
2010-10-18 14:47:09 status half-installed alsa-utils 1.0.23-2ubuntu3
2010-10-18 14:47:09 status triggers-pending ureadahead 0.100.0-8
2010-10-18 14:47:09 status half-installed alsa-utils 1.0.23-2ubuntu3
2010-10-18 14:47:09 status triggers-pending ureadahead 0.100.0-8
2010-10-18 14:47:09 status triggers-pending man-db 2.5.7-4
2010-10-18 14:47:09 status half-installed alsa-utils 1.0.23-2ubuntu3
2010-10-18 14:47:09 status config-files alsa-utils 1.0.23-2ubuntu3
2010-10-18 14:47:10 purge alsa-utils 1.0.23-2ubuntu3 1.0.23-2ubuntu3
2010-10-18 14:47:10 status config-files alsa-utils 1.0.23-2ubuntu3
2010-10-18 14:47:10 status config-files alsa-utils 1.0.23-2ubuntu3
2010-10-18 14:47:10 status config-files alsa-utils 1.0.23-2ubuntu3
2010-10-18 14:47:10 status config-files alsa-utils 1.0.23-2ubuntu3
2010-10-18 14:47:10 status config-files alsa-utils 1.0.23-2ubuntu3
2010-10-18 14:47:10 status config-files alsa-utils 1.0.23-2ubuntu3
2010-10-18 14:47:10 status not-installed alsa-utils <none>
2010-10-18 14:47:10 status installed linux-sound-base 1.0.23+dfsg-1ubuntu4
2010-10-18 14:47:10 remove linux-sound-base 1.0.23+dfsg-1ubuntu4 1.0.23+dfsg-1ubuntu4
2010-10-18 14:47:10 status half-configured linux-sound-base 1.0.23+dfsg-1ubuntu4
2010-10-18 14:47:10 status half-installed linux-sound-base 1.0.23+dfsg-1ubuntu4
2010-10-18 14:47:10 status config-files linux-sound-base 1.0.23+dfsg-1ubuntu4
2010-10-18 14:47:11 purge linux-sound-base 1.0.23+dfsg-1ubuntu4 1.0.23+dfsg-1ubuntu4
2010-10-18 14:47:11 status config-files linux-sound-base 1.0.23+dfsg-1ubuntu4
2010-10-18 14:47:11 status config-files linux-sound-base 1.0.23+dfsg-1ubuntu4
2010-10-18 14:47:11 status config-files linux-sound-base 1.0.23+dfsg-1ubuntu4
2010-10-18 14:47:11 status config-files linux-sound-base 1.0.23+dfsg-1ubuntu4
2010-10-18 14:47:11 status config-files linux-sound-base 1.0.23+dfsg-1ubuntu4
2010-10-18 14:47:12 status not-installed linux-sound-base <none>
2010-10-18 14:47:12 trigproc ureadahead 0.100.0-8 0.100.0-8
2010-10-18 14:47:12 status half-configured ureadahead 0.100.0-8
2010-10-18 14:47:12 status installed ureadahead 0.100.0-8
2010-10-18 14:47:12 trigproc man-db 2.5.7-4 2.5.7-4
2010-10-18 14:47:12 status half-configured man-db 2.5.7-4
2010-10-18 14:47:12 status installed man-db 2.5.7-4
2010-10-18 14:48:20 startup archives unpack
2010-10-18 14:48:21 install linux-sound-base <none> 1.0.23+dfsg-1ubuntu4
2010-10-18 14:48:21 status half-installed linux-sound-base 1.0.23+dfsg-1ubuntu4
2010-10-18 14:48:21 status unpacked linux-sound-base 1.0.23+dfsg-1ubuntu4
2010-10-18 14:48:21 status unpacked linux-sound-base 1.0.23+dfsg-1ubuntu4
2010-10-18 14:48:22 install alsa-base <none> 1.0.23+dfsg-1ubuntu4
2010-10-18 14:48:22 status half-installed alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-18 14:48:22 status unpacked alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-18 14:48:22 status unpacked alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-18 14:48:23 install alsa-utils <none> 1.0.23-2ubuntu3
2010-10-18 14:48:23 status half-installed alsa-utils 1.0.23-2ubuntu3
2010-10-18 14:48:23 status triggers-pending man-db 2.5.7-4
2010-10-18 14:48:23 status half-installed alsa-utils 1.0.23-2ubuntu3
2010-10-18 14:48:23 status triggers-pending ureadahead 0.100.0-8
2010-10-18 14:48:23 status half-installed alsa-utils 1.0.23-2ubuntu3
2010-10-18 14:48:23 status triggers-pending ureadahead 0.100.0-8
2010-10-18 14:48:23 status unpacked alsa-utils 1.0.23-2ubuntu3
2010-10-18 14:48:24 status unpacked alsa-utils 1.0.23-2ubuntu3
2010-10-18 14:48:24 trigproc man-db 2.5.7-4 2.5.7-4
2010-10-18 14:48:24 status half-configured man-db 2.5.7-4
2010-10-18 14:48:24 status installed man-db 2.5.7-4
2010-10-18 14:48:24 trigproc ureadahead 0.100.0-8 0.100.0-8
2010-10-18 14:48:24 status half-configured ureadahead 0.100.0-8
2010-10-18 14:48:24 status installed ureadahead 0.100.0-8
2010-10-18 14:48:25 startup packages configure
2010-10-18 14:48:25 configure linux-sound-base 1.0.23+dfsg-1ubuntu4 1.0.23+dfsg-1ubuntu4
2010-10-18 14:48:25 status unpacked linux-sound-base 1.0.23+dfsg-1ubuntu4
2010-10-18 14:48:25 status half-configured linux-sound-base 1.0.23+dfsg-1ubuntu4
2010-10-18 14:48:25 status installed linux-sound-base 1.0.23+dfsg-1ubuntu4
2010-10-18 14:48:26 configure alsa-base 1.0.23+dfsg-1ubuntu4 1.0.23+dfsg-1ubuntu4
2010-10-18 14:48:26 status unpacked alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-18 14:48:26 status unpacked alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-18 14:48:26 status unpacked alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-18 14:48:26 status unpacked alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-18 14:48:26 status half-configured alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-18 14:48:26 status installed alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-18 14:48:26 configure alsa-utils 1.0.23-2ubuntu3 1.0.23-2ubuntu3
2010-10-18 14:48:26 status unpacked alsa-utils 1.0.23-2ubuntu3
2010-10-18 14:48:26 status unpacked alsa-utils 1.0.23-2ubuntu3
2010-10-18 14:48:26 status half-configured alsa-utils 1.0.23-2ubuntu3
2010-10-18 14:48:27 status installed alsa-utils 1.0.23-2ubuntu3
2010-10-18 16:56:54 startup packages purge
2010-10-18 16:56:54 status installed flashplugin-installer 10.1.85.3ubuntu1
2010-10-18 16:56:55 remove flashplugin-installer 10.1.85.3ubuntu1 10.1.85.3ubuntu1
2010-10-18 16:56:55 status half-configured flashplugin-installer 10.1.85.3ubuntu1
2010-10-18 16:56:56 status half-installed flashplugin-installer 10.1.85.3ubuntu1
2010-10-18 16:56:56 status config-files flashplugin-installer 10.1.85.3ubuntu1
2010-10-18 16:56:56 purge flashplugin-installer 10.1.85.3ubuntu1 10.1.85.3ubuntu1
2010-10-18 16:56:56 status config-files flashplugin-installer 10.1.85.3ubuntu1
2010-10-18 16:56:56 status config-files flashplugin-installer 10.1.85.3ubuntu1
2010-10-18 16:56:56 status config-files flashplugin-installer 10.1.85.3ubuntu1
2010-10-18 16:56:57 status config-files flashplugin-installer 10.1.85.3ubuntu1
2010-10-18 16:56:57 status config-files flashplugin-installer 10.1.85.3ubuntu1
2010-10-18 16:56:57 status not-installed flashplugin-installer <none>
2010-10-18 16:56:57 status installed flashplugin-nonfree-extrasound 0.0.svn2431-3
2010-10-18 16:56:57 remove flashplugin-nonfree-extrasound 0.0.svn2431-3 0.0.svn2431-3
2010-10-18 16:56:57 status half-configured flashplugin-nonfree-extrasound 0.0.svn2431-3
2010-10-18 16:56:57 status half-installed flashplugin-nonfree-extrasound 0.0.svn2431-3
2010-10-18 16:56:57 status config-files flashplugin-nonfree-extrasound 0.0.svn2431-3
2010-10-18 16:56:57 status config-files flashplugin-nonfree-extrasound 0.0.svn2431-3
2010-10-18 16:56:57 status config-files flashplugin-nonfree-extrasound 0.0.svn2431-3
2010-10-18 16:56:57 status not-installed flashplugin-nonfree-extrasound <none>
2010-10-18 17:00:41 startup archives unpack
2010-10-18 17:00:42 install adobe-flashplugin <none> 10.1.85.3-1maverick1
2010-10-18 17:00:42 status half-installed adobe-flashplugin 10.1.85.3-1maverick1
2010-10-18 17:00:42 status unpacked adobe-flashplugin 10.1.85.3-1maverick1
2010-10-18 17:00:42 status unpacked adobe-flashplugin 10.1.85.3-1maverick1
2010-10-18 17:00:43 startup packages configure
2010-10-18 17:00:43 configure adobe-flashplugin 10.1.85.3-1maverick1 10.1.85.3-1maverick1
2010-10-18 17:00:43 status unpacked adobe-flashplugin 10.1.85.3-1maverick1
2010-10-18 17:00:43 status half-configured adobe-flashplugin 10.1.85.3-1maverick1
2010-10-18 17:00:43 status installed adobe-flashplugin 10.1.85.3-1maverick1
2010-10-18 17:34:30 startup archives unpack
2010-10-18 17:34:32 install libfltk1.1 <none> 1.1.10-2
2010-10-18 17:34:32 status half-installed libfltk1.1 1.1.10-2
2010-10-18 17:34:32 status unpacked libfltk1.1 1.1.10-2
2010-10-18 17:34:32 status unpacked libfltk1.1 1.1.10-2
2010-10-18 17:34:32 install alsamixergui <none> 0.9.0rc2-1-9
2010-10-18 17:34:32 status half-installed alsamixergui 0.9.0rc2-1-9
2010-10-18 17:34:32 status triggers-pending man-db 2.5.7-4
2010-10-18 17:34:32 status half-installed alsamixergui 0.9.0rc2-1-9
2010-10-18 17:34:32 status triggers-pending menu 2.1.44ubuntu1
2010-10-18 17:34:33 status half-installed alsamixergui 0.9.0rc2-1-9
2010-10-18 17:34:33 status triggers-pending desktop-file-utils 0.16-0ubuntu4
2010-10-18 17:34:33 status half-installed alsamixergui 0.9.0rc2-1-9
2010-10-18 17:34:33 status triggers-pending python-gmenu 2.30.4-0ubuntu1
2010-10-18 17:34:33 status half-installed alsamixergui 0.9.0rc2-1-9
2010-10-18 17:34:33 status unpacked alsamixergui 0.9.0rc2-1-9
2010-10-18 17:34:33 status unpacked alsamixergui 0.9.0rc2-1-9
2010-10-18 17:34:33 trigproc man-db 2.5.7-4 2.5.7-4
2010-10-18 17:34:33 status half-configured man-db 2.5.7-4
2010-10-18 17:34:34 status installed man-db 2.5.7-4
2010-10-18 17:34:34 trigproc menu 2.1.44ubuntu1 2.1.44ubuntu1
2010-10-18 17:34:34 status half-configured menu 2.1.44ubuntu1
2010-10-18 17:34:35 status installed menu 2.1.44ubuntu1
2010-10-18 17:34:35 trigproc desktop-file-utils 0.16-0ubuntu4 0.16-0ubuntu4
2010-10-18 17:34:35 status half-configured desktop-file-utils 0.16-0ubuntu4
2010-10-18 17:34:35 status installed desktop-file-utils 0.16-0ubuntu4
2010-10-18 17:34:35 trigproc python-gmenu 2.30.4-0ubuntu1 2.30.4-0ubuntu1
2010-10-18 17:34:35 status half-configured python-gmenu 2.30.4-0ubuntu1
2010-10-18 17:34:36 status installed python-gmenu 2.30.4-0ubuntu1
2010-10-18 17:34:36 status triggers-pending python-support 1.0.9ubuntu1
2010-10-18 17:34:36 trigproc python-support 1.0.9ubuntu1 1.0.9ubuntu1
2010-10-18 17:34:36 status half-configured python-support 1.0.9ubuntu1
2010-10-18 17:34:36 status installed python-support 1.0.9ubuntu1
2010-10-18 17:34:37 startup packages configure
2010-10-18 17:34:37 configure libfltk1.1 1.1.10-2 1.1.10-2
2010-10-18 17:34:37 status unpacked libfltk1.1 1.1.10-2
2010-10-18 17:34:38 status half-configured libfltk1.1 1.1.10-2
2010-10-18 17:34:38 status installed libfltk1.1 1.1.10-2
2010-10-18 17:34:38 status triggers-pending libc-bin 2.12.1-0ubuntu6
2010-10-18 17:34:38 configure alsamixergui 0.9.0rc2-1-9 0.9.0rc2-1-9
2010-10-18 17:34:38 status unpacked alsamixergui 0.9.0rc2-1-9
2010-10-18 17:34:38 status half-configured alsamixergui 0.9.0rc2-1-9
2010-10-18 17:34:38 status installed alsamixergui 0.9.0rc2-1-9
2010-10-18 17:34:39 status triggers-pending menu 2.1.44ubuntu1
2010-10-18 17:34:39 status triggers-awaited menu 2.1.44ubuntu1
2010-10-18 17:34:39 trigproc libc-bin 2.12.1-0ubuntu6 2.12.1-0ubuntu6
2010-10-18 17:34:39 status half-configured libc-bin 2.12.1-0ubuntu6
2010-10-18 17:34:39 status installed libc-bin 2.12.1-0ubuntu6
2010-10-18 17:34:39 trigproc menu 2.1.44ubuntu1 2.1.44ubuntu1
2010-10-18 17:34:39 status half-configured menu 2.1.44ubuntu1
2010-10-18 17:34:39 status installed menu 2.1.44ubuntu1
2010-10-18 17:38:34 startup packages purge
2010-10-18 17:38:34 status installed alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-18 17:38:34 remove alsa-base 1.0.23+dfsg-1ubuntu4 1.0.23+dfsg-1ubuntu4
2010-10-18 17:38:34 status half-configured alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-18 17:38:34 status half-installed alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-18 17:38:34 status config-files alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-18 17:38:34 purge alsa-base 1.0.23+dfsg-1ubuntu4 1.0.23+dfsg-1ubuntu4
2010-10-18 17:38:34 status config-files alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-18 17:38:35 status config-files alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-18 17:38:35 status config-files alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-18 17:38:35 status config-files alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-18 17:38:35 status config-files alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-18 17:38:35 status not-installed alsa-base <none>
2010-10-18 17:38:35 status installed alsa-utils 1.0.23-2ubuntu3
2010-10-18 17:38:35 remove alsa-utils 1.0.23-2ubuntu3 1.0.23-2ubuntu3
2010-10-18 17:38:35 status half-configured alsa-utils 1.0.23-2ubuntu3
2010-10-18 17:38:35 status half-installed alsa-utils 1.0.23-2ubuntu3
2010-10-18 17:38:35 status triggers-pending ureadahead 0.100.0-8
2010-10-18 17:38:35 status half-installed alsa-utils 1.0.23-2ubuntu3
2010-10-18 17:38:35 status triggers-pending ureadahead 0.100.0-8
2010-10-18 17:38:35 status triggers-pending man-db 2.5.7-4
2010-10-18 17:38:35 status half-installed alsa-utils 1.0.23-2ubuntu3
2010-10-18 17:38:35 status config-files alsa-utils 1.0.23-2ubuntu3
2010-10-18 17:38:35 purge alsa-utils 1.0.23-2ubuntu3 1.0.23-2ubuntu3
2010-10-18 17:38:35 status config-files alsa-utils 1.0.23-2ubuntu3
2010-10-18 17:38:35 status config-files alsa-utils 1.0.23-2ubuntu3
2010-10-18 17:38:36 status config-files alsa-utils 1.0.23-2ubuntu3
2010-10-18 17:38:36 status config-files alsa-utils 1.0.23-2ubuntu3
2010-10-18 17:38:36 status config-files alsa-utils 1.0.23-2ubuntu3
2010-10-18 17:38:36 status config-files alsa-utils 1.0.23-2ubuntu3
2010-10-18 17:38:36 status not-installed alsa-utils <none>
2010-10-18 17:38:36 status installed linux-sound-base 1.0.23+dfsg-1ubuntu4
2010-10-18 17:38:36 remove linux-sound-base 1.0.23+dfsg-1ubuntu4 1.0.23+dfsg-1ubuntu4
2010-10-18 17:38:36 status half-configured linux-sound-base 1.0.23+dfsg-1ubuntu4
2010-10-18 17:38:36 status half-installed linux-sound-base 1.0.23+dfsg-1ubuntu4
2010-10-18 17:38:36 status config-files linux-sound-base 1.0.23+dfsg-1ubuntu4
2010-10-18 17:38:36 purge linux-sound-base 1.0.23+dfsg-1ubuntu4 1.0.23+dfsg-1ubuntu4
2010-10-18 17:38:36 status config-files linux-sound-base 1.0.23+dfsg-1ubuntu4
2010-10-18 17:38:36 status config-files linux-sound-base 1.0.23+dfsg-1ubuntu4
2010-10-18 17:38:36 status config-files linux-sound-base 1.0.23+dfsg-1ubuntu4
2010-10-18 17:38:37 status config-files linux-sound-base 1.0.23+dfsg-1ubuntu4
2010-10-18 17:38:37 status config-files linux-sound-base 1.0.23+dfsg-1ubuntu4
2010-10-18 17:38:37 status not-installed linux-sound-base <none>
2010-10-18 17:38:37 trigproc ureadahead 0.100.0-8 0.100.0-8
2010-10-18 17:38:37 status half-configured ureadahead 0.100.0-8
2010-10-18 17:38:37 status installed ureadahead 0.100.0-8
2010-10-18 17:38:37 trigproc man-db 2.5.7-4 2.5.7-4
2010-10-18 17:38:37 status half-configured man-db 2.5.7-4
2010-10-18 17:38:38 status installed man-db 2.5.7-4
2010-10-18 17:38:59 startup archives unpack
2010-10-18 17:39:00 install linux-sound-base <none> 1.0.23+dfsg-1ubuntu4
2010-10-18 17:39:00 status half-installed linux-sound-base 1.0.23+dfsg-1ubuntu4
2010-10-18 17:39:00 status unpacked linux-sound-base 1.0.23+dfsg-1ubuntu4
2010-10-18 17:39:00 status unpacked linux-sound-base 1.0.23+dfsg-1ubuntu4
2010-10-18 17:39:00 install alsa-base <none> 1.0.23+dfsg-1ubuntu4
2010-10-18 17:39:00 status half-installed alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-18 17:39:01 status unpacked alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-18 17:39:01 status unpacked alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-18 17:39:01 install alsa-utils <none> 1.0.23-2ubuntu3
2010-10-18 17:39:01 status half-installed alsa-utils 1.0.23-2ubuntu3
2010-10-18 17:39:01 status triggers-pending man-db 2.5.7-4
2010-10-18 17:39:01 status half-installed alsa-utils 1.0.23-2ubuntu3
2010-10-18 17:39:01 status triggers-pending ureadahead 0.100.0-8
2010-10-18 17:39:01 status half-installed alsa-utils 1.0.23-2ubuntu3
2010-10-18 17:39:01 status triggers-pending ureadahead 0.100.0-8
2010-10-18 17:39:02 status unpacked alsa-utils 1.0.23-2ubuntu3
2010-10-18 17:39:02 status unpacked alsa-utils 1.0.23-2ubuntu3
2010-10-18 17:39:02 trigproc man-db 2.5.7-4 2.5.7-4
2010-10-18 17:39:02 status half-configured man-db 2.5.7-4
2010-10-18 17:39:03 status installed man-db 2.5.7-4
2010-10-18 17:39:03 trigproc ureadahead 0.100.0-8 0.100.0-8
2010-10-18 17:39:03 status half-configured ureadahead 0.100.0-8
2010-10-18 17:39:03 status installed ureadahead 0.100.0-8
2010-10-18 17:39:03 startup packages configure
2010-10-18 17:39:03 configure linux-sound-base 1.0.23+dfsg-1ubuntu4 1.0.23+dfsg-1ubuntu4
2010-10-18 17:39:03 status unpacked linux-sound-base 1.0.23+dfsg-1ubuntu4
2010-10-18 17:39:04 status half-configured linux-sound-base 1.0.23+dfsg-1ubuntu4
2010-10-18 17:39:04 status installed linux-sound-base 1.0.23+dfsg-1ubuntu4
2010-10-18 17:39:04 configure alsa-base 1.0.23+dfsg-1ubuntu4 1.0.23+dfsg-1ubuntu4
2010-10-18 17:39:04 status unpacked alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-18 17:39:04 status unpacked alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-18 17:39:04 status unpacked alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-18 17:39:04 status unpacked alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-18 17:39:04 status half-configured alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-18 17:39:04 status installed alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-18 17:39:04 configure alsa-utils 1.0.23-2ubuntu3 1.0.23-2ubuntu3
2010-10-18 17:39:04 status unpacked alsa-utils 1.0.23-2ubuntu3
2010-10-18 17:39:04 status unpacked alsa-utils 1.0.23-2ubuntu3
2010-10-18 17:39:05 status half-configured alsa-utils 1.0.23-2ubuntu3
2010-10-18 17:39:05 status installed alsa-utils 1.0.23-2ubuntu3
2010-10-18 17:54:15 startup archives unpack
2010-10-18 17:54:16 install fxload <none> 0.0.20081013-1ubuntu1
2010-10-18 17:54:16 status half-installed fxload 0.0.20081013-1ubuntu1
2010-10-18 17:54:17 status triggers-pending man-db 2.5.7-4
2010-10-18 17:54:17 status half-installed fxload 0.0.20081013-1ubuntu1
2010-10-18 17:54:17 status unpacked fxload 0.0.20081013-1ubuntu1
2010-10-18 17:54:17 status unpacked fxload 0.0.20081013-1ubuntu1
2010-10-18 17:54:17 install alsa-firmware-loaders <none> 1.0.23-3ubuntu1
2010-10-18 17:54:17 status half-installed alsa-firmware-loaders 1.0.23-3ubuntu1
2010-10-18 17:54:17 status half-installed alsa-firmware-loaders 1.0.23-3ubuntu1
2010-10-18 17:54:18 status unpacked alsa-firmware-loaders 1.0.23-3ubuntu1
2010-10-18 17:54:18 status unpacked alsa-firmware-loaders 1.0.23-3ubuntu1
2010-10-18 17:54:18 install alsa-firmware <none> 1.0.20-0medibuntu4.1
2010-10-18 17:54:18 status half-installed alsa-firmware 1.0.20-0medibuntu4.1
2010-10-18 17:54:19 status unpacked alsa-firmware 1.0.20-0medibuntu4.1
2010-10-18 17:54:19 status unpacked alsa-firmware 1.0.20-0medibuntu4.1
2010-10-18 17:54:19 install alsa-tools <none> 1.0.23-3ubuntu1
2010-10-18 17:54:19 status half-installed alsa-tools 1.0.23-3ubuntu1
2010-10-18 17:54:19 status half-installed alsa-tools 1.0.23-3ubuntu1
2010-10-18 17:54:19 status unpacked alsa-tools 1.0.23-3ubuntu1
2010-10-18 17:54:19 status unpacked alsa-tools 1.0.23-3ubuntu1
2010-10-18 17:54:20 trigproc man-db 2.5.7-4 2.5.7-4
2010-10-18 17:54:20 status half-configured man-db 2.5.7-4
2010-10-18 17:54:20 status installed man-db 2.5.7-4
2010-10-18 17:54:21 startup packages configure
2010-10-18 17:54:21 configure fxload 0.0.20081013-1ubuntu1 0.0.20081013-1ubuntu1
2010-10-18 17:54:21 status unpacked fxload 0.0.20081013-1ubuntu1
2010-10-18 17:54:21 status half-configured fxload 0.0.20081013-1ubuntu1
2010-10-18 17:54:21 status installed fxload 0.0.20081013-1ubuntu1
2010-10-18 17:54:21 configure alsa-firmware-loaders 1.0.23-3ubuntu1 1.0.23-3ubuntu1
2010-10-18 17:54:21 status unpacked alsa-firmware-loaders 1.0.23-3ubuntu1
2010-10-18 17:54:21 status half-configured alsa-firmware-loaders 1.0.23-3ubuntu1
2010-10-18 17:54:21 status installed alsa-firmware-loaders 1.0.23-3ubuntu1
2010-10-18 17:54:21 configure alsa-firmware 1.0.20-0medibuntu4.1 1.0.20-0medibuntu4.1
2010-10-18 17:54:21 status unpacked alsa-firmware 1.0.20-0medibuntu4.1
2010-10-18 17:54:21 status half-configured alsa-firmware 1.0.20-0medibuntu4.1
2010-10-18 17:54:22 status installed alsa-firmware 1.0.20-0medibuntu4.1
2010-10-18 17:54:22 configure alsa-tools 1.0.23-3ubuntu1 1.0.23-3ubuntu1
2010-10-18 17:54:22 status unpacked alsa-tools 1.0.23-3ubuntu1
2010-10-18 17:54:22 status half-configured alsa-tools 1.0.23-3ubuntu1
2010-10-18 17:54:22 status installed alsa-tools 1.0.23-3ubuntu1
2010-10-18 17:54:26 startup archives unpack
2010-10-18 17:54:26 install alsa-oss <none> 1.0.17-4
2010-10-18 17:54:26 status half-installed alsa-oss 1.0.17-4
2010-10-18 17:54:26 status triggers-pending man-db 2.5.7-4
2010-10-18 17:54:26 status half-installed alsa-oss 1.0.17-4
2010-10-18 17:54:27 status unpacked alsa-oss 1.0.17-4
2010-10-18 17:54:27 status unpacked alsa-oss 1.0.17-4
2010-10-18 17:54:27 trigproc man-db 2.5.7-4 2.5.7-4
2010-10-18 17:54:27 status half-configured man-db 2.5.7-4
2010-10-18 17:54:27 status installed man-db 2.5.7-4
2010-10-18 17:54:28 startup packages configure
2010-10-18 17:54:28 configure alsa-oss 1.0.17-4 1.0.17-4
2010-10-18 17:54:28 status unpacked alsa-oss 1.0.17-4
2010-10-18 17:54:28 status half-configured alsa-oss 1.0.17-4
2010-10-18 17:54:28 status installed alsa-oss 1.0.17-4
2010-10-18 17:54:29 status triggers-pending libc-bin 2.12.1-0ubuntu6
2010-10-18 17:54:29 trigproc libc-bin 2.12.1-0ubuntu6 2.12.1-0ubuntu6
2010-10-18 17:54:29 status half-configured libc-bin 2.12.1-0ubuntu6
2010-10-18 17:54:29 status installed libc-bin 2.12.1-0ubuntu6
2010-10-18 17:54:41 startup archives unpack
2010-10-18 17:54:41 install alsa-tools-gui <none> 1.0.23-3ubuntu1
2010-10-18 17:54:41 status half-installed alsa-tools-gui 1.0.23-3ubuntu1
2010-10-18 17:54:41 status triggers-pending desktop-file-utils 0.16-0ubuntu4
2010-10-18 17:54:41 status half-installed alsa-tools-gui 1.0.23-3ubuntu1
2010-10-18 17:54:41 status triggers-pending python-gmenu 2.30.4-0ubuntu1
2010-10-18 17:54:41 status half-installed alsa-tools-gui 1.0.23-3ubuntu1
2010-10-18 17:54:41 status triggers-pending man-db 2.5.7-4
2010-10-18 17:54:41 status half-installed alsa-tools-gui 1.0.23-3ubuntu1
2010-10-18 17:54:41 status triggers-pending menu 2.1.44ubuntu1
2010-10-18 17:54:41 status half-installed alsa-tools-gui 1.0.23-3ubuntu1
2010-10-18 17:54:42 status unpacked alsa-tools-gui 1.0.23-3ubuntu1
2010-10-18 17:54:42 status unpacked alsa-tools-gui 1.0.23-3ubuntu1
2010-10-18 17:54:42 trigproc desktop-file-utils 0.16-0ubuntu4 0.16-0ubuntu4
2010-10-18 17:54:42 status half-configured desktop-file-utils 0.16-0ubuntu4
2010-10-18 17:54:42 status installed desktop-file-utils 0.16-0ubuntu4
2010-10-18 17:54:43 trigproc python-gmenu 2.30.4-0ubuntu1 2.30.4-0ubuntu1
2010-10-18 17:54:43 status half-configured python-gmenu 2.30.4-0ubuntu1
2010-10-18 17:54:43 status installed python-gmenu 2.30.4-0ubuntu1
2010-10-18 17:54:43 status triggers-pending python-support 1.0.9ubuntu1
2010-10-18 17:54:43 trigproc man-db 2.5.7-4 2.5.7-4
2010-10-18 17:54:43 status half-configured man-db 2.5.7-4
2010-10-18 17:54:43 status installed man-db 2.5.7-4
2010-10-18 17:54:43 trigproc menu 2.1.44ubuntu1 2.1.44ubuntu1
2010-10-18 17:54:43 status half-configured menu 2.1.44ubuntu1
2010-10-18 17:54:44 status installed menu 2.1.44ubuntu1
2010-10-18 17:54:44 trigproc python-support 1.0.9ubuntu1 1.0.9ubuntu1
2010-10-18 17:54:44 status half-configured python-support 1.0.9ubuntu1
2010-10-18 17:54:45 status installed python-support 1.0.9ubuntu1
2010-10-18 17:54:46 startup packages configure
2010-10-18 17:54:46 configure alsa-tools-gui 1.0.23-3ubuntu1 1.0.23-3ubuntu1
2010-10-18 17:54:46 status unpacked alsa-tools-gui 1.0.23-3ubuntu1
2010-10-18 17:54:46 status half-configured alsa-tools-gui 1.0.23-3ubuntu1
2010-10-18 17:54:46 status installed alsa-tools-gui 1.0.23-3ubuntu1
2010-10-18 17:54:46 status triggers-pending menu 2.1.44ubuntu1
2010-10-18 17:54:46 status triggers-awaited menu 2.1.44ubuntu1
2010-10-18 17:54:46 trigproc menu 2.1.44ubuntu1 2.1.44ubuntu1
2010-10-18 17:54:46 status half-configured menu 2.1.44ubuntu1
2010-10-18 17:54:47 status installed menu 2.1.44ubuntu1
2010-10-18 17:54:55 startup archives unpack
2010-10-18 17:54:57 install aconnectgui <none> 0.9.0rc2-1-9
2010-10-18 17:54:57 status half-installed aconnectgui 0.9.0rc2-1-9
2010-10-18 17:54:57 status triggers-pending man-db 2.5.7-4
2010-10-18 17:54:57 status half-installed aconnectgui 0.9.0rc2-1-9
2010-10-18 17:54:57 status triggers-pending menu 2.1.44ubuntu1
2010-10-18 17:54:57 status half-installed aconnectgui 0.9.0rc2-1-9
2010-10-18 17:54:57 status triggers-pending desktop-file-utils 0.16-0ubuntu4
2010-10-18 17:54:57 status half-installed aconnectgui 0.9.0rc2-1-9
2010-10-18 17:54:57 status triggers-pending python-gmenu 2.30.4-0ubuntu1
2010-10-18 17:54:58 status half-installed aconnectgui 0.9.0rc2-1-9
2010-10-18 17:54:58 status unpacked aconnectgui 0.9.0rc2-1-9
2010-10-18 17:54:58 status unpacked aconnectgui 0.9.0rc2-1-9
2010-10-18 17:54:58 trigproc man-db 2.5.7-4 2.5.7-4
2010-10-18 17:54:58 status half-configured man-db 2.5.7-4
2010-10-18 17:54:59 status installed man-db 2.5.7-4
2010-10-18 17:54:59 trigproc menu 2.1.44ubuntu1 2.1.44ubuntu1
2010-10-18 17:54:59 status half-configured menu 2.1.44ubuntu1
2010-10-18 17:54:59 status installed menu 2.1.44ubuntu1
2010-10-18 17:54:59 trigproc desktop-file-utils 0.16-0ubuntu4 0.16-0ubuntu4
2010-10-18 17:54:59 status half-configured desktop-file-utils 0.16-0ubuntu4
2010-10-18 17:54:59 status installed desktop-file-utils 0.16-0ubuntu4
2010-10-18 17:54:59 trigproc python-gmenu 2.30.4-0ubuntu1 2.30.4-0ubuntu1
2010-10-18 17:54:59 status half-configured python-gmenu 2.30.4-0ubuntu1
2010-10-18 17:55:00 status installed python-gmenu 2.30.4-0ubuntu1
2010-10-18 17:55:00 status triggers-pending python-support 1.0.9ubuntu1
2010-10-18 17:55:00 trigproc python-support 1.0.9ubuntu1 1.0.9ubuntu1
2010-10-18 17:55:00 status half-configured python-support 1.0.9ubuntu1
2010-10-18 17:55:00 status installed python-support 1.0.9ubuntu1
2010-10-18 17:55:01 startup packages configure
2010-10-18 17:55:01 configure aconnectgui 0.9.0rc2-1-9 0.9.0rc2-1-9
2010-10-18 17:55:01 status unpacked aconnectgui 0.9.0rc2-1-9
2010-10-18 17:55:01 status half-configured aconnectgui 0.9.0rc2-1-9
2010-10-18 17:55:01 status installed aconnectgui 0.9.0rc2-1-9
2010-10-18 17:55:01 status triggers-pending menu 2.1.44ubuntu1
2010-10-18 17:55:01 status triggers-awaited menu 2.1.44ubuntu1
2010-10-18 17:55:01 trigproc menu 2.1.44ubuntu1 2.1.44ubuntu1
2010-10-18 17:55:01 status half-configured menu 2.1.44ubuntu1
2010-10-18 17:55:01 status installed menu 2.1.44ubuntu1
2010-10-18 18:00:09 startup archives unpack
2010-10-18 18:00:09 install libstdc++6-4.4-dev <none> 4.4.4-14ubuntu5
2010-10-18 18:00:09 status half-installed libstdc++6-4.4-dev 4.4.4-14ubuntu5
2010-10-18 18:00:10 status unpacked libstdc++6-4.4-dev 4.4.4-14ubuntu5
2010-10-18 18:00:10 status unpacked libstdc++6-4.4-dev 4.4.4-14ubuntu5
2010-10-18 18:00:10 install g++-4.4 <none> 4.4.4-14ubuntu5
2010-10-18 18:00:10 status half-installed g++-4.4 4.4.4-14ubuntu5
2010-10-18 18:00:10 status triggers-pending man-db 2.5.7-4
2010-10-18 18:00:10 status half-installed g++-4.4 4.4.4-14ubuntu5
2010-10-18 18:00:11 status unpacked g++-4.4 4.4.4-14ubuntu5
2010-10-18 18:00:11 status unpacked g++-4.4 4.4.4-14ubuntu5
2010-10-18 18:00:11 install g++ <none> 4:4.4.4-1ubuntu2
2010-10-18 18:00:11 status half-installed g++ 4:4.4.4-1ubuntu2
2010-10-18 18:00:11 status half-installed g++ 4:4.4.4-1ubuntu2
2010-10-18 18:00:11 status unpacked g++ 4:4.4.4-1ubuntu2
2010-10-18 18:00:11 status unpacked g++ 4:4.4.4-1ubuntu2
2010-10-18 18:00:11 install libdpkg-perl <none> 1.15.8.4ubuntu3
2010-10-18 18:00:11 status half-installed libdpkg-perl 1.15.8.4ubuntu3
2010-10-18 18:00:12 status half-installed libdpkg-perl 1.15.8.4ubuntu3
2010-10-18 18:00:12 status unpacked libdpkg-perl 1.15.8.4ubuntu3
2010-10-18 18:00:12 status unpacked libdpkg-perl 1.15.8.4ubuntu3
2010-10-18 18:00:12 install patch <none> 2.6-2ubuntu1
2010-10-18 18:00:12 status half-installed patch 2.6-2ubuntu1
2010-10-18 18:00:12 status half-installed patch 2.6-2ubuntu1
2010-10-18 18:00:13 status unpacked patch 2.6-2ubuntu1
2010-10-18 18:00:13 status unpacked patch 2.6-2ubuntu1
2010-10-18 18:00:13 install dpkg-dev <none> 1.15.8.4ubuntu3
2010-10-18 18:00:13 status half-installed dpkg-dev 1.15.8.4ubuntu3
2010-10-18 18:00:13 status half-installed dpkg-dev 1.15.8.4ubuntu3
2010-10-18 18:00:14 status unpacked dpkg-dev 1.15.8.4ubuntu3
2010-10-18 18:00:14 status unpacked dpkg-dev 1.15.8.4ubuntu3
2010-10-18 18:00:14 install build-essential <none> 11.5
2010-10-18 18:00:14 status half-installed build-essential 11.5
2010-10-18 18:00:15 status unpacked build-essential 11.5
2010-10-18 18:00:15 status unpacked build-essential 11.5
2010-10-18 18:00:15 install fakeroot <none> 1.14.4-1ubuntu1
2010-10-18 18:00:15 status half-installed fakeroot 1.14.4-1ubuntu1
2010-10-18 18:00:15 status half-installed fakeroot 1.14.4-1ubuntu1
2010-10-18 18:00:15 status unpacked fakeroot 1.14.4-1ubuntu1
2010-10-18 18:00:16 status unpacked fakeroot 1.14.4-1ubuntu1
2010-10-18 18:00:16 install libalgorithm-diff-perl <none> 1.19.02-1
2010-10-18 18:00:16 status half-installed libalgorithm-diff-perl 1.19.02-1
2010-10-18 18:00:16 status half-installed libalgorithm-diff-perl 1.19.02-1
2010-10-18 18:00:16 status unpacked libalgorithm-diff-perl 1.19.02-1
2010-10-18 18:00:16 status unpacked libalgorithm-diff-perl 1.19.02-1
2010-10-18 18:00:17 install libalgorithm-merge-perl <none> 0.08-1
2010-10-18 18:00:17 status half-installed libalgorithm-merge-perl 0.08-1
2010-10-18 18:00:17 status half-installed libalgorithm-merge-perl 0.08-1
2010-10-18 18:00:17 status unpacked libalgorithm-merge-perl 0.08-1
2010-10-18 18:00:17 status unpacked libalgorithm-merge-perl 0.08-1
2010-10-18 18:00:17 trigproc man-db 2.5.7-4 2.5.7-4
2010-10-18 18:00:17 status half-configured man-db 2.5.7-4
2010-10-18 18:00:19 status installed man-db 2.5.7-4
2010-10-18 18:00:20 startup packages configure
2010-10-18 18:00:20 configure libdpkg-perl 1.15.8.4ubuntu3 1.15.8.4ubuntu3
2010-10-18 18:00:20 status unpacked libdpkg-perl 1.15.8.4ubuntu3
2010-10-18 18:00:20 status half-configured libdpkg-perl 1.15.8.4ubuntu3
2010-10-18 18:00:20 status installed libdpkg-perl 1.15.8.4ubuntu3
2010-10-18 18:00:20 configure patch 2.6-2ubuntu1 2.6-2ubuntu1
2010-10-18 18:00:20 status unpacked patch 2.6-2ubuntu1
2010-10-18 18:00:20 status half-configured patch 2.6-2ubuntu1
2010-10-18 18:00:20 status installed patch 2.6-2ubuntu1
2010-10-18 18:00:20 configure dpkg-dev 1.15.8.4ubuntu3 1.15.8.4ubuntu3
2010-10-18 18:00:20 status unpacked dpkg-dev 1.15.8.4ubuntu3
2010-10-18 18:00:20 status unpacked dpkg-dev 1.15.8.4ubuntu3
2010-10-18 18:00:20 status unpacked dpkg-dev 1.15.8.4ubuntu3
2010-10-18 18:00:21 status half-configured dpkg-dev 1.15.8.4ubuntu3
2010-10-18 18:00:21 status installed dpkg-dev 1.15.8.4ubuntu3
2010-10-18 18:00:21 configure fakeroot 1.14.4-1ubuntu1 1.14.4-1ubuntu1
2010-10-18 18:00:21 status unpacked fakeroot 1.14.4-1ubuntu1
2010-10-18 18:00:21 status half-configured fakeroot 1.14.4-1ubuntu1
2010-10-18 18:00:21 status installed fakeroot 1.14.4-1ubuntu1
2010-10-18 18:00:21 configure libalgorithm-diff-perl 1.19.02-1 1.19.02-1
2010-10-18 18:00:21 status unpacked libalgorithm-diff-perl 1.19.02-1
2010-10-18 18:00:21 status half-configured libalgorithm-diff-perl 1.19.02-1
2010-10-18 18:00:21 status installed libalgorithm-diff-perl 1.19.02-1
2010-10-18 18:00:21 configure libalgorithm-merge-perl 0.08-1 0.08-1
2010-10-18 18:00:21 status unpacked libalgorithm-merge-perl 0.08-1
2010-10-18 18:00:21 status half-configured libalgorithm-merge-perl 0.08-1
2010-10-18 18:00:21 status installed libalgorithm-merge-perl 0.08-1
2010-10-18 18:00:21 configure libstdc++6-4.4-dev 4.4.4-14ubuntu5 4.4.4-14ubuntu5
2010-10-18 18:00:21 status unpacked libstdc++6-4.4-dev 4.4.4-14ubuntu5
2010-10-18 18:00:21 status half-configured libstdc++6-4.4-dev 4.4.4-14ubuntu5
2010-10-18 18:00:22 status installed libstdc++6-4.4-dev 4.4.4-14ubuntu5
2010-10-18 18:00:22 configure g++-4.4 4.4.4-14ubuntu5 4.4.4-14ubuntu5
2010-10-18 18:00:22 status unpacked g++-4.4 4.4.4-14ubuntu5
2010-10-18 18:00:22 status half-configured g++-4.4 4.4.4-14ubuntu5
2010-10-18 18:00:22 status installed g++-4.4 4.4.4-14ubuntu5
2010-10-18 18:00:23 configure g++ 4:4.4.4-1ubuntu2 4:4.4.4-1ubuntu2
2010-10-18 18:00:23 status unpacked g++ 4:4.4.4-1ubuntu2
2010-10-18 18:00:23 status half-configured g++ 4:4.4.4-1ubuntu2
2010-10-18 18:00:23 status installed g++ 4:4.4.4-1ubuntu2
2010-10-18 18:00:23 configure build-essential 11.5 11.5
2010-10-18 18:00:23 status unpacked build-essential 11.5
2010-10-18 18:00:23 status half-configured build-essential 11.5
2010-10-18 18:00:23 status installed build-essential 11.5
2010-10-18 18:00:30 startup archives unpack
2010-10-18 18:00:30 install module-assistant <none> 0.11.3ubuntu1
2010-10-18 18:00:30 status half-installed module-assistant 0.11.3ubuntu1
2010-10-18 18:00:30 status triggers-pending man-db 2.5.7-4
2010-10-18 18:00:30 status half-installed module-assistant 0.11.3ubuntu1
2010-10-18 18:00:30 status unpacked module-assistant 0.11.3ubuntu1
2010-10-18 18:00:30 status unpacked module-assistant 0.11.3ubuntu1
2010-10-18 18:00:31 trigproc man-db 2.5.7-4 2.5.7-4
2010-10-18 18:00:31 status half-configured man-db 2.5.7-4
2010-10-18 18:00:31 status installed man-db 2.5.7-4
2010-10-18 18:00:32 startup packages configure
2010-10-18 18:00:32 configure module-assistant 0.11.3ubuntu1 0.11.3ubuntu1
2010-10-18 18:00:32 status unpacked module-assistant 0.11.3ubuntu1
2010-10-18 18:00:32 status unpacked module-assistant 0.11.3ubuntu1
2010-10-18 18:00:32 status half-configured module-assistant 0.11.3ubuntu1
2010-10-18 18:00:32 status installed module-assistant 0.11.3ubuntu1
2010-10-18 18:00:36 startup archives unpack
2010-10-18 18:00:37 install xmlto <none> 0.0.23-2
2010-10-18 18:00:37 status half-installed xmlto 0.0.23-2
2010-10-18 18:00:37 status triggers-pending man-db 2.5.7-4
2010-10-18 18:00:37 status half-installed xmlto 0.0.23-2
2010-10-18 18:00:37 status unpacked xmlto 0.0.23-2
2010-10-18 18:00:37 status unpacked xmlto 0.0.23-2
2010-10-18 18:00:37 trigproc man-db 2.5.7-4 2.5.7-4
2010-10-18 18:00:37 status half-configured man-db 2.5.7-4
2010-10-18 18:00:38 status installed man-db 2.5.7-4
2010-10-18 18:00:39 startup packages configure
2010-10-18 18:00:39 configure xmlto 0.0.23-2 0.0.23-2
2010-10-18 18:00:39 status unpacked xmlto 0.0.23-2
2010-10-18 18:00:39 status half-configured xmlto 0.0.23-2
2010-10-18 18:00:39 status installed xmlto 0.0.23-2
2010-10-18 18:04:19 startup archives unpack
2010-10-18 18:04:19 install html2text <none> 1.3.2a-15
2010-10-18 18:04:19 status half-installed html2text 1.3.2a-15
2010-10-18 18:04:19 status triggers-pending man-db 2.5.7-4
2010-10-18 18:04:19 status half-installed html2text 1.3.2a-15
2010-10-18 18:04:19 status unpacked html2text 1.3.2a-15
2010-10-18 18:04:19 status unpacked html2text 1.3.2a-15
2010-10-18 18:04:20 install libunistring0 <none> 0.9.3-1
2010-10-18 18:04:20 status half-installed libunistring0 0.9.3-1
2010-10-18 18:04:20 status unpacked libunistring0 0.9.3-1
2010-10-18 18:04:20 status unpacked libunistring0 0.9.3-1
2010-10-18 18:04:20 install gettext <none> 0.18.1.1-1ubuntu2
2010-10-18 18:04:20 status half-installed gettext 0.18.1.1-1ubuntu2
2010-10-18 18:04:20 status half-installed gettext 0.18.1.1-1ubuntu2
2010-10-18 18:04:21 status triggers-pending install-info 4.13a.dfsg.1-5ubuntu1
2010-10-18 18:04:21 status half-installed gettext 0.18.1.1-1ubuntu2
2010-10-18 18:04:21 status unpacked gettext 0.18.1.1-1ubuntu2
2010-10-18 18:04:21 status unpacked gettext 0.18.1.1-1ubuntu2
2010-10-18 18:04:21 install intltool-debian <none> 0.35.0+20060710.1
2010-10-18 18:04:21 status half-installed intltool-debian 0.35.0+20060710.1
2010-10-18 18:04:22 status unpacked intltool-debian 0.35.0+20060710.1
2010-10-18 18:04:22 status unpacked intltool-debian 0.35.0+20060710.1
2010-10-18 18:04:22 install po-debconf <none> 1.0.16
2010-10-18 18:04:22 status half-installed po-debconf 1.0.16
2010-10-18 18:04:22 status triggers-pending doc-base 0.9.5
2010-10-18 18:04:22 status half-installed po-debconf 1.0.16
2010-10-18 18:04:22 status half-installed po-debconf 1.0.16
2010-10-18 18:04:23 status unpacked po-debconf 1.0.16
2010-10-18 18:04:23 status unpacked po-debconf 1.0.16
2010-10-18 18:04:23 install debhelper <none> 8.0.0ubuntu1
2010-10-18 18:04:23 status half-installed debhelper 8.0.0ubuntu1
2010-10-18 18:04:24 status half-installed debhelper 8.0.0ubuntu1
2010-10-18 18:04:24 status unpacked debhelper 8.0.0ubuntu1
2010-10-18 18:04:24 status unpacked debhelper 8.0.0ubuntu1
2010-10-18 18:04:24 install debconf-utils <none> 1.5.32ubuntu3
2010-10-18 18:04:24 status half-installed debconf-utils 1.5.32ubuntu3
2010-10-18 18:04:24 status half-installed debconf-utils 1.5.32ubuntu3
2010-10-18 18:04:25 status unpacked debconf-utils 1.5.32ubuntu3
2010-10-18 18:04:25 status unpacked debconf-utils 1.5.32ubuntu3
2010-10-18 18:04:25 install alsa-source <none> 1.0.23+dfsg-1ubuntu4
2010-10-18 18:04:25 status half-installed alsa-source 1.0.23+dfsg-1ubuntu4
2010-10-18 18:04:26 status unpacked alsa-source 1.0.23+dfsg-1ubuntu4
2010-10-18 18:04:26 status unpacked alsa-source 1.0.23+dfsg-1ubuntu4
2010-10-18 18:04:26 install libsys-hostname-long-perl <none> 1.4-2
2010-10-18 18:04:26 status half-installed libsys-hostname-long-perl 1.4-2
2010-10-18 18:04:26 status half-installed libsys-hostname-long-perl 1.4-2
2010-10-18 18:04:27 status unpacked libsys-hostname-long-perl 1.4-2
2010-10-18 18:04:27 status unpacked libsys-hostname-long-perl 1.4-2
2010-10-18 18:04:27 install libmail-sendmail-perl <none> 0.79.16-1
2010-10-18 18:04:27 status half-installed libmail-sendmail-perl 0.79.16-1
2010-10-18 18:04:27 status half-installed libmail-sendmail-perl 0.79.16-1
2010-10-18 18:04:27 status unpacked libmail-sendmail-perl 0.79.16-1
2010-10-18 18:04:27 status unpacked libmail-sendmail-perl 0.79.16-1
2010-10-18 18:04:27 trigproc man-db 2.5.7-4 2.5.7-4
2010-10-18 18:04:27 status half-configured man-db 2.5.7-4
2010-10-18 18:04:29 status installed man-db 2.5.7-4
2010-10-18 18:04:29 trigproc install-info 4.13a.dfsg.1-5ubuntu1 4.13a.dfsg.1-5ubuntu1
2010-10-18 18:04:29 status half-configured install-info 4.13a.dfsg.1-5ubuntu1
2010-10-18 18:04:30 status installed install-info 4.13a.dfsg.1-5ubuntu1
2010-10-18 18:04:30 trigproc doc-base 0.9.5 0.9.5
2010-10-18 18:04:30 status half-configured doc-base 0.9.5
2010-10-18 18:04:30 status installed doc-base 0.9.5
2010-10-18 18:04:31 startup packages configure
2010-10-18 18:04:31 configure html2text 1.3.2a-15 1.3.2a-15
2010-10-18 18:04:31 status unpacked html2text 1.3.2a-15
2010-10-18 18:04:31 status half-configured html2text 1.3.2a-15
2010-10-18 18:04:31 status installed html2text 1.3.2a-15
2010-10-18 18:04:31 configure libunistring0 0.9.3-1 0.9.3-1
2010-10-18 18:04:31 status unpacked libunistring0 0.9.3-1
2010-10-18 18:04:31 status half-configured libunistring0 0.9.3-1
2010-10-18 18:04:32 status installed libunistring0 0.9.3-1
2010-10-18 18:04:32 status triggers-pending libc-bin 2.12.1-0ubuntu6
2010-10-18 18:04:32 configure gettext 0.18.1.1-1ubuntu2 0.18.1.1-1ubuntu2
2010-10-18 18:04:32 status unpacked gettext 0.18.1.1-1ubuntu2
2010-10-18 18:04:32 status half-configured gettext 0.18.1.1-1ubuntu2
2010-10-18 18:04:32 status installed gettext 0.18.1.1-1ubuntu2
2010-10-18 18:04:33 configure intltool-debian 0.35.0+20060710.1 0.35.0+20060710.1
2010-10-18 18:04:33 status unpacked intltool-debian 0.35.0+20060710.1
2010-10-18 18:04:33 status half-configured intltool-debian 0.35.0+20060710.1
2010-10-18 18:04:33 status installed intltool-debian 0.35.0+20060710.1
2010-10-18 18:04:33 configure po-debconf 1.0.16 1.0.16
2010-10-18 18:04:33 status unpacked po-debconf 1.0.16
2010-10-18 18:04:33 status half-configured po-debconf 1.0.16
2010-10-18 18:04:33 status installed po-debconf 1.0.16
2010-10-18 18:04:33 configure debhelper 8.0.0ubuntu1 8.0.0ubuntu1
2010-10-18 18:04:33 status unpacked debhelper 8.0.0ubuntu1
2010-10-18 18:04:33 status half-configured debhelper 8.0.0ubuntu1
2010-10-18 18:04:33 status installed debhelper 8.0.0ubuntu1
2010-10-18 18:04:33 configure debconf-utils 1.5.32ubuntu3 1.5.32ubuntu3
2010-10-18 18:04:33 status unpacked debconf-utils 1.5.32ubuntu3
2010-10-18 18:04:34 status half-configured debconf-utils 1.5.32ubuntu3
2010-10-18 18:04:34 status installed debconf-utils 1.5.32ubuntu3
2010-10-18 18:04:34 configure alsa-source 1.0.23+dfsg-1ubuntu4 1.0.23+dfsg-1ubuntu4
2010-10-18 18:04:34 status unpacked alsa-source 1.0.23+dfsg-1ubuntu4
2010-10-18 18:04:34 status half-configured alsa-source 1.0.23+dfsg-1ubuntu4
2010-10-18 18:04:34 status installed alsa-source 1.0.23+dfsg-1ubuntu4
2010-10-18 18:04:34 configure libsys-hostname-long-perl 1.4-2 1.4-2
2010-10-18 18:04:34 status unpacked libsys-hostname-long-perl 1.4-2
2010-10-18 18:04:34 status half-configured libsys-hostname-long-perl 1.4-2
2010-10-18 18:04:34 status installed libsys-hostname-long-perl 1.4-2
2010-10-18 18:04:34 configure libmail-sendmail-perl 0.79.16-1 0.79.16-1
2010-10-18 18:04:34 status unpacked libmail-sendmail-perl 0.79.16-1
2010-10-18 18:04:34 status half-configured libmail-sendmail-perl 0.79.16-1
2010-10-18 18:04:34 status installed libmail-sendmail-perl 0.79.16-1
2010-10-18 18:04:34 trigproc libc-bin 2.12.1-0ubuntu6 2.12.1-0ubuntu6
2010-10-18 18:04:34 status half-configured libc-bin 2.12.1-0ubuntu6
2010-10-18 18:04:35 status installed libc-bin 2.12.1-0ubuntu6
2010-10-18 18:08:31 startup archives unpack
2010-10-18 18:08:32 install zlib1g-dev <none> 1:1.2.3.4.dfsg-3ubuntu1
2010-10-18 18:08:32 status half-installed zlib1g-dev 1:1.2.3.4.dfsg-3ubuntu1
2010-10-18 18:08:32 status triggers-pending man-db 2.5.7-4
2010-10-18 18:08:32 status half-installed zlib1g-dev 1:1.2.3.4.dfsg-3ubuntu1
2010-10-18 18:08:32 status unpacked zlib1g-dev 1:1.2.3.4.dfsg-3ubuntu1
2010-10-18 18:08:32 status unpacked zlib1g-dev 1:1.2.3.4.dfsg-3ubuntu1
2010-10-18 18:08:32 install libssl-dev <none> 0.9.8o-1ubuntu4.1
2010-10-18 18:08:32 status half-installed libssl-dev 0.9.8o-1ubuntu4.1
2010-10-18 18:08:32 status half-installed libssl-dev 0.9.8o-1ubuntu4.1
2010-10-18 18:08:33 status unpacked libssl-dev 0.9.8o-1ubuntu4.1
2010-10-18 18:08:33 status unpacked libssl-dev 0.9.8o-1ubuntu4.1
2010-10-18 18:08:33 install python2.6-dev <none> 2.6.6-5ubuntu1
2010-10-18 18:08:33 status half-installed python2.6-dev 2.6.6-5ubuntu1
2010-10-18 18:08:34 status unpacked python2.6-dev 2.6.6-5ubuntu1
2010-10-18 18:08:34 status unpacked python2.6-dev 2.6.6-5ubuntu1
2010-10-18 18:08:34 install python-dev <none> 2.6.6-2ubuntu1
2010-10-18 18:08:34 status half-installed python-dev 2.6.6-2ubuntu1
2010-10-18 18:08:34 status unpacked python-dev 2.6.6-2ubuntu1
2010-10-18 18:08:34 status unpacked python-dev 2.6.6-2ubuntu1
2010-10-18 18:08:34 trigproc man-db 2.5.7-4 2.5.7-4
2010-10-18 18:08:34 status half-configured man-db 2.5.7-4
2010-10-18 18:08:36 status installed man-db 2.5.7-4
2010-10-18 18:08:36 startup packages configure
2010-10-18 18:08:36 configure zlib1g-dev 1:1.2.3.4.dfsg-3ubuntu1 1:1.2.3.4.dfsg-3ubuntu1
2010-10-18 18:08:36 status unpacked zlib1g-dev 1:1.2.3.4.dfsg-3ubuntu1
2010-10-18 18:08:36 status half-configured zlib1g-dev 1:1.2.3.4.dfsg-3ubuntu1
2010-10-18 18:08:36 status installed zlib1g-dev 1:1.2.3.4.dfsg-3ubuntu1
2010-10-18 18:08:37 configure libssl-dev 0.9.8o-1ubuntu4.1 0.9.8o-1ubuntu4.1
2010-10-18 18:08:37 status unpacked libssl-dev 0.9.8o-1ubuntu4.1
2010-10-18 18:08:37 status half-configured libssl-dev 0.9.8o-1ubuntu4.1
2010-10-18 18:08:37 status installed libssl-dev 0.9.8o-1ubuntu4.1
2010-10-18 18:08:37 configure python2.6-dev 2.6.6-5ubuntu1 2.6.6-5ubuntu1
2010-10-18 18:08:37 status unpacked python2.6-dev 2.6.6-5ubuntu1
2010-10-18 18:08:37 status half-configured python2.6-dev 2.6.6-5ubuntu1
2010-10-18 18:08:37 status installed python2.6-dev 2.6.6-5ubuntu1
2010-10-18 18:08:37 configure python-dev 2.6.6-2ubuntu1 2.6.6-2ubuntu1
2010-10-18 18:08:37 status unpacked python-dev 2.6.6-2ubuntu1
2010-10-18 18:08:37 status half-configured python-dev 2.6.6-2ubuntu1
2010-10-18 18:08:37 status installed python-dev 2.6.6-2ubuntu1
2010-10-18 18:08:56 startup archives unpack
2010-10-18 18:08:56 install libasound2-dev <none> 1.0.23-1ubuntu2
2010-10-18 18:08:56 status half-installed libasound2-dev 1.0.23-1ubuntu2
2010-10-18 18:08:57 status unpacked libasound2-dev 1.0.23-1ubuntu2
2010-10-18 18:08:57 status unpacked libasound2-dev 1.0.23-1ubuntu2
2010-10-18 18:08:58 startup packages configure
2010-10-18 18:08:58 configure libasound2-dev 1.0.23-1ubuntu2 1.0.23-1ubuntu2
2010-10-18 18:08:58 status unpacked libasound2-dev 1.0.23-1ubuntu2
2010-10-18 18:08:58 status half-configured libasound2-dev 1.0.23-1ubuntu2
2010-10-18 18:08:58 status installed libasound2-dev 1.0.23-1ubuntu2
2010-10-18 18:09:02 startup archives unpack
2010-10-18 18:09:02 install libsysfs-dev <none> 2.1.0+repack-1
2010-10-18 18:09:02 status half-installed libsysfs-dev 2.1.0+repack-1
2010-10-18 18:09:02 status triggers-pending doc-base 0.9.5
2010-10-18 18:09:02 status half-installed libsysfs-dev 2.1.0+repack-1
2010-10-18 18:09:02 status unpacked libsysfs-dev 2.1.0+repack-1
2010-10-18 18:09:02 status unpacked libsysfs-dev 2.1.0+repack-1
2010-10-18 18:09:03 trigproc doc-base 0.9.5 0.9.5
2010-10-18 18:09:03 status half-configured doc-base 0.9.5
2010-10-18 18:09:03 status installed doc-base 0.9.5
2010-10-18 18:09:04 startup packages configure
2010-10-18 18:09:04 configure libsysfs-dev 2.1.0+repack-1 2.1.0+repack-1
2010-10-18 18:09:04 status unpacked libsysfs-dev 2.1.0+repack-1
2010-10-18 18:09:04 status half-configured libsysfs-dev 2.1.0+repack-1
2010-10-18 18:09:04 status installed libsysfs-dev 2.1.0+repack-1
2010-10-18 18:10:05 startup archives unpack
2010-10-18 18:10:06 install libncurses5-dev <none> 5.7+20100626-0ubuntu1
2010-10-18 18:10:06 status half-installed libncurses5-dev 5.7+20100626-0ubuntu1
2010-10-18 18:10:06 status triggers-pending man-db 2.5.7-4
2010-10-18 18:10:06 status half-installed libncurses5-dev 5.7+20100626-0ubuntu1
2010-10-18 18:10:06 status unpacked libncurses5-dev 5.7+20100626-0ubuntu1
2010-10-18 18:10:07 status unpacked libncurses5-dev 5.7+20100626-0ubuntu1
2010-10-18 18:10:07 trigproc man-db 2.5.7-4 2.5.7-4
2010-10-18 18:10:07 status half-configured man-db 2.5.7-4
2010-10-18 18:10:07 status installed man-db 2.5.7-4
2010-10-18 18:10:08 startup packages configure
2010-10-18 18:10:08 configure libncurses5-dev 5.7+20100626-0ubuntu1 5.7+20100626-0ubuntu1
2010-10-18 18:10:08 status unpacked libncurses5-dev 5.7+20100626-0ubuntu1
2010-10-18 18:10:08 status half-configured libncurses5-dev 5.7+20100626-0ubuntu1
2010-10-18 18:10:08 status installed libncurses5-dev 5.7+20100626-0ubuntu1
2010-10-18 18:10:30 startup archives unpack
2010-10-18 18:10:30 install libncursesw5-dev <none> 5.7+20100626-0ubuntu1
2010-10-18 18:10:30 status half-installed libncursesw5-dev 5.7+20100626-0ubuntu1
2010-10-18 18:10:31 status unpacked libncursesw5-dev 5.7+20100626-0ubuntu1
2010-10-18 18:10:31 status unpacked libncursesw5-dev 5.7+20100626-0ubuntu1
2010-10-18 18:10:32 startup packages configure
2010-10-18 18:10:32 configure libncursesw5-dev 5.7+20100626-0ubuntu1 5.7+20100626-0ubuntu1
2010-10-18 18:10:32 status unpacked libncursesw5-dev 5.7+20100626-0ubuntu1
2010-10-18 18:10:32 status half-configured libncursesw5-dev 5.7+20100626-0ubuntu1
2010-10-18 18:10:32 status installed libncursesw5-dev 5.7+20100626-0ubuntu1
2010-10-18 18:14:10 startup archives unpack
2010-10-18 18:14:10 install x11proto-core-dev <none> 7.0.17-1
2010-10-18 18:14:10 status half-installed x11proto-core-dev 7.0.17-1
2010-10-18 18:14:11 status unpacked x11proto-core-dev 7.0.17-1
2010-10-18 18:14:11 status unpacked x11proto-core-dev 7.0.17-1
2010-10-18 18:14:11 install libice-dev <none> 2:1.0.6-1
2010-10-18 18:14:11 status half-installed libice-dev 2:1.0.6-1
2010-10-18 18:14:11 status unpacked libice-dev 2:1.0.6-1
2010-10-18 18:14:11 status unpacked libice-dev 2:1.0.6-1
2010-10-18 18:14:11 install libxau-dev <none> 1:1.0.6-1
2010-10-18 18:14:11 status half-installed libxau-dev 1:1.0.6-1
2010-10-18 18:14:11 status triggers-pending man-db 2.5.7-4
2010-10-18 18:14:11 status half-installed libxau-dev 1:1.0.6-1
2010-10-18 18:14:12 status unpacked libxau-dev 1:1.0.6-1
2010-10-18 18:14:12 status unpacked libxau-dev 1:1.0.6-1
2010-10-18 18:14:12 install libxdmcp-dev <none> 1:1.0.3-2
2010-10-18 18:14:12 status half-installed libxdmcp-dev 1:1.0.3-2
2010-10-18 18:14:12 status unpacked libxdmcp-dev 1:1.0.3-2
2010-10-18 18:14:12 status unpacked libxdmcp-dev 1:1.0.3-2
2010-10-18 18:14:13 install x11proto-input-dev <none> 2.0-2
2010-10-18 18:14:13 status half-installed x11proto-input-dev 2.0-2
2010-10-18 18:14:13 status unpacked x11proto-input-dev 2.0-2
2010-10-18 18:14:13 status unpacked x11proto-input-dev 2.0-2
2010-10-18 18:14:13 install x11proto-kb-dev <none> 1.0.4-1
2010-10-18 18:14:13 status half-installed x11proto-kb-dev 1.0.4-1
2010-10-18 18:14:13 status unpacked x11proto-kb-dev 1.0.4-1
2010-10-18 18:14:13 status unpacked x11proto-kb-dev 1.0.4-1
2010-10-18 18:14:14 install xtrans-dev <none> 1.2.5-1
2010-10-18 18:14:14 status half-installed xtrans-dev 1.2.5-1
2010-10-18 18:14:15 status unpacked xtrans-dev 1.2.5-1
2010-10-18 18:14:15 status unpacked xtrans-dev 1.2.5-1
2010-10-18 18:14:15 install libpthread-stubs0 <none> 0.3-2
2010-10-18 18:14:15 status half-installed libpthread-stubs0 0.3-2
2010-10-18 18:14:15 status unpacked libpthread-stubs0 0.3-2
2010-10-18 18:14:15 status unpacked libpthread-stubs0 0.3-2
2010-10-18 18:14:15 install libpthread-stubs0-dev <none> 0.3-2
2010-10-18 18:14:15 status half-installed libpthread-stubs0-dev 0.3-2
2010-10-18 18:14:16 status unpacked libpthread-stubs0-dev 0.3-2
2010-10-18 18:14:16 status unpacked libpthread-stubs0-dev 0.3-2
2010-10-18 18:14:16 install libxcb1-dev <none> 1.6-1
2010-10-18 18:14:16 status half-installed libxcb1-dev 1.6-1
2010-10-18 18:14:17 status unpacked libxcb1-dev 1.6-1
2010-10-18 18:14:17 status unpacked libxcb1-dev 1.6-1
2010-10-18 18:14:17 install libx11-dev <none> 2:1.3.3-3ubuntu1
2010-10-18 18:14:17 status half-installed libx11-dev 2:1.3.3-3ubuntu1
2010-10-18 18:14:17 status half-installed libx11-dev 2:1.3.3-3ubuntu1
2010-10-18 18:14:18 status unpacked libx11-dev 2:1.3.3-3ubuntu1
2010-10-18 18:14:18 status unpacked libx11-dev 2:1.3.3-3ubuntu1
2010-10-18 18:14:18 install libavahi-common-dev <none> 0.6.27-2ubuntu3
2010-10-18 18:14:18 status half-installed libavahi-common-dev 0.6.27-2ubuntu3
2010-10-18 18:14:18 status unpacked libavahi-common-dev 0.6.27-2ubuntu3
2010-10-18 18:14:19 status unpacked libavahi-common-dev 0.6.27-2ubuntu3
2010-10-18 18:14:19 install libdbus-1-dev <none> 1.4.0-0ubuntu1
2010-10-18 18:14:19 status half-installed libdbus-1-dev 1.4.0-0ubuntu1
2010-10-18 18:14:19 status unpacked libdbus-1-dev 1.4.0-0ubuntu1
2010-10-18 18:14:19 status unpacked libdbus-1-dev 1.4.0-0ubuntu1
2010-10-18 18:14:19 install libavahi-client-dev <none> 0.6.27-2ubuntu3
2010-10-18 18:14:19 status half-installed libavahi-client-dev 0.6.27-2ubuntu3
2010-10-18 18:14:20 status unpacked libavahi-client-dev 0.6.27-2ubuntu3
2010-10-18 18:14:20 status unpacked libavahi-client-dev 0.6.27-2ubuntu3
2010-10-18 18:14:20 install libglib2.0-bin <none> 2.26.0-0ubuntu1
2010-10-18 18:14:20 status half-installed libglib2.0-bin 2.26.0-0ubuntu1
2010-10-18 18:14:20 status half-installed libglib2.0-bin 2.26.0-0ubuntu1
2010-10-18 18:14:20 status unpacked libglib2.0-bin 2.26.0-0ubuntu1
2010-10-18 18:14:20 status unpacked libglib2.0-bin 2.26.0-0ubuntu1
2010-10-18 18:14:20 install libglib2.0-dev <none> 2.26.0-0ubuntu1
2010-10-18 18:14:20 status half-installed libglib2.0-dev 2.26.0-0ubuntu1
2010-10-18 18:14:21 status triggers-pending libglib2.0-0 2.26.0-0ubuntu1
2010-10-18 18:14:21 status half-installed libglib2.0-dev 2.26.0-0ubuntu1
2010-10-18 18:14:21 status half-installed libglib2.0-dev 2.26.0-0ubuntu1
2010-10-18 18:14:21 status unpacked libglib2.0-dev 2.26.0-0ubuntu1
2010-10-18 18:14:21 status unpacked libglib2.0-dev 2.26.0-0ubuntu1
2010-10-18 18:14:21 install libsm-dev <none> 2:1.1.1-1
2010-10-18 18:14:21 status half-installed libsm-dev 2:1.1.1-1
2010-10-18 18:14:23 status unpacked libsm-dev 2:1.1.1-1
2010-10-18 18:14:23 status unpacked libsm-dev 2:1.1.1-1
2010-10-18 18:14:23 install libxt-dev <none> 1:1.0.7-1
2010-10-18 18:14:23 status half-installed libxt-dev 1:1.0.7-1
2010-10-18 18:14:23 status half-installed libxt-dev 1:1.0.7-1
2010-10-18 18:14:24 status unpacked libxt-dev 1:1.0.7-1
2010-10-18 18:14:24 status unpacked libxt-dev 1:1.0.7-1
2010-10-18 18:14:24 install libpulse-dev <none> 1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu21
2010-10-18 18:14:24 status half-installed libpulse-dev 1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu21
2010-10-18 18:14:24 status unpacked libpulse-dev 1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu21
2010-10-18 18:14:24 status unpacked libpulse-dev 1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu21
2010-10-18 18:14:24 trigproc man-db 2.5.7-4 2.5.7-4
2010-10-18 18:14:24 status half-configured man-db 2.5.7-4
2010-10-18 18:14:26 status installed man-db 2.5.7-4
2010-10-18 18:14:26 trigproc libglib2.0-0 2.26.0-0ubuntu1 2.26.0-0ubuntu1
2010-10-18 18:14:26 status half-configured libglib2.0-0 2.26.0-0ubuntu1
2010-10-18 18:14:26 status installed libglib2.0-0 2.26.0-0ubuntu1
2010-10-18 18:14:27 startup packages configure
2010-10-18 18:14:27 configure x11proto-core-dev 7.0.17-1 7.0.17-1
2010-10-18 18:14:27 status unpacked x11proto-core-dev 7.0.17-1
2010-10-18 18:14:27 status half-configured x11proto-core-dev 7.0.17-1
2010-10-18 18:14:27 status installed x11proto-core-dev 7.0.17-1
2010-10-18 18:14:27 configure libice-dev 2:1.0.6-1 2:1.0.6-1
2010-10-18 18:14:27 status unpacked libice-dev 2:1.0.6-1
2010-10-18 18:14:27 status half-configured libice-dev 2:1.0.6-1
2010-10-18 18:14:27 status installed libice-dev 2:1.0.6-1
2010-10-18 18:14:27 configure libxau-dev 1:1.0.6-1 1:1.0.6-1
2010-10-18 18:14:27 status unpacked libxau-dev 1:1.0.6-1
2010-10-18 18:14:27 status half-configured libxau-dev 1:1.0.6-1
2010-10-18 18:14:27 status installed libxau-dev 1:1.0.6-1
2010-10-18 18:14:27 configure libxdmcp-dev 1:1.0.3-2 1:1.0.3-2
2010-10-18 18:14:27 status unpacked libxdmcp-dev 1:1.0.3-2
2010-10-18 18:14:28 status half-configured libxdmcp-dev 1:1.0.3-2
2010-10-18 18:14:28 status installed libxdmcp-dev 1:1.0.3-2
2010-10-18 18:14:28 configure x11proto-input-dev 2.0-2 2.0-2
2010-10-18 18:14:28 status unpacked x11proto-input-dev 2.0-2
2010-10-18 18:14:28 status half-configured x11proto-input-dev 2.0-2
2010-10-18 18:14:28 status installed x11proto-input-dev 2.0-2
2010-10-18 18:14:28 configure x11proto-kb-dev 1.0.4-1 1.0.4-1
2010-10-18 18:14:28 status unpacked x11proto-kb-dev 1.0.4-1
2010-10-18 18:14:28 status half-configured x11proto-kb-dev 1.0.4-1
2010-10-18 18:14:28 status installed x11proto-kb-dev 1.0.4-1
2010-10-18 18:14:28 configure xtrans-dev 1.2.5-1 1.2.5-1
2010-10-18 18:14:28 status unpacked xtrans-dev 1.2.5-1
2010-10-18 18:14:28 status half-configured xtrans-dev 1.2.5-1
2010-10-18 18:14:28 status installed xtrans-dev 1.2.5-1
2010-10-18 18:14:29 configure libpthread-stubs0 0.3-2 0.3-2
2010-10-18 18:14:29 status unpacked libpthread-stubs0 0.3-2
2010-10-18 18:14:29 status half-configured libpthread-stubs0 0.3-2
2010-10-18 18:14:29 status installed libpthread-stubs0 0.3-2
2010-10-18 18:14:29 configure libpthread-stubs0-dev 0.3-2 0.3-2
2010-10-18 18:14:29 status unpacked libpthread-stubs0-dev 0.3-2
2010-10-18 18:14:29 status half-configured libpthread-stubs0-dev 0.3-2
2010-10-18 18:14:29 status installed libpthread-stubs0-dev 0.3-2
2010-10-18 18:14:29 configure libxcb1-dev 1.6-1 1.6-1
2010-10-18 18:14:29 status unpacked libxcb1-dev 1.6-1
2010-10-18 18:14:29 status half-configured libxcb1-dev 1.6-1
2010-10-18 18:14:30 status installed libxcb1-dev 1.6-1
2010-10-18 18:14:30 configure libx11-dev 2:1.3.3-3ubuntu1 2:1.3.3-3ubuntu1
2010-10-18 18:14:30 status unpacked libx11-dev 2:1.3.3-3ubuntu1
2010-10-18 18:14:30 status half-configured libx11-dev 2:1.3.3-3ubuntu1
2010-10-18 18:14:30 status installed libx11-dev 2:1.3.3-3ubuntu1
2010-10-18 18:14:30 configure libavahi-common-dev 0.6.27-2ubuntu3 0.6.27-2ubuntu3
2010-10-18 18:14:30 status unpacked libavahi-common-dev 0.6.27-2ubuntu3
2010-10-18 18:14:30 status half-configured libavahi-common-dev 0.6.27-2ubuntu3
2010-10-18 18:14:30 status installed libavahi-common-dev 0.6.27-2ubuntu3
2010-10-18 18:14:30 configure libdbus-1-dev 1.4.0-0ubuntu1 1.4.0-0ubuntu1
2010-10-18 18:14:30 status unpacked libdbus-1-dev 1.4.0-0ubuntu1
2010-10-18 18:14:30 status half-configured libdbus-1-dev 1.4.0-0ubuntu1
2010-10-18 18:14:30 status installed libdbus-1-dev 1.4.0-0ubuntu1
2010-10-18 18:14:30 configure libavahi-client-dev 0.6.27-2ubuntu3 0.6.27-2ubuntu3
2010-10-18 18:14:30 status unpacked libavahi-client-dev 0.6.27-2ubuntu3
2010-10-18 18:14:30 status half-configured libavahi-client-dev 0.6.27-2ubuntu3
2010-10-18 18:14:30 status installed libavahi-client-dev 0.6.27-2ubuntu3
2010-10-18 18:14:30 configure libglib2.0-bin 2.26.0-0ubuntu1 2.26.0-0ubuntu1
2010-10-18 18:14:30 status unpacked libglib2.0-bin 2.26.0-0ubuntu1
2010-10-18 18:14:31 status half-configured libglib2.0-bin 2.26.0-0ubuntu1
2010-10-18 18:14:31 status installed libglib2.0-bin 2.26.0-0ubuntu1
2010-10-18 18:14:31 configure libglib2.0-dev 2.26.0-0ubuntu1 2.26.0-0ubuntu1
2010-10-18 18:14:31 status unpacked libglib2.0-dev 2.26.0-0ubuntu1
2010-10-18 18:14:31 status half-configured libglib2.0-dev 2.26.0-0ubuntu1
2010-10-18 18:14:31 status installed libglib2.0-dev 2.26.0-0ubuntu1
2010-10-18 18:14:31 configure libsm-dev 2:1.1.1-1 2:1.1.1-1
2010-10-18 18:14:31 status unpacked libsm-dev 2:1.1.1-1
2010-10-18 18:14:31 status half-configured libsm-dev 2:1.1.1-1
2010-10-18 18:14:31 status installed libsm-dev 2:1.1.1-1
2010-10-18 18:14:31 configure libxt-dev 1:1.0.7-1 1:1.0.7-1
2010-10-18 18:14:31 status unpacked libxt-dev 1:1.0.7-1
2010-10-18 18:14:31 status half-configured libxt-dev 1:1.0.7-1
2010-10-18 18:14:31 status installed libxt-dev 1:1.0.7-1
2010-10-18 18:14:31 configure libpulse-dev 1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu21 1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu21
2010-10-18 18:14:31 status unpacked libpulse-dev 1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu21
2010-10-18 18:14:31 status half-configured libpulse-dev 1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu21
2010-10-18 18:14:31 status installed libpulse-dev 1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu21
2010-10-18 18:14:37 startup archives unpack
2010-10-18 18:14:37 install libspeex-dev <none> 1.2~rc1-1ubuntu1
2010-10-18 18:14:37 status half-installed libspeex-dev 1.2~rc1-1ubuntu1
2010-10-18 18:14:37 status unpacked libspeex-dev 1.2~rc1-1ubuntu1
2010-10-18 18:14:37 status unpacked libspeex-dev 1.2~rc1-1ubuntu1
2010-10-18 18:14:38 startup packages configure
2010-10-18 18:14:38 configure libspeex-dev 1.2~rc1-1ubuntu1 1.2~rc1-1ubuntu1
2010-10-18 18:14:38 status unpacked libspeex-dev 1.2~rc1-1ubuntu1
2010-10-18 18:14:38 status half-configured libspeex-dev 1.2~rc1-1ubuntu1
2010-10-18 18:14:38 status installed libspeex-dev 1.2~rc1-1ubuntu1
2010-10-18 18:16:26 startup archives unpack
2010-10-18 18:16:26 install libavutil-dev <none> 4:0.6-2ubuntu6
2010-10-18 18:16:26 status half-installed libavutil-dev 4:0.6-2ubuntu6
2010-10-18 18:16:27 status unpacked libavutil-dev 4:0.6-2ubuntu6
2010-10-18 18:16:27 status unpacked libavutil-dev 4:0.6-2ubuntu6
2010-10-18 18:16:27 install libavcodec-dev <none> 4:0.6-2ubuntu6
2010-10-18 18:16:27 status half-installed libavcodec-dev 4:0.6-2ubuntu6
2010-10-18 18:16:27 status unpacked libavcodec-dev 4:0.6-2ubuntu6
2010-10-18 18:16:27 status unpacked libavcodec-dev 4:0.6-2ubuntu6
2010-10-18 18:16:28 startup packages configure
2010-10-18 18:16:28 configure libavutil-dev 4:0.6-2ubuntu6 4:0.6-2ubuntu6
2010-10-18 18:16:28 status unpacked libavutil-dev 4:0.6-2ubuntu6
2010-10-18 18:16:28 status half-configured libavutil-dev 4:0.6-2ubuntu6
2010-10-18 18:16:28 status installed libavutil-dev 4:0.6-2ubuntu6
2010-10-18 18:16:28 configure libavcodec-dev 4:0.6-2ubuntu6 4:0.6-2ubuntu6
2010-10-18 18:16:28 status unpacked libavcodec-dev 4:0.6-2ubuntu6
2010-10-18 18:16:28 status half-configured libavcodec-dev 4:0.6-2ubuntu6
2010-10-18 18:16:28 status installed libavcodec-dev 4:0.6-2ubuntu6
2010-10-18 18:16:50 startup archives unpack
2010-10-18 18:16:50 install libavformat-dev <none> 4:0.6-2ubuntu6
2010-10-18 18:16:50 status half-installed libavformat-dev 4:0.6-2ubuntu6
2010-10-18 18:16:51 status unpacked libavformat-dev 4:0.6-2ubuntu6
2010-10-18 18:16:51 status unpacked libavformat-dev 4:0.6-2ubuntu6
2010-10-18 18:16:51 startup packages configure
2010-10-18 18:16:51 configure libavformat-dev 4:0.6-2ubuntu6 4:0.6-2ubuntu6
2010-10-18 18:16:51 status unpacked libavformat-dev 4:0.6-2ubuntu6
2010-10-18 18:16:51 status half-configured libavformat-dev 4:0.6-2ubuntu6
2010-10-18 18:16:51 status installed libavformat-dev 4:0.6-2ubuntu6
2010-10-18 18:17:28 startup archives unpack
2010-10-18 18:17:28 install libmpeg4ip-0 <none> 1:1.6dfsg-0.2ubuntu9
2010-10-18 18:17:28 status half-installed libmpeg4ip-0 1:1.6dfsg-0.2ubuntu9
2010-10-18 18:17:29 status unpacked libmpeg4ip-0 1:1.6dfsg-0.2ubuntu9
2010-10-18 18:17:29 status unpacked libmpeg4ip-0 1:1.6dfsg-0.2ubuntu9
2010-10-18 18:17:29 install libmpeg4ip-dev <none> 1:1.6dfsg-0.2ubuntu9
2010-10-18 18:17:29 status half-installed libmpeg4ip-dev 1:1.6dfsg-0.2ubuntu9
2010-10-18 18:17:29 status unpacked libmpeg4ip-dev 1:1.6dfsg-0.2ubuntu9
2010-10-18 18:17:29 status unpacked libmpeg4ip-dev 1:1.6dfsg-0.2ubuntu9
2010-10-18 18:17:30 startup packages configure
2010-10-18 18:17:30 configure libmpeg4ip-0 1:1.6dfsg-0.2ubuntu9 1:1.6dfsg-0.2ubuntu9
2010-10-18 18:17:30 status unpacked libmpeg4ip-0 1:1.6dfsg-0.2ubuntu9
2010-10-18 18:17:30 status half-configured libmpeg4ip-0 1:1.6dfsg-0.2ubuntu9
2010-10-18 18:17:30 status installed libmpeg4ip-0 1:1.6dfsg-0.2ubuntu9
2010-10-18 18:17:30 status triggers-pending libc-bin 2.12.1-0ubuntu6
2010-10-18 18:17:30 configure libmpeg4ip-dev 1:1.6dfsg-0.2ubuntu9 1:1.6dfsg-0.2ubuntu9
2010-10-18 18:17:30 status unpacked libmpeg4ip-dev 1:1.6dfsg-0.2ubuntu9
2010-10-18 18:17:30 status half-configured libmpeg4ip-dev 1:1.6dfsg-0.2ubuntu9
2010-10-18 18:17:30 status installed libmpeg4ip-dev 1:1.6dfsg-0.2ubuntu9
2010-10-18 18:17:30 trigproc libc-bin 2.12.1-0ubuntu6 2.12.1-0ubuntu6
2010-10-18 18:17:30 status half-configured libc-bin 2.12.1-0ubuntu6
2010-10-18 18:17:31 status installed libc-bin 2.12.1-0ubuntu6
2010-10-18 18:17:36 startup archives unpack
2010-10-18 18:17:37 install liba52-0.7.4 <none> 0.7.4-14ubuntu1
2010-10-18 18:17:37 status half-installed liba52-0.7.4 0.7.4-14ubuntu1
2010-10-18 18:17:37 status unpacked liba52-0.7.4 0.7.4-14ubuntu1
2010-10-18 18:17:37 status unpacked liba52-0.7.4 0.7.4-14ubuntu1
2010-10-18 18:17:37 install liba52-0.7.4-dev <none> 0.7.4-14ubuntu1
2010-10-18 18:17:37 status half-installed liba52-0.7.4-dev 0.7.4-14ubuntu1
2010-10-18 18:17:37 status triggers-pending man-db 2.5.7-4
2010-10-18 18:17:37 status half-installed liba52-0.7.4-dev 0.7.4-14ubuntu1
2010-10-18 18:17:38 status unpacked liba52-0.7.4-dev 0.7.4-14ubuntu1
2010-10-18 18:17:38 status unpacked liba52-0.7.4-dev 0.7.4-14ubuntu1
2010-10-18 18:17:38 trigproc man-db 2.5.7-4 2.5.7-4
2010-10-18 18:17:38 status half-configured man-db 2.5.7-4
2010-10-18 18:17:38 status installed man-db 2.5.7-4
2010-10-18 18:17:39 startup packages configure
2010-10-18 18:17:39 configure liba52-0.7.4 0.7.4-14ubuntu1 0.7.4-14ubuntu1
2010-10-18 18:17:39 status unpacked liba52-0.7.4 0.7.4-14ubuntu1
2010-10-18 18:17:39 status half-configured liba52-0.7.4 0.7.4-14ubuntu1
2010-10-18 18:17:39 status installed liba52-0.7.4 0.7.4-14ubuntu1
2010-10-18 18:17:39 status triggers-pending libc-bin 2.12.1-0ubuntu6
2010-10-18 18:17:39 configure liba52-0.7.4-dev 0.7.4-14ubuntu1 0.7.4-14ubuntu1
2010-10-18 18:17:39 status unpacked liba52-0.7.4-dev 0.7.4-14ubuntu1
2010-10-18 18:17:39 status half-configured liba52-0.7.4-dev 0.7.4-14ubuntu1
2010-10-18 18:17:39 status installed liba52-0.7.4-dev 0.7.4-14ubuntu1
2010-10-18 18:17:39 trigproc libc-bin 2.12.1-0ubuntu6 2.12.1-0ubuntu6
2010-10-18 18:17:39 status half-configured libc-bin 2.12.1-0ubuntu6
2010-10-18 18:17:40 status installed libc-bin 2.12.1-0ubuntu6
2010-10-18 18:18:30 startup archives unpack
2010-10-18 18:18:30 install libsamplerate0-dev <none> 0.1.7-3
2010-10-18 18:18:30 status half-installed libsamplerate0-dev 0.1.7-3
2010-10-18 18:18:30 status triggers-pending doc-base 0.9.5
2010-10-18 18:18:30 status half-installed libsamplerate0-dev 0.1.7-3
2010-10-18 18:18:31 status unpacked libsamplerate0-dev 0.1.7-3
2010-10-18 18:18:31 status unpacked libsamplerate0-dev 0.1.7-3
2010-10-18 18:18:31 trigproc doc-base 0.9.5 0.9.5
2010-10-18 18:18:31 status half-configured doc-base 0.9.5
2010-10-18 18:18:31 status installed doc-base 0.9.5
2010-10-18 18:18:32 startup packages configure
2010-10-18 18:18:32 configure libsamplerate0-dev 0.1.7-3 0.1.7-3
2010-10-18 18:18:32 status unpacked libsamplerate0-dev 0.1.7-3
2010-10-18 18:18:32 status half-configured libsamplerate0-dev 0.1.7-3
2010-10-18 18:18:32 status installed libsamplerate0-dev 0.1.7-3
2010-10-18 18:19:11 startup archives unpack
2010-10-18 18:19:11 install libkms1 <none> 2.4.21-1ubuntu2
2010-10-18 18:19:11 status half-installed libkms1 2.4.21-1ubuntu2
2010-10-18 18:19:11 status unpacked libkms1 2.4.21-1ubuntu2
2010-10-18 18:19:11 status unpacked libkms1 2.4.21-1ubuntu2
2010-10-18 18:19:12 install libdrm-dev <none> 2.4.21-1ubuntu2
2010-10-18 18:19:12 status half-installed libdrm-dev 2.4.21-1ubuntu2
2010-10-18 18:19:12 status unpacked libdrm-dev 2.4.21-1ubuntu2
2010-10-18 18:19:12 status unpacked libdrm-dev 2.4.21-1ubuntu2
2010-10-18 18:19:12 install libfltk1.1-dev <none> 1.1.10-2
2010-10-18 18:19:12 status half-installed libfltk1.1-dev 1.1.10-2
2010-10-18 18:19:12 status triggers-pending man-db 2.5.7-4
2010-10-18 18:19:13 status half-installed libfltk1.1-dev 1.1.10-2
2010-10-18 18:19:13 status unpacked libfltk1.1-dev 1.1.10-2
2010-10-18 18:19:13 status unpacked libfltk1.1-dev 1.1.10-2
2010-10-18 18:19:13 install mesa-common-dev <none> 7.9~git20100924-0ubuntu2
2010-10-18 18:19:13 status half-installed mesa-common-dev 7.9~git20100924-0ubuntu2
2010-10-18 18:19:14 status unpacked mesa-common-dev 7.9~git20100924-0ubuntu2
2010-10-18 18:19:14 status unpacked mesa-common-dev 7.9~git20100924-0ubuntu2
2010-10-18 18:19:14 install libgl1-mesa-dev <none> 7.9~git20100924-0ubuntu2
2010-10-18 18:19:14 status half-installed libgl1-mesa-dev 7.9~git20100924-0ubuntu2
2010-10-18 18:19:14 status unpacked libgl1-mesa-dev 7.9~git20100924-0ubuntu2
2010-10-18 18:19:14 status unpacked libgl1-mesa-dev 7.9~git20100924-0ubuntu2
2010-10-18 18:19:14 trigproc man-db 2.5.7-4 2.5.7-4
2010-10-18 18:19:14 status half-configured man-db 2.5.7-4
2010-10-18 18:19:15 status installed man-db 2.5.7-4
2010-10-18 18:19:16 startup packages configure
2010-10-18 18:19:16 configure libkms1 2.4.21-1ubuntu2 2.4.21-1ubuntu2
2010-10-18 18:19:16 status unpacked libkms1 2.4.21-1ubuntu2
2010-10-18 18:19:16 status half-configured libkms1 2.4.21-1ubuntu2
2010-10-18 18:19:16 status installed libkms1 2.4.21-1ubuntu2
2010-10-18 18:19:16 status triggers-pending libc-bin 2.12.1-0ubuntu6
2010-10-18 18:19:16 configure libdrm-dev 2.4.21-1ubuntu2 2.4.21-1ubuntu2
2010-10-18 18:19:16 status unpacked libdrm-dev 2.4.21-1ubuntu2
2010-10-18 18:19:16 status half-configured libdrm-dev 2.4.21-1ubuntu2
2010-10-18 18:19:16 status installed libdrm-dev 2.4.21-1ubuntu2
2010-10-18 18:19:16 configure libfltk1.1-dev 1.1.10-2 1.1.10-2
2010-10-18 18:19:16 status unpacked libfltk1.1-dev 1.1.10-2
2010-10-18 18:19:16 status half-configured libfltk1.1-dev 1.1.10-2
2010-10-18 18:19:17 status installed libfltk1.1-dev 1.1.10-2
2010-10-18 18:19:17 configure mesa-common-dev 7.9~git20100924-0ubuntu2 7.9~git20100924-0ubuntu2
2010-10-18 18:19:17 status unpacked mesa-common-dev 7.9~git20100924-0ubuntu2
2010-10-18 18:19:17 status half-configured mesa-common-dev 7.9~git20100924-0ubuntu2
2010-10-18 18:19:17 status installed mesa-common-dev 7.9~git20100924-0ubuntu2
2010-10-18 18:19:17 configure libgl1-mesa-dev 7.9~git20100924-0ubuntu2 7.9~git20100924-0ubuntu2
2010-10-18 18:19:17 status unpacked libgl1-mesa-dev 7.9~git20100924-0ubuntu2
2010-10-18 18:19:17 status half-configured libgl1-mesa-dev 7.9~git20100924-0ubuntu2
2010-10-18 18:19:17 status installed libgl1-mesa-dev 7.9~git20100924-0ubuntu2
2010-10-18 18:19:17 trigproc libc-bin 2.12.1-0ubuntu6 2.12.1-0ubuntu6
2010-10-18 18:19:17 status half-configured libc-bin 2.12.1-0ubuntu6
2010-10-18 18:19:17 status installed libc-bin 2.12.1-0ubuntu6
2010-10-18 19:33:16 startup packages purge
2010-10-18 19:33:16 status installed alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-18 19:33:17 remove alsa-base 1.0.23+dfsg-1ubuntu4 1.0.23+dfsg-1ubuntu4
2010-10-18 19:33:17 status half-configured alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-18 19:33:17 status half-installed alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-18 19:33:18 status config-files alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-18 19:33:18 purge alsa-base 1.0.23+dfsg-1ubuntu4 1.0.23+dfsg-1ubuntu4
2010-10-18 19:33:18 status config-files alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-18 19:33:18 status config-files alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-18 19:33:18 status config-files alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-18 19:33:18 status config-files alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-18 19:33:18 status config-files alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-18 19:33:18 status not-installed alsa-base <none>
2010-10-18 19:33:18 status installed alsa-utils 1.0.23-2ubuntu3
2010-10-18 19:33:18 remove alsa-utils 1.0.23-2ubuntu3 1.0.23-2ubuntu3
2010-10-18 19:33:18 status half-configured alsa-utils 1.0.23-2ubuntu3
2010-10-18 19:33:18 status half-installed alsa-utils 1.0.23-2ubuntu3
2010-10-18 19:33:18 status triggers-pending ureadahead 0.100.0-8
2010-10-18 19:33:18 status half-installed alsa-utils 1.0.23-2ubuntu3
2010-10-18 19:33:18 status triggers-pending ureadahead 0.100.0-8
2010-10-18 19:33:18 status triggers-pending man-db 2.5.7-4
2010-10-18 19:33:19 status half-installed alsa-utils 1.0.23-2ubuntu3
2010-10-18 19:33:19 status config-files alsa-utils 1.0.23-2ubuntu3
2010-10-18 19:33:19 purge alsa-utils 1.0.23-2ubuntu3 1.0.23-2ubuntu3
2010-10-18 19:33:19 status config-files alsa-utils 1.0.23-2ubuntu3
2010-10-18 19:33:19 status config-files alsa-utils 1.0.23-2ubuntu3
2010-10-18 19:33:19 status config-files alsa-utils 1.0.23-2ubuntu3
2010-10-18 19:33:19 status config-files alsa-utils 1.0.23-2ubuntu3
2010-10-18 19:33:19 status config-files alsa-utils 1.0.23-2ubuntu3
2010-10-18 19:33:19 status config-files alsa-utils 1.0.23-2ubuntu3
2010-10-18 19:33:19 status not-installed alsa-utils <none>
2010-10-18 19:33:19 status installed linux-sound-base 1.0.23+dfsg-1ubuntu4
2010-10-18 19:33:19 remove linux-sound-base 1.0.23+dfsg-1ubuntu4 1.0.23+dfsg-1ubuntu4
2010-10-18 19:33:19 status half-configured linux-sound-base 1.0.23+dfsg-1ubuntu4
2010-10-18 19:33:19 status half-installed linux-sound-base 1.0.23+dfsg-1ubuntu4
2010-10-18 19:33:19 status config-files linux-sound-base 1.0.23+dfsg-1ubuntu4
2010-10-18 19:33:19 purge linux-sound-base 1.0.23+dfsg-1ubuntu4 1.0.23+dfsg-1ubuntu4
2010-10-18 19:33:19 status config-files linux-sound-base 1.0.23+dfsg-1ubuntu4
2010-10-18 19:33:20 status config-files linux-sound-base 1.0.23+dfsg-1ubuntu4
2010-10-18 19:33:20 status config-files linux-sound-base 1.0.23+dfsg-1ubuntu4
2010-10-18 19:33:20 status config-files linux-sound-base 1.0.23+dfsg-1ubuntu4
2010-10-18 19:33:20 status config-files linux-sound-base 1.0.23+dfsg-1ubuntu4
2010-10-18 19:33:20 status not-installed linux-sound-base <none>
2010-10-18 19:33:20 trigproc ureadahead 0.100.0-8 0.100.0-8
2010-10-18 19:33:20 status half-configured ureadahead 0.100.0-8
2010-10-18 19:33:20 status installed ureadahead 0.100.0-8
2010-10-18 19:33:20 trigproc man-db 2.5.7-4 2.5.7-4
2010-10-18 19:33:20 status half-configured man-db 2.5.7-4
2010-10-18 19:33:22 status installed man-db 2.5.7-4
2010-10-18 19:33:39 startup archives unpack
2010-10-18 19:33:40 install linux-sound-base <none> 1.0.23+dfsg-1ubuntu4
2010-10-18 19:33:40 status half-installed linux-sound-base 1.0.23+dfsg-1ubuntu4
2010-10-18 19:33:40 status unpacked linux-sound-base 1.0.23+dfsg-1ubuntu4
2010-10-18 19:33:40 status unpacked linux-sound-base 1.0.23+dfsg-1ubuntu4
2010-10-18 19:33:41 install alsa-base <none> 1.0.23+dfsg-1ubuntu4
2010-10-18 19:33:41 status half-installed alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-18 19:33:41 status unpacked alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-18 19:33:41 status unpacked alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-18 19:33:42 install alsa-utils <none> 1.0.23-2ubuntu3
2010-10-18 19:33:42 status half-installed alsa-utils 1.0.23-2ubuntu3
2010-10-18 19:33:42 status triggers-pending man-db 2.5.7-4
2010-10-18 19:33:42 status half-installed alsa-utils 1.0.23-2ubuntu3
2010-10-18 19:33:42 status triggers-pending ureadahead 0.100.0-8
2010-10-18 19:33:42 status half-installed alsa-utils 1.0.23-2ubuntu3
2010-10-18 19:33:42 status triggers-pending ureadahead 0.100.0-8
2010-10-18 19:33:42 status unpacked alsa-utils 1.0.23-2ubuntu3
2010-10-18 19:33:43 status unpacked alsa-utils 1.0.23-2ubuntu3
2010-10-18 19:33:43 trigproc man-db 2.5.7-4 2.5.7-4
2010-10-18 19:33:43 status half-configured man-db 2.5.7-4
2010-10-18 19:33:43 status installed man-db 2.5.7-4
2010-10-18 19:33:43 trigproc ureadahead 0.100.0-8 0.100.0-8
2010-10-18 19:33:43 status half-configured ureadahead 0.100.0-8
2010-10-18 19:33:43 status installed ureadahead 0.100.0-8
2010-10-18 19:33:44 startup packages configure
2010-10-18 19:33:44 configure linux-sound-base 1.0.23+dfsg-1ubuntu4 1.0.23+dfsg-1ubuntu4
2010-10-18 19:33:44 status unpacked linux-sound-base 1.0.23+dfsg-1ubuntu4
2010-10-18 19:33:44 status half-configured linux-sound-base 1.0.23+dfsg-1ubuntu4
2010-10-18 19:33:44 status installed linux-sound-base 1.0.23+dfsg-1ubuntu4
2010-10-18 19:33:44 configure alsa-base 1.0.23+dfsg-1ubuntu4 1.0.23+dfsg-1ubuntu4
2010-10-18 19:33:44 status unpacked alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-18 19:33:44 status unpacked alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-18 19:33:45 status unpacked alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-18 19:33:45 status unpacked alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-18 19:33:45 status half-configured alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-18 19:33:45 status installed alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-18 19:33:45 configure alsa-utils 1.0.23-2ubuntu3 1.0.23-2ubuntu3
2010-10-18 19:33:45 status unpacked alsa-utils 1.0.23-2ubuntu3
2010-10-18 19:33:45 status unpacked alsa-utils 1.0.23-2ubuntu3
2010-10-18 19:33:45 status half-configured alsa-utils 1.0.23-2ubuntu3
2010-10-18 19:33:45 status installed alsa-utils 1.0.23-2ubuntu3
2010-10-18 19:40:12 startup packages remove
2010-10-18 19:40:12 status installed libboost-filesystem1.42.0 1.42.0-3ubuntu1
2010-10-18 19:40:13 remove libboost-filesystem1.42.0 1.42.0-3ubuntu1 1.42.0-3ubuntu1
2010-10-18 19:40:13 status half-configured libboost-filesystem1.42.0 1.42.0-3ubuntu1
2010-10-18 19:40:13 status half-installed libboost-filesystem1.42.0 1.42.0-3ubuntu1
2010-10-18 19:40:13 status triggers-pending libc-bin 2.12.1-0ubuntu6
2010-10-18 19:40:13 status config-files libboost-filesystem1.42.0 1.42.0-3ubuntu1
2010-10-18 19:40:13 status config-files libboost-filesystem1.42.0 1.42.0-3ubuntu1
2010-10-18 19:40:13 status installed libboost-system1.42.0 1.42.0-3ubuntu1
2010-10-18 19:40:14 remove libboost-system1.42.0 1.42.0-3ubuntu1 1.42.0-3ubuntu1
2010-10-18 19:40:14 status half-configured libboost-system1.42.0 1.42.0-3ubuntu1
2010-10-18 19:40:14 status half-installed libboost-system1.42.0 1.42.0-3ubuntu1
2010-10-18 19:40:14 status config-files libboost-system1.42.0 1.42.0-3ubuntu1
2010-10-18 19:40:14 status config-files libboost-system1.42.0 1.42.0-3ubuntu1
2010-10-18 19:40:14 status installed libdbus-c++-1-0 0~20090907-1
2010-10-18 19:40:14 remove libdbus-c++-1-0 0~20090907-1 0~20090907-1
2010-10-18 19:40:14 status half-configured libdbus-c++-1-0 0~20090907-1
2010-10-18 19:40:14 status half-installed libdbus-c++-1-0 0~20090907-1
2010-10-18 19:40:14 status config-files libdbus-c++-1-0 0~20090907-1
2010-10-18 19:40:14 status config-files libdbus-c++-1-0 0~20090907-1
2010-10-18 19:40:14 status installed libpanelappletmm-2.6-1c2 2.26.0-1
2010-10-18 19:40:14 remove libpanelappletmm-2.6-1c2 2.26.0-1 2.26.0-1
2010-10-18 19:40:14 status half-configured libpanelappletmm-2.6-1c2 2.26.0-1
2010-10-18 19:40:14 status half-installed libpanelappletmm-2.6-1c2 2.26.0-1
2010-10-18 19:40:15 status config-files libpanelappletmm-2.6-1c2 2.26.0-1
2010-10-18 19:40:15 status config-files libpanelappletmm-2.6-1c2 2.26.0-1
2010-10-18 19:40:15 status installed libgconfmm-2.6-1c2 2.28.0-1
2010-10-18 19:40:15 remove libgconfmm-2.6-1c2 2.28.0-1 2.28.0-1
2010-10-18 19:40:15 status half-configured libgconfmm-2.6-1c2 2.28.0-1
2010-10-18 19:40:15 status half-installed libgconfmm-2.6-1c2 2.28.0-1
2010-10-18 19:40:15 status config-files libgconfmm-2.6-1c2 2.28.0-1
2010-10-18 19:40:15 status config-files libgconfmm-2.6-1c2 2.28.0-1
2010-10-18 19:40:15 status installed libpcrecpp0 8.02-1
2010-10-18 19:40:15 remove libpcrecpp0 8.02-1 8.02-1
2010-10-18 19:40:15 status half-configured libpcrecpp0 8.02-1
2010-10-18 19:40:15 status half-installed libpcrecpp0 8.02-1
2010-10-18 19:40:16 status config-files libpcrecpp0 8.02-1
2010-10-18 19:40:16 status config-files libpcrecpp0 8.02-1
2010-10-18 19:40:16 trigproc libc-bin 2.12.1-0ubuntu6 2.12.1-0ubuntu6
2010-10-18 19:40:16 status half-configured libc-bin 2.12.1-0ubuntu6
2010-10-18 19:40:16 status installed libc-bin 2.12.1-0ubuntu6
2010-10-19 08:09:31 startup archives unpack
2010-10-19 08:09:33 install libdvdread4 <none> 4.1.3-10ubuntu2
2010-10-19 08:09:33 status half-installed libdvdread4 4.1.3-10ubuntu2
2010-10-19 08:09:33 status unpacked libdvdread4 4.1.3-10ubuntu2
2010-10-19 08:09:33 status unpacked libdvdread4 4.1.3-10ubuntu2
2010-10-19 08:09:34 install libid3tag0 <none> 0.15.1b-10build2
2010-10-19 08:09:34 status half-installed libid3tag0 0.15.1b-10build2
2010-10-19 08:09:34 status unpacked libid3tag0 0.15.1b-10build2
2010-10-19 08:09:34 status unpacked libid3tag0 0.15.1b-10build2
2010-10-19 08:09:34 install libmad0 <none> 0.15.1b-4ubuntu2
2010-10-19 08:09:34 status half-installed libmad0 0.15.1b-4ubuntu2
2010-10-19 08:09:35 status unpacked libmad0 0.15.1b-4ubuntu2
2010-10-19 08:09:35 status unpacked libmad0 0.15.1b-4ubuntu2
2010-10-19 08:09:35 install libmpeg2-4 <none> 0.4.1-3
2010-10-19 08:09:35 status half-installed libmpeg2-4 0.4.1-3
2010-10-19 08:09:35 status unpacked libmpeg2-4 0.4.1-3
2010-10-19 08:09:35 status unpacked libmpeg2-4 0.4.1-3
2010-10-19 08:09:35 install libopencore-amrnb0 <none> 0.1.2-1
2010-10-19 08:09:35 status half-installed libopencore-amrnb0 0.1.2-1
2010-10-19 08:09:36 status unpacked libopencore-amrnb0 0.1.2-1
2010-10-19 08:09:36 status unpacked libopencore-amrnb0 0.1.2-1
2010-10-19 08:09:36 install libopencore-amrwb0 <none> 0.1.2-1
2010-10-19 08:09:36 status half-installed libopencore-amrwb0 0.1.2-1
2010-10-19 08:09:37 status unpacked libopencore-amrwb0 0.1.2-1
2010-10-19 08:09:37 status unpacked libopencore-amrwb0 0.1.2-1
2010-10-19 08:09:37 install libsidplay1 <none> 1.36.59-5
2010-10-19 08:09:37 status half-installed libsidplay1 1.36.59-5
2010-10-19 08:09:38 status unpacked libsidplay1 1.36.59-5
2010-10-19 08:09:38 status unpacked libsidplay1 1.36.59-5
2010-10-19 08:09:38 install libtwolame0 <none> 0.3.12-1
2010-10-19 08:09:38 status half-installed libtwolame0 0.3.12-1
2010-10-19 08:09:39 status unpacked libtwolame0 0.3.12-1
2010-10-19 08:09:39 status unpacked libtwolame0 0.3.12-1
2010-10-19 08:09:39 install gstreamer0.10-plugins-ugly <none> 0.10.16-1
2010-10-19 08:09:39 status half-installed gstreamer0.10-plugins-ugly 0.10.16-1
2010-10-19 08:09:39 status unpacked gstreamer0.10-plugins-ugly 0.10.16-1
2010-10-19 08:09:39 status unpacked gstreamer0.10-plugins-ugly 0.10.16-1
2010-10-19 08:09:40 install libdvdnav4 <none> 4.1.3-7
2010-10-19 08:09:40 status half-installed libdvdnav4 4.1.3-7
2010-10-19 08:09:40 status unpacked libdvdnav4 4.1.3-7
2010-10-19 08:09:40 status unpacked libdvdnav4 4.1.3-7
2010-10-19 08:09:41 startup packages configure
2010-10-19 08:09:41 configure libdvdread4 4.1.3-10ubuntu2 4.1.3-10ubuntu2
2010-10-19 08:09:41 status unpacked libdvdread4 4.1.3-10ubuntu2
2010-10-19 08:09:41 status half-configured libdvdread4 4.1.3-10ubuntu2
2010-10-19 08:09:41 status installed libdvdread4 4.1.3-10ubuntu2
2010-10-19 08:09:41 status triggers-pending libc-bin 2.12.1-0ubuntu6
2010-10-19 08:09:41 configure libid3tag0 0.15.1b-10build2 0.15.1b-10build2
2010-10-19 08:09:41 status unpacked libid3tag0 0.15.1b-10build2
2010-10-19 08:09:41 status half-configured libid3tag0 0.15.1b-10build2
2010-10-19 08:09:41 status installed libid3tag0 0.15.1b-10build2
2010-10-19 08:09:41 configure libmad0 0.15.1b-4ubuntu2 0.15.1b-4ubuntu2
2010-10-19 08:09:41 status unpacked libmad0 0.15.1b-4ubuntu2
2010-10-19 08:09:42 status half-configured libmad0 0.15.1b-4ubuntu2
2010-10-19 08:09:42 status installed libmad0 0.15.1b-4ubuntu2
2010-10-19 08:09:42 configure libmpeg2-4 0.4.1-3 0.4.1-3
2010-10-19 08:09:42 status unpacked libmpeg2-4 0.4.1-3
2010-10-19 08:09:42 status half-configured libmpeg2-4 0.4.1-3
2010-10-19 08:09:42 status installed libmpeg2-4 0.4.1-3
2010-10-19 08:09:42 configure libopencore-amrnb0 0.1.2-1 0.1.2-1
2010-10-19 08:09:42 status unpacked libopencore-amrnb0 0.1.2-1
2010-10-19 08:09:42 status half-configured libopencore-amrnb0 0.1.2-1
2010-10-19 08:09:42 status installed libopencore-amrnb0 0.1.2-1
2010-10-19 08:09:42 configure libopencore-amrwb0 0.1.2-1 0.1.2-1
2010-10-19 08:09:42 status unpacked libopencore-amrwb0 0.1.2-1
2010-10-19 08:09:42 status half-configured libopencore-amrwb0 0.1.2-1
2010-10-19 08:09:43 status installed libopencore-amrwb0 0.1.2-1
2010-10-19 08:09:43 configure libsidplay1 1.36.59-5 1.36.59-5
2010-10-19 08:09:43 status unpacked libsidplay1 1.36.59-5
2010-10-19 08:09:43 status half-configured libsidplay1 1.36.59-5
2010-10-19 08:09:43 status installed libsidplay1 1.36.59-5
2010-10-19 08:09:44 configure libtwolame0 0.3.12-1 0.3.12-1
2010-10-19 08:09:44 status unpacked libtwolame0 0.3.12-1
2010-10-19 08:09:44 status half-configured libtwolame0 0.3.12-1
2010-10-19 08:09:44 status installed libtwolame0 0.3.12-1
2010-10-19 08:09:44 configure gstreamer0.10-plugins-ugly 0.10.16-1 0.10.16-1
2010-10-19 08:09:44 status unpacked gstreamer0.10-plugins-ugly 0.10.16-1
2010-10-19 08:09:44 status half-configured gstreamer0.10-plugins-ugly 0.10.16-1
2010-10-19 08:09:44 status installed gstreamer0.10-plugins-ugly 0.10.16-1
2010-10-19 08:09:44 configure libdvdnav4 4.1.3-7 4.1.3-7
2010-10-19 08:09:44 status unpacked libdvdnav4 4.1.3-7
2010-10-19 08:09:44 status half-configured libdvdnav4 4.1.3-7
2010-10-19 08:09:44 status installed libdvdnav4 4.1.3-7
2010-10-19 08:09:44 trigproc libc-bin 2.12.1-0ubuntu6 2.12.1-0ubuntu6
2010-10-19 08:09:44 status half-configured libc-bin 2.12.1-0ubuntu6
2010-10-19 08:09:44 status installed libc-bin 2.12.1-0ubuntu6
2010-10-19 08:10:46 startup archives unpack
2010-10-19 08:10:46 install gstreamer0.10-ffmpeg <none> 0.10.11-1
2010-10-19 08:10:46 status half-installed gstreamer0.10-ffmpeg 0.10.11-1
2010-10-19 08:10:46 status unpacked gstreamer0.10-ffmpeg 0.10.11-1
2010-10-19 08:10:47 status unpacked gstreamer0.10-ffmpeg 0.10.11-1
2010-10-19 08:10:47 startup packages configure
2010-10-19 08:10:47 configure gstreamer0.10-ffmpeg 0.10.11-1 0.10.11-1
2010-10-19 08:10:47 status unpacked gstreamer0.10-ffmpeg 0.10.11-1
2010-10-19 08:10:47 status half-configured gstreamer0.10-ffmpeg 0.10.11-1
2010-10-19 08:10:47 status installed gstreamer0.10-ffmpeg 0.10.11-1
2010-10-19 10:15:06 startup archives unpack
2010-10-19 10:15:07 upgrade libc6-dev 2.12.1-0ubuntu6 2.12.1-0ubuntu7
2010-10-19 10:15:07 status half-configured libc6-dev 2.12.1-0ubuntu6
2010-10-19 10:15:07 status unpacked libc6-dev 2.12.1-0ubuntu6
2010-10-19 10:15:07 status half-installed libc6-dev 2.12.1-0ubuntu6
2010-10-19 10:15:08 status half-installed libc6-dev 2.12.1-0ubuntu6
2010-10-19 10:15:08 status unpacked libc6-dev 2.12.1-0ubuntu7
2010-10-19 10:15:09 status unpacked libc6-dev 2.12.1-0ubuntu7
2010-10-19 10:15:09 upgrade libc-dev-bin 2.12.1-0ubuntu6 2.12.1-0ubuntu7
2010-10-19 10:15:09 status half-configured libc-dev-bin 2.12.1-0ubuntu6
2010-10-19 10:15:09 status unpacked libc-dev-bin 2.12.1-0ubuntu6
2010-10-19 10:15:09 status half-installed libc-dev-bin 2.12.1-0ubuntu6
2010-10-19 10:15:09 status triggers-pending man-db 2.5.7-4
2010-10-19 10:15:09 status half-installed libc-dev-bin 2.12.1-0ubuntu6
2010-10-19 10:15:09 status half-installed libc-dev-bin 2.12.1-0ubuntu6
2010-10-19 10:15:09 status unpacked libc-dev-bin 2.12.1-0ubuntu7
2010-10-19 10:15:09 status unpacked libc-dev-bin 2.12.1-0ubuntu7
2010-10-19 10:15:10 upgrade libc-bin 2.12.1-0ubuntu6 2.12.1-0ubuntu7
2010-10-19 10:15:10 status half-configured libc-bin 2.12.1-0ubuntu6
2010-10-19 10:15:10 status unpacked libc-bin 2.12.1-0ubuntu6
2010-10-19 10:15:10 status half-installed libc-bin 2.12.1-0ubuntu6
2010-10-19 10:15:10 status half-installed libc-bin 2.12.1-0ubuntu6
2010-10-19 10:15:10 status half-installed libc-bin 2.12.1-0ubuntu6
2010-10-19 10:15:11 status unpacked libc-bin 2.12.1-0ubuntu7
2010-10-19 10:15:11 status unpacked libc-bin 2.12.1-0ubuntu7
2010-10-19 10:15:11 trigproc man-db 2.5.7-4 2.5.7-4
2010-10-19 10:15:11 status half-configured man-db 2.5.7-4
2010-10-19 10:15:12 status installed man-db 2.5.7-4
2010-10-19 10:15:13 startup packages configure
2010-10-19 10:15:13 configure libc-bin 2.12.1-0ubuntu7 2.12.1-0ubuntu7
2010-10-19 10:15:13 status unpacked libc-bin 2.12.1-0ubuntu7
2010-10-19 10:15:13 status unpacked libc-bin 2.12.1-0ubuntu7
2010-10-19 10:15:13 status unpacked libc-bin 2.12.1-0ubuntu7
2010-10-19 10:15:13 status unpacked libc-bin 2.12.1-0ubuntu7
2010-10-19 10:15:13 status half-configured libc-bin 2.12.1-0ubuntu7
2010-10-19 10:15:13 status installed libc-bin 2.12.1-0ubuntu7
2010-10-19 10:15:14 startup archives unpack
2010-10-19 10:15:14 upgrade libc6 2.12.1-0ubuntu6 2.12.1-0ubuntu7
2010-10-19 10:15:14 status half-configured libc6 2.12.1-0ubuntu6
2010-10-19 10:15:15 status unpacked libc6 2.12.1-0ubuntu6
2010-10-19 10:15:15 status half-installed libc6 2.12.1-0ubuntu6
2010-10-19 10:15:16 status half-installed libc6 2.12.1-0ubuntu6
2010-10-19 10:15:16 status unpacked libc6 2.12.1-0ubuntu7
2010-10-19 10:15:16 status unpacked libc6 2.12.1-0ubuntu7
2010-10-19 10:15:17 startup packages configure
2010-10-19 10:15:17 configure libc6 2.12.1-0ubuntu7 2.12.1-0ubuntu7
2010-10-19 10:15:17 status unpacked libc6 2.12.1-0ubuntu7
2010-10-19 10:15:17 status unpacked libc6 2.12.1-0ubuntu7
2010-10-19 10:15:17 status half-configured libc6 2.12.1-0ubuntu7
2010-10-19 10:15:19 status installed libc6 2.12.1-0ubuntu7
2010-10-19 10:15:19 status triggers-pending libc-bin 2.12.1-0ubuntu7
2010-10-19 10:15:19 trigproc libc-bin 2.12.1-0ubuntu7 2.12.1-0ubuntu7
2010-10-19 10:15:19 status half-configured libc-bin 2.12.1-0ubuntu7
2010-10-19 10:15:19 status installed libc-bin 2.12.1-0ubuntu7
2010-10-19 10:15:20 startup archives unpack
2010-10-19 10:15:20 upgrade libudev0 162-2 162-2.1
2010-10-19 10:15:20 status half-configured libudev0 162-2
2010-10-19 10:15:21 status unpacked libudev0 162-2
2010-10-19 10:15:21 status half-installed libudev0 162-2
2010-10-19 10:15:21 status half-installed libudev0 162-2
2010-10-19 10:15:21 status unpacked libudev0 162-2.1
2010-10-19 10:15:21 status unpacked libudev0 162-2.1
2010-10-19 10:15:21 upgrade udev 162-2 162-2.1
2010-10-19 10:15:21 status half-configured udev 162-2
2010-10-19 10:15:22 status unpacked udev 162-2
2010-10-19 10:15:22 status half-installed udev 162-2
2010-10-19 10:15:22 status triggers-pending ureadahead 0.100.0-8
2010-10-19 10:15:22 status half-installed udev 162-2
2010-10-19 10:15:22 status triggers-pending ureadahead 0.100.0-8
2010-10-19 10:15:22 status triggers-pending man-db 2.5.7-4
2010-10-19 10:15:22 status half-installed udev 162-2
2010-10-19 10:15:22 status half-installed udev 162-2
2010-10-19 10:15:23 status unpacked udev 162-2.1
2010-10-19 10:15:23 status unpacked udev 162-2.1
2010-10-19 10:15:23 upgrade libclamav6 0.96.3+dfsg-2ubuntu1 0.96.3+dfsg-2ubuntu1.1
2010-10-19 10:15:23 status half-configured libclamav6 0.96.3+dfsg-2ubuntu1
2010-10-19 10:15:23 status unpacked libclamav6 0.96.3+dfsg-2ubuntu1
2010-10-19 10:15:23 status half-installed libclamav6 0.96.3+dfsg-2ubuntu1
2010-10-19 10:15:24 status half-installed libclamav6 0.96.3+dfsg-2ubuntu1
2010-10-19 10:15:24 status unpacked libclamav6 0.96.3+dfsg-2ubuntu1.1
2010-10-19 10:15:24 status unpacked libclamav6 0.96.3+dfsg-2ubuntu1.1
2010-10-19 10:15:24 upgrade clamav-base 0.96.3+dfsg-2ubuntu1 0.96.3+dfsg-2ubuntu1.1
2010-10-19 10:15:24 status half-configured clamav-base 0.96.3+dfsg-2ubuntu1
2010-10-19 10:15:24 status unpacked clamav-base 0.96.3+dfsg-2ubuntu1
2010-10-19 10:15:24 status half-installed clamav-base 0.96.3+dfsg-2ubuntu1
2010-10-19 10:15:25 status half-installed clamav-base 0.96.3+dfsg-2ubuntu1
2010-10-19 10:15:25 status half-installed clamav-base 0.96.3+dfsg-2ubuntu1
2010-10-19 10:15:25 status unpacked clamav-base 0.96.3+dfsg-2ubuntu1.1
2010-10-19 10:15:25 status unpacked clamav-base 0.96.3+dfsg-2ubuntu1.1
2010-10-19 10:15:26 upgrade clamav-freshclam 0.96.3+dfsg-2ubuntu1 0.96.3+dfsg-2ubuntu1.1
2010-10-19 10:15:26 status half-configured clamav-freshclam 0.96.3+dfsg-2ubuntu1
2010-10-19 10:15:27 status unpacked clamav-freshclam 0.96.3+dfsg-2ubuntu1
2010-10-19 10:15:27 status half-installed clamav-freshclam 0.96.3+dfsg-2ubuntu1
2010-10-19 10:15:27 status half-installed clamav-freshclam 0.96.3+dfsg-2ubuntu1
2010-10-19 10:15:27 status half-installed clamav-freshclam 0.96.3+dfsg-2ubuntu1
2010-10-19 10:15:27 status half-installed clamav-freshclam 0.96.3+dfsg-2ubuntu1
2010-10-19 10:15:28 status unpacked clamav-freshclam 0.96.3+dfsg-2ubuntu1.1
2010-10-19 10:15:28 status unpacked clamav-freshclam 0.96.3+dfsg-2ubuntu1.1
2010-10-19 10:15:28 upgrade clamav 0.96.3+dfsg-2ubuntu1 0.96.3+dfsg-2ubuntu1.1
2010-10-19 10:15:28 status half-configured clamav 0.96.3+dfsg-2ubuntu1
2010-10-19 10:15:28 status unpacked clamav 0.96.3+dfsg-2ubuntu1
2010-10-19 10:15:28 status half-installed clamav 0.96.3+dfsg-2ubuntu1
2010-10-19 10:15:28 status half-installed clamav 0.96.3+dfsg-2ubuntu1
2010-10-19 10:15:29 status half-installed clamav 0.96.3+dfsg-2ubuntu1
2010-10-19 10:15:29 status unpacked clamav 0.96.3+dfsg-2ubuntu1.1
2010-10-19 10:15:29 status unpacked clamav 0.96.3+dfsg-2ubuntu1.1
2010-10-19 10:15:29 upgrade gconf2-common 2.31.91-0ubuntu3 2.31.91-0ubuntu3.1
2010-10-19 10:15:29 status half-configured gconf2-common 2.31.91-0ubuntu3
2010-10-19 10:15:29 status unpacked gconf2-common 2.31.91-0ubuntu3
2010-10-19 10:15:29 status half-installed gconf2-common 2.31.91-0ubuntu3
2010-10-19 10:15:29 status triggers-pending gconf2 2.31.91-0ubuntu3
2010-10-19 10:15:29 status half-installed gconf2-common 2.31.91-0ubuntu3
2010-10-19 10:15:29 status triggers-pending gconf2 2.31.91-0ubuntu3
2010-10-19 10:15:29 status triggers-pending gconf2 2.31.91-0ubuntu3
2010-10-19 10:15:30 status half-installed gconf2-common 2.31.91-0ubuntu3
2010-10-19 10:15:30 status unpacked gconf2-common 2.31.91-0ubuntu3.1
2010-10-19 10:15:30 status unpacked gconf2-common 2.31.91-0ubuntu3.1
2010-10-19 10:15:30 upgrade libgconf2-4 2.31.91-0ubuntu3 2.31.91-0ubuntu3.1
2010-10-19 10:15:30 status half-configured libgconf2-4 2.31.91-0ubuntu3
2010-10-19 10:15:30 status unpacked libgconf2-4 2.31.91-0ubuntu3
2010-10-19 10:15:30 status half-installed libgconf2-4 2.31.91-0ubuntu3
2010-10-19 10:15:31 status half-installed libgconf2-4 2.31.91-0ubuntu3
2010-10-19 10:15:31 status unpacked libgconf2-4 2.31.91-0ubuntu3.1
2010-10-19 10:15:31 status unpacked libgconf2-4 2.31.91-0ubuntu3.1
2010-10-19 10:15:31 upgrade gconf-defaults-service 2.31.91-0ubuntu3 2.31.91-0ubuntu3.1
2010-10-19 10:15:31 status half-configured gconf-defaults-service 2.31.91-0ubuntu3
2010-10-19 10:15:31 status unpacked gconf-defaults-service 2.31.91-0ubuntu3
2010-10-19 10:15:31 status half-installed gconf-defaults-service 2.31.91-0ubuntu3
2010-10-19 10:15:32 status half-installed gconf-defaults-service 2.31.91-0ubuntu3
2010-10-19 10:15:32 status unpacked gconf-defaults-service 2.31.91-0ubuntu3.1
2010-10-19 10:15:32 status unpacked gconf-defaults-service 2.31.91-0ubuntu3.1
2010-10-19 10:15:32 upgrade gconf2 2.31.91-0ubuntu3 2.31.91-0ubuntu3.1
2010-10-19 10:15:32 status half-configured gconf2 2.31.91-0ubuntu3
2010-10-19 10:15:33 status unpacked gconf2 2.31.91-0ubuntu3
2010-10-19 10:15:33 status half-installed gconf2 2.31.91-0ubuntu3
2010-10-19 10:15:33 status half-installed gconf2 2.31.91-0ubuntu3
2010-10-19 10:15:34 status half-installed gconf2 2.31.91-0ubuntu3
2010-10-19 10:15:34 status unpacked gconf2 2.31.91-0ubuntu3.1
2010-10-19 10:15:34 status unpacked gconf2 2.31.91-0ubuntu3.1
2010-10-19 10:15:34 upgrade gdm-guest-session 0.16 0.17
2010-10-19 10:15:34 status half-configured gdm-guest-session 0.16
2010-10-19 10:15:35 status unpacked gdm-guest-session 0.16
2010-10-19 10:15:35 status half-installed gdm-guest-session 0.16
2010-10-19 10:15:35 status half-installed gdm-guest-session 0.16
2010-10-19 10:15:35 status unpacked gdm-guest-session 0.17
2010-10-19 10:15:36 status unpacked gdm-guest-session 0.17
2010-10-19 10:15:36 upgrade jockey-gtk 0.5.10-0ubuntu5 0.5.10-0ubuntu5.1
2010-10-19 10:15:36 status half-configured jockey-gtk 0.5.10-0ubuntu5
2010-10-19 10:15:36 status unpacked jockey-gtk 0.5.10-0ubuntu5
2010-10-19 10:15:36 status half-installed jockey-gtk 0.5.10-0ubuntu5
2010-10-19 10:15:36 status triggers-pending desktop-file-utils 0.16-0ubuntu4
2010-10-19 10:15:36 status half-installed jockey-gtk 0.5.10-0ubuntu5
2010-10-19 10:15:36 status triggers-pending python-gmenu 2.30.4-0ubuntu1
2010-10-19 10:15:36 status half-installed jockey-gtk 0.5.10-0ubuntu5
2010-10-19 10:15:36 status half-installed jockey-gtk 0.5.10-0ubuntu5
2010-10-19 10:15:37 status unpacked jockey-gtk 0.5.10-0ubuntu5.1
2010-10-19 10:15:37 status unpacked jockey-gtk 0.5.10-0ubuntu5.1
2010-10-19 10:15:37 upgrade jockey-common 0.5.10-0ubuntu5 0.5.10-0ubuntu5.1
2010-10-19 10:15:37 status half-configured jockey-common 0.5.10-0ubuntu5
2010-10-19 10:15:37 status unpacked jockey-common 0.5.10-0ubuntu5
2010-10-19 10:15:37 status half-installed jockey-common 0.5.10-0ubuntu5
2010-10-19 10:15:37 status triggers-pending hicolor-icon-theme 0.11-1
2010-10-19 10:15:37 status half-installed jockey-common 0.5.10-0ubuntu5
2010-10-19 10:15:38 status half-installed jockey-common 0.5.10-0ubuntu5
2010-10-19 10:15:38 status unpacked jockey-common 0.5.10-0ubuntu5.1
2010-10-19 10:15:38 status unpacked jockey-common 0.5.10-0ubuntu5.1
2010-10-19 10:15:38 upgrade libgudev-1.0-0 1:162-2 1:162-2.1
2010-10-19 10:15:38 status half-configured libgudev-1.0-0 1:162-2
2010-10-19 10:15:39 status unpacked libgudev-1.0-0 1:162-2
2010-10-19 10:15:39 status half-installed libgudev-1.0-0 1:162-2
2010-10-19 10:15:39 status half-installed libgudev-1.0-0 1:162-2
2010-10-19 10:15:39 status unpacked libgudev-1.0-0 1:162-2.1
2010-10-19 10:15:39 status unpacked libgudev-1.0-0 1:162-2.1
2010-10-19 10:15:40 upgrade libutouch-grail1 1.0.14-0ubuntu1 1.0.15-0ubuntu1
2010-10-19 10:15:40 status half-configured libutouch-grail1 1.0.14-0ubuntu1
2010-10-19 10:15:40 status unpacked libutouch-grail1 1.0.14-0ubuntu1
2010-10-19 10:15:40 status half-installed libutouch-grail1 1.0.14-0ubuntu1
2010-10-19 10:15:41 status half-installed libutouch-grail1 1.0.14-0ubuntu1
2010-10-19 10:15:41 status unpacked libutouch-grail1 1.0.15-0ubuntu1
2010-10-19 10:15:41 status unpacked libutouch-grail1 1.0.15-0ubuntu1
2010-10-19 10:15:42 upgrade ubuntu-tweak 0.5.7-1~lucid1 0.5.7-1~maverick1
2010-10-19 10:15:42 status half-configured ubuntu-tweak 0.5.7-1~lucid1
2010-10-19 10:15:42 status unpacked ubuntu-tweak 0.5.7-1~lucid1
2010-10-19 10:15:42 status half-installed ubuntu-tweak 0.5.7-1~lucid1
2010-10-19 10:15:42 status half-installed ubuntu-tweak 0.5.7-1~lucid1
2010-10-19 10:15:42 status half-installed ubuntu-tweak 0.5.7-1~lucid1
2010-10-19 10:15:42 status half-installed ubuntu-tweak 0.5.7-1~lucid1
2010-10-19 10:15:43 status half-installed ubuntu-tweak 0.5.7-1~lucid1
2010-10-19 10:15:43 status unpacked ubuntu-tweak 0.5.7-1~maverick1
2010-10-19 10:15:43 status unpacked ubuntu-tweak 0.5.7-1~maverick1
2010-10-19 10:15:43 upgrade gnome-settings-daemon 2.32.0-0ubuntu2 2.32.0-0ubuntu3
2010-10-19 10:15:43 status half-configured gnome-settings-daemon 2.32.0-0ubuntu2
2010-10-19 10:15:43 status unpacked gnome-settings-daemon 2.32.0-0ubuntu2
2010-10-19 10:15:43 status half-installed gnome-settings-daemon 2.32.0-0ubuntu2
2010-10-19 10:15:43 status half-installed gnome-settings-daemon 2.32.0-0ubuntu2
2010-10-19 10:15:44 status half-installed gnome-settings-daemon 2.32.0-0ubuntu2
2010-10-19 10:15:45 status half-installed gnome-settings-daemon 2.32.0-0ubuntu2
2010-10-19 10:15:45 status unpacked gnome-settings-daemon 2.32.0-0ubuntu3
2010-10-19 10:15:45 status unpacked gnome-settings-daemon 2.32.0-0ubuntu3
2010-10-19 10:15:45 trigproc ureadahead 0.100.0-8 0.100.0-8
2010-10-19 10:15:45 status half-configured ureadahead 0.100.0-8
2010-10-19 10:15:45 status installed ureadahead 0.100.0-8
2010-10-19 10:15:45 trigproc man-db 2.5.7-4 2.5.7-4
2010-10-19 10:15:45 status half-configured man-db 2.5.7-4
2010-10-19 10:15:46 status installed man-db 2.5.7-4
2010-10-19 10:15:46 trigproc desktop-file-utils 0.16-0ubuntu4 0.16-0ubuntu4
2010-10-19 10:15:46 status half-configured desktop-file-utils 0.16-0ubuntu4
2010-10-19 10:15:46 status installed desktop-file-utils 0.16-0ubuntu4
2010-10-19 10:15:46 trigproc python-gmenu 2.30.4-0ubuntu1 2.30.4-0ubuntu1
2010-10-19 10:15:46 status half-configured python-gmenu 2.30.4-0ubuntu1
2010-10-19 10:15:47 status installed python-gmenu 2.30.4-0ubuntu1
2010-10-19 10:15:47 status triggers-pending python-support 1.0.9ubuntu1
2010-10-19 10:15:47 trigproc hicolor-icon-theme 0.11-1 0.11-1
2010-10-19 10:15:47 status half-configured hicolor-icon-theme 0.11-1
2010-10-19 10:15:49 status installed hicolor-icon-theme 0.11-1
2010-10-19 10:15:49 trigproc python-support 1.0.9ubuntu1 1.0.9ubuntu1
2010-10-19 10:15:49 status half-configured python-support 1.0.9ubuntu1
2010-10-19 10:15:50 status installed python-support 1.0.9ubuntu1
2010-10-19 10:15:51 startup packages configure
2010-10-19 10:15:51 configure libc-dev-bin 2.12.1-0ubuntu7 2.12.1-0ubuntu7
2010-10-19 10:15:51 status unpacked libc-dev-bin 2.12.1-0ubuntu7
2010-10-19 10:15:51 status half-configured libc-dev-bin 2.12.1-0ubuntu7
2010-10-19 10:15:51 status installed libc-dev-bin 2.12.1-0ubuntu7
2010-10-19 10:15:51 configure libc6-dev 2.12.1-0ubuntu7 2.12.1-0ubuntu7
2010-10-19 10:15:51 status unpacked libc6-dev 2.12.1-0ubuntu7
2010-10-19 10:15:51 status half-configured libc6-dev 2.12.1-0ubuntu7
2010-10-19 10:15:51 status installed libc6-dev 2.12.1-0ubuntu7
2010-10-19 10:15:52 configure libudev0 162-2.1 162-2.1
2010-10-19 10:15:52 status unpacked libudev0 162-2.1
2010-10-19 10:15:52 status half-configured libudev0 162-2.1
2010-10-19 10:15:52 status installed libudev0 162-2.1
2010-10-19 10:15:52 status triggers-pending libc-bin 2.12.1-0ubuntu7
2010-10-19 10:15:52 configure udev 162-2.1 162-2.1
2010-10-19 10:15:52 status unpacked udev 162-2.1
2010-10-19 10:15:52 status unpacked udev 162-2.1
2010-10-19 10:15:52 status unpacked udev 162-2.1
2010-10-19 10:15:52 status unpacked udev 162-2.1
2010-10-19 10:15:52 status unpacked udev 162-2.1
2010-10-19 10:15:52 status unpacked udev 162-2.1
2010-10-19 10:15:52 status unpacked udev 162-2.1
2010-10-19 10:15:52 status half-configured udev 162-2.1
2010-10-19 10:15:53 status installed udev 162-2.1
2010-10-19 10:15:53 status triggers-pending initramfs-tools 0.98.1ubuntu6
2010-10-19 10:15:53 configure libclamav6 0.96.3+dfsg-2ubuntu1.1 0.96.3+dfsg-2ubuntu1.1
2010-10-19 10:15:53 status unpacked libclamav6 0.96.3+dfsg-2ubuntu1.1
2010-10-19 10:15:53 status half-configured libclamav6 0.96.3+dfsg-2ubuntu1.1
2010-10-19 10:15:53 status installed libclamav6 0.96.3+dfsg-2ubuntu1.1
2010-10-19 10:15:53 configure clamav-base 0.96.3+dfsg-2ubuntu1.1 0.96.3+dfsg-2ubuntu1.1
2010-10-19 10:15:53 status unpacked clamav-base 0.96.3+dfsg-2ubuntu1.1
2010-10-19 10:15:53 status half-configured clamav-base 0.96.3+dfsg-2ubuntu1.1
2010-10-19 10:15:54 status installed clamav-base 0.96.3+dfsg-2ubuntu1.1
2010-10-19 10:15:54 configure clamav-freshclam 0.96.3+dfsg-2ubuntu1.1 0.96.3+dfsg-2ubuntu1.1
2010-10-19 10:15:54 status unpacked clamav-freshclam 0.96.3+dfsg-2ubuntu1.1
2010-10-19 10:15:54 status unpacked clamav-freshclam 0.96.3+dfsg-2ubuntu1.1
2010-10-19 10:15:54 status unpacked clamav-freshclam 0.96.3+dfsg-2ubuntu1.1
2010-10-19 10:15:54 status unpacked clamav-freshclam 0.96.3+dfsg-2ubuntu1.1
2010-10-19 10:15:54 status unpacked clamav-freshclam 0.96.3+dfsg-2ubuntu1.1
2010-10-19 10:15:54 status unpacked clamav-freshclam 0.96.3+dfsg-2ubuntu1.1
2010-10-19 10:15:54 status unpacked clamav-freshclam 0.96.3+dfsg-2ubuntu1.1
2010-10-19 10:15:54 status unpacked clamav-freshclam 0.96.3+dfsg-2ubuntu1.1
2010-10-19 10:15:54 status half-configured clamav-freshclam 0.96.3+dfsg-2ubuntu1.1
2010-10-19 10:15:56 status installed clamav-freshclam 0.96.3+dfsg-2ubuntu1.1
2010-10-19 10:15:56 configure clamav 0.96.3+dfsg-2ubuntu1.1 0.96.3+dfsg-2ubuntu1.1
2010-10-19 10:15:56 status unpacked clamav 0.96.3+dfsg-2ubuntu1.1
2010-10-19 10:15:56 status half-configured clamav 0.96.3+dfsg-2ubuntu1.1
2010-10-19 10:15:56 status installed clamav 0.96.3+dfsg-2ubuntu1.1
2010-10-19 10:15:56 configure gconf2-common 2.31.91-0ubuntu3.1 2.31.91-0ubuntu3.1
2010-10-19 10:15:56 status unpacked gconf2-common 2.31.91-0ubuntu3.1
2010-10-19 10:15:56 status unpacked gconf2-common 2.31.91-0ubuntu3.1
2010-10-19 10:15:56 status unpacked gconf2-common 2.31.91-0ubuntu3.1
2010-10-19 10:15:56 status half-configured gconf2-common 2.31.91-0ubuntu3.1
2010-10-19 10:15:57 status installed gconf2-common 2.31.91-0ubuntu3.1
2010-10-19 10:15:57 configure libgconf2-4 2.31.91-0ubuntu3.1 2.31.91-0ubuntu3.1
2010-10-19 10:15:57 status unpacked libgconf2-4 2.31.91-0ubuntu3.1
2010-10-19 10:15:57 status half-configured libgconf2-4 2.31.91-0ubuntu3.1
2010-10-19 10:15:57 status installed libgconf2-4 2.31.91-0ubuntu3.1
2010-10-19 10:15:57 configure gconf-defaults-service 2.31.91-0ubuntu3.1 2.31.91-0ubuntu3.1
2010-10-19 10:15:57 status unpacked gconf-defaults-service 2.31.91-0ubuntu3.1
2010-10-19 10:15:57 status unpacked gconf-defaults-service 2.31.91-0ubuntu3.1
2010-10-19 10:15:57 status half-configured gconf-defaults-service 2.31.91-0ubuntu3.1
2010-10-19 10:15:57 status installed gconf-defaults-service 2.31.91-0ubuntu3.1
2010-10-19 10:15:57 configure gconf2 2.31.91-0ubuntu3.1 2.31.91-0ubuntu3.1
2010-10-19 10:15:57 status unpacked gconf2 2.31.91-0ubuntu3.1
2010-10-19 10:15:57 status unpacked gconf2 2.31.91-0ubuntu3.1
2010-10-19 10:15:57 status half-configured gconf2 2.31.91-0ubuntu3.1
2010-10-19 10:16:02 status installed gconf2 2.31.91-0ubuntu3.1
2010-10-19 10:16:02 configure gdm-guest-session 0.17 0.17
2010-10-19 10:16:02 status unpacked gdm-guest-session 0.17
2010-10-19 10:16:02 status unpacked gdm-guest-session 0.17
2010-10-19 10:16:02 status half-configured gdm-guest-session 0.17
2010-10-19 10:16:02 status installed gdm-guest-session 0.17
2010-10-19 10:16:02 configure jockey-common 0.5.10-0ubuntu5.1 0.5.10-0ubuntu5.1
2010-10-19 10:16:02 status unpacked jockey-common 0.5.10-0ubuntu5.1
2010-10-19 10:16:02 status unpacked jockey-common 0.5.10-0ubuntu5.1
2010-10-19 10:16:02 status unpacked jockey-common 0.5.10-0ubuntu5.1
2010-10-19 10:16:02 status half-configured jockey-common 0.5.10-0ubuntu5.1
2010-10-19 10:16:03 status installed jockey-common 0.5.10-0ubuntu5.1
2010-10-19 10:16:03 status triggers-pending python-central 0.6.15ubuntu2
2010-10-19 10:16:03 status triggers-awaited jockey-common 0.5.10-0ubuntu5.1
2010-10-19 10:16:03 configure libgudev-1.0-0 1:162-2.1 1:162-2.1
2010-10-19 10:16:03 status unpacked libgudev-1.0-0 1:162-2.1
2010-10-19 10:16:03 status half-configured libgudev-1.0-0 1:162-2.1
2010-10-19 10:16:03 status installed libgudev-1.0-0 1:162-2.1
2010-10-19 10:16:03 configure libutouch-grail1 1.0.15-0ubuntu1 1.0.15-0ubuntu1
2010-10-19 10:16:03 status unpacked libutouch-grail1 1.0.15-0ubuntu1
2010-10-19 10:16:03 status half-configured libutouch-grail1 1.0.15-0ubuntu1
2010-10-19 10:16:03 status installed libutouch-grail1 1.0.15-0ubuntu1
2010-10-19 10:16:03 configure ubuntu-tweak 0.5.7-1~maverick1 0.5.7-1~maverick1
2010-10-19 10:16:03 status unpacked ubuntu-tweak 0.5.7-1~maverick1
2010-10-19 10:16:03 status unpacked ubuntu-tweak 0.5.7-1~maverick1
2010-10-19 10:16:03 status half-configured ubuntu-tweak 0.5.7-1~maverick1
2010-10-19 10:16:04 status installed ubuntu-tweak 0.5.7-1~maverick1
2010-10-19 10:16:04 status triggers-awaited ubuntu-tweak 0.5.7-1~maverick1
2010-10-19 10:16:04 configure gnome-settings-daemon 2.32.0-0ubuntu3 2.32.0-0ubuntu3
2010-10-19 10:16:04 status unpacked gnome-settings-daemon 2.32.0-0ubuntu3
2010-10-19 10:16:04 status unpacked gnome-settings-daemon 2.32.0-0ubuntu3
2010-10-19 10:16:04 status unpacked gnome-settings-daemon 2.32.0-0ubuntu3
2010-10-19 10:16:04 status unpacked gnome-settings-daemon 2.32.0-0ubuntu3
2010-10-19 10:16:04 status unpacked gnome-settings-daemon 2.32.0-0ubuntu3
2010-10-19 10:16:04 status unpacked gnome-settings-daemon 2.32.0-0ubuntu3
2010-10-19 10:16:04 status unpacked gnome-settings-daemon 2.32.0-0ubuntu3
2010-10-19 10:16:04 status unpacked gnome-settings-daemon 2.32.0-0ubuntu3
2010-10-19 10:16:04 status half-configured gnome-settings-daemon 2.32.0-0ubuntu3
2010-10-19 10:16:04 status installed gnome-settings-daemon 2.32.0-0ubuntu3
2010-10-19 10:16:04 trigproc python-central 0.6.15ubuntu2 0.6.15ubuntu2
2010-10-19 10:16:04 status half-configured python-central 0.6.15ubuntu2
2010-10-19 10:16:04 status installed ubuntu-tweak 0.5.7-1~maverick1
2010-10-19 10:16:04 status installed jockey-common 0.5.10-0ubuntu5.1
2010-10-19 10:16:04 status installed python-central 0.6.15ubuntu2
2010-10-19 10:16:05 configure jockey-gtk 0.5.10-0ubuntu5.1 0.5.10-0ubuntu5.1
2010-10-19 10:16:05 status unpacked jockey-gtk 0.5.10-0ubuntu5.1
2010-10-19 10:16:05 status unpacked jockey-gtk 0.5.10-0ubuntu5.1
2010-10-19 10:16:05 status half-configured jockey-gtk 0.5.10-0ubuntu5.1
2010-10-19 10:16:05 status installed jockey-gtk 0.5.10-0ubuntu5.1
2010-10-19 10:16:05 trigproc libc-bin 2.12.1-0ubuntu7 2.12.1-0ubuntu7
2010-10-19 10:16:05 status half-configured libc-bin 2.12.1-0ubuntu7
2010-10-19 10:16:05 status installed libc-bin 2.12.1-0ubuntu7
2010-10-19 10:16:06 trigproc initramfs-tools 0.98.1ubuntu6 0.98.1ubuntu6
2010-10-19 10:16:06 status half-configured initramfs-tools 0.98.1ubuntu6
2010-10-19 10:16:14 status installed initramfs-tools 0.98.1ubuntu6
2010-10-19 10:36:33 startup packages remove
2010-10-19 10:36:33 status installed alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-19 10:36:33 remove alsa-base 1.0.23+dfsg-1ubuntu4 1.0.23+dfsg-1ubuntu4
2010-10-19 10:36:33 status half-configured alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-19 10:36:33 status half-installed alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-19 10:36:33 status config-files alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-19 10:36:33 status config-files alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-19 10:36:33 status installed alsa-utils 1.0.23-2ubuntu3
2010-10-19 10:36:33 remove alsa-utils 1.0.23-2ubuntu3 1.0.23-2ubuntu3
2010-10-19 10:36:33 status half-configured alsa-utils 1.0.23-2ubuntu3
2010-10-19 10:36:33 status half-installed alsa-utils 1.0.23-2ubuntu3
2010-10-19 10:36:34 status triggers-pending ureadahead 0.100.0-8
2010-10-19 10:36:34 status half-installed alsa-utils 1.0.23-2ubuntu3
2010-10-19 10:36:34 status triggers-pending ureadahead 0.100.0-8
2010-10-19 10:36:34 status triggers-pending man-db 2.5.7-4
2010-10-19 10:36:34 status half-installed alsa-utils 1.0.23-2ubuntu3
2010-10-19 10:36:34 status config-files alsa-utils 1.0.23-2ubuntu3
2010-10-19 10:36:34 status config-files alsa-utils 1.0.23-2ubuntu3
2010-10-19 10:36:34 trigproc ureadahead 0.100.0-8 0.100.0-8
2010-10-19 10:36:34 status half-configured ureadahead 0.100.0-8
2010-10-19 10:36:34 status installed ureadahead 0.100.0-8
2010-10-19 10:36:34 trigproc man-db 2.5.7-4 2.5.7-4
2010-10-19 10:36:34 status half-configured man-db 2.5.7-4
2010-10-19 10:36:35 status installed man-db 2.5.7-4
2010-10-19 10:36:36 startup packages purge
2010-10-19 10:36:36 status installed linux-sound-base 1.0.23+dfsg-1ubuntu4
2010-10-19 10:36:36 remove linux-sound-base 1.0.23+dfsg-1ubuntu4 1.0.23+dfsg-1ubuntu4
2010-10-19 10:36:36 status half-configured linux-sound-base 1.0.23+dfsg-1ubuntu4
2010-10-19 10:36:36 status half-installed linux-sound-base 1.0.23+dfsg-1ubuntu4
2010-10-19 10:36:36 status config-files linux-sound-base 1.0.23+dfsg-1ubuntu4
2010-10-19 10:36:36 purge linux-sound-base 1.0.23+dfsg-1ubuntu4 1.0.23+dfsg-1ubuntu4
2010-10-19 10:36:36 status config-files linux-sound-base 1.0.23+dfsg-1ubuntu4
2010-10-19 10:36:36 status config-files linux-sound-base 1.0.23+dfsg-1ubuntu4
2010-10-19 10:36:36 status config-files linux-sound-base 1.0.23+dfsg-1ubuntu4
2010-10-19 10:36:37 status config-files linux-sound-base 1.0.23+dfsg-1ubuntu4
2010-10-19 10:36:37 status config-files linux-sound-base 1.0.23+dfsg-1ubuntu4
2010-10-19 10:36:37 status not-installed linux-sound-base <none>
2010-10-19 10:37:54 startup packages purge
2010-10-19 10:37:54 status config-files alsa-utils 1.0.23-2ubuntu3
2010-10-19 10:37:54 remove alsa-utils 1.0.23-2ubuntu3 1.0.23-2ubuntu3
2010-10-19 10:37:54 purge alsa-utils 1.0.23-2ubuntu3 1.0.23-2ubuntu3
2010-10-19 10:37:54 status config-files alsa-utils 1.0.23-2ubuntu3
2010-10-19 10:37:55 status config-files alsa-utils 1.0.23-2ubuntu3
2010-10-19 10:37:55 status config-files alsa-utils 1.0.23-2ubuntu3
2010-10-19 10:37:55 status config-files alsa-utils 1.0.23-2ubuntu3
2010-10-19 10:37:55 status triggers-pending ureadahead 0.100.0-8
2010-10-19 10:37:55 status config-files alsa-utils 1.0.23-2ubuntu3
2010-10-19 10:37:55 status config-files alsa-utils 1.0.23-2ubuntu3
2010-10-19 10:37:55 status not-installed alsa-utils <none>
2010-10-19 10:37:55 trigproc ureadahead 0.100.0-8 0.100.0-8
2010-10-19 10:37:55 status half-configured ureadahead 0.100.0-8
2010-10-19 10:37:55 status installed ureadahead 0.100.0-8
2010-10-19 10:41:02 startup archives unpack
2010-10-19 10:41:02 install linux-sound-base <none> 1.0.23+dfsg-1ubuntu4
2010-10-19 10:41:02 status half-installed linux-sound-base 1.0.23+dfsg-1ubuntu4
2010-10-19 10:41:03 status unpacked linux-sound-base 1.0.23+dfsg-1ubuntu4
2010-10-19 10:41:03 status unpacked linux-sound-base 1.0.23+dfsg-1ubuntu4
2010-10-19 10:41:03 install alsa-base 1.0.23+dfsg-1ubuntu4 1.0.23+dfsg-1ubuntu4
2010-10-19 10:41:03 status half-installed alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-19 10:41:04 status unpacked alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-19 10:41:04 status unpacked alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-19 10:41:04 install alsa-utils <none> 1.0.23-2ubuntu3
2010-10-19 10:41:04 status half-installed alsa-utils 1.0.23-2ubuntu3
2010-10-19 10:41:04 status triggers-pending man-db 2.5.7-4
2010-10-19 10:41:04 status half-installed alsa-utils 1.0.23-2ubuntu3
2010-10-19 10:41:04 status triggers-pending ureadahead 0.100.0-8
2010-10-19 10:41:04 status half-installed alsa-utils 1.0.23-2ubuntu3
2010-10-19 10:41:04 status triggers-pending ureadahead 0.100.0-8
2010-10-19 10:41:05 status unpacked alsa-utils 1.0.23-2ubuntu3
2010-10-19 10:41:05 status unpacked alsa-utils 1.0.23-2ubuntu3
2010-10-19 10:41:05 trigproc man-db 2.5.7-4 2.5.7-4
2010-10-19 10:41:05 status half-configured man-db 2.5.7-4
2010-10-19 10:41:06 status installed man-db 2.5.7-4
2010-10-19 10:41:06 trigproc ureadahead 0.100.0-8 0.100.0-8
2010-10-19 10:41:06 status half-configured ureadahead 0.100.0-8
2010-10-19 10:41:06 status installed ureadahead 0.100.0-8
2010-10-19 10:41:06 startup packages configure
2010-10-19 10:41:06 configure linux-sound-base 1.0.23+dfsg-1ubuntu4 1.0.23+dfsg-1ubuntu4
2010-10-19 10:41:06 status unpacked linux-sound-base 1.0.23+dfsg-1ubuntu4
2010-10-19 10:41:06 status half-configured linux-sound-base 1.0.23+dfsg-1ubuntu4
2010-10-19 10:41:07 status installed linux-sound-base 1.0.23+dfsg-1ubuntu4
2010-10-19 10:41:07 configure alsa-base 1.0.23+dfsg-1ubuntu4 1.0.23+dfsg-1ubuntu4
2010-10-19 10:41:07 status unpacked alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-19 10:41:07 status unpacked alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-19 10:41:07 status unpacked alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-19 10:41:07 status unpacked alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-19 10:41:07 status half-configured alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-19 10:41:07 status installed alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-19 10:41:08 configure alsa-utils 1.0.23-2ubuntu3 1.0.23-2ubuntu3
2010-10-19 10:41:08 status unpacked alsa-utils 1.0.23-2ubuntu3
2010-10-19 10:41:08 status unpacked alsa-utils 1.0.23-2ubuntu3
2010-10-19 10:41:08 status half-configured alsa-utils 1.0.23-2ubuntu3
2010-10-19 10:41:08 status installed alsa-utils 1.0.23-2ubuntu3
2010-10-19 12:09:55 startup packages purge
2010-10-19 12:09:55 status installed alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-19 12:09:56 remove alsa-base 1.0.23+dfsg-1ubuntu4 1.0.23+dfsg-1ubuntu4
2010-10-19 12:09:56 status half-configured alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-19 12:09:56 status half-installed alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-19 12:09:56 status config-files alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-19 12:09:56 purge alsa-base 1.0.23+dfsg-1ubuntu4 1.0.23+dfsg-1ubuntu4
2010-10-19 12:09:56 status config-files alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-19 12:09:56 status config-files alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-19 12:09:56 status config-files alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-19 12:09:56 status config-files alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-19 12:09:56 status config-files alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-19 12:09:56 status not-installed alsa-base <none>
2010-10-19 12:09:56 status installed alsa-utils 1.0.23-2ubuntu3
2010-10-19 12:09:56 remove alsa-utils 1.0.23-2ubuntu3 1.0.23-2ubuntu3
2010-10-19 12:09:56 status half-configured alsa-utils 1.0.23-2ubuntu3
2010-10-19 12:09:56 status half-installed alsa-utils 1.0.23-2ubuntu3
2010-10-19 12:09:56 status triggers-pending ureadahead 0.100.0-8
2010-10-19 12:09:56 status half-installed alsa-utils 1.0.23-2ubuntu3
2010-10-19 12:09:56 status triggers-pending ureadahead 0.100.0-8
2010-10-19 12:09:57 status triggers-pending man-db 2.5.7-4
2010-10-19 12:09:57 status half-installed alsa-utils 1.0.23-2ubuntu3
2010-10-19 12:09:57 status config-files alsa-utils 1.0.23-2ubuntu3
2010-10-19 12:09:57 purge alsa-utils 1.0.23-2ubuntu3 1.0.23-2ubuntu3
2010-10-19 12:09:57 status config-files alsa-utils 1.0.23-2ubuntu3
2010-10-19 12:09:57 status config-files alsa-utils 1.0.23-2ubuntu3
2010-10-19 12:09:57 status config-files alsa-utils 1.0.23-2ubuntu3
2010-10-19 12:09:57 status config-files alsa-utils 1.0.23-2ubuntu3
2010-10-19 12:09:57 status config-files alsa-utils 1.0.23-2ubuntu3
2010-10-19 12:09:57 status config-files alsa-utils 1.0.23-2ubuntu3
2010-10-19 12:09:57 status not-installed alsa-utils <none>
2010-10-19 12:09:57 status installed linux-sound-base 1.0.23+dfsg-1ubuntu4
2010-10-19 12:09:57 remove linux-sound-base 1.0.23+dfsg-1ubuntu4 1.0.23+dfsg-1ubuntu4
2010-10-19 12:09:57 status half-configured linux-sound-base 1.0.23+dfsg-1ubuntu4
2010-10-19 12:09:57 status half-installed linux-sound-base 1.0.23+dfsg-1ubuntu4
2010-10-19 12:09:57 status config-files linux-sound-base 1.0.23+dfsg-1ubuntu4
2010-10-19 12:09:57 purge linux-sound-base 1.0.23+dfsg-1ubuntu4 1.0.23+dfsg-1ubuntu4
2010-10-19 12:09:57 status config-files linux-sound-base 1.0.23+dfsg-1ubuntu4
2010-10-19 12:09:58 status config-files linux-sound-base 1.0.23+dfsg-1ubuntu4
2010-10-19 12:09:58 status config-files linux-sound-base 1.0.23+dfsg-1ubuntu4
2010-10-19 12:09:58 status config-files linux-sound-base 1.0.23+dfsg-1ubuntu4
2010-10-19 12:09:58 status config-files linux-sound-base 1.0.23+dfsg-1ubuntu4
2010-10-19 12:09:58 status not-installed linux-sound-base <none>
2010-10-19 12:09:58 trigproc ureadahead 0.100.0-8 0.100.0-8
2010-10-19 12:09:58 status half-configured ureadahead 0.100.0-8
2010-10-19 12:09:58 status installed ureadahead 0.100.0-8
2010-10-19 12:09:58 trigproc man-db 2.5.7-4 2.5.7-4
2010-10-19 12:09:58 status half-configured man-db 2.5.7-4
2010-10-19 12:09:59 status installed man-db 2.5.7-4
2010-10-19 12:10:44 startup archives unpack
2010-10-19 12:10:45 install linux-sound-base <none> 1.0.23+dfsg-1ubuntu4
2010-10-19 12:10:45 status half-installed linux-sound-base 1.0.23+dfsg-1ubuntu4
2010-10-19 12:10:45 status unpacked linux-sound-base 1.0.23+dfsg-1ubuntu4
2010-10-19 12:10:45 status unpacked linux-sound-base 1.0.23+dfsg-1ubuntu4
2010-10-19 12:10:45 install alsa-base <none> 1.0.23+dfsg-1ubuntu4
2010-10-19 12:10:45 status half-installed alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-19 12:10:46 status unpacked alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-19 12:10:46 status unpacked alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-19 12:10:46 install alsa-utils <none> 1.0.23-2ubuntu3
2010-10-19 12:10:46 status half-installed alsa-utils 1.0.23-2ubuntu3
2010-10-19 12:10:46 status triggers-pending man-db 2.5.7-4
2010-10-19 12:10:46 status half-installed alsa-utils 1.0.23-2ubuntu3
2010-10-19 12:10:46 status triggers-pending ureadahead 0.100.0-8
2010-10-19 12:10:46 status half-installed alsa-utils 1.0.23-2ubuntu3
2010-10-19 12:10:46 status triggers-pending ureadahead 0.100.0-8
2010-10-19 12:10:47 status unpacked alsa-utils 1.0.23-2ubuntu3
2010-10-19 12:10:47 status unpacked alsa-utils 1.0.23-2ubuntu3
2010-10-19 12:10:47 trigproc man-db 2.5.7-4 2.5.7-4
2010-10-19 12:10:47 status half-configured man-db 2.5.7-4
2010-10-19 12:10:48 status installed man-db 2.5.7-4
2010-10-19 12:10:48 trigproc ureadahead 0.100.0-8 0.100.0-8
2010-10-19 12:10:48 status half-configured ureadahead 0.100.0-8
2010-10-19 12:10:48 status installed ureadahead 0.100.0-8
2010-10-19 12:10:49 startup packages configure
2010-10-19 12:10:49 configure linux-sound-base 1.0.23+dfsg-1ubuntu4 1.0.23+dfsg-1ubuntu4
2010-10-19 12:10:49 status unpacked linux-sound-base 1.0.23+dfsg-1ubuntu4
2010-10-19 12:10:49 status half-configured linux-sound-base 1.0.23+dfsg-1ubuntu4
2010-10-19 12:10:49 status installed linux-sound-base 1.0.23+dfsg-1ubuntu4
2010-10-19 12:10:49 configure alsa-base 1.0.23+dfsg-1ubuntu4 1.0.23+dfsg-1ubuntu4
2010-10-19 12:10:49 status unpacked alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-19 12:10:49 status unpacked alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-19 12:10:49 status unpacked alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-19 12:10:49 status unpacked alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-19 12:10:49 status half-configured alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-19 12:10:49 status installed alsa-base 1.0.23+dfsg-1ubuntu4
2010-10-19 12:10:50 configure alsa-utils 1.0.23-2ubuntu3 1.0.23-2ubuntu3
2010-10-19 12:10:50 status unpacked alsa-utils 1.0.23-2ubuntu3
2010-10-19 12:10:50 status unpacked alsa-utils 1.0.23-2ubuntu3
2010-10-19 12:10:50 status half-configured alsa-utils 1.0.23-2ubuntu3
2010-10-19 12:10:50 status installed alsa-utils 1.0.23-2ubuntu3
2010-10-19 12:12:21 startup archives unpack
2010-10-19 12:12:21 install ubuntu-desktop <none> 1.207
2010-10-19 12:12:21 status half-installed ubuntu-desktop 1.207
2010-10-19 12:12:22 status unpacked ubuntu-desktop 1.207
2010-10-19 12:12:22 status unpacked ubuntu-desktop 1.207
2010-10-19 12:12:23 startup packages configure
2010-10-19 12:12:23 configure ubuntu-desktop 1.207 1.207
2010-10-19 12:12:23 status unpacked ubuntu-desktop 1.207
2010-10-19 12:12:23 status half-configured ubuntu-desktop 1.207
2010-10-19 12:12:23 status installed ubuntu-desktop 1.207
2010-10-20 07:59:18 startup archives unpack
2010-10-20 07:59:19 install udo <none> 6.4.1-1
2010-10-20 07:59:19 status half-installed udo 6.4.1-1
2010-10-20 07:59:19 status triggers-pending man-db 2.5.7-4
2010-10-20 07:59:19 status half-installed udo 6.4.1-1
2010-10-20 07:59:20 status unpacked udo 6.4.1-1
2010-10-20 07:59:20 status unpacked udo 6.4.1-1
2010-10-20 07:59:20 trigproc man-db 2.5.7-4 2.5.7-4
2010-10-20 07:59:20 status half-configured man-db 2.5.7-4
2010-10-20 07:59:21 status installed man-db 2.5.7-4
2010-10-20 07:59:21 startup packages configure
2010-10-20 07:59:21 configure udo 6.4.1-1 6.4.1-1
2010-10-20 07:59:21 status unpacked udo 6.4.1-1
2010-10-20 07:59:21 status half-configured udo 6.4.1-1
2010-10-20 07:59:21 status installed udo 6.4.1-1
```

---

### Post by typos1 on 2010-10-20
Well, I ve ried loads more things: 

Googled the problem and found something about sound going in 10.10 for some reason and that the way to get it back was to go to admin/users&groups/advanced/user privileges and check "audio devices" if unchecked. Mine was unchecked, so checked it and...still no sound : ( 

I m using Avant Window Manager so I d deleted the top panel (and therefore volume icon/applet in it) not long before sound went, was wondering if the disappearance of the icon might be the problem. Uninstalled all pulseaudio stuff, then reinstalled it all, including the icon/applet, still no sound (and still no icon/applet, even though it was reinstalled) : ( 

Was going to try and uninstall all ALSA stuff, but couldnt find anything installed in software centre, so I tried installing ALSAmixer, still no sound. 

Then I discovered that "pulseaudio volumecontrol" was in apps/sound&video, opened it and found volume muted, unmuted it and SOUND!! 

It sorted my problem anyway, well the little red cross over the speaker showing its muted is still there, but it ISNT muted and at least I have sound. 

Does it or anything else sort anyone elses?

---

### Post by P4man on 2010-10-20
yeah the muted sound might have been the OP's original problem, but running the alsa update script, he now has another one since alsa is no longer running or detecting any audiocards. Unmute wont help for him. Reinstalling I guess would if no one has a better idea.

---

### Post by typos1 on 2010-10-20
Well my problem was something different-it appears that removing the icon/applet removed pusleaudio volume control altogether, hence no sound. 

Sorry if this doesnt help the op, but I m sorted, good luck with your problem Paulgirardin.

---

### Post by Paulgirardin on 2010-10-20
News:
Update manager performed a routine kernal update and the missing items have returned,but the sound is still out.
I am considering a reinstall.

---

### Post by P4man on 2010-10-20
> **Paulgirardin said:**
> News:
Update manager performed a routine kernal update and the missing items have returned,but the sound is still out.
I am considering a reinstall.

Does aplay -l now report audio cards? In that case, check your mixer settings. Then its probably a trivial issue.

---

### Post by HDTimeshifter on 2010-10-25
> **P4man said:**
> That seems like a nasty bug in that script, if thats what removed alsa.

Id just try try reinstalling alsa;

```
sudo apt-get install linux-sound-base alsa-base alsa-utils
```

The script tried updating it to the same version you already had, so dont bother trying that again and perhaps report the bug to the author.

I have no sound in 10.10 either.  I just did a fresh install of Ubuntu 10.10 on a new drive and have no sound.  I rebooted and the sound control panel sound test worked, but after I loaded a browser and a flash window, the sound stopped working.  Strange as I thought it worked on my other drive that was upgraded to 10.10.  I tried reinstalling as above, but now get no sound at all.

---

### Post by lidex on 2010-10-25
> **HDTimeshifter said:**
> I have no sound in 10.10 either.  I just did a fresh install of Ubuntu 10.10 on a new drive and have no sound.  I rebooted and the sound control panel sound test worked, but after I loaded a browser and a flash window, the sound stopped working.  Strange as I thought it worked on my other drive that was upgraded to 10.10.  I tried reinstalling as above, but now get no sound at all.

What is this output:
```
sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
```

Try this:
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Logout/in.**
(Removes old audio config files)

---

### Post by HDTimeshifter on 2010-11-03
Well, I installed 64-bit Windows 7 on another hard drive, and after getting that all configured, I had no sound in Firefox with Flash either, however the sound control panel allowed test sounds to play through the satellite speakers.  Then I rebooted to the 64-bit Ubuntu drive and I got sound again.  Weird.  I rebooted to the Windows drive and no sound there, but upon opening the sound control panel, selected S/PDIF and got sound there as well.  Apparently, even though S/PDIF, HDMI, and a couple other sound drivers/options were displayed, I actually hadn't selected a driver.

Dunno why sound stopped working for a while in Ubuntu 10.10, but everything is good now.

---

### Post by blazemiskulin on 2010-11-10
I, too, have this problem, and after much mucking about, I've discovered that it *is* Flash that's causing the problem.  I just don't know how to fix it.  :)

Yesterday (in Karmic) I updated Flash in order to watch videos on Hulu.  I lost my sound.  I decided it was a good time to upgrade to Lucid, so I did so.  Still no sound (and Songbird died).

Nothing is muted in Alsamixer.

I could go into System Settings and play test sounds on the analog outputs (I have no digital sound devices), but YouTube wouldn't play sounds.

Reboot, and sound comes back for a while.  I watched a couple vids in MPlayer, and the sound worked fine.  Went to sleep, got up... no sound again--the very last thing I was doing last night was watching a video (MPlayer), sound just stopped on it's own.

Today... I muck about with settings some more, try to test sound, and get it to come back in the System Settings test mode.  Play a video in MPlayer; it has sound.  Try to play Songbird; no sound.  Try a video again; it has sound.  Try YouTube; no sound.  Go back to the same MPlayer video (20 seconds later)... And the sound is dead.  Wait a couple minutes (to write this far), test in System Settings and I have sound.  Test the MPlayer, I have sound. Play Songbird; no sound.  Try the MPlayer again, no sound.

And... to wrap it up, I just tried to test in System Settings, and I get "device does not work" on both of the analog options.

This is *very* frustrating.

I've dug through the forums here and done my best with websearches. This is the only place I've seen this listed.  Any help or pointers would be greatly appreciated.

---

### Post by lidex on 2010-11-10
Try resetting your pulse config.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Logout/in.**

No joy? Run theses commands and post the terminal output:
```
sudo alsa force-reload
pkill pulseaudio; sleep 2; pulseaudio -vv
```

---

### Post by nestor77 on 2010-11-25
I have i.386 computer and Ubuntu 10.10
after upgrading I lost the sound
The following information works for me:

Just a hint to spare the time of the next who may experience this: when  using a SDL 1.2.14 built from sources (with options  --enable-video-directfb=no --disable-rpath --prefix=XXX  -exec-prefix=YYY), at least on Ubuntu Maverick, with the resulting  library no sound was available ("No available audio device"). 
 
I could check that PulseAudio was activated and running  (/usr/bin/pulseaudio --start --log-target=syslog), but at SDL  configuration-time the PulseAudio support got nevertheless deactivated: 
 
""" 
checking for ALSA CFLAGS...  
checking for ALSA LDFLAGS... -lasound -lm -ldl -lpthread  
checking for libasound headers version >= 0.9.0... not present.  
checking for snd_ctl_open in -lasound... no  
checking for artsc-config... no  
checking for esd-config... no  
checking for ESD - version >= 0.2.8... no  
*** The esd-config script installed by ESD could not be found  
*** If ESD was installed in PREFIX, make sure PREFIX/bin is in  
*** your path, or set the ESD_CONFIG environment variable to the  
*** full path to esd-config.  
checking for pkg-config... /usr/bin/pkg-config  
[B]checking for PulseAudio 0.9 support... no  
[/B]checking audio/audiolib.h usability... no  
checking audio/audiolib.h presence... no  
checking for audio/audiolib.h... no  
checking for AuOpenServer in -laudio... no  
""" 
 
After some investigation, to enable PulseAudio support in the resulting  library, you must have libpulse-simple.* files, which are provided by  the [SIZE=4]**[COLOR=Black]libpulse-dev[/COLOR]**[/SIZE] package. 
 
Then build and execution works as expected (with proper sound). 
 
Best regards, 
 
Olivier Boudeville.

---

### Post by pandeiro on 2010-12-21
Bump... I'm having this issue too. Sound is working at boot but after watching less than 5 minutes of Flash video online, it stops.

Is there any new information on this? Did the OP ever resolve this?

Thanks

---

### Post by pandeiro on 2010-12-23
Following up, lidex's first code snippet did the trick. I don't have asound installed but clearing the pulseaudio and cache folders got everything working again.

---

