---
title: "Crackling sound"
date: 2011-01-15
forum: Multimedia Software
---

### Post by Kryzzalid on 2011-01-15
Hi.

Since my update to Lucid my sound has been crackling. I've tried to "play" with the sound mixer and reinstall ALSA and other few thing i read on internet but no can do nothing seems to work. I can increase the sound till about 30% after that the crackling noise becomes annoying. Here are some information about the system:

```

!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Sat Jan 15 11:16:52 UTC 2011


!!Linux Distribution
!!------------------

Ubuntu 10.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.10"


!!DMI Information
!!---------------

Manufacturer:      Hewlett-Packard
Product Name:      Pavilion ZV6100 (EE976EA#AK8)     
Product Version:   F.1C


!!Kernel Information
!!------------------

Kernel release:    2.6.35-24-generic
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

snd_atiixp
snd_atiixp_modem


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

 0 [IXP            ]: ATIIXP - ATI IXP
                      ATI IXP rev 1 with Cx20468-31 at 0xb0003400, irq 17
 1 [Modem          ]: ATIIXP-MODEM - ATI IXP Modem
                      ATI IXP Modem rev 1 at 0xb0003800, irq 17


!!PCI Soundcards installed in the system
!!--------------------------------------

00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 01)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

00:14.5 0401: 1002:4370 (rev 01)
	Subsystem: 103c:3085


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

!!Module: snd_atiixp
	ac97_clock : 48000
	ac97_codec : -1
	ac97_quirk : (null)
	enable : N
	id : (null)
	index : -1
	spdif_aclink : Y

!!Module: snd_atiixp_modem
	ac97_clock : 48000
	enable : N
	id : (null)
	index : -2


!!AC97 Codec information
!!---------------------------
--startcollapse--

0-0/0: Conexant Cx20468-31

PCI Subsys Vendor: 0x103c
PCI Subsys Device: 0x3085

Flags: 8
Revision         : 0x00
Compat. Class    : 0x00
Subsys. Vendor ID: 0x0000
Subsys. ID       : 0x0000

Capabilities     : -reserved1- -headphone out-
DAC resolution   : 18-bit
ADC resolution   : 18-bit
3D enhancement   : No 3D Stereo Enhancement

Current setup
Mic gain         :  20dB [ 20dB]
POP path         : pre 3D
Sim. stereo      : off
3D enhancement   : off
Loudness         : off
Mono output      : MIX
Mic select       : Mic1
ADC/DAC loopback : off
Extended ID      : codec=0 rev=2 AMAP DSA=0 SPDIF
Extended status  : PRL PRK PRJ PRI SPCV SPDIF=7/8
SPDIF Control    : Consumer PCM Copyright Category=0x0 Generation=0 Rate=48kHz
Extended modem ID: codec=0 LIN1
Modem status     : GPIO
Line1 rate       : 48000Hz

0:00 = 0152
0:02 = 0e0e
0:04 = 0000
0:06 = 0000
0:08 = 0000
0:0a = 8000
0:0c = 0000
0:0e = 805f
0:10 = 0000
0:12 = 0000
0:14 = 0000
0:16 = 0000
0:18 = 0b0b
0:1a = 0000
0:1c = 0000
0:1e = 0000
0:20 = 0000
0:22 = 0000
0:24 = 0000
0:26 = 800f
0:28 = 0a04
0:2a = 7c10
0:2c = bb80
0:2e = 0000
0:30 = 0000
0:32 = bb80
0:34 = 0000
0:36 = 0000
0:38 = 0000
0:3a = 2000
0:3c = 0001
0:3e = 0001
0:40 = bb80
0:42 = 0000
0:44 = 0000
0:46 = 0000
0:48 = 0000
0:4a = 0000
0:4c = 0030
0:4e = ffff
0:50 = 0000
0:52 = 0000
0:54 = 0000
0:56 = 0000
0:58 = 0000
0:5a = 0000
0:5c = 060c
0:5e = a001
0:60 = 0000
0:62 = 0000
0:64 = 0000
0:66 = 0012
0:68 = 0000
0:6a = 8000
0:6c = 0000
0:6e = 0000
0:70 = 0000
0:72 = 0000
0:74 = 0000
0:76 = 0000
0:78 = 0000
0:7a = 8004
0:7c = 4358
0:7e = 5430
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----  1 root audio 116, 9 Jan 15 13:07 /dev/snd/controlC0
crw-rw----  1 root audio 116, 6 Jan 15 13:07 /dev/snd/controlC1
crw-rw----  1 root audio 116, 8 Jan 15 13:09 /dev/snd/pcmC0D0c
crw-rw----  1 root audio 116, 7 Jan 15 13:09 /dev/snd/pcmC0D0p
crw-rw----  1 root audio 116, 5 Jan 15 13:07 /dev/snd/pcmC1D0c
crw-rw----  1 root audio 116, 4 Jan 15 13:07 /dev/snd/pcmC1D0p
crw-rw----  1 root audio 116, 3 Jan 15 13:07 /dev/snd/seq
crw-rw----  1 root audio 116, 2 Jan 15 13:07 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  80 Jan 15 13:07 .
drwxr-xr-x 3 root root 220 Jan 15 13:07 ..
lrwxrwxrwx 1 root root  12 Jan 15 13:07 pci-0000:00:14.5 -> ../controlC0
lrwxrwxrwx 1 root root  12 Jan 15 13:07 pci-0000:00:14.6 -> ../controlC1


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Modem [ATI IXP Modem], device 0: ATI IXP MC97 [ATI IXP MC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Modem [ATI IXP Modem], device 0: ATI IXP MC97 [ATI IXP MC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [IXP]

Card hw:0 'IXP'/'ATI IXP rev 1 with Cx20468-31 at 0xb0003400, irq 17'
  Mixer name	: 'Conexant Cx20468-31'
  Components	: 'AC97a:43585430'
  Controls      : 23
  Simple ctrls  : 16
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 17 [55%] [-21.00dB] [on]
  Front Right: Playback 17 [55%] [-21.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 20 [65%] [-4.50dB] [on]
  Front Right: Playback 20 [65%] [-4.50dB] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 31 [100%] [12.00dB] [on] Capture [off]
  Front Right: Playback 31 [100%] [12.00dB] [on] Capture [off]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 31 [100%] [12.00dB] [on] Capture [off]
  Front Right: Playback 31 [100%] [12.00dB] [on] Capture [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-34.50dB] [off]
  Front Left: Capture [on]
  Front Right: Capture [on]
Simple mixer control 'Mic Boost ( 20dB)',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Video',0
  Capabilities: cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Phone',0
  Capabilities: cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Beep',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 15
  Mono: Playback 0 [0%] [-45.00dB] [off]
Simple mixer control 'Aux',0
  Capabilities: cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch cswitch-joined penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 0 [0%] [0.00dB] [on]
  Front Right: Capture 0 [0%] [0.00dB] [on]
Simple mixer control 'Mix',0
  Capabilities: cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Mix Mono',0
  Capabilities: cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'External Amplifier',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]

!!-------Mixer controls for card 1 [Modem]

Card hw:1 'Modem'/'ATI IXP Modem rev 1 at 0xb0003800, irq 17'
  Mixer name	: 'Conexant Cx20468-31'
  Components	: 'AC97m:43585430'
  Controls      : 2
  Simple ctrls  : 2
Simple mixer control 'Caller ID',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Off-hook',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]


!!Alsactl output
!!-------------

--startcollapse--
state.IXP {
	control.1 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Master Playback Switch'
		value true
	}
	control.2 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -4650
		comment.dbmax 0
		iface MIXER
		name 'Master Playback Volume'
		value.0 17
		value.1 17
	}
	control.3 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Headphone Playback Switch'
		value true
	}
	control.4 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -4650
		comment.dbmax 0
		iface MIXER
		name 'Headphone Playback Volume'
		value.0 31
		value.1 31
	}
	control.5 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Beep Playback Switch'
		value false
	}
	control.6 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 15'
		comment.dbmin -4500
		comment.dbmax 0
		iface MIXER
		name 'Beep Playback Volume'
		value 0
	}
	control.7 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Mic Playback Switch'
		value false
	}
	control.8 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Mic Playback Volume'
		value 0
	}
	control.9 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Mic Boost ( 20dB)'
		value true
	}
	control.10 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Line Playback Switch'
		value true
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
		value.0 31
		value.1 31
	}
	control.12 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'CD Playback Switch'
		value true
	}
	control.13 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'CD Playback Volume'
		value.0 31
		value.1 31
	}
	control.14 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'PCM Playback Switch'
		value true
	}
	control.15 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'PCM Playback Volume'
		value.0 20
		value.1 20
	}
	control.16 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 2
		comment.item.0 Mic
		comment.item.1 CD
		comment.item.2 Video
		comment.item.3 Aux
		comment.item.4 Line
		comment.item.5 Mix
		comment.item.6 'Mix Mono'
		comment.item.7 Phone
		iface MIXER
		name 'Capture Source'
		value.0 Mic
		value.1 Mic
	}
	control.17 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Capture Switch'
		value true
	}
	control.18 {
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
	control.19 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Con Mask'
		value '0fff000f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.20 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		value cf00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
	}
	control.21 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Default'
		value '0082000200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.22 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Switch'
		value true
	}
	control.23 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'External Amplifier'
		value false
	}
}
state.Modem {
	control.1 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Off-hook Switch'
		value false
	}
	control.2 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Caller ID Switch'
		value false
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
cryptd
aes_x86_64
aes_generic
rfcomm
binfmt_misc
sco
bnep
l2cap
vboxnetadp
vboxnetflt
vboxdrv
parport_pc
ppdev
ipt_REJECT
ipt_LOG
xt_limit
xt_tcpudp
ipt_addrtype
xt_state
snd_atiixp
snd_atiixp_modem
snd_ac97_codec
ac97_bus
ip6table_filter
snd_pcm
ip6_tables
snd_seq_midi
nf_nat_irc
snd_rawmidi
nf_conntrack_irc
snd_seq_midi_event
radeon
nf_nat_ftp
snd_seq
nf_nat
pcmcia
snd_timer
arc4
b43
nf_conntrack_ipv4
nf_defrag_ipv4
mac80211
nf_conntrack_ftp
nf_conntrack
ttm
firewire_ohci
tifm_7xx1
sdhci_pci
snd_seq_device
yenta_socket
usbhid
drm_kms_helper
firewire_core
sdhci
tifm_core
iptable_filter
pcmcia_rsrc
drm
pcmcia_core
hid
edac_core
crc_itu_t
cfg80211
snd
ssb
soundcore
i2c_algo_bit
edac_mce_amd
led_class
btusb
ip_tables
snd_page_alloc
i2c_piix4
joydev
8139too
8139cp
mii
shpchp
bluetooth
x_tables
video
hp_wmi
k8temp
output
psmouse
serio_raw
lp
parport
pata_atiixp


!!ALSA/HDA dmesg
!!-----------------


```


Thank you!

---

