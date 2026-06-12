---
title: "Not all Audio-Jacks working on Shuttle SG41J1 v2"
date: 2010-11-10
forum: Multimedia Software
---

### Post by b4ss00k4 on 2010-11-10
Hi!


I also posted this in launchpad under [https://answers.launchpad.net/ubuntu/+question/132972](https://answers.launchpad.net/ubuntu/+question/132972). I got no response, so I try it here again:

 I just got my new Shuttle SG41J1 v2. Everything works fine under  10.10 except audio. I can hear sound at the headphone-jack on the  frontpanel but the jack on the rear isn't working. I tried different  models in /etc/modprobe.d/alsa-base.conf (3stack, 5stack,  test), nothing helped. All channels in alsamixer are unmuted and the  sliders turned up. In the output of alsa-info.sh I can see Nodes for all  jacks (Speaker, Mic and Line-In at Ext-Rear for example) but alsamixer  and all other mixer-applications I tried shows only Master, PCM, Front  Mic, Line, Mic and Aux (all in the Playback section). Also I found  nothing in /usr/share/doc/alsa-base/driver/HD-Audio-Models.txt.gz about my Codec "IDT ID 76c1". Any ideas? I googled for many hours but nothing I tried seems to work.
 

Here is the output of alsa-info.sh:
```
!!################################
!!ALSA Information Script v 0.4.59
!!################################
 !!Script ran on: Sun Nov  7 11:24:23 UTC 2010
 !!Linux Distribution
!!------------------
 Ubuntu 10.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.10"
 !!DMI Information
!!---------------
 Manufacturer:      Shuttle Inc
Product Name:      SG41
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
                      HDA Intel at 0xfeaf8000 irq 43
 !!PCI Soundcards installed in the system
!!--------------------------------------
 00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
 !!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------
 00:1b.0 0403: 8086:27d8 (rev 01)
 Subsystem: 1297:4001
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
 bdl_pos_adj : 1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
 beep_mode : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
 enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
 enable_msi : -1
 id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
 index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
 model : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
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
 Codec: IDT ID 76c1
Address: 0
Function Id: 0x1
Vendor Id: 0x111d76c1
Subsystem Id: 0x12974001
Revision Id: 0x100102
No Modem Function Group found
Default PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
Default Amp-Out caps: ofs=0x7f, nsteps=0x7f, stepsize=0x02, mute=1
GPIO: io=5, o=0, i=0, unsolicited=1, wake=1
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[2]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[3]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[4]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Node 0x0a [Pin Complex] wcaps 0x400583: Stereo Amp-In
  Amp-In caps: N/A
  Amp-In vals:  [0x03 0x03]
  Pincap 0x0001173c: IN OUT HP EAPD Detect
    Vref caps: HIZ 50 GRD 80
  EAPD 0x2: EAPD
  Pin Default 0x0221401f: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Green
    DefAssociation = 0x1, Sequence = 0xf
  Pin-ctls: 0xc0: OUT HP VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 4
     0x15* 0x16 0x1e 0x17
Node 0x0b [Pin Complex] wcaps 0x400583: Stereo Amp-In
  Amp-In caps: N/A
  Amp-In vals:  [0x03 0x03]
  Pincap 0x00011734: IN OUT EAPD Detect
    Vref caps: HIZ 50 GRD 80
  EAPD 0x2: EAPD
  Pin Default 0x02a19021: [Jack] Mic at Ext Front
    Conn = 1/8, Color = Pink
    DefAssociation = 0x2, Sequence = 0x1
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 4
     0x15* 0x16 0x1e 0x17
Node 0x0c [Pin Complex] wcaps 0x400583: Stereo Amp-In
  Amp-In caps: N/A
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00010034: IN OUT EAPD Detect
  EAPD 0x2: EAPD
  Pin Default 0x0181302e: [Jack] Line In at Ext Rear
    Conn = 1/8, Color = Blue
    DefAssociation = 0x2, Sequence = 0xe
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 4
     0x15* 0x16 0x1e 0x17
Node 0x0d [Pin Complex] wcaps 0x400583: Stereo Amp-In
  Amp-In caps: N/A
  Amp-In vals:  [0x03 0x03]
  Pincap 0x0001003c: IN OUT HP EAPD Detect
  EAPD 0x2: EAPD
  Pin Default 0x01114010: [Jack] Speaker at Ext Rear
    Conn = 1/8, Color = Green
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0xc0: OUT HP
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 4
     0x15 0x16 0x1e* 0x17
Node 0x0e [Pin Complex] wcaps 0x400583: Stereo Amp-In
  Amp-In caps: N/A
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00011734: IN OUT EAPD Detect
    Vref caps: HIZ 50 GRD 80
  EAPD 0x2: EAPD
  Pin Default 0x01a19020: [Jack] Mic at Ext Rear
    Conn = 1/8, Color = Pink
    DefAssociation = 0x2, Sequence = 0x0
  Pin-ctls: 0x00: VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 4
     0x15* 0x16 0x1e 0x17
Node 0x0f [Pin Complex] wcaps 0x400583: Stereo Amp-In
  Amp-In caps: N/A
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00010034: IN OUT EAPD Detect
  EAPD 0x2: EAPD
  Pin Default 0x90970122: [Fixed] Aux at Int N/A
    Conn = Analog, Color = Unknown
    DefAssociation = 0x2, Sequence = 0x2
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 4
     0x15* 0x16 0x1e 0x17
Node 0x10 [Pin Complex] wcaps 0x400583: Stereo Amp-In
  Amp-In caps: N/A
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00010034: IN OUT EAPD Detect
  EAPD 0x2: EAPD
  Pin Default 0x400000f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 4
     0x15* 0x16 0x1e 0x17
Node 0x11 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x12 [Pin Complex] wcaps 0x400401: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x400000f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00:
  Power: setting=D0, actual=D0
Node 0x13 [Pin Complex] wcaps 0x400403: Stereo Amp-In
  Amp-In caps: N/A
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00000020: IN
  Pin Default 0x400000f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00:
  Power: setting=D0, actual=D0
Node 0x14 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x15 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out R/L
  Control: name="Master Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Master Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Device: name="HDA Generic", type="Audio", device=0
  Amp-Out caps: N/A
  Amp-Out vals:  [0x59 0x59]
  Converter: stream=0, channel=0
  Power: setting=D0, actual=D0
  Delay: 13 samples
Node 0x16 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out R/L
  Amp-Out caps: N/A
  Amp-Out vals:  [0xff 0xff]
  Converter: stream=0, channel=0
  Power: setting=D0, actual=D0
  Delay: 13 samples
Node 0x17 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out R/L
  Amp-Out caps: N/A
  Amp-Out vals:  [0xff 0xff]
  Converter: stream=0, channel=0
  Power: setting=D0, actual=D0
  Delay: 13 samples
Node 0x18 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x19 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x1a [Audio Input] wcaps 0x1d0541: Stereo
  Device: name="HDA Generic", type="Audio", device=0
  Converter: stream=0, channel=0
  SDI-Select: 0
  Power: setting=D0, actual=D0
  Delay: 13 samples
  Connection: 1
     0x20
  Processing caps: benign=0, ncoeff=0
Node 0x1b [Audio Input] wcaps 0x1d0541: Stereo
  Converter: stream=0, channel=0
  SDI-Select: 0
  Power: setting=D0, actual=D0
  Delay: 13 samples
  Connection: 1
     0x21
  Processing caps: benign=0, ncoeff=0
Node 0x1c [Beep Generator Widget] wcaps 0x70040c: Mono Amp-Out
  Amp-Out caps: ofs=0x03, nsteps=0x03, stepsize=0x17, mute=1
  Amp-Out vals:  [0x00]
  Power: setting=D0, actual=D0
Node 0x1d [Audio Mixer] wcaps 0x20050b: Stereo Amp-In
  Control: name="Front Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Front Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Line Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Control: name="Line Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Control: name="Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=1, ofs=0
  Control: name="Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=1, ofs=0
  Control: name="Aux Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Aux Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x19 0x19] [0x19 0x19] [0x19 0x19] [0x97 0x97] [0x97 0x97]
  Power: setting=D0, actual=D0
  Connection: 5
     0x28 0x29 0x2a 0x2b 0x12
Node 0x1e [Audio Selector] wcaps 0x30050d: Stereo Amp-Out
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x00 0x00]
  Power: setting=D0, actual=D0
  Connection: 1
     0x1d
Node 0x1f [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x20 [Audio Selector] wcaps 0x300d0d: Stereo Amp-Out R/L
  Amp-Out caps: ofs=0x00, nsteps=0x0f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x0f 0x0f]
  Power: setting=D0, actual=D0
  Connection: 10
     0x1d* 0x0a 0x0b 0x0c 0x0d 0x0e 0x0f 0x10 0x12 0x13
Node 0x21 [Audio Selector] wcaps 0x300d0d: Stereo Amp-Out R/L
  Amp-Out caps: ofs=0x00, nsteps=0x0f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x80 0x80]
  Power: setting=D0, actual=D0
  Connection: 10
     0x1d* 0x0a 0x0b 0x0c 0x0d 0x0e 0x0f 0x10 0x12 0x13
Node 0x22 [Pin Complex] wcaps 0x400781: Stereo Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x400000f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 1
     0x25
Node 0x23 [Pin Complex] wcaps 0x400701: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x98560160: [Fixed] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x6, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Power: setting=D0, actual=D0
  Connection: 1
     0x26
Node 0x24 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x25 [Audio Output] wcaps 0x4061d: Stereo Digital Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Power: setting=D0, actual=D0
  Delay: 4 samples
Node 0x26 [Audio Output] wcaps 0x4061d: Stereo Digital Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Power: setting=D0, actual=D0
  Delay: 4 samples
Node 0x27 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x28 [Audio Selector] wcaps 0x300501: Stereo
  Power: setting=D0, actual=D0
  Connection: 4
     0x0a 0x0b 0x0d 0x0f*
Node 0x29 [Audio Selector] wcaps 0x300501: Stereo
  Power: setting=D0, actual=D0
  Connection: 3
     0x0a 0x0e* 0x10
Node 0x2a [Audio Selector] wcaps 0x300501: Stereo
  Power: setting=D0, actual=D0
  Connection: 3
     0x0b 0x0c* 0x10
Node 0x2b [Audio Selector] wcaps 0x300501: Stereo
  Power: setting=D0, actual=D0
  Connection: 3
     0x15* 0x16 0x17
--endcollapse--
 !!ALSA Device nodes
!!-----------------
 crw-rw----+ 1 root audio 116, 7 Nov  7 12:18 /dev/snd/controlC0
crw-rw----+ 1 root audio 116, 6 Nov  7 12:18 /dev/snd/hwC0D0
crw-rw----+ 1 root audio 116, 5 Nov  7 12:19 /dev/snd/pcmC0D0c
crw-rw----+ 1 root audio 116, 4 Nov  7 12:19 /dev/snd/pcmC0D0p
crw-rw----+ 1 root audio 116, 3 Nov  7 12:18 /dev/snd/seq
crw-rw----+ 1 root audio 116, 2 Nov  7 12:18 /dev/snd/timer
 /dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Nov  7 12:18 .
drwxr-xr-x 3 root root 180 Nov  7 12:18 ..
lrwxrwxrwx 1 root root  12 Nov  7 12:18 pci-0000:00:1b.0 -> ../controlC0
 !!Aplay/Arecord output
!!------------
 APLAY
 **** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
 ARECORD
 **** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
 !!Amixer output
!!-------------
 !!-------Mixer controls for card 0 [Intel]
 Card hw:0 'Intel'/'HDA Intel at 0xfeaf8000 irq 43'
  Mixer name    : 'IDT ID 76c1'
  Components    : 'HDA:111d76c1,12974001,00100102'
  Controls      : 11
  Simple ctrls  : 6
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 127
  Mono:
  Front Left: Playback 89 [70%] [-28.50dB] [on]
  Front Right: Playback 89 [70%] [-28.50dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 252 [99%] [0.60dB]
  Front Right: Playback 252 [99%] [0.60dB]
Simple mixer control 'Front Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 25 [81%] [3.00dB] [on]
  Front Right: Playback 25 [81%] [3.00dB] [on]
Simple mixer control 'Line',0
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
  Front Left: Playback 25 [81%] [3.00dB] [on]
  Front Right: Playback 25 [81%] [3.00dB] [on]
Simple mixer control 'Aux',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 25 [81%] [3.00dB] [on]
  Front Right: Playback 25 [81%] [3.00dB] [on]
 !!Alsactl output
!!-------------
 --startcollapse--
state.Intel {
 control.1 {
  comment.access 'read write'
  comment.type BOOLEAN
  comment.count 2
  iface MIXER
  name 'Master Playback Switch'
  value.0 true
  value.1 true
 }
 control.2 {
  comment.access 'read write'
  comment.type INTEGER
  comment.count 2
  comment.range '0 - 127'
  comment.dbmin -9525
  comment.dbmax 0
  iface MIXER
  name 'Master Playback Volume'
  value.0 89
  value.1 89
 }
 control.3 {
  comment.access 'read write'
  comment.type BOOLEAN
  comment.count 2
  iface MIXER
  name 'Front Mic Playback Switch'
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
  name 'Front Mic Playback Volume'
  value.0 25
  value.1 25
 }
 control.5 {
  comment.access 'read write'
  comment.type BOOLEAN
  comment.count 2
  iface MIXER
  name 'Line Playback Switch'
  value.0 true
  value.1 true
 }
 control.6 {
  comment.access 'read write'
  comment.type INTEGER
  comment.count 2
  comment.range '0 - 31'
  comment.dbmin -3450
  comment.dbmax 1200
  iface MIXER
  name 'Line Playback Volume'
  value.0 25
  value.1 25
 }
 control.7 {
  comment.access 'read write'
  comment.type BOOLEAN
  comment.count 2
  iface MIXER
  name 'Mic Playback Switch'
  value.0 true
  value.1 true
 }
 control.8 {
  comment.access 'read write'
  comment.type INTEGER
  comment.count 2
  comment.range '0 - 31'
  comment.dbmin -3450
  comment.dbmax 1200
  iface MIXER
  name 'Mic Playback Volume'
  value.0 25
  value.1 25
 }
 control.9 {
  comment.access 'read write'
  comment.type BOOLEAN
  comment.count 2
  iface MIXER
  name 'Aux Playback Switch'
  value.0 true
  value.1 true
 }
 control.10 {
  comment.access 'read write'
  comment.type INTEGER
  comment.count 2
  comment.range '0 - 31'
  comment.dbmin -3450
  comment.dbmax 1200
  iface MIXER
  name 'Aux Playback Volume'
  value.0 25
  value.1 25
 }
 control.11 {
  comment.access 'read write user'
  comment.type INTEGER
  comment.count 2
  comment.range '0 - 255'
  comment.tlv '0000000100000008ffffec1400000014'
  comment.dbmin -5100
  comment.dbmax 0
  iface MIXER
  name 'PCM Playback Volume'
  value.0 252
  value.1 252
 }
}
--endcollapse--
 !!All Loaded Modules
!!------------------
 Module
parport_pc
ppdev
joydev
binfmt_misc
mt2266
snd_hda_codec_idt
i915
snd_hda_intel
drm_kms_helper
snd_hda_codec
drm
snd_hwdep
snd_pcm
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
snd_seq
dvb_usb_dib0700
dib7000p
dib0090
dib7000m
dib0070
dvb_usb
dib8000
snd_timer
snd_seq_device
rt2870sta
dvb_core
dib3000mc
usbhid
dibx000_common
crc_ccitt
snd
hid
psmouse
serio_raw
led_class
lp
i2c_algo_bit
video
soundcore
intel_agp
output
snd_page_alloc
parport
sky2
 !!Sysfs Files
!!-----------
 /sys/class/sound/hwC0D0/init_pin_configs:
0x0a 0x0221401f
0x0b 0x02a19021
0x0c 0x0181302e
0x0d 0x01114010
0x0e 0x01a19020
0x0f 0x90970122
0x10 0x400000f0
0x12 0x400000f0
0x13 0x400000f0
0x22 0x400000f0
0x23 0x98560160
 /sys/class/sound/hwC0D0/driver_pin_configs:
 /sys/class/sound/hwC0D0/user_pin_configs:
 /sys/class/sound/hwC0D0/init_verbs:
 !!ALSA/HDA dmesg
!!------------------
 [    6.429337] [drm] Initialized drm 1.1.0 20060810
[    6.444130] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    6.444215]   alloc irq_desc for 43 on node -1
[    6.444217]   alloc kstat_irqs on node -1
[    6.444229] HDA Intel 0000:00:1b.0: irq 43 for MSI/MSI-X
[    6.444258] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    6.549768] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16

```

---

### Post by b4ss00k4 on 2010-11-13
I got it! I used the ALSA HDA Analyser, played a little with various  switches and sliders (unmuted everything, assigned widget controls,  turned volumes up) and so on. Finally the following changes in Node 0x0d  (Speaker) did it: In the Connection List Audio Output [0x15] had to be  activated and In Widget Control I marked HP and OUT as active. I haven't  tested the Mic- and Line-In-Jacks, but the Output-Jacks (Headphone on  the front and Speaker on the rear) are working now.
But now I have another problem: How do I save these changes permanently?  I figured out, that HDA Analyser changed a few things in /proc/asound/card0/codec#0. alsactl store didn't help, after rebooting the changes are gone and I have to tweak the settings again using HDA Analyzer.

---

### Post by b4ss00k4 on 2010-11-21
Anyone? How can I get my new codec working permanently?

---

### Post by dipshat on 2010-11-28
I have this exact same problem.  I will let you know if I figure it out.  You do the same.

Dipshat

---

### Post by dipshat on 2010-11-28
From what I have read our sound card isn't properly supported with alsa.  There are alot of laptops that have the same problem that we are having.  It has to do with the pin routing from what I read.  I did however find tool to set the parameters you are changing with hda analyzer at boot.  But I don't know how to use it so I will have to do more reading.  Hope this helps.   


See:  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/393523]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/393523")

Look for the hda-verb comment about 3/4 down

---

### Post by b4ss00k4 on 2010-11-29
Nice, I'll try it later this day.

---

### Post by b4ss00k4 on 2010-11-29
Thanks for your hint, it's working! I downloaded HDA Verb from kernel.org, compiled it and copied the executable to /usr/local/bin. Wasn't hard to find the right options for HDA VERB. In my case
```
sudo hda-verb /dev/snd/hwC0D0 0x0d SET_CONNECT_SEL 0
```did it. It's exactly the change I had to do manually with HDA Analyzer (setting connection of node 0x0d to entry 0 in the connection list). After that I successfully created an Upstart-Job (had to learn how, because since 10.10 /etc/rc.local isn't working any more) that executes this command every time my system starts.

To create an Upstart-Job create a text-file in /etc/init/. In my case I called it /etc/init/soundfix.conf (the extension is important) and it contains the following:
```
description     "command to fix Intel HDA sound issues on Shuttle SG41J1v2"

start on runlevel [2345]
stop on runlevel [!2345]

exec /usr/local/bin/hda-verb /dev/snd/hwC0D0 0x0d SET_CONNECT_SEL 0
```

---

### Post by dipshat on 2010-11-29
Thanks for the update.  I just put the command line you mentioned above in /etc/rc.local and everything worked.  I haven't tested the other ports to see if they are working but this for sure corrected the back audio jack.  Thats the only port I ever use so this was perfect for me. Thanks for the help.

/etc/local.rc
```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

hda-verb /dev/snd/hwC0D0 0x0d SET_CONNECT_SEL 0
exit 0
```

Ohh yeah I had to make it executable before it would work.
```
sudo chmod u+x /etc/rc.local
```

---

### Post by b4ss00k4 on 2010-11-30
My /etc/rc.local is 755, so thats not the problem. But I don't care, it's working the way I did it :wink:

---

### Post by dipshat on 2010-12-02
b4ss00k4:  Does your script to correct the audio run after hibernate/suspend?  I found my audio dropping after suspend.  Can you test that?  I had to create a script in /etc/pm/sleep.d/ (Ubuntu 10.04+ uses this directory but it is different in versions before 10.04) to correct the audio jack after it wakes from a hibernate/suspend.  It was just the same command line as used above but for sure rc.local does not run after a wake from suspend.

---

### Post by b4ss00k4 on 2010-12-03
Since sleep / hibernate isn't working on my SG41J1v2 (how did you get it working?) I can't test that. But I observed, that in a few cases my script didn't work. For example after the reboot following the last update of the kernel headers... I think that wasn't a full reboot (was very quick), maybe the drivers were loaded again but the script wasn't executed. If I find a solution for my sleep / hibernate problem I'll tell you whether it's working or not. :wink:

---

### Post by dipshat on 2010-12-05
Your hibernate and sleep problems are probably in the bios settings.  I believe I cahnged mine to ACPI 2.0 or something like that.  Try that.

---

### Post by b4ss00k4 on 2010-12-05
No, it's still not working. It would be great if you could post your BIOS Power Management Configuration.

---

