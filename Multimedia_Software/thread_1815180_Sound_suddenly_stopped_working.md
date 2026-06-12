---
title: "Sound suddenly stopped working"
date: 2011-07-30
forum: Multimedia Software
---

### Post by JimPBarber on 2011-07-30
Hi,

  Thanks for reading my thread.  A couple of days ago my sound stopped working all together.  I have no idea why.  I have an external usb card that was working and works on my other Ubuntu installs  all are 11.04.  We faithfully install our updates.  Any help is appreciated.

My ALSA info is below:

upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Sat Jul 30 23:57:35 UTC 2011


!!Linux Distribution
!!------------------

Ubuntu 11.04 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 11.04"


!!DMI Information
!!---------------

Manufacturer:      Supermicro
Product Name:      X6DH8
Product Version:   0123456789


!!Kernel Information
!!------------------

Kernel release:    2.6.38-11-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         x86_64
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.23
Library version:    1.0.24.1
Utilities version:  1.0.24.2


!!Loaded ALSA modules
!!-------------------

snd_usb_audio


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

 1 [default        ]: USB-Audio - C-Media USB Headphone Set  
                      C-Media USB Headphone Set   at usb-0000:00:1d.1-1, full speed


!!PCI Soundcards installed in the system
!!--------------------------------------



!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------



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

!!Module: snd_usb_audio
	async_unlink : Y
	device_setup : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	ignore_ctl_error : N
	index : -2,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	nrpacks : 8
	pid : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	vid : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1


!!USB Mixer information
!!---------------------------
--startcollapse--

USB Mixer: usb_id=0x0d8c000c, ctrlif=0, ctlerr=0
Card: C-Media USB Headphone Set   at usb-0000:00:1d.1-1, full speed
  Unit: 9
    Control: name="Speaker Playback Volume", index=0
    Info: id=9, control=2, cmask=0x3, channels=2, type="S16"
    Volume: min=-7264, max=-16, dBmin=-2837, dBmax=-6
  Unit: 9
    Control: name="Speaker Playback Switch", index=0
    Info: id=9, control=1, cmask=0x0, channels=1, type="INV_BOOLEAN"
    Volume: min=0, max=1, dBmin=0, dBmax=0
  Unit: 10
    Control: name="Auto Gain Control", index=0
    Info: id=10, control=7, cmask=0x0, channels=1, type="BOOLEAN"
    Volume: min=0, max=1, dBmin=0, dBmax=0
  Unit: 10
    Control: name="Mic Capture Volume", index=0
    Info: id=10, control=2, cmask=0x0, channels=1, type="S16"
    Volume: min=0, max=6096, dBmin=0, dBmax=2381
  Unit: 10
    Control: name="Mic Capture Switch", index=0
    Info: id=10, control=1, cmask=0x0, channels=1, type="INV_BOOLEAN"
    Volume: min=0, max=1, dBmin=0, dBmax=0
  Unit: 13
    Control: name="Mic Playback Volume", index=0
    Info: id=13, control=2, cmask=0x0, channels=1, type="S16"
    Volume: min=0, max=12240, dBmin=0, dBmax=4781
  Unit: 13
    Control: name="Mic Playback Switch", index=0
    Info: id=13, control=1, cmask=0x0, channels=1, type="INV_BOOLEAN"
    Volume: min=0, max=1, dBmin=0, dBmax=0
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116,  4 Jul 30 16:47 /dev/snd/controlC1
crw-rw----+ 1 root audio 116,  3 Jul 30 16:47 /dev/snd/pcmC1D0c
crw-rw----+ 1 root audio 116,  2 Jul 30 16:57 /dev/snd/pcmC1D0p
crw-rw----+ 1 root audio 116,  1 Jul 30 16:47 /dev/snd/seq
crw-rw----+ 1 root audio 116, 33 Jul 30 16:47 /dev/snd/timer

/dev/snd/by-id:
total 0
drwxr-xr-x 2 root root  60 Jul 30 16:47 .
drwxr-xr-x 4 root root 180 Jul 30 16:47 ..
lrwxrwxrwx 1 root root  12 Jul 30 16:47 usb-0d8c_C-Media_USB_Headphone_Set-00 -> ../controlC1

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Jul 30 16:47 .
drwxr-xr-x 4 root root 180 Jul 30 16:47 ..
lrwxrwxrwx 1 root root  12 Jul 30 16:47 pci-0000:00:1d.1-usb-0:1:1.0 -> ../controlC1


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 1: default [C-Media USB Headphone Set  ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 1: default [C-Media USB Headphone Set  ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 1 [default]

Card hw:1 'default'/'C-Media USB Headphone Set   at usb-0000:00:1d.1-1, full speed'
  Mixer name	: 'USB Mixer'
  Components	: 'USB0d8c:000c'
  Controls      : 7
  Simple ctrls  : 3
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 151
  Mono:
  Front Left: Playback 0 [0%] [-28.37dB] [on]
  Front Right: Playback 0 [0%] [-28.37dB] [on]
Simple mixer control 'Mic',0
  Capabilities: pvolume pvolume-joined cvolume cvolume-joined pswitch pswitch-joined cswitch cswitch-joined penum
  Playback channels: Mono
  Capture channels: Mono
  Limits: Playback 0 - 32 Capture 0 - 16
  Mono: Playback 23 [72%] [34.36dB] [off] Capture 16 [100%] [23.81dB] [on]
Simple mixer control 'Auto Gain Control',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]


!!Alsactl output
!!-------------

--startcollapse--
state.default {
	control.1 {
		iface MIXER
		name 'Mic Playback Switch'
		value false
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.2 {
		iface MIXER
		name 'Mic Playback Volume'
		value 23
		comment {
			access 'read write'
			type INTEGER
			count 1
			range '0 - 32'
			dbmin 0
			dbmax 4781
			dbvalue.0 3436
		}
	}
	control.3 {
		iface MIXER
		name 'Speaker Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.4 {
		iface MIXER
		name 'Speaker Playback Volume'
		value.0 0
		value.1 0
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 151'
			dbmin -2837
			dbmax -6
			dbvalue.0 -2837
			dbvalue.1 -2837
		}
	}
	control.5 {
		iface MIXER
		name 'Mic Capture Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.6 {
		iface MIXER
		name 'Mic Capture Volume'
		value 16
		comment {
			access 'read write'
			type INTEGER
			count 1
			range '0 - 16'
			dbmin 0
			dbmax 2381
			dbvalue.0 2381
		}
	}
	control.7 {
		iface MIXER
		name 'Auto Gain Control'
		value true
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
sha256_generic
cryptd
aes_x86_64
aes_generic
binfmt_misc
dm_crypt
vesafb
nvidia
snd_usb_audio
snd_pcm
snd_page_alloc
snd_hwdep
snd_usbmidi_lib
snd_seq_midi
snd_rawmidi
nfsd
lockd
nfs_acl
auth_rpcgss
sunrpc
exportfs
snd_seq_midi_event
snd_seq
snd_timer
snd_seq_device
snd
soundcore
ppdev
psmouse
serio_raw
parport_pc
shpchp
e752x_edac
edac_core
lp
parport
usbhid
hid
floppy
e1000
aic79xx
scsi_transport_spi


!!ALSA/HDA dmesg
!!------------------

---

