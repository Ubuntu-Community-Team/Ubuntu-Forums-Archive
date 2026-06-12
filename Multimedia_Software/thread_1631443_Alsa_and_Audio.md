---
title: "Alsa and Audio"
date: 2010-11-26
forum: Multimedia Software
---

### Post by u2v2a0 on 2010-11-26
I have recenlty did a clean install of 10.10 and my audio was no longer working, after removing pulseaudio because i could not control my volume and it was too loud, I install alsa which works, i can change volume but only with alsa mixer, is there a way I can set my shortcuts to control the master volume for alsa mixer?

or are there known fixes for pulseaudio, I have tried reinstalling it but now it does not show my output speakers and only shows dummy output or something like that. 

Dell inspiron e1705
ubuntu 10.10
will provide more if you tell me where to find the info

---

### Post by lidex on 2010-11-27
> **u2v2a0 said:**
> I have recenlty did a clean install of 10.10 and my audio was no longer working, after removing pulseaudio because i could not control my volume and it was too loud, I install alsa which works, i can change volume but only with alsa mixer, is there a way I can set my shortcuts to control the master volume for alsa mixer?

or are there known fixes for pulseaudio, I have tried reinstalling it but now it does not show my output speakers and only shows dummy output or something like that. 

Dell inspiron e1705
ubuntu 10.10
will provide more if you tell me where to find the info
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by Yellow Pasque on 2010-11-27
If you want to run without pulse, use this to get media keys and volume control back: [https://launchpad.net/~dtl131/+archive/ppa](https://launchpad.net/~dtl131/+archive/ppa)

---

### Post by u2v2a0 on 2010-12-13
> **lidex said:**
> Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]


Here is the information from the text doc
sorry it's taken so long to respond had to go back to school without this computer 
Not really sure what you are looking for so here is the whole thing. thanks so much

upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.59
!!################################

!!Script ran on: Tue Dec 14 00:10:56 UTC 2010


!!Linux Distribution
!!------------------

Ubuntu 10.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.10"


!!DMI Information
!!---------------

Manufacturer:      Dell Inc.
Product Name:      MP061                           


!!Kernel Information
!!------------------

Kernel release:    2.6.35-23-generic
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

No sound servers found.


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xdfebc000 irq 44


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:27d8 (rev 01)
	Subsystem: 1028:01cd


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
	beep_mode : 1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1
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

Codec: SigmaTel STAC9200
Address: 0
AFG Function Id: 0x1 (unsol 1)
Vendor Id: 0x83847690
Subsystem Id: 0x102801cd
Revision Id: 0x102201
No Modem Function Group found
Default PCM:
    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=1
GPIO: io=4, o=0, i=0, unsolicited=1, wake=1
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[2]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[3]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Node 0x02 [Audio Output] wcaps 0xd0401: Stereo
  Device: name="STAC92xx Analog", type="Audio", device=0
  Converter: stream=5, channel=0
  Power: setting=D0, actual=D0
  Delay: 13 samples
Node 0x03 [Audio Input] wcaps 0x1d0541: Stereo
  Device: name="STAC92xx Analog", type="Audio", device=0
  Converter: stream=0, channel=0
  SDI-Select: 0
  Power: setting=D0, actual=D0
  Delay: 13 samples
  Connection: 1
     0x0a
  Processing caps: benign=0, ncoeff=0
Node 0x04 [Audio Input] wcaps 0x140311: Stereo Digital
  Converter: stream=0, channel=0
  SDI-Select: 0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Delay: 4 samples
  Connection: 1
     0x08
Node 0x05 [Audio Output] wcaps 0x40211: Stereo Digital
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Control: name="IEC958 Default PCM Playback Switch", index=0, device=0
  Device: name="STAC92xx Digital", type="SPDIF", device=1
  Converter: stream=5, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x1e0]: 44100 48000 88200 96000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Delay: 4 samples
Node 0x06 [Vendor Defined Widget] wcaps 0xf30201: Stereo Digital
  Delay: 3 samples
Node 0x07 [Audio Selector] wcaps 0x300901: Stereo R/L
  Connection: 3
     0x02* 0x08 0x0a
Node 0x08 [Pin Complex] wcaps 0x430681: Stereo Digital
  Pincap 0x00010024: IN EAPD Detect
  EAPD 0x0:
  Pin Default 0x40c003fa: [N/A] SPDIF In at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0xa
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Delay: 3 samples
Node 0x09 [Pin Complex] wcaps 0x400301: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x01441340: [Jack] SPDIF Out at Ext Rear
    Conn = RCA, Color = Black
    DefAssociation = 0x4, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Connection: 2
     0x05* 0x0a
Node 0x0a [Audio Selector] wcaps 0x30090d: Stereo Amp-Out R/L
  Control: name="Capture Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Capture Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x00, nsteps=0x0f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x80 0x80]
  Connection: 1
     0x0c
Node 0x0b [Audio Selector] wcaps 0x300105: Stereo Amp-Out
  Control: name="Master Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Master Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: N/A
  Amp-Out vals:  [0x8f 0x8f]
  Connection: 1
     0x07
Node 0x0c [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Control: name="Mux Capture Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x00, nsteps=0x04, stepsize=0x27, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 5
     0x10* 0x0f 0x0e 0x0d 0x12
Node 0x0d [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x0000003f: IN OUT HP Detect Trigger ImpSense
  Pin Default 0x0421121f: [Jack] HP Out at Ext Right
    Conn = 1/8, Color = Black
    DefAssociation = 0x1, Sequence = 0xf
  Pin-ctls: 0x00:
  Unsolicited: tag=01, enabled=1
  Connection: 1
     0x0b
Node 0x0e [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x0000003f: IN OUT HP Detect Trigger ImpSense
  Pin Default 0x90170310: [Fixed] Speaker at Int N/A
    Conn = Analog, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x0b
Node 0x0f [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x00000037: IN OUT Detect Trigger ImpSense
  Pin Default 0x90170310: [Fixed] Speaker at Int N/A
    Conn = Analog, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x0b
Node 0x10 [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x00001737: IN OUT Detect Trigger ImpSense
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x04a11020: [Jack] Mic at Ext Right
    Conn = 1/8, Color = Black
    DefAssociation = 0x2, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=02, enabled=1
  Connection: 1
     0x0b
Node 0x11 [Pin Complex] wcaps 0x400104: Mono Amp-Out
  Control: name="LFE Playback Volume", index=0, device=0
    ControlAmp: chs=1, dir=Out, idx=0, ofs=0
  Control: name="LFE Playback Switch", index=0, device=0
    ControlAmp: chs=1, dir=Out, idx=0, ofs=0
  Amp-Out caps: N/A
  Amp-Out vals:  [0x00]
  Pincap 0x00000010: OUT
  Pin Default 0x90170310: [Fixed] Speaker at Int N/A
    Conn = Analog, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x13
Node 0x12 [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x40f003fc: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0xc
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
Node 0x13 [Audio Mixer] wcaps 0x200100: Mono
  Connection: 1
     0x07
Node 0x14 [Beep Generator Widget] wcaps 0x70000c: Mono Amp-Out
  Amp-Out caps: ofs=0x03, nsteps=0x03, stepsize=0x17, mute=1
  Amp-Out vals:  [0x00]
Codec: Conexant ID 2bfa
Address: 1
MFG Function Id: 0x2 (unsol 1)
Vendor Id: 0x14f12bfa
Subsystem Id: 0x14f100c3
Revision Id: 0x90000
Modem Function Group: 0x2
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116,  7 Dec 12 16:30 /dev/snd/controlC0
crw-rw----+ 1 root audio 116,  6 Dec 12 16:30 /dev/snd/hwC0D0
crw-rw----+ 1 root audio 116,  5 Dec 12 16:30 /dev/snd/hwC0D1
crw-rw----+ 1 root audio 116,  4 Dec 12 16:30 /dev/snd/pcmC0D0c
crw-rw----+ 1 root audio 116,  3 Dec 13 18:45 /dev/snd/pcmC0D0p
crw-rw----+ 1 root audio 116,  2 Dec 12 16:30 /dev/snd/pcmC0D1p
crw-rw----+ 1 root audio 116,  1 Dec 12 16:30 /dev/snd/seq
crw-rw----+ 1 root audio 116, 33 Dec 12 16:30 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Dec 12 16:30 .
drwxr-xr-x 3 root root 220 Dec 12 16:30 ..
lrwxrwxrwx 1 root root  12 Dec 12 16:30 pci-0000:00:1b.0 -> ../controlC0


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [Intel]

Card hw:0 'Intel'/'HDA Intel at 0xdfebc000 irq 44'
  Mixer name	: 'SigmaTel STAC9200'
  Components	: 'HDA:83847690,102801cd,00102201 HDA:14f12bfa,14f100c3,00090000'
  Controls      : 13
  Simple ctrls  : 7
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 15 [48%] [-24.00dB] [off]
  Front Right: Playback 15 [48%] [-24.00dB] [off]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 182 [71%] [-14.60dB]
  Front Right: Playback 192 [75%] [-12.60dB]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 24 [77%] [-10.50dB] [on]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 0 [0%] [0.00dB] [off]
  Front Right: Capture 0 [0%] [0.00dB] [off]
Simple mixer control 'Mux',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 4
  Front Left: Capture 0 [0%] [0.00dB]
  Front Right: Capture 0 [0%] [0.00dB]


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
		name 'Master Playback Volume'
		value.0 15
		value.1 15
	}
	control.2 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Master Playback Switch'
		value.0 false
		value.1 false
	}
	control.3 {
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
	control.4 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Capture Switch'
		value.0 false
		value.1 false
	}
	control.5 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 31'
		comment.dbmin -4650
		comment.dbmax 0
		iface MIXER
		name 'LFE Playback Volume'
		value 24
	}
	control.6 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'LFE Playback Switch'
		value true
	}
	control.7 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 4'
		comment.dbmin 0
		comment.dbmax 4000
		iface MIXER
		name 'Mux Capture Volume'
		value.0 0
		value.1 0
	}
	control.8 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Con Mask'
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.9 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.10 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Default'
		value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.11 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Switch'
		value false
	}
	control.12 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Default PCM Playback Switch'
		value false
	}
	control.13 {
		comment.access 'read write user'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 255'
		comment.tlv '0000000100000008ffffec1400000014'
		comment.dbmin -5100
		comment.dbmax 0
		iface MIXER
		name 'PCM Playback Volume'
		value.0 182
		value.1 192
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
parport_pc
ppdev
snd_hda_codec_idt
binfmt_misc
arc4
iwl3945
snd_hda_intel
snd_hda_codec
snd_hwdep
snd_pcm
i915
iwlcore
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
mac80211
snd_seq
drm_kms_helper
snd_timer
snd_seq_device
drm
r852
sm_common
intel_agp
nand
nand_ids
nand_ecc
cfg80211
snd
psmouse
dell_laptop
joydev
i2c_algo_bit
mtd
serio_raw
soundcore
snd_page_alloc
dcdbas
video
output
agpgart
lp
parport
hid_logitech
ff_memless
usbhid
hid
b44
firewire_ohci
sdhci_pci
sdhci
ssb
firewire_core
led_class
mii
crc_itu_t


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x08 0x40f000f0
0x09 0x40f000f1
0x0d 0x0421101f
0x0e 0x90170310
0x0f 0x40f000f2
0x10 0x04a11020
0x11 0x40f000f3
0x12 0x40f000f4

/sys/class/sound/hwC0D0/driver_pin_configs:
0x08 0x40c003fa
0x09 0x01441340
0x0d 0x0421121f
0x0e 0x90170310
0x0f 0x90170310
0x10 0x04a11020
0x11 0x90170310
0x12 0x40f003fc

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:

/sys/class/sound/hwC0D1/init_pin_configs:
0x73 0x016a0000

/sys/class/sound/hwC0D1/driver_pin_configs:

/sys/class/sound/hwC0D1/user_pin_configs:

/sys/class/sound/hwC0D1/init_verbs:


!!ALSA/HDA dmesg
!!------------------

[   20.195023] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   20.195079] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   20.195132]   alloc irq_desc for 44 on node -1
[   20.195135]   alloc kstat_irqs on node -1
[   20.195149] HDA Intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[   20.195186] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   20.195193] ALSA hda_intel.c:2560: chipset global capabilities = 0x4401
[   20.232037] ALSA hda_intel.c:914: codec_mask = 0x3
[   20.232136] ALSA hda_intel.c:1354: codec #0 probed OK
[   20.232171] ALSA hda_intel.c:1354: codec #1 probed OK
[   20.262949] ALSA hda_codec.c:3726: hda_codec: model 'dell-m27' is selected for config 1028:1cd (Dell Inspiron E1705/9400)
[   20.262991] ALSA hda_codec.c:4619: autoconfig: line_outs=3 (0xe/0x11/0xf/0x0/0x0)
[   20.263004] ALSA hda_codec.c:4623:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   20.263008] ALSA hda_codec.c:4627:    hp_outs=1 (0xd/0x0/0x0/0x0/0x0)
[   20.263013] ALSA hda_codec.c:4628:    mono: mono_out=0x0
[   20.263020] ALSA hda_codec.c:4631:    dig-out=0x9/0x0
[   20.263024] ALSA hda_codec.c:4632:    inputs:
[   20.263028] ALSA hda_codec.c:4636:  Mic=0x10
[   20.263031] ALSA hda_codec.c:4638: 
[   20.276761] input: HDA Intel Mic at Ext Right Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   20.276883] input: HDA Intel HP Out at Ext Right Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   20.277394] Skipping EDID probe due to cached edid
--
[   59.884065] Skipping EDID probe due to cached edid
[   60.794997] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x31
[   60.795013] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x5, stream=0x5, channel=0, format=0x31
[   60.795146] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x31
[   61.300083] Skipping EDID probe due to cached edid
--
[   67.452089] Skipping EDID probe due to cached edid
[   68.261675] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   68.261682] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x5
[   73.920039] wlan0: no IPv6 routers present
--
[  207.998177] lo: Disabled Privacy Extensions
[  650.878550] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x31
[  650.878572] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x5, stream=0x5, channel=0, format=0x31
[  650.878583] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x31
[  755.778191] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  755.778198] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x5
[ 1049.213033] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x31
[ 1049.213055] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x5, stream=0x5, channel=0, format=0x31
[ 1049.213065] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x31
[ 1133.969681] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[ 1133.969688] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x5
[ 1136.247089] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x31
[ 1136.247105] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x5, stream=0x5, channel=0, format=0x31
[ 1136.247111] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x31
[ 1238.859574] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[ 1238.859581] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x5
[ 1387.890255] lo: Disabled Privacy Extensions
[ 1798.762073] lo: Disabled Privacy Extensions
[ 1894.692145] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x31
[ 1894.692167] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x5, stream=0x5, channel=0, format=0x31
[ 1894.692178] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x31
[ 1903.204099] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[ 1903.204107] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x5
[ 2594.028142] wlan0: deauthenticating from 00:22:75:5c:d7:c4 by local choice (reason=3)
--
[ 2606.696190] Skipping EDID probe due to cached edid
[ 2607.937547] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x31
[ 2607.937564] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x5, stream=0x5, channel=0, format=0x31
[ 2607.937570] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x31
[ 2610.128674] wlan0: authenticate with 00:22:75:5c:d7:c4 (try 1)
--
[ 2613.408245] Skipping EDID probe due to cached edid
[ 2615.573293] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[ 2615.573305] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x5
[ 2654.048408] lo: Disabled Privacy Extensions
--
[ 2687.948318] Skipping EDID probe due to cached edid
[ 2688.837348] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x31
[ 2688.837367] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x5, stream=0x5, channel=0, format=0x31
[ 2688.837374] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x31
[ 2689.925556] Skipping EDID probe due to cached edid
--
[ 2694.225120] Skipping EDID probe due to cached edid
[ 2696.452293] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[ 2696.452304] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x5
[ 2807.296142] wlan0: deauthenticating from 00:22:75:5c:d7:c4 by local choice (reason=3)
--
[ 2820.280190] Skipping EDID probe due to cached edid
[ 2821.495042] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x31
[ 2821.495058] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x5, stream=0x5, channel=0, format=0x31
[ 2821.495064] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x31
[ 2823.339664] wlan0: authenticate with 00:22:75:5c:d7:c4 (try 1)
--
[ 2826.385213] Skipping EDID probe due to cached edid
[ 2829.260169] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[ 2829.260181] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x5
[ 3123.189574] lo: Disabled Privacy Extensions
[ 3187.028025] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x31
[ 3187.028048] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x5, stream=0x5, channel=0, format=0x31
[ 3187.028059] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x31
[ 3293.032696] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[ 3293.032703] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x5
[ 3312.487896] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x31
[ 3312.487918] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x5, stream=0x5, channel=0, format=0x31
[ 3312.487929] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x31
[ 3342.247780] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[ 3342.247791] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x5
[ 3363.375702] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x31
[ 3363.375724] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x5, stream=0x5, channel=0, format=0x31
[ 3363.375734] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x31
[ 3384.111434] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[ 3384.111446] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x5
[ 3617.611061] lo: Disabled Privacy Extensions
--
[ 3666.512035] ehci_hcd 0000:00:1d.7: PCI INT A disabled
[ 3666.628090] HDA Intel 0000:00:1b.0: PCI INT A disabled
[ 3666.644020] PM: suspend of drv:HDA Intel dev:0000:00:1b.0 complete after 224.298 msecs
[ 3666.794147] PM: suspend of drv:sd dev:0:0:0:0 complete after 412.862 msecs
--
[ 3667.065894] i915 0000:00:02.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[ 3667.065949] HDA Intel 0000:00:1b.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[ 3667.065970] HDA Intel 0000:00:1b.0: restoring config space at offset 0x4 (was 0x4, writing 0xdfebc004)
[ 3667.065977] HDA Intel 0000:00:1b.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 3667.065984] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100102)
[ 3667.066020] pcieport 0000:00:1c.0: restoring config space at offset 0xf (was 0x100, writing 0x20100)
--
[ 3667.076389] i915 0000:00:02.0: setting latency timer to 64
[ 3667.077671] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[ 3667.077681] HDA Intel 0000:00:1b.0: setting latency timer to 64
[ 3667.077735] HDA Intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[ 3667.077787] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
--
[ 3684.320124] wlan0: no IPv6 routers present
[ 4177.555074] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x31
[ 4177.555095] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x5, stream=0x5, channel=0, format=0x31
[ 4177.555254] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x31
[ 4235.808574] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[ 4235.808585] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x5
[ 4269.809787] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x31
[ 4269.809806] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x5, stream=0x5, channel=0, format=0x31
[ 4269.809812] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x31
[ 4389.791581] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[ 4389.791593] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x5
[ 4573.370714] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x31
[ 4573.370737] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x5, stream=0x5, channel=0, format=0x31
[ 4573.370748] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x31
[ 4753.892249] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[ 4753.892257] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x5
[ 4782.989309] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x31
[ 4782.989331] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x5, stream=0x5, channel=0, format=0x31
[ 4782.989342] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x31
[ 4979.190829] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[ 4979.190840] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x5
[ 5004.213484] lo: Disabled Privacy Extensions
--
[ 5298.920230] Skipping EDID probe due to cached edid
[ 5299.986727] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x31
[ 5299.986743] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x5, stream=0x5, channel=0, format=0x31
[ 5299.986749] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x31
[ 5300.820063] Skipping EDID probe due to cached edid
--
[ 5305.032140] Skipping EDID probe due to cached edid
[ 5307.753037] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[ 5307.753049] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x5
[ 5350.967108] lo: Disabled Privacy Extensions
--
[33957.170801] lo: Disabled Privacy Extensions
[34236.387115] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x31
[34236.387134] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x5, stream=0x5, channel=0, format=0x31
[34236.387140] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x31
[34356.877239] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[34356.877251] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x5
[34582.856730] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x31
[34582.856747] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x5, stream=0x5, channel=0, format=0x31
[34582.856753] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x31
[34807.026181] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[34807.026192] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x5
[35230.259712] CE: hpet increased min_delta_ns to 7500 nsec
--
[35515.012244] Skipping EDID probe due to cached edid
[35515.891631] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x31
[35515.891648] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x5, stream=0x5, channel=0, format=0x31
[35515.891654] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x31
[35517.028128] Skipping EDID probe due to cached edid
--
[35520.637055] Skipping EDID probe due to cached edid
[35522.887691] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[35522.887703] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x5
[35664.718410] lo: Disabled Privacy Extensions
--
[53572.000162] CE: hpet increased min_delta_ns to 11250 nsec
[54122.031096] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x31
[54122.031115] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x5, stream=0x5, channel=0, format=0x31
[54122.031121] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x31
[54543.298274] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[54543.298281] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x5
[54714.088249] Skipping EDID probe due to cached edid
--
[67739.183385] Skipping EDID probe due to cached edid
[68991.627165] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x31
[68991.627181] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x5, stream=0x5, channel=0, format=0x31
[68991.627188] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x31
[69073.439937] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[69073.439943] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x5
[69109.909060] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x31
[69109.909076] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x5, stream=0x5, channel=0, format=0x31
[69109.909082] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x31

---

