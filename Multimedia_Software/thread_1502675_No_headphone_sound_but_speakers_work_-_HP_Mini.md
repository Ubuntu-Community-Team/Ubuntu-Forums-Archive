---
title: "No headphone sound but speakers work - HP Mini"
date: 2010-06-05
forum: Multimedia Software
---

### Post by markinf on 2010-06-05
Hello guys,

I'm not being able to hear any sound from Alsa/Pulse in my headphone right now, tried with severall ones. The speakers works flawless. On the default/stock kernel the sound was ok on both outputs (speakers and headphone). But after the security updates I'm just not working. I've tried botting on the older kernel, but still got no sound on the headphone.

My alsamixers levels are ok, heres some additional info.

marcos@Pandora:~$ uname -a
Linux Pandora 2.6.32-22-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux

marcos@Pandora:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.

marcos@Pandora:~$ head -n 1 /proc/asound/card*/codec#*
Codec: IDT 92HD75B2X5

Output of alsa-info.sh =]
```

upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.59
!!################################

!!Script ran on: Sun Jun 6 01:05:07 UTC 2010

!!Linux Distribution
!!------------------

Ubuntu 10.04 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.04 LTS"

!!DMI Information
!!---------------

Manufacturer: Hewlett-Packard
Product Name: HP Mini 1000 Netbook PC

!!Kernel Information
!!------------------

Kernel release: 2.6.32-22-generic
Operating System: GNU/Linux
Architecture: i686
Processor: unknown
SMP Enabled: Yes

!!ALSA Version
!!------------

Driver version: 1.0.21
Library version: 1.0.22
Utilities version: 1.0.22

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

 0 [Intel ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfe938000 irq 16

!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)

!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:27d8 (rev 02)
 Subsystem: 103c:361a
--
 Prefetchable memory behind bridge: 0000000040000000-00000000401fffff
 Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
--
 Prefetchable memory behind bridge: 0000000040200000-00000000403fffff
 Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-

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

!!Loaded sound module options
!!--------------------------

!!Module: snd_hda_intel
 bdl_pos_adj : 1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
 enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
 enable_msi : 0
 id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
 index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
 model : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
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

Codec: IDT 92HD75B2X5
Address: 0
Function Id: 0x1
Vendor Id: 0x111d7608
Subsystem Id: 0x103c361a
Revision Id: 0x100102
No Modem Function Group found
Default PCM:
    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
Default Amp-Out caps: ofs=0x7f, nsteps=0x7f, stepsize=0x02, mute=1
GPIO: io=8, o=0, i=0, unsolicited=1, wake=1
  IO[0]: enable=1, dir=1, wake=0, sticky=0, data=1, unsol=0
  IO[1]: enable=1, dir=0, wake=0, sticky=0, data=0, unsol=1
  IO[2]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[3]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[4]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[5]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[6]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[7]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Power-Map: 0x00
Analog Loopback: 0x00
Node 0x0a [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x0000001c: OUT HP Detect
  Pin Default 0x0121101f: [Jack] HP Out at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0x1, Sequence = 0xf
  Pin-ctls: 0xc0: OUT HP
  Unsolicited: tag=02, enabled=1
  Connection: 3
     0x10 0x11* 0x17
Node 0x0b [Pin Complex] wcaps 0x400081: Stereo
  Pincap 0x00001724: IN Detect
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x01a11020: [Jack] Mic at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0x2, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=03, enabled=1
Node 0x0c [Pin Complex] wcaps 0x400081: Stereo
  Pincap 0x00001724: IN Detect
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x21a11030: [Jack] Mic at Sep Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0x3, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=04, enabled=1
Node 0x0d [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x00000014: OUT Detect
  Pin Default 0x90110110: [Fixed] Speaker at Int N/A
    Conn = 1/8, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Connection: 3
     0x10* 0x11 0x17
Node 0x0e [Pin Complex] wcaps 0x400081: Stereo
  Pincap 0x00001724: IN Detect
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x01813040: [Jack] Line In at Ext Rear
    Conn = 1/8, Color = Blue
    DefAssociation = 0x4, Sequence = 0x0
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=05, enabled=1
Node 0x0f [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x00000014: OUT Detect
  Pin Default 0x40f000f0: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Connection: 3
     0x10 0x11 0x17*
Node 0x10 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out R/L
  Amp-Out caps: N/A
  Amp-Out vals: [0x79 0x79]
  Converter: stream=5, channel=0
  Power: setting=D0, actual=D0
  Delay: 13 samples
Node 0x11 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out R/L
  Amp-Out caps: N/A
  Amp-Out vals: [0x79 0x79]
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
  Pincap 0x00000030: IN OUT
  Pin Default 0x40f000f1: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x1
  Pin-ctls: 0x00:
  Connection: 1
     0x16
Node 0x15 [Audio Selector] wcaps 0x300101: Stereo
  Connection: 3
     0x10 0x11 0x17*
Node 0x16 [Audio Mixer] wcaps 0x200100: Mono
  Connection: 1
     0x15
Node 0x17 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals: [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97]
  Connection: 5
     0x10 0x11 0x14 0x1a 0x1b
Node 0x18 [Pin Complex] wcaps 0x40000b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals: [0x00 0x00]
  Pincap 0x00000020: IN
  Pin Default 0x40f000f2: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x2
  Pin-ctls: 0x00:
Node 0x19 [Pin Complex] wcaps 0x40000b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals: [0x00 0x00]
  Pincap 0x00000020: IN
  Pin Default 0x40f000f3: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x3
  Pin-ctls: 0x00:
Node 0x1a [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-Out vals: [0x00 0x00]
  Connection: 3
     0x0b* 0x0c 0x0e
Node 0x1b [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-Out vals: [0x00 0x00]
  Connection: 3
     0x0b* 0x0c 0x0e
Node 0x1c [Audio Selector] wcaps 0x30090d: Stereo Amp-Out R/L
  Amp-Out caps: ofs=0x00, nsteps=0x0f, stepsize=0x05, mute=1
  Amp-Out vals: [0x00 0x00]
  Connection: 4
     0x1a* 0x17 0x18 0x19
Node 0x1d [Audio Selector] wcaps 0x30090d: Stereo Amp-Out R/L
  Amp-Out caps: ofs=0x00, nsteps=0x0f, stepsize=0x05, mute=1
  Amp-Out vals: [0x80 0x80]
  Connection: 4
     0x1b* 0x17 0x18 0x19
Node 0x1e [Pin Complex] wcaps 0x400301: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x40f000f4: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x4
  Pin-ctls: 0x00:
  Connection: 1
     0x24
Node 0x1f [Pin Complex] wcaps 0x400701: Stereo Digital
  Pincap 0x00010010: OUT EAPD
  EAPD 0x0:
  Pin Default 0x40f000f5: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x5
  Pin-ctls: 0x00:
  Power: setting=D0, actual=D0
  Connection: 2
     0x24* 0x25
Node 0x20 [Pin Complex] wcaps 0x400301: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x40f000f6: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
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
  Amp-Out vals: [0x00]
Node 0x27 [Volume Knob Widget] wcaps 0x600000: Mono
  Volume-Knob: delta=1, steps=127, direct=0, val=127
  Connection: 2
     0x10 0x11
--endcollapse--

!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116, 7 Jun 5 21:44 /dev/snd/controlC0
crw-rw----+ 1 root audio 116, 6 Jun 5 21:44 /dev/snd/hwC0D0
crw-rw----+ 1 root audio 116, 5 Jun 5 21:52 /dev/snd/pcmC0D0c
crw-rw----+ 1 root audio 116, 4 Jun 5 21:47 /dev/snd/pcmC0D0p
crw-rw----+ 1 root audio 116, 3 Jun 5 21:44 /dev/snd/seq
crw-rw----+ 1 root audio 116, 2 Jun 5 21:44 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root 60 Jun 5 21:44 .
drwxr-xr-x 3 root root 180 Jun 5 21:44 ..
lrwxrwxrwx 1 root root 12 Jun 5 21:44 pci-0000:00:1b.0 -> ../controlC0

!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
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

Card hw:0 'Intel'/'HDA Intel at 0xfe938000 irq 16'
  Mixer name : 'IDT 92HD75B2X5'
  Components : 'HDA:111d7608,103c361a,00100102'
  Controls : 20
  Simple ctrls : 14
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 58 [91%] [-4.50dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
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
  Front Left: Playback 253 [99%] [0.40dB]
  Front Right: Playback 253 [99%] [0.40dB]
Simple mixer control 'Front Mic Jack Mode',0
  Capabilities: enum
  Items: 'Mic In' 'Line In'
  Item0: 'Mic In'
Simple mixer control 'Line Jack Mode',0
  Capabilities: enum
  Items: 'Mic In' 'Line In'
  Item0: 'Line In'
Simple mixer control 'Mic Jack Mode',0
  Capabilities: enum
  Items: 'Mic In' 'Line In'
  Item0: 'Mic In'
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 0 [0%] [0.00dB] [on]
  Front Right: Capture 0 [0%] [0.00dB] [on]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 0 [0%] [0.00dB] [off]
  Front Right: Capture 0 [0%] [0.00dB] [off]
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Mic' 'Front Mic' 'Line'
  Item0: 'Mic'
Simple mixer control 'Input Source',1
  Capabilities: cenum
  Items: 'Mic' 'Front Mic' 'Line'
  Item0: 'Mic'
Simple mixer control 'Mux',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 3
  Front Left: Capture 0 [0%] [0.00dB]
  Front Right: Capture 0 [0%] [0.00dB]
Simple mixer control 'Mux',1
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 3
  Front Left: Capture 0 [0%] [0.00dB]
  Front Right: Capture 0 [0%] [0.00dB]
Simple mixer control 'PC Beep',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 3
  Mono: Playback 0 [0%] [-18.00dB] [off]

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
  comment.type ENUMERATED
  comment.count 1
  comment.item.0 'Mic In'
  comment.item.1 'Line In'
  iface MIXER
  name 'Line Jack Mode'
  value 2
 }
 control.6 {
  comment.access 'read write'
  comment.type BOOLEAN
  comment.count 1
  iface MIXER
  name 'PC Beep Playback Switch'
  value false
 }
 control.7 {
  comment.access 'read write'
  comment.type INTEGER
  comment.count 1
  comment.range '0 - 3'
  comment.dbmin -1800
  comment.dbmax 0
  iface MIXER
  name 'PC Beep Playback Volume'
  value 0
 }
 control.8 {
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
 control.9 {
  comment.access 'read write'
  comment.type BOOLEAN
  comment.count 2
  iface MIXER
  name 'Headphone Playback Switch'
  value.0 true
  value.1 true
 }
 control.10 {
  comment.access 'read write'
  comment.type INTEGER
  comment.count 2
  comment.range '0 - 15'
  comment.dbmin 0
  comment.dbmax 2250
  iface MIXER
  name 'Capture Volume'
  value.0 0
  value.1 0
 }
 control.11 {
  comment.access 'read write'
  comment.type BOOLEAN
  comment.count 2
  iface MIXER
  name 'Capture Switch'
  value.0 true
  value.1 true
 }
 control.12 {
  comment.access 'read write'
  comment.type INTEGER
  comment.count 2
  comment.range '0 - 15'
  comment.dbmin 0
  comment.dbmax 2250
  iface MIXER
  name 'Capture Volume'
  index 1
  value.0 0
  value.1 0
 }
 control.13 {
  comment.access 'read write'
  comment.type BOOLEAN
  comment.count 2
  iface MIXER
  name 'Capture Switch'
  index 1
  value.0 false
  value.1 false
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
  value.0 0
  value.1 0
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
  value.0 0
  value.1 0
 }
 control.16 {
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
 control.17 {
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
 control.18 {
  comment.access 'read write'
  comment.type INTEGER
  comment.count 1
  comment.range '0 - 64'
  comment.dbmin -4800
  comment.dbmax 0
  iface MIXER
  name 'Master Playback Volume'
  value 58
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
  comment.access 'read write user'
  comment.type INTEGER
  comment.count 2
  comment.range '0 - 255'
  comment.tlv '0000000100000008ffffec1400000014'
  comment.dbmin -5100
  comment.dbmax 0
  iface MIXER
  name 'PCM Playback Volume'
  value.0 253
  value.1 253
 }
}
--endcollapse--

!!All Loaded Modules
!!------------------

Module
michael_mic
arc4
aes_i586
aes_generic
binfmt_misc
rfcomm
sco
bridge
stp
ppdev
bnep
l2cap
dm_crypt
snd_hda_codec_idt
snd_hda_intel
snd_hda_codec
snd_hwdep
snd_pcm_oss
snd_mixer_oss
snd_pcm
joydev
snd_seq_dummy
snd_seq_oss
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
snd_seq
uvcvideo
snd_timer
snd_seq_device
btusb
lib80211_crypt_tkip
snd
videodev
bluetooth
psmouse
lp
wl
soundcore
serio_raw
v4l1_compat
snd_page_alloc
lib80211
parport
fbcon
tileblit
font
bitblit
softcursor
vga16fb
vgastate
usbhid
hid
i915
drm_kms_helper
drm
i2c_algo_bit
intel_agp
video
sky2
agpgart
output

!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x0a 0x0121101f
0x0b 0x01a11020
0x0c 0x21a11030
0x0d 0x90110110
0x0e 0x90a7012e
0x0f 0x40f000f0
0x14 0x40f000f1
0x18 0x40f000f2
0x19 0x40f000f3
0x1e 0x40f000f4
0x1f 0x40f000f5
0x20 0x40f000f6

/sys/class/sound/hwC0D0/driver_pin_configs:
0x0f 0x40f000f0
0x19 0x40f000f3
0x0e 0x01813040

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:

!!ALSA/HDA dmesg
!!------------------

[ 18.779627] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input9
[ 19.212309] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 19.212846] HDA Intel 0000:00:1b.0: setting latency timer to 64
[ 19.384998] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input10
[ 19.406429] input: HDA Intel Line In at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[ 19.406941] input: HDA Intel Mic at Sep Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[ 19.407443] input: HDA Intel Mic at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[ 19.407954] input: HDA Intel HP Out at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[ 19.450851] EXT4-fs (sda5): mounted filesystem with ordered data mode

ProblemType: Bug
DistroRelease: Ubuntu 10.04
Package: alsa-base 1.0.22.1+dfsg-0ubuntu3
ProcVersionSignature: Ubuntu 2.6.32-21.32-generic 2.6.32.11+drm33.2
Uname: Linux 2.6.32-21-generic i686
NonfreeKernelModules: wl
AlsaVersion: Advanced Linux Sound Architecture Driver Version 1.0.21.
AplayDevices:
 **** List of PLAYBACK Hardware Devices ****
 card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
   Subdevices: 0/1
   Subdevice #0: subdevice #0
Architecture: i386
ArecordDevices:
 **** List of CAPTURE Hardware Devices ****
 card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
   Subdevices: 2/2
   Subdevice #0: subdevice #0
   Subdevice #1: subdevice #1
AudioDevicesInUse:
 USER PID ACCESS COMMAND
 /dev/snd/controlC0: marcos 1424 F.... pulseaudio
 /dev/snd/pcmC0D0p: marcos 1424 F...m pulseaudio
Card0.Amixer.info:
 Card hw:0 'Intel'/'HDA Intel at 0xfe938000 irq 16'
   Mixer name : 'IDT 92HD75B2X5'
   Components : 'HDA:111d7608,103c361a,00100102'
   Controls : 20
   Simple ctrls : 14
Date: Sat Jun 5 21:54:07 2010
EcryptfsInUse: Yes
InstallationMedia: Ubuntu-Netbook 10.04 "Lucid Lynx" - Release i386 (20100429.4)
PackageArchitecture: all
ProcEnviron:
 LANGUAGE=pt_BR:pt:en
 LANG=pt_BR.utf8
 SHELL=/bin/bash
SourcePackage: alsa-driver
dmi.bios.date: 05/11/2009
dmi.bios.vendor: Hewlett-Packard
dmi.bios.version: 361A0 Ver. F.13
dmi.board.name: 361A
dmi.board.vendor: Hewlett-Packard
dmi.board.version: KBC Version 02.11
dmi.chassis.type: 10
dmi.chassis.vendor: Hewlett-Packard
dmi.modalias: dmi:bvnHewlett-Packard:bvr361A0Ver.F.13:bd05/11/2009:svnHewlett-Packard:pnHPMini1000NetbookPC:pvrB.12:rvnHewlett-Packard:rn361A:rvrKBCVersion02.11:cvnHewlett-Packard:ct10:cvr:
dmi.product.name: HP Mini 1000 Netbook PC
dmi.product.version: B.12
dmi.sys.vendor: Hewlett-Packard
```

---

### Post by Bucky Ball on 2010-06-05
Applications->Sound and Video->Pulse Audio Device Chooser.

You should now have an icon for it in your toolbar. Click that and 'volume control'.

Get some sound going and you should see the stream come up in the volume window. Right click it and 'Move Stream ...'

You should see a list of available devices. Have a tweak and see if you can find the headphone hw and move stream to there.

Tell us how you go.

---

### Post by markinf on 2010-06-05
> **Bucky Ball said:**
> Applications->Sound and Video->Pulse Audio Device Chooser.

You should now have an icon for it in your toolbar. Click that and 'volume control'.

Get some sound going and you should see the stream come up in the volume window. Right click it and 'Move Stream ...'

You should see a list of available devices. Have a tweak and see if you can find the headphone hw and move stream to there.

Tell us how you go.
No luck ;/

---

### Post by Yellow Pasque on 2010-06-05
To get the jack sensing working properly:
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```
Copy/paste this line to the end of the file:
```
options snd-hda-intel model=hp-m4
```
Save. Quit. Reboot. If that doesn't work, you may need to upgrade ALSA: [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

---

### Post by lidex on 2010-06-05
May just need to tweak your mixer settings, which tend to get reset on upgrades.
Try gnome-alsamixer.
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

---

### Post by markinf on 2010-06-05
> **Temüjin said:**
> To get the jack sensing working properly:
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```
Copy/paste this line to the end of the file:
```
options snd-hda-intel model=hp-m4
```
Save. Quit. Reboot. If that doesn't work, you may need to upgrade ALSA: [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

I already did that before posting here. Changed to all values possible on my codec section (wildcard).

Also installed alsa 1.0.23 (latest) and had the same result.

> **lidex said:**
> May just need to tweak your mixer settings, which tend to get reset on upgrades.
Try gnome-alsamixer.
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

No luck here :/

---

### Post by markinf on 2010-06-05
bump

---

### Post by lidex on 2010-06-05
What do you have in sound preferences, output tab, connector drop-down?

---

