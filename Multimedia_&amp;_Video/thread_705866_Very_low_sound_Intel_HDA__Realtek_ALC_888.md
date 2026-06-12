---
title: "Very low sound Intel HDA / Realtek ALC 888"
date: 2008-02-23
forum: Multimedia &amp; Video
---

### Post by garolou on 2008-02-23
Hi everyone,

After spending two days searching and trying, I can't get a good sound level out of the speakers. Let me explain...

**Problem:**
If I plug my 2 channel speakers in any of the 'out' jacks on the rear panel, the sound is very low even though the volume control is maxed out for any channel.

**Observations:**
If i plug those same speakers in the front chassis headphone jack the sound is at the level expected.

**My system:**
MOBO: ASROCK CONROE1333-D667 R1.0
CPU: INTEL CELERON 430 1.80GHz FSB800MHz 512KB 
Memory:	1Gb (2x DDR2 512M 533MHz PC2-4200 Major)
Audio: Onboard Intel HDA (ICH7) / Realtek ALC888...
Realtek's blurb:
> The ALC888 series are high-performance 7.1+2 Channel High Definition Audio Codecs providing ten DAC channels that simultaneously support 7.1 sound playback, plus 2 channels of independent stereo sound output (multiple streaming) through the front panel stereo outputs.

Ubuntu 2.6.22-14.52-server  x86_64 GNU/Linux
I have compiled and installed the latest alsa package (1.0.16)
more detailed info below...

**Questions:**
1) Do I need a speaker system with built in amplifiers to deal with modern sound cards or should my cheap 10year old small speakers still work?
2) Is it normal that when one plugs-in the headphones in the front chassis panel jack, that the rear chassis panel connected speakers still stay enabled?
3) Can someone more experienced in the subject of Linux & sound controllers verify my data and point me in possible direction of a solution?


As previously mentionned, I have installed the latest alsa drivers (more than once). All channels are max (not muted). Ran alsaconfig too many times.
Followed the suggestions from [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) and many of the other postings on this forum and others. It seems that the new alsa drivers help most but not me. Maybe my system is too new???.
The following should answer most questions regarding my configuration. I have also included below the output of lspci and dmesg. I want to get your opinion before I open a bug report. Maybe I screwed-up somewhere and I just can't see it.

Thanks for looking and helping out.
Dave
:-)

result of alsa-info.sh script:
```

!!################################
!!ALSA Information Script v 0.4.37
!!################################

!!Script ran on: Sat Feb 23 21:33:48 AST 2008


!!Linux Distribution
!!------------------

Ubuntu 7.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 7.10"


!!Kernel Information
!!------------------

Kernel release:    2.6.22-14-server
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.16
Library version:    1.0.16
Utilities version:  1.0.16


!!Loaded ALSA modules
!!-------------------

snd_hda_intel


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfea38000 irq 16


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:27d8 (rev 01)
	Subsystem: 1849:0888


!!Modprobe options (Sound related)
!!--------------------------------

snd-bt87x: index=-2
snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-usx2y: index=-2
snd-usb-caiaq: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-hda-intel: model=6stack-dig


!!Loaded sound module options
!!--------------------------

!!Module: snd_hda_intel
enable : Y,Y,Y,Y,Y,Y,Y,Y
enable_msi : 0
id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
index : -1,-1,-1,-1,-1,-1,-1,-1
model : 6stack-dig,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
position_fix : 0,0,0,0,0,0,0,0
power_save : 0
power_save_controller : Y
probe_mask : -1,-1,-1,-1,-1,-1,-1,-1
single_cmd : N


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: Realtek ALC888
Address: 0
Vendor Id: 0x10ec0888
Subsystem Id: 0x18491e01
Revision Id: 0x100001
No Modem Function Group found
Default PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=3, o=0, i=0, unsolicited=1, wake=0
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0
  IO[2]: enable=0, dir=0, wake=0, sticky=0, data=0
Node 0x02 [Audio Output] wcaps 0x11: Stereo
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
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0x1e]: 16 20 24 32
    formats [0x1]: PCM
Node 0x07 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x08 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Amp-In caps: ofs=0x0b, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x1f 0x1f]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0x6]: 16 20
    formats [0x1]: PCM
  Connection: 1
     0x23
Node 0x09 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Amp-In caps: ofs=0x0b, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x1e 0x1e]
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
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x80 0x80] [0x8b 0x8b] [0x80 0x80] [0x80 0x80] [0x8f 0x8f] [0x1f 0x1f] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 10
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17
Node 0x0c [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x1f 0x1f]
  Connection: 2
     0x02 0x0b
Node 0x0d [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x1f 0x1f]
  Connection: 2
     0x03 0x0b
Node 0x0e [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x1f 0x1f]
  Connection: 2
     0x04 0x0b
Node 0x0f [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x1f 0x1f]
  Connection: 2
     0x05 0x0b
Node 0x10 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x11 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x12 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x13 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x14 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x083e: IN OUT HP Detect Trigger
  Pin Default 0x01014010: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Green
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x15 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x083e: IN OUT HP Detect Trigger
  Pin Default 0x01011012: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0x1, Sequence = 0x2
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c 0x0d* 0x0e 0x0f 0x26
Node 0x16 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0836: IN OUT Detect Trigger
  Pin Default 0x01016011: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Orange
    DefAssociation = 0x1, Sequence = 0x1
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c 0x0d 0x0e* 0x0f 0x26
Node 0x17 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0836: IN OUT Detect Trigger
  Pin Default 0x01012014: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Grey
    DefAssociation = 0x1, Sequence = 0x4
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c 0x0d 0x0e 0x0f* 0x26
Node 0x18 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x08373e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x01a19830: [Jack] Mic at Ext Rear
    Conn = 1/8, Color = Pink
    DefAssociation = 0x3, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x19 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x08373e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x02a19840: [Jack] Mic at Ext Front
    Conn = 1/8, Color = Pink
    DefAssociation = 0x4, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1a [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x08373e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x0181303f: [Jack] Line In at Ext Rear
    Conn = 1/8, Color = Blue
    DefAssociation = 0x3, Sequence = 0xf
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1b [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x08373e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x02214020: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Green
    DefAssociation = 0x2, Sequence = 0x0
  Pin-ctls: 0xc0: OUT HP VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1c [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x0820: IN
  Pin Default 0x59330100: [N/A] CD at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0x0, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
Node 0x1d [Pin Complex] wcaps 0x400000: Mono
  Pincap 0x0820: IN
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
Node 0x1e [Pin Complex] wcaps 0x400300: Mono Digital
  Pincap 0x0810: OUT
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x06
Node 0x1f [Pin Complex] wcaps 0x400200: Mono Digital
  Pincap 0x0820: IN
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
Node 0x20 [Vendor Defined Widget] wcaps 0xf00040: Mono
  Processing caps: benign=0, ncoeff=17
Node 0x21 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x22 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x80 0x80] [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 11
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b
Node 0x23 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x80 0x80] [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
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
  Amp-In vals:  [0x00 0x00] [0x80 0x80]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 2
     0x25 0x0b
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw---- 1 root audio 116,  0 2008-02-23 21:28 /dev/snd/controlC0
crw-rw---- 1 root audio 116,  4 2008-02-23 21:28 /dev/snd/hwC0D0
crw-rw---- 1 root audio 116, 24 2008-02-23 21:28 /dev/snd/pcmC0D0c
crw-rw---- 1 root audio 116, 16 2008-02-23 21:28 /dev/snd/pcmC0D0p
crw-rw---- 1 root audio 116, 25 2008-02-23 21:28 /dev/snd/pcmC0D1c
crw-rw---- 1 root audio 116, 17 2008-02-23 21:28 /dev/snd/pcmC0D1p
crw-rw---- 1 root audio 116, 26 2008-02-23 21:28 /dev/snd/pcmC0D2c
crw-rw---- 1 root audio 116,  1 2008-02-23 21:28 /dev/snd/seq
crw-rw---- 1 root audio 116, 33 2008-02-23 21:28 /dev/snd/timer


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 2: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [Intel]

Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pswitch
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [on]
  Front Right: Playback [on]
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
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Front Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 11 [35%] [-18.00dB] [off]
  Front Right: Playback 11 [35%] [-18.00dB] [off]
Simple mixer control 'Front Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%]
  Front Right: 0 [0%]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Side',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 15 [48%] [-12.00dB] [off]
  Front Right: Playback 15 [48%] [-12.00dB] [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%]
  Front Right: 0 [0%]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined cswitch cswitch-joined
  Playback channels: Mono
  Capture channels: Mono
  Mono: Playback [off] Capture [off]
Simple mixer control 'PC Speaker',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [12.00dB] [on]
  Front Right: Playback 31 [100%] [12.00dB] [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 31 [100%] [30.00dB] [on]
  Front Right: Capture 31 [100%] [30.00dB] [on]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 30 [97%] [28.50dB] [on]
  Front Right: Capture 30 [97%] [28.50dB] [on]
Simple mixer control 'Channel Mode',0
  Capabilities: enum
  Items: '6ch' '8ch'
  Item0: '6ch'
Simple mixer control 'Digital',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 120
  Front Left: Capture 116 [97%] [28.00dB]
  Front Right: Capture 116 [97%] [28.00dB]
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Mic' 'Front Mic' 'Line' 'CD'
  Item0: 'Mic'
Simple mixer control 'Input Source',1
  Capabilities: cenum
  Items: 'Mic' 'Front Mic' 'Line' 'CD'
  Item0: 'Mic'


!!Alsactl output
!!-------------

--startcollapse--
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
		name 'CD Playback Volume'
		value.0 15
		value.1 15
	}
	control.13 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'CD Playback Switch'
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
		name 'Line Playback Volume'
		value.0 0
		value.1 0
	}
	control.15 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Line Playback Switch'
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
		name 'Mic Playback Volume'
		value.0 0
		value.1 0
	}
	control.17 {
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
	control.18 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Mic Playback Switch'
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
		name 'Front Mic Playback Volume'
		value.0 11
		value.1 11
	}
	control.20 {
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
	control.21 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Front Mic Playback Switch'
		value.0 false
		value.1 false
	}
	control.22 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'PC Speaker Playback Volume'
		value.0 31
		value.1 31
	}
	control.23 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'PC Speaker Playback Switch'
		value.0 true
		value.1 true
	}
	control.24 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -1650
		comment.dbmax 3000
		iface MIXER
		name 'Capture Volume'
		value.0 31
		value.1 31
	}
	control.25 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Capture Switch'
		value.0 true
		value.1 true
	}
	control.26 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -1650
		comment.dbmax 3000
		iface MIXER
		name 'Capture Volume'
		index 1
		value.0 30
		value.1 30
	}
	control.27 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Capture Switch'
		index 1
		value.0 true
		value.1 true
	}
	control.28 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Mic
		comment.item.1 'Front Mic'
		comment.item.2 Line
		comment.item.3 CD
		iface MIXER
		name 'Input Source'
		value Mic
	}
	control.29 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Mic
		comment.item.1 'Front Mic'
		comment.item.2 Line
		comment.item.3 CD
		iface MIXER
		name 'Input Source'
		index 1
		value Mic
	}
	control.30 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 '6ch'
		comment.item.1 '8ch'
		iface MIXER
		name 'Channel Mode'
		value '6ch'
	}
	control.31 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Con Mask'
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.32 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.33 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Default'
		value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.34 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Switch'
		value false
	}
	control.35 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Capture Switch'
		value false
	}
	control.36 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Capture Default'
		value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.37 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 31'
		comment.dbmin -4650
		comment.dbmax 0
		iface MIXER
		name 'Master Playback Volume'
		value 31
	}
	control.38 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Master Playback Switch'
		value true
	}
	control.39 {
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
	control.40 {
		comment.access 'read write user'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 120'
		comment.tlv '0000000100000008fffff44800000032'
		comment.dbmin -3000
		comment.dbmax 3000
		iface MIXER
		name 'Digital Capture Volume'
		value.0 116
		value.1 116
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
i915
drm
ppdev
cpufreq_conservative
cpufreq_userspace
cpufreq_powersave
cpufreq_stats
cpufreq_ondemand
freq_table
sbs
container
video
dock
ac
button
battery
ipv6
lp
loop
snd_hda_intel
snd_pcm_oss
snd_mixer_oss
snd_pcm
snd_page_alloc
snd_hwdep
snd_seq_oss
irtty_sir
sir_dev
xpad
snd_seq_midi_event
snd_seq
snd_timer
snd_seq_device
irda
parport_pc
parport
psmouse
iTCO_wdt
iTCO_vendor_support
crc_ccitt
serio_raw
pcspkr
snd
shpchp
pci_hotplug
intel_agp
soundcore
af_packet
evdev
ext3
jbd
mbcache
usbhid
hid
sg
sr_mod
cdrom
sd_mod
ata_piix
ata_generic
libata
scsi_mod
r8169
ehci_hcd
uhci_hcd
usbcore
dm_mirror
dm_snapshot
dm_mod
thermal
processor
fan
fuse
apparmor
commoncap


!!ALSA Device nodes
!!-----------------

crw-rw---- 1 root audio 116,  0 2008-02-23 21:28 /dev/snd/controlC0
crw-rw---- 1 root audio 116,  4 2008-02-23 21:28 /dev/snd/hwC0D0
crw-rw---- 1 root audio 116, 24 2008-02-23 21:28 /dev/snd/pcmC0D0c
crw-rw---- 1 root audio 116, 16 2008-02-23 21:28 /dev/snd/pcmC0D0p
crw-rw---- 1 root audio 116, 25 2008-02-23 21:28 /dev/snd/pcmC0D1c
crw-rw---- 1 root audio 116, 17 2008-02-23 21:28 /dev/snd/pcmC0D1p
crw-rw---- 1 root audio 116, 26 2008-02-23 21:28 /dev/snd/pcmC0D2c
crw-rw---- 1 root audio 116,  1 2008-02-23 21:28 /dev/snd/seq
crw-rw---- 1 root audio 116, 33 2008-02-23 21:28 /dev/snd/timer


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 2: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [Intel]

Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pswitch
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [on]
  Front Right: Playback [on]
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
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Front Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 11 [35%] [-18.00dB] [off]
  Front Right: Playback 11 [35%] [-18.00dB] [off]
Simple mixer control 'Front Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%]
  Front Right: 0 [0%]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Side',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 15 [48%] [-12.00dB] [off]
  Front Right: Playback 15 [48%] [-12.00dB] [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%]
  Front Right: 0 [0%]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined cswitch cswitch-joined
  Playback channels: Mono
  Capture channels: Mono
  Mono: Playback [off] Capture [off]
Simple mixer control 'PC Speaker',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [12.00dB] [on]
  Front Right: Playback 31 [100%] [12.00dB] [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 31 [100%] [30.00dB] [on]
  Front Right: Capture 31 [100%] [30.00dB] [on]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 30 [97%] [28.50dB] [on]
  Front Right: Capture 30 [97%] [28.50dB] [on]
Simple mixer control 'Channel Mode',0
  Capabilities: enum
  Items: '6ch' '8ch'
  Item0: '6ch'
Simple mixer control 'Digital',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 120
  Front Left: Capture 116 [97%] [28.00dB]
  Front Right: Capture 116 [97%] [28.00dB]
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Mic' 'Front Mic' 'Line' 'CD'
  Item0: 'Mic'
Simple mixer control 'Input Source',1
  Capabilities: cenum
  Items: 'Mic' 'Front Mic' 'Line' 'CD'
  Item0: 'Mic'


!!Alsactl output
!!-------------

--startcollapse--
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
		name 'CD Playback Volume'
		value.0 15
		value.1 15
	}
	control.13 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'CD Playback Switch'
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
		name 'Line Playback Volume'
		value.0 0
		value.1 0
	}
	control.15 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Line Playback Switch'
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
		name 'Mic Playback Volume'
		value.0 0
		value.1 0
	}
	control.17 {
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
	control.18 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Mic Playback Switch'
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
		name 'Front Mic Playback Volume'
		value.0 11
		value.1 11
	}
	control.20 {
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
	control.21 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Front Mic Playback Switch'
		value.0 false
		value.1 false
	}
	control.22 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'PC Speaker Playback Volume'
		value.0 31
		value.1 31
	}
	control.23 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'PC Speaker Playback Switch'
		value.0 true
		value.1 true
	}
	control.24 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -1650
		comment.dbmax 3000
		iface MIXER
		name 'Capture Volume'
		value.0 31
		value.1 31
	}
	control.25 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Capture Switch'
		value.0 true
		value.1 true
	}
	control.26 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -1650
		comment.dbmax 3000
		iface MIXER
		name 'Capture Volume'
		index 1
		value.0 30
		value.1 30
	}
	control.27 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Capture Switch'
		index 1
		value.0 true
		value.1 true
	}
	control.28 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Mic
		comment.item.1 'Front Mic'
		comment.item.2 Line
		comment.item.3 CD
		iface MIXER
		name 'Input Source'
		value Mic
	}
	control.29 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Mic
		comment.item.1 'Front Mic'
		comment.item.2 Line
		comment.item.3 CD
		iface MIXER
		name 'Input Source'
		index 1
		value Mic
	}
	control.30 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 '6ch'
		comment.item.1 '8ch'
		iface MIXER
		name 'Channel Mode'
		value '6ch'
	}
	control.31 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Con Mask'
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.32 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.33 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Default'
		value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.34 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Switch'
		value false
	}
	control.35 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Capture Switch'
		value false
	}
	control.36 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Capture Default'
		value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.37 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 31'
		comment.dbmin -4650
		comment.dbmax 0
		iface MIXER
		name 'Master Playback Volume'
		value 31
	}
	control.38 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Master Playback Switch'
		value true
	}
	control.39 {
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
	control.40 {
		comment.access 'read write user'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 120'
		comment.tlv '0000000100000008fffff44800000032'
		comment.dbmin -3000
		comment.dbmax 3000
		iface MIXER
		name 'Digital Capture Volume'
		value.0 116
		value.1 116
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
i915
drm
ppdev
cpufreq_conservative
cpufreq_userspace
cpufreq_powersave
cpufreq_stats
cpufreq_ondemand
freq_table
sbs
container
video
dock
ac
button
battery
ipv6
lp
loop
snd_hda_intel
snd_pcm_oss
snd_mixer_oss
snd_pcm
snd_page_alloc
snd_hwdep
snd_seq_oss
irtty_sir
sir_dev
xpad
snd_seq_midi_event
snd_seq
snd_timer
snd_seq_device
irda
parport_pc
parport
psmouse
iTCO_wdt
iTCO_vendor_support
crc_ccitt
serio_raw
pcspkr
snd
shpchp
pci_hotplug
intel_agp
soundcore
af_packet
evdev
ext3
jbd
mbcache
usbhid
hid
sg
sr_mod
cdrom
sd_mod
ata_piix
ata_generic
libata
scsi_mod
r8169
ehci_hcd
uhci_hcd
usbcore
dm_mirror
dm_snapshot
dm_mod
thermal
processor
fan
fuse
apparmor
commoncap



```

result of lspci -vvnn:
```

00:00.0 Host bridge [0600]: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub [8086:2770] (rev 02)
	Subsystem: ASRock Incorporation Unknown device [1849:2770]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
	Latency: 0
	Capabilities: [e0] Vendor Specific Information

00:02.0 VGA compatible controller [0300]: Intel Corporation 82945G/GZ Integrated Graphics Controller [8086:2772] (rev 02) (prog-if 00 [VGA controller])
	Subsystem: ASRock Incorporation Unknown device [1849:2772]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at fea80000 (32-bit, non-prefetchable) [size=512K]
	Region 1: I/O ports at dc00 [size=8]
	Region 2: Memory at d0000000 (32-bit, prefetchable) [size=256M]
	Region 3: Memory at fea40000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
		Address: 00000000  Data: 0000
	Capabilities: [d0] Power Management version 2
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 01)
	Subsystem: ASRock Incorporation Unknown device [1849:0888]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at fea38000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=55mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
		Address: 0000000000000000  Data: 0000
	Capabilities: [70] Express Unknown type IRQ 0
		Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
		Device: Latency L0s <64ns, L1 <1us
		Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
		Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop+
		Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
		Link: Supported Speed unknown, Width x0, ASPM unknown, Port 0
		Link: Latency L0s <64ns, L1 <1us
		Link: ASPM Disabled CommClk- ExtSynch-
		Link: Speed unknown, Width x0

00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 01) (prog-if 00 [Normal decode])
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 32 bytes
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Prefetchable memory behind bridge: 00000000fdf00000-00000000fdffffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
		Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
		Device: Latency L0s unlimited, L1 unlimited
		Device: Errors: Correctable+ Non-Fatal+ Fatal+ Unsupported+
		Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
		Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
		Link: Supported Speed 2.5Gb/s, Width x1, ASPM L0s L1, Port 1
		Link: Latency L0s <1us, L1 <4us
		Link: ASPM Disabled RCB 64 bytes CommClk- ExtSynch-
		Link: Speed 2.5Gb/s, Width x0
		Slot: AtnBtn- PwrCtrl- MRL- AtnInd- PwrInd- HotPlug+ Surpise+
		Slot: Number 0, PowerLimit 0.000000
		Slot: Enabled AtnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq-
		Slot: AttnInd Unknown, PwrInd Unknown, Power-
		Root: Correctable- Non-Fatal- Fatal- PME-
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
		Address: 00000000  Data: 0000
	Capabilities: [90] Subsystem: ASRock Incorporation Unknown device [1849:27d0]
	Capabilities: [a0] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:1c.1 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 [8086:27d2] (rev 01) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 32 bytes
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: feb00000-febfffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
		Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
		Device: Latency L0s unlimited, L1 unlimited
		Device: Errors: Correctable+ Non-Fatal+ Fatal+ Unsupported+
		Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
		Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
		Link: Supported Speed 2.5Gb/s, Width x1, ASPM L0s L1, Port 2
		Link: Latency L0s <256ns, L1 <4us
		Link: ASPM Disabled RCB 64 bytes CommClk+ ExtSynch-
		Link: Speed 2.5Gb/s, Width x1
		Slot: AtnBtn- PwrCtrl- MRL- AtnInd- PwrInd- HotPlug+ Surpise+
		Slot: Number 0, PowerLimit 0.000000
		Slot: Enabled AtnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq-
		Slot: AttnInd Unknown, PwrInd Unknown, Power-
		Root: Correctable- Non-Fatal- Fatal- PME-
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
		Address: 00000000  Data: 0000
	Capabilities: [90] Subsystem: ASRock Incorporation Unknown device [1849:27d2]
	Capabilities: [a0] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 01) (prog-if 00 [UHCI])
	Subsystem: ASRock Incorporation Unknown device [1849:27c8]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 23
	Region 4: I/O ports at d400 [size=32]

00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 01) (prog-if 00 [UHCI])
	Subsystem: ASRock Incorporation Unknown device [1849:27c9]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin B routed to IRQ 19
	Region 4: I/O ports at d480 [size=32]

00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 01) (prog-if 00 [UHCI])
	Subsystem: ASRock Incorporation Unknown device [1849:27ca]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin C routed to IRQ 18
	Region 4: I/O ports at d800 [size=32]

00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 01) (prog-if 00 [UHCI])
	Subsystem: ASRock Incorporation Unknown device [1849:27cb]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin D routed to IRQ 16
	Region 4: I/O ports at d880 [size=32]

00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 01) (prog-if 20 [EHCI])
	Subsystem: ASRock Incorporation Unknown device [1849:27cc]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 23
	Region 0: Memory at fea37c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [58] Debug port

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev e1) (prog-if 01 [Subtractive decode])
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
	Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
	Capabilities: [50] Subsystem: ASRock Incorporation Unknown device [1849:244e]

00:1f.0 ISA bridge [0601]: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge [8086:27b8] (rev 01)
	Subsystem: ASRock Incorporation Unknown device [1849:27b8]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Capabilities: [e0] Vendor Specific Information

00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 01) (prog-if 8a [Master SecP PriP])
	Subsystem: ASRock Incorporation Unknown device [1849:27df]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 18
	Region 0: I/O ports at 01f0 [size=8]
	Region 1: I/O ports at 03f4 [size=1]
	Region 2: I/O ports at 0170 [size=8]
	Region 3: I/O ports at 0374 [size=1]
	Region 4: I/O ports at ffa0 [size=16]

00:1f.2 IDE interface [0101]: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller [8086:27c0] (rev 01) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: ASRock Incorporation Unknown device [1849:27c0]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin B routed to IRQ 19
	Region 0: I/O ports at d080 [size=8]
	Region 1: I/O ports at d000 [size=4]
	Region 2: I/O ports at cc00 [size=8]
	Region 3: I/O ports at c880 [size=4]
	Region 4: I/O ports at c800 [size=16]
	Capabilities: [70] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 01)
	Subsystem: ASRock Incorporation Unknown device [1849:27da]
	Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Interrupt: pin B routed to IRQ 5
	Region 4: I/O ports at 0400 [size=32]

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller [10ec:8136] (rev 01)
	Subsystem: ASRock Incorporation Unknown device [1849:8136]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 17
	Region 0: I/O ports at e800 [size=256]
	Region 2: Memory at febff000 (64-bit, non-prefetchable) [size=4K]
	Expansion ROM at febc0000 [disabled] [size=128K]
	Capabilities: [40] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0-,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [48] Vital Product Data
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable-
		Address: 0000000000000000  Data: 0000
	Capabilities: [60] Express Endpoint IRQ 0
		Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag+
		Device: Latency L0s <128ns, L1 unlimited
		Device: AtnBtn+ AtnInd+ PwrInd+
		Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
		Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
		Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
		Link: Supported Speed 2.5Gb/s, Width x1, ASPM L0s, Port 0
		Link: Latency L0s unlimited, L1 unlimited
		Link: ASPM Disabled RCB 64 bytes CommClk+ ExtSynch-
		Link: Speed 2.5Gb/s, Width x1
	Capabilities: [84] Vendor Specific Information


```

result of dmesg:
```

[    0.000000] Linux version 2.6.22-14-server (buildd@king) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 03:10:53 UTC 2008 (Ubuntu 2.6.22-14.52-server)
[    0.000000] Command line: root=/dev/mapper/ubuntu64-root ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f7b0000 (usable)
[    0.000000]  BIOS-e820: 000000003f7b0000 - 000000003f7c0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003f7c0000 - 000000003f7f0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003f7f0000 - 000000003f800000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff380000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 260016) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F9410 checksum 0
[    0.000000] ACPI: RSDP 000F9410, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 3F7B0000, 0038 (r1 A_M_I  OEMRSDT   9000714 MSFT       97)
[    0.000000] ACPI: FACP 3F7B0200, 0084 (r2 A M I  OEMFACP  12000601 MSFT       97)
[    0.000000] ACPI: DSDT 3F7B0440, 4756 (r1  ASR18 ASR18141      141 INTL  2002026)
[    0.000000] ACPI: FACS 3F7C0000, 0040
[    0.000000] ACPI: APIC 3F7B0390, 006C (r1 A_M_I  OEMAPIC   9000714 MSFT       97)
[    0.000000] ACPI: MCFG 3F7B0400, 003C (r1 A_M_I  OEMMCFG   9000714 MSFT       97)
[    0.000000] ACPI: OEMB 3F7C0040, 0046 (r1 A_M_I  AMI_OEM   9000714 MSFT       97)
[    0.000000] ACPI: HPET 3F7B4BA0, 0038 (r1 A_M_I  OEMHPET   9000714 MSFT       97)
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000003f7b0000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 260016) 1 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-000000003f7b0000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   260016
[    0.000000] On node 0 totalpages: 259919
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1242 pages reserved
[    0.000000]   DMA zone: 2701 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 3498 pages used for memmap
[    0.000000]   DMA32 zone: 252422 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e4000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 3f800000:bf500000)
[    0.000000] SMP: Allowing 4 CPUs, 3 hotplug CPUs
[    0.000000] PERCPU: Allocating 42120 bytes of per cpu data
[    0.000000] Built 1 zonelists.  Total pages: 255123
[    0.000000] Kernel command line: root=/dev/mapper/ubuntu64-root ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[   28.551853] time.c: Detected 1795.029 MHz processor.
[   28.552958] Console: colour VGA+ 80x25
[   28.552980] Checking aperture...
[   28.552990] Calgary: detecting Calgary via BIOS EBDA area
[   28.552992] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[   28.566098] Memory: 1012384k/1040064k available (2296k kernel code, 27292k reserved, 1238k data, 308k init)
[   28.566173] SLUB: Genslabs=23, HWalign=64, Order=0-1, MinObjects=4, CPUs=4, Nodes=1
[   28.716011] Calibrating delay using timer specific routine.. 3592.25 BogoMIPS (lpj=17961285)
[   28.716049] Security Framework v1.0.0 initialized
[   28.716058] SELinux:  Disabled at boot.
[   28.716180] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   28.716954] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
[   28.717390] Mount-cache hash table entries: 256
[   28.717574] CPU: L1 I cache: 32K, L1 D cache: 32K
[   28.717578] CPU: L2 cache: 512K
[   28.717581] CPU 0/0 -> Node 0
[   28.717582] using mwait in idle threads.
[   28.717590] CPU0: Thermal monitoring enabled (TM2)
[   28.717605] SMP alternatives: switching to UP code
[   28.717902] Early unpacking initramfs... done
[   29.129606] ACPI: Core revision 20070126
[   29.129655] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   29.243388] Using local APIC timer interrupts.
[   29.299059] result 12465469
[   29.299061] Detected 12.465 MHz APIC timer.
[   29.305574] Brought up 1 CPUs
[   29.305837] NET: Registered protocol family 16
[   29.305950] ACPI: bus type pci registered
[   29.305958] PCI: Using configuration type 1
[   29.308642] ACPI: EC: Look up EC in DSDT
[   29.312751] ACPI: Interpreter enabled
[   29.312756] ACPI: (supports S0 S1 S3 S4 S5)
[   29.312775] ACPI: Using IOAPIC for interrupt routing
[   29.313016] Error attaching device data
[   29.313063] Error attaching device data
[   29.313112] Error attaching device data
[   29.313155] Error attaching device data
[   29.322455] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   29.322474] PCI: Probing PCI hardware (bus 00)
[   29.322997] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[   29.323001] PCI quirk: region 0480-04bf claimed by ICH6 GPIO
[   29.323442] PCI: Transparent bridge - 0000:00:1e.0
[   29.323492] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   29.323646] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   29.323758] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[   29.323841] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
[   29.332314] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   29.332427] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   29.332536] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 *6 7 10 11 12 14 15)
[   29.332644] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   29.332754] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   29.332862] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   29.332971] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   29.333078] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 14 *15)
[   29.333195] Linux Plug and Play Support v0.97 (c) Adam Belay
[   29.333207] pnp: PnP ACPI init
[   29.333224] ACPI: bus type pnp registered
[   29.338316] pnp: PnP ACPI: found 19 devices
[   29.338319] ACPI: ACPI bus type pnp unregistered
[   29.338392] PCI: Using ACPI for IRQ routing
[   29.338395] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   29.338484] NET: Registered protocol family 8
[   29.338487] NET: Registered protocol family 20
[   29.338495] NetLabel: Initializing
[   29.338498] NetLabel:  domain hash size = 128
[   29.338500] NetLabel:  protocols = UNLABELED CIPSOv4
[   29.338517] NetLabel:  unlabeled traffic allowed by default
[   29.338522] PCI-GART: No AMD northbridge found.
[   29.338527] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   29.338530] hpet0: 3 64-bit timers, 14318180 Hz
[   29.339617] pnp: 00:01: iomem range 0xfed13000-0xfed19fff has been reserved
[   29.339628] pnp: 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
[   29.339631] pnp: 00:08: iomem range 0xfed20000-0xfed8ffff has been reserved
[   29.339638] pnp: 00:0b: iomem range 0xffc00000-0xfff7ffff could not be reserved
[   29.339645] pnp: 00:0c: iomem range 0xfec00000-0xfec00fff has been reserved
[   29.339647] pnp: 00:0c: iomem range 0xfee00000-0xfee00fff could not be reserved
[   29.339654] pnp: 00:10: ioport range 0x290-0x29f has been reserved
[   29.339659] pnp: 00:11: iomem range 0xe0000000-0xefffffff has been reserved
[   29.339665] pnp: 00:12: iomem range 0x0-0x9ffff could not be reserved
[   29.339667] pnp: 00:12: iomem range 0xc0000-0xcffff has been reserved
[   29.339670] pnp: 00:12: iomem range 0xe0000-0xfffff could not be reserved
[   29.339672] pnp: 00:12: iomem range 0x100000-0x3f7fffff could not be reserved
[   29.340024] PCI: Bridge: 0000:00:1c.0
[   29.340027]   IO window: disabled.
[   29.340031]   MEM window: disabled.
[   29.340035]   PREFETCH window: fdf00000-fdffffff
[   29.340039] PCI: Bridge: 0000:00:1c.1
[   29.340042]   IO window: e000-efff
[   29.340046]   MEM window: feb00000-febfffff
[   29.340050]   PREFETCH window: disabled.
[   29.340054] PCI: Bridge: 0000:00:1e.0
[   29.340055]   IO window: disabled.
[   29.340059]   MEM window: disabled.
[   29.340062]   PREFETCH window: disabled.
[   29.340091] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   29.340097] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   29.340113] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
[   29.340117] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   29.340127] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   29.340141] NET: Registered protocol family 2
[   29.345499] Time: tsc clocksource has been installed.
[   29.415753] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[   29.416115] TCP established hash table entries: 131072 (order: 9, 3145728 bytes)
[   29.418527] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   29.419355] TCP: Hash tables configured (established 131072 bind 65536)
[   29.419359] TCP reno registered
[   29.445855] checking if image is initramfs... it is
[   30.250926] Freeing initrd memory: 7824k freed
[   30.255309] audit: initializing netlink socket (disabled)
[   30.255326] audit(1203816480.670:1): initialized
[   30.257712] VFS: Disk quotas dquot_6.5.1
[   30.257792] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   30.257921] io scheduler noop registered
[   30.257924] io scheduler anticipatory registered
[   30.257926] io scheduler deadline registered (default)
[   30.258074] io scheduler cfq registered
[   30.258089] Boot video device is 0000:00:02.0
[   30.258447] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   30.258485] assign_interrupt_mode Found MSI capability
[   30.258488] Allocate Port Service[0000:00:1c.0:pcie00]
[   30.258533] Allocate Port Service[0000:00:1c.0:pcie02]
[   30.258620] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   30.258657] assign_interrupt_mode Found MSI capability
[   30.258659] Allocate Port Service[0000:00:1c.1:pcie00]
[   30.258697] Allocate Port Service[0000:00:1c.1:pcie02]
[   30.305276] Real Time Clock Driver v1.12ac
[   30.305455] hpet_resources: 0xfed00000 is busy
[   30.305483] Linux agpgart interface v0.102 (c) Dave Jones
[   30.305486] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   30.305606] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   30.305875] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   30.306801] 00:0f: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   30.307662] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   30.307893] input: Macintosh mouse button emulation as /class/input/input0
[   30.307991] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   30.311447] serio: i8042 KBD port at 0x60,0x64 irq 1
[   30.311455] serio: i8042 AUX port at 0x60,0x64 irq 12
[   30.311695] mice: PS/2 mouse device common for all mice
[   30.311836] TCP cubic registered
[   30.311935] NET: Registered protocol family 1
[   30.312148] /build/buildd/linux-source-2.6.22-2.6.22/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   30.312156] Freeing unused kernel memory: 308k freed
[   30.329425] input: AT Translated Set 2 keyboard as /class/input/input1
[   31.534131] AppArmor: AppArmor initialized<5>audit(1203816481.950:2):  type=1505 info="AppArmor initialized" pid=1213
[   31.539898] fuse init (API version 7.8)
[   31.544492] Failure registering capabilities with primary security module.
[   31.564537] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   31.564548] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   31.564556] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   31.576480] device-mapper: ioctl: 4.11.0-ioctl (2006-10-12) initialised: dm-devel@redhat.com
[   32.513620] usbcore: registered new interface driver usbfs
[   32.513645] usbcore: registered new interface driver hub
[   32.513670] usbcore: registered new device driver usb
[   32.514498] USB Universal Host Controller Interface driver v3.0
[   32.514604] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 23
[   32.514615] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   32.514618] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   32.514783] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   32.514812] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000d400
[   32.514928] usb usb1: configuration #1 chosen from 1 choice
[   32.514957] hub 1-0:1.0: USB hub found
[   32.514964] hub 1-0:1.0: 2 ports detected
[   32.577690] SCSI subsystem initialized
[   32.582161] libata version 2.21 loaded.
[   32.625782] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[   32.625795] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   32.625798] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   32.625830] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   32.625857] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d480
[   32.625952] usb usb2: configuration #1 chosen from 1 choice
[   32.625978] hub 2-0:1.0: USB hub found
[   32.625985] hub 2-0:1.0: 2 ports detected
[   32.735701] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   32.735713] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   32.735716] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   32.735741] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   32.735768] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d800
[   32.735865] usb usb3: configuration #1 chosen from 1 choice
[   32.735893] hub 3-0:1.0: USB hub found
[   32.735900] hub 3-0:1.0: 2 ports detected
[   32.845899] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[   32.845914] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   32.845919] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   32.845952] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   32.845983] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000d880
[   32.846098] usb usb4: configuration #1 chosen from 1 choice
[   32.846123] hub 4-0:1.0: USB hub found
[   32.846129] hub 4-0:1.0: 2 ports detected
[   32.905927] usb 1-2: new low speed USB device using uhci_hcd and address 2
[   32.956412] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 23
[   32.956536] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   32.956543] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   32.956592] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   32.956627] ehci_hcd 0000:00:1d.7: debug port 1
[   32.956632] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   32.956640] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfea37c00
[   33.036205] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   33.036352] usb usb5: configuration #1 chosen from 1 choice
[   33.036387] hub 5-0:1.0: USB hub found
[   33.036397] hub 5-0:1.0: 8 ports detected
[   33.147013] r8169 Gigabit Ethernet driver 2.2LK loaded
[   33.147039] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   33.147057] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   33.147263] eth0: RTL8101e at 0xffffc200005e4000, 00:19:66:51:19:a0, XID 34200000 IRQ 17
[   33.150167] ata_piix 0000:00:1f.1: version 2.11
[   33.150184] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   33.150212] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   33.150779] scsi0 : ata_piix
[   33.150843] scsi1 : ata_piix
[   33.150939] ata1: PATA max UDMA/133 cmd 0x00000000000101f0 ctl 0x00000000000103f6 bmdma 0x000000000001ffa0 irq 14
[   33.150943] ata2: PATA max UDMA/133 cmd 0x0000000000010170 ctl 0x0000000000010376 bmdma 0x000000000001ffa8 irq 15
[   33.318457] ata2: port disabled. ignoring.
[   33.318500] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[   33.318523] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[   33.318553] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   33.318591] scsi2 : ata_piix
[   33.318653] scsi3 : ata_piix
[   33.318680] ata3: SATA max UDMA/133 cmd 0x000000000001d080 ctl 0x000000000001d002 bmdma 0x000000000001c800 irq 19
[   33.318684] ata4: SATA max UDMA/133 cmd 0x000000000001cc00 ctl 0x000000000001c882 bmdma 0x000000000001c808 irq 19
[   33.457485] usb 1-2: device not accepting address 2, error -71
[   33.541692] ata3.00: ATA-7: ST3320620AS, 3.AAK, max UDMA/133
[   33.541697] ata3.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   33.624925] ata3.00: configured for UDMA/133
[   33.989780] ata4.00: ATA-8: ST3500320AS, AD14, max UDMA/133
[   33.989785] ata4.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   33.989790] ata4.01: ATAPI: LITE-ON DVDRW LH-20A1S, 9L08, max UDMA/100
[   34.029909] ata4.00: configured for UDMA/133
[   34.159815] usb 1-2: new low speed USB device using uhci_hcd and address 4
[   34.230297] ata4.01: configured for UDMA/100
[   34.230431] scsi 2:0:0:0: Direct-Access     ATA      ST3320620AS      3.AA PQ: 0 ANSI: 5
[   34.231842] scsi 3:0:0:0: Direct-Access     ATA      ST3500320AS      AD14 PQ: 0 ANSI: 5
[   34.233887] scsi 3:0:1:0: CD-ROM            LITE-ON  DVDRW LH-20A1S   9L08 PQ: 0 ANSI: 5
[   34.243410] sd 2:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[   34.243421] sd 2:0:0:0: [sda] Write Protect is off
[   34.243423] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   34.243434] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   34.243482] sd 2:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[   34.243489] sd 2:0:0:0: [sda] Write Protect is off
[   34.243491] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   34.243501] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   34.243504]  sda: sda1 sda2 < sda5 >
[   34.269961] sd 2:0:0:0: [sda] Attached SCSI disk
[   34.273134] sd 3:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[   34.273145] sd 3:0:0:0: [sdb] Write Protect is off
[   34.273148] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   34.273158] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   34.273212] sd 3:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[   34.273219] sd 3:0:0:0: [sdb] Write Protect is off
[   34.273221] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   34.273231] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   34.273234]  sdb: unknown partition table
[   34.291147] sd 3:0:0:0: [sdb] Attached SCSI disk
[   34.297447] sd 2:0:0:0: Attached scsi generic sg0 type 0
[   34.297467] sd 3:0:0:0: Attached scsi generic sg1 type 0
[   34.297487] sr 3:0:1:0: Attached scsi generic sg2 type 5
[   34.336088] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   34.336093] Uniform CD-ROM driver Revision: 3.20
[   34.336150] sr 3:0:1:0: Attached scsi CD-ROM sr0
[   34.378509] usb 1-2: configuration #1 chosen from 1 choice
[   34.397189] usbcore: registered new interface driver hiddev
[   34.772143] Attempting manual resume
[   34.772147] swsusp: Resume From Partition 254:1
[   34.772149] PM: Checking swsusp image.
[   34.772317] PM: Resume from disk failed.
[   34.809481] kjournald starting.  Commit interval 5 seconds
[   34.809497] EXT3-fs: mounted filesystem with ordered data mode.
[   34.846088] hiddev96: USB HID v1.10 Device [APC Back-UPS ES 550 FW:840.B2.D USB FW:B2] on usb-0000:00:1d.0-2
[   34.846106] usbcore: registered new interface driver usbhid
[   34.846110] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   39.221303] r8169: eth0: link up
[   39.221313] r8169: eth0: link up
[   40.557498] NET: Registered protocol family 17
[   40.924652] agpgart: Detected an Intel 945G Chipset.
[   40.924802] agpgart: Detected 7932K stolen memory.
[   40.939213] agpgart: AGP aperture is 256M @ 0xd0000000
[   40.964056] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   41.001927] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   41.041729] intel_rng: FWH not detected
[   41.921556] input: PC Speaker as /class/input/input2
[   41.992097] iTCO_vendor_support: vendor-support=0
[   42.009304] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   42.009375] iTCO_wdt: Found a ICH7 or ICH7R TCO device (Version=2, TCOBASE=0x0860)
[   42.009405] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   42.140980] irda_init()
[   42.140998] NET: Registered protocol family 23
[   42.256190] usbcore: registered new interface driver xpad
[   42.256195] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: driver for Xbox controllers v0.1.6
[   42.567775] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
[   42.567870] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   42.776342] input: ImPS/2 Logitech Wheel Mouse as /class/input/input3
[   42.779119] parport_pc 00:07: reported by Plug and Play ACPI
[   42.779174] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   43.234050] loop: module loaded
[   43.264744] lp0: using parport0 (interrupt-driven).
[   43.372373] Adding 1511416k swap on /dev/mapper/ubuntu64-swap_1.  Priority:-1 extents:1 across:1511416k
[   43.739674] EXT3 FS on dm-0, internal journal
[   44.772946] kjournald starting.  Commit interval 5 seconds
[   44.795651] NET: Registered protocol family 10
[   44.795758] lo: Disabled Privacy Extensions
[   44.802278] EXT3 FS on sda1, internal journal
[   44.802286] EXT3-fs: mounted filesystem with ordered data mode.
[   44.910163] kjournald starting.  Commit interval 5 seconds
[   44.910556] EXT3 FS on dm-2, internal journal
[   44.910562] EXT3-fs: mounted filesystem with ordered data mode.
[   45.585089] input: Power Button (FF) as /class/input/input4
[   45.585107] ACPI: Power Button (FF) [PWRF]
[   45.585196] input: Power Button (CM) as /class/input/input5
[   45.585208] ACPI: Power Button (CM) [PWRB]
[   45.693766] No dock devices found.
[   47.180528] ppdev: user-space parallel port driver
[   47.368775] audit(1203816498.212:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4823 profile="/usr/sbin/cupsd"
[   55.236518] eth0: no IPv6 routers present
[   57.946787] Failure registering capabilities with primary security module.
[   59.987211] [drm] Initialized drm 1.1.0 20060810
[   60.003694] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   60.003788] [drm] Initialized i915 1.6.0 20060119 on minor 0

```

---

### Post by CRCarl on 2008-02-24
Something to try - 

Right click on the speaker icon in the tray, click "Open Volume Control". Make sure that all the outputs are maxed out. Click "File -> Change Device" select the next device, make sure that all the outputs are maxed out. Do this for every device, then let us know.

---

### Post by garolou on 2008-02-24
Hi CRCarl,
All my channels are maxed; both devices: HDA Intel (alsa mixer) and Realtek ALC888 (OSS mixer). From the volume control preferences menu I  ticked everything to be sure I didn't miss any channels (tracks). I also ran alsamixer at the command line where every channel is always listed.

Dave
:-)

---

### Post by _Doc_ on 2008-02-25
I had the same problem... quiet sound even when it was maxed out.  i found that i had to open the volume control... make sure it says  HDA Intel on top and then go to Edit and preferences.  Then check the Front option... once i did that and i cranked up the front I got my sound back.

---

### Post by sofamensch on 2008-03-04
Yes its a almost standard procedure. Open it, ensure you get all the sliders (including FRONT, SURROUND,...) and that you plugged in into the right box. (for only one i suggest the middle green one as it is the front).

Also ensure - that there is no other soundcard installed! Because ubuntu 7.10 tends to use only the other card then with the ALSA.

---

### Post by rickyrockrat on 2008-03-26
Generally, the outputs on the back of the PC are not designed to drive speakers, so if you are not using amplified speakers, I would not expect to get much sound out of them.

plug in a pair of 32 ohm headphones and check the output level. Slide the volume controls up and down to see if they are working. If they adjust the volume level, but your sound level is not high enough, then you either need to turn the volume up on your speakers (assuming you have a vol. control) or go get amplified ones.

---

### Post by alejo0823 on 2008-04-15
I have the same problem with my sound and I also have the alc 888 on board still no solution, have you found 1?

---

### Post by garolou on 2008-04-21
rickyrockrat : Unfortunately, headphones pluged in the back still has low volume.

alejo0823 : No solution yet. Although at this point i'm not searching anymore. There is a limit on how many days one should spend searching. And I have spent way too much time! It took one year for Ubuntu to mature enough to allow me to install it on my laptop; I expect one day or the other someone will resolve this and all the other problems I have and this computer system will be usable at 100%.

I will post a solution if it comes along.

Cheers

Dave

---

### Post by minhaz4u on 2008-04-22
I have the same problem too...Rear Speakers are not working anymore :-(

---

### Post by jetpeach on 2008-04-26
same problem here- it's not awful for me (my speakers can still get loud if i have the volume on the amp high enough) but it's definitely quiet than before i upgraded to hardy

---

### Post by cuhlik on 2008-07-20
I have the same problem, very low volume on rear speaker outputs --- but my front headphone jack plays the same, very low volume.  I've turned up all volume controls on HDA Intel (Alsa mixer) and Realtek ALC888 (OSS Mixer) devices on the gnome audio control.  I've turned on all sliders and turned them all up.  The sound is coming from the "Front" PCM channel as that's the one that affects the volume.  But even turned all the way up, the sound is very faint -- dominated by amplifier hum.  Note that the ubuntu startup sound plays at normal volume, but after logging in, everything else plays very quietly. 

I downloaded, compiled, installed new drivers alsa-driver-1.0.17  alsa-lib-1.0.17  alsa-utils-1.0.17 and rebooted with no change.

kathi@KB:/usr/src/alsa$ uname -a
Linux KB-linux 2.6.22-15-generic #1 SMP Tue Jun 10 09:21:34 UTC 2008 i686 GNU/Linux

kathi@KB:/usr/src/alsa$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC888


Anyone have any further suggestions?

Thanks,

Chris

---

