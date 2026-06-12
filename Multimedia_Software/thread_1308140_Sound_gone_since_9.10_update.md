---
title: "Sound gone since 9.10 update"
date: 2009-10-31
forum: Multimedia Software
---

### Post by maff on 2009-10-31
Since the update to 9.10 my sound has vanished, it used to do this in 9.04 when it picked one of the tv capture cards by mistake, but not this time.

Im getting this:
```

maff@mythbox:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
maff@mythbox:~$ 

```

```

maff@mythbox:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0f.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:10.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:11.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation C68 [GeForce 7050 PV / nForce 630a] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:06.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
01:06.1 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
01:06.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
01:06.4 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [IR Port] (rev 05)
01:07.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
01:07.1 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
01:07.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
01:07.4 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [IR Port] (rev 05)
maff@mythbox:~$ 

```

and this from the alsa-info.sh script
```

upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.58
!!################################

!!Script ran on: Sat Oct 31 17:54:33 UTC 2009


!!Linux Distribution
!!------------------

Ubuntu 9.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 9.10"


!!DMI Information
!!---------------

Manufacturer:      System manufacturer
Product Name:      System Product Name


!!Kernel Information
!!------------------

Kernel release:    2.6.31-14-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.20
Library version:    1.0.20
Utilities version:  1.0.20


!!Loaded ALSA modules
!!-------------------

cx88_alsa
cx88_alsa


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

 0 [CX8801_1       ]: CX88x - Conexant CX8801
                      Conexant CX8801 at 0xda000000
 1 [CX8801         ]: CX88x - Conexant CX8801
                      Conexant CX8801 at 0xde000000


!!PCI Soundcards installed in the system
!!--------------------------------------

00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
01:06.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
01:06.1 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
01:06.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
01:06.4 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [IR Port] (rev 05)
01:07.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
01:07.1 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
01:07.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
01:07.4 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [IR Port] (rev 05)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:07.0 0403: 10de:055c (rev a1)
	Subsystem: 1043:8230


!!Modprobe options (Sound related)
!!--------------------------------

snd_hda_intel: index=0
snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-usb-caiaq: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-hda-intel: power_save=10 power_save_controller=N


!!Loaded sound module options
!!--------------------------

!!Module: cx88_alsa
	debug : 0
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	index : -2,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1

!!Module: cx88_alsa
	debug : 0
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	index : -2,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116, 7 Oct 31 17:16 /dev/snd/controlC0
crw-rw----+ 1 root audio 116, 5 Oct 31 17:16 /dev/snd/controlC1
crw-rw----+ 1 root audio 116, 6 Oct 31 17:42 /dev/snd/pcmC0D0c
crw-rw----+ 1 root audio 116, 4 Oct 31 17:42 /dev/snd/pcmC1D0c
crw-rw----+ 1 root audio 116, 3 Oct 31 17:16 /dev/snd/seq
crw-rw----+ 1 root audio 116, 2 Oct 31 17:16 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  80 Oct 31 17:16 .
drwxr-xr-x 3 root root 180 Oct 31 17:16 ..
lrwxrwxrwx 1 root root  12 Oct 31 17:16 pci-0000:01:06.1 -> ../controlC1
lrwxrwxrwx 1 root root  12 Oct 31 17:16 pci-0000:01:07.1 -> ../controlC0


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: CX8801_1 [Conexant CX8801], device 0: CX88 Digital [CX88 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CX8801 [Conexant CX8801], device 0: CX88 Digital [CX88 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [CX8801_1]

Card hw:0 'CX8801_1'/'Conexant CX8801 at 0xda000000'
  Mixer name	: 'CX88'
  Components	: ''
  Controls      : 3
  Simple ctrls  : 2
Simple mixer control 'Playback',0
  Capabilities: volume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 63
  Front Left: 54 [86%] [-9.00dB] Playback [on]
  Front Right: 54 [86%] [-9.00dB] Playback [on]
Simple mixer control 'Capture',0
  Capabilities: cswitch cswitch-joined
  Capture channels: Mono
  Mono: Capture [on]

!!-------Mixer controls for card 1 [CX8801]

Card hw:1 'CX8801'/'Conexant CX8801 at 0xde000000'
  Mixer name	: 'CX88'
  Components	: ''
  Controls      : 3
  Simple ctrls  : 2
Simple mixer control 'Playback',0
  Capabilities: volume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 63
  Front Left: 63 [100%] [0.00dB] Playback [on]
  Front Right: 63 [100%] [0.00dB] Playback [on]
Simple mixer control 'Capture',0
  Capabilities: cswitch cswitch-joined
  Capture channels: Mono
  Mono: Capture [on]


!!Alsactl output
!!-------------

--startcollapse--
state.CX8801_1 {
	control.1 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 63'
		comment.dbmin -6300
		comment.dbmax 0
		iface MIXER
		name 'Playback Volume'
		value.0 54
		value.1 54
	}
	control.2 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Playback Switch'
		value true
	}
	control.3 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Capture Switch'
		value true
	}
}
state.CX8801 {
	control.1 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 63'
		comment.dbmin -6300
		comment.dbmax 0
		iface MIXER
		name 'Playback Volume'
		value.0 63
		value.1 63
	}
	control.2 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Playback Switch'
		value true
	}
	control.3 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Capture Switch'
		value true
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
nls_iso8859_1
nls_cp437
vfat
fat
binfmt_misc
lirc_dev
bridge
stp
bnep
isl6421
cx24123
cx88_dvb
snd_hda_intel
cx88_vp3054_i2c
videobuf_dvb
snd_hda_codec
dvb_core
cx88_alsa
snd_hwdep
snd_pcm_oss
snd_mixer_oss
snd_pcm
cx8800
cx8802
cx88xx
snd_seq_dummy
snd_seq_oss
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
snd_seq
ir_common
snd_timer
i2c_algo_bit
snd_seq_device
v4l2_common
videodev
snd
sbp2
soundcore
tveeprom
v4l1_compat
ppdev
nvidia
videobuf_dma_sg
snd_page_alloc
ieee1394
videobuf_core
parport_pc
btcx_risc
iptable_filter
i2c_nforce2
joydev
lp
agpgart
psmouse
serio_raw
ip_tables
asus_atk0110
parport
x_tables
k8temp
btusb
usb_storage
dm_raid45
usbhid
xor
forcedeth


!!ALSA/HDA dmesg
!!------------------

[    9.675346] IRQ 19/cx88[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[    9.675367] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
[    9.676296] cx88[1]: subsystem: 0070:9202, board: Hauppauge Nova-S-Plus DVB-S [card=37,autodetected], frontend(s): 1
--
[    9.840319] IRQ 18/cx88[1]: IRQF_DISABLED is not guaranteed on shared IRQs
[    9.840335] cx88[1]/1: CX88x/1: ALSA support for cx2388x boards
[    9.917462] cannot find the slot for index 0 (range 0-1), error: -16
[    9.917517] hda-intel: Error creating card!
[    9.917572] HDA Intel: probe of 0000:00:07.0 failed with error -16
[    9.990005] cx88/2: cx2388x dvb driver version 0.0.7 loaded


```

Any help would be much apreciated.
Cheers

---

### Post by SurferGTO on 2009-11-16
same problem here man, so far no help and no suggestions. same audio device as well.

---

### Post by kschanaman on 2009-11-17
I have a similar problem with my system here as well. Get static/tinny sound, low volume and severe microphone noise in Audacity, upwards of -24 dB Only way I can record off of my system to Audacity is to set pulseaudio hardware profile setting to Analog 4.1 Outpout but then can't use the microphone. When setting to Analog 4.1 Output + Analog Stereo Input, I can't record audio off the system but CAN use the microphone, with the terrible system noise. Unmuting microphone causes system sounds to sound tinny and distorted. 

Vendor: nVidia Corporation
Product: MCP61 High Definition Audio
Version: a2
Width: 32 bits
Clock: 66 MHz
Capabilities: pm msi ht bus_master cap_list
Configuration: HDA Intel latency=0 maxlatency=5 mingnt=2
Resources: irq:21 memory: dfe78000-dfe7bfff

It's an IEC985 listing under gnome-alsamixer

With these problems, Ubuntu Studio isn't really anything "studio" at all. Nothing studio-quality about it.

---

### Post by VertexPusher on 2009-11-17
> **kschanaman said:**
> I have a similar problem with my system here as well. Get static/tinny sound, low volume and severe microphone noise
Your problem isn't similar at all. Your sound isn't gone, your audio devices aren't missing. You are more likely to get help if you open a separate thread.

---

### Post by raghaven.kumar on 2010-02-10
Hi,

Even for me after updating to Ubuntu 9.10 i get distorted audio.
Really Horrible!!
Some system data:
```
:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
:~$ 
:~$ sudo lshw -class sound
  *-multimedia            
       description: Audio device
       product: MCP61 High Definition Audio
       vendor: nVidia Corporation
       physical id: 5
       bus info: pci@0000:00:05.0
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list
       configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2
       resources: irq:21 memory:dfff8000-dfffbfff
:~$ 
```My /var/log/messages says this```
Feb 10 19:52:08 example kernel: [164780.692033] hda_codec: invalid CONNECT_LIST verb 12[2]:2100
Feb 10 19:54:13 example kernel: [164905.680033] hda_codec: invalid CONNECT_LIST verb 12[2]:2100
Feb 10 20:32:43 example pulseaudio[16110]: ratelimit.c: 9 events suppressed
Feb 10 20:41:49 example kernel: [167761.312042] hda_codec: invalid CONNECT_LIST verb 12[2]:2100

```
What could be the issue guys?
Cant listen to a nice song :( :(

---

