---
title: "No Sound Through Speakers, only through Bluetooth"
date: 2012-01-14
forum: Multimedia Software
---

### Post by maxietom on 2012-01-14
I recently upgraded my motherboard to an Asus M5A97, since my old board was about 5 years old and was getting slow because of Unity and Gnome 3's heavy RAM useage. (I only had one gig)

I originally had sound after my upgrade, but then I ran an update, and the sound didn't work. I'm not entirely sure what the update was, but it knocked out my sound. I've tried reinstalling PulseAudio, ALSA, ALSAMixer, etc, but it refuses to work. Alsamixer gives me an error saying **cannot load mixer controls: Invalid argument**. The sounds settings detects my sound card, and my bluetooth headset. The headset gets sound perfectly fine, so I'm guessing it's a missing module for ALSA. I tried upgrading to the 3.2 linux kernel, but that didn't help. If I have to, I'll revert back to 3.0.0-14.

My sound card is a RealTek "Azalia" ALC887-VD with HD Digital Sound.

Alsa-Info:

```

upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Sat Jan 14 21:43:17 UTC 2012


!!Linux Distribution
!!------------------

Ubuntu 11.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 11.10"


!!DMI Information
!!---------------

Manufacturer:      To be filled by O.E.M.
Product Name:      To be filled by O.E.M.
Product Version:   To be filled by O.E.M.


!!Kernel Information
!!------------------

Kernel release:    3.2.0-9-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         x86_64
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.24
Library version:    1.0.24.1
Utilities version:  1.0.24.2


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

 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfe300000 irq 16


!!PCI Soundcards installed in the system
!!--------------------------------------

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

00:14.2 0403: 1002:4383 (rev 40)
	Subsystem: 1043:8444


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
!!--------------------------

!!Module: snd_hda_intel
	align_buffer_size : Y
	bdl_pos_adj : 32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	beep_mode : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	enable_msi : -1
	id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	model : 6stack-dig,(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	patch : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	position_fix : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	power_save : 0
	power_save_controller : Y
	probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	single_cmd : N
	snoop : Y


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: Realtek ALC887-VD
Address: 0
AFG Function Id: 0x1 (unsol 1)
Vendor Id: 0x10ec0887
Subsystem Id: 0x10438444
Revision Id: 0x100302
No Modem Function Group found
Default PCM:
    rates [0x5f0]: 32000 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=2, o=0, i=0, unsolicited=1, wake=0
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Node 0x02 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Device: name="ALC887-VD Analog", type="Audio", device=0
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x40 0x40]
  Converter: stream=8, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x03 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x40 0x40]
  Converter: stream=8, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x04 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x40 0x40]
  Converter: stream=8, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x05 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x40 0x40]
  Converter: stream=8, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x06 [Audio Output] wcaps 0x611: Stereo Digital
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Control: name="IEC958 Default PCM Playback Switch", index=0, device=0
  Device: name="ALC887-VD Digital", type="SPDIF", device=1
  Converter: stream=8, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x5f0]: 32000 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x07 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x08 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Control: name="Capture Switch", index=0, device=0
  Control: name="Capture Volume", index=0, device=0
  Device: name="ALC887-VD Analog", type="Audio", device=0
  Amp-In caps: ofs=0x10, nsteps=0x2e, stepsize=0x03, mute=1
  Amp-In vals:  [0x10 0x10]
  Converter: stream=4, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x23
Node 0x09 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Control: name="Capture Switch", index=1, device=0
  Control: name="Capture Volume", index=1, device=0
  Device: name="ALC887-VD Analog", type="Audio", device=2
  Amp-In caps: ofs=0x10, nsteps=0x2e, stepsize=0x03, mute=1
  Amp-In vals:  [0x80 0x80]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x22
Node 0x0a [Audio Input] wcaps 0x100711: Stereo Digital
  Control: name="IEC958 Capture Switch", index=0, device=0
  Control: name="IEC958 Capture Default", index=0, device=0
  Device: name="ALC887-VD Digital", type="SPDIF", device=1
  Converter: stream=0, channel=0
  SDI-Select: 0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x1f
Node 0x0b [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="CD Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=4, ofs=0
  Control: name="CD Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=4, ofs=0
  Control: name="Line Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Control: name="Line Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Control: name="Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Front Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=1, ofs=0
  Control: name="Front Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=1, ofs=0
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 10
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17
Node 0x0c [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Front Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x02 0x0b
Node 0x0d [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Surround Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x03 0x0b
Node 0x0e [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Center Playback Volume", index=0, device=0
    ControlAmp: chs=1, dir=Out, idx=0, ofs=0
  Control: name="LFE Playback Volume", index=0, device=0
    ControlAmp: chs=2, dir=Out, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x04 0x0b
Node 0x0f [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Side Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x05 0x0b
Node 0x10 [Audio Output] wcaps 0x611: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x5f0]: 32000 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x11 [Pin Complex] wcaps 0x400781: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x01456130: [Jack] SPDIF Out at Ext Rear
    Conn = Optical, Color = Orange
    DefAssociation = 0x3, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x10
Node 0x12 [Pin Complex] wcaps 0x400401: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x13 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x14 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0001003e: IN OUT HP EAPD Detect Trigger
  EAPD 0x2: EAPD
  Pin Default 0x01014010: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Green
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x0c
Node 0x15 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x00000036: IN OUT Detect Trigger
  Pin Default 0x01011012: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0x1, Sequence = 0x2
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x0d
Node 0x16 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x00000036: IN OUT Detect Trigger
  Pin Default 0x01016011: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Orange
    DefAssociation = 0x1, Sequence = 0x1
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x0e
Node 0x17 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x00000036: IN OUT Detect Trigger
  Pin Default 0x01012014: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Grey
    DefAssociation = 0x1, Sequence = 0x4
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x0f
Node 0x18 [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Control: name="Mic Boost Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00003736: IN OUT Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x01a19850: [Jack] Mic at Ext Rear
    Conn = 1/8, Color = Pink
    DefAssociation = 0x5, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x19 [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Control: name="Front Mic Boost Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000373e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x02a19c60: [Jack] Mic at Ext Front
    Conn = 1/8, Color = Pink
    DefAssociation = 0x6, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1a [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00003736: IN OUT Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x0181305f: [Jack] Line In at Ext Rear
    Conn = 1/8, Color = Blue
    DefAssociation = 0x5, Sequence = 0xf
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1b [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Control: name="Headphone Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0001373e: IN OUT HP EAPD Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  EAPD 0x2: EAPD
  Pin Default 0x02214c20: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Green
    DefAssociation = 0x2, Sequence = 0x0
  Pin-ctls: 0xc0: OUT HP VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1c [Pin Complex] wcaps 0x400481: Stereo
  Pincap 0x00000024: IN Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x1d [Pin Complex] wcaps 0x400400: Mono
  Pincap 0x00000020: IN
  Pin Default 0x4005e601: [N/A] Line Out at Ext N/A
    Conn = Optical, Color = White
    DefAssociation = 0x0, Sequence = 0x1
  Pin-ctls: 0x20: IN
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x1e [Pin Complex] wcaps 0x400781: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x99430140: [Fixed] SPDIF Out at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0x4, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x06
Node 0x1f [Pin Complex] wcaps 0x400681: Stereo Digital
  Pincap 0x00000020: IN
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x20 [Vendor Defined Widget] wcaps 0xf00040: Mono
  Processing caps: benign=0, ncoeff=24
Node 0x21 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x22 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Input Source", index=1, device=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 12
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b 0x12
Node 0x23 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Input Source", index=0, device=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 11
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b
Node 0x24 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x25 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x40 0x40]
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x26 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80]
  Connection: 2
     0x25 0x0b
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116,  8 Jan 14 12:44 /dev/snd/controlC0
crw-rw----+ 1 root audio 116,  7 Jan 14 12:44 /dev/snd/hwC0D0
crw-rw----+ 1 root audio 116,  6 Jan 14 12:48 /dev/snd/pcmC0D0c
crw-rw----+ 1 root audio 116,  5 Jan 14 13:00 /dev/snd/pcmC0D0p
crw-rw----+ 1 root audio 116,  4 Jan 14 12:44 /dev/snd/pcmC0D1c
crw-rw----+ 1 root audio 116,  3 Jan 14 12:45 /dev/snd/pcmC0D1p
crw-rw----+ 1 root audio 116,  2 Jan 14 12:44 /dev/snd/pcmC0D2c
crw-rw----+ 1 root audio 116,  1 Jan 14 12:44 /dev/snd/seq
crw-rw----+ 1 root audio 116, 33 Jan 14 12:44 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Jan 14 12:44 .
drwxr-xr-x 3 root root 240 Jan 14 12:44 ..
lrwxrwxrwx 1 root root  12 Jan 14 12:44 pci-0000:00:14.2 -> ../controlC0


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC887-VD Analog [ALC887-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC887-VD Digital [ALC887-VD Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC887-VD Analog [ALC887-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC887-VD Digital [ALC887-VD Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 2: ALC887-VD Analog [ALC887-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [SB]

amixer: Mixer load hw:0 error: Invalid argument
Card hw:0 'SB'/'HDA ATI SB at 0xfe300000 irq 16'
  Mixer name	: 'Realtek ALC887-VD'
  Components	: 'HDA:10ec0887,10438444,00100302'
  Controls      : 38
amixer: Mixer hw:0 load error: Invalid argument


!!Alsactl output
!!-------------

--startcollapse--
--endcollapse--


!!All Loaded Modules
!!------------------

Module
rfcomm
bnep
parport_pc
ppdev
binfmt_misc
vesafb
snd_hda_codec_realtek
arc4
snd_hda_intel
snd_hda_codec
snd_hwdep
rt61pci
crc_itu_t
rt2x00pci
rt2x00lib
mac80211
snd_pcm
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
nvidia
snd_seq
snd_timer
snd_seq_device
snd
joydev
btusb
bluetooth
soundcore
cfg80211
sp5100_tco
hid_microsoft
snd_page_alloc
i2c_piix4
eeepc_wmi
edac_core
eeprom_93cx6
k10temp
edac_mce_amd
asus_wmi
sparse_keymap
mac_hid
psmouse
serio_raw
wmi
lp
parport
usb_storage
usbhid
hid
tulip
r8169


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x11 0x01456130
0x12 0x411111f0
0x14 0x01014010
0x15 0x01011012
0x16 0x01016011
0x17 0x01012014
0x18 0x01a19850
0x19 0x02a19c60
0x1a 0x0181305f
0x1b 0x02214c20
0x1c 0x411111f0
0x1d 0x4005e601
0x1e 0x99430140
0x1f 0x411111f0

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:


!!ALSA/HDA dmesg
!!------------------

[   14.171878] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.212379] snd_hda_intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   14.250911] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
--
[   14.636256] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
[   14.641259] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   14.674262] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   14.674317] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   14.674463] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   14.674551] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   14.674857] hda_codec: num_steps = 0 for NID=0xd (ctl = Surround Playback Volume)
[   14.675231] hda_codec: num_steps = 0 for NID=0xe (ctl = Center Playback Volume)
[   14.675276] hda_codec: num_steps = 0 for NID=0xe (ctl = LFE Playback Volume)
[   14.675646] hda_codec: num_steps = 0 for NID=0xf (ctl = Side Playback Volume)
[   14.678249] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   14.938636] vesafb: mode is 1280x1024x32, linelength=5120, pages=0
--
[   17.008583] type=1400 audit(1326573886.734:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=1101 comm="apparmor_parser"
[   17.107332] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   17.107641] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   17.107703] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   17.107784] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   17.107871] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   17.107933] hda_codec: num_steps = 0 for NID=0xd (ctl = Surround Playback Volume)
[   17.107973] hda_codec: num_steps = 0 for NID=0xe (ctl = Center Playback Volume)
[   17.108032] hda_codec: num_steps = 0 for NID=0xe (ctl = LFE Playback Volume)
[   17.108093] hda_codec: num_steps = 0 for NID=0xf (ctl = Side Playback Volume)
[   17.108256] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   17.112614] init: failsafe main process (1013) killed by TERM signal
--
[   20.595566] wlan0: associated
[   20.705301] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   20.714147] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   20.720471] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   20.752360] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   20.800386] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   20.816860] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   20.832757] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   20.860841] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   20.923149] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   20.930501] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   86.612488] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   86.632379] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   93.293329] Bluetooth: hci0 SCO packet for unknown connection handle 0
--
[  250.780293] ehci_hcd 0000:00:12.2: PCI INT B disabled
[  250.829832] snd_hda_intel 0000:00:14.2: PCI INT A disabled
[  250.844286] PM: suspend of drv:snd_hda_intel dev:0000:00:14.2 complete after 118.199 msecs
[  251.226371] PM: suspend of drv:sd dev:0:0:0:0 complete after 877.815 msecs
--
[  251.344319] ehci_hcd 0000:00:13.2: PME# disabled
[  251.344341] snd_hda_intel 0000:00:14.2: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[  251.344353] snd_hda_intel 0000:00:14.2: restoring config space at offset 0x3 (was 0x0, writing 0x2010)
[  251.344385] pci 0000:00:14.4: restoring config space at offset 0x6 (was 0x20040400, writing 0x40040400)
--
[  251.360967] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[  251.360979] snd_hda_intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  251.360999] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
--
[  259.336683] wlan0: associated
[  425.288510] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[  427.746606] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[  916.586089] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[  920.033381] wlan0: deauthenticated from c0:c1:c0:04:d8:93 (Reason: 7)
--
[  922.071934] wlan0: associated
[ 3524.329441] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[ 3524.332402] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[ 3524.667460] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)



```

---

### Post by maxietom on 2012-01-20
Bump

I still haven't made any progress. I did notice that "ESound" is disabled, which apperently combines sounds together instead of having one program use the device. Also, I forgot to mention that the back is a 7.1 surround sound port with 6 spots to place speakers.

But, does anyone have any help to give? It's really hard to use a computer in dead silence. :(

---

### Post by maxietom on 2012-01-24
More progress. It turns out that HDA-Analyzer as well as the Alsa-Info script both say that my audio pins are **muted**. However, I can't unmute them from anything, as Ubuntu's volume is maxed. Does anyone know how to unmute the actual hardware?

---

### Post by maxietom on 2012-02-08
This is ridiculous. It's been almost a month, and I have got no help from launchpad or here. Can someone PLEASE HELP? I'm really annoyed that I can't just get a little bit of help from anyone.

If it helps, here's some pics:
[http://tinypic.com/r/5am1qw/5](http://tinypic.com/r/5am1qw/5)
[http://tinypic.com/r/2mht21c/5](http://tinypic.com/r/2mht21c/5)

---

### Post by MoreOrLess on 2012-02-09
I would try the latest kernel module (it may have been fixed upstream): [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)


> **maxietom said:**
> I did notice that "ESound" is disabled
Esound is ancient/deprecated (pre-pulseaudio days). Also, the mere mention of it sends a chill down my spine similar to the effect of nails on a blackboard.

---

### Post by maxietom on 2012-02-11
Thanks for the reply. However, I tried that, and it didn't work. I checked alsamixer and everything else, and they all are on 100% volume, but still no sound.

I've seen others with my same motherboard that apparently had sound working. Perhaps they switched from Windows to Ubuntu, and they had the drivers installed and configurated to activate the pins, because everything seems to be muted in [hda-analyzer]("http://www.alsa-project.org/main/index.php/HDA_Analyzer"), including the audio pins and mixers. I tried to modify the master volume, but it seems to be read only.

I have an XP disk available, so if I had to, I could make a small 20 GB partition for XP so I can install drivers. Just a thought.

---

