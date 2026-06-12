---
title: "Front speakers stopped working after upgrade to 12.04"
date: 2012-04-29
forum: Multimedia Software
---

### Post by messelink on 2012-04-29
Just as an introduction: before the upgrade to 12.04 I was only able to get surround sound working by using the AlsaUpgrade script to upgrade alsa to 1.0.25. Without that I would have only stereo options in Sounds Settings.

The upgrade to to 12.04 overwrote the alsa on the system back to version 1.0.24, but Sound Settings does show 5.1 output. However, with that selected and using Test Sound only the rear and center/lfe speakers work properly. There is no sound from the front left and right speaker. The alsamixer levels were all okay.

Re-running the AlsaUpgrade script brought the alsa version back to 1.0.25, but the systom is the same: no sound from the front left and right speaker. I really don't understand what can cause this problem. Can anyone shed some light on this?

alsa-info.sh output:
```


!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Sun Apr 29 09:58:03 UTC 2012


!!Linux Distribution
!!------------------

Ubuntu 12.04 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"


!!DMI Information
!!---------------

Manufacturer:      Gigabyte Technology Co., Ltd.
Product Name:      G41MT-S2P
Product Version:    


!!Kernel Information
!!------------------

Kernel release:    3.2.0-24-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         x86_64
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.25
Library version:    1.0.25
Utilities version:  1.0.25


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
                      HDA Intel at 0xfdff8000 irq 43


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:27d8 (rev 01)
	Subsystem: 1458:a014


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
snd-hda-intel: model=3stack


!!Loaded sound module options
!!--------------------------

!!Module: snd_hda_intel
	align_buffer_size : N
	bdl_pos_adj : 1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	beep_mode : 1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	enable_msi : Y
	id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	model : 3stack,(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
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

Codec: VIA VT2020
Address: 2
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x11060441
Subsystem Id: 0x1458a014
Revision Id: 0x100100
No Modem Function Group found
Default PCM:
    rates [0x0]:
    bits [0x0]:
    formats [0x0]:
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=1, o=0, i=0, unsolicited=1, wake=0
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Node 0x08 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Control: name="Front Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Device: name="VT2020 Analog", type="Audio", device=0
  Amp-Out caps: ofs=0x2a, nsteps=0x2a, stepsize=0x05, mute=0
  Amp-Out vals:  [0x17 0x17]
  Converter: stream=8, channel=0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3
  Power: setting=D3, actual=D3
Node 0x09 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Control: name="Surround Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x2a, nsteps=0x2a, stepsize=0x05, mute=0
  Amp-Out vals:  [0x17 0x17]
  Converter: stream=8, channel=2
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
Node 0x0a [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Control: name="Center Playback Volume", index=0, device=0
    ControlAmp: chs=1, dir=Out, idx=0, ofs=0
  Control: name="LFE Playback Volume", index=0, device=0
    ControlAmp: chs=2, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x2a, nsteps=0x2a, stepsize=0x05, mute=0
  Amp-Out vals:  [0x19 0x19]
  Converter: stream=8, channel=4
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
Node 0x0b [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Control: name="Headphone Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Device: name="VT2020 HP", type="Audio", device=2
  Amp-Out caps: ofs=0x2a, nsteps=0x2a, stepsize=0x05, mute=0
  Amp-Out vals:  [0x19 0x19]
  Converter: stream=8, channel=0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3
  Power: setting=D3, actual=D3
Node 0x0c [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Amp-Out caps: ofs=0x2a, nsteps=0x2a, stepsize=0x05, mute=0
  Amp-Out vals:  [0x2a 0x2a]
  Converter: stream=0, channel=0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
Node 0x0d [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0e [Audio Output] wcaps 0x611: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
Node 0x0f [Audio Output] wcaps 0x611: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
Node 0x10 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Control: name="Capture Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Capture Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Device: name="VT2020 Analog", type="Audio", device=0
  Amp-In caps: ofs=0x0b, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x0c 0x0c]
  Converter: stream=4, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
  Connection: 1
     0x1e
Node 0x11 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Control: name="Capture Volume", index=1, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Capture Switch", index=1, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x0b, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x9f 0x9f]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
  Connection: 1
     0x1f
Node 0x12 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x13 [Audio Input] wcaps 0x100711: Stereo Digital
  Converter: stream=0, channel=0
  SDI-Select: 0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x1f0]: 32000 44100 48000 88200 96000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
  Connection: 1
     0x2f
Node 0x14 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x15 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x16 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x17 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x18 [Audio Mixer] wcaps 0x20050b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80]
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
  Connection: 2
     0x08 0x21
Node 0x19 [Audio Mixer] wcaps 0x20050b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80]
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
  Connection: 2
     0x09 0x21
Node 0x1a [Audio Mixer] wcaps 0x20050b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80]
  Power states:  D0 D1 D2 D3
  Power: setting=D3, actual=D3
  Connection: 2
     0x0b 0x21
Node 0x1b [Audio Mixer] wcaps 0x20050b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80]
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
  Connection: 2
     0x34 0x21
Node 0x1c [Audio Mixer] wcaps 0x20050b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80]
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
  Connection: 2
     0x35 0x21
Node 0x1d [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x1e [Audio Selector] wcaps 0x300501: Stereo
  Control: name="Input Source", index=0, device=0
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
  Connection: 6
     0x2c 0x2b 0x2a 0x29* 0x28 0x21
Node 0x1f [Audio Selector] wcaps 0x300501: Stereo
  Control: name="Input Source", index=1, device=0
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
  Connection: 6
     0x2c 0x2b* 0x2a 0x29 0x28 0x21
Node 0x20 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x21 [Audio Mixer] wcaps 0x20050b: Stereo Amp-In
  Control: name="PCM Loopback Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=5, ofs=0
  Control: name="PCM Loopback Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=5, ofs=0
  Control: name="Front Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=3, ofs=0
  Control: name="Front Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=3, ofs=0
  Control: name="Rear Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=1, ofs=0
  Control: name="Rear Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=1, ofs=0
  Control: name="Line Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Control: name="Line Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x80 0x80] [0x9f 0x9f] [0x9f 0x9f] [0x1f 0x1f] [0x80 0x80]
  Power states:  D0 D1 D2 D3
  Power: setting=D3, actual=D3
  Connection: 5
     0x2c 0x2b 0x2a 0x29 0x28
Node 0x22 [Beep Generator Widget] wcaps 0x70040c: Mono Amp-Out
  Amp-Out caps: ofs=0x0a, nsteps=0x12, stepsize=0x05, mute=1
  Amp-Out vals:  [0x00]
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
Node 0x23 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x24 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Control: name="Front Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Line-Out Jack", index=0, device=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0001001c: OUT HP EAPD Detect
  EAPD 0x2: EAPD
  Pin Default 0x01014010: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Green
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=02, enabled=1
  Power states:  D0 D1 D2 D3
  Power: setting=D3, actual=D3
  Connection: 1
     0x18
Node 0x25 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000001c: OUT HP Detect
  Pin Default 0x410110f2: [N/A] Line Out at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x2
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3
  Power: setting=D3, actual=D3
  Connection: 1
     0x19
Node 0x26 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00000014: OUT Detect
  Pin Default 0x410160f1: [N/A] Line Out at Ext Rear
    Conn = 1/8, Color = Orange
    DefAssociation = 0xf, Sequence = 0x1
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3
  Power: setting=D3, actual=D3
  Connection: 1
     0x0a
Node 0x27 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00000014: OUT Detect
  Pin Default 0x410120f4: [N/A] Line Out at Ext Rear
    Conn = 1/8, Color = Grey
    DefAssociation = 0xf, Sequence = 0x4
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3
  Power: setting=D3, actual=D3
  Connection: 1
     0x1a
Node 0x28 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Control: name="Headphone Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Independent HP", index=0, device=0
  Control: name="Front Headphone Jack", index=0, device=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000233c: IN OUT HP Detect
    Vref caps: HIZ 50 100
  Pin Default 0x0221401f: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Green
    DefAssociation = 0x1, Sequence = 0xf
  Pin-ctls: 0xc0: OUT HP VREF_HIZ
  Unsolicited: tag=01, enabled=1
  Power states:  D0 D1 D2 D3
  Power: setting=D3, actual=D3
  Connection: 1
     0x1b
Node 0x29 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Control: name="Front Mic Boost Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Front Mic Jack", index=0, device=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000233c: IN OUT HP Detect
    Vref caps: HIZ 50 100
  Pin Default 0x02a19037: [Jack] Mic at Ext Front
    Conn = 1/8, Color = Pink
    DefAssociation = 0x3, Sequence = 0x7
  Pin-ctls: 0x21: IN VREF_50
  Unsolicited: tag=03, enabled=1
  Power states:  D0 D1 D2 D3
  Power: setting=D3, actual=D3
  Connection: 1
     0x1c
Node 0x2a [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Control: name="Surround Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Line Jack", index=0, device=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x00002334: IN OUT Detect
    Vref caps: HIZ 50 100
  Pin Default 0x0181303e: [Jack] Line In at Ext Rear
    Conn = 1/8, Color = Blue
    DefAssociation = 0x3, Sequence = 0xe
  Pin-ctls: 0x40: OUT VREF_HIZ
  Unsolicited: tag=05, enabled=1
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
  Connection: 2
     0x09* 0x0c
Node 0x2b [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Control: name="Center Playback Switch", index=0, device=0
    ControlAmp: chs=1, dir=Out, idx=0, ofs=0
  Control: name="LFE Playback Switch", index=0, device=0
    ControlAmp: chs=2, dir=Out, idx=0, ofs=0
  Control: name="Rear Mic Boost Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Rear Mic Jack", index=0, device=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x00002334: IN OUT Detect
    Vref caps: HIZ 50 100
  Pin Default 0x01a19036: [Jack] Mic at Ext Rear
    Conn = 1/8, Color = Pink
    DefAssociation = 0x3, Sequence = 0x6
  Pin-ctls: 0x41: OUT VREF_50
  Unsolicited: tag=04, enabled=1
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
  Connection: 2
     0x0a* 0x0c
Node 0x2c [Pin Complex] wcaps 0x400401: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x593700f8: [N/A] CD at Int ATAPI
    Conn = Analog, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x8
  Pin-ctls: 0x00:
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
Node 0x2d [Pin Complex] wcaps 0x400701: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x474410f0: [N/A] SPDIF Out at Ext Rear Panel
    Conn = RCA, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00:
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
  Connection: 1
     0x0e
Node 0x2e [Pin Complex] wcaps 0x400701: Stereo Digital
  Pincap 0x00000090: OUT HDMI
  Pin Default 0x585600f0: [N/A] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00:
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
  Connection: 1
     0x0f
Node 0x2f [Pin Complex] wcaps 0x400601: Stereo Digital
  Pincap 0x00000030: IN OUT
  Pin Default 0x47c420f0: [N/A] SPDIF In at Ext Rear Panel
    Conn = RCA, Color = Grey
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
Node 0x30 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x31 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x32 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x33 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x34 [Audio Selector] wcaps 0x300501: Stereo
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
  Connection: 3
     0x08 0x0b* 0x0c
Node 0x35 [Audio Selector] wcaps 0x300501: Stereo
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
  Connection: 3
     0x08* 0x0b 0x0c
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw---T  1 root audio 116,  6 Apr 29 10:50 /dev/snd/controlC0
crw-rw---T  1 root audio 116,  5 Apr 29 10:50 /dev/snd/hwC0D2
crw-rw---T  1 root audio 116,  4 Apr 29 10:52 /dev/snd/pcmC0D0c
crw-rw---T  1 root audio 116,  3 Apr 29 10:54 /dev/snd/pcmC0D0p
crw-rw---T  1 root audio 116,  2 Apr 29 10:50 /dev/snd/pcmC0D2p
crw-rw---T  1 root audio 116,  1 Apr 29 10:50 /dev/snd/seq
crw-rw---T  1 root audio 116, 33 Apr 29 10:50 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Apr 29 10:50 .
drwxr-xr-x 3 root root 200 Apr 29 10:50 ..
lrwxrwxrwx 1 root root  12 Apr 29 10:50 pci-0000:00:1b.0 -> ../controlC0


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: VT2020 Analog [VT2020 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 2: VT2020 HP [VT2020 HP]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: VT2020 Analog [VT2020 Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [Intel]

Card hw:0 'Intel'/'HDA Intel at 0xfdff8000 irq 43'
  Mixer name	: 'VIA VT2020'
  Components	: 'HDA:11060441,1458a014,00100100'
  Controls      : 39
  Simple ctrls  : 22
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 42
  Mono: Playback 25 [60%] [-25.50dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 42
  Mono:
  Front Left: Playback 42 [100%] [0.00dB] [on]
  Front Right: Playback 42 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'PCM Loopback',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [12.00dB] [on]
  Front Right: Playback 31 [100%] [12.00dB] [on]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 42
  Mono:
  Front Left: Playback 40 [95%] [-3.00dB] [on]
  Front Right: Playback 40 [95%] [-3.00dB] [on]
Simple mixer control 'Front Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [12.00dB] [on]
  Front Right: Playback 31 [100%] [12.00dB] [on]
Simple mixer control 'Front Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 3 [100%] [30.75dB]
  Front Right: 3 [100%] [30.75dB]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 42
  Mono:
  Front Left: Playback 40 [95%] [-3.00dB] [on]
  Front Right: Playback 40 [95%] [-3.00dB] [on]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 42
  Mono: Playback 42 [100%] [0.00dB] [on]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 42
  Mono: Playback 42 [100%] [0.00dB] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [12.00dB] [off]
  Front Right: Playback 31 [100%] [12.00dB] [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 12 [39%] [1.50dB] [on]
  Front Right: Capture 12 [39%] [1.50dB] [on]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 31 [100%] [30.00dB] [off]
  Front Right: Capture 31 [100%] [30.00dB] [off]
Simple mixer control 'Digital',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 120
  Front Left: Capture 60 [50%] [0.00dB]
  Front Right: Capture 60 [50%] [0.00dB]
Simple mixer control 'Dynamic Power-Control',0
  Capabilities: enum
  Items: 'Disabled' 'Enabled'
  Item0: 'Enabled'
Simple mixer control 'Independent HP',0
  Capabilities: enum
  Items: 'OFF' 'ON'
  Item0: 'OFF'
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Front Mic' 'Rear Mic' 'Line' 'Stereo Mixer'
  Item0: 'Front Mic'
Simple mixer control 'Input Source',1
  Capabilities: cenum
  Items: 'Front Mic' 'Rear Mic' 'Line' 'Stereo Mixer'
  Item0: 'Front Mic'
Simple mixer control 'Loopback Mixing',0
  Capabilities: enum
  Items: 'Disabled' 'Enabled'
  Item0: 'Disabled'
Simple mixer control 'Rear Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [12.00dB] [off]
  Front Right: Playback 31 [100%] [12.00dB] [off]
Simple mixer control 'Rear Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB]
Simple mixer control 'Smart 5.1',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]


!!Alsactl output
!!-------------

--startcollapse--
state.Intel {
	control.1 {
		iface MIXER
		name 'Front Playback Volume'
		value.0 40
		value.1 40
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 42'
			dbmin -6300
			dbmax 0
			dbvalue.0 -300
			dbvalue.1 -300
		}
	}
	control.2 {
		iface MIXER
		name 'Front Playback Switch'
		value.0 true
		value.1 true
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.3 {
		iface MIXER
		name 'Surround Playback Volume'
		value.0 40
		value.1 40
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 42'
			dbmin -6300
			dbmax 0
			dbvalue.0 -300
			dbvalue.1 -300
		}
	}
	control.4 {
		iface MIXER
		name 'Surround Playback Switch'
		value.0 true
		value.1 true
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.5 {
		iface MIXER
		name 'Center Playback Volume'
		value 42
		comment {
			access 'read write'
			type INTEGER
			count 1
			range '0 - 42'
			dbmin -6300
			dbmax 0
			dbvalue.0 0
		}
	}
	control.6 {
		iface MIXER
		name 'Center Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.7 {
		iface MIXER
		name 'LFE Playback Volume'
		value 42
		comment {
			access 'read write'
			type INTEGER
			count 1
			range '0 - 42'
			dbmin -6300
			dbmax 0
			dbvalue.0 0
		}
	}
	control.8 {
		iface MIXER
		name 'LFE Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.9 {
		iface MIXER
		name 'PCM Loopback Playback Volume'
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
	control.10 {
		iface MIXER
		name 'PCM Loopback Playback Switch'
		value.0 true
		value.1 true
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.11 {
		iface MIXER
		name 'Headphone Playback Volume'
		value.0 42
		value.1 42
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 42'
			dbmin -6300
			dbmax 0
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.12 {
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
	control.13 {
		iface MIXER
		name 'Loopback Mixing'
		value Disabled
		comment {
			access 'read write'
			type ENUMERATED
			count 1
			item.0 Disabled
			item.1 Enabled
		}
	}
	control.14 {
		iface MIXER
		name 'Capture Volume'
		value.0 12
		value.1 12
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 31'
			dbmin -1650
			dbmax 3000
			dbvalue.0 150
			dbvalue.1 150
		}
	}
	control.15 {
		iface MIXER
		name 'Capture Switch'
		value.0 true
		value.1 true
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.16 {
		iface MIXER
		name 'Capture Volume'
		index 1
		value.0 31
		value.1 31
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 31'
			dbmin -1650
			dbmax 3000
			dbvalue.0 3000
			dbvalue.1 3000
		}
	}
	control.17 {
		iface MIXER
		name 'Capture Switch'
		index 1
		value.0 false
		value.1 false
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.18 {
		iface MIXER
		name 'Input Source'
		value 'Front Mic'
		comment {
			access 'read write'
			type ENUMERATED
			count 1
			item.0 'Front Mic'
			item.1 'Rear Mic'
			item.2 Line
			item.3 'Stereo Mixer'
		}
	}
	control.19 {
		iface MIXER
		name 'Input Source'
		index 1
		value 'Front Mic'
		comment {
			access 'read write'
			type ENUMERATED
			count 1
			item.0 'Front Mic'
			item.1 'Rear Mic'
			item.2 Line
			item.3 'Stereo Mixer'
		}
	}
	control.20 {
		iface MIXER
		name 'Front Mic Playback Volume'
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
	control.21 {
		iface MIXER
		name 'Front Mic Playback Switch'
		value.0 true
		value.1 true
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.22 {
		iface MIXER
		name 'Rear Mic Playback Volume'
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
	control.23 {
		iface MIXER
		name 'Rear Mic Playback Switch'
		value.0 false
		value.1 false
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.24 {
		iface MIXER
		name 'Line Playback Volume'
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
	control.25 {
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
	control.26 {
		iface MIXER
		name 'Front Mic Boost Volume'
		value.0 3
		value.1 3
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 3'
			dbmin 0
			dbmax 3075
			dbvalue.0 3075
			dbvalue.1 3075
		}
	}
	control.27 {
		iface MIXER
		name 'Rear Mic Boost Volume'
		value.0 0
		value.1 0
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 3'
			dbmin 0
			dbmax 3075
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.28 {
		iface MIXER
		name 'Independent HP'
		value OFF
		comment {
			access 'read write'
			type ENUMERATED
			count 1
			item.0 OFF
			item.1 ON
		}
	}
	control.29 {
		iface MIXER
		name 'Smart 5.1'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.30 {
		iface MIXER
		name 'Dynamic Power-Control'
		value Enabled
		comment {
			access 'read write'
			type ENUMERATED
			count 1
			item.0 Disabled
			item.1 Enabled
		}
	}
	control.31 {
		iface MIXER
		name 'Master Playback Volume'
		value 25
		comment {
			access 'read write'
			type INTEGER
			count 1
			range '0 - 42'
			dbmin -6300
			dbmax 0
			dbvalue.0 -2550
		}
	}
	control.32 {
		iface MIXER
		name 'Master Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.33 {
		iface CARD
		name 'Line-Out Jack'
		value false
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.34 {
		iface CARD
		name 'Front Headphone Jack'
		value false
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.35 {
		iface CARD
		name 'Front Mic Jack'
		value false
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.36 {
		iface CARD
		name 'Rear Mic Jack'
		value false
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.37 {
		iface CARD
		name 'Line Jack'
		value false
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.38 {
		iface MIXER
		name 'PCM Playback Volume'
		value.0 255
		value.1 255
		comment {
			access 'read write user'
			type INTEGER
			count 2
			range '0 - 255'
			tlv '0000000100000008ffffec1400000014'
			dbmin -5100
			dbmax 0
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.39 {
		iface MIXER
		name 'Digital Capture Volume'
		value.0 60
		value.1 60
		comment {
			access 'read write user'
			type INTEGER
			count 2
			range '0 - 120'
			tlv '0000000100000008fffff44800000032'
			dbmin -3000
			dbmax 3000
			dbvalue.0 0
			dbvalue.1 0
		}
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
hidp
nfnetlink_queue
nfnetlink
nf_conntrack_ipv4
nf_defrag_ipv4
ipt_REJECT
xt_tcpudp
iptable_filter
ip_tables
xt_iprange
xt_state
nf_conntrack
xt_mark
xt_NFQUEUE
x_tables
dm_crypt
rfcomm
bnep
binfmt_misc
nfsd
nfs
lockd
fscache
auth_rpcgss
nfs_acl
sunrpc
usblp
ext2
tda18271
snd_hda_codec_via
btusb
bluetooth
af9013
snd_hda_intel
snd_hda_codec
snd_hwdep
snd_pcm
snd_seq
snd_timer
snd_seq_device
dvb_usb_af9015
dvb_usb
dvb_core
ppdev
nvidia
ir_lirc_codec
lirc_dev
ir_mce_kbd_decoder
ir_sony_decoder
ir_jvc_decoder
ir_rc6_decoder
rc_imon_pad
ir_rc5_decoder
ir_nec_decoder
imon
rc_core
snd
serio_raw
joydev
parport_pc
soundcore
snd_page_alloc
mac_hid
hwmon_vid
coretemp
lp
parport
hid_logitech
hid_pl
ff_memless
usbhid
hid
floppy
atl1c


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D2/init_pin_configs:
0x24 0x01014010
0x25 0x410110f2
0x26 0x410160f1
0x27 0x410120f4
0x28 0x0221401f
0x29 0x02a19037
0x2a 0x0181303e
0x2b 0x01a19036
0x2c 0x593700f8
0x2d 0x474410f0
0x2e 0x585600f0
0x2f 0x47c420f0

/sys/class/sound/hwC0D2/driver_pin_configs:

/sys/class/sound/hwC0D2/user_pin_configs:

/sys/class/sound/hwC0D2/init_verbs:


!!ALSA/HDA dmesg
!!------------------

[   26.258067] DVB: registering new adapter (KWorld PlusTV Dual DVB-T PCI (DVB-T PC160-2T))
[   26.591205] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   26.591263] snd_hda_intel 0000:00:1b.0: irq 43 for MSI/MSI-X
[   26.591290] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   26.680204] af9013: firmware version:4.95.0.0
--
[   26.686955] DVB: registering adapter 0 frontend 0 (Afatech AF9013 DVB-T)...
[   26.748538] input: HDA Intel Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   26.748643] input: HDA Intel Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   26.748733] input: HDA Intel Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   26.748816] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   26.748898] input: HDA Intel Line-Out as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   26.756289] tda18271 0-00c0: creating new instance

```

---

### Post by messelink on 2012-04-29
Solved by setting Dynamic Power-Control to [Disabled] in alsamixer. Can't say that I understand it, but it works now. Might as well go back to the original alsa version (1.0.24) of precise now that it works.

---

### Post by SPARTAN-118 on 2012-04-29
> **messelink said:**
> Solved by setting Dynamic Power-Control to [Disabled] in alsamixer. Can't say that I understand it, but it works now. Might as well go back to the original alsa version (1.0.24) of precise now that it works.

Hi, I'd just like to know how to do that? Fresh 12.04 install here, same problem as your original post: front speakers dead (or very, very quiet, not sure).

I looked in alsamixer but there was no option for Dynamic Power-Control. I did however change my [channel] settings to 6, as it should be (I think). Correct me if I'm wrong on that part.

EDIT: Nevermind, I got it working. That one option might have been it, though I was following a guide on that one sticky, so that might have helped, too.

---

### Post by Yellow Pasque on 2012-04-29
> **messelink said:**
> Might as well go back to the original alsa version (1.0.24) of precise now that it works.

Not recommended. Look how many things were fixed for vt1718S/2020 codec in ALSA 1.0.25: [http://www.alsa-project.org/main/index.php/Changes_v1.0.24_v1.0.25#HDA_Codec_driver](http://www.alsa-project.org/main/index.php/Changes_v1.0.24_v1.0.25#HDA_Codec_driver)

---

### Post by Shocker on 2012-05-01
In my fresh install of Ubuntu PP 12.04, I noticed that the front speaker (headphones) do not riproduce any audio stream while the display speakers work.

I noticed that changing the Independent HP switching I can turn on the speaker or the headphones.

Can anyone tell me how to set it up as it was in the previous release (audio stream riproduced by both devices simultaneously)?

Thanks for your support,

Regards 

Shocker

---

### Post by messelink on 2012-05-12
> **Temüjin said:**
> Not recommended. Look how many things were fixed for vt1718S/2020 codec in ALSA 1.0.25: [http://www.alsa-project.org/main/index.php/Changes_v1.0.24_v1.0.25#HDA_Codec_driver](http://www.alsa-project.org/main/index.php/Changes_v1.0.24_v1.0.25#HDA_Codec_driver)

Oh, thanks for that heads-up. Much appreciated!

---

