---
title: "VT1708BCE - Audio not working"
date: 2011-06-26
forum: Multimedia Software
---

### Post by eduardoboca on 2011-06-26
Hello. I'm having problems configuring chipset VT1708BCE on an Ubuntu 10.04 box. I'm using alsa 1.0.23.

First I installed Ubuntu 10.04 (alsa 1.0.21). With this configuration, the audio (front and rear) works. However, none of the microphones (front and rear) work. 

Then I upgraded alsa to version 1.0.23, and the result was that the rear audio AND MICROPHONE did work, but the front panel (audio and microphone) stopped working.

Below are the results of the alsa-info.sh script. From that I can see (search for "control.20")  that the volume on 'Front Mic Boost Capture Volume' is set to 0. I've tried to change the volume using alsamixer and gnome-volume, but none of them seem to work.

Does anyone have a clue of what could be wrong? Thank you very much!

!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Sun Jun 26 18:49:46 UTC 2011


!!Linux Distribution
!!------------------

Ubuntu 10.04 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.04 LTS"


!!DMI Information
!!---------------

Manufacturer:      BIOSTAR Group
Product Name:      N68S3B
Product Version:    


!!Kernel Information
!!------------------

Kernel release:    2.6.32-32-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.23
Library version:    1.0.22
Utilities version:  1.0.22


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
                      HDA NVidia at 0xdfff8000 irq 21


!!PCI Soundcards installed in the system
!!--------------------------------------

00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

00:05.0 0403: 10de:03f0 (rev a2)
    Subsystem: 1565:810a


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
snd-hda-intel: model=auto


!!Loaded sound module options
!!--------------------------

!!Module: snd_hda_intel
    bdl_pos_adj : 32,-1,-1,-1,-1,-1,-1,-1
    beep_mode : 1,1,1,1,1,1,1,1
    enable : Y,Y,Y,Y,Y,Y,Y,Y
    enable_msi : -1
    id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
    index : -1,-1,-1,-1,-1,-1,-1,-1
    model : auto,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
    patch : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
    position_fix : 0,0,0,0,0,0,0,0
    power_save : 0
    power_save_controller : Y
    probe_mask : -1,-1,-1,-1,-1,-1,-1,-1
    probe_only : 0,0,0,0,0,0,0,0
    single_cmd : N


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: VIA VT1708BCE
Address: 0
Function Id: 0x1
Vendor Id: 0x1106e721
Subsystem Id: 0x1565810a
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
Node 0x10 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Control: name="Front Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Device: name="VT1708BCE Analog", type="Audio", device=0
  Amp-Out caps: ofs=0x2a, nsteps=0x2a, stepsize=0x05, mute=0
  Amp-Out vals:  [0x2a 0x2a]
  Converter: stream=0, channel=0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
Node 0x11 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Amp-Out caps: ofs=0x2a, nsteps=0x2a, stepsize=0x05, mute=0
  Amp-Out vals:  [0x2a 0x2a]
  Converter: stream=0, channel=0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3
  Power: setting=D3, actual=D3
Node 0x12 [Audio Output] wcaps 0x611: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
Node 0x13 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Control: name="Capture Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Capture Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Device: name="VT1708BCE Analog", type="Audio", device=0
  Amp-In caps: ofs=0x0b, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x1f 0x1f]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3
  Power: setting=D3, actual=D3
  Connection: 1
     0x17
Node 0x14 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Control: name="Capture Volume", index=1, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Capture Switch", index=1, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x0b, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x00 0x00]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3
  Power: setting=D3, actual=D3
  Connection: 1
     0x1e
Node 0x15 [Audio Output] wcaps 0x611: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
Node 0x16 [Audio Mixer] wcaps 0x20050b: Stereo Amp-In
  Control: name="Master Front Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Master Front Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Control: name="Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Control: name="Front Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=4, ofs=0
  Control: name="Front Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=4, ofs=0
  Control: name="Line Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=3, ofs=0
  Control: name="Line Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=3, ofs=0
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x1e 0x1e] [0x00 0x00] [0x80 0x80] [0x00 0x00] [0x00 0x00] [0x97 0x97] [0x97 0x97]
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
  Connection: 7
     0x10 0x1f 0x1a 0x1b 0x1e 0x1d 0x25
Node 0x17 [Audio Selector] wcaps 0x300501: Stereo
  Control: name="Input Source", index=0, device=0
  Power states:  D0 D1 D2 D3
  Power: setting=D3, actual=D3
  Connection: 6
     0x1f 0x1a 0x1b 0x1e* 0x1d 0x16
Node 0x18 [Audio Selector] wcaps 0x30050d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Power states:  D0 D1 D2 D3
  Power: setting=D3, actual=D3
  Connection: 1
     0x11
Node 0x19 [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x00000014: OUT Detect
  Pin Default 0x410110f2: [N/A] Line Out at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x2
  Pin-ctls: 0x00:
  Unsolicited: tag=04, enabled=1
  Power states:  D0 D1 D2 D3
  Power: setting=D3, actual=D3
  Connection: 1
     0x18
Node 0x1a [Pin Complex] wcaps 0x400581: Stereo
  Control: name="Mic Boost Capture Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Smart 5.1", index=0, device=0
  Pincap 0x00002334: IN OUT Detect
    Vref caps: HIZ 50 100
  Pin Default 0x01a19036: [Jack] Mic at Ext Rear
    Conn = 1/8, Color = Pink
    DefAssociation = 0x3, Sequence = 0x6
  Pin-ctls: 0x21: IN VREF_50
  Unsolicited: tag=04, enabled=1
  Power states:  D0 D1 D2 D3
  Power: setting=D3, actual=D3
  Connection: 1
     0x26
Node 0x1b [Pin Complex] wcaps 0x400581: Stereo
  Control: name="Independent HP", index=0, device=0
  Control: name="Smart 5.1", index=0, device=0
  Pincap 0x00002334: IN OUT Detect
    Vref caps: HIZ 50 100
  Pin Default 0x0181303e: [Jack] Line In at Ext Rear
    Conn = 1/8, Color = Blue
    DefAssociation = 0x3, Sequence = 0xe
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=04, enabled=1
  Power states:  D0 D1 D2 D3
  Power: setting=D3, actual=D3
  Connection: 1
     0x18
Node 0x1c [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Control: name="Front Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0001001c: OUT HP EAPD Detect
  EAPD 0x2: EAPD
  Pin Default 0x01014010: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Green
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=04, enabled=1
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
  Connection: 1
     0x16
Node 0x1d [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Control: name="Headphone Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Independent HP", index=0, device=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000233c: IN OUT HP Detect
    Vref caps: HIZ 50 100
  Pin Default 0x0221401f: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Green
    DefAssociation = 0x1, Sequence = 0xf
  Pin-ctls: 0xc0: OUT HP VREF_HIZ
  Unsolicited: tag=05, enabled=1
  Power states:  D0 D1 D2 D3
  Power: setting=D3, actual=D3
  Connection: 2
     0x16* 0x25
Node 0x1e [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Control: name="Front Mic Boost Capture Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Smart 5.1", index=0, device=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000233c: IN OUT HP Detect
    Vref caps: HIZ 50 100
  Pin Default 0x02a19038: [Jack] Mic at Ext Front
    Conn = 1/8, Color = Pink
    DefAssociation = 0x3, Sequence = 0x8
  Pin-ctls: 0x21: IN VREF_50
  Unsolicited: tag=04, enabled=1
  Power states:  D0 D1 D2 D3
  Power: setting=D3, actual=D3
  Connection: 2
     0x16 0x25*
Node 0x1f [Pin Complex] wcaps 0x400401: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x503701f7: [N/A] CD at Int N/A
    Conn = Analog, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x7
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
Node 0x20 [Pin Complex] wcaps 0x400701: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x474411f0: [N/A] SPDIF Out at Ext Rear Panel
    Conn = RCA, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
  Connection: 1
     0x12
Node 0x21 [Pin Complex] wcaps 0x400701: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x47c421f0: [N/A] SPDIF In at Ext Rear Panel
    Conn = RCA, Color = Grey
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
  Connection: 1
     0x15
Node 0x22 [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x00000014: OUT Detect
  Pin Default 0x410160f1: [N/A] Line Out at Ext Rear
    Conn = 1/8, Color = Orange
    DefAssociation = 0xf, Sequence = 0x1
  Pin-ctls: 0x00:
  Unsolicited: tag=04, enabled=1
  Power states:  D0 D1 D2 D3
  Power: setting=D3, actual=D3
  Connection: 1
     0x26
Node 0x23 [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x00000014: OUT Detect
  Pin Default 0x410120f4: [N/A] Line Out at Ext Rear
    Conn = 1/8, Color = Grey
    DefAssociation = 0xf, Sequence = 0x4
  Pin-ctls: 0x00:
  Unsolicited: tag=04, enabled=1
  Power states:  D0 D1 D2 D3
  Power: setting=D3, actual=D3
  Connection: 1
     0x27
Node 0x24 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Amp-Out caps: ofs=0x2a, nsteps=0x2a, stepsize=0x05, mute=0
  Amp-Out vals:  [0x2a 0x2a]
  Converter: stream=0, channel=0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3
  Power: setting=D3, actual=D3
Node 0x25 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Control: name="Headphone Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x2a, nsteps=0x2a, stepsize=0x05, mute=0
  Amp-Out vals:  [0x2a 0x2a]
  Converter: stream=0, channel=0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
Node 0x26 [Audio Selector] wcaps 0x30050d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Power states:  D0 D1 D2 D3
  Power: setting=D3, actual=D3
  Connection: 1
     0x24
Node 0x27 [Audio Selector] wcaps 0x30050d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
  Connection: 1
     0x25
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----  1 root audio 116,  0 Jun 26 14:32 /dev/snd/controlC0
crw-rw----  1 root audio 116,  4 Jun 26 14:32 /dev/snd/hwC0D0
crw-rw----  1 root audio 116, 24 Jun 26 15:47 /dev/snd/pcmC0D0c
crw-rw----  1 root audio 116, 16 Jun 26 15:48 /dev/snd/pcmC0D0p
crw-rw----  1 root audio 116,  1 Jun 26 14:32 /dev/snd/seq
crw-rw----  1 root audio 116, 33 Jun 26 14:32 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Jun 26 14:32 .
drwxr-xr-x 3 root root 180 Jun 26 14:32 ..
lrwxrwxrwx 1 root root  12 Jun 26 14:32 pci-0000:00:05.0 -> ../controlC0


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: VT1708BCE Analog [VT1708BCE Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: VT1708BCE Analog [VT1708BCE Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [NVidia]

Card hw:0 'NVidia'/'HDA NVidia at 0xdfff8000 irq 21'
  Mixer name    : 'VIA VT1708BCE'
  Components    : 'HDA:1106e721,1565810a,00100100'
  Controls      : 22
  Simple ctrls  : 14
Simple mixer control 'Master Front',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 30 [97%] [10.50dB] [on]
  Front Right: Playback 30 [97%] [10.50dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 253 [99%] [0.40dB]
  Front Right: Playback 253 [99%] [0.40dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 42
  Mono:
  Front Left: Playback 42 [100%] [0.00dB] [on]
  Front Right: Playback 42 [100%] [0.00dB] [on]
Simple mixer control 'Front Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [on]
  Front Right: Playback 0 [0%] [-34.50dB] [on]
Simple mixer control 'Front Mic Boost',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 3
  Front Left: Capture 0 [0%] [0.00dB]
  Front Right: Capture 0 [0%] [0.00dB]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [on]
  Front Right: Playback 0 [0%] [-34.50dB] [on]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Mic Boost',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 3
  Front Left: Capture 3 [100%] [30.75dB]
  Front Right: Capture 3 [100%] [30.75dB]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 31 [100%] [30.00dB] [on]
  Front Right: Capture 31 [100%] [30.00dB] [on]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 0 [0%] [-16.50dB] [on]
  Front Right: Capture 0 [0%] [-16.50dB] [on]
Simple mixer control 'Independent HP',0
  Capabilities: enum
  Items: 'OFF' 'ON'
  Item0: 'OFF'
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Stereo Mixer' 'Mic' 'Front Mic' 'Line'
  Item0: 'Front Mic'
Simple mixer control 'Smart 5.1',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]


!!Alsactl output
!!-------------

--startcollapse--
state.NVidia {
    control.1 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'Master Front Playback Volume'
        value.0 30
        value.1 30
    }
    control.2 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Master Front Playback Switch'
        value.0 true
        value.1 true
    }
    control.3 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 42'
        comment.dbmin -6300
        comment.dbmax 0
        iface MIXER
        name 'Front Playback Volume'
        value.0 42
        value.1 42
    }
    control.4 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Front Playback Switch'
        value.0 true
        value.1 true
    }
    control.7 {
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
    control.8 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Mic Playback Switch'
        value.0 false
        value.1 false
    }
    control.9 {
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
    control.10 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Front Mic Playback Switch'
        value.0 true
        value.1 true
    }
    control.11 {
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
    control.12 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Line Playback Switch'
        value.0 true
        value.1 true
    }
    control.13 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 1
        comment.item.0 OFF
        comment.item.1 ON
        iface MIXER
        name 'Independent HP'
        value OFF
    }
    control.14 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Smart 5.1'
        value false
    }
    control.15 {
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
    control.16 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Capture Switch'
        value.0 true
        value.1 true
    }
    control.17 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -1650
        comment.dbmax 3000
        iface MIXER
        name 'Capture Volume'
        index 1
        value.0 0
        value.1 0
    }
    control.18 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Capture Switch'
        index 1
        value.0 true
        value.1 true
    }
    control.19 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 3'
        comment.dbmin 0
        comment.dbmax 3075
        iface MIXER
        name 'Mic Boost Capture Volume'
        value.0 3
        value.1 3
    }
    control.20 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 3'
        comment.dbmin 0
        comment.dbmax 3075
        iface MIXER
        name 'Front Mic Boost Capture Volume'
        value.0 0
        value.1 0
    }
    control.21 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 1
        comment.item.0 'Stereo Mixer'
        comment.item.1 Mic
        comment.item.2 'Front Mic'
        comment.item.3 Line
        iface MIXER
        name 'Input Source'
        value 'Front Mic'
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
        value.0 253
        value.1 253
    }
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
snd_hda_codec_via
snd_hda_intel
snd_hda_codec
snd_hwdep
snd_pcm_oss
snd_mixer_oss
snd_pcm
snd_seq_dummy
snd_seq_oss
binfmt_misc
fbcon
tileblit
font
bitblit
softcursor
snd_seq_midi
snd_rawmidi
vga16fb
vgastate
snd_seq_midi_event
snd_seq
snd_timer
snd_seq_device
nouveau
ttm
snd
drm_kms_helper
drm
ppdev
soundcore
snd_page_alloc
parport_pc
agpgart
i2c_algo_bit
i2c_nforce2
lp
parport
usbhid
hid
pata_amd
forcedeth
sata_nv


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x19 0x410110f2
0x1a 0x01a19036
0x1b 0x0181303e
0x1c 0x01014010
0x1d 0x0221401f
0x1e 0x02a19038
0x1f 0x503701f7
0x20 0x474411f0
0x21 0x47c421f0
0x22 0x410160f1
0x23 0x410120f4

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:


!!ALSA/HDA dmesg
!!------------------

[   11.310034] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 21
[   11.310040] HDA Intel 0000:00:05.0: PCI INT B -> Link[LAZA] -> GSI 21 (level, low) -> IRQ 21
[   11.310043] hda_intel: Disable MSI for Nvidia chipset
[   11.310065] HDA Intel 0000:00:05.0: setting latency timer to 64
[   20.756355] eth0: no IPv6 routers present

---

### Post by eduardoboca on 2011-06-28
Hello? Any clue?

---

### Post by baturay on 2011-07-13
I've got a VIA VT1708S and the same problem. This solved my problem:
[http://excid3.com/blog/changing-the-ubuntu-10-04-audio-channel-control/ ]("http://excid3.com/blog/changing-the-ubuntu-10-04-audio-channel-control/")

also look here:
[http://ubuntuforums.org/showthread.php?p=8243843](http://ubuntuforums.org/showthread.php?p=8243843)[LEFT]


[/LEFT]

---

### Post by lidex on 2011-07-14
Part of your problem is your alsa upgrade didn't turn out:
```
!!ALSA Version
!!------------

Driver version: 1.0.23
Library version: 1.0.22
Utilities version: 1.0.22
```
Use the alsa upgade link in my sig to get v 1.0.24

---

### Post by simonderricutt on 2011-08-17
I installed linux-backports-modules-alsa-lucid-generic using synaptic. This put in a full version of alsa 1.0.23 and fixed the mis-reading of my sound chip type. Sound currently working. I have an NVidia MCP61 chipset, which needs the HDA-Intel driver.
Skype now has sound OK, though still problems with Twinkle.

---

