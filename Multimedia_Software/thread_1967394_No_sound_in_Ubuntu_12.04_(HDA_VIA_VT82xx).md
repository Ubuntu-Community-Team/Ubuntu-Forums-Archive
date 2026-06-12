---
title: "No sound in Ubuntu 12.04 (HDA VIA VT82xx)"
date: 2012-04-28
forum: Multimedia Software
---

### Post by na5h on 2012-04-28
I apologize for making a new thread, but I haven't been able to find any solutions in the other threads regarding problems with sound.

The laptop seems to recognize my sound card. In fact, everything looks fine...yet, no sound! Nothing is muted in alsamixer and all channels are at full volume...the headphone jack actually works, but the volume is way too low.

This is my output of **aplay -l**
```
**** List of PLAYBACK Hardware Devices ****
card 0: VT82xx [HDA VIA VT82xx], device 0: VT1708 Analog [VT1708 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: VT82xx [HDA VIA VT82xx], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

This is my output of **lspci -v**
```
04:01.0 Audio device: VIA Technologies, Inc. VT8237A/VT8251 HDA Controller (rev 10)
	Subsystem: Fujitsu Technology Solutions Device 10d9
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at d9000000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel

```

Any ideas? The sound stopped working after my upgrade to 12.04. I also tried running it from a Live CD with the same results...

---

### Post by xyzzyman on 2012-04-28
As it's also occuring on a 12.04 LiveCD, it's most likely a problem with the new jack parsing system put into 12.04. Previously it was kind of generic for Intel HDA spec cards, especially if you had a subwoofer, etc in your laptop. Now it detects things, has seperate volume for headphones/internal speakers, but it's not suprising some models may need to be tweaked. So to start can you do this:

[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

As that will generate a very detailed report.

---

### Post by mörgæs on 2012-04-28
Moved to the multimedia forum.

---

### Post by na5h on 2012-04-28
Here is the detailed report:
```
!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Sat Apr 28 09:44:17 UTC 2012


!!Linux Distribution
!!------------------

Ubuntu 12.04 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"


!!DMI Information
!!---------------

Manufacturer:      FUJITSU SIEMENS
Product Name:      AMILO La1703
Product Version:   1.0


!!Kernel Information
!!------------------

Kernel release:    3.2.0-24-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         athlon
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

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [VT82xx         ]: HDA-Intel - HDA VIA VT82xx
                      HDA VIA VT82xx at 0xd9000000 irq 17


!!PCI Soundcards installed in the system
!!--------------------------------------

04:01.0 Audio device: VIA Technologies, Inc. VT8237A/VT8251 HDA Controller (rev 10)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

04:01.0 0403: 1106:3288 (rev 10)
	Subsystem: 1734:10d9


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
	align_buffer_size : Y
	bdl_pos_adj : 32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
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

Codec: VIA VT1708
Address: 0
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x11061708
Subsystem Id: 0x173410d9
Revision Id: 0x100700
No Modem Function Group found
Default PCM:
    rates [0x0]:
    bits [0x0]:
    formats [0x0]:
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x10 [Audio Output] wcaps 0x411: Stereo
  Device: name="VT1708 Analog", type="Audio", device=0
  Converter: stream=0, channel=0
  PCM:
    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
    bits [0xa]: 16 24
    formats [0x1]: PCM
  Power states:  D0 D1
  Power: setting=D0, actual=D0
Node 0x11 [Audio Output] wcaps 0x411: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
    bits [0xa]: 16 24
    formats [0x1]: PCM
  Power states:  D0 D1
  Power: setting=D0, actual=D0
Node 0x12 [Audio Output] wcaps 0x411: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
    bits [0xa]: 16 24
    formats [0x1]: PCM
  Power states:  D0 D1
  Power: setting=D0, actual=D0
Node 0x13 [Audio Output] wcaps 0x411: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
    bits [0xa]: 16 24
    formats [0x1]: PCM
  Power states:  D0 D1
  Power: setting=D0, actual=D0
Node 0x14 [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
    bits [0xa]: 16 24
    formats [0x5]: PCM AC3
Node 0x15 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Control: name="Capture Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Capture Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Device: name="VT1708 Analog", type="Audio", device=0
  Amp-In caps: ofs=0x00, nsteps=0x14, stepsize=0x06, mute=1
  Amp-In vals:  [0x06 0x06]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x440]: 48000 192000
    bits [0xa]: 16 24
    formats [0x1]: PCM
  Power states:  D0 D1
  Power: setting=D0, actual=D0
  Connection: 1
     0x18
Node 0x16 [Audio Input] wcaps 0x100311: Stereo Digital
  Converter: stream=0, channel=0
  SDI-Select: 0
  Digital: Validity
  Digital category: 0x0
  PCM:
    rates [0x1f0]: 32000 44100 48000 88200 96000
    bits [0xa]: 16 24
    formats [0x5]: PCM AC3
  Connection: 1
     0x26
Node 0x17 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="PCM Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="PCM Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Control: name="Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x06, mute=1
  Amp-In vals:  [0x1f 0x1f] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 6
     0x10 0x24 0x1d 0x1e 0x21 0x13
Node 0x18 [Audio Selector] wcaps 0x300101: Stereo
  Control: name="Input Source", index=0, device=0
  Connection: 5
     0x17 0x24 0x1d* 0x1e 0x21
Node 0x19 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x1b, nsteps=0x1b, stepsize=0x06, mute=1
  Amp-Out vals:  [0x80 0x80]
  Connection: 1
     0x11
Node 0x1a [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x1b, nsteps=0x1b, stepsize=0x06, mute=1
  Amp-Out vals:  [0x80 0x80]
  Connection: 1
     0x12
Node 0x1b [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x1b, nsteps=0x1b, stepsize=0x06, mute=1
  Amp-Out vals:  [0x80 0x80]
  Connection: 1
     0x13
Node 0x1c [Pin Complex] wcaps 0x40010d: Stereo Amp-Out
  Amp-Out caps: N/A
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000001c: OUT HP Detect
  Pin Default 0x410110f2: [N/A] Line Out at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x2
  Pin-ctls: 0x00:
  Connection: 1
     0x19
Node 0x1d [Pin Complex] wcaps 0x400101: Stereo
  Pincap 0x00000334: IN OUT Detect
    Vref caps: HIZ 50
  Pin Default 0x01a190f0: [Jack] Mic at Ext Rear
    Conn = 1/8, Color = Pink
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x21: IN VREF_50
  Connection: 1
     0x1a
Node 0x1e [Pin Complex] wcaps 0x400101: Stereo
  Pincap 0x00000334: IN OUT Detect
    Vref caps: HIZ 50
  Pin Default 0x418130fe: [N/A] Line In at Ext Rear
    Conn = 1/8, Color = Blue
    DefAssociation = 0xf, Sequence = 0xe
  Pin-ctls: 0x00: VREF_HIZ
  Connection: 1
     0x19
Node 0x1f [Pin Complex] wcaps 0x40010d: Stereo Amp-Out
  Control: name="Front Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Front Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x1b, nsteps=0x1b, stepsize=0x06, mute=1
  Amp-Out vals:  [0x1b 0x1b]
  Pincap 0x0000001c: OUT HP Detect
  Pin Default 0x110140f0: [Jack] Line Out at Int Rear
    Conn = 1/8, Color = Green
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x17
Node 0x20 [Pin Complex] wcaps 0x40010d: Stereo Amp-Out
  Control: name="Headphone Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Headphone Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x1b, nsteps=0x1b, stepsize=0x06, mute=1
  Amp-Out vals:  [0x1b 0x1b]
  Pincap 0x0000001c: OUT HP Detect
  Pin Default 0x022140f0: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Green
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0xc0: OUT HP
  Connection: 1
     0x17
Node 0x21 [Pin Complex] wcaps 0x400101: Stereo
  Pincap 0x00000334: IN OUT Detect
    Vref caps: HIZ 50
  Pin Default 0x42a190f0: [N/A] Mic at Ext Front
    Conn = 1/8, Color = Pink
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00: VREF_HIZ
  Connection: 1
     0x1b
Node 0x22 [Pin Complex] wcaps 0x400101: Stereo
  Pincap 0x00000014: OUT Detect
  Pin Default 0x410160f1: [N/A] Line Out at Ext Rear
    Conn = 1/8, Color = Orange
    DefAssociation = 0xf, Sequence = 0x1
  Pin-ctls: 0x00:
  Connection: 1
     0x1a
Node 0x23 [Pin Complex] wcaps 0x400101: Stereo
  Pincap 0x00000014: OUT Detect
  Pin Default 0x410120f4: [N/A] Line Out at Ext Rear
    Conn = 1/8, Color = Grey
    DefAssociation = 0xf, Sequence = 0x4
  Pin-ctls: 0x00:
  Connection: 1
     0x1b
Node 0x24 [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x593301f7: [N/A] CD at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x7
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
Node 0x25 [Pin Complex] wcaps 0x400301: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x474411f0: [N/A] SPDIF Out at Ext Rear Panel
    Conn = RCA, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Connection: 1
     0x14
Node 0x26 [Pin Complex] wcaps 0x400201: Stereo Digital
  Pincap 0x00010030: IN OUT EAPD
  EAPD 0x0:
  Pin Default 0x47c421f0: [N/A] SPDIF In at Ext Rear Panel
    Conn = RCA, Color = Grey
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
Node 0x27 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Control: name="Capture Volume", index=1, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Capture Switch", index=1, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x14, stepsize=0x06, mute=1
  Amp-In vals:  [0x00 0x00]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x440]: 48000 192000
    bits [0xa]: 16 24
    formats [0x1]: PCM
  Power states:  D0 D1
  Power: setting=D0, actual=D0
  Connection: 1
     0x21
Codec: Motorola Si3054
Address: 1
MFG Function Id: 0x2 (unsol 1)
Vendor Id: 0x10573055
Subsystem Id: 0x10573055
Revision Id: 0x100700
Modem Function Group: 0x1
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw---T  1 root audio 116,  8 Apr 28 12:41 /dev/snd/controlC0
crw-rw---T  1 root audio 116,  7 Apr 28 12:41 /dev/snd/hwC0D0
crw-rw---T  1 root audio 116,  6 Apr 28 12:41 /dev/snd/hwC0D1
crw-rw---T  1 root audio 116,  5 Apr 28 12:41 /dev/snd/pcmC0D0c
crw-rw---T  1 root audio 116,  4 Apr 28 12:41 /dev/snd/pcmC0D0p
crw-rw---T  1 root audio 116,  3 Apr 28 12:41 /dev/snd/pcmC0D6c
crw-rw---T  1 root audio 116,  2 Apr 28 12:41 /dev/snd/pcmC0D6p
crw-rw---T  1 root audio 116,  1 Apr 28 12:41 /dev/snd/seq
crw-rw---T  1 root audio 116, 33 Apr 28 12:41 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Apr 28 12:41 .
drwxr-xr-x 3 root root 240 Apr 28 12:41 ..
lrwxrwxrwx 1 root root  12 Apr 28 12:41 pci-0000:04:01.0 -> ../controlC0


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: VT82xx [HDA VIA VT82xx], device 0: VT1708 Analog [VT1708 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: VT82xx [HDA VIA VT82xx], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: VT82xx [HDA VIA VT82xx], device 0: VT1708 Analog [VT1708 Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: VT82xx [HDA VIA VT82xx], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [VT82xx]

Card hw:0 'VT82xx'/'HDA VIA VT82xx at 0xd9000000 irq 17'
  Mixer name	: 'VIA VT1708'
  Components	: 'HDA:11061708,173410d9,00100700 HDA:10573055,10573055,00100700'
  Controls      : 19
  Simple ctrls  : 12
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 27
  Mono: Playback 27 [100%] [6.75dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 27
  Mono:
  Front Left: Playback 27 [100%] [0.00dB] [on]
  Front Right: Playback 27 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [14.00dB] [on]
  Front Right: Playback 31 [100%] [14.00dB] [on]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 27
  Mono:
  Front Left: Playback 27 [100%] [0.00dB] [on]
  Front Right: Playback 27 [100%] [0.00dB] [on]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-40.25dB] [off]
  Front Right: Playback 0 [0%] [-40.25dB] [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 20
  Front Left: Capture 6 [30%] [10.50dB] [on]
  Front Right: Capture 6 [30%] [10.50dB] [on]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 20
  Front Left: Capture 0 [0%] [0.00dB] [on]
  Front Right: Capture 0 [0%] [0.00dB] [on]
Simple mixer control 'Caller ID',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Mic' 'Stereo Mixer'
  Item0: 'Mic'
Simple mixer control 'Jack Detect',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Loopback Mixing',0
  Capabilities: enum
  Items: 'Disabled' 'Enabled'
  Item0: 'Disabled'
Simple mixer control 'Off-hook',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]


!!Alsactl output
!!-------------

--startcollapse--
state.VT82xx {
	control.1 {
		iface MIXER
		name 'Front Playback Volume'
		value.0 27
		value.1 27
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 27'
			dbmin -4725
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
		name 'PCM Playback Volume'
		value.0 31
		value.1 31
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 31'
			dbmin -4025
			dbmax 1400
			dbvalue.0 1400
			dbvalue.1 1400
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
		name 'Headphone Playback Volume'
		value.0 27
		value.1 27
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 27'
			dbmin -4725
			dbmax 0
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.6 {
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
	control.7 {
		iface MIXER
		name 'Loopback Mixing'
		value Disabled
		comment {
			access 'read write'
			type ENUMERATED
			count 1
			item.0 Disabled
			item.1 Enabled
		}
	}
	control.8 {
		iface MIXER
		name 'Capture Volume'
		value.0 6
		value.1 6
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 20'
			dbmin 0
			dbmax 3500
			dbvalue.0 1050
			dbvalue.1 1050
		}
	}
	control.9 {
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
	control.10 {
		iface MIXER
		name 'Capture Volume'
		index 1
		value.0 0
		value.1 0
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 20'
			dbmin 0
			dbmax 3500
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.11 {
		iface MIXER
		name 'Capture Switch'
		index 1
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
		name 'Input Source'
		value Mic
		comment {
			access 'read write'
			type ENUMERATED
			count 1
			item.0 Mic
			item.1 'Stereo Mixer'
		}
	}
	control.13 {
		iface MIXER
		name 'Mic Playback Volume'
		value.0 0
		value.1 0
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 31'
			dbmin -4025
			dbmax 1400
			dbvalue.0 -4025
			dbvalue.1 -4025
		}
	}
	control.14 {
		iface MIXER
		name 'Mic Playback Switch'
		value.0 false
		value.1 false
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.15 {
		iface MIXER
		name 'Jack Detect'
		value false
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.16 {
		iface MIXER
		name 'Master Playback Volume'
		value 27
		comment {
			access 'read write'
			type INTEGER
			count 1
			range '0 - 27'
			dbmin 0
			dbmax 675
			dbvalue.0 675
		}
	}
	control.17 {
		iface MIXER
		name 'Master Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.18 {
		iface MIXER
		name 'Off-hook Switch'
		value false
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.19 {
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
usbhid
hid
via
drm
vesafb
joydev
arc4
rtl8187
mac80211
cfg80211
eeprom_93cx6
psmouse
k8temp
i2c_viapro
serio_raw
shpchp
rfcomm
bnep
bluetooth
parport_pc
ppdev
binfmt_misc
video
snd_hda_codec_si3054
snd_hda_codec_via
mac_hid
snd_hda_intel
snd_hda_codec
snd_hwdep
snd_pcm
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
snd_seq
snd_timer
snd_seq_device
snd
soundcore
snd_page_alloc
lp
parport
via_rhine
pata_via
sata_via


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x1c 0x410110f2
0x1d 0x01a190f0
0x1e 0x418130fe
0x1f 0x110140f0
0x20 0x022140f0
0x21 0x42a190f0
0x22 0x410160f1
0x23 0x410120f4
0x24 0x593301f7
0x25 0x474411f0
0x26 0x47c421f0

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:

/sys/class/sound/hwC0D1/init_pin_configs:

/sys/class/sound/hwC0D1/driver_pin_configs:

/sys/class/sound/hwC0D1/user_pin_configs:

/sys/class/sound/hwC0D1/init_verbs:


!!ALSA/HDA dmesg
!!------------------

[   23.839491] lp: driver loaded but no devices found
[   24.022797] snd_hda_intel 0000:04:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   24.022914] snd_hda_intel 0000:04:01.0: setting latency timer to 64
[   24.022927] snd_hda_intel 0000:04:01.0: PCI: Disallowing DAC for device
[   24.029841] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro


```

or alternatively:
[http://www.alsa-project.org/db/?f=d13acfdd8f0a3efe2fb747ea56f590d2e84bc8e6](http://www.alsa-project.org/db/?f=d13acfdd8f0a3efe2fb747ea56f590d2e84bc8e6)

---

### Post by xyzzyman on 2012-04-28
Okay. It's a long shot but in sound settings is there other outputs to choose other than anything like an hdmi or digital output to switch to? I see in Fedora people have had issues with a similiar card and had to be switched to an amped output.

From what I see your mixer settings are all proper though, but your VT1708 chip has alot of bug fixes in Alsa 1.0.25 [http://www.alsa-project.org/main/index.php/Changes_v1.0.24_v1.0.25](http://www.alsa-project.org/main/index.php/Changes_v1.0.24_v1.0.25) (You're on 1.0.24 right now.

You can easily upgrade to the latest ALSA which may take care of it by following the instructions on: [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

---

### Post by na5h on 2012-04-28
I tried upgrading to the latest ALSA using DKMS, but that just made my outputs go "dummy output"...I uninstalled it and things went back to "normal".

Here is a screenshot of my outputs:

---

### Post by LucasQueiroz on 2012-04-28
I too am having the same issues. If I can add some more info, here is my alsa-info output.

[http://www.alsa-project.org/db/?f=b65158fc8772b698de4fff7c4edbe76a955ca828](http://www.alsa-project.org/db/?f=b65158fc8772b698de4fff7c4edbe76a955ca828)

Notice that we don't have the same model of sound board, but both are Intel ones.

---

### Post by mikiemorales on 2012-04-28
> **LucasQueiroz said:**
> I too am having the same issues. If I can add some more info, here is my alsa-info output.

[http://www.alsa-project.org/db/?f=b65158fc8772b698de4fff7c4edbe76a955ca828](http://www.alsa-project.org/db/?f=b65158fc8772b698de4fff7c4edbe76a955ca828)

Notice that we don't have the same model of sound board, but both are Intel ones.

I'm having the same. I have a docking station and for some reason I can#t use the speakers connected to the dock, they won't work either from the laptop. I noticed, though, I can use my headphones plug with no issues.


Miguel

---

### Post by na5h on 2012-04-30
*bump bump bum--TILT*

---

### Post by Tomtompiper on 2012-04-30
Same problem, solved a Grub start up problem, followed by no video, and now this, They should have a warning on the install update button, *Choosing this option will render your computer unusable."

[http://www.alsa-project.org/db/?f=75caaf836333f9a287f09bf0cdba60c304806cf7](http://www.alsa-project.org/db/?f=75caaf836333f9a287f09bf0cdba60c304806cf7)


Any help would be appreciated.

---

### Post by na5h on 2012-04-30
Problem solved! I downgraded my kernel to a previous one (as my sound was working fine in Ubuntu 11.10)...

---

### Post by Daimonea on 2012-04-30
Hi!

I have exactly the same notebook and problem as you have, @na5h. 
Could you please describe how you did the kernel downgrade?

On Ubuntu 11.10 sound worked here too. With the only restriction that when i use the headphone jack, the speaker doesn't shut up. :)

But that's still better than having no sound at all.

lg, michael

---

### Post by Tomtompiper on 2012-04-30
Logged back on after a session on Mint and the sound was back. I had not done anything?  One last problem the side bar is stuck out, I will work on that. :p

---

### Post by na5h on 2012-04-30
@Daimonea: Yes, of course...I'll post some step-by-step instructions in a jiffy, just gotta tie up a few loose ends first...

---

### Post by Daimonea on 2012-04-30
[-o<

Thank you so much, na5h. :)

---

### Post by na5h on 2012-04-30
For those of you that are interested in trying my little fix:
There are probably many different ways to do all this...this is just how I did it. I would also like to point out that I'm not that used to playing around with kernels and with GRUB, so if you choose to follow these instructions, please do so at your own risk! 
Here goes...

**1. CHECK IF THERE ARE ANY PREVIOUS KERNELS AVAILABLE**
If you upgraded from 11.10 then you might still have an older kernel installed (I think)...in that case you wont have to download anything. 

Open up a terminal (CTRL+ALT+T) and run the following command to check if there are any previous kernels available in the GRUB list: 
```
cat /boot/grub/grub.cfg  |grep menuentry
```
See if you can find any kernels that are numbered 3.0.xx-xx, for instance "Linux 3.0.0-17-generic". The ones that start with 3.2 are too new! If there is a suitable kernel available, go to step 3.


**2. DOWNLOAD AND INSTALL AN OLDER KERNEL:**
Go to [http://packages.ubuntu.com/oneiric-updates/linux-image]("http://packages.ubuntu.com/oneiric-updates/linux-image") and download an older kernel (change the "oneiric" part of the address if you want a kernel from an even older release).

Select a generic image (for instance linux-image-3.0.0-13-generic) and download it to your home folder (click on the right image, then scroll down to the bottom of the next page and download the right package for your architecture. The amd64 is for 64-bit versions and the i386 is for 32-bit versions).

Open a terminal and run the following command to install the downloaded kernel:
```
sudo dpkg -i package_name
```
For instance, "sudo dpkg -i linux-image-3.0.0-13-generic_3.0.0-13.22_i386.deb".

Update GRUB by running the following command:
```
sudo update-grub
```


**3. BOOT INTO THE OLDER KERNEL TO SEE THAT EVERYTHING IS WORKING THE WAY IT SHOULD**
Reboot you computer and hold down the Shift-key before the GRUB menu appears (or before the Ubuntu-logo starts to "load", if Ubuntu is your only operating system)

Select "previous linux versions" from the GRUB menu and boot into the older kernel of your choice.

**4. REMOVE THE NEWER KERNELS**
Use Synaptic Package manager (not installed by default, can be found in the Software Center) to remove the newer kernels:
Type "linux-image" in the search box, scroll down and mark the newer images for complete removal (right-click->mark for complete removal), then klick on "Apply". 

Update GRUB by running the following command:
```
sudo update-grub
```

**ENJOY!** :)

P.S. I think Ubuntu installs new kernels by default or something...so, um...you should probably just stick to the kernel you just installed/picked and not install newer kernels with update manager?

> On Ubuntu 11.10 sound worked here too. With the only restriction that when i use the headphone jack, the speaker doesn't shut up.
Yeah...I had that problem too. You can use alsamixer to mute the speaker while using your headphones: 
Open a terminal and type "alsamixer", then use the arrow keys to change the volume of the different channels (the speaker will shut up if you mute the "front" channel). No permanent fix...but it works!

---

### Post by rickbeton on 2012-04-30
Same problem happened on my laptop after upgrading to 12.04. Here's the Alsa report:

[http://www.alsa-project.org/db/?f=60574c1908d880243dea0c00086efc71a99c8cb9](http://www.alsa-project.org/db/?f=60574c1908d880243dea0c00086efc71a99c8cb9)

Rick

PS: More specifically:
* the HDMI output works fine
* there is SPDIF output but I haven't tested it
* when the headphones are unplugged, the built-in speakers work fine
* when headphones are plugged in, this is evident from the changed sound control panel. But the headphones **don't work now**.
* My bluetooth headphones do still work fine, however.

---

### Post by fijired2 on 2012-04-30
> **na5h said:**
> 
Yeah...I had that problem too. You can use alsamixer to mute the speaker while using your headphones: 
Open a terminal and type "alsamixer", then use the arrow keys to change the volume of the different channels (the speaker will shut up if you mute the "front" channel). No permanent fix...but it works!

Thanks for this - alsamixer had my Master volume as "0" so changing that brought my sound back!

---

### Post by mörgæs on 2012-05-01
Na5h, thanks for posting the solution. 

Please mark the thread 'solved' using 'thread tools'.

---

### Post by Daimonea on 2012-05-01
Thank you very much for this tutorial and the alsamixer-tip, na5h!

Great work!

lg, michael

---

### Post by na5h on 2012-05-01
You're welcome! :) I'm glad I could help!

---

### Post by xyzzyman on 2012-05-01
The jack detection is in the kernel (A lot of which was back ported from kernel 3.3) so you should file a bug report against it.

---

### Post by rickbeton on 2012-05-02
The alsamixer suggestion works for me, too.

Thanks.

---

### Post by timjohn7 on 2012-05-03
Same problem, some days after upgrading from 11.10 (sound worked fine) to 12.04 (sound worked fine for 6 days).  Now I have the "Dummy Output" as my only hardware choice.
None of the recommended fixes work for me, but here's an interesting variation... I logged out and back in as a different user... sound is fine with 3 hardware device choices.
Logged back in as myself (hoping...) sound still broken.

---

### Post by buntya on 2012-05-04
[SOLVED]

I have the same issue. No issue until I had 11.10.


HP-Compaq-8710w:/usr/bin$ sudo gnome-alsamixer

(gnome-alsamixer:2891): GLib-GObject-CRITICAL **: g_type_instance_get_private: assertion `instance != NULL && instance->g_class != NULL' failed


lspci -v

HP-C00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
        Subsystem: Hewlett-Packard Company Device 30c3
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at e8044000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel modules: snd-hda-intel

compaq-8710w:/usr/bin$ sudo aplay -l
aplay: device_list:252: no soundcards found...

---

### Post by buntya on 2012-05-05
In my case I had an incompatible alsa-hda-dkms installed. 
I removed alsa-hda-dkms(alsa-hda-dkms 0.201205021650~precise1) and rebooted. Sound is back. Weirdo.

---

### Post by timjohn7 on 2012-05-05
I deselected the device ticked on the hardware tag, selected None, then reselected Analogue Stereo Device and my sound was restored as before, except that I now do not have a panel indicator.

---

### Post by tolubalogun on 2012-05-12
Hello folks, don't be too hard.

install pvaucontrol from terminal

run it and go to the config tap and choose audio duplex

problem solved

---

### Post by tjg on 2012-07-18
Heyy,
 
I see this as resolved, but for all of you to spread the word --
 
Without downgrading your kernel, this is what worked for me on a fresh install of Ubunut 12.04 on a VM in VMware workstation:
 
Basically, using pavucontrol gives you access to all of the previous sound settings that were removed from the default pulseaudio sound settings app. (Setting audio Output to "Analog Output" for example, which fixes 99% of no audio in VM issues and "cant attach audio device because device is out of range" VM issues)
 
so: sudo apt-get install pavucontrol
 
then: pavucontrol
 
to run it.
 
This is a much more granular control over the sound settings and much similar to the sound settings found in 11.10. 
 
I hope this helps others out there! What a headache!
 
 
Thanks,
 
Tjg
 
EDIT:: Go figure, I didn't even see the previous reply that has this exact solution... Apologies, but at least I can vouch that it works to solve VM problems as well.

---

### Post by scyntl on 2012-08-04
just wanted to post that i too had no sound after a fresh 12.04 install, but after about 15min the track i had playing in audacious finished and i heard the familiar click of the speakers (an annoying click that's been around since ~11.04; i guess i should check the forums about that...). I turned up the voume (again) and the sound was back. . . confused, but happy.

---

### Post by Rinre on 2012-10-12
I had the same problem, or at least very similar:
On my girlfriend's brand new ASUS 1225C, with Ubuntu 12.04 preinstalled, the speakers worked fine at first. The second time she started it up (this time with the battery plugged in, don't know if that makes a difference), the sound only worked in headphones/external speakers. 

After looking around a bit, I found this ingenious solution:
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1037763](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1037763)

That is, I upgraded the ALSA dkms package through the link given in the bug report ([https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems))

After I rebooted the computer, the sound works perfectly (also the switch between speakers and headphones., i.e. the speakers are silent when headphones are plugged in).

Seems easier, to me at least, than downgrading the Kernel or something drastic like that. Hope this helps someone :O)

---

### Post by yrohinkumar on 2012-12-12
I am having the same problem on Dell D520... I had it in 12.04 after upgrade...and it is continuing after 12.10 upgrade... I don't want to downgrade the kernel... and pavucontrol solution didn't work for me :( 

My sound card is not listed in the hardware...I can't increase or decrease system volume...

Any other ideas?

---

### Post by Crowrider7 on 2013-05-26
I myself have about had it with trying to get answers to questions about ubuntu sound problems. Everyone seems to have the same problem, but nobody can answer this simple question directly. Why when I turn on my $2,000.00 HP Desktop computer, I do not have any sound in ubuntu? I am running 12.04 and 13.04 side by side, and both have the same sound problems. This should not be such a hard thing to fix. There are 50 different people telling you 50 different ways to fix the problem, and nothing seems to work. It's just crazy and uncalled for any OS system not to be able to supply direct answers to direct questions. I have been a programmer for over 30 years now, and I know a Jack-Leg system when I see it. Linux ubuntu is just plain pitiful when it comes to support issues. Cary @ [EMAIL="clwilkins7@aol.com"]clwilkins7@aol.com[/EMAIL]

---

