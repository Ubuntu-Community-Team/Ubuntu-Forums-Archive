---
title: "Soundcard Problem Creative"
date: 2012-04-18
forum: Multimedia Software
---

### Post by jask05 on 2012-04-18
Hi :)
I updated my Ubuntu to the last stable release and appeared a big problem. I recorded a video of it:

[http://www.dailymotion.com/video/xphuv8_problema-sonido-ubuntu-11-10_tech](http://www.dailymotion.com/video/xphuv8_problema-sonido-ubuntu-11-10_tech)

As can you see, I have a problem with the sound. It hop every 2 or 3 seconds and I can't hear music, show videos, etc. 

I have a Creative SB X-Fi Xtreme Audio (CA0110-IBG) and this is my alsa info:

```

!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Wed Apr 18 20:47:19 UTC 2012


!!Linux Distribution
!!------------------

Ubuntu 11.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 11.10"


!!DMI Information
!!---------------

Manufacturer:      System manufacturer
Product Name:      System Product Name
Product Version:   System Version


!!Kernel Information
!!------------------

Kernel release:    3.0.0-17-generic
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
snd_usb_audio
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
                      HDA ATI SB at 0xf9ff4000 irq 16
 1 [Camera         ]: USB-Audio - Deasy USB2.0 Camera
                      PixArt Imaging Inc. Deasy USB2.0 Camera at usb-0000:00:13.5-3, high speed
 2 [Creative       ]: HDA-Intel - HDA Creative
                      HDA Creative at 0xfeafc000 irq 19


!!PCI Soundcards installed in the system
!!--------------------------------------

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
06:00.0 PCI bridge: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG PCI to PCIe Bridge
07:00.0 Audio device: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

00:14.2 0403: 1002:4383
    Subsystem: 1043:8288
--
07:00.0 0403: 1102:0009
    Subsystem: 1102:0018


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
    bdl_pos_adj : 32,32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    beep_mode : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
    enable_msi : -1
    id :  (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    model :  (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    patch :  (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
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
    id :  (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    ignore_ctl_error : N
    index : -2,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    nrpacks : 8
    pid : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    vid : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1

!!Module: snd_hda_intel
    bdl_pos_adj : 32,32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    beep_mode : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
    enable_msi : -1
    id :  (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    model :  (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    patch :  (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    position_fix : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    power_save : 0
    power_save_controller : Y
    probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    single_cmd : N


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: Analog Devices AD1988B
Address: 0
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x11d4198b
Subsystem Id: 0x1043829b
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
  Digital: Enabled
  Digital category: 0x0
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
  Amp-Out vals:  [0x27 0x27]
  Converter: stream=0, channel=0
  Power states:  D0 D3
  Power: setting=D0, actual=D0
Node 0x05 [Audio Output] wcaps 0x405: Stereo Amp-Out
  Control: name="Center Playback Volume", index=0, device=0
    ControlAmp: chs=1, dir=Out, idx=0, ofs=0
  Control: name="LFE Playback Volume", index=0, device=0
    ControlAmp: chs=2, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x27, nsteps=0x27, stepsize=0x05, mute=0
  Amp-Out vals:  [0x27 0x27]
  Converter: stream=0, channel=0
  Power states:  D0 D3
  Power: setting=D0, actual=D0
Node 0x06 [Audio Output] wcaps 0x405: Stereo Amp-Out
  Control: name="Surround Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x27, nsteps=0x27, stepsize=0x05, mute=0
  Amp-Out vals:  [0x27 0x27]
  Converter: stream=0, channel=0
  Power states:  D0 D3
  Power: setting=D0, actual=D0
Node 0x07 [Audio Input] wcaps 0x130391: Stereo Digital
  Converter: stream=0, channel=0
  SDI-Select: 0
  Digital: Validity
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
  Amp-Out vals:  [0x27 0x27]
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
  Amp-Out vals:  [0x35 0x35]
  Connection: 10
     0x38 0x39* 0x3a 0x3b 0x3c 0x18 0x24 0x25 0x3d 0x20
Node 0x0d [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Control: name="Capture Volume", index=1, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Capture Switch", index=1, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Input Source", index=1, device=0
  Amp-Out caps: ofs=0x27, nsteps=0x36, stepsize=0x05, mute=1
  Amp-Out vals:  [0xa7 0xa7]
  Connection: 10
     0x38 0x39* 0x3a 0x3b 0x3c 0x18 0x24 0x25 0x3d 0x20
Node 0x0e [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Control: name="Capture Volume", index=2, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Capture Switch", index=2, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Input Source", index=2, device=0
  Amp-Out caps: ofs=0x27, nsteps=0x36, stepsize=0x05, mute=1
  Amp-Out vals:  [0xa7 0xa7]
  Connection: 10
     0x38 0x39* 0x3a 0x3b 0x3c 0x18 0x24 0x25 0x3d 0x20
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
  Pin Default 0x02a19021: [Jack] Mic at Ext Front
    Conn = 1/8, Color = Pink
    DefAssociation = 0x2, Sequence = 0x1
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x2b
Node 0x15 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00003737: IN OUT Detect Trigger ImpSense
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x0181302e: [Jack] Line In at Ext Rear
    Conn = 1/8, Color = Blue
    DefAssociation = 0x2, Sequence = 0xe
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
  Pin Default 0x99331122: [Fixed] CD at Int ATAPI
    Conn = ATAPI, Color = Black
    DefAssociation = 0x2, Sequence = 0x2
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
Node 0x19 [Power Widget] wcaps 0x500500: Mono
  Power states:  D0 D3
  Power: setting=D0, actual=D0
  Connection: 2
     0x20 0x21
Node 0x1a [Pin Complex] wcaps 0x400000: Mono
  Pincap 0x00000020: IN
  Pin Default 0x91f711f0: [Fixed] Other at Int Rear
    Conn = Analog, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
Node 0x1b [Pin Complex] wcaps 0x40030d: Stereo Digital Amp-Out
  Control: name="IEC958 Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="IEC958 Playback Source", index=0, device=0
  Amp-Out caps: ofs=0x27, nsteps=0x27, stepsize=0x05, mute=1
  Amp-Out vals:  [0x27 0x27]
  Pincap 0x00000010: OUT
  Pin Default 0x0145f1a0: [Jack] SPDIF Out at Ext Rear
    Conn = Optical, Color = Other
    DefAssociation = 0xa, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x02
Node 0x1c [Pin Complex] wcaps 0x40020b: Stereo Digital Amp-In
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x97 0x97]
  Pincap 0x00000020: IN
  Pin Default 0x41c5f160: [N/A] SPDIF In at Ext Rear
    Conn = Optical, Color = Other
    DefAssociation = 0x6, Sequence = 0x0
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
  Control: name="Front Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Front Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Rear Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=4, ofs=0
  Control: name="Rear Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=4, ofs=0
  Control: name="Line Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=1, ofs=0
  Control: name="Line Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=1, ofs=0
  Control: name="CD Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=6, ofs=0
  Control: name="CD Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=6, ofs=0
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
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
  Control: name="Headphone Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
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
  Pin Default 0x01012014: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Grey
    DefAssociation = 0x1, Sequence = 0x4
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
  Control: name="Center Playback Switch", index=0, device=0
    ControlAmp: chs=1, dir=In, idx=2, ofs=0
  Control: name="LFE Playback Switch", index=0, device=0
    ControlAmp: chs=2, dir=In, idx=2, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x05 0x21
Node 0x28 [Audio Mixer] wcaps 0x200103: Stereo Amp-In
  Control: name="Side Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x0a 0x21
Node 0x29 [Audio Mixer] wcaps 0x200103: Stereo Amp-In
  Control: name="Front Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x04 0x21
Node 0x2a [Audio Mixer] wcaps 0x200103: Stereo Amp-In
  Control: name="Surround Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
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
  Control: name="Front Mic Boost Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=1, ofs=0
  Amp-Out caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-Out vals:  [0x03 0x03]
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
  Control: name="Rear Mic Boost Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=4, ofs=0
  Amp-Out caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 1
     0x17
Node 0x3d [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 1
     0x12
Codec: Creative CA0110-IBG
Address: 1
AFG Function Id: 0x1 (unsol 1)
Vendor Id: 0x1102000a
Subsystem Id: 0x11021002
Revision Id: 0x100000
No Modem Function Group found
Default PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xa]: 16 24
    formats [0x1]: PCM
Default Amp-In caps: ofs=0x67, nsteps=0x73, stepsize=0x01, mute=0
Default Amp-Out caps: ofs=0x67, nsteps=0x67, stepsize=0x01, mute=0
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x02 [Audio Output] wcaps 0x5: Stereo Amp-Out
  Control: name="Front Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Device: name="CA0110 Analog", type="Audio", device=0
  Amp-Out caps: ofs=0x67, nsteps=0x7f, stepsize=0x01, mute=0
  Amp-Out vals:  [0x66 0x66]
  Converter: stream=1, channel=0
Node 0x03 [Audio Output] wcaps 0x5: Stereo Amp-Out
  Control: name="Center Playback Volume", index=0, device=0
    ControlAmp: chs=1, dir=Out, idx=0, ofs=0
  Control: name="LFE Playback Volume", index=0, device=0
    ControlAmp: chs=1, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x67, nsteps=0x7f, stepsize=0x01, mute=0
  Amp-Out vals:  [0x67 0x00]
  Converter: stream=1, channel=4
Node 0x04 [Audio Output] wcaps 0x5: Stereo Amp-Out
  Control: name="Surround Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x67, nsteps=0x7f, stepsize=0x01, mute=0
  Amp-Out vals:  [0x67 0x67]
  Converter: stream=1, channel=2
Node 0x05 [Audio Output] wcaps 0x5: Stereo Amp-Out
  Control: name="Side Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x67, nsteps=0x7f, stepsize=0x01, mute=0
  Amp-Out vals:  [0x67 0x67]
  Converter: stream=1, channel=0
Node 0x06 [Audio Output] wcaps 0x5: Stereo Amp-Out
  Control: name="Headphone Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x67, nsteps=0x7f, stepsize=0x01, mute=0
  Amp-Out vals:  [0x67 0x67]
  Converter: stream=1, channel=0
Node 0x07 [Audio Output] wcaps 0x205: Stereo Digital Amp-Out
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Control: name="IEC958 Default PCM Playback Switch", index=0, device=0
  Device: name="CA0110 Digital", type="SPDIF", device=1
  Amp-Out caps: ofs=0x67, nsteps=0x7f, stepsize=0x01, mute=0
  Amp-Out vals:  [0x00 0x00]
  Converter: stream=3, channel=0
  Digital: Enabled
  Digital category: 0x0
Node 0x08 [Audio Input] wcaps 0x100103: Stereo Amp-In
  Control: name="Line Capture Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Device: name="CA0110 Analog", type="Audio", device=0
  Amp-In caps: ofs=0x67, nsteps=0x7f, stepsize=0x01, mute=0
  Amp-In vals:  [0x00 0x00]
  Converter: stream=1, channel=0
  SDI-Select: 1
  Connection: 1
     0x10
Node 0x09 [Audio Input] wcaps 0x10010b: Stereo Amp-In
  Control: name="Front Mic Capture Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x67, nsteps=0x7f, stepsize=0x01, mute=0
  Amp-In vals:  [0x65 0x65]
  Converter: stream=0, channel=0
  SDI-Select: 1
  Connection: 1
     0x11
Node 0x0a [Audio Input] wcaps 0x100303: Stereo Digital Amp-In
  Control: name="IEC958 Capture Switch", index=0, device=0
  Control: name="IEC958 Capture Default", index=0, device=0
  Control: name="IEC958 Capture Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Device: name="CA0110 Digital", type="SPDIF", device=1
  Amp-In caps: ofs=0x67, nsteps=0x7f, stepsize=0x01, mute=0
  Amp-In vals:  [0x00 0x00]
  Converter: stream=3, channel=0
  SDI-Select: 1
  Digital: Non-Audio Pro GenLevel
  Digital category: 0x7f
  Connection: 1
     0x13
Node 0x0b [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Control: name="Front Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x00000014: OUT Detect
  Pin Default 0x01014010: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Green
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0xc0: OUT HP
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x02
Node 0x0c [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Control: name="Center Playback Switch", index=0, device=0
    ControlAmp: chs=1, dir=Out, idx=0, ofs=0
  Control: name="LFE Playback Switch", index=0, device=0
    ControlAmp: chs=1, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x00000014: OUT Detect
  Pin Default 0x01016011: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Orange
    DefAssociation = 0x1, Sequence = 0x1
  Pin-ctls: 0xc0: OUT HP
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x03
Node 0x0d [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Control: name="Surround Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x00000014: OUT Detect
  Pin Default 0x01011012: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0x1, Sequence = 0x2
  Pin-ctls: 0xc0: OUT HP
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x04
Node 0x0e [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Control: name="Side Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x00000014: OUT Detect
  Pin Default 0x01012014: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Grey
    DefAssociation = 0x1, Sequence = 0x4
  Pin-ctls: 0xc0: OUT HP
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x05
Node 0x0f [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Control: name="Headphone Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000001c: OUT HP Detect
  Pin Default 0x02214020: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Green
    DefAssociation = 0x2, Sequence = 0x0
  Pin-ctls: 0xc0: OUT HP
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x06
Node 0x10 [Pin Complex] wcaps 0x40008b: Stereo Amp-In
  Control: name="Line Capture Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80]
  Pincap 0x00000024: IN Detect
  Pin Default 0x01813030: [Jack] Line In at Ext Rear
    Conn = 1/8, Color = Blue
    DefAssociation = 0x3, Sequence = 0x0
  Pin-ctls: 0x24: IN
  Unsolicited: tag=00, enabled=0
Node 0x11 [Pin Complex] wcaps 0x40008b: Stereo Amp-In
  Control: name="Front Mic Capture Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00000024: IN Detect
  Pin Default 0x02a19040: [Jack] Mic at Ext Front
    Conn = 1/8, Color = Pink
    DefAssociation = 0x4, Sequence = 0x0
  Pin-ctls: 0x24: IN
  Unsolicited: tag=00, enabled=0
Node 0x12 [Pin Complex] wcaps 0x40038d: Stereo Digital Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x00000010: OUT
  Pin Default 0x01452150: [Jack] SPDIF Out at Ext Rear
    Conn = Optical, Color = Grey
    DefAssociation = 0x5, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0xc0: OUT HP
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x07
Node 0x13 [Pin Complex] wcaps 0x40028b: Stereo Digital Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00000020: IN
  Pin Default 0x01c51160: [Jack] SPDIF In at Ext Rear
    Conn = Optical, Color = Black
    DefAssociation = 0x6, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x24: IN
  Unsolicited: tag=00, enabled=0
Node 0x14 [Vendor Defined Widget] wcaps 0xf00080: Mono
  Unsolicited: tag=00, enabled=0
--endcollapse--


!!USB Mixer information
!!---------------------------
--startcollapse--

USB Mixer: usb_id=0x093a2700, ctrlif=2, ctlerr=0
Card: PixArt Imaging Inc. Deasy USB2.0 Camera at usb-0000:00:13.5-3, high speed
  Unit: 5
    Control: name="Mic Capture Volume", index=0
    Info: id=5, control=2, cmask=0x0, channels=1, type="S16"
    Volume: min=7680, max=12800, dBmin=3000, dBmax=5000
  Unit: 5
    Control: name="Mic Capture Switch", index=0
    Info: id=5, control=1, cmask=0x0, channels=1, type="INV_BOOLEAN"
    Volume: min=0, max=1, dBmin=0, dBmax=0
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----  1 root audio 116,  8 Apr 18 22:41 /dev/snd/controlC0
crw-rw----  1 root audio 116,  3 Apr 18 22:41 /dev/snd/controlC1
crw-rw----  1 root audio 116, 14 Apr 18 22:41 /dev/snd/controlC2
crw-rw----  1 root audio 116,  7 Apr 18 22:41 /dev/snd/hwC0D0
crw-rw----  1 root audio 116, 13 Apr 18 22:41 /dev/snd/hwC2D1
crw-rw----  1 root audio 116,  6 Apr 18 22:41 /dev/snd/pcmC0D0c
crw-rw----  1 root audio 116,  5 Apr 18 22:45 /dev/snd/pcmC0D0p
crw-rw----  1 root audio 116,  4 Apr 18 22:41 /dev/snd/pcmC0D1p
crw-rw----  1 root audio 116,  2 Apr 18 22:41 /dev/snd/pcmC1D0c
crw-rw----  1 root audio 116, 12 Apr 18 22:41 /dev/snd/pcmC2D0c
crw-rw----  1 root audio 116, 11 Apr 18 22:41 /dev/snd/pcmC2D0p
crw-rw----  1 root audio 116, 10 Apr 18 22:41 /dev/snd/pcmC2D1c
crw-rw----  1 root audio 116,  9 Apr 18 22:41 /dev/snd/pcmC2D1p
crw-rw----  1 root audio 116,  1 Apr 18 22:41 /dev/snd/seq
crw-rw----  1 root audio 116, 33 Apr 18 22:41 /dev/snd/timer

/dev/snd/by-id:
total 0
drwxr-xr-x 2 root root  60 Apr 18 22:41 .
drwxr-xr-x 4 root root 380 Apr 18 22:41 ..
lrwxrwxrwx 1 root root  12 Apr 18 22:41 usb-PixArt_Imaging_Inc._Deasy_USB2.0_Camera-02 -> ../controlC1

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root 100 Apr 18 22:41 .
drwxr-xr-x 4 root root 380 Apr 18 22:41 ..
lrwxrwxrwx 1 root root  12 Apr 18 22:41 pci-0000:00:13.5-usb-0:3:1.2 -> ../controlC1
lrwxrwxrwx 1 root root  12 Apr 18 22:41 pci-0000:00:14.2 -> ../controlC0
lrwxrwxrwx 1 root root  12 Apr 18 22:41 pci-0000:07:00.0 -> ../controlC2


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
card 2: Creative [HDA Creative], device 0: CA0110 Analog [CA0110 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Creative [HDA Creative], device 1: CA0110 Digital [CA0110 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 3/3
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
card 1: Camera [Deasy USB2.0 Camera], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Creative [HDA Creative], device 0: CA0110 Analog [CA0110 Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 2: Creative [HDA Creative], device 1: CA0110 Digital [CA0110 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [SB]

Card hw:0 'SB'/'HDA ATI SB at 0xf9ff4000 irq 16'
  Mixer name    : 'Analog Devices AD1988B'
  Components    : 'HDA:11d4198b,1043829b,00100400'
  Controls      : 44
  Simple ctrls  : 25
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 39
  Mono: Playback 39 [100%] [0.00dB] [on]
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
  Limits: Playback 0 - 39
  Mono:
  Front Left: Playback 39 [100%] [0.00dB] [on]
  Front Right: Playback 39 [100%] [0.00dB] [on]
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
  Front Left: 3 [100%] [30.00dB]
  Front Right: 3 [100%] [30.00dB]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 39
  Mono:
  Front Left: Playback 39 [100%] [0.00dB] [on]
  Front Right: Playback 39 [100%] [0.00dB] [on]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 39
  Mono: Playback 39 [100%] [0.00dB] [on]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 39
  Mono: Playback 39 [100%] [0.00dB] [on]
Simple mixer control 'Side',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 39
  Mono:
  Front Left: Playback 39 [100%] [0.00dB] [on]
  Front Right: Playback 39 [100%] [0.00dB] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'IEC958',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 39
  Mono:
  Front Left: Playback 39 [100%] [0.00dB] [on]
  Front Right: Playback 39 [100%] [0.00dB] [on]
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
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 54
  Front Left: Capture 53 [98%] [21.00dB] [on]
  Front Right: Capture 53 [98%] [21.00dB] [on]
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
  Items: 'Front Mic' 'Rear Mic' 'Line' 'CD' 'Mix'
  Item0: 'Front Mic'
Simple mixer control 'Input Source',1
  Capabilities: cenum
  Items: 'Front Mic' 'Rear Mic' 'Line' 'CD' 'Mix'
  Item0: 'Front Mic'
Simple mixer control 'Input Source',2
  Capabilities: cenum
  Items: 'Front Mic' 'Rear Mic' 'Line' 'CD' 'Mix'
  Item0: 'Front Mic'
Simple mixer control 'Rear Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Rear Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB]

!!-------Mixer controls for card 1 [Camera]

Card hw:1 'Camera'/'PixArt Imaging Inc. Deasy USB2.0 Camera at usb-0000:00:13.5-3, high speed'
  Mixer name    : 'USB Mixer'
  Components    : 'USB093a:2700'
  Controls      : 2
  Simple ctrls  : 1
Simple mixer control 'Mic',0
  Capabilities: cvolume cvolume-joined cswitch cswitch-joined penum
  Capture channels: Mono
  Limits: Capture 0 - 2
  Mono: Capture 1 [50%] [40.00dB] [on]

!!-------Mixer controls for card 2 [Creative]

Card hw:2 'Creative'/'HDA Creative at 0xfeafc000 irq 19'
  Mixer name    : 'Creative CA0110-IBG'
  Components    : 'HDA:1102000a,11021002,00100000'
  Controls      : 25
  Simple ctrls  : 11
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 103
  Mono:
  Front Left: Playback 103 [100%] [0.00dB] [on]
  Front Right: Playback 103 [100%] [0.00dB] [on]
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
  Limits: Playback 0 - 103
  Mono:
  Front Left: Playback 102 [99%] [0.50dB] [on]
  Front Right: Playback 102 [99%] [0.50dB] [on]
Simple mixer control 'Front Mic',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 127
  Front Left: Capture 101 [80%] [-1.00dB] [on]
  Front Right: Capture 101 [80%] [-1.00dB] [on]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 103
  Mono:
  Front Left: Playback 103 [100%] [0.00dB] [on]
  Front Right: Playback 103 [100%] [0.00dB] [on]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 103
  Mono: Playback 103 [100%] [0.00dB] [on]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 103
  Mono: Playback 103 [100%] [0.00dB] [on]
Simple mixer control 'Side',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 103
  Mono:
  Front Left: Playback 103 [100%] [0.00dB] [on]
  Front Right: Playback 103 [100%] [0.00dB] [on]
Simple mixer control 'Line',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 115
  Front Left: Capture 0 [0%] [-51.50dB] [off]
  Front Right: Capture 0 [0%] [-51.50dB] [off]
Simple mixer control 'IEC958',0
  Capabilities: cvolume pswitch pswitch-joined cswitch cswitch-joined penum
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 115
  Mono: Playback [on]
  Front Left: Capture 0 [0%] [-51.50dB] [off]
  Front Right: Capture 0 [0%] [-51.50dB] [off]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]


!!Alsactl output
!!-------------

--startcollapse--
state.SB {
    control.1 {
        iface MIXER
        name 'Front Playback Volume'
        value.0 39
        value.1 39
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 39'
            dbmin -5850
            dbmax 0
            dbvalue.0 0
            dbvalue.1 0
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
        value.0 39
        value.1 39
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 39'
            dbmin -5850
            dbmax 0
            dbvalue.0 0
            dbvalue.1 0
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
        value 39
        comment {
            access 'read write'
            type INTEGER
            count 1
            range '0 - 39'
            dbmin -5850
            dbmax 0
            dbvalue.0 0
        }
    }
    control.6 {
        iface MIXER
        name 'LFE Playback Volume'
        value 39
        comment {
            access 'read write'
            type INTEGER
            count 1
            range '0 - 39'
            dbmin -5850
            dbmax 0
            dbvalue.0 0
        }
    }
    control.7 {
        iface MIXER
        name 'Center Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
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
        name 'Side Playback Volume'
        value.0 39
        value.1 39
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 39'
            dbmin -5850
            dbmax 0
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.10 {
        iface MIXER
        name 'Side Playback Switch'
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
        name 'Headphone Playback Switch'
        value.0 true
        value.1 true
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.12 {
        iface MIXER
        name 'Front Mic Playback Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 31'
            dbmin -3450
            dbmax 1200
            dbvalue.0 -3450
            dbvalue.1 -3450
        }
    }
    control.13 {
        iface MIXER
        name 'Front Mic Playback Switch'
        value.0 false
        value.1 false
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.14 {
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
            dbmax 3000
            dbvalue.0 3000
            dbvalue.1 3000
        }
    }
    control.15 {
        iface MIXER
        name 'Rear Mic Playback Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 31'
            dbmin -3450
            dbmax 1200
            dbvalue.0 -3450
            dbvalue.1 -3450
        }
    }
    control.16 {
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
    control.17 {
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
            dbmax 3000
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.18 {
        iface MIXER
        name 'Line Playback Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 31'
            dbmin -3450
            dbmax 1200
            dbvalue.0 -3450
            dbvalue.1 -3450
        }
    }
    control.19 {
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
    control.20 {
        iface MIXER
        name 'CD Playback Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 31'
            dbmin -3450
            dbmax 1200
            dbvalue.0 -3450
            dbvalue.1 -3450
        }
    }
    control.21 {
        iface MIXER
        name 'CD Playback Switch'
        value.0 false
        value.1 false
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.22 {
        iface MIXER
        name 'Analog Mix Playback Volume'
        value.0 31
        value.1 31
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 31'
            dbmin -4650
            dbmax 0
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.23 {
        iface MIXER
        name 'Analog Mix Playback Switch'
        value.0 true
        value.1 true
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.24 {
        iface MIXER
        name 'Capture Volume'
        value.0 53
        value.1 53
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 54'
            dbmin -5850
            dbmax 2250
            dbvalue.0 2100
            dbvalue.1 2100
        }
    }
    control.25 {
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
    control.26 {
        iface MIXER
        name 'Capture Volume'
        index 1
        value.0 39
        value.1 39
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 54'
            dbmin -5850
            dbmax 2250
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.27 {
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
    control.28 {
        iface MIXER
        name 'Capture Volume'
        index 2
        value.0 39
        value.1 39
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 54'
            dbmin -5850
            dbmax 2250
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.29 {
        iface MIXER
        name 'Capture Switch'
        index 2
        value.0 false
        value.1 false
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.30 {
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
            item.3 CD
            item.4 Mix
        }
    }
    control.31 {
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
            item.3 CD
            item.4 Mix
        }
    }
    control.32 {
        iface MIXER
        name 'Input Source'
        index 2
        value 'Front Mic'
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 'Front Mic'
            item.1 'Rear Mic'
            item.2 Line
            item.3 CD
            item.4 Mix
        }
    }
    control.33 {
        iface MIXER
        name 'IEC958 Playback Volume'
        value.0 39
        value.1 39
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 39'
            dbmin -5850
            dbmax 0
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.34 {
        iface MIXER
        name 'IEC958 Playback Source'
        value PCM
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 PCM
            item.1 ADC1
            item.2 ADC2
            item.3 ADC3
        }
    }
    control.35 {
        iface MIXER
        name 'IEC958 Playback Con Mask'
        value  '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.36 {
        iface MIXER
        name 'IEC958 Playback Pro Mask'
        value  '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.37 {
        iface MIXER
        name 'IEC958 Playback Default'
        value  '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access 'read write'
            type IEC958
            count 1
        }
    }
    control.38 {
        iface MIXER
        name 'IEC958 Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.39 {
        iface MIXER
        name 'IEC958 Default PCM Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.40 {
        iface MIXER
        name 'Beep Playback Volume'
        value 15
        comment {
            access 'read write'
            type INTEGER
            count 1
            range '0 - 15'
            dbmin -4500
            dbmax 0
            dbvalue.0 0
        }
    }
    control.41 {
        iface MIXER
        name 'Beep Playback Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.42 {
        iface MIXER
        name 'Master Playback Volume'
        value 39
        comment {
            access 'read write'
            type INTEGER
            count 1
            range '0 - 39'
            dbmin -5850
            dbmax 0
            dbvalue.0 0
        }
    }
    control.43 {
        iface MIXER
        name 'Master Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.44 {
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
}
state.Camera {
    control.1 {
        iface MIXER
        name 'Mic Capture Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.2 {
        iface MIXER
        name 'Mic Capture Volume'
        value 1
        comment {
            access 'read write'
            type INTEGER
            count 1
            range '0 - 2'
            dbmin 3000
            dbmax 5000
            dbvalue.0 4000
        }
    }
}
state.Creative {
    control.1 {
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
    control.2 {
        iface MIXER
        name 'Front Playback Volume'
        value.0 102
        value.1 102
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 103'
            dbmin -5150
            dbmax 0
            dbvalue.0 -50
            dbvalue.1 -50
        }
    }
    control.3 {
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
    control.4 {
        iface MIXER
        name 'Surround Playback Volume'
        value.0 103
        value.1 103
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 103'
            dbmin -5150
            dbmax 0
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.5 {
        iface MIXER
        name 'Center Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.6 {
        iface MIXER
        name 'LFE Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.7 {
        iface MIXER
        name 'Center Playback Volume'
        value 103
        comment {
            access 'read write'
            type INTEGER
            count 1
            range '0 - 103'
            dbmin -5150
            dbmax 0
            dbvalue.0 0
        }
    }
    control.8 {
        iface MIXER
        name 'LFE Playback Volume'
        value 103
        comment {
            access 'read write'
            type INTEGER
            count 1
            range '0 - 103'
            dbmin -5150
            dbmax 0
            dbvalue.0 0
        }
    }
    control.9 {
        iface MIXER
        name 'Side Playback Switch'
        value.0 true
        value.1 true
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.10 {
        iface MIXER
        name 'Side Playback Volume'
        value.0 103
        value.1 103
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 103'
            dbmin -5150
            dbmax 0
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.11 {
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
    control.12 {
        iface MIXER
        name 'Headphone Playback Volume'
        value.0 103
        value.1 103
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 103'
            dbmin -5150
            dbmax 0
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.13 {
        iface MIXER
        name 'Line Capture Switch'
        value.0 false
        value.1 false
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.14 {
        iface MIXER
        name 'Line Capture Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 115'
            dbmin -5150
            dbmax 600
            dbvalue.0 -5150
            dbvalue.1 -5150
        }
    }
    control.15 {
        iface MIXER
        name 'Front Mic Capture Switch'
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
        name 'Front Mic Capture Volume'
        value.0 101
        value.1 101
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 127'
            dbmin -5150
            dbmax 1200
            dbvalue.0 -100
            dbvalue.1 -100
        }
    }
    control.17 {
        iface MIXER
        name 'IEC958 Playback Con Mask'
        value  '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.18 {
        iface MIXER
        name 'IEC958 Playback Pro Mask'
        value  '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.19 {
        iface MIXER
        name 'IEC958 Playback Default'
        value  '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access 'read write'
            type IEC958
            count 1
        }
    }
    control.20 {
        iface MIXER
        name 'IEC958 Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.21 {
        iface MIXER
        name 'IEC958 Default PCM Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.22 {
        iface MIXER
        name 'IEC958 Capture Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.23 {
        iface MIXER
        name 'IEC958 Capture Default'
        value  '0300000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.24 {
        iface MIXER
        name 'IEC958 Capture Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 115'
            dbmin -5150
            dbmax 600
            dbvalue.0 -5150
            dbvalue.1 -5150
        }
    }
    control.25 {
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
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
parport_pc
ppdev
vesafb
bnep
rfcomm
bluetooth
binfmt_misc
snd_hda_codec_ca0110
snd_hda_codec_analog
nvidia
arc4
sp5100_tco
joydev
uvcvideo
snd_usb_audio
snd_usbmidi_lib
videodev
v4l2_compat_ioctl32
snd_hda_intel
snd_hda_codec
snd_hwdep
snd_pcm
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
snd_seq
asus_atk0110
snd_timer
snd_seq_device
snd
psmouse
wmi
ath5k
i2c_piix4
edac_core
ath
mac80211
edac_mce_amd
k10temp
soundcore
snd_page_alloc
serio_raw
shpchp
cfg80211
lp
parport
firewire_ohci
usbhid
firewire_core
hid
pata_marvell
crc_itu_t
pata_atiixp
ahci
sky2
libahci


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x11 0x02214030
0x12 0x01014010
0x13 0x511711f0
0x14 0x02a19021
0x15 0x0181302e
0x16 0x01011012
0x17 0x01a19020
0x18 0x99331122
0x1a 0x91f711f0
0x1b 0x0145f1a0
0x1c 0x41c5f160
0x24 0x01016011
0x25 0x01012014

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:

/sys/class/sound/hwC2D1/init_pin_configs:
0x0b 0x01014010
0x0c 0x01016011
0x0d 0x01011012
0x0e 0x01012014
0x0f 0x02214020
0x10 0x01813030
0x11 0x02a19040
0x12 0x01452150
0x13 0x01c51160

/sys/class/sound/hwC2D1/driver_pin_configs:

/sys/class/sound/hwC2D1/user_pin_configs:

/sys/class/sound/hwC2D1/init_verbs:


!!ALSA/HDA dmesg
!!------------------

[   12.652282] ath: Regpair used: 0x37
[   12.652313] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.652376] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
--
[   13.127280] Disabling lock debugging due to kernel taint
[   13.249180] hda_codec: AD1988B: BIOS auto-probing.
[   13.260852] HDA Intel 0000:07:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   13.339381] type=1400 audit(1334781661.373:5): apparmor="STATUS"  operation="profile_replace" name="/sbin/dhclient" pid=979  comm="apparmor_parser"

```



[http://www.alsa-project.org/db/?f=899a9ba1afa0feaaa698505edd1b5a830704b4dc](http://www.alsa-project.org/db/?f=899a9ba1afa0feaaa698505edd1b5a830704b4dc)

I'm using ubuntu 11.10 64 bits.

Can everybody help me?

Thanks :) ):P

---

### Post by cgaie on 2012-04-19
I am in the same boat. 

I have a Creative SB X-Fi Xtreme Audio card

I am running a Windows 7 dual boot on a Dell XPS8300 and the sound works great in Windows, but in Ubuntu 11.10,I don't get sound

It hops all the time and I can't listen to music.  Try installing different players and it's the same I get a distorted sound

If I go to system/audio, then I click on audio I can hear audio, the problem occurs when playing any music 

I have tried Installing Linux Alsa Driver Modules and not joy

Any ideas what can be done?


Thanks

:guitar: I can't hear

---

### Post by jask05 on 2012-04-20
> **cgaie said:**
> I am in the same boat. 

I have a Creative SB X-Fi Xtreme Audio card

I am running a Windows 7 dual boot on a Dell XPS8300 and the sound works great in Windows, but in Ubuntu 11.10,I don't get sound

It hops all the time and I can't listen to music.  Try installing different players and it's the same I get a distorted sound

If I go to system/audio, then I click on audio I can hear audio, the problem occurs when playing any music 

I have tried Installing Linux Alsa Driver Modules and not joy

Any ideas what can be done?


Thanks

:guitar: I can't hear

Yes, we have the same problem. I would like one person can help us :( I want to listen music :( !!! :guitar:

Thanks !!

---

### Post by cgaie on 2012-04-20
I have tried Linuxmint and my audio doesn't work neither but I tried beta build 12.04 and my audio Creative SB X-Fi Xtreme Audio works out of the box

It looks like they are working on it

---

### Post by jask05 on 2012-04-21
> **cgaie said:**
> I have tried Linuxmint and my audio doesn't work neither but I tried beta build 12.04 and my audio Creative SB X-Fi Xtreme Audio works out of the box

It looks like they are working on it

Good :) I hope the next release can fix this problem.

Thanks :)

---

