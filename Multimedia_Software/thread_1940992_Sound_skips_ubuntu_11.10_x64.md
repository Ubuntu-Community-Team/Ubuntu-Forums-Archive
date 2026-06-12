---
title: "Sound skips ubuntu 11.10 x64"
date: 2012-03-14
forum: Multimedia Software
---

### Post by Pale091 on 2012-03-14
Sound skips on the live CD as well, but not in windows.

Can't watch youtube video in firefox or chromium. VLC nor banshee work properly. Startup sound plays incorrectly (skips).

I have tried the solution in this thread: [http://ubuntuforums.org/showthread.php?t=1878921](http://ubuntuforums.org/showthread.php?t=1878921)

And this one: [http://ubuntuforums.org/showthread.php?t=1804083](http://ubuntuforums.org/showthread.php?t=1804083)

Added an /etc/asound.conf 
```
pcm.pulse {
type pulse
}
ctl.pulse {
type pulse
}
pcm.!default {
type pulse
}
ctl.!default {
type pulse
} 
```And so I turn to making a thread on the forums as a last resort. Can anyone enlighten me?
Its OK if you can't. The only reason I install Ubuntu is to play around with this kind of thing :D

Alsa.info
```
upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Wed Mar 14 23:22:18 UTC 2012


!!Linux Distribution
!!------------------

Ubuntu 11.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 11.10"


!!DMI Information
!!---------------

Manufacturer:      MSI
Product Name:      MS-7520
Product Version:   1.0


!!Kernel Information
!!------------------

Kernel release:    3.0.0-16-generic
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

 0 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xfb8fc000 irq 47
 1 [Creative       ]: HDA-Intel - HDA Creative
                      HDA Creative at 0xfbdfc000 irq 16


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
03:00.1 Audio device: ATI Technologies Inc Radeon HD 3870 Audio device
08:00.0 PCI bridge: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG PCI to PCIe Bridge
09:00.0 Audio device: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:3a3e
    Subsystem: 1462:7520
--
03:00.1 0403: 1002:aa18
    Subsystem: 1092:aa18
--
09:00.0 0403: 1102:0009
    Subsystem: 1102:0018


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-hda-intel: model=touchsmart
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
    bdl_pos_adj : 1,32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    beep_mode : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
    enable_msi : -1
    id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    model : touchsmart,(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    patch : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    position_fix : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    power_save : 0
    power_save_controller : Y
    probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    single_cmd : N

!!Module: snd_hda_intel
    bdl_pos_adj : 1,32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    beep_mode : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
    enable_msi : -1
    id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    model : touchsmart,(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
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
  Digital: Enabled
  Digital category: 0x0
Node 0x03 [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000094: OUT Detect HDMI
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=03, enabled=1
  Connection: 1
     0x02
Codec: Creative CA0110-IBG
Address: 1
AFG Function Id: 0x1 (unsol 1)
Vendor Id: 0x1102000a
Subsystem Id: 0x1462c320
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
  Amp-Out vals:  [0x67 0x67]
  Converter: stream=1, channel=0
Node 0x03 [Audio Output] wcaps 0x5: Stereo Amp-Out
  Control: name="Center Playback Volume", index=0, device=0
    ControlAmp: chs=1, dir=Out, idx=0, ofs=0
  Control: name="LFE Playback Volume", index=0, device=0
    ControlAmp: chs=1, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x67, nsteps=0x7f, stepsize=0x01, mute=0
  Amp-Out vals:  [0x67 0x00]
  Converter: stream=1, channel=0
Node 0x04 [Audio Output] wcaps 0x5: Stereo Amp-Out
  Control: name="Surround Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x67, nsteps=0x7f, stepsize=0x01, mute=0
  Amp-Out vals:  [0x67 0x67]
  Converter: stream=1, channel=0
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
  Converter: stream=1, channel=0
  Digital: Enabled
  Digital category: 0x0
Node 0x08 [Audio Input] wcaps 0x100103: Stereo Amp-In
  Control: name="Rear Mic Capture Volume", index=0, device=0
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
  Amp-In vals:  [0x00 0x00]
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
  Control: name="Rear Mic Capture Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80]
  Pincap 0x00000024: IN Detect
  Pin Default 0x01a19030: [Jack] Mic at Ext Rear
    Conn = 1/8, Color = Pink
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


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116,  4 Mar 14 19:11 /dev/snd/controlC0
crw-rw----+ 1 root audio 116, 10 Mar 14 19:11 /dev/snd/controlC1
crw-rw----+ 1 root audio 116,  3 Mar 14 19:11 /dev/snd/hwC0D0
crw-rw----+ 1 root audio 116,  9 Mar 14 19:11 /dev/snd/hwC1D1
crw-rw----+ 1 root audio 116,  2 Mar 14 19:11 /dev/snd/pcmC0D3p
crw-rw----+ 1 root audio 116,  8 Mar 14 19:11 /dev/snd/pcmC1D0c
crw-rw----+ 1 root audio 116,  7 Mar 14 19:15 /dev/snd/pcmC1D0p
crw-rw----+ 1 root audio 116,  6 Mar 14 19:11 /dev/snd/pcmC1D1c
crw-rw----+ 1 root audio 116,  5 Mar 14 19:11 /dev/snd/pcmC1D1p
crw-rw----+ 1 root audio 116,  1 Mar 14 19:11 /dev/snd/seq
crw-rw----+ 1 root audio 116, 33 Mar 14 19:11 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  80 Mar 14 19:11 .
drwxr-xr-x 3 root root 280 Mar 14 19:11 ..
lrwxrwxrwx 1 root root  12 Mar 14 19:11 pci-0000:03:00.1 -> ../controlC0
lrwxrwxrwx 1 root root  12 Mar 14 19:11 pci-0000:09:00.0 -> ../controlC1


!!ALSA configuration files
!!------------------------

!!System wide config file (/etc/asound.conf)

pcm.pulse {
type pulse
}
ctl.pulse {
type pulse
}
pcm.!default {
type pulse
}
ctl.!default {
type pulse
} 


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Creative [HDA Creative], device 0: CA0110 Analog [CA0110 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Creative [HDA Creative], device 1: CA0110 Digital [CA0110 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 1: Creative [HDA Creative], device 0: CA0110 Analog [CA0110 Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 1: Creative [HDA Creative], device 1: CA0110 Digital [CA0110 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [HDMI]

Card hw:0 'HDMI'/'HDA ATI HDMI at 0xfb8fc000 irq 47'
  Mixer name    : 'ATI R6xx HDMI'
  Components    : 'HDA:1002aa01,00aa0100,00100000'
  Controls      : 4
  Simple ctrls  : 1
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]

!!-------Mixer controls for card 1 [Creative]

Card hw:1 'Creative'/'HDA Creative at 0xfbdfc000 irq 16'
  Mixer name    : 'Creative CA0110-IBG'
  Components    : 'HDA:1102000a,1462c320,00100000'
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
  Front Left: Playback 103 [100%] [0.00dB] [on]
  Front Right: Playback 103 [100%] [0.00dB] [on]
Simple mixer control 'Front Mic',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 127
  Front Left: Capture 0 [0%] [-51.50dB] [on]
  Front Right: Capture 0 [0%] [-51.50dB] [on]
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
Simple mixer control 'Rear Mic',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 115
  Front Left: Capture 0 [0%] [-51.50dB] [off]
  Front Right: Capture 0 [0%] [-51.50dB] [off]


!!Alsactl output
!!-------------

--startcollapse--
state.HDMI {
    control.1 {
        iface MIXER
        name 'IEC958 Playback Con Mask'
        value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.2 {
        iface MIXER
        name 'IEC958 Playback Pro Mask'
        value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.3 {
        iface MIXER
        name 'IEC958 Playback Default'
        value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access 'read write'
            type IEC958
            count 1
        }
    }
    control.4 {
        iface MIXER
        name 'IEC958 Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
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
        name 'Rear Mic Capture Switch'
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
        name 'Rear Mic Capture Volume'
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
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 127'
            dbmin -5150
            dbmax 1200
            dbvalue.0 -5150
            dbvalue.1 -5150
        }
    }
    control.17 {
        iface MIXER
        name 'IEC958 Playback Con Mask'
        value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.18 {
        iface MIXER
        name 'IEC958 Playback Pro Mask'
        value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.19 {
        iface MIXER
        name 'IEC958 Playback Default'
        value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
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
        value '0300000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
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
joydev
binfmt_misc
snd_hda_codec_ca0110
mxm_wmi
snd_hda_codec_hdmi
arc4
rt2800pci
rt2800lib
crc_ccitt
rt2x00pci
rt2x00lib
psmouse
serio_raw
mac80211
cfg80211
eeprom_93cx6
snd_hda_intel
snd_seq_midi
snd_hda_codec
snd_hwdep
fglrx
snd_rawmidi
snd_pcm
snd_seq_midi_event
snd_seq
snd_timer
snd_seq_device
shpchp
i7core_edac
snd
edac_core
soundcore
snd_page_alloc
wmi
lp
parport
usbhid
hid
firewire_ohci
firewire_core
crc_itu_t
pata_jmicron
r8169
ahci
libahci


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x03 0x18560010

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:

/sys/class/sound/hwC1D1/init_pin_configs:
0x0b 0x01014010
0x0c 0x01016011
0x0d 0x01011012
0x0e 0x01012014
0x0f 0x02214020
0x10 0x01a19030
0x11 0x02a19040
0x12 0x01452150
0x13 0x01c51160

/sys/class/sound/hwC1D1/driver_pin_configs:

/sys/class/sound/hwC1D1/user_pin_configs:

/sys/class/sound/hwC1D1/init_verbs:


!!ALSA/HDA dmesg
!!------------------

[   18.853425] type=1400 audit(1331766699.892:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=659 comm="apparmor_parser"
[   18.859212] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   18.859256] HDA Intel 0000:00:1b.0: irq 47 for MSI/MSI-X
[   18.859278] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   18.879161] [fglrx] Maximum main memory to use for locked dma buffers: 5776 MBytes.
--
[   18.884945] cfg80211: Calling CRDA to update world regulatory domain
[   18.889729] hda-intel: no codecs found!
[   18.889789] HDA Intel 0000:00:1b.0: PCI INT A disabled
[   18.889824] HDA Intel 0000:03:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   18.889886] HDA Intel 0000:03:00.1: irq 47 for MSI/MSI-X
[   18.889910] HDA Intel 0000:03:00.1: setting latency timer to 64
[   18.893150] rt2800pci 0000:0a:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
--
[   18.902801] Registered led device: rt2800pci-phy0::quality
[   18.913427] HDMI status: Pin=3 Presence_Detect=0 ELD_Valid=0
[   18.913532] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:07.0/0000:03:00.1/sound/card0/input5
[   18.913730] HDA Intel 0000:09:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   18.935169] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:


```

---

