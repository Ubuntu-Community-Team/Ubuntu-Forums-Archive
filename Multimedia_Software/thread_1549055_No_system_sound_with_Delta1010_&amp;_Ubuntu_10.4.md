---
title: "No system sound with Delta1010 &amp; Ubuntu 10.4"
date: 2010-08-09
forum: Multimedia Software
---

### Post by GinoCyber on 2010-08-09
Hi everyone,

I have disabled the ac97 sound chip from the motherboard bios.

When I go into the speaker properties to configure my sound card, all I see are options to select various digital inputs & outputs. There are no selections for the 8 analog ins & outs. Since I am only connecting the analog ins/outs of my sound card, I am assuming this is why I don't get any system sounds and all apps that use the system sound like Rhytmbox also gives me no sound.

The only app that gives me audio is audacity.

Jack crashes when using Alsa but is able to start when I select OSS.

I have entered snd_ad97 in the blacklist just to make sure but that didn't help.

Any ideas?

---

### Post by simosx on 2010-08-09
> **GinoCyber said:**
> Hi everyone,

I have disabled the ac97 sound chip from the motherboard bios.

When I go into the speaker properties to configure my sound card, all I see are options to select various digital inputs & outputs. There are no selections for the 8 analog ins & outs. Since I am only connecting the analog ins/outs of my sound card, I am assuming this is why I don't get any system sounds and all apps that use the system sound like Rhytmbox also gives me no sound.

The only app that gives me audio is audacity.

Jack crashes when using Alsa but is able to start when I select OSS.

I have entered snd_ad97 in the blacklist just to make sure but that didn't help.

Any ideas?

To figure out how to help, what's needed are the full details of your soundcard(s).

Obtain the full soundcard details with
[FONT="Courier New"]
wget [www.alsa-project.org/alsa-info.sh](www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh[/FONT]


When prompted, say Yes to send the data to alsa-project.org (Alsa website) and post here the URL you will be given. In this way we can see what hardware you have and if there are any problems.

---

### Post by GinoCyber on 2010-08-09
Thanks. I will get you this info tonite when I get home from work.

---

### Post by GinoCyber on 2010-08-09
Here you go:

upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.59
!!################################

!!Script ran on: Tue Aug 10 01:42:36 UTC 2010


!!Linux Distribution
!!------------------

Ubuntu 10.04.1 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"


!!DMI Information
!!---------------

Manufacturer:      System manufacturer
Product Name:      System Product Name


!!Kernel Information
!!------------------

Kernel release:    2.6.32-24-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.21
Library version:    1.0.22
Utilities version:  1.0.22


!!Loaded ALSA modules
!!-------------------

snd_ice1712
snd_mpu401


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No

Jack:
      Installed - Yes (/usr/bin/jackd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [M1010          ]: ICE1712 - M Audio Delta 1010
                      M Audio Delta 1010 at 0x9000, irq 16
 1 [UART           ]: MPU-401 UART - MPU-401 UART
                      MPU-401 UART at 0x330, irq 10


!!PCI Soundcards installed in the system
!!--------------------------------------

05:06.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

05:06.0 0401: 1412:1712 (rev 02)
	Subsystem: 1412:d630


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


!!Loaded sound module options
!!--------------------------

!!Module: snd_ice1712
	cs8427_timeout : 500,500,500,500,500,500,500,500,500,500,500,500,500,500,500,500,500,500,500,500,500,500,500,500,500,500,500,500,500,500,500,500
	dxr_enable : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
	index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	model : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
	omni : N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N

!!Module: snd_mpu401
	enable : Y,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N
	id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
	index : -2,-2,-2,-2,-2,-2,-2,-2,-2,-2,-2,-2,-2,-2,-2,-2,-2,-2,-2,-2,-2,-2,-2,-2,-2,-2,-2,-2,-2,-2,-2,-2
	irq : 10,65535,65535,65535,65535,65535,65535,65535,65535,65535,65535,65535,65535,65535,65535,65535,65535,65535,65535,65535,65535,65535,65535,65535,65535,65535,65535,65535,65535,65535,65535,65535
	pnp : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	port : 816,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1
	uart_enter : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116, 9 Dec 31  2005 /dev/snd/controlC0
crw-rw----+ 1 root audio 116, 5 Dec 31  2005 /dev/snd/controlC1
crw-rw----+ 1 root audio 116, 6 Dec 31  2005 /dev/snd/midiC0D0
crw-rw----+ 1 root audio 116, 4 Dec 31  2005 /dev/snd/midiC1D0
crw-rw----+ 1 root audio 116, 8 Aug  9 21:30 /dev/snd/pcmC0D0c
crw-rw----+ 1 root audio 116, 7 Aug  9 21:36 /dev/snd/pcmC0D0p
crw-rw----+ 1 root audio 116, 3 Dec 31  2005 /dev/snd/seq
crw-rw----+ 1 root audio 116, 2 Dec 31  2005 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Dec 31  2005 .
drwxr-xr-x 3 root root 220 Dec 31  2005 ..
lrwxrwxrwx 1 root root  12 Dec 31  2005 pci-0000:05:06.0 -> ../controlC0


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: M1010 [M Audio Delta 1010], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: M1010 [M Audio Delta 1010], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [M1010]

Card hw:0 'M1010'/'M Audio Delta 1010 at 0x9000, irq 16'
  Mixer name	: 'ICE1712 - multitrack'
  Components	: ''
  Controls      : 64
  Simple ctrls  : 38
Simple mixer control 'IEC958',0
  Capabilities: penum
  Items: 'PCM Out' 'H/W In 0' 'H/W In 1' 'H/W In 2' 'H/W In 3' 'H/W In 4' 'H/W In 5' 'H/W In 6' 'H/W In 7' 'IEC958 In L' 'IEC958 In R' 'Digital Mixer'
  Item0: 'Digital Mixer'
Simple mixer control 'IEC958 Multi',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 96
  Front Left: Capture 0 [0%] [off]
  Front Right: Capture 0 [0%] [off]
Simple mixer control 'IEC958 Multi',1
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 96
  Front Left: Capture 0 [0%] [off]
  Front Right: Capture 0 [0%] [off]
Simple mixer control 'IEC958',1
  Capabilities: penum
  Items: 'PCM Out' 'H/W In 0' 'H/W In 1' 'H/W In 2' 'H/W In 3' 'H/W In 4' 'H/W In 5' 'H/W In 6' 'H/W In 7' 'IEC958 In L' 'IEC958 In R' 'Digital Mixer'
  Item0: 'Digital Mixer'
Simple mixer control 'Delta IEC958 Input Status',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'H/W',0
  Capabilities: penum
  Items: 'PCM Out' 'H/W In 0' 'H/W In 1' 'H/W In 2' 'H/W In 3' 'H/W In 4' 'H/W In 5' 'H/W In 6' 'H/W In 7' 'IEC958 In L' 'IEC958 In R' 'Digital Mixer'
  Item0: 'PCM Out'
Simple mixer control 'H/W',1
  Capabilities: penum
  Items: 'PCM Out' 'H/W In 0' 'H/W In 1' 'H/W In 2' 'H/W In 3' 'H/W In 4' 'H/W In 5' 'H/W In 6' 'H/W In 7' 'IEC958 In L' 'IEC958 In R' 'Digital Mixer'
  Item0: 'PCM Out'
Simple mixer control 'H/W',2
  Capabilities: penum
  Items: 'PCM Out' 'H/W In 0' 'H/W In 1' 'H/W In 2' 'H/W In 3' 'H/W In 4' 'H/W In 5' 'H/W In 6' 'H/W In 7' 'IEC958 In L' 'IEC958 In R'
  Item0: 'PCM Out'
Simple mixer control 'H/W',3
  Capabilities: penum
  Items: 'PCM Out' 'H/W In 0' 'H/W In 1' 'H/W In 2' 'H/W In 3' 'H/W In 4' 'H/W In 5' 'H/W In 6' 'H/W In 7' 'IEC958 In L' 'IEC958 In R'
  Item0: 'PCM Out'
Simple mixer control 'H/W',4
  Capabilities: penum
  Items: 'PCM Out' 'H/W In 0' 'H/W In 1' 'H/W In 2' 'H/W In 3' 'H/W In 4' 'H/W In 5' 'H/W In 6' 'H/W In 7' 'IEC958 In L' 'IEC958 In R'
  Item0: 'PCM Out'
Simple mixer control 'H/W',5
  Capabilities: penum
  Items: 'PCM Out' 'H/W In 0' 'H/W In 1' 'H/W In 2' 'H/W In 3' 'H/W In 4' 'H/W In 5' 'H/W In 6' 'H/W In 7' 'IEC958 In L' 'IEC958 In R'
  Item0: 'PCM Out'
Simple mixer control 'H/W',6
  Capabilities: penum
  Items: 'PCM Out' 'H/W In 0' 'H/W In 1' 'H/W In 2' 'H/W In 3' 'H/W In 4' 'H/W In 5' 'H/W In 6' 'H/W In 7' 'IEC958 In L' 'IEC958 In R'
  Item0: 'H/W In 6'
Simple mixer control 'H/W',7
  Capabilities: penum
  Items: 'PCM Out' 'H/W In 0' 'H/W In 1' 'H/W In 2' 'H/W In 3' 'H/W In 4' 'H/W In 5' 'H/W In 6' 'H/W In 7' 'IEC958 In L' 'IEC958 In R'
  Item0: 'H/W In 7'
Simple mixer control 'H/W Multi',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 96
  Front Left: Capture 0 [0%] [-144.00dB] [off]
  Front Right: Capture 0 [0%] [-144.00dB] [off]
Simple mixer control 'H/W Multi',1
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 96
  Front Left: Capture 0 [0%] [-144.00dB] [off]
  Front Right: Capture 0 [0%] [-144.00dB] [off]
Simple mixer control 'H/W Multi',2
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 96
  Front Left: Capture 0 [0%] [-144.00dB] [off]
  Front Right: Capture 0 [0%] [-144.00dB] [off]
Simple mixer control 'H/W Multi',3
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 96
  Front Left: Capture 0 [0%] [-144.00dB] [off]
  Front Right: Capture 0 [0%] [-144.00dB] [off]
Simple mixer control 'H/W Multi',4
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 96
  Front Left: Capture 0 [0%] [-144.00dB] [off]
  Front Right: Capture 0 [0%] [-144.00dB] [off]
Simple mixer control 'H/W Multi',5
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 96
  Front Left: Capture 0 [0%] [-144.00dB] [off]
  Front Right: Capture 0 [0%] [-144.00dB] [off]
Simple mixer control 'H/W Multi',6
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 96
  Front Left: Capture 0 [0%] [-144.00dB] [off]
  Front Right: Capture 0 [0%] [-144.00dB] [off]
Simple mixer control 'H/W Multi',7
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 96
  Front Left: Capture 0 [0%] [-144.00dB] [off]
  Front Right: Capture 0 [0%] [-144.00dB] [off]
Simple mixer control 'Multi',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 96
  Mono:
  Front Left: Playback 0 [0%] [-144.00dB] [off]
  Front Right: Playback 0 [0%] [-144.00dB] [off]
Simple mixer control 'Multi',1
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 96
  Mono:
  Front Left: Playback 0 [0%] [-144.00dB] [off]
  Front Right: Playback 0 [0%] [-144.00dB] [off]
Simple mixer control 'Multi',2
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 96
  Mono:
  Front Left: Playback 0 [0%] [-144.00dB] [off]
  Front Right: Playback 0 [0%] [-144.00dB] [off]
Simple mixer control 'Multi',3
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 96
  Mono:
  Front Left: Playback 0 [0%] [-144.00dB] [off]
  Front Right: Playback 0 [0%] [-144.00dB] [off]
Simple mixer control 'Multi',4
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 96
  Mono:
  Front Left: Playback 0 [0%] [-144.00dB] [off]
  Front Right: Playback 0 [0%] [-144.00dB] [off]
Simple mixer control 'Multi',5
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 96
  Mono:
  Front Left: Playback 0 [0%] [-144.00dB] [off]
  Front Right: Playback 0 [0%] [-144.00dB] [off]
Simple mixer control 'Multi',6
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 96
  Mono:
  Front Left: Playback 0 [0%] [-144.00dB] [off]
  Front Right: Playback 0 [0%] [-144.00dB] [off]
Simple mixer control 'Multi',7
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 96
  Mono:
  Front Left: Playback 0 [0%] [-144.00dB] [off]
  Front Right: Playback 0 [0%] [-144.00dB] [off]
Simple mixer control 'Multi',8
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 96
  Mono:
  Front Left: Playback 0 [0%] [-144.00dB] [off]
  Front Right: Playback 0 [0%] [-144.00dB] [off]
Simple mixer control 'Multi',9
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 96
  Mono:
  Front Left: Playback 0 [0%] [-144.00dB] [off]
  Front Right: Playback 0 [0%] [-144.00dB] [off]
Simple mixer control 'Multi Track Internal Clock',0
  Capabilities: enum
  Items: '8000' '9600' '11025' '12000' '16000' '22050' '24000' '32000' '44100' '48000' '64000' '88200' '96000' 'IEC958 Input'
  Item0: '44100'
Simple mixer control 'Multi Track Internal Clock Default',0
  Capabilities: enum
  Items: '8000' '9600' '11025' '12000' '16000' '22050' '24000' '32000' '44100' '48000' '64000' '88200' '96000'
  Item0: '44100'
Simple mixer control 'Multi Track Rate Locking',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Multi Track Rate Reset',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Multi Track Volume Rate',0
  Capabilities: volume volume-joined penum
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 255
  Mono: 48 [19%]
Simple mixer control 'Word Clock Status',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Word Clock Sync',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]

!!-------Mixer controls for card 1 [UART]

Card hw:1 'UART'/'MPU-401 UART at 0x330, irq 10'
  Mixer name	: ''
  Components	: ''
  Controls      : 0
  Simple ctrls  : 0


!!Alsactl output
!!-------------

--startcollapse--
state.M1010 {
	control.1 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Multi Playback Switch'
		value.0 false
		value.1 false
	}
	control.2 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Multi Playback Switch'
		index 1
		value.0 false
		value.1 false
	}
	control.3 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Multi Playback Switch'
		index 2
		value.0 false
		value.1 false
	}
	control.4 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Multi Playback Switch'
		index 3
		value.0 false
		value.1 false
	}
	control.5 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Multi Playback Switch'
		index 4
		value.0 false
		value.1 false
	}
	control.6 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Multi Playback Switch'
		index 5
		value.0 false
		value.1 false
	}
	control.7 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Multi Playback Switch'
		index 6
		value.0 false
		value.1 false
	}
	control.8 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Multi Playback Switch'
		index 7
		value.0 false
		value.1 false
	}
	control.9 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Multi Playback Switch'
		index 8
		value.0 false
		value.1 false
	}
	control.10 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Multi Playback Switch'
		index 9
		value.0 false
		value.1 false
	}
	control.11 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 96'
		comment.dbmin -14400
		comment.dbmax 0
		iface MIXER
		name 'Multi Playback Volume'
		value.0 0
		value.1 0
	}
	control.12 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 96'
		comment.dbmin -14400
		comment.dbmax 0
		iface MIXER
		name 'Multi Playback Volume'
		index 1
		value.0 0
		value.1 0
	}
	control.13 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 96'
		comment.dbmin -14400
		comment.dbmax 0
		iface MIXER
		name 'Multi Playback Volume'
		index 2
		value.0 0
		value.1 0
	}
	control.14 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 96'
		comment.dbmin -14400
		comment.dbmax 0
		iface MIXER
		name 'Multi Playback Volume'
		index 3
		value.0 0
		value.1 0
	}
	control.15 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 96'
		comment.dbmin -14400
		comment.dbmax 0
		iface MIXER
		name 'Multi Playback Volume'
		index 4
		value.0 0
		value.1 0
	}
	control.16 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 96'
		comment.dbmin -14400
		comment.dbmax 0
		iface MIXER
		name 'Multi Playback Volume'
		index 5
		value.0 0
		value.1 0
	}
	control.17 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 96'
		comment.dbmin -14400
		comment.dbmax 0
		iface MIXER
		name 'Multi Playback Volume'
		index 6
		value.0 0
		value.1 0
	}
	control.18 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 96'
		comment.dbmin -14400
		comment.dbmax 0
		iface MIXER
		name 'Multi Playback Volume'
		index 7
		value.0 0
		value.1 0
	}
	control.19 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 96'
		comment.dbmin -14400
		comment.dbmax 0
		iface MIXER
		name 'Multi Playback Volume'
		index 8
		value.0 0
		value.1 0
	}
	control.20 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 96'
		comment.dbmin -14400
		comment.dbmax 0
		iface MIXER
		name 'Multi Playback Volume'
		index 9
		value.0 0
		value.1 0
	}
	control.21 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'H/W Multi Capture Switch'
		value.0 false
		value.1 false
	}
	control.22 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'H/W Multi Capture Switch'
		index 1
		value.0 false
		value.1 false
	}
	control.23 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'H/W Multi Capture Switch'
		index 2
		value.0 false
		value.1 false
	}
	control.24 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'H/W Multi Capture Switch'
		index 3
		value.0 false
		value.1 false
	}
	control.25 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'H/W Multi Capture Switch'
		index 4
		value.0 false
		value.1 false
	}
	control.26 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'H/W Multi Capture Switch'
		index 5
		value.0 false
		value.1 false
	}
	control.27 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'H/W Multi Capture Switch'
		index 6
		value.0 false
		value.1 false
	}
	control.28 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'H/W Multi Capture Switch'
		index 7
		value.0 false
		value.1 false
	}
	control.29 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'IEC958 Multi Capture Switch'
		value.0 false
		value.1 false
	}
	control.30 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'IEC958 Multi Capture Switch'
		index 1
		value.0 false
		value.1 false
	}
	control.31 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 96'
		comment.dbmin -14400
		comment.dbmax 0
		iface MIXER
		name 'H/W Multi Capture Volume'
		value.0 0
		value.1 0
	}
	control.32 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 96'
		comment.dbmin -14400
		comment.dbmax 0
		iface MIXER
		name 'H/W Multi Capture Volume'
		index 1
		value.0 0
		value.1 0
	}
	control.33 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 96'
		comment.dbmin -14400
		comment.dbmax 0
		iface MIXER
		name 'H/W Multi Capture Volume'
		index 2
		value.0 0
		value.1 0
	}
	control.34 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 96'
		comment.dbmin -14400
		comment.dbmax 0
		iface MIXER
		name 'H/W Multi Capture Volume'
		index 3
		value.0 0
		value.1 0
	}
	control.35 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 96'
		comment.dbmin -14400
		comment.dbmax 0
		iface MIXER
		name 'H/W Multi Capture Volume'
		index 4
		value.0 0
		value.1 0
	}
	control.36 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 96'
		comment.dbmin -14400
		comment.dbmax 0
		iface MIXER
		name 'H/W Multi Capture Volume'
		index 5
		value.0 0
		value.1 0
	}
	control.37 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 96'
		comment.dbmin -14400
		comment.dbmax 0
		iface MIXER
		name 'H/W Multi Capture Volume'
		index 6
		value.0 0
		value.1 0
	}
	control.38 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 96'
		comment.dbmin -14400
		comment.dbmax 0
		iface MIXER
		name 'H/W Multi Capture Volume'
		index 7
		value.0 0
		value.1 0
	}
	control.39 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 96'
		iface MIXER
		name 'IEC958 Multi Capture Volume'
		value.0 0
		value.1 0
	}
	control.40 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 96'
		iface MIXER
		name 'IEC958 Multi Capture Volume'
		index 1
		value.0 0
		value.1 0
	}
	control.41 {
		comment.access read
		comment.type BYTES
		comment.count 52
		iface CARD
		name 'ICE1712 EEPROM'
		value d63014121d011f80010322d0dd00000000000044010101010202020201000000000000000000000022000000d0000000dd000000
	}
	control.42 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 '8000'
		comment.item.1 '9600'
		comment.item.2 '11025'
		comment.item.3 '12000'
		comment.item.4 '16000'
		comment.item.5 '22050'
		comment.item.6 '24000'
		comment.item.7 '32000'
		comment.item.8 '44100'
		comment.item.9 '48000'
		comment.item.10 '64000'
		comment.item.11 '88200'
		comment.item.12 '96000'
		comment.item.13 'IEC958 Input'
		iface MIXER
		name 'Multi Track Internal Clock'
		value '44100'
	}
	control.43 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 '8000'
		comment.item.1 '9600'
		comment.item.2 '11025'
		comment.item.3 '12000'
		comment.item.4 '16000'
		comment.item.5 '22050'
		comment.item.6 '24000'
		comment.item.7 '32000'
		comment.item.8 '44100'
		comment.item.9 '48000'
		comment.item.10 '64000'
		comment.item.11 '88200'
		comment.item.12 '96000'
		iface MIXER
		name 'Multi Track Internal Clock Default'
		value '44100'
	}
	control.44 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Multi Track Rate Locking'
		value false
	}
	control.45 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Multi Track Rate Reset'
		value true
	}
	control.46 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 'PCM Out'
		comment.item.1 'H/W In 0'
		comment.item.2 'H/W In 1'
		comment.item.3 'H/W In 2'
		comment.item.4 'H/W In 3'
		comment.item.5 'H/W In 4'
		comment.item.6 'H/W In 5'
		comment.item.7 'H/W In 6'
		comment.item.8 'H/W In 7'
		comment.item.9 'IEC958 In L'
		comment.item.10 'IEC958 In R'
		comment.item.11 'Digital Mixer'
		iface MIXER
		name 'H/W Playback Route'
		value 'PCM Out'
	}
	control.47 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 'PCM Out'
		comment.item.1 'H/W In 0'
		comment.item.2 'H/W In 1'
		comment.item.3 'H/W In 2'
		comment.item.4 'H/W In 3'
		comment.item.5 'H/W In 4'
		comment.item.6 'H/W In 5'
		comment.item.7 'H/W In 6'
		comment.item.8 'H/W In 7'
		comment.item.9 'IEC958 In L'
		comment.item.10 'IEC958 In R'
		comment.item.11 'Digital Mixer'
		iface MIXER
		name 'H/W Playback Route'
		index 1
		value 'PCM Out'
	}
	control.48 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 'PCM Out'
		comment.item.1 'H/W In 0'
		comment.item.2 'H/W In 1'
		comment.item.3 'H/W In 2'
		comment.item.4 'H/W In 3'
		comment.item.5 'H/W In 4'
		comment.item.6 'H/W In 5'
		comment.item.7 'H/W In 6'
		comment.item.8 'H/W In 7'
		comment.item.9 'IEC958 In L'
		comment.item.10 'IEC958 In R'
		iface MIXER
		name 'H/W Playback Route'
		index 2
		value 'PCM Out'
	}
	control.49 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 'PCM Out'
		comment.item.1 'H/W In 0'
		comment.item.2 'H/W In 1'
		comment.item.3 'H/W In 2'
		comment.item.4 'H/W In 3'
		comment.item.5 'H/W In 4'
		comment.item.6 'H/W In 5'
		comment.item.7 'H/W In 6'
		comment.item.8 'H/W In 7'
		comment.item.9 'IEC958 In L'
		comment.item.10 'IEC958 In R'
		iface MIXER
		name 'H/W Playback Route'
		index 3
		value 'PCM Out'
	}
	control.50 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 'PCM Out'
		comment.item.1 'H/W In 0'
		comment.item.2 'H/W In 1'
		comment.item.3 'H/W In 2'
		comment.item.4 'H/W In 3'
		comment.item.5 'H/W In 4'
		comment.item.6 'H/W In 5'
		comment.item.7 'H/W In 6'
		comment.item.8 'H/W In 7'
		comment.item.9 'IEC958 In L'
		comment.item.10 'IEC958 In R'
		iface MIXER
		name 'H/W Playback Route'
		index 4
		value 'PCM Out'
	}
	control.51 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 'PCM Out'
		comment.item.1 'H/W In 0'
		comment.item.2 'H/W In 1'
		comment.item.3 'H/W In 2'
		comment.item.4 'H/W In 3'
		comment.item.5 'H/W In 4'
		comment.item.6 'H/W In 5'
		comment.item.7 'H/W In 6'
		comment.item.8 'H/W In 7'
		comment.item.9 'IEC958 In L'
		comment.item.10 'IEC958 In R'
		iface MIXER
		name 'H/W Playback Route'
		index 5
		value 'PCM Out'
	}
	control.52 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 'PCM Out'
		comment.item.1 'H/W In 0'
		comment.item.2 'H/W In 1'
		comment.item.3 'H/W In 2'
		comment.item.4 'H/W In 3'
		comment.item.5 'H/W In 4'
		comment.item.6 'H/W In 5'
		comment.item.7 'H/W In 6'
		comment.item.8 'H/W In 7'
		comment.item.9 'IEC958 In L'
		comment.item.10 'IEC958 In R'
		iface MIXER
		name 'H/W Playback Route'
		index 6
		value 'H/W In 6'
	}
	control.53 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 'PCM Out'
		comment.item.1 'H/W In 0'
		comment.item.2 'H/W In 1'
		comment.item.3 'H/W In 2'
		comment.item.4 'H/W In 3'
		comment.item.5 'H/W In 4'
		comment.item.6 'H/W In 5'
		comment.item.7 'H/W In 6'
		comment.item.8 'H/W In 7'
		comment.item.9 'IEC958 In L'
		comment.item.10 'IEC958 In R'
		iface MIXER
		name 'H/W Playback Route'
		index 7
		value 'H/W In 7'
	}
	control.54 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 'PCM Out'
		comment.item.1 'H/W In 0'
		comment.item.2 'H/W In 1'
		comment.item.3 'H/W In 2'
		comment.item.4 'H/W In 3'
		comment.item.5 'H/W In 4'
		comment.item.6 'H/W In 5'
		comment.item.7 'H/W In 6'
		comment.item.8 'H/W In 7'
		comment.item.9 'IEC958 In L'
		comment.item.10 'IEC958 In R'
		comment.item.11 'Digital Mixer'
		iface MIXER
		name 'IEC958 Playback Route'
		value 'Digital Mixer'
	}
	control.55 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 'PCM Out'
		comment.item.1 'H/W In 0'
		comment.item.2 'H/W In 1'
		comment.item.3 'H/W In 2'
		comment.item.4 'H/W In 3'
		comment.item.5 'H/W In 4'
		comment.item.6 'H/W In 5'
		comment.item.7 'H/W In 6'
		comment.item.8 'H/W In 7'
		comment.item.9 'IEC958 In L'
		comment.item.10 'IEC958 In R'
		comment.item.11 'Digital Mixer'
		iface MIXER
		name 'IEC958 Playback Route'
		index 1
		value 'Digital Mixer'
	}
	control.56 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 255'
		iface MIXER
		name 'Multi Track Volume Rate'
		value 48
	}
	control.57 {
		comment.access read
		comment.type INTEGER
		comment.count 22
		comment.range '0 - 255'
		iface PCM
		name 'Multi Track Peak'
		value.0 0
		value.1 0
		value.2 0
		value.3 0
		value.4 0
		value.5 0
		value.6 0
		value.7 0
		value.8 0
		value.9 0
		value.10 0
		value.11 0
		value.12 0
		value.13 0
		value.14 0
		value.15 0
		value.16 0
		value.17 0
		value.18 0
		value.19 0
		value.20 0
		value.21 0
	}
	control.58 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Word Clock Sync'
		value false
	}
	control.59 {
		comment.access read
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Word Clock Status'
		value true
	}
	control.60 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface PCM
		name 'IEC958 Playback Default'
		value '0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.61 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface PCM
		name 'IEC958 Playback Con Mask'
		value ffffffffff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
	}
	control.62 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface PCM
		name 'IEC958 Playback Pro Mask'
		value ffffffffff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
	}
	control.64 {
		comment.access read
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Delta IEC958 Input Status'
		value false
	}
}
state.UART {
	control {
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
binfmt_misc
snd_ice1712
snd_ice17xx_ak4xxx
snd_ak4xxx_adda
snd_cs8427
snd_ac97_codec
snd_pcm_oss
snd_mixer_oss
snd_pcm
snd_page_alloc
ac97_bus
snd_i2c
snd_mpu401
snd_mpu401_uart
snd_seq_dummy
snd_seq_oss
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
snd_seq
snd_timer
snd_seq_device
ns558
fbcon
tileblit
font
bitblit
softcursor
ppdev
gameport
nvidia
snd
psmouse
asus_atk0110
parport_pc
vga16fb
vgastate
serio_raw
k8temp
edac_core
edac_mce_amd
soundcore
i2c_nforce2
lp
parport
usbhid
hid
ohci1394
forcedeth
sata_nv
pata_amd
ieee1394
floppy


!!ALSA/HDA dmesg
!!------------------

---

### Post by lidex on 2010-08-09
See this:
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442)
BTW, if you're going to post large blocks of text, please use the code tags - the # in the post editing toolbar.

---

### Post by GinoCyber on 2010-08-10
Thanks for the link and sorry about the long post.

---

### Post by GinoCyber on 2010-08-11
For anyone who has a delta1010, the subsys id is 0xd630

Use it with solution #63 on the link mentioned by lidex and you're set.

---

### Post by lidex on 2010-08-11
Great. Don't forget to mark the thread solved. Thanks.

---

