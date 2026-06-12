---
title: "Alienware m15x ubuntu 10.10 realtek ALC889A NO SOUND HELP PLSSS"
date: 2011-04-18
forum: Multimedia Software
---

### Post by elflako17 on 2011-04-18
Plss help i have been looking for a solution to this this hole week i cant seem to find it and i am loosing my patients plss help here is some info about my alienware

upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Mon Apr 18 04:07:44 UTC 2011


!!Linux Distribution
!!------------------

Ubuntu 10.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.10"


!!DMI Information
!!---------------

Manufacturer:      Alienware   
Product Name:      m15x            
Product Version:   Not Applicable


!!Kernel Information
!!------------------

Kernel release:    2.6.35-28-generic
Operating System:  GNU/Linux
Architecture:      i686
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
                      HDA Intel at 0xf0600000 irq 48
 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xcfeec000 irq 49


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
01:00.1 Audio device: ATI Technologies Inc Radeon HD 3870 Audio device


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:284b (rev 03)
    Subsystem: 152d:0770
--
01:00.1 0403: 1002:aa18
    Subsystem: 152d:aa18


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
snd-hda-intel: model=generic


!!Loaded sound module options
!!--------------------------

!!Module: snd_hda_intel
    bdl_pos_adj : 1,32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    beep_mode : 1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1
    enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
    enable_msi : -1
    id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    model : dell,(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    patch : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    position_fix : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    power_save : 0
    power_save_controller : Y
    probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    single_cmd : N

!!Module: snd_hda_intel
    bdl_pos_adj : 1,32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    beep_mode : 1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1
    enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
    enable_msi : -1
    id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    model : dell,(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
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

Codec: Realtek ALC889A
Address: 0
AFG Function Id: 0x1 (unsol 1)
Vendor Id: 0x10ec0885
Subsystem Id: 0x152d0770
Revision Id: 0x100103
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
  Device: name="ALC889A Analog", type="Audio", device=0
  Converter: stream=5, channel=0
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
  Device: name="ALC889A Digital", type="SPDIF", device=1
  Converter: stream=8, channel=0
  Digital: Enabled GenLevel
  Digital category: 0x2
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0x1e]: 16 20 24 32
    formats [0x1]: PCM
Node 0x07 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Control: name="Capture Switch", index=0, device=0
  Control: name="Capture Volume", index=0, device=0
  Device: name="ALC889A Analog", type="Audio", device=0
  Amp-In caps: ofs=0x10, nsteps=0x2e, stepsize=0x03, mute=1
  Amp-In vals:  [0x80 0x80]
  Converter: stream=1, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Connection: 1
     0x24
Node 0x08 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Control: name="Capture Switch", index=1, device=0
  Control: name="Capture Volume", index=1, device=0
  Amp-In caps: ofs=0x10, nsteps=0x2e, stepsize=0x03, mute=1
  Amp-In vals:  [0x00 0x00]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Connection: 1
     0x23
Node 0x09 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Control: name="Capture Switch", index=2, device=0
  Control: name="Capture Volume", index=2, device=0
  Amp-In caps: ofs=0x10, nsteps=0x2e, stepsize=0x03, mute=1
  Amp-In vals:  [0x00 0x00]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
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
  Control: name="Beep Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=5, ofs=0
  Control: name="Beep Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=5, ofs=0
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x80 0x80] [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97]
  Connection: 10
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17
Node 0x0c [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Control: name="Speaker Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Speaker Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x40 0x40]
  Connection: 2
     0x02 0x0b
Node 0x0d [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 2
     0x03 0x0b
Node 0x0e [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 2
     0x04 0x0b
Node 0x0f [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x00 0x00]
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
  Pincap 0x0000373c: IN OUT HP Detect
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x99130110: [Fixed] Speaker at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x15 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000373c: IN OUT HP Detect
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c 0x0d* 0x0e 0x0f 0x26
Node 0x16 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000003c: IN OUT HP Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c 0x0d 0x0e* 0x0f 0x26
Node 0x17 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000003c: IN OUT HP Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c 0x0d 0x0e 0x0f* 0x26
Node 0x18 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Control: name="Mic Boost Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000373c: IN OUT HP Detect
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x01a1ec30: [Jack] Mic at Ext Rear
    Conn = 1/8, Color = White
    DefAssociation = 0x3, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x19 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000373c: IN OUT HP Detect
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1a [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000373c: IN OUT HP Detect
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
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
  Pincap 0x0000373c: IN OUT HP Detect
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x0121ec1f: [Jack] HP Out at Ext Rear
    Conn = 1/8, Color = White
    DefAssociation = 0x1, Sequence = 0xf
  Pin-ctls: 0xc0: OUT HP VREF_HIZ
  Unsolicited: tag=04, enabled=1
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1c [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
Node 0x1d [Pin Complex] wcaps 0x400000: Mono
  Pincap 0x00000020: IN
  Pin Default 0x40168a2d: [N/A] Speaker at Ext N/A
    Conn = Digital, Color = Purple
    DefAssociation = 0x2, Sequence = 0xd
  Pin-ctls: 0x20: IN
Node 0x1e [Pin Complex] wcaps 0x400300: Mono Digital
  Pincap 0x00000010: OUT
  Pin Default 0x0145e120: [Jack] SPDIF Out at Ext Rear
    Conn = Optical, Color = White
    DefAssociation = 0x2, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x06
Node 0x1f [Pin Complex] wcaps 0x400200: Mono Digital
  Pincap 0x00000020: IN
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
Node 0x20 [Vendor Defined Widget] wcaps 0xf00040: Mono
  Processing caps: benign=0, ncoeff=17
Node 0x21 [Volume Knob Widget] wcaps 0x600080: Mono
  Volume-Knob: delta=0, steps=32, direct=0, val=64
  Unsolicited: tag=00, enabled=0
  Connection: 0
Node 0x22 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 11
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b
Node 0x23 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 11
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b
Node 0x24 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 11
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b
Node 0x25 [Audio Output] wcaps 0x11: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x26 [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x40 0x40]
  Connection: 2
     0x25 0x0b
Codec: ATI R6xx HDMI
Address: 0
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x1002aa01
Subsystem Id: 0x00aa0100
Revision Id: 0x100000
No Modem Function Group found
Default PCM:
    rates [0x40]: 48000
    bits [0x2]: 16
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x02 [Audio Output] wcaps 0x201: Stereo Digital
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Device: name="HDMI 0", type="HDMI", device=3
  Converter: stream=1, channel=0
  Digital: Enabled GenLevel
  Digital category: 0x2
Node 0x03 [Pin Complex] wcaps 0x400381: Stereo Digital
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

crw-rw----+ 1 root audio 116,  6 Apr 18 00:00 /dev/snd/controlC0
crw-rw----+ 1 root audio 116,  9 Apr 18 00:00 /dev/snd/controlC1
crw-rw----+ 1 root audio 116,  5 Apr 18 00:00 /dev/snd/hwC0D0
crw-rw----+ 1 root audio 116,  8 Apr 18 00:00 /dev/snd/hwC1D0
crw-rw----+ 1 root audio 116,  4 Apr 18 00:05 /dev/snd/pcmC0D0c
crw-rw----+ 1 root audio 116,  3 Apr 18 00:00 /dev/snd/pcmC0D0p
crw-rw----+ 1 root audio 116,  2 Apr 18 00:06 /dev/snd/pcmC0D1p
crw-rw----+ 1 root audio 116,  7 Apr 18 00:06 /dev/snd/pcmC1D3p
crw-rw----+ 1 root audio 116,  1 Apr 18 00:00 /dev/snd/seq
crw-rw----+ 1 root audio 116, 33 Apr 18 00:00 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  80 Apr 18 00:00 .
drwxr-xr-x 3 root root 260 Apr 18 00:00 ..
lrwxrwxrwx 1 root root  12 Apr 18 00:00 pci-0000:00:1b.0 -> ../controlC0
lrwxrwxrwx 1 root root  12 Apr 18 00:00 pci-0000:01:00.1 -> ../controlC1


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [Intel]

Card hw:0 'Intel'/'HDA Intel at 0xf0600000 irq 48'
  Mixer name    : 'Realtek ALC889A'
  Components    : 'HDA:10ec0885,152d0770,00100103'
  Controls      : 22
  Simple ctrls  : 12
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pswitch penum
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [on]
  Front Right: Playback [on]
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
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
  Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB]
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
  Front Left: Playback 23 [74%] [0.00dB] [off]
  Front Right: Playback 23 [74%] [0.00dB] [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 46
  Front Left: Capture 0 [0%] [-16.00dB] [off]
  Front Right: Capture 0 [0%] [-16.00dB] [off]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 46
  Front Left: Capture 0 [0%] [-16.00dB] [on]
  Front Right: Capture 0 [0%] [-16.00dB] [on]
Simple mixer control 'Capture',2
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 46
  Front Left: Capture 0 [0%] [-16.00dB] [on]
  Front Right: Capture 0 [0%] [-16.00dB] [on]

!!-------Mixer controls for card 1 [HDMI]

Card hw:1 'HDMI'/'HDA ATI HDMI at 0xcfeec000 irq 49'
  Mixer name    : 'ATI R6xx HDMI'
  Components    : 'HDA:1002aa01,00aa0100,00100000'
  Controls      : 4
  Simple ctrls  : 1
Simple mixer control 'IEC958',0
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
        comment.range '0 - 64'
        comment.dbmin -6400
        comment.dbmax 0
        iface MIXER
        name 'Speaker Playback Volume'
        value.0 64
        value.1 64
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
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Headphone Playback Switch'
        value.0 true
        value.1 true
    }
    control.4 {
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
    control.5 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Mic Playback Switch'
        value.0 false
        value.1 false
    }
    control.6 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 3'
        comment.dbmin 0
        comment.dbmax 3000
        iface MIXER
        name 'Mic Boost Volume'
        value.0 0
        value.1 0
    }
    control.7 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Capture Switch'
        value.0 false
        value.1 false
    }
    control.8 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Capture Switch'
        index 1
        value.0 true
        value.1 true
    }
    control.9 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Capture Switch'
        index 2
        value.0 true
        value.1 true
    }
    control.10 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 46'
        comment.dbmin -1600
        comment.dbmax 3000
        iface MIXER
        name 'Capture Volume'
        value.0 0
        value.1 0
    }
    control.11 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 46'
        comment.dbmin -1600
        comment.dbmax 3000
        iface MIXER
        name 'Capture Volume'
        index 1
        value.0 0
        value.1 0
    }
    control.12 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 46'
        comment.dbmin -1600
        comment.dbmax 3000
        iface MIXER
        name 'Capture Volume'
        index 2
        value.0 0
        value.1 0
    }
    control.13 {
        comment.access read
        comment.type IEC958
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Con Mask'
        value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.14 {
        comment.access read
        comment.type IEC958
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Pro Mask'
        value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.15 {
        comment.access 'read write'
        comment.type IEC958
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Default'
        value '0482000200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.16 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Switch'
        value true
    }
    control.17 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'IEC958 Default PCM Playback Switch'
        value true
    }
    control.18 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'Beep Playback Volume'
        value.0 23
        value.1 23
    }
    control.19 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Beep Playback Switch'
        value.0 false
        value.1 false
    }
    control.20 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 64'
        comment.dbmin -6400
        comment.dbmax 0
        iface MIXER
        name 'Master Playback Volume'
        value 64
    }
    control.21 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Master Playback Switch'
        value true
    }
    control.22 {
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
state.HDMI {
    control.1 {
        comment.access read
        comment.type IEC958
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Con Mask'
        value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.2 {
        comment.access read
        comment.type IEC958
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Pro Mask'
        value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.3 {
        comment.access 'read write'
        comment.type IEC958
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Default'
        value '0482000200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.4 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Switch'
        value true
    }
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
aes_i586
aes_generic
nls_utf8
udf
parport_pc
ppdev
dm_crypt
binfmt_misc
arc4
snd_hda_codec_hdmi
snd_hda_codec_realtek
snd_hda_intel
snd_hda_codec
snd_hwdep
snd_pcm
iwlagn
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
snd_seq
iwlcore
snd_timer
mac80211
snd_seq_device
fglrx
r852
sm_common
uvcvideo
sparse_keymap
nand
nand_ids
nand_ecc
joydev
cfg80211
videodev
mtd
psmouse
snd
v4l1_compat
serio_raw
soundcore
snd_page_alloc
lp
parport
dm_raid45
xor
btrfs
zlib_deflate
crc32c
libcrc32c
usbhid
hid
video
ahci
firewire_ohci
sdhci_pci
sdhci
output
tg3
intel_agp
led_class
firewire_core
libahci
crc_itu_t
agpgart
ramzswap
lzo_compress


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x14 0x99130110
0x15 0x411111f0
0x16 0x411111f0
0x17 0x411111f0
0x18 0x01a1ec30
0x19 0x411111f0
0x1a 0x411111f0
0x1b 0x0121ec1f
0x1c 0x411111f0
0x1d 0x40168a2d
0x1e 0x0145e120
0x1f 0x411111f0

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:

/sys/class/sound/hwC1D0/init_pin_configs:
0x03 0x18560010

/sys/class/sound/hwC1D0/driver_pin_configs:

/sys/class/sound/hwC1D0/user_pin_configs:

/sys/class/sound/hwC1D0/init_verbs:


!!ALSA/HDA dmesg
!!------------------

[   20.999729]   alloc kstat_irqs on node -1
[   20.999744] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   20.999833]   alloc irq_desc for 48 on node -1
[   20.999838]   alloc kstat_irqs on node -1
[   20.999859] HDA Intel 0000:00:1b.0: irq 48 for MSI/MSI-X
[   20.999920] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   20.999931] ALSA hda_intel.c:2565: chipset global capabilities = 0x4401
[   21.029053] ALSA hda_intel.c:914: codec_mask = 0x1
[   21.029166] ALSA hda_intel.c:1357: codec #0 probed OK
[   21.060201] hda_codec: ALC889A: BIOS auto-probing.
[   21.060211] ALSA patch_realtek.c:1476: SKU: Nid=0x1d sku_cfg=0x40168a2d
[   21.060221] ALSA patch_realtek.c:1478: SKU: port_connectivity=0x1
[   21.060229] ALSA patch_realtek.c:1479: SKU: enable_pcbeep=0x1
[   21.060238] ALSA patch_realtek.c:1480: SKU: check_sum=0x00000006
[   21.060246] ALSA patch_realtek.c:1481: SKU: customization=0x0000008a
[   21.060254] ALSA patch_realtek.c:1482: SKU: external_amp=0x5
[   21.060262] ALSA patch_realtek.c:1483: SKU: platform_type=0x1
[   21.060270] ALSA patch_realtek.c:1484: SKU: swap=0x0
[   21.060278] ALSA patch_realtek.c:1485: SKU: override=0x1
[   21.060290] ALSA hda_codec.c:4699: autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0)
[   21.060300] ALSA hda_codec.c:4703:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   21.060310] ALSA hda_codec.c:4707:    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[   21.060320] ALSA hda_codec.c:4708:    mono: mono_out=0x0
[   21.060328] ALSA hda_codec.c:4711:    dig-out=0x1e/0x0
[   21.060335] ALSA hda_codec.c:4712:    inputs:
[   21.060343] ALSA hda_codec.c:4716:  Mic=0x18
[   21.060350] ALSA hda_codec.c:4718: 
[   21.060824] ALSA patch_realtek.c:1533: realtek: No valid SSID, checking pincfg 0x40168a2d for NID 0x1d
[   21.060834] ALSA patch_realtek.c:1549: realtek: Enabling init ASM_ID=0x8a2d CODEC_ID=10ec0885
[   21.060844] ALSA patch_realtek.c:1363: realtek: Enable HP auto-muting on NID 0x1b
[   21.060985] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input10
[   21.063819] ALSA hda_codec.c:2230: Cannot find slave Front Playback Volume, skipped
[   21.063830] ALSA hda_codec.c:2230: Cannot find slave Surround Playback Volume, skipped
[   21.063839] ALSA hda_codec.c:2230: Cannot find slave Center Playback Volume, skipped
[   21.063849] ALSA hda_codec.c:2230: Cannot find slave LFE Playback Volume, skipped
[   21.063858] ALSA hda_codec.c:2230: Cannot find slave Side Playback Volume, skipped
[   21.063867] ALSA hda_codec.c:2230: Cannot find slave Headphone Playback Volume, skipped
[   21.063880] ALSA hda_codec.c:2230: Cannot find slave Mono Playback Volume, skipped
[   21.063889] ALSA hda_codec.c:2230: Cannot find slave Line-Out Playback Volume, skipped
[   21.063897] ALSA hda_codec.c:2230: Cannot find slave PCM Playback Volume, skipped
[   21.063917] ALSA hda_codec.c:2230: Cannot find slave Front Playback Switch, skipped
[   21.063926] ALSA hda_codec.c:2230: Cannot find slave Surround Playback Switch, skipped
[   21.063935] ALSA hda_codec.c:2230: Cannot find slave Center Playback Switch, skipped
[   21.063944] ALSA hda_codec.c:2230: Cannot find slave LFE Playback Switch, skipped
[   21.063954] ALSA hda_codec.c:2230: Cannot find slave Side Playback Switch, skipped
[   21.063969] ALSA hda_codec.c:2230: Cannot find slave Mono Playback Switch, skipped
[   21.063983] ALSA hda_codec.c:2230: Cannot find slave Line-Out Playback Switch, skipped
[   21.063992] ALSA hda_codec.c:2230: Cannot find slave PCM Playback Switch, skipped
[   21.065741] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   21.066538] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   21.066641]   alloc irq_desc for 49 on node -1
[   21.066647]   alloc kstat_irqs on node -1
[   21.066670] HDA Intel 0000:01:00.1: irq 49 for MSI/MSI-X
[   21.066727] HDA Intel 0000:01:00.1: setting latency timer to 64
[   21.066738] ALSA hda_intel.c:2565: chipset global capabilities = 0x1001
[   21.081053] ALSA hda_intel.c:914: codec_mask = 0x1
[   21.081131] ALSA hda_intel.c:1357: codec #0 probed OK
[   21.082918] iwlagn 0000:06:00.0: loaded firmware version 228.61.2.24
[   21.101534] HDMI: sink_present = 0, eld_valid = 1
[   21.222607] phy0: Selected rate control algorithm 'iwl-agn-rs'
--
[   23.742091] [fglrx] Reserved FB block: Unshared offset:1fffc000, size:4000 
[   26.277874] ALSA hda_intel.c:1682: azx_pcm_prepare: bufsize=0x3c00, format=0x11
[   26.277911] ALSA hda_codec.c:1293: hda_codec_setup_stream: NID=0x2, stream=0x1, channel=0, format=0x11
[   26.285048] ALSA hda_intel.c:1682: azx_pcm_prepare: bufsize=0x3c00, format=0x11
[   26.285076] ALSA hda_codec.c:1293: hda_codec_setup_stream: NID=0x2, stream=0x1, channel=0, format=0x11
[   26.288216] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.288283] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.295521] ALSA hda_intel.c:1682: azx_pcm_prepare: bufsize=0x10000, format=0x11
[   26.295552] ALSA hda_codec.c:1293: hda_codec_setup_stream: NID=0x2, stream=0x1, channel=0, format=0x11
[   26.295577] ALSA hda_intel.c:1682: azx_pcm_prepare: bufsize=0x10000, format=0x11
[   26.295603] ALSA hda_codec.c:1293: hda_codec_setup_stream: NID=0x2, stream=0x1, channel=0, format=0x11
[   26.320232] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.320702] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.321424] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.322376] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.322846] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.323300] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.323933] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.324878] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.325367] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.325820] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.326450] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.327391] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.327859] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.328315] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.328949] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.329922] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.330391] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.330846] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.331480] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.332432] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.335869] ALSA hda_intel.c:1682: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   26.335895] ALSA hda_codec.c:1293: hda_codec_setup_stream: NID=0x6, stream=0x5, channel=0, format=0x4011
[   26.345040] ALSA hda_codec.c:1293: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[   26.353050] ALSA hda_intel.c:1682: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   26.353071] ALSA hda_codec.c:1293: hda_codec_setup_stream: NID=0x6, stream=0x5, channel=0, format=0x4011
[   26.353085] ALSA hda_codec.c:1293: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[   26.353617] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x7
[   26.354078] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x7
[   26.354718] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x7
[   26.355664] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x7
[   26.356966] ALSA hda_intel.c:1682: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   26.356985] ALSA hda_codec.c:1293: hda_codec_setup_stream: NID=0x7, stream=0x1, channel=0, format=0x4011
[   26.365051] ALSA hda_intel.c:1682: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   26.365067] ALSA hda_codec.c:1293: hda_codec_setup_stream: NID=0x7, stream=0x1, channel=0, format=0x4011
[   26.365115] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x7
[   26.365145] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x7
[   26.367026] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.367037] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x6
[   26.367072] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.368092] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.369131] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.370457] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.372135] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.373198] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.374211] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.375517] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.378654] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.379678] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.380689] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.382040] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.383714] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.384738] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.385779] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.387098] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.388769] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.389824] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.390837] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.392156] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.395327] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.396263] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.397214] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.398167] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.399127] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.400041] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.400943] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.401915] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.402871] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.403782] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.404685] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.406895] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.407872] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.408783] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.409841] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.410794] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.411752] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.412664] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.413715] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.414658] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.415617] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.416526] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.417601] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.418546] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.419499] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.420406] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.421467] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.422415] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.423374] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.424284] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.425354] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.426302] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.427265] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.428175] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.429249] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.430202] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.431161] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.432077] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.432977] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.434392] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.435345] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.436362] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.437876] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.439197] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.440861] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.442314] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.443328] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.444646] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.446819] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.447843] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.448856] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.450588] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.452261] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.453747] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.454764] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.456082] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.458183] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.459207] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.460214] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.461936] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.463611] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.464636] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.466160] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.467477] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.473374] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.474411] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.475422] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.477333] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.479010] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.480035] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.481516] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.482840] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.483638] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   26.484505] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.485565] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.486571] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.487882] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.489596] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.490624] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.491633] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.492952] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.494649] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   26.496045] ALSA hda_intel.c:1682: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   26.496071] ALSA hda_codec.c:1293: hda_codec_setup_stream: NID=0x6, stream=0x8, channel=0, format=0x4011
[   26.496164] ALSA hda_intel.c:1682: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   26.496186] ALSA hda_codec.c:1293: hda_codec_setup_stream: NID=0x6, stream=0x8, channel=0, format=0x4011
[   26.496689] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x7
[   26.497171] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x7
[   26.497806] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x7
[   26.498751] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x7
[   26.500041] ALSA hda_intel.c:1682: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   26.500060] ALSA hda_codec.c:1293: hda_codec_setup_stream: NID=0x7, stream=0x1, channel=0, format=0x4011
[   26.500086] ALSA hda_intel.c:1682: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   26.500101] ALSA hda_codec.c:1293: hda_codec_setup_stream: NID=0x7, stream=0x1, channel=0, format=0x4011
[   26.500135] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x7
[   26.500165] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x7
[   26.502026] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x6
[   26.502090] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x6
[   26.503346] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x6
[   26.504598] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x6
[   26.506066] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x6
[   26.507808] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x6
[   26.509146] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x6
[   26.510402] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x6
[   26.511833] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x6
[   26.513617] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x6
[   26.514896] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x6
[   26.516151] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x6
[   26.517610] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x6
[   26.519356] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x6
[   26.520622] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x6
[   26.521919] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x6
[   26.523362] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x6
[   26.525157] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x6
[   26.526426] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x6
[   26.527677] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x6
[   26.529133] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x6
[   26.530879] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x6
[   26.536520] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x7
[   26.536975] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x7
[   26.537635] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x7
[   26.538575] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x7
[   26.539868] ALSA hda_intel.c:1682: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   26.539888] ALSA hda_codec.c:1293: hda_codec_setup_stream: NID=0x7, stream=0x1, channel=0, format=0x4011
[   26.539914] ALSA hda_intel.c:1682: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   26.539929] ALSA hda_codec.c:1293: hda_codec_setup_stream: NID=0x7, stream=0x1, channel=0, format=0x4011
[   26.539969] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x7
[   26.540002] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x7
[   26.545251] ALSA hda_intel.c:1682: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[   26.545276] ALSA hda_codec.c:1293: hda_codec_setup_stream: NID=0x6, stream=0x5, channel=0, format=0x4011
[   26.545334] ALSA hda_codec.c:1293: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[   26.545361] ALSA hda_intel.c:1682: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[   26.545379] ALSA hda_codec.c:1293: hda_codec_setup_stream: NID=0x6, stream=0x5, channel=0, format=0x4011
[   26.545392] ALSA hda_codec.c:1293: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[   26.566537] ALSA hda_intel.c:1682: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[   26.566556] ALSA hda_codec.c:1293: hda_codec_setup_stream: NID=0x7, stream=0x1, channel=0, format=0x4011
[   26.566582] ALSA hda_intel.c:1682: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[   26.566599] ALSA hda_codec.c:1293: hda_codec_setup_stream: NID=0x7, stream=0x1, channel=0, format=0x4011
[   27.415507] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[   31.654071] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x7
[   31.654116] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x7
[   31.655524] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   31.655612] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   32.739688] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   32.739701] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x6
[   32.739746] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   38.335364] ALSA hda_intel.c:1682: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[   38.335392] ALSA hda_codec.c:1293: hda_codec_setup_stream: NID=0x6, stream=0x5, channel=0, format=0x4011
[   38.335406] ALSA hda_codec.c:1293: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[   38.335432] ALSA hda_intel.c:1682: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[   38.335454] ALSA hda_codec.c:1293: hda_codec_setup_stream: NID=0x6, stream=0x5, channel=0, format=0x4011
[   38.335467] ALSA hda_codec.c:1293: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[   40.968109] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   40.968121] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x6
[   40.968182] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.215005] ALSA hda_intel.c:1682: azx_pcm_prepare: bufsize=0x3c00, format=0x11
[   42.215055] ALSA hda_codec.c:1293: hda_codec_setup_stream: NID=0x2, stream=0x1, channel=0, format=0x11
[   42.215081] ALSA hda_intel.c:1682: azx_pcm_prepare: bufsize=0x3c00, format=0x11
[   42.215108] ALSA hda_codec.c:1293: hda_codec_setup_stream: NID=0x2, stream=0x1, channel=0, format=0x11
[   42.219532] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.219760] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.227665] ALSA hda_intel.c:1682: azx_pcm_prepare: bufsize=0x10000, format=0x11
[   42.227698] ALSA hda_codec.c:1293: hda_codec_setup_stream: NID=0x2, stream=0x1, channel=0, format=0x11
[   42.227723] ALSA hda_intel.c:1682: azx_pcm_prepare: bufsize=0x10000, format=0x11
[   42.227750] ALSA hda_codec.c:1293: hda_codec_setup_stream: NID=0x2, stream=0x1, channel=0, format=0x11
[   42.289364] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.289993] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.290839] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.291995] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.292521] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.292979] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.293612] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.294561] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.295027] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.295482] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.296145] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.297096] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.297560] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.298013] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.298641] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.299585] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.300099] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.300553] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.301182] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.302125] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.303460] ALSA hda_intel.c:1682: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   42.303487] ALSA hda_codec.c:1293: hda_codec_setup_stream: NID=0x6, stream=0x5, channel=0, format=0x4011
[   42.303501] ALSA hda_codec.c:1293: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[   42.303537] ALSA hda_intel.c:1682: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   42.303561] ALSA hda_codec.c:1293: hda_codec_setup_stream: NID=0x6, stream=0x5, channel=0, format=0x4011
[   42.303574] ALSA hda_codec.c:1293: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[   42.304086] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x7
[   42.304543] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x7
[   42.305175] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x7
[   42.306117] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x7
[   42.307395] ALSA hda_intel.c:1682: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   42.307414] ALSA hda_codec.c:1293: hda_codec_setup_stream: NID=0x7, stream=0x1, channel=0, format=0x4011
[   42.307439] ALSA hda_intel.c:1682: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   42.307454] ALSA hda_codec.c:1293: hda_codec_setup_stream: NID=0x7, stream=0x1, channel=0, format=0x4011
[   42.307494] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x7
[   42.307526] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x7
[   42.312717] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.312728] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x6
[   42.312852] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.314155] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.315444] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.317079] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.319024] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.320431] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.321718] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.323313] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.325440] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.326761] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.328148] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.329873] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.331968] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.333353] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.334640] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.336355] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.338308] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.339609] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.341185] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.342888] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.345092] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.346437] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.347739] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.349331] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.350591] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.351917] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.353370] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.354717] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.356180] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.357392] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.358694] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.360145] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.361405] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.362723] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.364150] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.365398] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.366781] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.367996] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.369473] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.370834] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.372329] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.373655] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.374863] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.376355] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.377735] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.379043] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.380380] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.381741] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.383113] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.386589] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.387786] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.389136] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.390375] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.391565] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.392890] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.394128] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.395370] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.396721] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.397928] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.399180] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.400569] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.401888] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.403182] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.404910] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.406866] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.408292] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.409590] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.411194] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.413291] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.414606] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.415900] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.417798] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.419865] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.423367] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.424763] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.426373] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.428450] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.429762] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.431064] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.432803] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.434783] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.436221] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.437537] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.439142] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.441234] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.442557] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.443863] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.445770] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.447729] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.449207] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.450507] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.452504] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.456525] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.457969] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.459384] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.461261] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.463342] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.464865] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.466283] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.467991] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.470198] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   42.472153] ALSA hda_intel.c:1682: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   42.472179] ALSA hda_codec.c:1293: hda_codec_setup_stream: NID=0x6, stream=0x8, channel=0, format=0x4011
[   42.472269] ALSA hda_intel.c:1682: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   42.472292] ALSA hda_codec.c:1293: hda_codec_setup_stream: NID=0x6, stream=0x8, channel=0, format=0x4011
[   42.473093] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x7
[   42.473714] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x7
[   42.474616] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x7
[   42.475830] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x7
[   42.477540] ALSA hda_intel.c:1682: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   42.477559] ALSA hda_codec.c:1293: hda_codec_setup_stream: NID=0x7, stream=0x1, channel=0, format=0x4011
[   42.477587] ALSA hda_intel.c:1682: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   42.477602] ALSA hda_codec.c:1293: hda_codec_setup_stream: NID=0x7, stream=0x1, channel=0, format=0x4011
[   42.477637] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x7
[   42.477873] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x7
[   42.480371] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x6
[   42.480584] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x6
[   42.482276] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x6
[   42.484190] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x6
[   42.486071] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x6
[   42.488345] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x6
[   42.490028] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x6
[   42.491699] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x6
[   42.494419] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x6
[   42.496783] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x6
[   42.498989] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x6
[   42.500845] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x6
[   42.502697] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x6
[   42.505131] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x6
[   42.506706] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x6
[   42.508485] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x6
[   42.510461] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x6
[   42.512806] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x6
[   42.514501] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x6
[   42.516255] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x6
[   42.518111] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x6
[   42.520497] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x6
[   42.527625] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x7
[   42.530366] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x7
[   42.531165] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x7
[   42.532383] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x7
[   42.533855] ALSA hda_intel.c:1682: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   42.533875] ALSA hda_codec.c:1293: hda_codec_setup_stream: NID=0x7, stream=0x1, channel=0, format=0x4011
[   42.533903] ALSA hda_intel.c:1682: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   42.533918] ALSA hda_codec.c:1293: hda_codec_setup_stream: NID=0x7, stream=0x1, channel=0, format=0x4011
[   42.533958] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x7
[   42.534082] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x7
[   42.540329] ALSA hda_intel.c:1682: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[   42.540354] ALSA hda_codec.c:1293: hda_codec_setup_stream: NID=0x6, stream=0x8, channel=0, format=0x4011
[   42.540383] ALSA hda_intel.c:1682: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[   42.540415] ALSA hda_codec.c:1293: hda_codec_setup_stream: NID=0x6, stream=0x8, channel=0, format=0x4011
[   42.764382] ALSA hda_intel.c:1682: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[   42.764403] ALSA hda_codec.c:1293: hda_codec_setup_stream: NID=0x7, stream=0x1, channel=0, format=0x4011
[   42.764430] ALSA hda_intel.c:1682: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[   42.764445] ALSA hda_codec.c:1293: hda_codec_setup_stream: NID=0x7, stream=0x1, channel=0, format=0x4011
[   46.623001] UDF-fs: Partition marked readonly; forcing readonly mount
[   46.623834] UDF-fs INFO UDF: Mounting volume 'OFFICE12', timestamp 2006/10/27 20:00 (1f10)
[   48.160590] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x7
[   48.160641] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x7
[   48.166432] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x6
[   48.166529] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x6
[   56.776043] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   56.776158] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   57.352337] wlan0: authenticate with 00:24:01:41:9e:f1 (try 1)
--
[   57.411250] padlock: VIA PadLock not detected.
[   79.456880] ALSA hda_intel.c:1682: azx_pcm_prepare: bufsize=0x10000, format=0x11
[   79.456916] ALSA hda_codec.c:1293: hda_codec_setup_stream: NID=0x2, stream=0x1, channel=0, format=0x11
[   79.456942] ALSA hda_intel.c:1682: azx_pcm_prepare: bufsize=0x10000, format=0x11
[   79.456968] ALSA hda_codec.c:1293: hda_codec_setup_stream: NID=0x2, stream=0x1, channel=0, format=0x11
[   89.120985] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[   89.121098] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[  361.978841] ALSA hda_intel.c:1682: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[  361.978863] ALSA hda_codec.c:1293: hda_codec_setup_stream: NID=0x7, stream=0x1, channel=0, format=0x4011
[  361.978891] ALSA hda_intel.c:1682: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[  361.978906] ALSA hda_codec.c:1293: hda_codec_setup_stream: NID=0x7, stream=0x1, channel=0, format=0x4011
[  384.203798] ALSA hda_intel.c:1682: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[  384.203825] ALSA hda_codec.c:1293: hda_codec_setup_stream: NID=0x6, stream=0x8, channel=0, format=0x4011
[  384.203854] ALSA hda_intel.c:1682: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[  384.203876] ALSA hda_codec.c:1293: hda_codec_setup_stream: NID=0x6, stream=0x8, channel=0, format=0x4011
[  396.077888] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x6
[  396.077979] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x6
[  397.523621] ALSA hda_intel.c:1682: azx_pcm_prepare: bufsize=0x10000, format=0x11
[  397.523663] ALSA hda_codec.c:1293: hda_codec_setup_stream: NID=0x2, stream=0x1, channel=0, format=0x11
[  397.523689] ALSA hda_intel.c:1682: azx_pcm_prepare: bufsize=0x10000, format=0x11
[  397.523716] ALSA hda_codec.c:1293: hda_codec_setup_stream: NID=0x2, stream=0x1, channel=0, format=0x11
[  404.390465] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[  404.390566] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x2
[  407.866773] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x7
[  407.866826] ALSA hda_codec.c:1356: hda_codec_cleanup_stream: NID=0x7

---

### Post by joedoe47 on 2011-04-18
I just pmed flako about this issue and I asked if he could give the output for "lshw" (the output was in html, I just pasted it here as plaintext). I know from experience with a different model laptop that lshw can be helpful to determine what is there, missing and or incompatible.



   ```

id:    
flako-m15x
description:     Computer
product:     m15x
vendor:     Alienware
version:     Not Applicable
serial:     None
width:     32 bits
capabilities:     smbios-2.4 dmi-2.4 smp-1.4 smp
configuration:    
administrator_password    =    disabled
boot    =    oem-specific
cpus    =    2
frontpanel_password    =    unknown
keyboard_password    =    unknown
power-on_password    =    disabled
uuid    =    414C4945-3000-1030-8034-B0C04F374632
id:    
core
description:     Motherboard
product:     m15x
vendor:     Alienware
physical id:     
0
version:     Not Applicable
id:    
firmware
description:     BIOS
vendor:     Quanta
physical id:     
0
version:     vX36 P3 (08/29/2008)
size:     101KiB
capacity:     960KiB
capabilities:     isa pci pnp upgrade shadowing escd cdboot acpi usb agp biosbootspecification
id:    
cpu:0
description:     CPU
product:     Intel(R) Core(TM)2 Duo CPU T9500 @ 2.60GHz
vendor:     Intel Corp.
physical id:     
4
bus info:     
cpu@0
version:     6.7.6
serial:     0001-0676-0000-0000-0000-0000
slot:     U2E1
size:     800MHz
capacity:     2600MHz
width:     64 bits
clock:     200MHz
capabilities:     boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm tpr_shadow vnmi flexpriority cpufreq
configuration:    
id    =    1
id:    
cache:0
description:     L1 cache
physical id:     
5
slot:     L1 Cache
size:     64KiB
capacity:     64KiB
capabilities:     asynchronous internal write-back
id:    
cache:1
description:     L2 cache
physical id:     
6
slot:     L2 Cache
size:     6MiB
capabilities:     burst internal write-back
id:    
logicalcpu:0
description:     Logical CPU
physical id:     
1.1
width:     64 bits
capabilities:     logical
id:    
logicalcpu:1
description:     Logical CPU
physical id:     
1.2
width:     64 bits
capabilities:     logical
id:    
memory
description:     System Memory
physical id:     
f
slot:     System board or motherboard
size:     4GiB
id:    
bank:0
description:     SODIMM DDR2 Synchronous 667 MHz (1.5 ns)
product:     SODIMM000
vendor:     Mfg 0
physical id:     
0
serial:     1234-B0
slot:     M1
size:     2GiB
width:     64 bits
clock:     667MHz (1.5ns)
id:    
bank:1
description:     SODIMM DDR2 Synchronous 667 MHz (1.5 ns)
product:     SODIMM001
vendor:     Mfg 1
physical id:     
1
serial:     1234-B1
slot:     M2
size:     2GiB
width:     64 bits
clock:     667MHz (1.5ns)
id:    
cpu:1
physical id:     
1
bus info:     
cpu@1
version:     6.7.6
serial:     0001-0676-0000-0000-0000-0000
size:     800MHz
capacity:     800MHz
capabilities:     vmx ht cpufreq
configuration:    
id    =    1
id:    
logicalcpu:0
description:     Logical CPU
physical id:     
1.1
capabilities:     logical
id:    
logicalcpu:1
description:     Logical CPU
physical id:     
1.2
capabilities:     logical
id:    
pci
description:     Host bridge
product:     Mobile PM965/GM965/GL960 Memory Controller Hub
vendor:     Intel Corporation
physical id:     
100
bus info:     
pci@0000:00:00.0
version:     03
width:     32 bits
clock:     33MHz
id:    
pci:0
description:     PCI bridge
product:     Mobile PM965/GM965/GL960 PCI Express Root Port
vendor:     Intel Corporation
physical id:     
1
bus info:     
pci@0000:00:01.0
version:     03
width:     32 bits
clock:     33MHz
capabilities:     pci pm msi pciexpress normal_decode bus_master cap_list
configuration:    
driver    =    pcieport
resources:    
irq    :    40
ioport    :    2000(size=4096)
memory    :    cfe00000-cfefffff
ioport    :    d0000000(size=268435456)
id:    
display
description:     VGA compatible controller
product:     M88 XT Mobility Radeon HD 3870]
vendor:     ATI Technologies Inc
physical id:     
0
bus info:     
pci@0000:01:00.0
version:     00
width:     64 bits
clock:     33MHz
capabilities:     pm pciexpress msi vga_controller bus_master cap_list rom
configuration:    
driver    =    fglrx_pci
latency    =    0
resources:    
irq    :    51
memory    :    d0000000-dfffffff
memory    :    cfef0000-cfefffff
ioport    :    2000(size=256)
memory    :    cfe00000-cfe1ffff
id:    
multimedia
description:     Audio device
product:     Radeon HD 3870 Audio device
vendor:     ATI Technologies Inc
physical id:     
0.1
bus info:     
pci@0000:01:00.1
version:     00
width:     64 bits
clock:     33MHz
capabilities:     pm pciexpress msi bus_master cap_list
configuration:    
driver    =    HDA Intel
latency    =    0
resources:    
irq    :    49
memory    :    cfeec000-cfeeffff
id:    
usb:0
description:     USB Controller
product:     82801H (ICH8 Family) USB UHCI Controller #4
vendor:     Intel Corporation
physical id:     
1a
bus info:     
pci@0000:00:1a.0
version:     03
width:     32 bits
clock:     33MHz
capabilities:     uhci bus_master
configuration:    
driver    =    uhci_hcd
latency    =    0
resources:    
irq    :    16
ioport    :    1800(size=32)
id:    
usb:1
description:     USB Controller
product:     82801H (ICH8 Family) USB UHCI Controller #5
vendor:     Intel Corporation
physical id:     
1a.1
bus info:     
pci@0000:00:1a.1
version:     03
width:     32 bits
clock:     33MHz
capabilities:     uhci bus_master
configuration:    
driver    =    uhci_hcd
latency    =    0
resources:    
irq    :    21
ioport    :    1820(size=32)
id:    
usb:2
description:     USB Controller
product:     82801H (ICH8 Family) USB2 EHCI Controller #2
vendor:     Intel Corporation
physical id:     
1a.7
bus info:     
pci@0000:00:1a.7
version:     03
width:     32 bits
clock:     33MHz
capabilities:     pm debug ehci bus_master cap_list
configuration:    
driver    =    ehci_hcd
latency    =    0
resources:    
irq    :    18
memory    :    f0604800-f0604bff
id:    
multimedia
description:     Audio device
product:     82801H (ICH8 Family) HD Audio Controller
vendor:     Intel Corporation
physical id:     
1b
bus info:     
pci@0000:00:1b.0
version:     03
width:     64 bits
clock:     33MHz
capabilities:     pm msi pciexpress bus_master cap_list
configuration:    
driver    =    HDA Intel
latency    =    0
resources:    
irq    :    47
memory    :    f0600000-f0603fff
id:    
pci:1
description:     PCI bridge
product:     82801H (ICH8 Family) PCI Express Port 1
vendor:     Intel Corporation
physical id:     
1c
bus info:     
pci@0000:00:1c.0
version:     03
width:     32 bits
clock:     33MHz
capabilities:     pci pciexpress msi pm normal_decode bus_master cap_list
configuration:    
driver    =    pcieport
resources:    
irq    :    41
ioport    :    3000(size=4096)
memory    :    c0000000-c01fffff
ioport    :    c0200000(size=2097152)
id:    
pci:2
description:     PCI bridge
product:     82801H (ICH8 Family) PCI Express Port 3
vendor:     Intel Corporation
physical id:     
1c.2
bus info:     
pci@0000:00:1c.2
version:     03
width:     32 bits
clock:     33MHz
capabilities:     pci pciexpress msi pm normal_decode bus_master cap_list
configuration:    
driver    =    pcieport
resources:    
irq    :    42
ioport    :    4000(size=4096)
memory    :    c0400000-c05fffff
ioport    :    c0600000(size=2097152)
id:    
firewire
description:     FireWire (IEEE 1394)
product:     FW643 PCI Express1394b Controller (PHY/Link)
vendor:     Agere Systems
physical id:     
0
bus info:     
pci@0000:05:00.0
version:     06
width:     64 bits
clock:     33MHz
capabilities:     pm msi pciexpress ohci bus_master cap_list
configuration:    
driver    =    firewire_ohci
latency    =    0
resources:    
irq    :    18
memory    :    c0400000-c0400fff
id:    
pci:3
description:     PCI bridge
product:     82801H (ICH8 Family) PCI Express Port 4
vendor:     Intel Corporation
physical id:     
1c.3
bus info:     
pci@0000:00:1c.3
version:     03
width:     32 bits
clock:     33MHz
capabilities:     pci pciexpress msi pm normal_decode bus_master cap_list
configuration:    
driver    =    pcieport
resources:    
irq    :    43
ioport    :    5000(size=4096)
memory    :    c0800000-c09fffff
ioport    :    c0a00000(size=2097152)
id:    
network
description:     Wireless interface
product:     PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
vendor:     Intel Corporation
physical id:     
0
bus info:     
pci@0000:06:00.0
logical name:     
wlan0
version:     61
serial:     00:21:5c:8b:b4:2b
width:     64 bits
clock:     33MHz
capabilities:     pm msi pciexpress bus_master cap_list ethernet physical wireless
configuration:    
broadcast    =    yes
driver    =    iwlagn
driverversion    =    2.6.35-28-generic
firmware    =    228.61.2.24
ip    =    192.168.0.11
latency    =    0
link    =    yes
multicast    =    yes
wireless    =    IEEE 802.11abg
resources:    
irq    :    48
memory    :    c0800000-c0801fff
id:    
pci:4
description:     PCI bridge
product:     82801H (ICH8 Family) PCI Express Port 5
vendor:     Intel Corporation
physical id:     
1c.4
bus info:     
pci@0000:00:1c.4
version:     03
width:     32 bits
clock:     33MHz
capabilities:     pci pciexpress msi pm normal_decode bus_master cap_list
configuration:    
driver    =    pcieport
resources:    
irq    :    44
ioport    :    6000(size=4096)
memory    :    c0c00000-c0dfffff
ioport    :    c0e00000(size=2097152)
id:    
pci:5
description:     PCI bridge
product:     82801H (ICH8 Family) PCI Express Port 6
vendor:     Intel Corporation
physical id:     
1c.5
bus info:     
pci@0000:00:1c.5
version:     03
width:     32 bits
clock:     33MHz
capabilities:     pci pciexpress msi pm normal_decode bus_master cap_list
configuration:    
driver    =    pcieport
resources:    
irq    :    45
ioport    :    7000(size=4096)
memory    :    c1000000-c11fffff
ioport    :    c1200000(size=2097152)
id:    
network
description:     Ethernet interface
product:     NetLink BCM5787M Gigabit Ethernet PCI Express
vendor:     Broadcom Corporation
physical id:     
0
bus info:     
pci@0000:08:00.0
logical name:     
eth0
version:     02
serial:     00:1b:24:00:00:5f
capacity:     1GB/s
width:     64 bits
clock:     33MHz
capabilities:     pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
configuration:    
autonegotiation    =    on
broadcast    =    yes
driver    =    tg3
driverversion    =    3.110
firmware    =    5787m-v3.26
latency    =    0
link    =    no
multicast    =    yes
port    =    twisted pair
resources:    
irq    :    50
memory    :    c1000000-c100ffff
id:    
usb:3
description:     USB Controller
product:     82801H (ICH8 Family) USB UHCI Controller #1
vendor:     Intel Corporation
physical id:     
1d
bus info:     
pci@0000:00:1d.0
version:     03
width:     32 bits
clock:     33MHz
capabilities:     uhci bus_master
configuration:    
driver    =    uhci_hcd
latency    =    0
resources:    
irq    :    23
ioport    :    1840(size=32)
id:    
usb:4
description:     USB Controller
product:     82801H (ICH8 Family) USB UHCI Controller #2
vendor:     Intel Corporation
physical id:     
1d.1
bus info:     
pci@0000:00:1d.1
version:     03
width:     32 bits
clock:     33MHz
capabilities:     uhci bus_master
configuration:    
driver    =    uhci_hcd
latency    =    0
resources:    
irq    :    19
ioport    :    1860(size=32)
id:    
usb:5
description:     USB Controller
product:     82801H (ICH8 Family) USB UHCI Controller #3
vendor:     Intel Corporation
physical id:     
1d.2
bus info:     
pci@0000:00:1d.2
version:     03
width:     32 bits
clock:     33MHz
capabilities:     uhci bus_master
configuration:    
driver    =    uhci_hcd
latency    =    0
resources:    
irq    :    18
ioport    :    1880(size=32)
id:    
usb:6
description:     USB Controller
product:     82801H (ICH8 Family) USB2 EHCI Controller #1
vendor:     Intel Corporation
physical id:     
1d.7
bus info:     
pci@0000:00:1d.7
version:     03
width:     32 bits
clock:     33MHz
capabilities:     pm debug ehci bus_master cap_list
configuration:    
driver    =    ehci_hcd
latency    =    0
resources:    
irq    :    23
memory    :    f0604c00-f0604fff
id:    
pci:6
description:     PCI bridge
product:     82801 Mobile PCI Bridge
vendor:     Intel Corporation
physical id:     
1e
bus info:     
pci@0000:00:1e.0
version:     f3
width:     32 bits
clock:     33MHz
capabilities:     pci subtractive_decode bus_master cap_list
resources:    
memory    :    f0500000-f05fffff
id:    
generic:0
description:     SD Host controller
product:     R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
vendor:     Ricoh Co Ltd
physical id:     
9
bus info:     
pci@0000:0a:09.0
version:     22
width:     32 bits
clock:     33MHz
capabilities:     pm bus_master cap_list
configuration:    
driver    =    sdhci-pci
latency    =    32
resources:    
irq    :    17
memory    :    f0500800-f05008ff
id:    
generic:1
description:     System peripheral
product:     R5C843 MMC Host Controller
vendor:     Ricoh Co Ltd
physical id:     
9.1
bus info:     
pci@0000:0a:09.1
version:     12
width:     32 bits
clock:     33MHz
capabilities:     pm bus_master cap_list
configuration:    
driver    =    sdhci-pci
latency    =    32
resources:    
irq    :    17
memory    :    f0500c00-f0500cff
id:    
generic:2
description:     System peripheral
product:     R5C592 Memory Stick Bus Host Adapter
vendor:     Ricoh Co Ltd
physical id:     
9.2
bus info:     
pci@0000:0a:09.2
version:     12
width:     32 bits
clock:     33MHz
capabilities:     pm bus_master cap_list
configuration:    
latency    =    32
resources:    
memory    :    f0501000-f05010ff
id:    
generic:3
description:     System peripheral
product:     xD-Picture Card Controller
vendor:     Ricoh Co Ltd
physical id:     
9.3
bus info:     
pci@0000:0a:09.3
version:     12
width:     32 bits
clock:     33MHz
capabilities:     pm bus_master cap_list
configuration:    
driver    =    r852
latency    =    32
resources:    
irq    :    17
memory    :    f0501400-f05014ff
id:    
isa
description:     ISA bridge
product:     82801HEM (ICH8M) LPC Interface Controller
vendor:     Intel Corporation
physical id:     
1f
bus info:     
pci@0000:00:1f.0
version:     03
width:     32 bits
clock:     33MHz
capabilities:     isa bus_master cap_list
configuration:    
latency    =    0
id:    
ide
description:     IDE interface
product:     82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller
vendor:     Intel Corporation
physical id:     
1f.1
bus info:     
pci@0000:00:1f.1
logical name:     
scsi0
version:     03
width:     32 bits
clock:     33MHz
capabilities:     ide bus_master emulated
configuration:    
driver    =    ata_piix
latency    =    0
resources:    
irq    :    19
ioport    :    1f0(size=8)
ioport    :    3f6
ioport    :    170(size=8)
ioport    :    376
ioport    :    18a0(size=16)
id:    
cdrom
description:     DVD-RAM writer
product:     DVD RW AD-7590A
vendor:     Optiarc
physical id:     
0.0.0
bus info:     
scsi@0:0.0.0
logical name:     
/dev/cdrom
logical name:     
/dev/cdrw
logical name:     
/dev/dvd
logical name:     
/dev/dvdrw
logical name:     
/dev/scd0
logical name:     
/dev/sr0
logical name:     
/media/OFFICE12
version:     1.05
capabilities:     removable audio cd-r cd-rw dvd dvd-r dvd-ram
configuration:    
ansiversion    =    5
mount.fstype    =    udf
mount.options    =    ro,nosuid,nodev,relatime,uid=1000,gid=1000,umask=77,iocharset=utf8
state    =    mounted
status    =    ready
id:    
medium
physical id:     
0
logical name:     
/dev/cdrom
logical name:     
/media/OFFICE12
configuration:    
mount.fstype    =    udf
mount.options    =    ro,nosuid,nodev,relatime,uid=1000,gid=1000,umask=77,iocharset=utf8
state    =    mounted
id:    
storage
description:     SATA controller
product:     82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller
vendor:     Intel Corporation
physical id:     
1f.2
bus info:     
pci@0000:00:1f.2
logical name:     
scsi2
version:     03
width:     32 bits
clock:     66MHz
capabilities:     storage msi pm ahci_1.0 bus_master cap_list emulated
configuration:    
driver    =    ahci
latency    =    0
resources:    
irq    :    46
ioport    :    18d8(size=8)
ioport    :    18cc(size=4)
ioport    :    18d0(size=8)
ioport    :    18c8(size=4)
ioport    :    18e0(size=32)
memory    :    f0604000-f06047ff
id:    
disk
description:     ATA Disk
product:     ST9250421ASG
vendor:     Seagate
physical id:     
0.0.0
bus info:     
scsi@2:0.0.0
logical name:     
/dev/sda
version:     DE17
serial:     5TH0LGAQ
size:     232GiB (250GB)
capabilities:     partitioned partitioned:dos
configuration:    
ansiversion    =    5
signature    =    def690fa
id:    
volume:0
description:     Windows NTFS volume
physical id:     
1
bus info:     
scsi@2:0.0.0,1
logical name:     
/dev/sda1
version:     3.1
serial:     2cea5c76-e191-104a-8690-edff1724f5c2
size:     136GiB
capacity:     136GiB
capabilities:     primary bootable ntfs initialized
configuration:    
clustersize    =    4096
created    =    2011-02-02 02:40:15
filesystem    =    ntfs
modified_by_chkdsk    =    true
mounted_on_nt4    =    true
resize_log_file    =    true
state    =    dirty
upgrade_on_mount    =    true
id:    
volume:1
description:     Windows NTFS volume
physical id:     
2
bus info:     
scsi@2:0.0.0,2
logical name:     
/dev/sda2
version:     3.1
serial:     8282-9d1e
size:     12GiB
capacity:     12GiB
capabilities:     primary boot ntfs initialized
configuration:    
clustersize    =    4096
created    =    2010-07-19 13:04:53
filesystem    =    ntfs
label    =    Respawn Recovery
state    =    clean
id:    
volume:2
description:     Extended partition
physical id:     
3
bus info:     
scsi@2:0.0.0,3
logical name:     
/dev/sda3
size:     84GiB
capacity:     84GiB
capabilities:     primary extended partitioned partitioned:extended
id:    
logicalvolume:0
description:     Linux filesystem partition
physical id:     
5
logical name:     
/dev/sda5
logical name:     
/
capacity:     80GiB
configuration:    
mount.fstype    =    ext4
mount.options    =    rw,relatime,errors=remount-ro,barrier=1,data=ordered
state    =    mounted
id:    
logicalvolume:1
description:     Linux swap / Solaris partition
physical id:     
6
logical name:     
/dev/sda6
capacity:     3556MiB
capabilities:     nofs
id:    
serial
description:     SMBus
product:     82801H (ICH8 Family) SMBus Controller
vendor:     Intel Corporation
physical id:     
1f.3
bus info:     
pci@0000:00:1f.3
version:     03
width:     32 bits
clock:     33MHz
configuration:    
latency    =    0
resources:    
memory    :    c1400000-c14000ff
ioport    :    1c00(size=32)
id:    
battery
description:     Lithium Ion Battery
product:     Intel Corporation
vendor:     Intel Corporation
physical id:     
1
slot:     Rear
capacity:     1000mWh
configuration:    
voltage    =    0.0V
id:    
remoteaccess
vendor:     Intel
physical id:     
2
capabilities:     inbound


```
     
   
*p.s. one thing that does bug me is that there are two multimedia (sound) controllers found and they are both saying 64bits (while the pc is in 32bits). IDK if that is normal or if something needs to be modified.

---

### Post by lidex on 2011-04-18
Could you please edit that post and put your alsa-info text into code tags? Just highlight the text and click the # in the editing toolbar. Now for your problem. What are these terminal outputs:
```
cat /etc/modprobe.d/alsa-base.conf
```
```
ls /etc/modprobe.d/
```

---

### Post by elflako17 on 2011-04-18
ok my problem is i got no sound at all and my friend joedoe47 gave me some code to run in terminal and i got what i posted on my first post can you please help me i need my sound

---

### Post by lidex on 2011-04-18
See my previous post.

---

### Post by elflako17 on 2011-04-18
[COLOR=Red]**cat /etc/modprobe.d/alsa-base.conf**[/COLOR]



flako@flako-m15x:~$ cat /etc/modprobe.d/alsa-base.conf
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
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
options snd-hda-intel model=generic
flako@flako-m15x:~$ 

__________________________________________________________________________________________________

**[COLOR=Red]ls /etc/modprobe.d/[/COLOR]**

flako@flako-m15x:~$ [COLOR=Red]ls /etc/modprobe.d/[/COLOR]
alsa-base.conf              blacklist-modem.conf
alsa-base.save              blacklist-oss.conf
blacklist-ath_pci.conf      blacklist-watchdog.conf
blacklist.conf              fglrx.conf
blacklist-firewire.conf     intel-5300-iwlagn-disable11n.conf
blacklist-framebuffer.conf
flako@flako-m15x:~$

---

### Post by lidex on 2011-04-18
I want you to remove the alsa-base.save file as it's still getting read.
```
cd /etc/modprobe.d/
```
```
sudo rm alsa-base.save
```

Now edit alsa-base.conf:
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```
Add this at the bottom:
```
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=lenovo-101e
```
Save. Close. Reboot.

---

### Post by elflako17 on 2011-04-18
ok i did what u said and this came up 

_____________________________________________________________________________________________________

flako@flako-m15x:~$ sudo rm alsa-base.save
[sudo] password for flako: 
rm: cannot remove `alsa-base.save': No such file or directory
flako@flako-m15x:~$ 

then i did the rest and i rebooted and nothing still

---

### Post by lidex on 2011-04-18
> **elflako17 said:**
> ok i did what u said and this came up 

_____________________________________________________________________________________________________

flako@flako-m15x:~$ sudo rm alsa-base.save
[sudo] password for flako: 
rm: cannot remove `alsa-base.save': No such file or directory
flako@flako-m15x:~$ 

then i did the rest and i rebooted and nothing still

You need to **c**hange **d**irectories first to get that file,ie:
```
cd /etc/modprobe.d/
```
Then remove:
```
sudo rm alsa-base.save
```

---

### Post by elflako17 on 2011-04-18
ok i did that i think and this came up

[B][COLOR=Blue]_____________________________________________________________________________________________________

[/COLOR][COLOR=Blue]
[COLOR=Black]flako@flako-m15x:~$ cd /etc/modprobe.d/
flako@flako-m15x:/etc/modprobe.d$ sudo rm alsa-base.save
[sudo] password for flako: 
flako@flako-m15x:/etc/modprobe.d$ sudo rm alsa-base.save
rm: cannot remove `alsa-base.save': No such file or directory
flako@flako-m15x:/etc/modprobe.d$[/COLOR][/COLOR][/B]

---

### Post by lidex on 2011-04-18
Run this again:
```
ls /etc/modprobe.d/
```

OK - I missed something. Re-open alsa-base.conf and remove this line:
```
options snd-hda-intel model=generic
```

Save and reboot.

---

### Post by elflako17 on 2011-04-18
here you go 

_____________________________________________________________________________________________

flako@flako-m15x:~$ ls /etc/modprobe.d/
alsa-base.conf              blacklist-modem.conf
blacklist-ath_pci.conf      blacklist-oss.conf
blacklist.conf              blacklist-watchdog.conf
blacklist-firewire.conf     fglrx.conf
blacklist-framebuffer.conf  intel-5300-iwlagn-disable11n.conf
flako@flako-m15x:~$



AND I DID THE SECOND PART NOW AM GOING TO REBOOT LEST SEE IF THERES SOUND

---

### Post by lidex on 2011-04-18
> **elflako17 said:**
> here you go

_____________________________________________________________________________________________

flako@flako-m15x:~$ ls /etc/modprobe.d/
alsa-base.conf              blacklist-modem.conf
blacklist-ath_pci.conf      blacklist-oss.conf
blacklist.conf              blacklist-watchdog.conf
blacklist-firewire.conf     fglrx.conf
blacklist-framebuffer.conf  intel-5300-iwlagn-disable11n.conf
flako@flako-m15x:~$

You must have gotten it the first time, it's definitely gone.
Check my last post - I edited it.

---

### Post by elflako17 on 2011-04-18
lidex you should get an :KSaward:KS bro like am listening to music now thanks to you i appreciate your time and i guess you guys could mark this one as SOLVED =] :lolflag:

---

### Post by lidex on 2011-04-18
> **elflako17 said:**
> lidex you should get an :KSaward:KS bro like am listening to music now thanks to you i appreciate your time and i guess you guys could mark this one as SOLVED =] :lolflag:

Sweet. You have to mark it - use the "Thread Tools" up top.

---

### Post by elflako17 on 2011-04-18
i just did thank u lidex =]

---

