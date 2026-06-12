---
title: "Sound card not being recognized"
date: 2011-02-03
forum: Multimedia Software
---

### Post by badnaam on 2011-02-03
2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:48 UTC 2011 i686 GNU/Linux

The soundcard was working with the exception of the mic. So I tried to install linuxant drivers and the installation failed for some reason. So I uninstalled it. After that my sound card is not being recognized.

Here is the output of the alsa diagnostic script. 

Please help.

****************************************************************
```

upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Fri Feb  4 00:04:43 UTC 2011


!!Linux Distribution
!!------------------

Ubuntu 10.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.10"


!!DMI Information
!!---------------

Manufacturer:      TOSHIBA
Product Name:      Satellite L305
Product Version:   PSLB8U-142025


!!Kernel Information
!!------------------

Kernel release:    2.6.35-25-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     
Library version:    1.0.23
Utilities version:  1.0.23


!!Loaded ALSA modules
!!-------------------



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



!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:293e (rev 03)
	Subsystem: 1179:ff66


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


!!ALSA Device nodes
!!-----------------

crw------- 1 root root 116,  1 Feb  1 15:10 /dev/snd/seq
crw------- 1 root root 116, 33 Feb  1 15:10 /dev/snd/timer


!!Aplay/Arecord output
!!------------

APLAY

aplay: device_list:235: no soundcards found...

ARECORD

arecord: device_list:235: no soundcards found...

!!Amixer output
!!-------------


!!Alsactl output
!!-------------

--startcollapse--
--endcollapse--


!!All Loaded Modules
!!------------------

Module
vmnet
parport_pc
vmblock
vsock
vmci
vmmon
aes_i586
aes_generic
binfmt_misc
ppdev
joydev
arc4
i915
rtl8187
mac80211
led_class
drm_kms_helper
drm
cfg80211
eeprom_93cx6
psmouse
serio_raw
intel_agp
soundcore
snd_page_alloc
i2c_algo_bit
lp
video
output
agpgart
parport
usb_storage
ahci
r8169
libahci
mii


!!ALSA/HDA dmesg
!!------------------

[   19.828367] agpgart-intel 0000:00:00.0: detected 131068K stolen memory, trimming to 32768K
[   19.881914] snd: Unknown symbol unregister_sound_special (err 0)
[   19.882265] snd: Unknown symbol register_sound_special_device (err 0)
[   19.883900] snd_timer: Unknown symbol snd_info_register (err 0)
```

---

### Post by Dahlgar on 2011-02-03
> [COLOR=Red]Driver version:     [/COLOR]
Library version:    1.0.23
Utilities version:  1.0.23I'm pretty new to Linux, but it looks like when the installation failed it didn't completely install the alsa driver. Try to reinstall the driver as demonstrated here: [https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)

---

### Post by badnaam on 2011-02-04
> **Dahlgar said:**
> I'm pretty new to Linux, but it looks like when the installation failed it didn't completely install the alsa driver. Try to reinstall the driver as demonstrated here: [https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)

Thanks. That did seems to fix the sound card recognition problem and now I can actually use the speakers and headphones. However, the mic does not seem to record anything (tried google voice, sound recorder etc). Any ideas?

here is the alsa diagnostic output.

```

upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Fri Feb  4 19:26:08 UTC 2011


!!Linux Distribution
!!------------------

Ubuntu 10.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.10"


!!DMI Information
!!---------------

Manufacturer:      TOSHIBA
Product Name:      Satellite L305
Product Version:   PSLB8U-142025


!!Kernel Information
!!------------------

Kernel release:    2.6.35-25-generic
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

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0x94600000 irq 45


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:293e (rev 03)
	Subsystem: 1179:ff66


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

Codec: Realtek ALC268
Address: 0
AFG Function Id: 0x1 (unsol 1)
Vendor Id: 0x10ec0268
Subsystem Id: 0x1179ff66
Revision Id: 0x100101
No Modem Function Group found
Default PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=4, o=0, i=0, unsolicited=1, wake=0
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[2]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[3]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Node 0x02 [Audio Output] wcaps 0x1d: Stereo Amp-Out
  Control: name="Speaker Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Device: name="ALC268 Analog", type="Audio", device=0
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x40 0x40]
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x03 [Audio Output] wcaps 0x1d: Stereo Amp-Out
  Control: name="Headphone Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x40 0x40]
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x04 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x05 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x06 [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0x1e]: 16 20 24 32
    formats [0x1]: PCM
Node 0x07 [Audio Input] wcaps 0x100111: Stereo
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Connection: 1
     0x24
Node 0x08 [Audio Input] wcaps 0x100111: Stereo
  Device: name="ALC268 Analog", type="Audio", device=0
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Connection: 1
     0x23
Node 0x09 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0a [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0b [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0c [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0d [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0e [Audio Mixer] wcaps 0x20010a: Mono Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00]
  Connection: 1
     0x02
Node 0x0f [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x02 0x1d
Node 0x10 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00] [0x80 0x80]
  Connection: 3
     0x03 0x1d 0x02
Node 0x11 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x12 [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
Node 0x13 [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
Node 0x14 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Control: name="Speaker Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0001003c: IN OUT HP EAPD Detect
  EAPD 0x2: EAPD
  Pin Default 0x99130110: [Fixed] Speaker at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x0f
Node 0x15 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Control: name="Headphone Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0001003c: IN OUT HP EAPD Detect
  EAPD 0x2: EAPD
  Pin Default 0x0221101f: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Black
    DefAssociation = 0x1, Sequence = 0xf
  Pin-ctls: 0xc0: OUT HP
  Unsolicited: tag=04, enabled=1
  Connection: 1
     0x10
Node 0x16 [Pin Complex] wcaps 0x40010c: Mono Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80]
  Pincap 0x00000010: OUT
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Connection: 1
     0x0e
Node 0x17 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x18 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Control: name="Mic Boost Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x02, stepsize=0x4f, mute=0
  Amp-In vals:  [0x02 0x02]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00003734: IN OUT Detect
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x02a11830: [Jack] Mic at Ext Front
    Conn = 1/8, Color = Black
    DefAssociation = 0x3, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x02
Node 0x19 [Pin Complex] wcaps 0x40008b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x02, stepsize=0x4f, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00003724: IN Detect
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
Node 0x1a [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x02, stepsize=0x4f, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00003734: IN OUT Detect
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x02
Node 0x1b [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x1c [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
Node 0x1d [Pin Complex] wcaps 0x400000: Mono
  Control: name="Beep Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Pincap 0x00000020: IN
  Pin Default 0x4015812d: [N/A] Speaker at Ext N/A
    Conn = Optical, Color = Purple
    DefAssociation = 0x2, Sequence = 0xd
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
Node 0x1e [Pin Complex] wcaps 0x400380: Mono Digital
  Pincap 0x00000010: OUT
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x06
Node 0x1f [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x20 [Vendor Defined Widget] wcaps 0xf00040: Mono
  Processing caps: benign=0, ncoeff=10
Node 0x21 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x22 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x23 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Control: name="Capture Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Capture Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x0a, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x1f 0x1f]
  Connection: 7
     0x18* 0x19 0x1a 0x1c 0x14 0x15 0x12
Node 0x24 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x0a, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x01 0x01]
  Connection: 7
     0x18 0x19 0x1a 0x1c 0x14* 0x15 0x13
Codec: LSI ID 1040
Address: 1
MFG Function Id: 0x2 (unsol 1)
Vendor Id: 0x11c11040
Subsystem Id: 0x11790001
Revision Id: 0x100200
Modem Function Group: 0x1
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116,  6 Feb  3 17:02 /dev/snd/controlC0
crw-rw----+ 1 root audio 116,  5 Feb  3 17:02 /dev/snd/hwC0D0
crw-rw----+ 1 root audio 116,  4 Feb  3 17:02 /dev/snd/hwC0D1
crw-rw----+ 1 root audio 116,  3 Feb  3 17:16 /dev/snd/pcmC0D0c
crw-rw----+ 1 root audio 116,  2 Feb  3 17:15 /dev/snd/pcmC0D0p
crw-rw----+ 1 root audio 116,  1 Feb  3 17:02 /dev/snd/seq
crw-rw----+ 1 root audio 116, 33 Feb  3 17:02 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Feb  3 17:02 .
drwxr-xr-x 3 root root 200 Feb  3 17:02 ..
lrwxrwxrwx 1 root root  12 Feb  3 17:02 pci-0000:00:1b.0 -> ../controlC0


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [Intel]

Card hw:0 'Intel'/'HDA Intel at 0x94600000 irq 45'
  Mixer name	: 'Realtek ALC268'
  Components	: 'HDA:10ec0268,1179ff66,00100101 HDA:11c11040,11790001,00100200'
  Controls      : 12
  Simple ctrls  : 7
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 64 [100%] [0.00dB] [on]
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
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 2
  Front Left: 2 [100%] [40.00dB]
  Front Right: 2 [100%] [40.00dB]
Simple mixer control 'Beep',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 12
  Mono:
  Front Left: Playback 0 [0%] [-24.00dB] [on]
  Front Right: Playback 0 [0%] [-24.00dB] [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 31 [100%] [31.50dB] [on]
  Front Right: Capture 31 [100%] [31.50dB] [on]


!!Alsactl output
!!-------------

--startcollapse--
state.Intel {
	control.1 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 64'
		comment.dbmin -6400
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
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 64'
		comment.dbmin -6400
		comment.dbmax 0
		iface MIXER
		name 'Headphone Playback Volume'
		value.0 64
		value.1 64
	}
	control.4 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Headphone Playback Switch'
		value.0 true
		value.1 true
	}
	control.5 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 2'
		comment.dbmin 0
		comment.dbmax 4000
		iface MIXER
		name 'Mic Boost Volume'
		value.0 2
		value.1 2
	}
	control.6 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 12'
		comment.dbmin -2400
		comment.dbmax 0
		iface MIXER
		name 'Beep Playback Volume'
		value.0 0
		value.1 0
	}
	control.7 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Beep Playback Switch'
		value.0 true
		value.1 true
	}
	control.8 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -1500
		comment.dbmax 3150
		iface MIXER
		name 'Capture Volume'
		value.0 31
		value.1 31
	}
	control.9 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Capture Switch'
		value.0 true
		value.1 true
	}
	control.10 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 64'
		comment.dbmin -6400
		comment.dbmax 0
		iface MIXER
		name 'Master Playback Volume'
		value 64
	}
	control.11 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Master Playback Switch'
		value true
	}
	control.12 {
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
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
binfmt_misc
vmnet
vmblock
vsock
vmci
vmmon
parport_pc
ppdev
snd_hda_codec_realtek
snd_hda_intel
snd_hda_codec
snd_hwdep
snd_pcm
arc4
snd_seq_midi
joydev
snd_rawmidi
snd_seq_midi_event
snd_seq
rtl8187
snd_timer
snd_seq_device
i915
drm_kms_helper
mac80211
snd
drm
intel_agp
psmouse
led_class
soundcore
agpgart
i2c_algo_bit
snd_page_alloc
serio_raw
cfg80211
eeprom_93cx6
lp
video
output
parport
usb_storage
ahci
libahci
r8169
mii


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x12 0x411111f0
0x13 0x411111f0
0x14 0x99130110
0x15 0x0221101f
0x16 0x411111f0
0x18 0x02a11830
0x19 0x411111f0
0x1a 0x411111f0
0x1c 0x411111f0
0x1d 0x4015812d
0x1e 0x411111f0

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:

/sys/class/sound/hwC0D1/init_pin_configs:

/sys/class/sound/hwC0D1/driver_pin_configs:

/sys/class/sound/hwC0D1/user_pin_configs:

/sys/class/sound/hwC0D1/init_verbs:


!!ALSA/HDA dmesg
!!------------------

[   17.397591]   alloc kstat_irqs on node -1
[   17.397599] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   17.397658]   alloc irq_desc for 45 on node -1
[   17.397660]   alloc kstat_irqs on node -1
[   17.397673] HDA Intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   17.397706] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   17.397712] ALSA hda_intel.c:2561: chipset global capabilities = 0x4401
[   17.428558] ALSA hda_intel.c:914: codec_mask = 0x3
[   17.428688] ALSA hda_intel.c:1354: codec #0 probed OK
[   17.428743] ALSA hda_intel.c:1354: codec #1 probed OK
[   17.491616] hda_codec: ALC268: BIOS auto-probing.
[   17.491623] ALSA hda_codec.c:4633: autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0)
[   17.491627] ALSA hda_codec.c:4637:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   17.491631] ALSA hda_codec.c:4641:    hp_outs=1 (0x15/0x0/0x0/0x0/0x0)
[   17.491635] ALSA hda_codec.c:4642:    mono: mono_out=0x0
[   17.491638] ALSA hda_codec.c:4646:    inputs:
[   17.491641] ALSA hda_codec.c:4650:  Mic=0x18
[   17.491645] ALSA hda_codec.c:4652: 
[   17.491829] ALSA patch_realtek.c:1587: realtek: No valid SSID, checking pincfg 0x4015812d for NID 0x1d
[   17.491833] ALSA patch_realtek.c:1603: realtek: Enabling init ASM_ID=0x812d CODEC_ID=10ec0268
[   17.491837] ALSA patch_realtek.c:1417: realtek: Enable HP auto-muting on NID 0x15
[   17.491918] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input6
[   17.495963] ALSA hda_codec.c:2164: Cannot find slave Front Playback Volume, skipped
[   17.495968] ALSA hda_codec.c:2164: Cannot find slave Surround Playback Volume, skipped
[   17.495972] ALSA hda_codec.c:2164: Cannot find slave Center Playback Volume, skipped
[   17.495975] ALSA hda_codec.c:2164: Cannot find slave LFE Playback Volume, skipped
[   17.495979] ALSA hda_codec.c:2164: Cannot find slave Side Playback Volume, skipped
[   17.495985] ALSA hda_codec.c:2164: Cannot find slave Mono Playback Volume, skipped
[   17.495988] ALSA hda_codec.c:2164: Cannot find slave Line-Out Playback Volume, skipped
[   17.495992] ALSA hda_codec.c:2164: Cannot find slave PCM Playback Volume, skipped
[   17.495999] ALSA hda_codec.c:2164: Cannot find slave Front Playback Switch, skipped
[   17.496020] ALSA hda_codec.c:2164: Cannot find slave Surround Playback Switch, skipped
[   17.496025] ALSA hda_codec.c:2164: Cannot find slave Center Playback Switch, skipped
[   17.496029] ALSA hda_codec.c:2164: Cannot find slave LFE Playback Switch, skipped
[   17.496034] ALSA hda_codec.c:2164: Cannot find slave Side Playback Switch, skipped
[   17.496042] ALSA hda_codec.c:2164: Cannot find slave Mono Playback Switch, skipped
[   17.496047] ALSA hda_codec.c:2164: Cannot find slave IEC958 Playback Switch, skipped
[   17.496052] ALSA hda_codec.c:2164: Cannot find slave Line-Out Playback Switch, skipped
[   17.496057] ALSA hda_codec.c:2164: Cannot find slave PCM Playback Switch, skipped
[   17.496228] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   19.827061] type=1400 audit(1296781343.615:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=1070 comm="apparmor_parser"
--
[   41.947782] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   42.422825] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.422831] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.423096] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.423100] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.424809] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.424814] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.425373] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.425378] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.425630] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.425634] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.425852] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.425856] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.426202] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.426207] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.426785] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.426790] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.427068] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.427073] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.427329] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.427333] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.427674] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.427678] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.428287] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.428291] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.428586] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.428591] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.428848] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.428852] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.429213] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.429219] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.429795] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.429800] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.430067] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.430071] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.430305] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.430309] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.430638] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.430642] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.431184] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.431188] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.593547] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   42.593560] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[   42.600017] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[   42.608051] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   42.608067] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[   42.608072] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[   42.608399] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[   42.608617] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[   42.608926] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[   42.609442] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[   42.610106] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   42.610116] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x1, channel=0, format=0x4011
[   42.616033] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   42.616041] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x1, channel=0, format=0x4011
[   42.616069] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[   42.616086] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[   42.617341] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.617345] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.617375] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.617378] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.617875] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.617879] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.618358] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.618362] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.619029] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.619034] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.619931] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.619935] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.620479] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.620483] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.621007] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.621012] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.621690] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.621695] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.622596] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.622600] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.623175] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.623180] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.623721] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.623726] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.624450] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.624455] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.625396] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.625400] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.625889] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.625894] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.626372] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.626376] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.627037] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.627041] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.627941] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.627945] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.628502] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.628511] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.629013] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.629018] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.629682] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.629686] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.630581] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.630585] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.631036] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.631040] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.631454] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.631458] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.631896] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.631900] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.632389] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.632394] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.632855] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.632860] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.633280] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.633284] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.633716] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.633720] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.634274] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.634279] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.634762] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.634767] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.635242] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.635246] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.635722] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.635727] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.636289] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.636294] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.636762] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.636766] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.637256] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.637261] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.637732] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.637736] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.638201] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.638205] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.638668] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.638673] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.639126] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.639130] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.639565] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.639569] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.640043] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.640048] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.640529] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.640533] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.640992] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.640997] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.641457] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.641462] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.641901] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.641906] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.642325] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.642329] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.642739] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.642744] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.643173] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.643177] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.643617] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.643621] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.644090] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.644094] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.644549] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.644553] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.645013] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.645017] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.645461] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.645465] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.645883] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.645887] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.646299] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.646304] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.646736] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.646740] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.647177] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.647181] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.647599] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.647603] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.648037] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.648043] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.648514] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.648518] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.649002] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.649006] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.649508] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.649513] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.649992] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.649996] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.650663] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.650667] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.651650] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.651655] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.652224] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.652229] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.652754] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.652759] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.653436] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.653440] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.654396] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.654401] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.654982] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.654988] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.655556] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.655560] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.656354] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.656359] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.657360] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.657365] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.657911] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.657916] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.658440] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.658444] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.659224] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.659229] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.660305] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.660311] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.660896] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.660901] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.661428] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.661433] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.662180] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.662185] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.663162] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.663167] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.663674] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.663679] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.664221] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.664225] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.664945] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.664950] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.665865] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.665870] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.666358] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.666363] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.666854] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.666858] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.667523] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.667527] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.668465] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.668469] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.668995] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.668999] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.669476] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.669481] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.670142] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.670147] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.671042] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.671046] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.671531] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.671536] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.672041] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.672047] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.672752] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.672756] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.673680] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.673684] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.674173] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.674177] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.674648] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.674653] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.675313] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.675317] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.676240] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   42.676245] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   42.682640] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[   42.682848] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[   42.683151] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[   42.683663] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[   42.684348] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   42.684359] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x1, channel=0, format=0x4011
[   42.684375] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   42.684383] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x1, channel=0, format=0x4011
[   42.684404] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[   42.684423] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[   42.687023] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[   42.687036] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[   42.687041] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[   42.687057] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[   42.687066] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[   42.687070] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[   42.790690] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[   42.790702] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x1, channel=0, format=0x4011
[   42.790718] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[   42.790726] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x1, channel=0, format=0x4011
[   48.182364] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[   48.182383] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[   49.449203] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   49.449209] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   49.449234] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   49.449237] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   64.972555] Skipping EDID probe due to cached edid
--
[   65.692035] Skipping EDID probe due to cached edid
[   66.598085] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.598091] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.598340] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.598344] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.598704] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.598708] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.599253] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.599258] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.599496] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.599500] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.599722] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.599726] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.600070] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.600075] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.600648] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.600654] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.600922] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.600926] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.601170] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.601174] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.601498] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.601503] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.602032] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.602036] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.602269] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.602273] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.602494] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.602498] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.602812] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.602816] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.603344] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.603349] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.603581] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.603585] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.603805] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.603809] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.604164] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.604168] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.604725] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.604729] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.608977] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   66.608990] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[   66.608995] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[   66.609010] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   66.609019] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[   66.609023] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[   66.609282] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[   66.609518] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[   66.609843] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[   66.610376] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[   66.611048] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   66.611058] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x1, channel=0, format=0x4011
[   66.611075] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   66.611083] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x1, channel=0, format=0x4011
[   66.611101] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[   66.611120] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[   66.612305] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.612309] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.612332] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.612335] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.612906] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.612911] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.613433] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.613437] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.614124] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.614129] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.615048] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.615052] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.615562] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.615567] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.616153] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.616158] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.616908] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.616913] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.617857] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.617861] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.618372] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.618377] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.618953] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.618958] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.619720] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.619726] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.620792] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.620797] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.621345] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.621349] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.621853] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.621857] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.622546] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.622550] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.623468] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.623473] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.623984] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.623988] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.624612] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.624616] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.625368] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.625373] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.626405] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.626410] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.626902] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.626906] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.627355] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.627359] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.627823] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.627828] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.628352] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.628357] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.628855] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.628859] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.629314] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.629319] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.629892] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.629897] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.630391] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.630395] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.630845] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.630849] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.631290] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.631294] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.631754] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.631758] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.632301] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.632305] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.632803] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.632808] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.633281] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.633285] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.633749] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.633753] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.634215] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.634220] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.634664] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.634668] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.635177] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.635181] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.635643] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.635647] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.636155] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.636160] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.636705] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.636710] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.637190] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.637194] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.637672] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.637677] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.638140] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.638144] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.638589] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.638593] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.639033] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.639037] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.639492] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.639496] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.639956] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.639960] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.640457] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.640462] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.640942] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.640947] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.641424] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.641429] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.641892] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.641896] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.642339] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.642344] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.642782] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.642786] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.643241] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.643246] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.643706] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.643710] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.644232] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.644237] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.644722] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.644727] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.645221] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.645225] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.645693] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.645697] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.646211] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.646216] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.646718] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.646723] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.647408] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.647413] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.648387] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.648392] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.648957] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.648962] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.649473] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.649478] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.650167] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.650172] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.651094] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.651098] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.651613] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.651617] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.652181] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.652186] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.652933] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.652938] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.653879] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.653884] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.654397] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.654401] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.654899] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.654904] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.655591] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.655596] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.656560] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.656565] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.657113] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.657117] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.657698] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.657702] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.658445] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.658450] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.659525] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.659530] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.660118] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.660123] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.660690] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.660695] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.661437] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.661442] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.662411] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.662416] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.662984] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.662989] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.663547] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.663551] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.664374] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.664379] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.665387] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.665392] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.665955] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.665960] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.666500] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.666505] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.667236] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.667241] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.668254] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.668259] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.668857] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.668862] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.669408] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.669413] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.670143] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.670148] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.671132] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.671137] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.671734] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.671738] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.672370] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.672375] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.673146] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.673152] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.674218] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   66.674224] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   66.682812] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[   66.683082] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[   66.683449] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[   66.684083] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[   66.684874] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   66.684887] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x1, channel=0, format=0x4011
[   66.684903] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   66.684911] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x1, channel=0, format=0x4011
[   66.684935] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[   66.684958] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[   66.687923] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[   66.687937] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[   66.687942] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[   66.687959] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[   66.687969] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[   66.687973] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[   66.790825] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[   66.790837] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x1, channel=0, format=0x4011
[   66.790853] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[   66.790861] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x1, channel=0, format=0x4011
[   70.216126] Skipping EDID probe due to cached edid
--
[   71.865339] wlan0: associate with 34:ef:44:0e:fd:41 (try 1)
[   72.008153] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[   72.008176] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[   72.008882] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   72.008888] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   72.008915] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   72.008918] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   72.064037] wlan0: associate with 34:ef:44:0e:fd:41 (try 2)
--
[   82.424527] wlan0: no IPv6 routers present
[   91.482696] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[   91.482708] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x1, channel=0, format=0x4011
[   91.482725] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[   91.482733] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x1, channel=0, format=0x4011
[  107.894245] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[  107.894258] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[  107.894263] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[  107.894279] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[  107.894287] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[  107.894291] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[  117.560890] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.560898] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  117.560928] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.560934] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  126.851315] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[  126.851332] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[  126.851340] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[  126.851360] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[  126.851372] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[  126.851379] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[  135.458344] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  135.458352] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  135.458382] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  135.458387] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  142.997870] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[  142.997909] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[  176.048520] ALSA hda_intel.c:707: azx_get_response timeout, polling the codec once: last cmd=0x010b2001
[  182.455311] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[  182.455323] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x1, channel=0, format=0x4011
[  182.455339] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[  182.455348] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x1, channel=0, format=0x4011
[  190.632182] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[  190.632200] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[  190.632208] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[  190.632228] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[  190.632240] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[  190.632247] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[  197.765833] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  197.765842] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  197.765872] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  197.765877] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  202.247802] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[  202.247854] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[  209.870772] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[  209.870785] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x1, channel=0, format=0x4011
[  209.870802] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[  209.870811] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x1, channel=0, format=0x4011
[  213.720563] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[  213.720582] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[  213.720590] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[  213.720611] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[  213.720623] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[  213.720629] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[  220.230059] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  220.230067] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  220.230096] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  220.230102] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  222.197426] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[  222.197466] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[  517.544033] Skipping EDID probe due to cached edid
[  746.022924] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[  746.022938] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x1, channel=0, format=0x4011
[  746.022954] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[  746.022962] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x1, channel=0, format=0x4011
[  750.567864] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[  750.567877] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[  750.567882] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[  750.567898] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[  750.567908] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[  750.567912] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[  754.474299] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[  754.474332] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[  757.570485] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  757.570494] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  757.570545] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  757.570550] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  768.450640] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[  768.450654] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x1, channel=0, format=0x4011
[  768.450672] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[  768.450680] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x1, channel=0, format=0x4011
[  772.112567] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[  772.112581] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[  772.112586] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[  772.112602] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[  772.112612] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[  772.112616] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[  776.280541] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[  776.280574] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[  779.822610] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  779.822619] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  779.822656] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  779.822662] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  783.302888] lo: Disabled Privacy Extensions
[  788.728688] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[  788.728701] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x1, channel=0, format=0x4011
[  788.728718] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[  788.728726] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x1, channel=0, format=0x4011
[  814.892730] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[  814.892782] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[  825.637759] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[  825.637771] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[  825.637776] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[  825.637792] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[  825.637801] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[  825.637805] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[  825.639116] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[  825.639128] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x1, channel=0, format=0x4011
[  825.639144] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[  825.639152] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x1, channel=0, format=0x4011
[  879.032735] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[  879.032768] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[  881.329970] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[  881.329982] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x1, channel=0, format=0x4011
[  881.329998] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[  881.330006] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x1, channel=0, format=0x4011
[  908.671959] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[  908.671982] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[  908.673631] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  908.673638] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  908.673667] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  908.673670] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[ 4810.966060] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
--
[ 4813.172028] ehci_hcd 0000:00:1a.7: PCI INT D disabled
[ 4813.364082] HDA Intel 0000:00:1b.0: PCI INT A disabled
[ 4813.380022] PM: suspend of drv:HDA Intel dev:0000:00:1b.0 complete after 222.747 msecs
[ 4813.760361] PM: suspend of drv:sd dev:0:0:0:0 complete after 699.624 msecs
--
[ 4975.928568] Component: suspend devices, time: 162868
[ 4975.928570] Modules linked in: binfmt_misc vmnet vmblock vsock vmci vmmon parport_pc ppdev snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm arc4 snd_seq_midi joydev snd_rawmidi snd_seq_midi_event snd_seq rtl8187 snd_timer snd_seq_device i915 drm_kms_helper mac80211 snd drm intel_agp psmouse led_class soundcore agpgart i2c_algo_bit snd_page_alloc serio_raw cfg80211 eeprom_93cx6 lp video output parport usb_storage ahci libahci r8169 mii
[ 4975.928602] Pid: 3174, comm: pm-suspend Not tainted 2.6.35-25-generic #44-Ubuntu
--
[ 4976.266086] ehci_hcd 0000:00:1a.7: restoring config space at offset 0x1 (was 0x2900006, writing 0x2900002)
[ 4976.266142] HDA Intel 0000:00:1b.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 4976.266149] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100006, writing 0x100002)
[ 4976.266184] pcieport 0000:00:1c.0: restoring config space at offset 0xf (was 0x100, writing 0x105)
--
[ 4976.278038] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[ 4976.278087] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[ 4976.278094] HDA Intel 0000:00:1b.0: setting latency timer to 64
[ 4976.278140] HDA Intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[ 4976.278184] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
```

---

### Post by Yellow Pasque on 2011-02-04
Please learn how to use [ code ][ /code ] tags on large blocks of output text to increase the lifespan of our scrollwheels ;)

---

### Post by johntaylor1887 on 2011-02-04
Click on the speaker icon and go to sound preferences and see what your mic settings are.

---

### Post by badnaam on 2011-02-04
> **johntaylor1887 said:**
> Click on the speaker icon and go to sound preferences and see what your mic settings are.

Here are the mic settings.

---

### Post by lidex on 2011-02-05
Try adding a model quirk to alsa-base.conf:
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=toshiba 
```
Save. Close. Reboot. 
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.
No joy? Change the model to "auto" - minus the quotes.

---

### Post by badnaam on 2011-02-05
I tried putting both toshiba and auto for snd-hda-intel model property. No luck with auto or toshiba.

here is what I see in the alsamixer and sound preferences. When I try to record something using the sound recorder I just hear a big hiss (with mic boost up) or nothing (with mic boost down).

---

### Post by badnaam on 2011-02-07
Folks any thoughts? Please help.

---

### Post by lidex on 2011-02-09
You have a mic and a front mic. Have you tried switching to the other?

---

### Post by badnaam on 2011-02-09
> **lidex said:**
> You have a mic and a front mic. Have you tried switching to the other?

Adjusted both mic, no joy. Here is the alsa diagnostic output.

```

upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Wed Feb  9 18:40:34 UTC 2011


!!Linux Distribution
!!------------------

Ubuntu 10.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.10"


!!DMI Information
!!---------------

Manufacturer:      TOSHIBA
Product Name:      Satellite L305
Product Version:   PSLB8U-142025


!!Kernel Information
!!------------------

Kernel release:    2.6.35-25-generic
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

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0x94600000 irq 45


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:293e (rev 03)
	Subsystem: 1179:ff66


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
snd-hda-intel: model=toshiba


!!Loaded sound module options
!!--------------------------

!!Module: snd_hda_intel
	bdl_pos_adj : 1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	beep_mode : 1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	enable_msi : -1
	id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	model : toshiba,(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
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

Codec: Realtek ALC268
Address: 0
AFG Function Id: 0x1 (unsol 1)
Vendor Id: 0x10ec0268
Subsystem Id: 0x1179ff66
Revision Id: 0x100101
No Modem Function Group found
Default PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=4, o=0, i=0, unsolicited=1, wake=0
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[2]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[3]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Node 0x02 [Audio Output] wcaps 0x1d: Stereo Amp-Out
  Control: name="Front Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Device: name="ALC268 Analog", type="Audio", device=0
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x40 0x40]
  Converter: stream=5, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x03 [Audio Output] wcaps 0x1d: Stereo Amp-Out
  Control: name="Headphone Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x40 0x40]
  Converter: stream=5, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x04 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x05 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x06 [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0x1e]: 16 20 24 32
    formats [0x1]: PCM
Node 0x07 [Audio Input] wcaps 0x100111: Stereo
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Connection: 1
     0x24
Node 0x08 [Audio Input] wcaps 0x100111: Stereo
  Device: name="ALC268 Analog", type="Audio", device=0
  Converter: stream=1, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Connection: 1
     0x23
Node 0x09 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0a [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0b [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0c [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0d [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0e [Audio Mixer] wcaps 0x20010a: Mono Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00]
  Connection: 1
     0x02
Node 0x0f [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x02 0x1d
Node 0x10 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00] [0x80 0x80]
  Connection: 3
     0x03 0x1d 0x02
Node 0x11 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x12 [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
Node 0x13 [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
Node 0x14 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0001003c: IN OUT HP EAPD Detect
  EAPD 0x2: EAPD
  Pin Default 0x99130110: [Fixed] Speaker at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x0f
Node 0x15 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0001003c: IN OUT HP EAPD Detect
  EAPD 0x2: EAPD
  Pin Default 0x0221101f: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Black
    DefAssociation = 0x1, Sequence = 0xf
  Pin-ctls: 0xc0: OUT HP
  Unsolicited: tag=04, enabled=1
  Connection: 1
     0x10
Node 0x16 [Pin Complex] wcaps 0x40010c: Mono Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80]
  Pincap 0x00000010: OUT
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x0e
Node 0x17 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x18 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Control: name="Mic Boost Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x02, stepsize=0x4f, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00003734: IN OUT Detect
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x02a11830: [Jack] Mic at Ext Front
    Conn = 1/8, Color = Black
    DefAssociation = 0x3, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x02
Node 0x19 [Pin Complex] wcaps 0x40008b: Stereo Amp-In
  Control: name="Front Mic Boost Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x02, stepsize=0x4f, mute=0
  Amp-In vals:  [0x01 0x01]
  Pincap 0x00003724: IN Detect
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
Node 0x1a [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Control: name="Line In Boost Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x02, stepsize=0x4f, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00003734: IN OUT Detect
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x02
Node 0x1b [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x1c [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
Node 0x1d [Pin Complex] wcaps 0x400000: Mono
  Control: name="Beep Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Pincap 0x00000020: IN
  Pin Default 0x4015812d: [N/A] Speaker at Ext N/A
    Conn = Optical, Color = Purple
    DefAssociation = 0x2, Sequence = 0xd
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
Node 0x1e [Pin Complex] wcaps 0x400380: Mono Digital
  Pincap 0x00000010: OUT
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x06
Node 0x1f [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x20 [Vendor Defined Widget] wcaps 0xf00040: Mono
  Processing caps: benign=0, ncoeff=10
Node 0x21 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x22 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x23 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Control: name="Capture Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Capture Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Input Source", index=0, device=0
  Amp-Out caps: ofs=0x0a, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x1f 0x1f]
  Connection: 7
     0x18 0x19* 0x1a 0x1c 0x14 0x15 0x12
Node 0x24 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x0a, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x00 0x00]
  Connection: 7
     0x18* 0x19 0x1a 0x1c 0x14 0x15 0x13
Codec: LSI ID 1040
Address: 1
MFG Function Id: 0x2 (unsol 1)
Vendor Id: 0x11c11040
Subsystem Id: 0x11790001
Revision Id: 0x100200
Modem Function Group: 0x1
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116,  6 Feb  9 10:15 /dev/snd/controlC0
crw-rw----+ 1 root audio 116,  5 Feb  9 10:15 /dev/snd/hwC0D0
crw-rw----+ 1 root audio 116,  4 Feb  9 10:15 /dev/snd/hwC0D1
crw-rw----+ 1 root audio 116,  3 Feb  9 10:37 /dev/snd/pcmC0D0c
crw-rw----+ 1 root audio 116,  2 Feb  9 10:37 /dev/snd/pcmC0D0p
crw-rw----+ 1 root audio 116,  1 Feb  9 10:15 /dev/snd/seq
crw-rw----+ 1 root audio 116, 33 Feb  9 10:15 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Feb  9 10:15 .
drwxr-xr-x 3 root root 200 Feb  9 10:15 ..
lrwxrwxrwx 1 root root  12 Feb  9 10:15 pci-0000:00:1b.0 -> ../controlC0


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [Intel]

Card hw:0 'Intel'/'HDA Intel at 0x94600000 irq 45'
  Mixer name	: 'Realtek ALC268'
  Components	: 'HDA:10ec0268,1179ff66,00100101 HDA:11c11040,11790001,00100200'
  Controls      : 13
  Simple ctrls  : 10
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB]
  Front Right: Playback 64 [100%] [0.00dB]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Front',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB]
  Front Right: Playback 64 [100%] [0.00dB]
Simple mixer control 'Front Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 2
  Front Left: 1 [50%] [20.00dB]
  Front Right: 1 [50%] [20.00dB]
Simple mixer control 'Line In Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 2
  Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB]
Simple mixer control 'Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 2
  Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB]
Simple mixer control 'Beep',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 12
  Mono:
  Front Left: Playback 0 [0%] [-24.00dB] [on]
  Front Right: Playback 0 [0%] [-24.00dB] [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 31 [100%] [31.50dB] [on]
  Front Right: Capture 31 [100%] [31.50dB] [on]
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Mic' 'Front Mic' 'Line' 'CD'
  Item0: 'Front Mic'


!!Alsactl output
!!-------------

--startcollapse--
state.Intel {
	control.1 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 64'
		comment.dbmin -6400
		comment.dbmax 0
		iface MIXER
		name 'Front Playback Volume'
		value.0 64
		value.1 64
	}
	control.2 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 64'
		comment.dbmin -6400
		comment.dbmax 0
		iface MIXER
		name 'Headphone Playback Volume'
		value.0 64
		value.1 64
	}
	control.3 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Master Playback Switch'
		value true
	}
	control.4 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 2'
		comment.dbmin 0
		comment.dbmax 4000
		iface MIXER
		name 'Mic Boost Volume'
		value.0 0
		value.1 0
	}
	control.5 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 2'
		comment.dbmin 0
		comment.dbmax 4000
		iface MIXER
		name 'Front Mic Boost Volume'
		value.0 1
		value.1 1
	}
	control.6 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 2'
		comment.dbmin 0
		comment.dbmax 4000
		iface MIXER
		name 'Line In Boost Volume'
		value.0 0
		value.1 0
	}
	control.7 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -1500
		comment.dbmax 3150
		iface MIXER
		name 'Capture Volume'
		value.0 31
		value.1 31
	}
	control.8 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Capture Switch'
		value.0 true
		value.1 true
	}
	control.9 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Mic
		comment.item.1 'Front Mic'
		comment.item.2 Line
		comment.item.3 CD
		iface MIXER
		name 'Input Source'
		value 'Front Mic'
	}
	control.10 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 12'
		comment.dbmin -2400
		comment.dbmax 0
		iface MIXER
		name 'Beep Playback Volume'
		value.0 0
		value.1 0
	}
	control.11 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Beep Playback Switch'
		value.0 true
		value.1 true
	}
	control.12 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 64'
		comment.dbmin -6400
		comment.dbmax 0
		iface MIXER
		name 'Master Playback Volume'
		value 64
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
		value.0 255
		value.1 255
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
binfmt_misc
vmnet
vmblock
vsock
vmci
vmmon
parport_pc
ppdev
joydev
snd_hda_codec_realtek
arc4
snd_hda_intel
snd_hda_codec
snd_hwdep
snd_pcm
snd_seq_midi
snd_rawmidi
i915
rtl8187
snd_seq_midi_event
mac80211
snd_seq
led_class
drm_kms_helper
snd_timer
snd_seq_device
cfg80211
drm
eeprom_93cx6
snd
intel_agp
psmouse
i2c_algo_bit
video
soundcore
lp
serio_raw
snd_page_alloc
output
agpgart
parport
usb_storage
ahci
r8169
libahci
mii


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x12 0x411111f0
0x13 0x411111f0
0x14 0x99130110
0x15 0x0221101f
0x16 0x411111f0
0x18 0x02a11830
0x19 0x411111f0
0x1a 0x411111f0
0x1c 0x411111f0
0x1d 0x4015812d
0x1e 0x411111f0

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:

/sys/class/sound/hwC0D1/init_pin_configs:

/sys/class/sound/hwC0D1/driver_pin_configs:

/sys/class/sound/hwC0D1/user_pin_configs:

/sys/class/sound/hwC0D1/init_verbs:


!!ALSA/HDA dmesg
!!------------------

[   22.413622]   alloc kstat_irqs on node -1
[   22.413630] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   22.413688]   alloc irq_desc for 45 on node -1
[   22.413689]   alloc kstat_irqs on node -1
[   22.413701] HDA Intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   22.413734] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   22.413741] ALSA hda_intel.c:2561: chipset global capabilities = 0x4401
[   22.438386] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x9280b1, caps: 0xa04711/0xa04000/0x0
[   22.438390] synaptics: Toshiba Satellite L305 detected, limiting rate to 40pps.
[   22.445013] ALSA hda_intel.c:914: codec_mask = 0x3
[   22.449221] ALSA hda_intel.c:1354: codec #0 probed OK
[   22.449267] ALSA hda_intel.c:1354: codec #1 probed OK
[   22.465057] Skipping EDID probe due to cached edid
[   22.496648] ALSA hda_codec.c:3701: hda_codec: model 'toshiba' is selected
[   22.496726] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input5
[   22.518243] ALSA hda_codec.c:2164: Cannot find slave Surround Playback Volume, skipped
[   22.518248] ALSA hda_codec.c:2164: Cannot find slave Center Playback Volume, skipped
[   22.518252] ALSA hda_codec.c:2164: Cannot find slave LFE Playback Volume, skipped
[   22.518256] ALSA hda_codec.c:2164: Cannot find slave Side Playback Volume, skipped
[   22.518260] ALSA hda_codec.c:2164: Cannot find slave Speaker Playback Volume, skipped
[   22.518264] ALSA hda_codec.c:2164: Cannot find slave Mono Playback Volume, skipped
[   22.518267] ALSA hda_codec.c:2164: Cannot find slave Line-Out Playback Volume, skipped
[   22.518271] ALSA hda_codec.c:2164: Cannot find slave PCM Playback Volume, skipped
[   22.518450] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   22.528462] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
--
[   27.504058] Skipping EDID probe due to cached edid
[   30.097333] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.097339] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.097343] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.097608] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.097613] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.097616] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.098019] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.098023] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.098027] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.098615] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.098619] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.098623] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.098924] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.098929] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.098932] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.099177] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.099181] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.099185] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.099533] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.099538] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.099541] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.100179] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.100184] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.100188] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.100492] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.100496] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.100500] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.100748] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.100752] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.100755] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.101116] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.101120] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.101124] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.101700] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.101705] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.101709] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.102007] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.102012] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.102015] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.102233] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.102237] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.102241] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.102547] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.102551] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.102555] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.103071] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.103075] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.103078] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.103304] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.103307] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.103311] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.103522] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.103526] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.103529] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.103837] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.103841] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.103844] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.104437] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.104441] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.104445] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.109064] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   30.109079] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[   30.120878] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[   30.132038] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[   30.132081] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   30.132091] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[   30.132095] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[   30.132099] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[   30.132465] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[   30.132717] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[   30.133041] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[   30.133584] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[   30.134291] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   30.134303] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x1, channel=0, format=0x4011
[   30.144059] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   30.144070] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x1, channel=0, format=0x4011
[   30.144108] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[   30.144128] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[   30.145291] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.145296] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.145300] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.145320] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.145323] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.145326] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.145926] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.145931] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.145934] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.146474] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.146479] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.146482] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.147192] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.147197] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.147200] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.148144] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.148149] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.148152] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.148728] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.148733] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.148736] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.149260] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.149264] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.149268] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.149989] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.149994] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.149997] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.150964] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.150969] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.150972] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.151503] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.151507] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.151511] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.152026] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.152030] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.152034] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.152798] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.152803] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.152806] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.153745] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.153749] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.153753] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.154261] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.154265] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.154269] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.154746] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.154750] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.154754] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.155427] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.155431] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.155435] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.156447] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.156453] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.156457] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.157093] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.157098] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.157102] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.157639] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.157644] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.157647] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.158372] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.158377] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.158381] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.159343] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.159348] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.159351] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.159832] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.159836] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.159840] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.160265] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.160270] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.160273] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.160791] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.160796] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.160800] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.161290] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.161295] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.161298] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.161739] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.161743] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.161747] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.162226] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.162231] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.162234] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.162709] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.162714] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.162718] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.163225] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.163229] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.163233] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.163702] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.163707] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.163710] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.164168] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.164172] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.164176] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.164675] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.164679] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.164682] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.165148] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.165152] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.165156] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.165590] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.165594] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.165598] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.166033] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.166037] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.166040] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.166480] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.166484] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.166487] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.166973] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.166977] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.166981] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.167407] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.167411] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.167415] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.167827] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.167831] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.167834] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.168279] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.168283] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.168287] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.168811] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.168815] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.168819] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.169262] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.169266] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.169270] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.169716] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.169721] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.169724] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.170248] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.170252] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.170256] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.170715] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.170719] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.170723] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.171173] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.171177] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.171181] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.171601] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.171605] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.171609] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.172053] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.172057] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.172060] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.172539] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.172545] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.172549] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.173010] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.173014] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.173018] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.173461] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.173466] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.173469] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.173919] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.173923] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.173927] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.174392] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.174396] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.174400] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.174842] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.174846] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.174850] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.175271] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.175276] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.175279] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.175719] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.175723] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.175727] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.176219] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.176224] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.176228] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.176834] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.176838] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.176842] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.177301] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.177305] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.177309] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.177773] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.177778] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.177781] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.178237] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.178242] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.178245] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.178743] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.178747] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.178751] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.179236] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.179241] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.179244] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.179917] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.179922] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.179925] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.180877] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.180882] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.180885] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.181421] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.181425] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.181428] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.181933] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.181937] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.181940] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.182613] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.182618] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.182621] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.183539] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.183543] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.183546] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.184048] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.184052] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.184055] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.184622] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.184627] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.184630] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.185349] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.185353] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.185356] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.186295] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.186300] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.186303] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.186848] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.186853] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.186856] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.187404] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.187409] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.187412] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.188159] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.188164] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.188168] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.189250] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.189255] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.189258] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.189817] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.189821] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.189825] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.190370] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.190375] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.190378] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.191133] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.191138] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.191142] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.192153] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.192159] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.192162] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.192886] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.192891] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.192895] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.193444] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.193448] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.193452] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.194225] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.194230] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.194234] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.195213] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.195218] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.195222] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.195767] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.195771] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.195775] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.196293] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.196297] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.196301] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.197049] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.197054] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.197057] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.198016] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.198021] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.198024] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.198609] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.198613] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.198617] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.199181] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.199186] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.199190] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.199960] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.199966] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.199970] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.201028] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.201032] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.201036] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.201601] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.201605] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.201609] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.202152] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.202157] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.202161] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.202919] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.202924] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.202928] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.203886] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.203891] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.203894] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.204448] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.204453] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.204457] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.205088] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.205093] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.205096] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.205803] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.205808] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.205811] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.206773] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   30.206778] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.206782] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   30.214074] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[   30.214336] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[   30.214678] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[   30.215222] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[   30.215949] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   30.215960] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x1, channel=0, format=0x4011
[   30.215977] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   30.215985] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x1, channel=0, format=0x4011
[   30.216012] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[   30.216028] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[   30.218707] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[   30.218721] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[   30.218726] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[   30.218730] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[   30.218746] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[   30.218755] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[   30.218759] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[   30.218763] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[   30.229771] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[   30.229785] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x1, channel=0, format=0x4011
[   30.229803] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[   30.229812] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x1, channel=0, format=0x4011
[   32.684478] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   35.318812] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[   35.318831] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[   36.383735] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   36.383740] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   36.383744] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   36.383767] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   36.383770] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   36.383773] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   36.992026] vmnet1: no IPv6 routers present
--
[  109.472081] Skipping EDID probe due to cached edid
[  110.008337] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.008342] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.008346] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.008628] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.008632] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.008635] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.009012] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.009016] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.009020] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.009579] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.009583] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.009586] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.009869] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.009873] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.009876] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.010129] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.010134] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.010137] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.010481] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.010485] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.010489] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.011075] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.011080] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.011084] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.011388] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.011392] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.011396] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.011654] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.011658] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.011662] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.012027] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.012032] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.012035] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.012655] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.012660] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.012663] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.012929] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.012933] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.012937] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.013172] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.013176] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.013180] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.013498] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.013502] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.013506] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.014063] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.014067] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.014071] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.014325] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.014329] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.014332] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.014566] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.014570] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.014573] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.014896] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.014900] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.014903] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.015440] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.015444] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.015448] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.019761] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[  110.019775] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[  110.019780] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[  110.019784] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[  110.019800] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[  110.019809] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[  110.019813] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[  110.019817] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[  110.020107] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[  110.020344] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[  110.020685] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[  110.021255] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[  110.022024] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[  110.022037] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x1, channel=0, format=0x4011
[  110.022054] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[  110.022062] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x1, channel=0, format=0x4011
[  110.022088] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[  110.022112] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[  110.023216] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.023221] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.023224] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.023245] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.023248] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.023252] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.023804] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.023808] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.023811] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.024379] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.024384] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.024388] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.025197] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.025202] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.025205] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.026221] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.026226] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.026230] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.026828] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.026833] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.026836] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.027401] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.027405] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.027408] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.028174] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.028179] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.028182] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.030448] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.030453] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.030457] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.031023] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.031027] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.031031] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.031559] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.031563] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.031566] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.032285] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.032289] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.032292] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.033318] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.033322] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.033325] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.033855] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.033859] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.033863] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.034425] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.034429] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.034433] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.035185] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.035189] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.035193] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.036219] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.036224] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.036228] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.036901] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.036907] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.036910] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.037549] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.037553] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.037557] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.038321] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.038326] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.038329] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.039322] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.039327] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.039330] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.039888] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.039892] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.039896] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.040401] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.040405] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.040409] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.040992] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.040997] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.041000] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.041551] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.041556] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.041559] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.042066] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.042070] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.042074] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.042577] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.042581] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.042585] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.043104] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.043108] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.043112] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.043589] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.043593] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.043597] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.044109] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.044114] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.044117] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.044664] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.044668] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.044672] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.045210] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.045215] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.045218] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.045751] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.045756] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.045759] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.046264] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.046268] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.046272] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.046745] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.046749] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.046753] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.047252] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.047257] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.047260] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.048132] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.048137] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.048140] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.048709] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.048714] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.048717] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.049193] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.049197] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.049200] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.049681] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.049685] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.049689] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.050177] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.050182] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.050185] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.050657] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.050661] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.050664] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.051130] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.051134] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.051137] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.051616] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.051620] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.051624] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.052114] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.052118] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.052122] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.052629] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.052633] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.052636] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.053105] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.053109] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.053112] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.053596] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.053600] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.053604] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.054098] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.054102] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.054105] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.054575] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.054579] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.054582] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.055044] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.055048] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.055051] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.055509] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.055513] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.055516] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.056005] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.056010] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.056014] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.056560] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.056564] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.056568] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.057042] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.057046] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.057050] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.057535] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.057539] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.057542] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.058032] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.058036] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.058039] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.058542] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.058546] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.058550] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.059023] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.059028] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.059031] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.059529] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.059534] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.059537] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.060043] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.060047] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.060051] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.060662] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.060667] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.060670] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.061215] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.061219] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.061222] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.061942] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.061946] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.061950] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.062922] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.062927] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.062930] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.063524] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.063529] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.063532] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.064067] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.064072] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.064075] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.064885] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.064890] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.064894] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.065910] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.065915] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.065919] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.066520] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.066524] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.066528] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.067068] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.067073] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.067076] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.067811] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.067816] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.067820] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.069074] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.069080] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.069083] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.069689] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.069693] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.069697] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.070251] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.070255] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.070258] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.071014] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.071019] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.071022] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.072063] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.072068] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.072072] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.072874] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.072879] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.072882] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.073421] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.073425] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.073428] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.074148] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.074152] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.074156] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.075113] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.075117] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.075121] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.075703] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.075708] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.075711] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.076253] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.076257] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.076261] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.077269] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.077274] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.077277] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.078296] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.078301] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.078304] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.078912] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.078917] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.078920] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.079502] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.079507] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.079511] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.080226] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.080231] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.080234] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.081461] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.081466] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.081469] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.082054] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.082059] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.082062] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.082660] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.082665] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.082668] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.083452] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.083457] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.083460] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.084481] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.084486] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.084489] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.085354] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.085358] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.085362] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.085937] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.085941] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.085945] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.086690] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.086695] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.086698] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.087712] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.087717] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.087720] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.088336] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.088341] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.088345] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.089113] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.089117] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.089121] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.089850] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.089855] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.089859] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.090881] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  110.090887] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.090890] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  110.098509] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[  110.098793] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[  110.099175] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[  110.099753] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[  110.100531] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[  110.100626] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x1, channel=0, format=0x4011
[  110.100647] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[  110.100655] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x1, channel=0, format=0x4011
[  110.100679] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[  110.100703] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[  110.103630] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[  110.103645] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[  110.103650] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[  110.103654] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[  110.103673] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[  110.103683] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[  110.103687] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[  110.103691] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[  110.137374] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[  110.137387] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x1, channel=0, format=0x4011
[  110.137405] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[  110.137413] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x1, channel=0, format=0x4011
[  111.320060] Skipping EDID probe due to cached edid
--
[  115.132082] Skipping EDID probe due to cached edid
[  115.283722] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[  115.283758] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[  115.285830] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  115.285838] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  115.285844] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  115.285885] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  115.285890] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  115.285896] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  117.552032] /dev/vmmon[0]: HostIF_ReadUptime: detected settimeofday: fixed uptimeBase old 18445446798382198512 new 18445446798383362738 attempts 1
--
[  299.675210] lo: Disabled Privacy Extensions
[  871.756643] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[  871.756657] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[  871.756662] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[  871.756667] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[  871.756684] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[  871.756694] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[  871.756698] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[  871.756702] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[  879.574546] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  879.574555] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  879.574560] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  879.574634] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  879.574639] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[  879.574645] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[ 1091.492599] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[ 1091.492611] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x1, channel=0, format=0x4011
[ 1091.492628] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[ 1091.492636] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x1, channel=0, format=0x4011
[ 1127.965657] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[ 1127.965671] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[ 1127.965676] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[ 1127.965681] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[ 1127.965697] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[ 1127.965706] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[ 1127.965710] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[ 1127.965714] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[ 1131.222968] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[ 1131.223002] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[ 1136.813009] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[ 1136.813018] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[ 1136.813024] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[ 1136.813062] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[ 1136.813067] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[ 1136.813072] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[ 1152.830005] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[ 1152.830019] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[ 1152.830024] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[ 1152.830028] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[ 1152.830045] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[ 1152.830054] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[ 1152.830058] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[ 1152.830062] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[ 1152.831558] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[ 1152.831570] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x1, channel=0, format=0x4011
[ 1152.831587] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[ 1152.831595] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x1, channel=0, format=0x4011
[ 1310.254970] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[ 1310.254994] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[ 1310.256735] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[ 1310.256741] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[ 1310.256744] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[ 1310.256774] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[ 1310.256777] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[ 1310.256780] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[ 1318.923136] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[ 1318.923153] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[ 1318.923158] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[ 1318.923163] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[ 1318.923180] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[ 1318.923190] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[ 1318.923194] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[ 1318.923198] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[ 1318.924943] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[ 1318.924957] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x1, channel=0, format=0x4011
[ 1318.924975] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[ 1318.924983] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x1, channel=0, format=0x4011
[ 1334.834687] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[ 1334.834719] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[ 1334.838419] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[ 1334.838428] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[ 1334.838433] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[ 1334.838470] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[ 1334.838475] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[ 1334.838481] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[ 1336.200165] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[ 1336.200180] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[ 1336.200185] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[ 1336.200189] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[ 1336.200206] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[ 1336.200216] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[ 1336.200220] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[ 1336.200224] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[ 1336.205611] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[ 1336.205623] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x1, channel=0, format=0x4011
[ 1336.205641] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[ 1336.205649] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x1, channel=0, format=0x4011
[ 1360.013180] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[ 1360.013213] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x8
[ 1360.047357] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[ 1360.047365] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[ 1360.047371] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[ 1360.047410] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[ 1360.047415] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[ 1360.047420] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3

```

---

### Post by lidex on 2011-02-09
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

Then go to 'Sound Preferences' to select the correct device and mic ('Connector' option) and unmute your mic in 'Input' tab.
Make sure you have selected a profile with 'duplex' or 'analog input' for the correct sound device on the 'Hardware' tab.
Use Pulse Audio Volume Control (pavucontrol) to unlock stereo sliders for the mic in 'Input Devices' tab. Drag the right slider down to zero. 

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

### Post by badnaam on 2011-02-15
I have already tried those steps, all I hear is a large hiss when I record something. I see a Microphone1, Micrrophone2 and Line in connector options, I have tried setting the right mic to 0 for all of these. I have also tried playing with the mixer settings in alsamixer as well as pavucontrol. No luck.

Any ideas?

---

### Post by badnaam on 2011-02-18
Anyone?

Thanks

---

### Post by lidex on 2011-02-18
Try removing the 'toshiba' model switch from alsa-base.conf
It should look like this:
```
options snd-hda-intel model=toshiba
```
To edit:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Save your changes and close gedit. Next try updating your alsa-driver-modules.
Using a Terminal="Applications->Accessories->Terminal"
Add the ubuntu-audio-dev ppa:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```
Now install:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
**Reboot**
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

---

