---
title: "No Sound Ati HDA (ad198x) on ubuntu 10.10"
date: 2010-10-23
forum: Multimedia Software
---

### Post by Megapearl on 2010-10-23
Hello,

I followed [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) to find a solution for my problem.
I don't get any sound, amplifier is connected to computer via spdif (coaxial) cable, in windows this setup is working fine.
When i change the profile in 'sound preferences' to 'analog stereo output' i do get sound out of the headphones connected through the 'green' output jack at the backside of the computer.
But all of the digital output settings in profile didn't work out to get sound out of the amplifier connected to the sp/dif connector.
I also tried different settings in /etc/modprobe.d/alsa-base.conf regarding the model=3stack-dig and model=6stack-dig ...

My setup:

```

!!################################
!!ALSA Information Script v 0.4.59
!!################################

!!Script ran on: Sat Oct 23 11:15:40 UTC 2010


!!Linux Distribution
!!------------------

Ubuntu 10.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.10"


!!DMI Information
!!---------------

Manufacturer:      System manufacturer
Product Name:      System Product Name


!!Kernel Information
!!------------------

Kernel release:    2.6.35-22-generic
Operating System:  GNU/Linux
Architecture:      x86_64
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
snd_usb_audio
snd_usb_audio


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
                      HDA ATI SB at 0xf7ff4000 irq 42
 1 [Q9000          ]: USB-Audio - QuickCam Pro 9000
                      Logitech, Inc. QuickCam Pro 9000 at usb-0000:00:13.5-4, high speed
 2 [Headset        ]: USB-Audio - Logitech Wireless Headset
                      Logitech Logitech Wireless Headset at usb-0000:00:13.0-2.3, full speed


!!PCI Soundcards installed in the system
!!--------------------------------------

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:14.2 0403: 1002:4383
	Subsystem: 1002:4383


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
snd-hda-intel: model=6stack-dig index=0


!!Loaded sound module options
!!--------------------------

!!Module: snd_hda_intel
	bdl_pos_adj : 32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	beep_mode : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	enable_msi : -1
	id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	index : 0,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	model : 6stack-dig,(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	patch : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	position_fix : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	power_save : 0
	power_save_controller : Y
	probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	single_cmd : N

!!Module: snd_usb_audio
	async_unlink : Y
	device_setup : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	ignore_ctl_error : N
	index : -2,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	nrpacks : 8
	pid : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	vid : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1

!!Module: snd_usb_audio
	async_unlink : Y
	device_setup : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	ignore_ctl_error : N
	index : -2,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	nrpacks : 8
	pid : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	vid : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: Analog Devices AD1988
Address: 0
Function Id: 0x1
Vendor Id: 0x11d41988
Subsystem Id: 0x104381e1
Revision Id: 0x100400
No Modem Function Group found
Default PCM:
    rates [0x7ff]: 8000 11025 16000 22050 32000 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
Default Amp-Out caps: ofs=0x27, nsteps=0x27, stepsize=0x05, mute=0
GPIO: io=2, o=0, i=0, unsolicited=1, wake=0
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=1, unsol=0
Node 0x02 [Audio Output] wcaps 0x30311: Stereo Digital
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Control: name="IEC958 Default PCM Playback Switch", index=0, device=0
  Control: name="IEC958 Playback Source", index=0, device=0
  Device: name="AD198x Digital", type="SPDIF", device=1
  Converter: stream=0, channel=0
  Digital: Non-Audio GenLevel
  Digital category: 0x2
  PCM:
    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Delay: 3 samples
  Connection: 1
     0x1d
Node 0x03 [Audio Output] wcaps 0x405: Stereo Amp-Out
  Amp-Out caps: ofs=0x27, nsteps=0x27, stepsize=0x05, mute=0
  Amp-Out vals:  [0x27 0x27]
  Converter: stream=0, channel=0
  Power states:  D0 D3
  Power: setting=D0, actual=D0
Node 0x04 [Audio Output] wcaps 0x405: Stereo Amp-Out
  Control: name="Front Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Device: name="AD198x Analog", type="Audio", device=0
  Amp-Out caps: ofs=0x27, nsteps=0x27, stepsize=0x05, mute=0
  Amp-Out vals:  [0x04 0x04]
  Converter: stream=0, channel=0
  Power states:  D0 D3
  Power: setting=D0, actual=D0
Node 0x05 [Audio Output] wcaps 0x405: Stereo Amp-Out
  Control: name="Center Playback Volume", index=0, device=0
    ControlAmp: chs=1, dir=Out, idx=0, ofs=0
  Control: name="LFE Playback Volume", index=0, device=0
    ControlAmp: chs=2, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x27, nsteps=0x27, stepsize=0x05, mute=0
  Amp-Out vals:  [0x00 0x00]
  Converter: stream=0, channel=0
  Power states:  D0 D3
  Power: setting=D0, actual=D0
Node 0x06 [Audio Output] wcaps 0x405: Stereo Amp-Out
  Control: name="Surround Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x27, nsteps=0x27, stepsize=0x05, mute=0
  Amp-Out vals:  [0x00 0x00]
  Converter: stream=0, channel=0
  Power states:  D0 D3
  Power: setting=D0, actual=D0
Node 0x07 [Audio Input] wcaps 0x130391: Stereo Digital
  Control: name="IEC958 Capture Switch", index=0, device=0
  Control: name="IEC958 Capture Default", index=0, device=0
  Device: name="AD198x Digital", type="SPDIF", device=1
  Converter: stream=0, channel=0
  SDI-Select: 0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Unsolicited: tag=00, enabled=0
  Delay: 3 samples
  Connection: 1
     0x1c
Node 0x08 [Audio Input] wcaps 0x100501: Stereo
  Device: name="AD198x Analog", type="Audio", device=0
  Converter: stream=0, channel=0
  SDI-Select: 0
  Power states:  D0 D3
  Power: setting=D0, actual=D0
  Connection: 1
     0x0c
Node 0x09 [Audio Input] wcaps 0x100501: Stereo
  Converter: stream=0, channel=0
  SDI-Select: 0
  Power states:  D0 D3
  Power: setting=D0, actual=D0
  Connection: 1
     0x0d
Node 0x0a [Audio Output] wcaps 0x405: Stereo Amp-Out
  Control: name="Side Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x27, nsteps=0x27, stepsize=0x05, mute=0
  Amp-Out vals:  [0x00 0x00]
  Converter: stream=0, channel=0
  Power states:  D0 D3
  Power: setting=D0, actual=D0
Node 0x0b [Audio Selector] wcaps 0x300301: Stereo Digital
  Connection: 3
     0x08* 0x09 0x0f
Node 0x0c [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Control: name="Capture Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Capture Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Input Source", index=0, device=0
  Amp-Out caps: ofs=0x27, nsteps=0x36, stepsize=0x05, mute=1
  Amp-Out vals:  [0xa7 0xa7]
  Connection: 10
     0x38 0x39 0x3a 0x3b 0x3c* 0x18 0x24 0x25 0x3d 0x20
Node 0x0d [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Control: name="Capture Volume", index=1, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Capture Switch", index=1, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Input Source", index=1, device=0
  Amp-Out caps: ofs=0x27, nsteps=0x36, stepsize=0x05, mute=1
  Amp-Out vals:  [0xa7 0xa7]
  Connection: 10
     0x38 0x39 0x3a 0x3b 0x3c* 0x18 0x24 0x25 0x3d 0x20
Node 0x0e [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Control: name="Capture Volume", index=2, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Capture Switch", index=2, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Input Source", index=2, device=0
  Amp-Out caps: ofs=0x27, nsteps=0x36, stepsize=0x05, mute=1
  Amp-Out vals:  [0xa7 0xa7]
  Connection: 10
     0x38 0x39 0x3a 0x3b 0x3c* 0x18 0x24 0x25 0x3d 0x20
Node 0x0f [Audio Input] wcaps 0x100501: Stereo
  Converter: stream=0, channel=0
  SDI-Select: 0
  Power states:  D0 D3
  Power: setting=D0, actual=D0
  Connection: 1
     0x0e
Node 0x10 [Beep Generator Widget] wcaps 0x70000c: Mono Amp-Out
  Control: name="Beep Playback Volume", index=0, device=0
    ControlAmp: chs=1, dir=Out, idx=0, ofs=0
  Control: name="Beep Playback Switch", index=0, device=0
    ControlAmp: chs=1, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x0f, nsteps=0x0f, stepsize=0x0b, mute=1
  Amp-Out vals:  [0x00]
Node 0x11 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000373f: IN OUT HP Detect Trigger ImpSense
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x02214030: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Green
    DefAssociation = 0x3, Sequence = 0x0
  Pin-ctls: 0xc0: OUT HP VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x22
Node 0x12 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000373f: IN OUT HP Detect Trigger ImpSense
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x01014010: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Green
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x29
Node 0x13 [Pin Complex] wcaps 0x40010c: Mono Amp-Out
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x00]
  Pincap 0x00000010: OUT
  Pin Default 0x511711f0: [N/A] Speaker at Int Rear
    Conn = Analog, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x2d
Node 0x14 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000373f: IN OUT HP Detect Trigger ImpSense
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x02a19022: [Jack] Mic at Ext Front
    Conn = 1/8, Color = Pink
    DefAssociation = 0x2, Sequence = 0x2
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x2b
Node 0x15 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00003737: IN OUT Detect Trigger ImpSense
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x01813021: [Jack] Line In at Ext Rear
    Conn = 1/8, Color = Blue
    DefAssociation = 0x2, Sequence = 0x1
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x2c
Node 0x16 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x00003737: IN OUT Detect Trigger ImpSense
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x01011012: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0x1, Sequence = 0x2
  Pin-ctls: 0x40: OUT VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x2a
Node 0x17 [Pin Complex] wcaps 0x40098d: Stereo Amp-Out R/L
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00003737: IN OUT Detect Trigger ImpSense
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x01a19020: [Jack] Mic at Ext Rear
    Conn = 1/8, Color = Pink
    DefAssociation = 0x2, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x26
Node 0x18 [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x9933112e: [Fixed] CD at Int ATAPI
    Conn = ATAPI, Color = Black
    DefAssociation = 0x2, Sequence = 0xe
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
Node 0x19 [Power Widget] wcaps 0x500500: Mono
  Power states:  D0 D3
  Power: setting=D0, actual=D0
  Connection: 2
     0x20 0x21
Node 0x1a [Pin Complex] wcaps 0x400000: Mono
  Pincap 0x00000020: IN
  Pin Default 0x918711f0: [Fixed] Line In at Int Rear
    Conn = Analog, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
Node 0x1b [Pin Complex] wcaps 0x40030d: Stereo Digital Amp-Out
  Control: name="IEC958 Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="IEC958 Playback Source", index=0, device=0
  Amp-Out caps: ofs=0x27, nsteps=0x27, stepsize=0x05, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x00000010: OUT
  Pin Default 0x0145f1f0: [Jack] SPDIF Out at Ext Rear
    Conn = Optical, Color = Other
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x02
Node 0x1c [Pin Complex] wcaps 0x40020b: Stereo Digital Amp-In
  Control: name="IEC958 Capture Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00000020: IN
  Pin Default 0x41c5f1f0: [N/A] SPDIF In at Ext Rear
    Conn = Optical, Color = Other
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
Node 0x1d [Audio Mixer] wcaps 0x200303: Stereo Digital Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80]
  Connection: 2
     0x01 0x0b
Node 0x1e [Audio Mixer] wcaps 0x200103: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80]
  Connection: 2
     0x36 0x21
Node 0x1f [Volume Knob Widget] wcaps 0x600080: Mono
  Volume-Knob: delta=1, steps=63, direct=0, val=0
  Unsolicited: tag=00, enabled=0
  Connection: 0
Node 0x20 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="CD Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=6, ofs=0
  Control: name="CD Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=6, ofs=0
  Control: name="Front Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Front Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Line Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=1, ofs=0
  Control: name="Line Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=1, ofs=0
  Control: name="Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=4, ofs=0
  Control: name="Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=4, ofs=0
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x8d 0x8d] [0x8d 0x8d] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x19 0x19] [0x80 0x80]
  Connection: 8
     0x39 0x33 0x38 0x3d 0x34 0x3b 0x18 0x1a
Node 0x21 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Control: name="Analog Mix Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Analog Mix Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x1f 0x1f]
  Connection: 1
     0x20
Node 0x22 [Audio Mixer] wcaps 0x200103: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80]
  Connection: 2
     0x37 0x21
Node 0x23 [Vendor Defined Widget] wcaps 0xf00100: Mono
  Connection: 18
     0x11* 0x12 0x13 0x14 0x15 0x16 0x17 0x18 0x24 0x25 0x38 0x39 0x3a 0x3b 0x3c 0x3d 0x20 0x21
Node 0x24 [Pin Complex] wcaps 0x40098d: Stereo Amp-Out R/L
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x00000037: IN OUT Detect Trigger ImpSense
  Pin Default 0x01016011: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Orange
    DefAssociation = 0x1, Sequence = 0x1
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x27
Node 0x25 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x00000037: IN OUT Detect Trigger ImpSense
  Pin Default 0x01012013: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Grey
    DefAssociation = 0x1, Sequence = 0x3
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x28
Node 0x26 [Audio Mixer] wcaps 0x200103: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80]
  Connection: 2
     0x32 0x21
Node 0x27 [Audio Mixer] wcaps 0x200103: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80]
  Connection: 2
     0x05 0x21
Node 0x28 [Audio Mixer] wcaps 0x200103: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80]
  Connection: 2
     0x0a 0x21
Node 0x29 [Audio Mixer] wcaps 0x200103: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80]
  Connection: 2
     0x04 0x21
Node 0x2a [Audio Mixer] wcaps 0x200103: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80]
  Connection: 2
     0x06 0x21
Node 0x2b [Audio Mixer] wcaps 0x200103: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80]
  Connection: 2
     0x30 0x21
Node 0x2c [Audio Mixer] wcaps 0x200103: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80]
  Connection: 2
     0x31 0x21
Node 0x2d [Audio Mixer] wcaps 0x200100: Mono
  Connection: 1
     0x1e
Node 0x2e [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x2f [Vendor Defined Widget] wcaps 0xf00100: Mono
  Connection: 6
     0x11* 0x12 0x14 0x15 0x16 0x17
Node 0x30 [Audio Selector] wcaps 0x300101: Stereo
  Connection: 3
     0x03* 0x04 0x06
Node 0x31 [Audio Selector] wcaps 0x300101: Stereo
  Connection: 2
     0x04* 0x0a
Node 0x32 [Audio Selector] wcaps 0x300101: Stereo
  Connection: 2
     0x05* 0x04
Node 0x33 [Audio Selector] wcaps 0x300101: Stereo
  Connection: 3
     0x3a* 0x25 0x24
Node 0x34 [Audio Selector] wcaps 0x300101: Stereo
  Connection: 3
     0x3c* 0x25 0x24
Node 0x35 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x36 [Audio Selector] wcaps 0x300101: Stereo
  Connection: 3
     0x03 0x04* 0x06
Node 0x37 [Audio Selector] wcaps 0x300101: Stereo
  Connection: 3
     0x03 0x04* 0x06
Node 0x38 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 1
     0x11
Node 0x39 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Control: name="Front Mic Boost", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-Out vals:  [0x01 0x01]
  Connection: 1
     0x14
Node 0x3a [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 1
     0x15
Node 0x3b [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 1
     0x16
Node 0x3c [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Control: name="Mic Boost", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 1
     0x17
Node 0x3d [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 1
     0x12
--endcollapse--


!!USB Mixer information
!!---------------------------
--startcollapse--

USB Mixer: usb_id=0x046d0990, ctrlif=2, ctlerr=0
Card: Logitech, Inc. QuickCam Pro 9000 at usb-0000:00:13.5-4, high speed
  Unit: 5
    Control: name="Mic Capture Volume", index=0
    Info: id=5, control=2, cmask=0x0, channels=1, type="S16"
    Volume: min=4608, max=7680, dBmin=1800, dBmax=3000
  Unit: 5
    Control: name="Mic Capture Switch", index=0
    Info: id=5, control=1, cmask=0x0, channels=1, type="INV_BOOLEAN"
    Volume: min=0, max=1, dBmin=0, dBmax=0
USB Mixer: usb_id=0x046d0a12, ctrlif=0, ctlerr=0
Card: Logitech Logitech Wireless Headset at usb-0000:00:13.0-2.3, full speed
  Unit: 2
    Control: name="PCM Playback Volume", index=0
    Info: id=2, control=2, cmask=0x0, channels=1, type="S16"
    Volume: min=-15360, max=-1536, dBmin=-6000, dBmax=-600
  Unit: 2
    Control: name="PCM Playback Switch", index=0
    Info: id=2, control=1, cmask=0x0, channels=1, type="INV_BOOLEAN"
    Volume: min=0, max=1, dBmin=0, dBmax=0
  Unit: 5
    Control: name="Mic Capture Volume", index=0
    Info: id=5, control=2, cmask=0x0, channels=1, type="S16"
    Volume: min=-7168, max=0, dBmin=-2800, dBmax=0
  Unit: 5
    Control: name="Mic Capture Switch", index=0
    Info: id=5, control=1, cmask=0x0, channels=1, type="INV_BOOLEAN"
    Volume: min=0, max=1, dBmin=0, dBmax=0
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----  1 root audio 116, 14 Oct 23 12:43 /dev/snd/controlC0
crw-rw----  1 root audio 116,  5 Oct 23 12:43 /dev/snd/controlC1
crw-rw----  1 root audio 116,  8 Oct 23 12:43 /dev/snd/controlC2
crw-rw----  1 root audio 116, 13 Oct 23 12:43 /dev/snd/hwC0D0
crw-rw----  1 root audio 116, 12 Oct 23 12:44 /dev/snd/pcmC0D0c
crw-rw----  1 root audio 116, 11 Oct 23 12:43 /dev/snd/pcmC0D0p
crw-rw----  1 root audio 116, 10 Oct 23 12:43 /dev/snd/pcmC0D1c
crw-rw----  1 root audio 116,  9 Oct 23 13:11 /dev/snd/pcmC0D1p
crw-rw----  1 root audio 116,  4 Oct 23 12:43 /dev/snd/pcmC1D0c
crw-rw----  1 root audio 116,  7 Oct 23 12:44 /dev/snd/pcmC2D0c
crw-rw----  1 root audio 116,  6 Oct 23 12:43 /dev/snd/pcmC2D0p
crw-rw----  1 root audio 116,  3 Oct 23 12:43 /dev/snd/seq
crw-rw----  1 root audio 116,  2 Oct 23 12:43 /dev/snd/timer

/dev/snd/by-id:
total 0
drwxr-xr-x 2 root root  80 Oct 23 12:43 .
drwxr-xr-x 4 root root 340 Oct 23 12:43 ..
lrwxrwxrwx 1 root root  12 Oct 23 12:43 usb-046d_0990_BBAA691D-02 -> ../controlC1
lrwxrwxrwx 1 root root  12 Oct 23 12:43 usb-Logitech_Logitech_Wireless_Headset-00 -> ../controlC2

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root 100 Oct 23 12:43 .
drwxr-xr-x 4 root root 340 Oct 23 12:43 ..
lrwxrwxrwx 1 root root  12 Oct 23 12:43 pci-0000:00:13.0-usb-0:2.3:1.0 -> ../controlC2
lrwxrwxrwx 1 root root  12 Oct 23 12:43 pci-0000:00:13.5-usb-0:4:1.2 -> ../controlC1
lrwxrwxrwx 1 root root  12 Oct 23 12:43 pci-0000:00:14.2 -> ../controlC0


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Headset [Logitech Wireless Headset], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 3/3
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
card 0: SB [HDA ATI SB], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Q9000 [QuickCam Pro 9000], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Headset [Logitech Wireless Headset], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [SB]

Card hw:0 'SB'/'HDA ATI SB at 0xf7ff4000 irq 42'
  Mixer name	: 'Analog Devices AD1988'
  Components	: 'HDA:11d41988,104381e1,00100400'
  Controls      : 48
  Simple ctrls  : 26
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 39
  Mono: Playback 26 [67%] [-19.50dB] [off]
Simple mixer control 'Headphone',0
  Capabilities: pswitch penum
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [off]
  Front Right: Playback [off]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 248 [97%] [-1.40dB]
  Front Right: Playback 248 [97%] [-1.40dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 39
  Mono:
  Front Left: Playback 17 [44%] [-33.00dB] [off]
  Front Right: Playback 17 [44%] [-33.00dB] [off]
Simple mixer control 'Front Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 13 [42%] [-15.00dB] [off]
  Front Right: Playback 13 [42%] [-15.00dB] [off]
Simple mixer control 'Front Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 1 [33%]
  Front Right: 1 [33%]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 39
  Mono:
  Front Left: Playback 0 [0%] [-58.50dB] [off]
  Front Right: Playback 0 [0%] [-58.50dB] [off]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 39
  Mono: Playback 0 [0%] [-58.50dB] [off]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 39
  Mono: Playback 0 [0%] [-58.50dB] [off]
Simple mixer control 'Side',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 39
  Mono:
  Front Left: Playback 0 [0%] [-58.50dB] [off]
  Front Right: Playback 0 [0%] [-58.50dB] [off]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 13 [42%] [-15.00dB] [off]
  Front Right: Playback 13 [42%] [-15.00dB] [off]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 25 [81%] [3.00dB] [on]
  Front Right: Playback 25 [81%] [3.00dB] [on]
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
  Capabilities: pvolume cvolume pswitch pswitch-joined cswitch cswitch-joined penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 39 Capture 0 - 31
  Front Left: Playback 0 [0%] [-58.50dB] [on] Capture 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-58.50dB] [on] Capture 0 [0%] [-34.50dB] [off]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958 Playback Source',0
  Capabilities: enum
  Items: 'PCM' 'ADC1' 'ADC2' 'ADC3'
  Item0: 'PCM'
Simple mixer control 'Beep',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 15
  Mono: Playback 15 [100%] [0.00dB] [off]
Simple mixer control 'Mono',0
  Capabilities: pswitch penum
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [off]
  Front Right: Playback [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 54
  Front Left: Capture 39 [72%] [0.00dB] [off]
  Front Right: Capture 39 [72%] [0.00dB] [off]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 54
  Front Left: Capture 39 [72%] [0.00dB] [off]
  Front Right: Capture 39 [72%] [0.00dB] [off]
Simple mixer control 'Capture',2
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 54
  Front Left: Capture 39 [72%] [0.00dB] [off]
  Front Right: Capture 39 [72%] [0.00dB] [off]
Simple mixer control 'Analog Mix',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Front Mic' 'Line' 'Mic' 'CD' 'Mix'
  Item0: 'Mic'
Simple mixer control 'Input Source',1
  Capabilities: cenum
  Items: 'Front Mic' 'Line' 'Mic' 'CD' 'Mix'
  Item0: 'Mic'
Simple mixer control 'Input Source',2
  Capabilities: cenum
  Items: 'Front Mic' 'Line' 'Mic' 'CD' 'Mix'
  Item0: 'Mic'

!!-------Mixer controls for card 1 [Q9000]

Card hw:1 'Q9000'/'Logitech, Inc. QuickCam Pro 9000 at usb-0000:00:13.5-4, high speed'
  Mixer name	: 'USB Mixer'
  Components	: 'USB046d:0990'
  Controls      : 2
  Simple ctrls  : 1
Simple mixer control 'Mic',0
  Capabilities: cvolume cvolume-joined cswitch cswitch-joined penum
  Capture channels: Mono
  Limits: Capture 0 - 3072
  Mono: Capture 0 [0%] [18.00dB] [on]

!!-------Mixer controls for card 2 [Headset]

Card hw:2 'Headset'/'Logitech Logitech Wireless Headset at usb-0000:00:13.0-2.3, full speed'
  Mixer name	: 'USB Mixer'
  Components	: 'USB046d:0a12'
  Controls      : 4
  Simple ctrls  : 2
Simple mixer control 'PCM',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 54
  Mono: Playback 44 [81%] [-16.00dB] [on]
Simple mixer control 'Mic',0
  Capabilities: cvolume cvolume-joined cswitch cswitch-joined penum
  Capture channels: Mono
  Limits: Capture 0 - 28
  Mono: Capture 3 [11%] [-25.00dB] [on]


!!Alsactl output
!!-------------

--startcollapse--
state.SB {
	control.1 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 39'
		comment.dbmin -5850
		comment.dbmax 0
		iface MIXER
		name 'Front Playback Volume'
		value.0 17
		value.1 17
	}
	control.2 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 39'
		comment.dbmin -5850
		comment.dbmax 0
		iface MIXER
		name 'Surround Playback Volume'
		value.0 0
		value.1 0
	}
	control.3 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 39'
		comment.dbmin -5850
		comment.dbmax 0
		iface MIXER
		name 'Center Playback Volume'
		value 0
	}
	control.4 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 39'
		comment.dbmin -5850
		comment.dbmax 0
		iface MIXER
		name 'LFE Playback Volume'
		value 0
	}
	control.5 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 39'
		comment.dbmin -5850
		comment.dbmax 0
		iface MIXER
		name 'Side Playback Volume'
		value.0 0
		value.1 0
	}
	control.6 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Front Playback Switch'
		value.0 false
		value.1 false
	}
	control.7 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Surround Playback Switch'
		value.0 false
		value.1 false
	}
	control.8 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Center Playback Switch'
		value false
	}
	control.9 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'LFE Playback Switch'
		value false
	}
	control.10 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Side Playback Switch'
		value.0 false
		value.1 false
	}
	control.11 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Headphone Playback Switch'
		value.0 false
		value.1 false
	}
	control.12 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Mono Playback Switch'
		value.0 false
		value.1 false
	}
	control.13 {
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
	control.14 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'CD Playback Switch'
		value.0 true
		value.1 true
	}
	control.15 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Front Mic Playback Volume'
		value.0 13
		value.1 13
	}
	control.16 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Front Mic Playback Switch'
		value.0 false
		value.1 false
	}
	control.17 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Line Playback Volume'
		value.0 13
		value.1 13
	}
	control.18 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Line Playback Switch'
		value.0 false
		value.1 false
	}
	control.19 {
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
	control.20 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Mic Playback Switch'
		value.0 false
		value.1 false
	}
	control.21 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -4650
		comment.dbmax 0
		iface MIXER
		name 'Analog Mix Playback Volume'
		value.0 31
		value.1 31
	}
	control.22 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Analog Mix Playback Switch'
		value.0 true
		value.1 true
	}
	control.23 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 3'
		comment.dbmin 0
		comment.dbmax 3000
		iface MIXER
		name 'Front Mic Boost'
		value.0 1
		value.1 1
	}
	control.24 {
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
	control.25 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 54'
		comment.dbmin -5850
		comment.dbmax 2250
		iface MIXER
		name 'Capture Volume'
		value.0 39
		value.1 39
	}
	control.26 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Capture Switch'
		value.0 false
		value.1 false
	}
	control.27 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 54'
		comment.dbmin -5850
		comment.dbmax 2250
		iface MIXER
		name 'Capture Volume'
		index 1
		value.0 39
		value.1 39
	}
	control.28 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Capture Switch'
		index 1
		value.0 false
		value.1 false
	}
	control.29 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 54'
		comment.dbmin -5850
		comment.dbmax 2250
		iface MIXER
		name 'Capture Volume'
		index 2
		value.0 39
		value.1 39
	}
	control.30 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Capture Switch'
		index 2
		value.0 false
		value.1 false
	}
	control.31 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 'Front Mic'
		comment.item.1 Line
		comment.item.2 Mic
		comment.item.3 CD
		comment.item.4 Mix
		iface MIXER
		name 'Input Source'
		value Mic
	}
	control.32 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 'Front Mic'
		comment.item.1 Line
		comment.item.2 Mic
		comment.item.3 CD
		comment.item.4 Mix
		iface MIXER
		name 'Input Source'
		index 1
		value Mic
	}
	control.33 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 'Front Mic'
		comment.item.1 Line
		comment.item.2 Mic
		comment.item.3 CD
		comment.item.4 Mix
		iface MIXER
		name 'Input Source'
		index 2
		value Mic
	}
	control.34 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 39'
		comment.dbmin -5850
		comment.dbmax 0
		iface MIXER
		name 'IEC958 Playback Volume'
		value.0 0
		value.1 0
	}
	control.35 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 PCM
		comment.item.1 ADC1
		comment.item.2 ADC2
		comment.item.3 ADC3
		iface MIXER
		name 'IEC958 Playback Source'
		value PCM
	}
	control.36 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'IEC958 Capture Volume'
		value.0 0
		value.1 0
	}
	control.37 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Con Mask'
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.38 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.39 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Default'
		value '0682000200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
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
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Default PCM Playback Switch'
		value true
	}
	control.42 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Capture Switch'
		value false
	}
	control.43 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Capture Default'
		value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.44 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 15'
		comment.dbmin -4500
		comment.dbmax 0
		iface MIXER
		name 'Beep Playback Volume'
		value 15
	}
	control.45 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Beep Playback Switch'
		value false
	}
	control.46 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 39'
		comment.dbmin -5850
		comment.dbmax 0
		iface MIXER
		name 'Master Playback Volume'
		value 26
	}
	control.47 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Master Playback Switch'
		value false
	}
	control.48 {
		comment.access 'read write user'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 255'
		comment.tlv '0000000100000008ffffec1400000014'
		comment.dbmin -5100
		comment.dbmax 0
		iface MIXER
		name 'PCM Playback Volume'
		value.0 248
		value.1 248
	}
}
state.Q9000 {
	control.1 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Mic Capture Switch'
		value true
	}
	control.2 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 3072'
		comment.dbmin 1800
		comment.dbmax 3000
		iface MIXER
		name 'Mic Capture Volume'
		value 0
	}
}
state.Headset {
	control.1 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'PCM Playback Switch'
		value true
	}
	control.2 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 54'
		comment.dbmin -6000
		comment.dbmax -600
		iface MIXER
		name 'PCM Playback Volume'
		value 44
	}
	control.3 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Mic Capture Switch'
		value true
	}
	control.4 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 28'
		comment.dbmin -2800
		comment.dbmax 0
		iface MIXER
		name 'Mic Capture Volume'
		value 3
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
rfcomm
parport_pc
ppdev
sco
bnep
l2cap
btusb
bluetooth
snd_hda_codec_analog
snd_hda_intel
snd_hda_codec
binfmt_misc
joydev
snd_usb_audio
snd_pcm
snd_hwdep
snd_usbmidi_lib
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
nvidia
snd_seq
snd_timer
snd_seq_device
asus_atk0110
usbhid
uvcvideo
videodev
hid
snd
v4l1_compat
v4l2_compat_ioctl32
k10temp
psmouse
edac_core
edac_mce_amd
serio_raw
soundcore
i2c_piix4
snd_page_alloc
lp
parport
usb_storage
floppy
skge
firewire_ohci
firewire_core
crc_itu_t
ahci
pata_atiixp
libahci


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x11 0x02214030
0x12 0x01014010
0x13 0x511711f0
0x14 0x02a19022
0x15 0x01813021
0x16 0x01011012
0x17 0x01a19020
0x18 0x9933112e
0x1a 0x918711f0
0x1b 0x0145f1f0
0x1c 0x41c5f1f0
0x24 0x01016011
0x25 0x01012013

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:


!!ALSA/HDA dmesg
!!------------------

[    7.652174] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  173.14.28  Wed Sep 29 09:44:58 PDT 2010
[    7.677754] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    7.677821]   alloc irq_desc for 42 on node 0
[    7.677823]   alloc kstat_irqs on node 0
[    7.677836] HDA Intel 0000:00:14.2: irq 42 for MSI/MSI-X
[    7.784668] usb 2-1.2: new full speed USB device using ohci_hcd and address 8

```

Anybody has the same problem as i am?
Any help would be greatly appreciated...

Regards,
Donald.

---

### Post by tomeq on 2010-10-24
Same problem here. I'm using 10.10 on PC with Asus P5B board with AD198x as an audio device. 

I'm using S/PDIF coax to connect pc to my amp. I've tried hundreds of solutions available on the internet, none of them works at all. I've tried to remove pulseaudio and use only bare alsa - no success.

Anything I get is stereo sound barely audible, compared to Win7 on the same machine or total silence or static noise when using VLC with AC3 S/PDIF passthrough option set. No other media player works.


I'm having this problem since 8.04 as I remember. None of later versions worked with surround audio over S/PDIF.

---

### Post by Megapearl on 2010-11-02
I found the solution!

Use sudo alsamixer from command prompt, select your soundcard by pressing F6, look for S/PDIF and turn up the volume to max, set the 'next' S/PDIF to PCM, and voila! i got sound now... don't know if this works for you, but you can try it... success!

Regards,
Donald.

---

### Post by petekalo on 2011-01-01
This worked for me a few kernel releases ago when I fiddled with alsamixer settings. Now its not working for some reason with the latest release, no matter what I do with alsamixer.

---

### Post by bupe on 2011-02-26
I have an Asus motherboard with the same integrated sound [http://www.asus.com/product.aspx?P_ID=KC8yHOfBMCe9SlrP]("http://www.asus.com/product.aspx?P_ID=KC8yHOfBMCe9SlrP").

I have the same issue, I don't get anything via the coaxial spdif out.

I tried the suggestion above with alsamixer, did not change anything for me.

Any other suggestions?

Cheers,
Peter

---

### Post by trout121234 on 2012-11-08
> **bupe said:**
> I have an Asus motherboard with the same integrated sound [http://www.asus.com/product.aspx?P_ID=KC8yHOfBMCe9SlrP]("http://www.asus.com/product.aspx?P_ID=KC8yHOfBMCe9SlrP").

I have the same issue, I don't get anything via the coaxial spdif out.

I tried the suggestion above with alsamixer, did not change anything for me.

Any other suggestions?

Cheers,
Peter

Peter, I hope these guys respond, for I am having the same issue as yourself.

---

### Post by mörgæs on 2012-11-08
The thread concerns 10.10, which is an obsolete Ubuntu release. Thus the information here is obsolete. 

I'm closing the thread, but feel free to open a new one.

---

