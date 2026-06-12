---
title: "ubuntu 10.10 live CD sound problem"
date: 2010-11-12
forum: Multimedia Software
---

### Post by camarathe on 2010-11-12
Hi,

Ubuntu 10.10 live CD does not play sound on my machine. Though, it seems to detect the audio card correctly. I can see the device detected in lsmod, lspci , aplay -l etc. Also see all the audio controls, but there is no sound!

The details are :

1. Gigabyte M68 MTD3 motherboard - AMD Athlon-II 245 processor,  Nvidia GeForce7025/ nForce 630a chipset. As per Nvidia webpage, snd-hda-intel driver should support nForce 430 or above chipset.

2. Output of also-config.sh is here:
[http://www.alsa-project.org/db/?f=71bd6ed25da3559989d381eee282c6b722c8bbde](http://www.alsa-project.org/db/?f=71bd6ed25da3559989d381eee282c6b722c8bbde)
(Copying at the end of thread)

3. Ethernet  / Display all work perfectly - its just the sound.

There are other threads noting problems with Gigabyte motherboard - leads me to suspect that my sound card is not yet supported on Linux. I have tried Fedora 14 and PCLinuxOS10 live CDs as well but same results.

Regards,
Shekhar

!!!################################
!!ALSA Information Script v 0.4.59
!!################################

!!Script ran on: Thu Nov 11 17:51:34 UTC 2010


!!Linux Distribution
!!------------------

Ubuntu 10.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.10"


!!DMI Information
!!---------------

Manufacturer:      Gigabyte Technology Co., Ltd.
Product Name:      M68MT-D3


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

 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfe024000 irq 21


!!PCI Soundcards installed in the system
!!--------------------------------------

00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:05.0 0403: 10de:03f0 (rev a2)
    Subsystem: 1458:a002


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
snd-hda-intel: model=5stack


!!Loaded sound module options
!!--------------------------

!!Module: snd_hda_intel
    bdl_pos_adj : 32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    beep_mode : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
    enable_msi : -1
    id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    model : 5stack,(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
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

Codec: Realtek ALC887
Address: 0
Function Id: 0x1
Vendor Id: 0x10ec0887
Subsystem Id: 0x1458a002
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
  Device: name="ALC887 Analog", type="Audio", device=0
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x40 0x40]
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x03 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x40 0x40]
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x04 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x40 0x40]
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x05 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x40 0x40]
  Converter: stream=0, channel=0
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
  Device: name="ALC887 Digital", type="SPDIF", device=1
  Converter: stream=0, channel=0
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
  Device: name="ALC887 Analog", type="Audio", device=0
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
     0x23
Node 0x09 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Control: name="Capture Switch", index=1, device=0
  Control: name="Capture Volume", index=1, device=0
  Device: name="ALC887 Analog", type="Audio", device=2
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
  Device: name="ALC887 Digital", type="SPDIF", device=1
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
  Amp-In vals:  [0x80 0x80] [0x80 0x80]
  Connection: 2
     0x02 0x0b
Node 0x0d [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Surround Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80]
  Connection: 2
     0x03 0x0b
Node 0x0e [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Center Playback Volume", index=0, device=0
    ControlAmp: chs=1, dir=Out, idx=0, ofs=0
  Control: name="LFE Playback Volume", index=0, device=0
    ControlAmp: chs=2, dir=Out, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80]
  Connection: 2
     0x04 0x0b
Node 0x0f [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Side Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80]
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
  Pincap 0x00000014: OUT Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
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
  Pincap 0x0000003e: IN OUT HP Detect Trigger
  Pin Default 0x01014410: [Jack] Line Out at Ext Rear
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
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
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
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
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
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x0f
Node 0x18 [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Control: name="Mic Boost", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00003736: IN OUT Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x01a19c40: [Jack] Mic at Ext Rear
    Conn = 1/8, Color = Pink
    DefAssociation = 0x4, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x19 [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Control: name="Front Mic Boost", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000373e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x02a19c50: [Jack] Mic at Ext Front
    Conn = 1/8, Color = Pink
    DefAssociation = 0x5, Sequence = 0x0
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
  Pin Default 0x0181344f: [Jack] Line In at Ext Rear
    Conn = 1/8, Color = Blue
    DefAssociation = 0x4, Sequence = 0xf
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
  Pincap 0x0000373e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
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
  Pin Default 0x593301f0: [N/A] CD at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x1d [Pin Complex] wcaps 0x400400: Mono
  Pincap 0x00000020: IN
  Pin Default 0x4005c603: [N/A] Line Out at Ext N/A
    Conn = Optical, Color = UNKNOWN
    DefAssociation = 0x0, Sequence = 0x3
  Pin-ctls: 0x20: IN
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x1e [Pin Complex] wcaps 0x400781: Stereo Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x014b6130: [Jack] SPDIF Out at Ext Rear
    Conn = Comb, Color = Orange
    DefAssociation = 0x3, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x06
Node 0x1f [Pin Complex] wcaps 0x400681: Stereo Digital
  Pincap 0x00000024: IN Detect
  Pin Default 0x01cb7160: [Jack] SPDIF In at Ext Rear
    Conn = Comb, Color = Yellow
    DefAssociation = 0x6, Sequence = 0x0
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
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
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

crw-rw----  1 root audio 116,  9 Nov 11 17:48 /dev/snd/controlC0
crw-rw----  1 root audio 116,  8 Nov 11 17:48 /dev/snd/hwC0D0
crw-rw----  1 root audio 116,  7 Nov 11 17:48 /dev/snd/pcmC0D0c
crw-rw----  1 root audio 116,  6 Nov 11 17:48 /dev/snd/pcmC0D0p
crw-rw----  1 root audio 116,  5 Nov 11 17:48 /dev/snd/pcmC0D1c
crw-rw----  1 root audio 116,  4 Nov 11 17:48 /dev/snd/pcmC0D1p
crw-rw----  1 root audio 116,  3 Nov 11 17:48 /dev/snd/pcmC0D2c
crw-rw----  1 root audio 116, 10 Nov 11 17:48 /dev/snd/seq
crw-rw----  1 root audio 116,  2 Nov 11  2010 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Nov 11 17:48 .
drwxr-xr-x 3 root root 240 Nov 11 17:48 ..
lrwxrwxrwx 1 root root  12 Nov 11 17:48 pci-0000:00:05.0 -> ../controlC0


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC887 Analog [ALC887 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC887 Digital [ALC887 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC887 Analog [ALC887 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC887 Digital [ALC887 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 2: ALC887 Analog [ALC887 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [NVidia]

amixer: Mixer load hw:0 error: Invalid argument
Card hw:0 'NVidia'/'HDA NVidia at 0xfe024000 irq 21'
  Mixer name    : 'Realtek ALC887'
  Components    : 'HDA:10ec0887,1458a002,00100302'
  Controls      : 38
amixer: Mixer hw:0 load error: Invalid argument


!!Alsactl output
!!-------------

--startcollapse--
--endcollapse--


!!All Loaded Modules
!!------------------

Module
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
snd_seq
snd_seq_device
snd_hda_intel
binfmt_misc
dm_crypt
lp
snd_hda_codec_realtek
snd_hda_codec
snd_hwdep
snd_pcm
ppdev
snd_timer
snd
parport_pc
parport
soundcore
snd_page_alloc
k10temp
i2c_nforce2
squashfs
aufs
nls_cp437
isofs
dm_raid45
xor
btrfs
zlib_deflate
crc32c
libcrc32c
nouveau
ttm
drm_kms_helper
drm
usbhid
hid
forcedeth
agpgart
i2c_algo_bit
sata_nv
pata_amd


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x11 0x411111f0
0x12 0x411111f0
0x14 0x01014410
0x15 0x411111f0
0x16 0x411111f0
0x17 0x411111f0
0x18 0x01a19c40
0x19 0x02a19c50
0x1a 0x0181344f
0x1b 0x02214c20
0x1c 0x593301f0
0x1d 0x4005c603
0x1e 0x014b6130
0x1f 0x01cb7160

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:


!!ALSA/HDA dmesg
!!------------------

[   67.090282] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 21
[   67.090287] HDA Intel 0000:00:05.0: PCI INT B -> Link[AAZA] -> GSI 21 (level, low) -> IRQ 21
[   67.090289] hda_intel: Disable MSI for Nvidia chipset
[   67.090308] HDA Intel 0000:00:05.0: setting latency timer to 64
[   67.529619]   alloc irq_desc for 40 on node -1
--
[   68.644898] lp0: using parport0 (interrupt-driven).
[   77.656039] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   77.876322] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   77.888310] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   78.136297] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   78.148313] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   78.160278] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   78.172314] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   78.184278] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   78.196314] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   78.208278] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   78.220312] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   78.232278] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   78.244313] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   78.256278] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   78.268314] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   78.280280] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   78.292067] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   78.304066] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   78.316063] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   78.328079] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   78.340064] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   78.352066] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   78.364079] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   78.376062] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   78.388037] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   78.400283] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   78.556299] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   78.568312] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   78.580278] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   78.592314] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   78.604278] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   78.616314] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   78.628050] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   78.640064] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   78.816299] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   78.828313] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   78.940029] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   78.952063] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   79.108270] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   79.188274] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   79.228020] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   79.244406] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   79.300634] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   79.664749] [drm] nouveau 0000:00:0d.0: Allocating FIFO number 1
[   79.664967] [drm] nouveau 0000:00:0d.0: nouveau_channel_alloc: initialised FIFO 1
[  111.656033] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[  111.696282] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[  143.833324] [drm] nouveau 0000:00:0d.0: nouveau_channel_free: freeing fifo 1
--
[  188.875831] eth0: link up.
[  737.756301] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[  737.776064] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[  737.952310] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[  882.920279] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[  897.596281] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[ 1024.608078] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[ 1024.628309] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[ 1024.668075] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[ 1579.933388] HDA Intel 0000:00:05.0: PCI INT B disabled
[ 1580.054224] HDA Intel 0000:00:05.0: PCI INT B -> Link[AAZA] -> GSI 21 (level, low) -> IRQ 21
[ 1580.054228] hda_intel: Disable MSI for Nvidia chipset
[ 1580.054271] HDA Intel 0000:00:05.0: setting latency timer to 64
[ 1580.980033] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[ 1580.992081] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[ 1581.080053] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[ 1581.104282] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[ 1581.128320] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[ 1581.208302] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[ 1581.236059] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[ 1581.260323] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[ 1581.340302] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[ 1581.368064] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[ 1581.460036] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[ 1581.484072] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[ 1581.508304] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[ 1581.588318] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[ 1581.616053] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[ 1581.640303] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[ 1581.664318] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[ 1581.696321] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[ 1581.724056] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[ 1581.748303] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[ 1581.772355] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[ 1581.804320] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[ 1581.832064] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[ 1581.852065] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[ 1581.872039] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[ 1581.884085] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[ 1581.896069] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[ 1581.908074] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[ 1581.920069] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[ 1581.932073] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[ 1581.944069] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[ 1581.956070] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[ 1581.968075] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[ 1581.980069] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[ 1581.992074] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[ 1582.004069] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[ 1582.016081] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[ 1582.028068] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[ 1582.040068] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[ 1582.052075] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[ 1582.064067] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[ 1582.076075] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[ 1582.088067] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[ 1752.708368] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[ 1752.728060] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[ 1752.768297] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)

---

