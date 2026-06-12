---
title: "Microphone not working on HP Pavilion dv7"
date: 2010-09-24
forum: Multimedia Software
---

### Post by QOLIM on 2010-09-24
Hey,

the microphone of my laptop doesn't work, I'm on a HP Pavilion dv7 and neither the build-in or a microphone plugged in works.

I tried many things (like this: [https://answers.launchpad.net/ubuntu/+question/78574](https://answers.launchpad.net/ubuntu/+question/78574)) to get it work, but none has worked. But I'm quite sure it worked in some earlier ubuntu version.
I'm running kubuntu so it's not a problem in pulseaudio.
Can anyone please help me with this, because I really hate it I have to restart in windows every time for the mic.
Any help?

Thanks,
QOLIM

Alsa info:
> upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.59
!!################################

!!Script ran on: Fri Sep 24 15:54:42 UTC 2010


!!Linux Distribution
!!------------------

Ubuntu 10.04.1 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"


!!DMI Information
!!---------------

Manufacturer:      Hewlett-Packard
Product Name:      HP Pavilion dv7 Notebook PC


!!Kernel Information
!!------------------

Kernel release:    2.6.32-24-generic-pae
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.21
Library version:    1.0.22
Utilities version:  1.0.22


!!Loaded ALSA modules
!!-------------------

snd_hda_intel


!!Sound Servers on this system
!!----------------------------

No sound servers found.


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xdf000000 irq 34


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:293e (rev 03)
	Subsystem: 103c:30f4


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-usb-caiaq: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-hda-intel: model=dell-m4-1
snd-hda-intel: enable_msi=1


!!Loaded sound module options
!!--------------------------

!!Module: snd_hda_intel
	bdl_pos_adj : 1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	enable_msi : 1
	id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
	index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	model : dell-m4-1,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
	patch : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
	position_fix : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	power_save : 0
	power_save_controller : Y
	probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	probe_only : N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N
	single_cmd : N


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: IDT 92HD71B7X
Address: 0
Function Id: 0x1
Vendor Id: 0x111d76b2
Subsystem Id: 0x103c30f4
Revision Id: 0x100302
No Modem Function Group found
Default PCM:
    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
Default Amp-Out caps: ofs=0x7f, nsteps=0x7f, stepsize=0x02, mute=1
GPIO: io=8, o=0, i=0, unsolicited=1, wake=1
  IO[0]: enable=1, dir=1, wake=0, sticky=0, data=1, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[2]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[3]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[4]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[5]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[6]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[7]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Power-Map: 0x01
Analog Loopback: 0x00
Node 0x0a [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x0000001c: OUT HP Detect
  Pin Default 0x0421101f: [Jack] HP Out at Ext Right
    Conn = 1/8, Color = Black
    DefAssociation = 0x1, Sequence = 0xf
  Pin-ctls: 0x00:
  Unsolicited: tag=01, enabled=1
  Connection: 3
     0x10 0x11* 0x17
Node 0x0b [Pin Complex] wcaps 0x400081: Stereo
  Pincap 0x00001724: IN Detect
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x04a11221: [Jack] Mic at Ext Right
    Conn = 1/8, Color = Black
    DefAssociation = 0x2, Sequence = 0x1
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=03, enabled=1
Node 0x0c [Pin Complex] wcaps 0x400081: Stereo
  Pincap 0x00001724: IN Detect
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x40f000f0: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00: VREF_HIZ
  Unsolicited: tag=00, enabled=0
Node 0x0d [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x00000014: OUT Detect
  Pin Default 0x90170110: [Fixed] Speaker at Int N/A
    Conn = Analog, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 3
     0x10* 0x11 0x17
Node 0x0e [Pin Complex] wcaps 0x400081: Stereo
  Pincap 0x00001724: IN Detect
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x23a1902e: [Jack] Mic at Sep Left
    Conn = 1/8, Color = Pink
    DefAssociation = 0x2, Sequence = 0xe
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=04, enabled=1
Node 0x0f [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x00000014: OUT Detect
  Pin Default 0x23014250: [Jack] Line Out at Sep Left
    Conn = 1/8, Color = Green
    DefAssociation = 0x5, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=02, enabled=1
  Connection: 3
     0x10* 0x11 0x17
Node 0x10 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out R/L
  Amp-Out caps: N/A
  Amp-Out vals:  [0x5b 0x5b]
  Converter: stream=5, channel=0
  Power: setting=D0, actual=D0
  Delay: 13 samples
Node 0x11 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out R/L
  Amp-Out caps: N/A
  Amp-Out vals:  [0x5b 0x5b]
  Converter: stream=5, channel=0
  Power: setting=D0, actual=D0
  Delay: 13 samples
Node 0x12 [Audio Input] wcaps 0x1d0541: Stereo
  Converter: stream=0, channel=0
  SDI-Select: 0
  Power: setting=D3, actual=D3
  Delay: 13 samples
  Connection: 1
     0x1c
  Processing caps: benign=0, ncoeff=0
Node 0x13 [Audio Input] wcaps 0x1d0541: Stereo
  Converter: stream=0, channel=0
  SDI-Select: 0
  Power: setting=D3, actual=D3
  Delay: 13 samples
  Connection: 1
     0x1d
  Processing caps: benign=0, ncoeff=0
Node 0x14 [Pin Complex] wcaps 0x400100: Mono
  Pincap 0x00000010: OUT
  Pin Default 0x40f000f0: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00:
  Connection: 1
     0x16
Node 0x15 [Audio Selector] wcaps 0x300101: Stereo
  Connection: 3
     0x10* 0x11 0x17
Node 0x16 [Audio Mixer] wcaps 0x200100: Mono
  Connection: 1
     0x15
Node 0x17 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97]
  Connection: 5
     0x10 0x11 0x27 0x1a 0x1b
Node 0x18 [Pin Complex] wcaps 0x40000d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-Out vals:  [0x03 0x03]
  Pincap 0x00000020: IN
  Pin Default 0x90a000f0: [Fixed] Mic at Int N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x20: IN
Node 0x19 [Pin Complex] wcaps 0x40000d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x00000020: IN
  Pin Default 0x40f000f0: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00:
Node 0x1a [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-Out vals:  [0x03 0x03]
  Connection: 3
     0x0b* 0x0c 0x0e
Node 0x1b [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-Out vals:  [0x03 0x03]
  Connection: 3
     0x0b 0x0c 0x0e*
Node 0x1c [Audio Selector] wcaps 0x30090d: Stereo Amp-Out R/L
  Amp-Out caps: ofs=0x00, nsteps=0x0f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x88 0x88]
  Connection: 4
     0x1a* 0x17 0x18 0x19
Node 0x1d [Audio Selector] wcaps 0x30090d: Stereo Amp-Out R/L
  Amp-Out caps: ofs=0x00, nsteps=0x0f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x88 0x88]
  Connection: 4
     0x1b* 0x17 0x18 0x19
Node 0x1e [Pin Complex] wcaps 0x400301: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x4f0000f0: [N/A] Line Out at Ext UNKNOWN
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00:
  Connection: 1
     0x24
Node 0x1f [Pin Complex] wcaps 0x400701: Stereo Digital
  Pincap 0x00010010: OUT EAPD
  EAPD 0x0:
  Pin Default 0x4f0000f0: [N/A] Line Out at Ext UNKNOWN
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00:
  Power: setting=D0, actual=D0
  Connection: 2
     0x24* 0x25
Node 0x20 [Pin Complex] wcaps 0x400301: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x40f100f6: [N/A] Other at Ext N/A
    Conn = 1/8, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x6
  Pin-ctls: 0x00:
  Connection: 1
     0x25
Node 0x21 [Audio Output] wcaps 0x40211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Delay: 4 samples
Node 0x22 [Audio Output] wcaps 0x40211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Delay: 4 samples
Node 0x23 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x24 [Audio Selector] wcaps 0x300101: Stereo
  Connection: 3
     0x21* 0x1c 0x1d
Node 0x25 [Audio Selector] wcaps 0x300101: Stereo
  Connection: 3
     0x22* 0x1c 0x1d
Node 0x26 [Beep Generator Widget] wcaps 0x70000c: Mono Amp-Out
  Amp-Out caps: ofs=0x03, nsteps=0x03, stepsize=0x17, mute=1
  Amp-Out vals:  [0x00]
Node 0x27 [Pin Complex] wcaps 0x400000: Mono
  Pincap 0x00000020: IN
  Pin Default 0x40f100f8: [N/A] Other at Ext N/A
    Conn = 1/8, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x8
  Pin-ctls: 0x00:
Node 0x28 [Volume Knob Widget] wcaps 0x600000: Mono
  Volume-Knob: delta=1, steps=127, direct=1, val=127
  Connection: 2
     0x10 0x11
Codec: Nvidia MCP78 HDMI
Address: 2
Function Id: 0x1
Vendor Id: 0x10de0006
Subsystem Id: 0x10de0101
Revision Id: 0x100000
No Modem Function Group found
Default PCM:
    rates [0x0]:
    bits [0x0]:
    formats [0x0]:
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x04 [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0xc0]: 48000 88200
    bits [0xf]: 8 16 20 24
    formats [0x1]: PCM
Node 0x05 [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x18560110: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x04
Node 0x06 [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0xc0]: 48000 88200
    bits [0xf]: 8 16 20 24
    formats [0x1]: PCM
Node 0x07 [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x58560121: [N/A] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x2, Sequence = 0x1
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x06
Node 0x08 [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0xc0]: 48000 88200
    bits [0xf]: 8 16 20 24
    formats [0x1]: PCM
Node 0x09 [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x58560122: [N/A] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x2, Sequence = 0x2
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x08
Node 0x0a [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0xc0]: 48000 88200
    bits [0xf]: 8 16 20 24
    formats [0x1]: PCM
Node 0x0b [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x58560123: [N/A] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x2, Sequence = 0x3
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x0a
Node 0x0c [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0xc0]: 48000 88200
    bits [0xf]: 8 16 20 24
    formats [0x1]: PCM
Node 0x0d [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x58560124: [N/A] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x2, Sequence = 0x4
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x0c
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116, 9 Sep 24 14:22 /dev/snd/controlC0
crw-rw----+ 1 root audio 116, 8 Sep 24 14:22 /dev/snd/hwC0D0
crw-rw----+ 1 root audio 116, 7 Sep 24 14:22 /dev/snd/hwC0D2
crw-rw----+ 1 root audio 116, 6 Sep 24 17:35 /dev/snd/pcmC0D0c
crw-rw----+ 1 root audio 116, 5 Sep 24 17:52 /dev/snd/pcmC0D0p
crw-rw----+ 1 root audio 116, 4 Sep 24 14:22 /dev/snd/pcmC0D3p
crw-rw----+ 1 root audio 116, 3 Sep 24 14:22 /dev/snd/seq
crw-rw----+ 1 root audio 116, 2 Sep 24 14:22 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Sep 24 14:22 .
drwxr-xr-x 3 root root 220 Sep 24 14:22 ..
lrwxrwxrwx 1 root root  12 Sep 24 14:22 pci-0000:00:1b.0 -> ../controlC0


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [Intel]

Card hw:0 'Intel'/'HDA Intel at 0xdf000000 irq 34'
  Mixer name	: 'Nvidia MCP78 HDMI'
  Components	: 'HDA:111d76b2,103c30f4,00100302 HDA:10de0006,10de0101,00100000'
  Controls      : 25
  Simple ctrls  : 16
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 28 [44%] [-27.00dB] [on]
Simple mixer control 'Headphone',0
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
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Front Mic Jack Mode',0
  Capabilities: enum
  Items: 'Mic In' 'Line In'
  Item0: 'Mic In'
Simple mixer control 'Mic Jack Mode',0
  Capabilities: enum
  Items: 'Mic In' 'Line In'
  Item0: 'Mic In'
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 8 [53%] [12.00dB] [off]
  Front Right: Capture 8 [53%] [12.00dB] [off]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 8 [53%] [12.00dB] [off]
  Front Right: Capture 8 [53%] [12.00dB] [off]
Simple mixer control 'Digital',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 120
  Front Left: Capture 120 [100%] [30.00dB]
  Front Right: Capture 120 [100%] [30.00dB]
Simple mixer control 'Digital Mic',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 3
  Front Left: Capture 3 [100%] [30.00dB]
  Front Right: Capture 3 [100%] [30.00dB]
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Mic' 'Front Mic' 'Digital Mic'
  Item0: 'Mic'
Simple mixer control 'Input Source',1
  Capabilities: cenum
  Items: 'Mic' 'Front Mic' 'Digital Mic'
  Item0: 'Front Mic'
Simple mixer control 'Mux',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 3
  Front Left: Capture 3 [100%] [30.00dB]
  Front Right: Capture 3 [100%] [30.00dB]
Simple mixer control 'Mux',1
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 3
  Front Left: Capture 3 [100%] [30.00dB]
  Front Right: Capture 3 [100%] [30.00dB]
Simple mixer control 'PC Beep',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 3
  Mono: Playback 3 [100%] [0.00dB] [off]


!!Alsactl output
!!-------------

--startcollapse--
state.Intel {
	control.1 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 64'
		comment.dbmin -4800
		comment.dbmax 0
		iface MIXER
		name 'Front Playback Volume'
		value.0 64
		value.1 64
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
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 'Mic In'
		comment.item.1 'Line In'
		iface MIXER
		name 'Mic Jack Mode'
		value 'Mic In'
	}
	control.4 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 'Mic In'
		comment.item.1 'Line In'
		iface MIXER
		name 'Front Mic Jack Mode'
		value 'Mic In'
	}
	control.5 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'PC Beep Playback Switch'
		value false
	}
	control.6 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 3'
		comment.dbmin -1800
		comment.dbmax 0
		iface MIXER
		name 'PC Beep Playback Volume'
		value 3
	}
	control.7 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 64'
		comment.dbmin -4800
		comment.dbmax 0
		iface MIXER
		name 'Headphone Playback Volume'
		value.0 64
		value.1 64
	}
	control.8 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Headphone Playback Switch'
		value.0 true
		value.1 true
	}
	control.9 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 15'
		comment.dbmin 0
		comment.dbmax 2250
		iface MIXER
		name 'Capture Volume'
		value.0 8
		value.1 8
	}
	control.10 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Capture Switch'
		value.0 false
		value.1 false
	}
	control.11 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 15'
		comment.dbmin 0
		comment.dbmax 2250
		iface MIXER
		name 'Capture Volume'
		index 1
		value.0 8
		value.1 8
	}
	control.12 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Capture Switch'
		index 1
		value.0 false
		value.1 false
	}
	control.13 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 3'
		comment.dbmin 0
		comment.dbmax 3000
		iface MIXER
		name 'Digital Mic Capture Volume'
		value.0 3
		value.1 3
	}
	control.14 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 3'
		comment.dbmin 0
		comment.dbmax 3000
		iface MIXER
		name 'Mux Capture Volume'
		value.0 3
		value.1 3
	}
	control.15 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 3'
		comment.dbmin 0
		comment.dbmax 3000
		iface MIXER
		name 'Mux Capture Volume'
		index 1
		value.0 3
		value.1 3
	}
	control.16 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Mic
		comment.item.1 'Front Mic'
		comment.item.2 'Digital Mic'
		iface MIXER
		name 'Input Source'
		value Mic
	}
	control.17 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Mic
		comment.item.1 'Front Mic'
		comment.item.2 'Digital Mic'
		iface MIXER
		name 'Input Source'
		index 1
		value 'Front Mic'
	}
	control.18 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 64'
		comment.dbmin -4800
		comment.dbmax 0
		iface MIXER
		name 'Master Playback Volume'
		value 28
	}
	control.19 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Master Playback Switch'
		value true
	}
	control.20 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Con Mask'
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.21 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.22 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Default'
		value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.23 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Switch'
		value false
	}
	control.24 {
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
	control.25 {
		comment.access 'read write user'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 120'
		comment.tlv '0000000100000008fffff44800000032'
		comment.dbmin -3000
		comment.dbmax 3000
		iface MIXER
		name 'Digital Capture Volume'
		value.0 120
		value.1 120
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
usbhid
hid
rfcomm
sco
bridge
stp
bnep
binfmt_misc
l2cap
ppdev
snd_hda_codec_nvhdmi
snd_hda_codec_idt
snd_hda_intel
snd_hda_codec
snd_hwdep
snd_pcm
snd_seq
snd_timer
snd_seq_device
arc4
iwlagn
btusb
iwlcore
nvidia
fbcon
tileblit
font
bitblit
softcursor
bluetooth
snd
uvcvideo
videodev
jmb38x_ms
v4l1_compat
mac80211
intel_agp
agpgart
vga16fb
vgastate
sdhci_pci
sdhci
memstick
psmouse
serio_raw
soundcore
snd_page_alloc
cfg80211
joydev
hp_accel
lis3lv02d
lirc_ene0100
lirc_dev
input_polldev
led_class
video
output
lp
parport
ohci1394
r8169
mii
ahci
ieee1394


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x0a 0x0221401f
0x0b 0x02a19020
0x0c 0x40f100f0
0x0d 0x90171110
0x0e 0x40f100f2
0x0f 0x40f100f7
0x14 0x40f100f3
0x18 0x85a61150
0x19 0x40f100f4
0x1e 0x014411a0
0x1f 0x40f100f5
0x20 0x40f100f6
0x27 0x40f100f8

/sys/class/sound/hwC0D0/driver_pin_configs:
0x0a 0x0421101f
0x0b 0x04a11221
0x0c 0x40f000f0
0x0d 0x90170110
0x0e 0x23a1902e
0x0f 0x23014250
0x14 0x40f000f0
0x18 0x90a000f0
0x19 0x40f000f0
0x1e 0x4f0000f0
0x1f 0x4f0000f0

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:

/sys/class/sound/hwC0D2/init_pin_configs:
0x05 0x18560110
0x07 0x58560121
0x09 0x58560122
0x0b 0x58560123
0x0d 0x58560124

/sys/class/sound/hwC0D2/driver_pin_configs:

/sys/class/sound/hwC0D2/user_pin_configs:

/sys/class/sound/hwC0D2/init_verbs:


!!ALSA/HDA dmesg
!!------------------

[   21.466179] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   21.548557] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
[   21.584550] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
[   21.584559] HDA Intel 0000:00:1b.0: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[   21.584603]   alloc irq_desc for 34 on node -1
[   21.584605]   alloc kstat_irqs on node -1
[   21.584616] HDA Intel 0000:00:1b.0: irq 34 for MSI/MSI-X
[   21.584647] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   21.637178] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
--
[   21.637449] NVRM: loading NVIDIA UNIX x86 Kernel Module  195.36.24  Thu Apr 22 09:18:20 PDT 2010
[   21.688162] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input9
[   21.705499] input: HDA Intel Mic at Sep Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   21.705668] input: HDA Intel Mic at Ext Right Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   21.705818] input: HDA Intel Line Out at Sep Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   21.705966] input: HDA Intel HP Out at Ext Right Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   21.896569] kjournald starting.  Commit interval 5 seconds




My /etc/modprobe.d/alsa-base.conf:
> # autoloader aliases
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
#install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
#install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
#install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
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
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2

#options snd-hda-intel power_save=10 power_save_controller=N #model=hp-dv7 enable_msi=1
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=dell-m4-1
options snd-hda-intel enable_msi=1

---

### Post by lkjoel on 2010-09-24
Is your soundcard working?
You might want to replace it.

---

### Post by QOLIM on 2010-09-24
Yes, it is. The sound is working
and in windows everything is working

---

### Post by lkjoel on 2010-09-24
Does your sound work
EDIT: I didn't read your post correctly!

---

### Post by lidex on 2010-09-25
Remove the alsa-base.conf entries you added and replace with this:
```
options snd-hda-intel model=hp-dv5 enable_msi=1
```

No Joy? Update your alsa install to v 1.0.23 using link in my sig

---

### Post by QOLIM on 2010-09-26
> **lidex said:**
> Remove the alsa-base.conf entries you added and replace with this:
```
options snd-hda-intel model=hp-dv5 enable_msi=1
```

No Joy? Update your alsa install to v 1.0.23 using link in my sig

Tried both of them,  it didn't work :(
My subwoofer (bass speaker) now works though  but no success with the mic

---

### Post by lidex on 2010-09-26
> **QOLIM said:**
> Tried both of them,  it didn't work :(
My subwoofer (bass speaker) now works though  but no success with the mic

First, for mic problem, check this.
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

Then go to 'Sound Preferences' to select and unmute your mic in 'Input' tab.
Make sure you have selected a profile with 'duplex' or 'analog input' for the correct sound device on the 'Hardware' tab.
Use Pulse Audio Volume Control (pavucontrol) to unlock stereo sliders for the mic in 'Input Devices' tab. Drag the right slider down to zero. The mic is a mono device.

From alsa documentation:
> Capture Problems
~~~~~~~~~~~~~~~~
The capture problems are often because of missing setups of mixers.
Thus, before submitting a bug report, make sure that you set up the
mixer correctly.  For example, both "Capture Volume" and "Capture
Switch" have to be set properly in addition to the right "Capture
Source" or "Input Source" selection.  Some devices have "Mic Boost"
volume or switch.

When the PCM device is opened via "default" PCM (without pulse-audio
plugin), you'll likely have "Digital Capture Volume" control as well.
This is provided for the extra gain/attenuation of the signal in
software, especially for the inputs without the hardware volume
control such as digital microphones.  Unless really needed, this
should be set to exactly 50%, corresponding to 0dB -- neither extra
gain nor attenuation.  When you use "hw" PCM, i.e., a raw access PCM,
this control will have no influence, though.

---

### Post by QOLIM on 2010-09-29
> Then go to 'Sound Preferences' to select and unmute your mic in 'Input' tab.
Make sure you have selected a profile with 'duplex' or 'analog input' for the correct sound device on the 'Hardware' tab.
Use Pulse Audio Volume Control (pavucontrol) to unlock stereo sliders for the mic in 'Input Devices' tab. Drag the right slider down to zero. The mic is a mono device.

Where is this?

---

### Post by lidex on 2010-09-30
Pulse audio volume control is not installed by default. To install:
```
sudo apt-get install pavucontrol
```

---

### Post by QOLIM on 2010-10-02
Like I said, I'm on kubuntu so I don't have pulseaudio.
This control you're talking about is for pulse audio, so doesn't fix anything for me.

But when I asked where, I ment the 'Sound Preferences' you said, is that in the alsamixer or what?

Thanks for helping btw

---

### Post by lidex on 2010-10-02
> **QOLIM said:**
> Like I said, I'm on kubuntu so I don't have pulseaudio.
This control you're talking about is for pulse audio, so doesn't fix anything for me.

But when I asked where, I ment the 'Sound Preferences' you said, is that in the alsamixer or what?

Thanks for helping btw
Sorry, alot of kubuntu users have installed pulse, so kind of a reflex, I guess. Anyway, ignore the gnome stuff and my suggestion for your next step is updating alsa to 1.0.23 via the link in my sig.

---

### Post by QOLIM on 2010-10-28
Tried it, but still it's not working :/
I think I'm gonna give up, I tried a lot but still no luck..

Thanks anyway

---

### Post by lidex on 2010-10-28
> **QOLIM said:**
> Tried it, but still it's not working :/
I think I'm gonna give up, I tried a lot but still no luck..

Thanks anyway

[http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/8#audio](http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/8#audio)
[http://www.linlap.com/wiki/hp+pavilion+dv7-1200](http://www.linlap.com/wiki/hp+pavilion+dv7-1200)

---

### Post by QOLIM on 2010-11-02
Thanks for all your effort man, it's really appreciated!
It turns out I just had to upgrade to 10.10 to get it all working, but by default it seems he only looked for new lts versions so I had to ajust it to just stable versions.

Thanks a lot, looks like i can finally use skype now :)

---

