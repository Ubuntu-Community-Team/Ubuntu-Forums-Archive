---
title: "Not recognizing Sound Blaster X-Fi card in laptop"
date: 2013-01-23
forum: Multimedia Software
---

### Post by SteamDonkey74 on 2013-01-23
I have been through the two sound problem step-by-step guides. My problem is not that I am getting no sound. The on-board sound works fine on my laptop. I can use either the headphone jack or the built-in speakers and things work.

I have a Sound Blaster X-Fi card model no. SB 0950. When I insert it into the appropriate slot it makes contact with the pins and the two happy little lights on it, CONNECT and POWER, come on. I can play music through the regular headphone jack or speakers but not the card.

ALSAmixer doesn't show this card as being an option. 

I have tried several things in the first sound guide and I have gone up through Step 7 in the other. My problem still is that the card does not seem to be recognized by the computer.


The particulars:

Creative Labs Sound Blaster X-Fi card model SB0950
Computer: HP Compaq NC6320 laptop
OS: Xubuntu 12.04 LTS



I have been looking through here and that web searching engine for some answers but haven't found them. I am sure I am not a trailblazer here, however, and if there is an easy answer I missed I apologize. Sometimes I don't know enough to know what I don't know.


Thanks in advance for your help,
Adam

---

### Post by SteamDonkey74 on 2013-01-23
When I was working through the second sound troubleshooter, this was what I got from Step 3 (IIRC):

> !!Script ran on: Wed Jan 23 07:21:11 UTC 2013


!!Linux Distribution
!!------------------

Ubuntu 12.04.1 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS" NAME="Ubuntu" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu precise (12.04.1 LTS)"


!!DMI Information
!!---------------

Manufacturer:      Hewlett-Packard
Product Name:      HP Compaq nc6320 (RM124UT#ABA)
Product Version:   F.0B
Firmware Version:  68YDU Ver. F.0B


!!Kernel Information
!!------------------

Kernel release:    3.2.0-36-generic-pae
Operating System:  GNU/Linux
Architecture:      i686
Processor:         i686
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.24
Library version:    1.0.25
Utilities version:  1.0.25


!!Loaded ALSA modules
!!-------------------

snd_hda_intel


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xe8580000 irq 45


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
02:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!-------------------------------------------------------

00:1b.0 0403: 8086:27d8 (rev 01)
    Subsystem: 103c:30aa


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
!!---------------------------

!!Module: snd_hda_intel
    align_buffer_size : Y
    bdl_pos_adj : 1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    beep_mode : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
    enable_msi : -1
    id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    model : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    patch : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    position_fix : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    power_save : 1
    power_save_controller : Y
    probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    single_cmd : N
    snoop : Y


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: Analog Devices AD1981
Address: 0
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x11d41981
Subsystem Id: 0x103c30aa
Revision Id: 0x100200
No Modem Function Group found
Default PCM:
    rates [0x7f]: 8000 11025 16000 22050 32000 44100 48000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
Default Amp-Out caps: ofs=0x3d, nsteps=0x3f, stepsize=0x05, mute=1
GPIO: io=4, o=0, i=0, unsolicited=1, wake=0
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=1, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=1, unsol=0
  IO[2]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[3]: enable=0, dir=0, wake=0, sticky=0, data=1, unsol=0
Node 0x02 [Audio Output] wcaps 0x30311: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x60]: 44100 48000
    bits [0x2]: 16
    formats [0x5]: PCM AC3
  Delay: 3 samples
  Connection: 2
     0x01* 0x04
Node 0x03 [Audio Output] wcaps 0x441: Stereo
  Device: name="AD198x Analog", type="Audio", device=0
  Converter: stream=0, channel=0
  Power states:  D0 D3
  Power: setting=D0, actual=D3
  Processing caps: benign=1, ncoeff=70
Node 0x04 [Audio Input] wcaps 0x100511: Stereo
  Device: name="AD198x Analog", type="Audio", device=0
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x7f]: 8000 11025 16000 22050 32000 44100 48000
    bits [0x6]: 16 20
    formats [0x1]: PCM
  Power states:  D0 D3
  Power: setting=D0, actual=D3
  Connection: 1
     0x15
Node 0x05 [Pin Complex] wcaps 0x400187: Stereo Amp-In Amp-Out
  Control: name="Master Playback Switch", index=0, device=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x3d, nsteps=0x3f, stepsize=0x05, mute=1
  Amp-Out vals:  [0xbf 0xbf]
  Pincap 0x0001173f: IN OUT HP EAPD Detect Trigger ImpSense
    Vref caps: HIZ 50 GRD 80
  EAPD 0x2: EAPD
  Pin Default 0x92174110: [Fixed] Speaker at Int Front
    Conn = Analog, Color = Green
    DefAssociation = 0x1, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 2
     0x03 0x0e*
Node 0x06 [Pin Complex] wcaps 0x400185: Stereo Amp-Out
  Amp-Out caps: ofs=0x3d, nsteps=0x3f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x3f 0x3f]
  Pincap 0x0000001f: OUT HP Detect Trigger ImpSense
  Pin Default 0x0321201f: [Jack] HP Out at Ext Left
    Conn = 1/8, Color = Grey
    DefAssociation = 0x1, Sequence = 0xf
  Pin-ctls: 0xc0: OUT HP
  Unsolicited: tag=37, enabled=1
  Connection: 2
     0x03 0x0e*
Node 0x07 [Pin Complex] wcaps 0x400104: Mono Amp-Out
  Amp-Out caps: ofs=0x3d, nsteps=0x3f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x80]
  Pincap 0x00000010: OUT
  Pin Default 0x410710f0: [N/A] Line Out at Ext Rear
    Conn = Analog, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x0f
Node 0x08 [Pin Complex] wcaps 0x400083: Stereo Amp-In
  Control: name="Mic Boost Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00001727: IN Detect Trigger ImpSense
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x03a12020: [Jack] Mic at Ext Left
    Conn = 1/8, Color = Grey
    DefAssociation = 0x2, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=38, enabled=1
Node 0x09 [Pin Complex] wcaps 0x400187: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x3d, nsteps=0x3f, stepsize=0x05, mute=1
  Amp-Out vals:  [0xbf 0xbf]
  Pincap 0x00001737: IN OUT Detect Trigger ImpSense
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x0181302e: [Jack] Line In at Ext Rear
    Conn = 1/8, Color = Blue
    DefAssociation = 0x2, Sequence = 0xe
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 2
     0x03* 0x0e
Node 0x0a [Pin Complex] wcaps 0x400301: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x4145f0f0: [N/A] SPDIF Out at Ext Rear
    Conn = Optical, Color = Other
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x02
Node 0x0b [Audio Selector] wcaps 0x300101: Stereo
  Connection: 6
     0x03 0x0c 0x09 0x0e* 0x05 0x18
Node 0x0c [Audio Mixer] wcaps 0x200101: Stereo
  Connection: 2
     0x1e 0x1f
Node 0x0d [Audio Selector] wcaps 0x30010c: Mono Amp-Out
  Control: name="Beep Playback Volume", index=0, device=0
    ControlAmp: chs=1, dir=Out, idx=0, ofs=0
  Control: name="Beep Playback Switch", index=0, device=0
    ControlAmp: chs=1, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x0f, nsteps=0x0f, stepsize=0x0b, mute=1
  Amp-Out vals:  [0x80]
  Connection: 2
     0x10* 0x16
Node 0x0e [Audio Mixer] wcaps 0x200101: Stereo
  Connection: 8
     0x0d 0x11 0x12 0x13 0x1a 0x1b 0x1c 0x1d
Node 0x0f [Audio Mixer] wcaps 0x200100: Mono
  Connection: 1
     0x0b
Node 0x10 [Beep Generator Widget] wcaps 0x700000: Mono
Node 0x11 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Control: name="PCM Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="PCM Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x17 0x17]
  Connection: 1
     0x03
Node 0x12 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x80 0x80]
  Connection: 1
     0x08
Node 0x13 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x80 0x80]
  Connection: 1
     0x09
Node 0x14 [Power Widget] wcaps 0x500500: Mono
  Power states:  D0 D3
  Power: setting=D0, actual=D3
  Connection: 13
     0x0d 0x0e 0x0f 0x10 0x13 0x14 0x15 0x16 0x17 0x18 0x19 0x1a 0x1d
Node 0x15 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Control: name="Capture Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Capture Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Capture Source", index=0, device=0
  Amp-Out caps: ofs=0x00, nsteps=0x0f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x08 0x08]
  Connection: 8
     0x0c* 0x09 0x0e 0x0f 0x19 0x05 0x18 0x17
Node 0x16 [Pin Complex] wcaps 0x400000: Mono
  Pincap 0x00000020: IN
  Pin Default 0x995711f0: [Fixed] Digital Out at Int ATAPI
    Conn = Analog, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
Node 0x17 [Pin Complex] wcaps 0x400081: Stereo
  Pincap 0x00000027: IN Detect Trigger ImpSense
  Pin Default 0x5993e0f0: [N/A] Aux at Int ATAPI
    Conn = ATAPI, Color = White
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
Node 0x18 [Pin Complex] wcaps 0x400187: Stereo Amp-In Amp-Out
  Control: name="Internal Mic Boost Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x3d, nsteps=0x3f, stepsize=0x05, mute=1
  Amp-Out vals:  [0xbf 0xbf]
  Pincap 0x00001737: IN OUT Detect Trigger ImpSense
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x91a79121: [Fixed] Mic at Int Rear
    Conn = Analog, Color = Pink
    DefAssociation = 0x2, Sequence = 0x1
    Misc = NO_PRESENCE
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Connection: 2
     0x03* 0x0e
Node 0x19 [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x593310f0: [N/A] CD at Int ATAPI
    Conn = ATAPI, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x20: IN
Node 0x1a [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x80 0x80]
  Connection: 1
     0x05
Node 0x1b [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x80 0x80]
  Connection: 1
     0x17
Node 0x1c [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x80 0x80]
  Connection: 1
     0x18
Node 0x1d [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x80 0x80]
  Connection: 1
     0x19
Node 0x1e [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Connection: 1
     0x08
Node 0x1f [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Connection: 1
     0x18
Codec: LSI Si3054
Address: 1
MFG Function Id: 0x2 (unsol 1)
Vendor Id: 0x11c13026
Subsystem Id: 0x103c30aa
Revision Id: 0x100700
Modem Function Group: 0x1
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw---T+ 1 root audio 116,  8 Jan 22 23:18 /dev/snd/controlC0
crw-rw---T+ 1 root audio 116,  7 Jan 22 23:18 /dev/snd/hwC0D0
crw-rw---T+ 1 root audio 116,  6 Jan 22 23:18 /dev/snd/hwC0D1
crw-rw---T+ 1 root audio 116,  5 Jan 22 23:18 /dev/snd/pcmC0D0c
crw-rw---T+ 1 root audio 116,  4 Jan 22 23:18 /dev/snd/pcmC0D0p
crw-rw---T+ 1 root audio 116,  3 Jan 22 23:18 /dev/snd/pcmC0D6c
crw-rw---T+ 1 root audio 116,  2 Jan 22 23:18 /dev/snd/pcmC0D6p
crw-rw---T+ 1 root audio 116,  1 Jan 22 23:18 /dev/snd/seq
crw-rw---T+ 1 root audio 116, 33 Jan 22 23:18 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Jan 22 23:18 .
drwxr-xr-x 3 root root 240 Jan 22 23:18 ..
lrwxrwxrwx 1 root root  12 Jan 22 23:18 pci-0000:00:1b.0 -> ../controlC0


!!Aplay/Arecord output
!!--------------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [Intel]

Card hw:0 'Intel'/'HDA Intel at 0xe8580000 irq 45'
  Mixer name    : 'Analog Devices AD1981'
  Components    : 'HDA:11d41981,103c30aa,00100200 HDA:11c13026,103c30aa,00100700'
  Controls      : 13
  Simple ctrls  : 11
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 63
  Mono:
  Front Left: Playback 63 [100%] [3.00dB] [on]
  Front Right: Playback 63 [100%] [3.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 23 [74%] [0.00dB] [on]
  Front Right: Playback 23 [74%] [0.00dB] [on]
Simple mixer control 'Mic',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Mono
  Mono: Capture [on]
Simple mixer control 'Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB]
Simple mixer control 'Beep',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 15
  Mono: Playback 0 [0%] [-45.00dB] [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 8 [53%] [12.00dB] [on]
  Front Right: Capture 8 [53%] [12.00dB] [on]
Simple mixer control 'Mix',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Mono
  Mono: Capture [off]
Simple mixer control 'Caller ID',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Docking-Station',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Mono
  Mono: Capture [off]
Simple mixer control 'Internal Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB]
Simple mixer control 'Off-hook',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]


!!Alsactl output
!!--------------

--startcollapse--
state.Intel {
    control.1 {
        iface MIXER
        name 'Master Playback Volume'
        value.0 63
        value.1 63
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 63'
            dbmin -9150
            dbmax 300
            dbvalue.0 300
            dbvalue.1 300
        }
    }
    control.2 {
        iface MIXER
        name 'Master Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.3 {
        iface MIXER
        name 'PCM Playback Volume'
        value.0 23
        value.1 23
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 31'
            dbmin -3450
            dbmax 1200
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.4 {
        iface MIXER
        name 'PCM Playback Switch'
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
        name 'Mic Boost Volume'
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
    control.6 {
        iface MIXER
        name 'Internal Mic Boost Volume'
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
    control.7 {
        iface MIXER
        name 'Capture Volume'
        value.0 8
        value.1 8
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 15'
            dbmin 0
            dbmax 2250
            dbvalue.0 1200
            dbvalue.1 1200
        }
    }
    control.8 {
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
    control.9 {
        iface MIXER
        name 'Capture Source'
        value Mic
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Mic
            item.1 Docking-Station
            item.2 Mix
        }
    }
    control.10 {
        iface MIXER
        name 'Beep Playback Volume'
        value 0
        comment {
            access 'read write'
            type INTEGER
            count 1
            range '0 - 15'
            dbmin -4500
            dbmax 0
            dbvalue.0 -4500
        }
    }
    control.11 {
        iface MIXER
        name 'Beep Playback Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.12 {
        iface MIXER
        name 'Off-hook Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.13 {
        iface MIXER
        name 'Caller ID Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
tpm_infineon
joydev
hp_wmi
sparse_keymap
pcmcia
dm_multipath
snd_hda_codec_si3054
snd_hda_codec_analog
psmouse
serio_raw
tifm_7xx1
tifm_core
snd_usb_audio
snd_usbmidi_lib
snd_hda_intel
snd_hda_codec
snd_hwdep
arc4
snd_pcm
yenta_socket
pcmcia_rsrc
pcmcia_core
ppdev
btusb
rfcomm
bnep
bluetooth
iwl3945
snd_seq_midi
iwl_legacy
mac80211
snd_rawmidi
parport_pc
binfmt_misc
cfg80211
snd_seq_midi_event
tpm_tis
snd_seq
mac_hid
snd_timer
snd_seq_device
snd
soundcore
snd_page_alloc
lp
parport
dm_raid45
xor
dm_mirror
dm_region_hash
dm_log
btrfs
zlib_deflate
libcrc32c
usbhid
hid
firewire_ohci
sdhci_pci
firewire_core
sdhci
crc_itu_t
tg3
i915
drm_kms_helper
drm
i2c_algo_bit
video
wmi
zram


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x05 0x92174110
0x06 0x0321201f
0x07 0x410710f0
0x08 0x03a12020
0x09 0x0181302e
0x0a 0x4145f0f0
0x16 0x995711f0
0x17 0x5993e0f0
0x18 0x91a79121
0x19 0x593310f0

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:

/sys/class/sound/hwC0D1/init_pin_configs:

/sys/class/sound/hwC0D1/driver_pin_configs:

/sys/class/sound/hwC0D1/user_pin_configs:

/sys/class/sound/hwC0D1/init_verbs:


!!ALSA/HDA dmesg
!!--------------

[   25.169836] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   25.171111] snd_hda_intel 0000:00:1b.0: power state changed by ACPI to D0
[   25.171123] snd_hda_intel 0000:00:1b.0: power state changed by ACPI to D0
[   25.171137] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   25.171224] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   25.171265] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   25.191574] intel_rng: FWH not detected




---

### Post by SteamDonkey74 on 2013-01-23
This is what returned when I did Step 4:

> Advanced Linux Sound Architecture Driver Version 1.0.24.
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xe8580000 irq 45
  1:        : sequencer
  2: [ 0- 6]: digital audio playback
  3: [ 0- 6]: digital audio capture
  4: [ 0- 0]: digital audio playback
  5: [ 0- 0]: digital audio capture
  6: [ 0- 1]: hardware dependent
  7: [ 0- 0]: hardware dependent
  8: [ 0]   : control
 33:        : timer
00-01: HDA Codec 1
00-00: HDA Codec 0
00-00: AD198x Analog : AD198x Analog : playback 1 : capture 1
00-06: Si3054 Modem : Si3054 Modem : playback 1 : capture 1
Client info
  cur  clients : 1
  peak clients : 1
  max  clients : 192

Client   0 : "System" [Kernel]
  Port   0 : "Timer" (Rwe-)
  Port   1 : "Announce" (R-e-)
Client  14 : "Midi Through" [Kernel]
  Port   0 : "Midi Through Port-0" (RWe-)
[sudo] password for adam: 
rm: cannot remove `/etc/asound.conf': No such file or directory
rm: cannot remove `/home/adam/.asound*': No such file or directory
Hit [http://apt.freegeek.org](http://apt.freegeek.org) lucid InRelease
Hit [http://apt.freegeek.org](http://apt.freegeek.org) precise InRelease                                  
Hit [http://apt.freegeek.org](http://apt.freegeek.org) lucid InRelease                                    
Hit [http://apt.freegeek.org](http://apt.freegeek.org) lucid/main i386 Packages                           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease                      
Ign [http://apt.freegeek.org](http://apt.freegeek.org) lucid/main TranslationIndex                        
Hit [http://apt.freegeek.org](http://apt.freegeek.org) precise/main i386 Packages                         
Ign [http://apt.freegeek.org](http://apt.freegeek.org) precise/main TranslationIndex                      
Hit [http://apt.freegeek.org](http://apt.freegeek.org) lucid/main i386 Packages                           
Ign [http://apt.freegeek.org](http://apt.freegeek.org) lucid/main TranslationIndex                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise InRelease                                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates InRelease                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                             
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise InRelease                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release.gpg                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex    
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release.gpg [198 B]            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex      
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free i386 Packages                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en      
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                 
Ign [http://apt.freegeek.org](http://apt.freegeek.org) lucid/main Translation-en_US                       
Ign [http://apt.freegeek.org](http://apt.freegeek.org) lucid/main Translation-en                          
Ign [http://apt.freegeek.org](http://apt.freegeek.org) precise/main Translation-en_US                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en        
Ign [http://apt.freegeek.org](http://apt.freegeek.org) precise/main Translation-en                        
Ign [http://apt.freegeek.org](http://apt.freegeek.org) lucid/main Translation-en_US                       
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release [49.6 kB]              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Ign [http://apt.freegeek.org](http://apt.freegeek.org) lucid/main Translation-en                          
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free i386 Packages               
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free TranslationIndex                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Sources                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Sources                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse Sources                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Sources                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main i386 Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted i386 Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse i386 Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe i386 Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main TranslationIndex                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse TranslationIndex              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted TranslationIndex              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe TranslationIndex                
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main Sources [203 kB] 
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free TranslationIndex            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US             
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted Sources [4,743 B]  
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse Sources [4,240 B]   
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe Sources [71.9 kB]     
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main i386 Packages [468 kB]    
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free Translation-en_US               
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted i386 Packages [8,999 B]
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse i386 Packages [9,678 B]
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe i386 Packages [172 kB]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free Translation-en                 
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free Translation-en_US           
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free Translation-en              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main TranslationIndex            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse TranslationIndex      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted TranslationIndex      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe TranslationIndex        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Translation-en                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse Translation-en                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Translation-en                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Translation-en                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main Translation-en              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse Translation-en        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted Translation-en        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe Translation-en          
Fetched 993 kB in 8s (113 kB/s)                                                
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
aptitude is already the newest version.
The following packages were automatically installed and are no longer required:
  gir1.2-json-1.0 gir1.2-timezonemap-1.0 linux-headers-3.2.0-32 kde-l10n-engb
  linux-headers-3.2.0-32-generic python-central rdesktop gir1.2-xkl-1.0
  freegeek-ubuntu-pocket-guide linux-headers-3.2.0-32-generic-pae
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
No candidate version found for padevchooser
No candidate version found for libsdl1.2debian-pulseaudio
No candidate version found for padevchooser
No candidate version found for libsdl1.2debian-pulseaudio
The following NEW packages will be installed:
  gnome-alsamixer libbonoboui2-0{a} libbonoboui2-common{a} 
  libglademm-2.4-1c2a{a} libgnomecanvas2-0{a} libgnomecanvas2-common{a} 
  libgnomeui-0{a} libgnomeui-common{a} libgtkmm-2.4-1c2a{a} paman 
  pavumeter{a} 
The following packages will be REMOVED:
  freegeek-ubuntu-pocket-guide{u} gir1.2-json-1.0{u} 
  gir1.2-timezonemap-1.0{u} gir1.2-xkl-1.0{u} kde-l10n-engb{u} 
  linux-headers-3.2.0-32{u} linux-headers-3.2.0-32-generic{u} 
  linux-headers-3.2.0-32-generic-pae{u} python-central{u} rdesktop{u} 
0 packages upgraded, 11 newly installed, 10 to remove and 4 not upgraded.
Need to get 1,792 kB of archives. After unpacking 77.0 MB will be freed.
Do you want to continue? [Y/n/?] y
Get: 1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates/main libgnomecanvas2-common all 2.30.3-1ubuntu1.1 [9,120 B]
Get: 2 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates/main libgnomecanvas2-0 i386 2.30.3-1ubuntu1.1 [101 kB]
Get: 3 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates/main libbonoboui2-common all 2.24.5-0ubuntu1.1 [11.7 kB]
Get: 4 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates/main libbonoboui2-0 i386 2.24.5-0ubuntu1.1 [188 kB]
Get: 5 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main libgnomeui-common all 2.24.5-2ubuntu2 [16.5 kB]
Get: 6 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main libgnomeui-0 i386 2.24.5-2ubuntu2 [252 kB]
Get: 7 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main libgtkmm-2.4-1c2a i386 1:2.24.2-1ubuntu1 [1,021 kB]
Get: 8 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/universe gnome-alsamixer i386 0.9.7~cvs.20060916.ds.1-3 [51.4 kB]
Get: 9 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/universe libglademm-2.4-1c2a i386 2.6.7-2build1 [21.8 kB]
Get: 10 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/universe paman i386 0.9.4-1ubuntu3 [91.7 kB]
Get: 11 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/universe pavumeter i386 0.9.3-1ubuntu2 [28.1 kB]
Fetched 1,792 kB in 6s (289 kB/s)                                               
(Reading database ... 298522 files and directories currently installed.)
Removing freegeek-ubuntu-pocket-guide ...
Removing gir1.2-timezonemap-1.0 ...
Removing gir1.2-json-1.0 ...
Removing gir1.2-xkl-1.0 ...
Removing kde-l10n-engb ...
Removing linux-headers-3.2.0-32-generic-pae ...
Removing linux-headers-3.2.0-32-generic ...
Removing linux-headers-3.2.0-32 ...
Removing python-central ...
Removing rdesktop ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for desktop-file-utils ...
Processing triggers for man-db ...
Selecting previously unselected package libgnomecanvas2-common.
(Reading database ... 267505 files and directories currently installed.)
Unpacking libgnomecanvas2-common (from .../libgnomecanvas2-common_2.30.3-1ubuntu1.1_all.deb) ...
Selecting previously unselected package libgnomecanvas2-0.
Unpacking libgnomecanvas2-0 (from .../libgnomecanvas2-0_2.30.3-1ubuntu1.1_i386.deb) ...
Selecting previously unselected package libbonoboui2-common.
Unpacking libbonoboui2-common (from .../libbonoboui2-common_2.24.5-0ubuntu1.1_all.deb) ...
Selecting previously unselected package libbonoboui2-0.
Unpacking libbonoboui2-0 (from .../libbonoboui2-0_2.24.5-0ubuntu1.1_i386.deb) ...
Selecting previously unselected package libgnomeui-common.
Unpacking libgnomeui-common (from .../libgnomeui-common_2.24.5-2ubuntu2_all.deb) ...
Selecting previously unselected package libgnomeui-0.
Unpacking libgnomeui-0 (from .../libgnomeui-0_2.24.5-2ubuntu2_i386.deb) ...
Selecting previously unselected package libgtkmm-2.4-1c2a.
Unpacking libgtkmm-2.4-1c2a (from .../libgtkmm-2.4-1c2a_1%3a2.24.2-1ubuntu1_i386.deb) ...
Selecting previously unselected package gnome-alsamixer.
Unpacking gnome-alsamixer (from .../gnome-alsamixer_0.9.7~cvs.20060916.ds.1-3_i386.deb) ...
Selecting previously unselected package libglademm-2.4-1c2a.
Unpacking libglademm-2.4-1c2a (from .../libglademm-2.4-1c2a_2.6.7-2build1_i386.deb) ...
Selecting previously unselected package paman.
Unpacking paman (from .../paman_0.9.4-1ubuntu3_i386.deb) ...
Selecting previously unselected package pavumeter.
Unpacking pavumeter (from .../pavumeter_0.9.3-1ubuntu2_i386.deb) ...
Processing triggers for gconf2 ...
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for desktop-file-utils ...
Setting up libgnomecanvas2-common (2.30.3-1ubuntu1.1) ...
Setting up libgnomecanvas2-0 (2.30.3-1ubuntu1.1) ...
Setting up libbonoboui2-common (2.24.5-0ubuntu1.1) ...
Setting up libbonoboui2-0 (2.24.5-0ubuntu1.1) ...
Setting up libgnomeui-common (2.24.5-2ubuntu2) ...
Setting up libgnomeui-0 (2.24.5-2ubuntu2) ...
Setting up libgtkmm-2.4-1c2a (1:2.24.2-1ubuntu1) ...
Setting up gnome-alsamixer (0.9.7~cvs.20060916.ds.1-3) ...
Setting up libglademm-2.4-1c2a (2.6.7-2build1) ...
Setting up paman (0.9.4-1ubuntu3) ...
Setting up pavumeter (0.9.3-1ubuntu2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
                                         
H/W path               Device      Class          Description
=============================================================
                                   system         HP Compaq nc6320 (RM124UT#ABA)
/0                                 bus            30AA
/0/0                               memory         128KiB BIOS
/0/4                               processor      Intel(R) Core(TM)2 CPU        
/0/4/5                             memory         64KiB L1 cache
/0/4/6                             memory         2MiB L2 cache
/0/4/0.1                           processor      Logical CPU
/0/4/0.2                           processor      Logical CPU
/0/a                               memory         2GiB System Memory
/0/a/0                             memory         1GiB SODIMM DDR2 Synchronous 6
/0/a/1                             memory         1GiB SODIMM DDR2 Synchronous 6
/0/100                             bridge         Mobile 945GM/PM/GMS, 943/940GM
/0/100/2                           display        Mobile 945GM/GMS, 943/940GML E
/0/100/2.1                         display        Mobile 945GM/GMS/GME, 943/940G
/0/100/1b                          multimedia     N10/ICH 7 Family High Definiti
/0/100/1c                          bridge         N10/ICH 7 Family PCI Express P
/0/100/1c/0            wlan0       network        PRO/Wireless 3945ABG [Golan] N
/0/100/1c.2                        bridge         N10/ICH 7 Family PCI Express P
/0/100/1c.3                        bridge         N10/ICH 7 Family PCI Express P
/0/100/1d                          bus            N10/ICH 7 Family USB UHCI Cont
/0/100/1d.1                        bus            N10/ICH 7 Family USB UHCI Cont
/0/100/1d.2                        bus            N10/ICH 7 Family USB UHCI Cont
/0/100/1d.3                        bus            N10/ICH 7 Family USB UHCI Cont
/0/100/1d.7                        bus            N10/ICH 7 Family USB2 EHCI Con
/0/100/1e                          bridge         82801 Mobile PCI Bridge
/0/100/1e/6                        bridge         PCIxx12 Cardbus Controller
/0/100/1e/6.1                      bus            PCIxx12 OHCI Compliant IEEE 13
/0/100/1e/6.2                      storage        5-in-1 Multimedia Card Reader 
/0/100/1e/6.3                      generic        PCIxx12 SDA Standard Compliant
/0/100/1e/6.4                      communication  PCIxx12 GemCore based SmartCar
/0/100/1e/e            eth0        network        NetXtreme BCM5788 Gigabit Ethe
/0/100/1f                          bridge         82801GBM (ICH7-M) LPC Interfac
/0/100/1f.1            scsi4       storage        82801G (ICH7 Family) IDE Contr
/0/100/1f.1/0.0.0      /dev/cdrom  disk           DVDRW   DVR-K17
/0/100/1f.2            scsi0       storage        82801GBM/GHM (ICH7-M Family) S
/0/100/1f.2/0.0.0      /dev/sda    disk           100GB FUJITSU MHW2100B
/0/100/1f.2/0.0.0/1    /dev/sda1   volume         91GiB EXT4 volume
/0/100/1f.2/0.0.0/2    /dev/sda2   volume         2038MiB Extended partition
/0/100/1f.2/0.0.0/2/5  /dev/sda5   volume         2038MiB Linux swap / Solaris p
total 0
crw-rw---T+  1 root audio 116, 33 Jan 23 09:57 timer
crw-rw---T+  1 root audio 116,  1 Jan 23 09:57 seq
crw-rw---T+  1 root audio 116,  2 Jan 23 09:57 pcmC0D6p
crw-rw---T+  1 root audio 116,  3 Jan 23 09:57 pcmC0D6c
crw-rw---T+  1 root audio 116,  6 Jan 23 09:57 hwC0D1
crw-rw---T+  1 root audio 116,  7 Jan 23 09:57 hwC0D0
crw-rw---T+  1 root audio 116,  8 Jan 23 09:57 controlC0
drwxr-xr-x   2 root root       60 Jan 23 09:57 by-path
drwxr-xr-x   3 root root      240 Jan 23 09:57 .
crw-rw---T+  1 root audio 116,  5 Jan 23 10:00 pcmC0D0c
crw-rw---T+  1 root audio 116,  4 Jan 23 10:29 pcmC0D0p
drwxr-xr-x  15 root root     4280 Jan 23 10:29 ..
cat: /dev/sndstat: No such file or directory
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 01)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 01)
00:1c.2 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 3 [8086:27d4] (rev 01)
00:1c.3 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 4 [8086:27d6] (rev 01)
00:1d.0 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 01)
00:1d.1 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 01)
00:1d.2 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 01)
00:1d.3 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 01)
00:1d.7 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 01)
00:1f.2 SATA controller [0106]: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [AHCI mode] [8086:27c5] (rev 01)
02:06.0 CardBus bridge [0607]: Texas Instruments PCIxx12 Cardbus Controller [104c:8039]
02:06.1 FireWire (IEEE 1394) [0c00]: Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller [104c:803a]
02:06.2 Mass storage controller [0180]: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) [104c:803b]
02:06.3 SD Host controller [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller [104c:803c]
02:06.4 Communication controller [0780]: Texas Instruments PCIxx12 GemCore based SmartCard controller [104c:803d]
02:0e.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5788 Gigabit Ethernet [14e4:169c] (rev 03)
08:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0424:2503 Standard Microsystems Corp. USB 2.0 Hub
Bus 001 Device 003: ID 03f0:171d Hewlett-Packard Bluetooth 2.0 Interface [Broadcom BCM2045]
Bus 001 Device 004: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor
Bus 002 Device 003: ID 041e:30d2 Creative Technology, Ltd 
/sbin/alsactl
Specified filename /dev/dsp does not exist.
                     USER        PID ACCESS COMMAND
/dev/snd/controlC0:  adam       1850 F.... xfce4-volumed
                     adam       1861 F.... pulseaudio
/dev/snd/pcmC0D0p:   adam       1861 F...m pulseaudio
dpkg-query: no path found matching pattern *bin/slmodemd*.
[    0.000000] Found optimal setting for mtrr clean up
[    0.305739] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.351618] ACPI: No dock devices found.
[    0.351620] HEST: Table not found.
[    0.416058] pnp: PnP ACPI: found 15 devices
[    0.455733] audit: initializing netlink socket (disabled)
[    0.455746] type=2000 audit(1358963846.448:1): initialized
[    0.563331] ERST: Table is not found!
[    0.938940] isapnp: No Plug & Play device found
[    1.020917] Fixed MDIO Bus: probed
[    1.021390] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    1.040209] hub 1-0:1.0: USB hub found
[    1.040657] hub 2-0:1.0: USB hub found
[    1.041053] hub 3-0:1.0: USB hub found
[    1.041439] hub 4-0:1.0: USB hub found
[    1.041824] hub 5-0:1.0: USB hub found
[    1.061372] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.484697] hub 1-1:1.0: USB hub found
[    1.714750] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    1.714919] [Firmware Bug]: _BCQ is used instead of _BQC
[    1.974958] sdhci-pci 0000:02:06.3: SDHCI controller found [104c:803c] (rev 0)
[    1.975056] mmc0: no vmmc regulator found
[   24.447025] lp: driver loaded but no devices found
[   24.814832] leds_ss4200: no LED devices found
[   24.851042] yenta_cardbus 0000:02:06.0: CardBus bridge found [103c:30aa]
[   24.929680] snd_hda_intel 0000:00:1b.0: power state changed by ACPI to D0
[   24.929692] snd_hda_intel 0000:00:1b.0: power state changed by ACPI to D0
[   24.929704] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   24.929798] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   24.929838] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   24.948533] type=1400 audit(1358963871.389:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=747 comm="apparmor_parser"
[   24.949078] type=1400 audit(1358963871.389:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=747 comm="apparmor_parser"
[   24.949393] type=1400 audit(1358963871.389:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=747 comm="apparmor_parser"
[   25.083806] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x7000-0x7fff: excluding 0x7000-0x70ff 0x7400-0x74ff
[   25.170005] pcmcia_socket pcmcia_socket0: cs: memory probe 0xe8100000-0xe83fffff: excluding 0xe8100000-0xe812ffff
[   25.170030] pcmcia_socket pcmcia_socket0: cs: memory probe 0x80000000-0x83ffffff: excluding 0x80000000-0x83ffffff
[   25.342387] type=1400 audit(1358963871.781:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=945 comm="apparmor_parser"
[   25.346020] type=1400 audit(1358963871.785:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=946 comm="apparmor_parser"
[   25.348492] type=1400 audit(1358963871.789:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=946 comm="apparmor_parser"
[   25.348809] type=1400 audit(1358963871.789:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=946 comm="apparmor_parser"
[   25.377061] type=1400 audit(1358963871.817:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=950 comm="apparmor_parser"
[   25.378113] type=1400 audit(1358963871.817:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=966 comm="apparmor_parser"
[   25.378777] type=1400 audit(1358963871.817:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=966 comm="apparmor_parser"
[   25.486291] iwl3945 0000:08:00.0: loaded firmware version 15.32.2.9
[   25.857322] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x1f0-0x1f7 0x370-0x37f
[   25.859273] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3ff 0x4d0-0x4d7
[   25.860928] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   25.861706] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   25.862444] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xc7fff 0xd0000-0xd3fff 0xe0000-0xfffff
[   25.862485] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: clean.
[   25.862523] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: excluding 0x60000000-0x60ffffff
[   25.862558] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[ 1211.333923] audit_printk_skb: 42 callbacks suppressed
[ 1211.333927] type=1400 audit(1358965057.774:26): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/telepathy/mission-control-5" name="/usr/share/gvfs/remote-volume-monitors/" pid=2310 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[ 1806.961119] snd-usb-audio: probe of 2-2:1.0 failed with error -5
[ 1806.961196] usbcore: registered new interface driver snd-usb-audio
[ 1814.703108] snd-usb-audio: probe of 2-2:1.0 failed with error -5
sudo: /etc/init.d/sl-modem-daemon: command not found
    Release Date: 12/15/2006
        Serial services are supported (int 14h)
    Manufacturer: Hewlett-Packard
    Product Name: HP Compaq nc6320 (RM124UT#ABA)
    Serial Number: CNU7090N8Y
    Manufacturer: Hewlett-Packard
    Product Name: 30AA
    Serial Number: Not Specified
    Manufacturer: Hewlett-Packard
    Serial Number: CNU7090N8Y
    Manufacturer: Intel(R)
    Serial Number: Not Specified
    Manufacturer: AD00000000000000
    Serial Number: 00002080
    Manufacturer: 7F7F7F0B00000000
    Serial Number: 7199348C
usbhid                 41937  0 
hid                    77428  1 usbhid
snd_usb_audio         101566  0 
snd_usbmidi_lib        24603  1 snd_usb_audio
snd_seq_dummy          12686  0 
snd_hda_codec_si3054    12864  1 
snd_hda_codec_analog    75395  1 
snd_hda_intel          32765  4 
snd_hda_codec         109562  3 snd_hda_codec_si3054,snd_hda_codec_analog,snd_hda_intel
snd_hwdep              13276  2 snd_usb_audio,snd_hda_codec
snd_pcm                80916  5 snd_usb_audio,snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec
btusb                  17948  2 
bluetooth             158479  23 rfcomm,bnep,btusb
snd_seq_midi           13132  0 
snd_rawmidi            25424  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  3 snd_seq_dummy,snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  4 snd_seq_dummy,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62218  19 snd_usb_audio,snd_usbmidi_lib,snd_hda_codec_si3054,snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
Terminating processes: 1861.
Unloading ALSA sound driver modules: snd-usb-audio snd-usbmidi-lib snd-seq-dummy snd-hda-codec-si3054 snd-hda-codec-analog snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc (failed: modules still loaded: snd-hda-codec-si3054 snd-hda-codec-analog snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc).
Loading ALSA sound driver modules: snd-usb-audio snd-usbmidi-lib snd-seq-dummy snd-hda-codec-si3054 snd-hda-codec-analog snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
  *-multimedia            
       description: Audio device
       product: N10/ICH 7 Family High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=snd_hda_intel latency=0
       resources: irq:45 memory:e8580000-e8583fff



I don't know if any of this helps.

---

### Post by SteamDonkey74 on 2013-01-24
Perhaps I am missing a driver? The more I look around the more it seems that drivers are often the problem with Creative Labs sound cards. I have not found a driver for a Sound Blaster X-Fi Notebook card.

---

### Post by SteamDonkey74 on 2013-01-25
I can't get anywhere on this and it appears nobody else knows, either. Fortunately, I can still return the card for store credit so I think I will.

Thanks for looking.

---

### Post by bigstonebang on 2013-02-25
did you make any head way or give up? 

I have the same x-fi HD USB, and im trying to get it to work on android.

At this point im trying to find ANYTHING on this card! it seems to be very rare, or people dont do crazy things with it.

I found one way to get it to work but its a closed source APP(the app is made for recording, and it only works in the APP, i need full global output) and the dev wont give me much info.

ive been trying cynogenmod but it behaves just like the stock rom. oh this is on the nexus 7 by the way.

If you can share ANY info on this sound card that would be AWESOME.

---

