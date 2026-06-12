---
title: "sound was working, now it's not"
date: 2010-11-26
forum: Multimedia Software
---

### Post by alvinmoneypit on 2010-11-26
I installed ubuntu 10.10 a couple weeks ago onto a brand new drive in this old AMD XP3200 system on a soyo motherboard with a  VIA 8237.  I had sound originally. 

 I notice 2 of my channels on this 5.1 system weren't working.  So I came to [this thread]("http://ubuntuforums.org/showthread.php?t=1593095") and tried some of the solutions there.  One of them, I think "update", "upgrade" and uninstall, reinstall alsa caused me to lose sound completely, the speaker icon on the top panel disappeared at the same time and cannot be recovered through panel preferences.

Through following some suggestions I found on various threads, It seems ubuntu sees my correct card, has the correct driver installed, I have my user prefs set up to use sound, I don't have anything muted anywhere that I can tell, yet no sound, not even the familiar click of the speakers when booting up.  

Any suggestions short of reloading from scratch?

I do get some errors on some searches, but not really sure what they mean or it they affect anything like the one below:```
 pulseaudio -vvv
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
D: core-rtclock.c: Timer slack is set to 50 us.
D: core-util.c: RealtimeKit worked.
I: core-util.c: Successfully gained nice level -11.
I: main.c: This is PulseAudio 0.9.21-63-gd3efa-dirty
D: main.c: Compilation host: i686-pc-linux-gnu
D: main.c: Compilation CFLAGS: -g -O2 -g -Wall -O3 -Wall -W -Wextra -pipe -Wno-long-long -Winline -Wvla -Wno-overlength-strings -Wunsafe-loop-optimizations -Wundef -Wformat=2 -Wlogical-op -Wsign-compare -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wold-style-definition -Wpointer-arith -Winit-self -Wdeclaration-after-statement -Wfloat-equal -Wmissing-prototypes -Wstrict-prototypes -Wredundant-decls -Wmissing-declarations -Wmissing-noreturn -Wshadow -Wendif-labels -Wcast-align -Wstrict-aliasing=2 -Wwrite-strings -Wno-unused-parameter -ffast-math -Wp,-D_FORTIFY_SOURCE=2 -fno-common -fdiagnostics-show-option
D: main.c: Running on host: Linux i686 2.6.35-23-generic #40-Ubuntu SMP Wed Nov 17 22:15:35 UTC 2010
D: main.c: Found 1 CPUs.
I: main.c: Page size is 4096 bytes
D: main.c: Compiled with Valgrind support: no
D: main.c: Running in valgrind mode: no
D: main.c: Running in VM: no
D: main.c: Optimized build: yes
D: main.c: All asserts enabled.
I: main.c: Machine ID is eab30b2f66a9aebab9786d8900000007.
I: main.c: Session ID is eab30b2f66a9aebab9786d8900000007-1290784256.133119-222843676.
I: main.c: Using runtime directory /home/patty/.pulse/eab30b2f66a9aebab9786d8900000007-runtime.
I: main.c: Using state directory /home/patty/.pulse.
I: main.c: Using modules directory /usr/lib/pulse-0.9.21/modules.
I: main.c: Running in system mode: no
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.

```

---

### Post by lidex on 2010-11-27
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by alvinmoneypit on 2010-11-28
Hi lidex,

I'll have to get back on this, it will be a couple of weeks. This system was never run on Windows XP or otherwise since it always had a separate sound card.  It has had a BIOS update.

---

### Post by alvinmoneypit on 2010-12-12
Here is the output of the command.  Looks like esound and some other things aren't working - I don't know if I need these or not.  :
```
upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.59
!!################################

!!Script ran on: Mon Dec 13 03:11:14 UTC 2010


!!Linux Distribution
!!------------------

Ubuntu 10.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.10"


!!DMI Information
!!---------------

Manufacturer:      soyocomputer
Product Name:      K7VKPE


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

snd_via82xx


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

 0 [V8237          ]: VIA8237 - VIA 8237
                      VIA 8237 with CMI9761A+ at 0xc400, irq 22


!!PCI Soundcards installed in the system
!!--------------------------------------

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:11.5 0401: 1106:3059 (rev 60)
	Subsystem: 1019:a101


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

!!Module: snd_via82xx
	ac97_clock : 48000
	ac97_quirk : (null)
	dxs_support : 5
	enable : N
	id : (null)
	index : -1
	joystick : N
	mpu_port : 0
	nodelay : 0


!!AC97 Codec information
!!---------------------------
--startcollapse--

0-0/0: C-Media Electronics CMI9761A+

PCI Subsys Vendor: 0x1019
PCI Subsys Device: 0xa101

Flags: 80
Revision         : 0x01
Compat. Class    : 0x03
Subsys. Vendor ID: 0xffff
Subsys. ID       : 0xffff

Capabilities     :
DAC resolution   : 16-bit
ADC resolution   : 16-bit
3D enhancement   : No 3D Stereo Enhancement

Current setup
Mic gain         : +0dB [+0dB]
POP path         : pre 3D
Sim. stereo      : off
3D enhancement   : off
Loudness         : off
Mono output      : MIX
Mic select       : Mic1
ADC/DAC loopback : off
Double rate slots: 10/11
Extended ID      : codec=0 rev=2 AMAP LDAC SDAC CDAC DSA=0 DRA
Extended status  : SPCV LDAC SDAC CDAC SPDIF

0:00 = 0000
0:02 = 8b0b
0:04 = 0000
0:06 = 0000
0:08 = 0000
0:0a = 800c
0:0c = 0000
0:0e = 8c0c
0:10 = 0000
0:12 = 0606
0:14 = 0000
0:16 = 8909
0:18 = 8808
0:1a = 0000
0:1c = 0a0a
0:1e = 0000
0:20 = 0000
0:22 = 0000
0:24 = 0000
0:26 = 000f
0:28 = 0bc2
0:2a = 05d4
0:2c = 0000
0:2e = 0000
0:30 = 0000
0:32 = 0000
0:34 = 0000
0:36 = 8080
0:38 = 8080
0:3a = 2824
0:3c = 0000
0:3e = 0000
0:40 = 0000
0:42 = 0000
0:44 = 0000
0:46 = 0000
0:48 = 0000
0:4a = 0000
0:4c = 0000
0:4e = 0000
0:50 = 0000
0:52 = 0000
0:54 = 0000
0:56 = 0000
0:58 = 0000
0:5a = 0000
0:5c = 0004
0:5e = 0000
0:60 = 0000
0:62 = 0000
0:64 = 3038
0:66 = 0016
0:68 = 0000
0:6a = 0000
0:6c = 0011
0:6e = 0000
0:70 = 0100
0:72 = 0020
0:74 = c000
0:76 = 3f3c
0:78 = 0000
0:7a = 0000
0:7c = 434d
0:7e = 4983
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116, 8 Dec 12 11:21 /dev/snd/controlC0
crw-rw----+ 1 root audio 116, 7 Dec 12 11:23 /dev/snd/pcmC0D0c
crw-rw----+ 1 root audio 116, 6 Dec 12 11:23 /dev/snd/pcmC0D0p
crw-rw----+ 1 root audio 116, 5 Dec 12 11:21 /dev/snd/pcmC0D1c
crw-rw----+ 1 root audio 116, 4 Dec 12 22:05 /dev/snd/pcmC0D1p
crw-rw----+ 1 root audio 116, 3 Dec 12 11:21 /dev/snd/seq
crw-rw----+ 1 root audio 116, 2 Dec 12 11:21 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Dec 12 11:21 .
drwxr-xr-x 3 root root 200 Dec 12 11:21 ..
lrwxrwxrwx 1 root root  12 Dec 12 11:21 pci-0000:00:11.5 -> ../controlC0


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [V8237]

Card hw:0 'V8237'/'VIA 8237 with CMI9761A+ at 0xc400, irq 22'
  Mixer name	: 'C-Media Electronics CMI9761A+'
  Components	: 'AC97a:434d4983'
  Controls      : 41
  Simple ctrls  : 30
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 20 [65%] [-16.50dB] [off]
  Front Right: Playback 20 [65%] [-16.50dB] [off]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [off]
  Front Right: Playback 31 [100%] [0.00dB] [off]
Simple mixer control 'Surround',0
  Capabilities: pswitch penum
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [off]
  Front Right: Playback [off]
Simple mixer control 'Surround Jack Mode',0
  Capabilities: enum
  Items: 'Shared' 'Independent'
  Item0: 'Independent'
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 20 [65%] [-16.50dB] [off]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 20 [65%] [-16.50dB] [off]
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
  Front Left: Playback 25 [81%] [3.00dB] [on] Capture [off]
  Front Right: Playback 25 [81%] [3.00dB] [on] Capture [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 19 [61%] [-6.00dB] [off] Capture [on]
  Front Right: Playback 19 [61%] [-6.00dB] [off] Capture [on]
Simple mixer control 'Mic Boost (+20dB)',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Mic Select',0
  Capabilities: enum
  Items: 'Mic1' 'Mic2'
  Item0: 'Mic1'
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
  Capabilities: pswitch pswitch-joined cswitch cswitch-joined penum
  Playback channels: Mono
  Capture channels: Mono
  Mono: Playback [on] Capture [on]
Simple mixer control 'IEC958 Capture Monitor',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 Capture Valid',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 Output',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 Playback AC97-SPSA',0
  Capabilities: volume volume-joined penum
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 3
  Mono: 1 [33%]
Simple mixer control 'IEC958 Playback Source',0
  Capabilities: enum
  Items: 'AC-Link' 'ADC' 'SPDIF-In'
  Item0: 'AC-Link'
Simple mixer control 'Beep',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 15
  Mono: Playback 9 [60%] [-18.00dB] [off]
Simple mixer control 'Aux',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 22 [71%] [-1.50dB] [off] Capture [off]
  Front Right: Playback 22 [71%] [-1.50dB] [off] Capture [off]
Simple mixer control 'Mono Output Select',0
  Capabilities: enum
  Items: 'Mix' 'Mic'
  Item0: 'Mix'
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch cswitch-joined penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 10 [67%] [15.00dB] [on]
  Front Right: Capture 10 [67%] [15.00dB] [on]
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
Simple mixer control 'Channel Mode',0
  Capabilities: enum
  Items: '2ch' '4ch' '6ch'
  Item0: '6ch'
Simple mixer control 'DAC Clock Source',0
  Capabilities: enum
  Items: 'AC-Link' 'SPDIF-In' 'Both'
  Item0: 'AC-Link'
Simple mixer control 'External Amplifier',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Input Source Select',0
  Capabilities: enum
  Items: 'Input1' 'Input2'
  Item0: 'Input1'
Simple mixer control 'Input Source Select',1
  Capabilities: enum
  Items: 'Input1' 'Input2'
  Item0: 'Input1'


!!Alsactl output
!!-------------

--startcollapse--
state.V8237 {
	control.1 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Master Playback Switch'
		value false
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
		value.0 20
		value.1 20
	}
	control.3 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Center Playback Switch'
		value false
	}
	control.4 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 31'
		comment.dbmin -4650
		comment.dbmax 0
		iface MIXER
		name 'Center Playback Volume'
		value 20
	}
	control.5 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'LFE Playback Switch'
		value false
	}
	control.6 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 31'
		comment.dbmin -4650
		comment.dbmax 0
		iface MIXER
		name 'LFE Playback Volume'
		value 20
	}
	control.7 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Surround Playback Switch'
		value.0 false
		value.1 false
	}
	control.8 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Beep Playback Switch'
		value false
	}
	control.9 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 15'
		comment.dbmin -4500
		comment.dbmax 0
		iface MIXER
		name 'Beep Playback Volume'
		value 9
	}
	control.10 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Mic Playback Switch'
		value false
	}
	control.11 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Mic Playback Volume'
		value.0 19
		value.1 19
	}
	control.12 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Mic Boost (+20dB)'
		value false
	}
	control.13 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Line Playback Switch'
		value true
	}
	control.14 {
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
	control.15 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'CD Playback Switch'
		value true
	}
	control.16 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'CD Playback Volume'
		value.0 25
		value.1 25
	}
	control.17 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Aux Playback Switch'
		value false
	}
	control.18 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Aux Playback Volume'
		value.0 22
		value.1 22
	}
	control.19 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'PCM Playback Switch'
		value false
	}
	control.20 {
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
	control.21 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Capture Switch'
		value true
	}
	control.22 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 15'
		comment.dbmin 0
		comment.dbmax 2250
		iface MIXER
		name 'Capture Volume'
		value.0 10
		value.1 10
	}
	control.23 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Mix
		comment.item.1 Mic
		iface MIXER
		name 'Mono Output Select'
		value Mix
	}
	control.24 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Mic1
		comment.item.1 Mic2
		iface MIXER
		name 'Mic Select'
		value Mic1
	}
	control.25 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Con Mask'
		value '0fff000f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.26 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		value cf00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
	}
	control.27 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Default'
		value '0082000200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.28 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Switch'
		value true
	}
	control.29 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 3'
		iface MIXER
		name 'IEC958 Playback AC97-SPSA'
		value 1
	}
	control.30 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 AC-Link
		comment.item.1 ADC
		comment.item.2 SPDIF-In
		iface MIXER
		name 'IEC958 Playback Source'
		value AC-Link
	}
	control.31 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Capture Valid Switch'
		value false
	}
	control.32 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Capture Monitor'
		value false
	}
	control.33 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Capture Switch'
		value true
	}
	control.34 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 AC-Link
		comment.item.1 SPDIF-In
		comment.item.2 Both
		iface MIXER
		name 'DAC Clock Source'
		value AC-Link
	}
	control.35 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Shared
		comment.item.1 Independent
		iface MIXER
		name 'Surround Jack Mode'
		value Independent
	}
	control.36 {
		comment.access 'read write locked'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 '2ch'
		comment.item.1 '4ch'
		comment.item.2 '6ch'
		iface MIXER
		name 'Channel Mode'
		value '6ch'
	}
	control.37 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'External Amplifier'
		value true
	}
	control.38 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Input1
		comment.item.1 Input2
		iface MIXER
		name 'Input Source Select'
		value Input1
	}
	control.39 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Input1
		comment.item.1 Input2
		iface MIXER
		name 'Input Source Select'
		index 1
		value Input1
	}
	control.40 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Output Switch'
		value false
	}
	control.41 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -4650
		comment.dbmax 0
		iface MIXER
		name 'PCM Playback Volume'
		value.0 31
		value.1 31
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
nvidia
binfmt_misc
ipt_REJECT
ipt_LOG
xt_limit
xt_tcpudp
ipt_addrtype
xt_state
snd_via82xx
ip6table_filter
gameport
ip6_tables
snd_ac97_codec
ac97_bus
nf_nat_irc
nf_conntrack_irc
snd_pcm
nf_nat_ftp
nf_nat
snd_page_alloc
snd_mpu401_uart
snd_seq_midi
nf_conntrack_ipv4
nf_defrag_ipv4
nf_conntrack_ftp
snd_rawmidi
nf_conntrack
snd_seq_midi_event
snd_seq
iptable_filter
ip_tables
snd_timer
x_tables
snd_seq_device
ppdev
snd
via_agp
psmouse
parport_pc
serio_raw
shpchp
i2c_viapro
soundcore
agpgart
lp
parport
via_rhine
pata_via
floppy
sata_via
mii


!!ALSA/HDA dmesg
!!------------------



```

---

### Post by alvinmoneypit on 2010-12-12
lidex,

I uploaded is as you said and here is the link

[http://www.alsa-project.org/db/?f=944e83b04f8cb33ef7e8db93eae82224d7a42f4a]("http://www.alsa-project.org/db/?f=944e83b04f8cb33ef7e8db93eae82224d7a42f4a")

---

### Post by cavalier911 on 2010-12-13
Your Master and PCM mixer controls are MUTED.

Whats in **bold** should say [on].

```
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 20 [65%] [-16.50dB] **[off]**
  Front Right: Playback 20 [65%] [-16.50dB] **[off]**
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] **[off]**
  Front Right: Playback 31 [100%] [0.00dB] **[off]**
Simple mixer control 'Surround',0
  Capabilities: pswitch penum
```

Open a terminal:

```
amixer -q set Master unmute
```

```
amixer -q set PCM unmute
```

Try your sound now.
If sound still doesn't work unmute every Playback control listed on the alsa information script under Mixer controls for card 0 [V8237] that indicates [off]

---

### Post by alvinmoneypit on 2010-12-14
cavalier,

I "unmuted" per your request.  Still no sound.  I checked some setting and see I have no input devices.

---

### Post by lidex on 2010-12-14
Looks like you're using latest release alsa. And your problem began when you upgraded? First you should check for a bios update.
What do you get for this:
```
sudo dmidecode -t bios
sudo dmidecode -t baseboard

```
For your panel applet try this. Make sure these are installed:
```
sudo apt-get install --reinstall gnome-media gnome-media-common indicator-applet indicator-applet-session indicator-me indicator-session indicator-complete indicator-sound
```
Now reset your panels:
```
gconftool-2 --recursive-unset  /apps/panel
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```
Next right-click on your panel and select 'Add to panel' and add back items that are missing. Indicator applet I believe should have volume control, but you may need to play around as there are three indicator entries in my add list. You may want to search synaptic for 'applet' to find any that are not in the list as they have to be installed to appear there.
You'll want to remove old pulse config as well.
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Logout/in.**

---

### Post by alvinmoneypit on 2010-12-14
Hello lidex,

I'm not sure if it started immediately after uninstalling/installing.  This is a new drive, not an upgraded Ubuntu.  Never had anything on it except 10.10.

I upgraded the BIOS many moons ago on this board, but it looks by the date this system is not seeing the upgrade.  I had it running a 2005 BIOS Ver. 1.07 - looks like this one is a 2001.  I recently looked for a BIOS update beforee installing Ubuntu on this drive, I wanted to have the latest BIOS since I was putting in this new system.  Turns out SOYO is out of business.  I found the ver. I mentioned as the latest one and I had it already on here.  I think I found one that claimed to be newer, but I wasn't sure of the source so I didn't download it, and because many other sites had my ver. as the latest.
Let me make sure everyone understands that I've never run the onboard audio until now with this system - I had a soundblaster in here since beginning with this board. 

 I had a lot of trouble making it work correctly (the soundblaster Audigy 2ZS) so under XP I entered a lot of solutions and stuff from the VIA site (drivers, windows packages, etc.  I did eventually get it working full 5.1  But that was a different hard drive. That hard drive is still in there but not hooked to the MB- both of these drives and my DVD burner are SATA and I only have 2 connections on my MB so I switch drive cables back and forth.

  The onboard audio works on XP albeit I only have 4 of my 6 channels (the front speakers didn't work, everything else does - it may be a physical problem with the board connectors or the board itself as I just recently tried this audio system on this old board I'm using. When I first loaded Ubuntu onto this new drive, I had 4 of my 6 channels working (exactly as the other drive with XP), so I was using solutions from the thread I mentioned to try and get my front channels working and one of them lost my speaker icon and all sound. 

Here is the results of the first command:
```
# dmidecode 2.9
SMBIOS 2.3 present.

Handle 0x0000, DMI type 0, 20 bytes
BIOS Information
	Vendor: American Megatrends Inc.
	Version: Version 07.00T
	Release Date: 04/02/01
	Address: 0xF0000
	Runtime Size: 64 kB
	ROM Size: 256 kB
	Characteristics:
		ISA is supported
		PCI is supported
		PNP is supported
		APM is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		ESCD support is available
		Boot from CD is supported
		Selectable boot is supported
		BIOS ROM is socketed
		EDD is supported
		5.25"/360 KB floppy services are supported (int 13h)
		5.25"/1.2 MB floppy services are supported (int 13h)
		3.5"/720 KB floppy services are supported (int 13h)
		3.5"/2.88 MB floppy services are supported (int 13h)
		Print screen service is supported (int 5h)
		8042 keyboard services are supported (int 9h)
		Printer services are supported (int 17h)
		CGA/mono video services are supported (int 10h)
		ACPI is supported
		USB legacy is supported
		AGP is supported
		LS-120 boot is supported
		ATAPI Zip drive boot is supported
		BIOS boot specification is supported

Handle 0x0014, DMI type 13, 22 bytes
BIOS Language Information
	Installable Languages: 4
		English
		Traditional Chinese
		Simplified Chinese
		Japanese
	Currently Installed Language: English
```


There's a problem with that terminal command:
> sudo apt-get install --reinstall gnome-media gnome-media-common indicator-applet indicator-applet-session indicator-me indicator-session indicator-complete indicator-sound

This yields:

> E: Unable to locate package indicator-complete


Could not find/remove old pulse config:

> rm: cannot remove `/etc/asound.conf': No such file or directory


---

### Post by alvinmoneypit on 2010-12-14
I tried refreshing the panel before - it only puts up another 'envelope' icon.

It looks like I'm running 2AA4 AMI BIOS from 1/28/2005

---

### Post by lidex on 2010-12-14
Looks like indicator-complete was deprecated and the asound.conf is only there if you created it. Did the other packages re-install?
Did you reset the panel?

---

### Post by alvinmoneypit on 2010-12-14
looks like the only errors I had was the ones I mentioned.  It looks like it unpacked the others.

Yes, I did the panel but the indicator applet only brings up the envelope icon.

I've looked in synaptic before for the speaker but so much stuff comes up, I had no idea what to choose.

---

### Post by lidex on 2010-12-14
If you go into system monitor, what do you see. Mine below.

---

### Post by alvinmoneypit on 2010-12-14
Sorry,

I don't have "system monitor" or I don't know how to start it.

---

### Post by Miwca on 2010-12-14
Hi I hope you dont mind I highjack this thread alittle since I'm having a very simulair problem. I have an asus 1005P Eee-PC wich has worked great in the 10.10 release, even though I've never had problem with audio earlier until now. I have used this computer at work and at home to play spotify, movies when I go to bed etc. Two days ago I rebooted it and now it cant load any driver or module. I didnt update ubuntu until afterwards so I cant really understand what I've done wrong.

I did wget -O alsa-info.sh [http://alsa-project.org/alsa-info.sh](http://alsa-project.org/alsa-info.sh) && bash ./alsa-info.sh yesterday wich turned out:
[http://www.alsa-project.org/db/?f=0f608044632b7e5fbdd81ab1673fb930447c1ca1](http://www.alsa-project.org/db/?f=0f608044632b7e5fbdd81ab1673fb930447c1ca1)

as you can see the driver version and loaded alsa modules are emty, even though my netbook still finds my sound card with:
lspci -v | less

I have followed this guide that I googled, but it doesnt really say how to fix it just howto find the problem.
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

I hope you dont mind I highjack this thread alittle.
/Mica

---

### Post by lidex on 2010-12-16
@alvinmoneypit
'Applications > System > Administration > System Monitor'
or in a terminal or Alt+F2 launcher:
```
gnome-system-monitor
```
or install with:
```
sudo apt-get install gnome-system-monitor
```


@Miwca
Try re-installing alsa.
Using a Terminal="Applications->Accessories->Terminal"
```
sudo apt-get update
sudo apt-get upgrade
```
```
sudo apt-get purge linux-sound-base alsa-base alsa-utils

```
```
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop

```
**Reboot.**
**gdm and ubuntu-desktop usually get taken out in the process, so we add them back**

---

### Post by Sworddragon on 2010-12-16
The problem sounds like mine so I'm posting here too. I have posted a week ago my problem on launchpad with some updates because I was thinking this is a bug in a package.

I have already made a detailed description [here]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/688196"). Maybe somebody have an idea how to solve this problem.

---

### Post by lidex on 2010-12-16
@Sworddragon
So it worked previously in natty, then not, after an update, correct? What is the make/model of the computer in question?

Post these outputs please:
```
sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
```
```
dmesg | grep -C1 -E 'ALSA|HDA|HDMI|sound|hda.codec|hda.intel'
```

---

### Post by alvinmoneypit on 2010-12-17
Lidex,

Hello.  "What do I see?"  I don't see alsa anywhere.  I don't see ' indicator - sound'

---

### Post by Sworddragon on 2010-12-17
> **lidex said:**
> @Sworddragon
So it worked previously in natty, then not, after an update, correct?

This is correct. My computer was running for ~4 days and after a restart the sound was going away. The shutdown (and so the later restart) was forced because the stream was going away for a few milliseconds. But as I said in launchpad the sound is still working with Knoppix so that there is no hardware defect.

> **lidex said:**
> What is the make/model of the computer in question?
I'm now loged in with ssh but I think it was a HP Pavilion t3546.de. But some components has changed a little. The nforce4 board was broken some time ago and the computer has now a nforce6 board.

> **lidex said:**
> ```
sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
```
The filenames /dev/dsp*and /dev/seq* don't exist.

> **lidex said:**
> ```
dmesg | grep -C1 -E 'ALSA|HDA|HDMI|sound|hda.codec|hda.intel'
```

> [   15.421547] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 22
[   15.421554] HDA Intel 0000:00:05.0: PCI INT B -> Link[LAZA] -> GSI 22 (level, low) -> IRQ 22
[   15.421558] hda_intel: Disable MSI for Nvidia chipset
[   15.421619] HDA Intel 0000:00:05.0: setting latency timer to 64
[   15.933646] eth0: link up.

---

### Post by lidex on 2010-12-17
@Sworddragon
You're missing the relevant portion of the fuser output. Example:
```
Specified filename /dev/dsp* does not exist.
Specified filename /dev/seq* does not exist.
                     USER        PID ACCESS COMMAND
/dev/snd/controlC0:  lidex      1568 F.... pulseaudio
/dev/snd/controlC1:  lidex      1568 F.... pulseaudio

```

Let's look at this also:
```
pkill pulseaudio; sleep 2; pulseaudio -vv
```

Might as well go here also since the board is not stock:
```
sudo dmidecode -t bios
sudo dmidecode -t baseboard

```

---

### Post by Sworddragon on 2010-12-17
> **lidex said:**
> @Sworddragon
You're missing the relevant portion of the fuser output. Example:
```
Specified filename /dev/dsp* does not exist.
Specified filename /dev/seq* does not exist.
                     USER        PID ACCESS COMMAND
/dev/snd/controlC0:  lidex      1568 F.... pulseaudio
/dev/snd/controlC1:  lidex      1568 F.... pulseaudio

```

There is no more output:

```
sworddragon@ubuntu:~$ sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
Angegebener Dateiname /dev/dsp* existiert nicht.
Angegebener Dateiname /dev/seq* existiert nicht.
sworddragon@ubuntu:~$
```It's german but it says just that the files not exist.

> **lidex said:**
> Let's look at this also:
```
pkill pulseaudio; sleep 2; pulseaudio -vv
```

pulseaudio was not installed (my sound worked weeks ago without the package pulseaudio). After I installed it I got the following output:

```
sworddragon@ubuntu:~$ pkill pulseaudio; sleep 2; pulseaudio -vv
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) fehlgeschlagen: Operation not permitted
I: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) fehlgeschlagen: Operation not permitted
D: core-rtclock.c: Timer slack is set to 50 us.
I: core-util.c: Failed to acquire high-priority scheduling: No such file or directory
I: main.c: Dies ist PulseAudio 0.9.21-63-gd3efa-dirty
D: main.c: Kompilier-Host: x86_64-pc-linux-gnu
D: main.c: Kompilier-CFLAGS: -g -O2 -g -Wall -O3 -Wall -W -Wextra -pipe -Wno-long-long -Winline -Wvla -Wno-overlength-strings -Wunsafe-loop-optimizations -Wundef -Wformat=2 -Wlogical-op -Wsign-compare -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wold-style-definition -Wpointer-arith -Winit-self -Wdeclaration-after-statement -Wfloat-equal -Wmissing-prototypes -Wstrict-prototypes -Wredundant-decls -Wmissing-declarations -Wmissing-noreturn -Wshadow -Wendif-labels -Wcast-align -Wstrict-aliasing=2 -Wwrite-strings -Wno-unused-parameter -ffast-math -Wp,-D_FORTIFY_SOURCE=2 -fno-common -fdiagnostics-show-option
D: main.c: Laufe auf Host: Linux x86_64 2.6.35-23-generic #41-Ubuntu SMP Wed Nov 24 11:55:36 UTC 2010
D: main.c: 2 CPUs gefunden.
I: main.c: Seitengröße ist 4096 Bytes.
D: main.c: Kompiliere mit Valgrind-Unterstützung: nein
D: main.c: Läuft im Valgrind-Modus: no
D: main.c: Running in VM: no
D: main.c: Optimiertes Build: ja
D: main.c: Alle Ansprüche aktiviert.
I: main.c: System- ID ist 277ed7ab8de41962bd7a5b54000006f1.
I: main.c: System- ID ist 277ed7ab8de41962bd7a5b54000006f1-1292631838.220955-346475731.
I: main.c: Nutze Laufzeit-Verzeichnis /home/sworddragon/.pulse/277ed7ab8de41962bd7a5b54000006f1-runtime.
I: main.c: Nutze Zustands-Verzeichnis /home/sworddragon/.pulse.
I: main.c: Modul-Verzeichnis /usr/lib/pulse-0.9.21/modules benutzen.
I: main.c: Laufe im System-Modus: no
I: main.c: Neue hochauslösende Timer verfügbar! Guten Appetit!
I: cpu-x86.c: CPU flags: CMOV MMX SSE SSE2 SSE3 MMXEXT 3DNOW 3DNOWEXT 
I: svolume_mmx.c: Initialising MMX optimized functions.
I: remap_mmx.c: Initialising MMX optimized remappers.
I: svolume_sse.c: Initialising SSE2 optimized functions.
I: remap_sse.c: Initialising SSE2 optimized remappers.
I: sconv_sse.c: Initialising SSE2 optimized conversions.
D: memblock.c: Using shared memory pool with 1024 slots of size 64,0 KB each, total size is 64,0 MB, maximum usable slot size is 65472
D: database-tdb.c: Opened TDB database '/home/sworddragon/.pulse/277ed7ab8de41962bd7a5b54000006f1-device-volumes.tdb'
I: module-device-restore.c: Sucessfully opened database file '/home/sworddragon/.pulse/277ed7ab8de41962bd7a5b54000006f1-device-volumes'.
I: module.c: Loaded "module-device-restore" (index: #0; argument: "").
D: database-tdb.c: Opened TDB database '/home/sworddragon/.pulse/277ed7ab8de41962bd7a5b54000006f1-stream-volumes.tdb'
I: module-stream-restore.c: Sucessfully opened database file '/home/sworddragon/.pulse/277ed7ab8de41962bd7a5b54000006f1-stream-volumes'.
I: module.c: Loaded "module-stream-restore" (index: #1; argument: "").
D: database-tdb.c: Opened TDB database '/home/sworddragon/.pulse/277ed7ab8de41962bd7a5b54000006f1-card-database.tdb'
I: module-card-restore.c: Sucessfully opened database file '/home/sworddragon/.pulse/277ed7ab8de41962bd7a5b54000006f1-card-database'.
I: module.c: Loaded "module-card-restore" (index: #2; argument: "").
I: module.c: Loaded "module-augment-properties" (index: #3; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9.21/modules/module-udev-detect.so': success
D: module-udev-detect.c: /dev/snd/controlC0 is accessible: yes
D: module-udev-detect.c: /devices/pci0000:00/0000:00:05.0/sound/card0 is busy: no
D: module-udev-detect.c: Loading module-alsa-card with arguments 'device_id="0" name="pci-0000_00_05.0" card_name="alsa_card.pci-0000_00_05.0" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1"'
D: dbus-util.c: Successfully connected to D-Bus session bus 2741eb2c967d91873dd186f80000002b as :1.8
D: reserve-wrap.c: Successfully acquired reservation lock on device 'Audio0'
D: alsa-mixer.c: Looking at profile output:analog-mono
D: alsa-mixer.c: Checking for playback on Analog Mono (analog-mono)
D: alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying plug:hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying plug:hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:analog-mono+input:analog-mono
D: alsa-mixer.c: Checking for playback on Analog Mono (analog-mono)
D: alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying plug:hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying plug:hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:analog-mono+input:analog-stereo
D: alsa-mixer.c: Checking for playback on Analog Mono (analog-mono)
D: alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying plug:hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying plug:hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:analog-mono+input:iec958-stereo
D: alsa-mixer.c: Checking for playback on Analog Mono (analog-mono)
D: alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying plug:hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying plug:hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:analog-mono+input:iec958-surround-40
D: alsa-mixer.c: Checking for playback on Analog Mono (analog-mono)
D: alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying plug:hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying plug:hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:analog-stereo
D: alsa-mixer.c: Checking for playback on Analog Stereo (analog-stereo)
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open front:0
D: alsa-util.c: Maximum hw buffer size is 23777 ms
D: alsa-util.c: Set buffer size first (to 3528 samples), period size second (to 441 samples).
D: alsa-mixer.c: Profile output:analog-stereo supported.
D: alsa-mixer.c: Looking at profile output:analog-stereo+input:analog-mono
D: alsa-mixer.c: Checking for recording on Analog Mono (analog-mono)
D: alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying plug:hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying plug:hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:analog-stereo+input:analog-stereo
D: alsa-mixer.c: Checking for recording on Analog Stereo (analog-stereo)
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open front:0
D: alsa-util.c: Maximum hw buffer size is 23777 ms
D: alsa-util.c: Set buffer size first (to 3528 samples), period size second (to 441 samples).
D: alsa-mixer.c: Profile output:analog-stereo+input:analog-stereo supported.
D: alsa-mixer.c: Looking at profile output:analog-stereo+input:iec958-stereo
D: alsa-mixer.c: Checking for recording on Digital Stereo (IEC958) (iec958-stereo)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D1c' failed (-2)
I: alsa-util.c: Error opening PCM device iec958:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:analog-stereo+input:iec958-surround-40
D: alsa-mixer.c: Checking for recording on Digital Surround 4.0 (IEC958) (iec958-surround-40)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D1c' failed (-2)
I: alsa-util.c: Error opening PCM device iec958:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:analog-surround-40
D: alsa-mixer.c: Checking for playback on Analog Surround 4.0 (analog-surround-40)
D: alsa-util.c: Trying surround40:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround40:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: alsa-util.c: Trying surround40:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround40:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: alsa-util.c: Trying plug:surround40:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround40:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: alsa-util.c: Trying plug:surround40:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround40:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround40:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:analog-surround-40+input:analog-mono
D: alsa-mixer.c: Checking for playback on Analog Surround 4.0 (analog-surround-40)
D: alsa-util.c: Trying surround40:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround40:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: alsa-util.c: Trying surround40:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround40:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: alsa-util.c: Trying plug:surround40:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround40:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: alsa-util.c: Trying plug:surround40:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround40:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround40:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:analog-surround-40+input:analog-stereo
D: alsa-mixer.c: Checking for playback on Analog Surround 4.0 (analog-surround-40)
D: alsa-util.c: Trying surround40:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround40:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: alsa-util.c: Trying surround40:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround40:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: alsa-util.c: Trying plug:surround40:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround40:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: alsa-util.c: Trying plug:surround40:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround40:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround40:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:analog-surround-40+input:iec958-stereo
D: alsa-mixer.c: Checking for playback on Analog Surround 4.0 (analog-surround-40)
D: alsa-util.c: Trying surround40:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround40:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: alsa-util.c: Trying surround40:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround40:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: alsa-util.c: Trying plug:surround40:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround40:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: alsa-util.c: Trying plug:surround40:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround40:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround40:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:analog-surround-40+input:iec958-surround-40
D: alsa-mixer.c: Checking for playback on Analog Surround 4.0 (analog-surround-40)
D: alsa-util.c: Trying surround40:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround40:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: alsa-util.c: Trying surround40:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround40:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: alsa-util.c: Trying plug:surround40:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround40:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: alsa-util.c: Trying plug:surround40:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround40:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround40:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:analog-surround-41
D: alsa-mixer.c: Checking for playback on Analog Surround 4.1 (analog-surround-41)
D: alsa-util.c: Trying surround41:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround41:0
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying surround41:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround41:0
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying plug:surround41:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround41:0
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying plug:surround41:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround41:0
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround41:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:analog-surround-41+input:analog-mono
D: alsa-mixer.c: Checking for playback on Analog Surround 4.1 (analog-surround-41)
D: alsa-util.c: Trying surround41:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround41:0
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying surround41:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround41:0
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying plug:surround41:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround41:0
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying plug:surround41:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround41:0
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround41:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:analog-surround-41+input:analog-stereo
D: alsa-mixer.c: Checking for playback on Analog Surround 4.1 (analog-surround-41)
D: alsa-util.c: Trying surround41:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround41:0
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying surround41:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround41:0
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying plug:surround41:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround41:0
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying plug:surround41:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround41:0
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround41:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:analog-surround-41+input:iec958-stereo
D: alsa-mixer.c: Checking for playback on Analog Surround 4.1 (analog-surround-41)
D: alsa-util.c: Trying surround41:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround41:0
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying surround41:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround41:0
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying plug:surround41:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround41:0
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying plug:surround41:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround41:0
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround41:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:analog-surround-41+input:iec958-surround-40
D: alsa-mixer.c: Checking for playback on Analog Surround 4.1 (analog-surround-41)
D: alsa-util.c: Trying surround41:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround41:0
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying surround41:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround41:0
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying plug:surround41:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround41:0
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying plug:surround41:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround41:0
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround41:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:analog-surround-50
D: alsa-mixer.c: Checking for playback on Analog Surround 5.0 (analog-surround-50)
D: alsa-util.c: Trying surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround50:0
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying surround50:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround50:0
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying plug:surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround50:0
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying plug:surround50:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround50:0
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround50:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:analog-surround-50+input:analog-mono
D: alsa-mixer.c: Checking for playback on Analog Surround 5.0 (analog-surround-50)
D: alsa-util.c: Trying surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround50:0
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying surround50:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround50:0
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying plug:surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround50:0
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying plug:surround50:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround50:0
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround50:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:analog-surround-50+input:analog-stereo
D: alsa-mixer.c: Checking for playback on Analog Surround 5.0 (analog-surround-50)
D: alsa-util.c: Trying surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround50:0
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying surround50:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround50:0
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying plug:surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround50:0
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying plug:surround50:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround50:0
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround50:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:analog-surround-50+input:iec958-stereo
D: alsa-mixer.c: Checking for playback on Analog Surround 5.0 (analog-surround-50)
D: alsa-util.c: Trying surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround50:0
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying surround50:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround50:0
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying plug:surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround50:0
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying plug:surround50:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround50:0
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround50:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:analog-surround-50+input:iec958-surround-40
D: alsa-mixer.c: Checking for playback on Analog Surround 5.0 (analog-surround-50)
D: alsa-util.c: Trying surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround50:0
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying surround50:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround50:0
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying plug:surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround50:0
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying plug:surround50:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround50:0
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround50:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:analog-surround-51
D: alsa-mixer.c: Checking for playback on Analog Surround 5.1 (analog-surround-51)
D: alsa-util.c: Trying surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround51:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Invalid argument
D: alsa-util.c: Trying surround51:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround51:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Invalid argument
D: alsa-util.c: Trying plug:surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround51:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Invalid argument
D: alsa-util.c: Trying plug:surround51:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround51:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround51:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:analog-surround-51+input:analog-mono
D: alsa-mixer.c: Checking for playback on Analog Surround 5.1 (analog-surround-51)
D: alsa-util.c: Trying surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround51:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Invalid argument
D: alsa-util.c: Trying surround51:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround51:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Invalid argument
D: alsa-util.c: Trying plug:surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround51:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Invalid argument
D: alsa-util.c: Trying plug:surround51:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround51:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround51:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:analog-surround-51+input:analog-stereo
D: alsa-mixer.c: Checking for playback on Analog Surround 5.1 (analog-surround-51)
D: alsa-util.c: Trying surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround51:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Invalid argument
D: alsa-util.c: Trying surround51:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround51:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Invalid argument
D: alsa-util.c: Trying plug:surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround51:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Invalid argument
D: alsa-util.c: Trying plug:surround51:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround51:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround51:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:analog-surround-51+input:iec958-stereo
D: alsa-mixer.c: Checking for playback on Analog Surround 5.1 (analog-surround-51)
D: alsa-util.c: Trying surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround51:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Invalid argument
D: alsa-util.c: Trying surround51:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround51:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Invalid argument
D: alsa-util.c: Trying plug:surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround51:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Invalid argument
D: alsa-util.c: Trying plug:surround51:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround51:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround51:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:analog-surround-51+input:iec958-surround-40
D: alsa-mixer.c: Checking for playback on Analog Surround 5.1 (analog-surround-51)
D: alsa-util.c: Trying surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround51:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Invalid argument
D: alsa-util.c: Trying surround51:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround51:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Invalid argument
D: alsa-util.c: Trying plug:surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround51:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Invalid argument
D: alsa-util.c: Trying plug:surround51:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround51:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround51:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:analog-surround-71
D: alsa-mixer.c: Checking for playback on Analog Surround 7.1 (analog-surround-71)
D: alsa-util.c: Trying surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround71:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Invalid argument
D: alsa-util.c: Trying surround71:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround71:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Invalid argument
D: alsa-util.c: Trying plug:surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround71:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Invalid argument
D: alsa-util.c: Trying plug:surround71:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround71:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround71:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:analog-surround-71+input:analog-mono
D: alsa-mixer.c: Checking for playback on Analog Surround 7.1 (analog-surround-71)
D: alsa-util.c: Trying surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround71:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Invalid argument
D: alsa-util.c: Trying surround71:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround71:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Invalid argument
D: alsa-util.c: Trying plug:surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround71:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Invalid argument
D: alsa-util.c: Trying plug:surround71:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround71:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround71:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:analog-surround-71+input:analog-stereo
D: alsa-mixer.c: Checking for playback on Analog Surround 7.1 (analog-surround-71)
D: alsa-util.c: Trying surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround71:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Invalid argument
D: alsa-util.c: Trying surround71:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround71:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Invalid argument
D: alsa-util.c: Trying plug:surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround71:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Invalid argument
D: alsa-util.c: Trying plug:surround71:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround71:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround71:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:analog-surround-71+input:iec958-stereo
D: alsa-mixer.c: Checking for playback on Analog Surround 7.1 (analog-surround-71)
D: alsa-util.c: Trying surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround71:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Invalid argument
D: alsa-util.c: Trying surround71:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround71:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Invalid argument
D: alsa-util.c: Trying plug:surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround71:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Invalid argument
D: alsa-util.c: Trying plug:surround71:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround71:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround71:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:analog-surround-71+input:iec958-surround-40
D: alsa-mixer.c: Checking for playback on Analog Surround 7.1 (analog-surround-71)
D: alsa-util.c: Trying surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround71:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Invalid argument
D: alsa-util.c: Trying surround71:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround71:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Invalid argument
D: alsa-util.c: Trying plug:surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround71:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Invalid argument
D: alsa-util.c: Trying plug:surround71:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround71:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround71:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:iec958-stereo
D: alsa-mixer.c: Checking for playback on Digital Stereo (IEC958) (iec958-stereo)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D1p' failed (-2)
I: alsa-util.c: Error opening PCM device iec958:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:iec958-stereo+input:analog-mono
D: alsa-mixer.c: Checking for playback on Digital Stereo (IEC958) (iec958-stereo)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D1p' failed (-2)
I: alsa-util.c: Error opening PCM device iec958:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:iec958-stereo+input:analog-stereo
D: alsa-mixer.c: Checking for playback on Digital Stereo (IEC958) (iec958-stereo)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D1p' failed (-2)
I: alsa-util.c: Error opening PCM device iec958:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:iec958-stereo+input:iec958-stereo
D: alsa-mixer.c: Checking for playback on Digital Stereo (IEC958) (iec958-stereo)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D1p' failed (-2)
I: alsa-util.c: Error opening PCM device iec958:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:iec958-stereo+input:iec958-surround-40
D: alsa-mixer.c: Checking for playback on Digital Stereo (IEC958) (iec958-stereo)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D1p' failed (-2)
I: alsa-util.c: Error opening PCM device iec958:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:iec958-surround-40
D: alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958) (iec958-surround-40)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D1p' failed (-2)
I: alsa-util.c: Error opening PCM device iec958:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:iec958-surround-40+input:analog-mono
D: alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958) (iec958-surround-40)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D1p' failed (-2)
I: alsa-util.c: Error opening PCM device iec958:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:iec958-surround-40+input:analog-stereo
D: alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958) (iec958-surround-40)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D1p' failed (-2)
I: alsa-util.c: Error opening PCM device iec958:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:iec958-surround-40+input:iec958-stereo
D: alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958) (iec958-surround-40)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D1p' failed (-2)
I: alsa-util.c: Error opening PCM device iec958:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:iec958-surround-40+input:iec958-surround-40
D: alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958) (iec958-surround-40)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D1p' failed (-2)
I: alsa-util.c: Error opening PCM device iec958:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:iec958-ac3-surround-40
D: alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958/AC3) (iec958-ac3-surround-40)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:iec958-ac3-surround-40+input:analog-mono
D: alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958/AC3) (iec958-ac3-surround-40)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:iec958-ac3-surround-40+input:analog-stereo
D: alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958/AC3) (iec958-ac3-surround-40)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:iec958-ac3-surround-40+input:iec958-stereo
D: alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958/AC3) (iec958-ac3-surround-40)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:iec958-ac3-surround-40+input:iec958-surround-40
D: alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958/AC3) (iec958-ac3-surround-40)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:iec958-ac3-surround-51
D: alsa-mixer.c: Checking for playback on Digital Surround 5.1 (IEC958/AC3) (iec958-ac3-surround-51)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:iec958-ac3-surround-51+input:analog-mono
D: alsa-mixer.c: Checking for playback on Digital Surround 5.1 (IEC958/AC3) (iec958-ac3-surround-51)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:iec958-ac3-surround-51+input:analog-stereo
D: alsa-mixer.c: Checking for playback on Digital Surround 5.1 (IEC958/AC3) (iec958-ac3-surround-51)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:iec958-ac3-surround-51+input:iec958-stereo
D: alsa-mixer.c: Checking for playback on Digital Surround 5.1 (IEC958/AC3) (iec958-ac3-surround-51)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:iec958-ac3-surround-51+input:iec958-surround-40
D: alsa-mixer.c: Checking for playback on Digital Surround 5.1 (IEC958/AC3) (iec958-ac3-surround-51)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:hdmi-stereo
D: alsa-mixer.c: Checking for playback on Digital Stereo (HDMI) (hdmi-stereo)
D: alsa-util.c: Trying hdmi:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D3p' failed (-2)
I: alsa-util.c: Error opening PCM device hdmi:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:hdmi-stereo+input:analog-mono
D: alsa-mixer.c: Checking for playback on Digital Stereo (HDMI) (hdmi-stereo)
D: alsa-util.c: Trying hdmi:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D3p' failed (-2)
I: alsa-util.c: Error opening PCM device hdmi:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:hdmi-stereo+input:analog-stereo
D: alsa-mixer.c: Checking for playback on Digital Stereo (HDMI) (hdmi-stereo)
D: alsa-util.c: Trying hdmi:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D3p' failed (-2)
I: alsa-util.c: Error opening PCM device hdmi:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:hdmi-stereo+input:iec958-stereo
D: alsa-mixer.c: Checking for playback on Digital Stereo (HDMI) (hdmi-stereo)
D: alsa-util.c: Trying hdmi:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D3p' failed (-2)
I: alsa-util.c: Error opening PCM device hdmi:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:hdmi-stereo+input:iec958-surround-40
D: alsa-mixer.c: Checking for playback on Digital Stereo (HDMI) (hdmi-stereo)
D: alsa-util.c: Trying hdmi:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D3p' failed (-2)
I: alsa-util.c: Error opening PCM device hdmi:0: No such file or directory
D: alsa-mixer.c: Looking at profile input:analog-mono
D: alsa-mixer.c: Checking for recording on Analog Mono (analog-mono)
D: alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying plug:hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying plug:hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Invalid argument
D: alsa-mixer.c: Looking at profile input:analog-stereo
D: alsa-mixer.c: Checking for recording on Analog Stereo (analog-stereo)
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open front:0
D: alsa-util.c: Maximum hw buffer size is 23777 ms
D: alsa-util.c: Set buffer size first (to 3528 samples), period size second (to 441 samples).
D: alsa-mixer.c: Profile input:analog-stereo supported.
D: alsa-mixer.c: Looking at profile input:iec958-stereo
D: alsa-mixer.c: Checking for recording on Digital Stereo (IEC958) (iec958-stereo)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D1c' failed (-2)
I: alsa-util.c: Error opening PCM device iec958:0: No such file or directory
D: alsa-mixer.c: Looking at profile input:iec958-surround-40
D: alsa-mixer.c: Checking for recording on Digital Surround 4.0 (IEC958) (iec958-surround-40)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D1c' failed (-2)
I: alsa-util.c: Error opening PCM device iec958:0: No such file or directory
I: card.c: Created 0 "alsa_card.pci-0000_00_05.0"
D: reserve-wrap.c: Successfully create reservation lock monitor for device 'Audio0'
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open front:0
D: alsa-util.c: Maximum hw buffer size is 23777 ms
D: alsa-util.c: Set buffer size first (to 88200 samples), period size second (to 88200 samples).
I: alsa-sink.c: Successfully opened device front:0.
I: alsa-sink.c: Selected mapping 'Analog Stereo' (analog-stereo).
I: alsa-sink.c: Successfully enabled mmap() mode.
I: alsa-sink.c: Successfully enabled timer-based scheduling mode.
I: (alsa-lib)control.c: Invalid CTL front:0
I: alsa-mixer.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-mixer.c: Successfully attached to mixer 'hw:0'
D: alsa-mixer.c: Probing path 'analog-output'
D: alsa-mixer.c: Probing path 'analog-output-speaker'
D: alsa-mixer.c: Probe of element 'Speaker' failed.
D: alsa-mixer.c: Probing path 'analog-output-speaker'
D: alsa-mixer.c: Probe of element 'Desktop Speaker' failed.
D: alsa-mixer.c: Probing path 'analog-output-headphones'
D: alsa-mixer.c: Probing path 'analog-output-headphones'
D: alsa-mixer.c: Probe of element 'Headphone2' failed.
D: alsa-mixer.c: Probing path 'analog-output-mono'
D: alsa-mixer.c: Probe of element 'Master Mono' failed.
D: alsa-mixer.c: Probing path 'analog-output-lfe-on-mono'
D: alsa-mixer.c: Probe of element 'Master Mono' failed.
D: alsa-sink.c: Probed mixer paths:
D: alsa-mixer.c: Path Set 0xe68fc0, direction=1, probed=yes
D: alsa-mixer.c: Path analog-output (Analog Output), direction=1, priority=99, probed=yes, supported=yes, has_mute=yes, has_volume=yes, has_dB=yes, min_volume=0, max_volume=31, min_dB=-148,5, max_dB=12
D: alsa-mixer.c: Element Master Front, direction=1, switch=1, volume=1, enumeration=0, required=0, required_absent=0, mask=0x4028000000000006, n_channels=2, override_map=yes
D: alsa-mixer.c: Element Headphone, direction=1, switch=1, volume=3, enumeration=0, required=0, required_absent=0, mask=0x6, n_channels=2, override_map=no
D: alsa-mixer.c: Element Front, direction=1, switch=1, volume=1, enumeration=0, required=0, required_absent=0, mask=0x6, n_channels=2, override_map=yes
D: alsa-mixer.c: Element PCM, direction=1, switch=0, volume=1, enumeration=0, required=0, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
D: alsa-mixer.c: Path analog-output-headphones (Analog Headphones), direction=1, priority=90, probed=yes, supported=yes, has_mute=yes, has_volume=yes, has_dB=yes, min_volume=0, max_volume=31, min_dB=-148,5, max_dB=12
D: alsa-mixer.c: Element Master Front, direction=1, switch=1, volume=1, enumeration=0, required=0, required_absent=0, mask=0x4028000000000006, n_channels=2, override_map=yes
D: alsa-mixer.c: Element Headphone, direction=1, switch=1, volume=1, enumeration=0, required=4, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
D: alsa-mixer.c: Element Front, direction=1, switch=2, volume=2, enumeration=0, required=0, required_absent=0, mask=0x6, n_channels=2, override_map=no
D: alsa-mixer.c: Element PCM, direction=1, switch=0, volume=1, enumeration=0, required=0, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
D: alsa-mixer.c: Added 2 ports
I: sink.c: Created sink 0 "alsa_output.pci-0000_00_05.0.analog-stereo" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: sink.c:     alsa.resolution_bits = "16"
I: sink.c:     device.api = "alsa"
I: sink.c:     device.class = "sound"
I: sink.c:     alsa.class = "generic"
I: sink.c:     alsa.subclass = "generic-mix"
I: sink.c:     alsa.name = "VT1708S Analog"
I: sink.c:     alsa.id = "VT1708S Analog"
I: sink.c:     alsa.subdevice = "0"
I: sink.c:     alsa.subdevice_name = "subdevice #0"
I: sink.c:     alsa.device = "0"
I: sink.c:     alsa.card = "0"
I: sink.c:     alsa.card_name = "HDA NVidia"
I: sink.c:     alsa.long_card_name = "HDA NVidia at 0xf7ff8000 irq 23"
I: sink.c:     alsa.driver_name = "snd_hda_intel"
I: sink.c:     device.bus_path = "pci-0000:00:05.0"
I: sink.c:     sysfs.path = "/devices/pci0000:00/0000:00:05.0/sound/card0"
I: sink.c:     device.bus = "pci"
I: sink.c:     device.vendor.id = "10de"
I: sink.c:     device.product.id = "03f0"
I: sink.c:     device.form_factor = "internal"
I: sink.c:     device.string = "front:0"
I: sink.c:     device.buffering.buffer_size = "352768"
I: sink.c:     device.buffering.fragment_size = "176384"
I: sink.c:     device.access_mode = "mmap+timer"
I: sink.c:     device.profile.name = "analog-stereo"
I: sink.c:     device.profile.description = "Analog Stereo"
I: sink.c:     device.description = "Internes Audio Analog Stereo"
I: sink.c:     alsa.mixer_name = "VIA VT1708S"
I: sink.c:     alsa.components = "HDA:11060397,18490397,00100000"
I: sink.c:     module-udev-detect.discovered = "1"
I: sink.c:     device.icon_name = "audio-card-pci"
D: core-subscribe.c: Dropped redundant event due to change event.
I: source.c: Created source 0 "alsa_output.pci-0000_00_05.0.analog-stereo.monitor" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: source.c:     device.description = "Monitor of Internes Audio Analog Stereo"
I: source.c:     device.class = "monitor"
I: source.c:     alsa.card = "0"
I: source.c:     alsa.card_name = "HDA NVidia"
I: source.c:     alsa.long_card_name = "HDA NVidia at 0xf7ff8000 irq 23"
I: source.c:     alsa.driver_name = "snd_hda_intel"
I: source.c:     device.bus_path = "pci-0000:00:05.0"
I: source.c:     sysfs.path = "/devices/pci0000:00/0000:00:05.0/sound/card0"
I: source.c:     device.bus = "pci"
I: source.c:     device.vendor.id = "10de"
I: source.c:     device.product.id = "03f0"
I: source.c:     device.form_factor = "internal"
I: source.c:     device.string = "0"
I: source.c:     module-udev-detect.discovered = "1"
I: source.c:     device.icon_name = "audio-card-pci"
I: alsa-sink.c: Using 2,0 fragments of size 176384 bytes (999,91ms), buffer size is 352768 bytes (1999,82ms)
I: alsa-sink.c: Time scheduling watermark is 20,00ms
D: alsa-sink.c: hwbuf_unused=0
D: alsa-sink.c: setting avail_min=87310
D: alsa-mixer.c: Activating path analog-output
D: alsa-mixer.c: Path analog-output (Analog Output), direction=1, priority=99, probed=yes, supported=yes, has_mute=yes, has_volume=yes, has_dB=yes, min_volume=0, max_volume=31, min_dB=-148,5, max_dB=12
D: alsa-mixer.c: Element Master Front, direction=1, switch=1, volume=1, enumeration=0, required=0, required_absent=0, mask=0x4028000000000006, n_channels=2, override_map=yes
D: alsa-mixer.c: Element Headphone, direction=1, switch=1, volume=3, enumeration=0, required=0, required_absent=0, mask=0x6, n_channels=2, override_map=no
D: alsa-mixer.c: Element Front, direction=1, switch=1, volume=1, enumeration=0, required=0, required_absent=0, mask=0x6, n_channels=2, override_map=yes
D: alsa-mixer.c: Element PCM, direction=1, switch=0, volume=1, enumeration=0, required=0, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
I: alsa-sink.c: Hardware volume ranges from -148,50 dB to 12,00 dB.
I: alsa-sink.c: Fixing base volume to -12,00 dB
I: alsa-sink.c: Using hardware volume control. Hardware dB scale supported.
I: alsa-sink.c: Using hardware mute control.
D: alsa-util.c: snd_pcm_dump():
D: alsa-util.c: Soft volume PCM
D: alsa-util.c: Control: PCM Playback Volume
D: alsa-util.c: min_dB: -51
D: alsa-util.c: max_dB: 0
D: alsa-util.c: resolution: 256
D: alsa-util.c: Its setup is:
D: alsa-util.c:   stream       : PLAYBACK
D: alsa-util.c:   access       : MMAP_INTERLEAVED
D: alsa-util.c:   format       : S16_LE
D: alsa-util.c:   subformat    : STD
D: alsa-util.c:   channels     : 2
D: alsa-util.c:   rate         : 44100
D: alsa-util.c:   exact rate   : 44100 (44100/1)
D: alsa-util.c:   msbits       : 16
D: alsa-util.c:   buffer_size  : 88192
D: alsa-util.c:   period_size  : 44096
D: alsa-util.c:   period_time  : 999909
D: alsa-util.c:   tstamp_mode  : ENABLE
D: alsa-util.c:   period_step  : 1
D: alsa-util.c:   avail_min    : 87310
D: alsa-util.c:   period_event : 0
D: alsa-util.c:   start_threshold  : -1
D: alsa-util.c:   stop_threshold   : 6205960286516543488
D: alsa-util.c:   silence_threshold: 0
D: alsa-util.c:   silence_size : 0
D: alsa-util.c:   boundary     : 6205960286516543488
D: alsa-util.c: Slave: Hardware PCM card 0 'HDA NVidia' device 0 subdevice 0
D: alsa-util.c: Its setup is:
D: alsa-util.c:   stream       : PLAYBACK
D: alsa-util.c:   access       : MMAP_INTERLEAVED
D: alsa-util.c:   format       : S16_LE
D: alsa-util.c:   subformat    : STD
D: alsa-util.c:   channels     : 2
D: alsa-util.c:   rate         : 44100
D: alsa-util.c:   exact rate   : 44100 (44100/1)
D: alsa-util.c:   msbits       : 16
D: alsa-util.c:   buffer_size  : 88192
D: alsa-util.c:   period_size  : 44096
D: alsa-util.c:   period_time  : 999909
D: alsa-util.c:   tstamp_mode  : ENABLE
D: alsa-util.c:   period_step  : 1
D: alsa-util.c:   avail_min    : 87310
D: alsa-util.c:   period_event : 0
D: alsa-util.c:   start_threshold  : -1
D: alsa-util.c:   stop_threshold   : 6205960286516543488
D: alsa-util.c:   silence_threshold: 0
D: alsa-util.c:   silence_size : 0
D: alsa-util.c:   boundary     : 6205960286516543488
D: alsa-util.c:   appl_ptr     : 0
D: alsa-util.c:   hw_ptr       : 0
D: alsa-sink.c: Read hardware volume: 0:  28% 1:  28%
D: alsa-sink.c: Thread starting up
I: core-util.c: Successfully enabled SCHED_RR scheduling for thread, with priority 4, which is lower than the requested 5.
I: alsa-sink.c: Starting playback.
D: alsa-sink.c: Cutting sleep time for the initial iterations by half.
D: alsa-sink.c: Cutting sleep time for the initial iterations by half.
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open front:0
D: alsa-util.c: Maximum hw buffer size is 23777 ms
D: alsa-util.c: Set buffer size first (to 88200 samples), period size second (to 88200 samples).
I: alsa-source.c: Successfully opened device front:0.
I: alsa-source.c: Selected mapping 'Analog Stereo' (analog-stereo).
I: alsa-source.c: Successfully enabled mmap() mode.
I: alsa-source.c: Successfully enabled timer-based scheduling mode.
I: (alsa-lib)control.c: Invalid CTL front:0
I: alsa-mixer.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-mixer.c: Successfully attached to mixer 'hw:0'
D: alsa-mixer.c: Probing path 'analog-input'
D: alsa-mixer.c: Probing path 'analog-input-microphone'
D: alsa-mixer.c: Probe of element 'Mic' failed.
D: alsa-mixer.c: Probing path 'analog-input-linein'
D: alsa-mixer.c: Probe of element 'Line' failed.
D: alsa-mixer.c: Probing path 'analog-input'
D: alsa-mixer.c: Probe of element 'Aux' failed.
D: alsa-mixer.c: Probing path 'analog-input-video'
D: alsa-mixer.c: Probe of element 'Video' failed.
D: alsa-mixer.c: Probing path 'analog-input-video'
D: alsa-mixer.c: Probe of element 'TV Tuner' failed.
D: alsa-mixer.c: Probing path 'analog-input-radio'
D: alsa-mixer.c: Probe of element 'FM' failed.
D: alsa-mixer.c: Probing path 'analog-input'
D: alsa-mixer.c: Probe of element 'Mic/Line' failed.
D: alsa-source.c: Probed mixer paths:
D: alsa-mixer.c: Path Set 0xe87bf0, direction=2, probed=yes
D: alsa-mixer.c: Path analog-input (Analog Input), direction=2, priority=100, probed=yes, supported=yes, has_mute=yes, has_volume=yes, has_dB=yes, min_volume=0, max_volume=31, min_dB=-16,5, max_dB=60,75
D: alsa-mixer.c: Element Capture, direction=2, switch=1, volume=1, enumeration=0, required=2, required_absent=0, mask=0x403f600000000f66, n_channels=2, override_map=yes
D: alsa-mixer.c: Element Input Source, direction=2, switch=0, volume=0, enumeration=1, required=0, required_absent=0, mask=0x0, n_channels=0, override_map=no
D: alsa-mixer.c: Option Mic (input-microphone-1/Microphone 1) index=1, priority=20
D: alsa-mixer.c: Option Front Mic (input-microphone-2/Microphone 2) index=2, priority=19
D: alsa-mixer.c: Option Line (input-linein/Line-In) index=3, priority=18
D: alsa-mixer.c: Element Mic Boost, direction=2, switch=0, volume=1, enumeration=0, required=0, required_absent=0, mask=0x403ec00000000006, n_channels=2, override_map=no
D: alsa-mixer.c: Setting input-microphone-1 (Microphone 1) priority=20
D: alsa-mixer.c: Setting input-microphone-2 (Microphone 2) priority=19
D: alsa-mixer.c: Setting input-linein (Line-In) priority=18
D: alsa-mixer.c: Added 3 ports
D: core-subscribe.c: Dropped redundant event due to change event.
I: source.c: Created source 1 "alsa_input.pci-0000_00_05.0.analog-stereo" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: source.c:     alsa.resolution_bits = "16"
I: source.c:     device.api = "alsa"
I: source.c:     device.class = "sound"
I: source.c:     alsa.class = "generic"
I: source.c:     alsa.subclass = "generic-mix"
I: source.c:     alsa.name = "VT1708S Analog"
I: source.c:     alsa.id = "VT1708S Analog"
I: source.c:     alsa.subdevice = "0"
I: source.c:     alsa.subdevice_name = "subdevice #0"
I: source.c:     alsa.device = "0"
I: source.c:     alsa.card = "0"
I: source.c:     alsa.card_name = "HDA NVidia"
I: source.c:     alsa.long_card_name = "HDA NVidia at 0xf7ff8000 irq 23"
I: source.c:     alsa.driver_name = "snd_hda_intel"
I: source.c:     device.bus_path = "pci-0000:00:05.0"
I: source.c:     sysfs.path = "/devices/pci0000:00/0000:00:05.0/sound/card0"
I: source.c:     device.bus = "pci"
I: source.c:     device.vendor.id = "10de"
I: source.c:     device.product.id = "03f0"
I: source.c:     device.form_factor = "internal"
I: source.c:     device.string = "front:0"
I: source.c:     device.buffering.buffer_size = "352768"
I: source.c:     device.buffering.fragment_size = "176384"
I: source.c:     device.access_mode = "mmap+timer"
I: source.c:     device.profile.name = "analog-stereo"
I: source.c:     device.profile.description = "Analog Stereo"
I: source.c:     device.description = "Internes Audio Analog Stereo"
I: source.c:     alsa.mixer_name = "VIA VT1708S"
I: source.c:     alsa.components = "HDA:11060397,18490397,00100000"
I: source.c:     module-udev-detect.discovered = "1"
I: source.c:     device.icon_name = "audio-card-pci"
I: alsa-source.c: Using 2,0 fragments of size 176384 bytes (999,91ms), buffer size is 352768 bytes (1999,82ms)
I: alsa-source.c: Time scheduling watermark is 20,00ms
D: alsa-source.c: hwbuf_unused=0
D: alsa-source.c: setting avail_min=87310
D: alsa-mixer.c: Activating path analog-input
D: alsa-mixer.c: Path analog-input (Analog Input), direction=2, priority=100, probed=yes, supported=yes, has_mute=yes, has_volume=yes, has_dB=yes, min_volume=0, max_volume=31, min_dB=-16,5, max_dB=60,75
D: alsa-mixer.c: Element Capture, direction=2, switch=1, volume=1, enumeration=0, required=2, required_absent=0, mask=0x403f600000000f66, n_channels=2, override_map=yes
D: alsa-mixer.c: Element Input Source, direction=2, switch=0, volume=0, enumeration=1, required=0, required_absent=0, mask=0x0, n_channels=0, override_map=no
D: alsa-mixer.c: Option Mic (input-microphone-1/Microphone 1) index=1, priority=20
D: alsa-mixer.c: Option Front Mic (input-microphone-2/Microphone 2) index=2, priority=19
D: alsa-mixer.c: Option Line (input-linein/Line-In) index=3, priority=18
D: alsa-mixer.c: Element Mic Boost, direction=2, switch=0, volume=1, enumeration=0, required=0, required_absent=0, mask=0x403ec00000000006, n_channels=2, override_map=no
D: alsa-mixer.c: Setting input-microphone-1 (Microphone 1) priority=20
D: alsa-mixer.c: Setting input-microphone-2 (Microphone 2) priority=19
D: alsa-mixer.c: Setting input-linein (Line-In) priority=18
I: alsa-source.c: Hardware volume ranges from -16,50 dB to 60,75 dB.
I: alsa-source.c: Fixing base volume to -60,75 dB
I: alsa-source.c: Using hardware volume control. Hardware dB scale supported.
I: alsa-source.c: Using hardware mute control.
D: alsa-util.c: snd_pcm_dump():
D: alsa-util.c: Soft volume PCM
D: alsa-util.c: Control: PCM Playback Volume
D: alsa-util.c: min_dB: -51
D: alsa-util.c: max_dB: 0
D: alsa-util.c: resolution: 256
D: alsa-util.c: Its setup is:
D: alsa-util.c:   stream       : CAPTURE
D: alsa-util.c:   access       : MMAP_INTERLEAVED
D: alsa-util.c:   format       : S16_LE
D: alsa-util.c:   subformat    : STD
D: alsa-util.c:   channels     : 2
D: alsa-util.c:   rate         : 44100
D: alsa-util.c:   exact rate   : 44100 (44100/1)
D: alsa-util.c:   msbits       : 16
D: alsa-util.c:   buffer_size  : 88192
D: alsa-util.c:   period_size  : 44096
D: alsa-util.c:   period_time  : 999909
D: alsa-util.c:   tstamp_mode  : ENABLE
D: alsa-util.c:   period_step  : 1
D: alsa-util.c:   avail_min    : 87310
D: alsa-util.c:   period_event : 0
D: alsa-util.c:   start_threshold  : -1
D: alsa-util.c:   stop_threshold   : 6205960286516543488
D: alsa-util.c:   silence_threshold: 0
D: alsa-util.c:   silence_size : 0
D: alsa-util.c:   boundary     : 6205960286516543488
D: alsa-util.c: Slave: Hardware PCM card 0 'HDA NVidia' device 0 subdevice 0
D: alsa-util.c: Its setup is:
D: alsa-util.c:   stream       : CAPTURE
D: alsa-util.c:   access       : MMAP_INTERLEAVED
D: alsa-util.c:   format       : S16_LE
D: alsa-util.c:   subformat    : STD
D: alsa-util.c:   channels     : 2
D: alsa-util.c:   rate         : 44100
D: alsa-util.c:   exact rate   : 44100 (44100/1)
D: alsa-util.c:   msbits       : 16
D: alsa-util.c:   buffer_size  : 88192
D: alsa-util.c:   period_size  : 44096
D: alsa-util.c:   period_time  : 999909
D: alsa-util.c:   tstamp_mode  : ENABLE
D: alsa-util.c:   period_step  : 1
D: alsa-util.c:   avail_min    : 87310
D: alsa-util.c:   period_event : 0
D: alsa-util.c:   start_threshold  : -1
D: alsa-util.c:   stop_threshold   : 6205960286516543488
D: alsa-util.c:   silence_threshold: 0
D: alsa-util.c:   silence_size : 0
D: alsa-util.c:   boundary     : 6205960286516543488
D: alsa-util.c:   appl_ptr     : 0
D: alsa-util.c:   hw_ptr       : 0
D: alsa-source.c: Read hardware volume: 0:  15% 1:  15%
D: alsa-source.c: Thread starting up
I: core-util.c: Successfully enabled SCHED_RR scheduling for thread, with priority 4, which is lower than the requested 5.
I: alsa-source.c: Starting capture.
I: module.c: Loaded "module-alsa-card" (index: #4; argument: "device_id="0" name="pci-0000_00_05.0" card_name="alsa_card.pci-0000_00_05.0" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1"").
I: module-udev-detect.c: Card /devices/pci0000:00/0000:00:05.0/sound/card0 (alsa_card.pci-0000_00_05.0) module loaded.
I: module-udev-detect.c: Found 1 cards.
I: module.c: Loaded "module-udev-detect" (index: #5; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9.21/modules/module-bluetooth-discover.so': failure
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9.21/modules/module-esound-protocol-unix.so': failure
I: module.c: Loaded "module-native-protocol-unix" (index: #6; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9.21/modules/module-gconf.so': failure
D: core-subscribe.c: Dropped redundant event due to change event.
I: module-default-device-restore.c: Restored default sink 'alsa_output.pci-0000_00_05.0.analog-stereo'.
D: core-subscribe.c: Dropped redundant event due to change event.
I: module-default-device-restore.c: Restored default source 'alsa_input.pci-0000_00_05.0.analog-stereo'.
I: module.c: Loaded "module-default-device-restore" (index: #7; argument: "").
I: module.c: Loaded "module-rescue-streams" (index: #8; argument: "").
I: module.c: Loaded "module-always-sink" (index: #9; argument: "").
I: module.c: Loaded "module-intended-roles" (index: #10; argument: "").
D: module-suspend-on-idle.c: Sink alsa_output.pci-0000_00_05.0.analog-stereo becomes idle, timeout in 5 seconds.
D: module-suspend-on-idle.c: Source alsa_input.pci-0000_00_05.0.analog-stereo becomes idle, timeout in 5 seconds.
I: module.c: Loaded "module-suspend-on-idle" (index: #11; argument: "").
D: dbus-util.c: Successfully connected to D-Bus system bus a33199c3257ec809e362cc5100000010 as :1.20
I: client.c: Created 0 "ConsoleKit Session /org/freedesktop/ConsoleKit/Session1"
D: module-console-kit.c: Added new session /org/freedesktop/ConsoleKit/Session1
I: module.c: Loaded "module-console-kit" (index: #12; argument: "").
I: module.c: Loaded "module-position-event-sounds" (index: #13; argument: "").
D: main.c: Got org.pulseaudio.Server!
I: main.c: Start des Daemons abgeschlossen.
D: module-console-kit.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
D: module-udev-detect.c: /dev/snd/controlC0 is accessible: yes
E: alsa-util.c: snd_pcm_avail_delay() returned strange values: delay 0 is less than avail 38.
E: alsa-util.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
E: alsa-util.c: snd_pcm_dump():
E: alsa-util.c: Soft volume PCM
E: alsa-util.c: Control: PCM Playback Volume
E: alsa-util.c: min_dB: -51
E: alsa-util.c: max_dB: 0
E: alsa-util.c: resolution: 256
E: alsa-util.c: Its setup is:
E: alsa-util.c:   stream       : CAPTURE
E: alsa-util.c:   access       : MMAP_INTERLEAVED
E: alsa-util.c:   format       : S16_LE
E: alsa-util.c:   subformat    : STD
E: alsa-util.c:   channels     : 2
E: alsa-util.c:   rate         : 44100
E: alsa-util.c:   exact rate   : 44100 (44100/1)
E: alsa-util.c:   msbits       : 16
E: alsa-util.c:   buffer_size  : 88192
E: alsa-util.c:   period_size  : 44096
E: alsa-util.c:   period_time  : 999909
E: alsa-util.c:   tstamp_mode  : ENABLE
E: alsa-util.c:   period_step  : 1
E: alsa-util.c:   avail_min    : 87310
E: alsa-util.c:   period_event : 0
E: alsa-util.c:   start_threshold  : -1
E: alsa-util.c:   stop_threshold   : 6205960286516543488
E: alsa-util.c:   silence_threshold: 0
E: alsa-util.c:   silence_size : 0
E: alsa-util.c:   boundary     : 6205960286516543488
E: alsa-util.c: Slave: Hardware PCM card 0 'HDA NVidia' device 0 subdevice 0
E: alsa-util.c: Its setup is:
E: alsa-util.c:   stream       : CAPTURE
E: alsa-util.c:   access       : MMAP_INTERLEAVED
E: alsa-util.c:   format       : S16_LE
E: alsa-util.c:   subformat    : STD
E: alsa-util.c:   channels     : 2
E: alsa-util.c:   rate         : 44100
E: alsa-util.c:   exact rate   : 44100 (44100/1)
E: alsa-util.c:   msbits       : 16
E: alsa-util.c:   buffer_size  : 88192
E: alsa-util.c:   period_size  : 44096
E: alsa-util.c:   period_time  : 999909
E: alsa-util.c:   tstamp_mode  : ENABLE
E: alsa-util.c:   period_step  : 1
E: alsa-util.c:   avail_min    : 87310
E: alsa-util.c:   period_event : 0
E: alsa-util.c:   start_threshold  : -1
E: alsa-util.c:   stop_threshold   : 6205960286516543488
E: alsa-util.c:   silence_threshold: 0
E: alsa-util.c:   silence_size : 0
E: alsa-util.c:   boundary     : 6205960286516543488
E: alsa-util.c:   appl_ptr     : 87376
E: alsa-util.c:   hw_ptr       : 87376
I: module-suspend-on-idle.c: Source alsa_input.pci-0000_00_05.0.analog-stereo idle for too long, suspending ...
D: source.c: Suspend cause of source alsa_input.pci-0000_00_05.0.analog-stereo is 0x0004, suspending
I: alsa-source.c: Device suspended...
I: module-suspend-on-idle.c: Sink alsa_output.pci-0000_00_05.0.analog-stereo idle for too long, suspending ...
D: sink.c: Suspend cause of sink alsa_output.pci-0000_00_05.0.analog-stereo is 0x0004, suspending
I: alsa-sink.c: Device suspended...
D: reserve-wrap.c: Device lock status of reserve-monitor-wrapper@Audio0 changed: not busy
D: module-udev-detect.c: /dev/snd/controlC0 is accessible: yes

```The command wasn't finished at this time but it haven't made anything more. Some of the last lines was warnings with a red color (the "E: alsa-util.c:" lines).

> **lidex said:**
> Might as well go here also since the board is not stock:
```
sudo dmidecode -t bios
sudo dmidecode -t baseboard

```

dmidecode wasn't installed too but I installed it now.

```
sworddragon@ubuntu:~$ sudo dmidecode -t bios
# dmidecode 2.9
SMBIOS 2.4 present.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
    Vendor: American Megatrends Inc.
    Version: P2.10
    Release Date: 04/21/2010
    Address: 0xF0000
    Runtime Size: 64 kB
    ROM Size: 512 kB
    Characteristics:
        PCI is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        Boot from CD is supported
        Selectable boot is supported
        BIOS ROM is socketed
        EDD is supported
        5.25"/1.2 MB floppy services are supported (int 13h)
        3.5"/720 KB floppy services are supported (int 13h)
        3.5"/2.88 MB floppy services are supported (int 13h)
        Print screen service is supported (int 5h)
        8042 keyboard services are supported (int 9h)
        Serial services are supported (int 14h)
        Printer services are supported (int 17h)
        CGA/mono video services are supported (int 10h)
        ACPI is supported
        USB legacy is supported
        LS-120 boot is supported
        ATAPI Zip drive boot is supported
        BIOS boot specification is supported
        Function key-initiated network boot is supported
        Targeted content distribution is supported
    BIOS Revision: 8.14
``````
sworddragon@ubuntu:~$ sudo dmidecode -t baseboard
# dmidecode 2.9
SMBIOS 2.4 present.

Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
    Manufacturer: ASRock
    Product Name: N68-S
    Version:                       
    Serial Number:                       
    Asset Tag:                       
    Features:
        Board is a hosting board
        Board is replaceable
    Location In Chassis:                       
    Chassis Handle: 0x0003
    Type: Motherboard
    Contained Object Handles: 0
```

---

### Post by alvinmoneypit on 2010-12-18
I flashed my BIOS the old fashioned way with the floppy disk (I'm glad I went to the online antique store years ago and bot a couple floppy drives).  Still no sound, but my XP drive is working as before.  

On my ALsa mixer my 'surround' scale is set a 00  and has no scaling like the  outputs on my other system - how do I change that?

---

### Post by Miwca on 2010-12-19
Ty so much. I've been trying to do what I just did manually without apt-get to get it working without success but this worked great. Thank you

---

### Post by lidex on 2010-12-20
> **alvinmoneypit said:**
> I flashed my BIOS the old fashioned way with the floppy disk (I'm glad I went to the online antique store years ago and bot a couple floppy drives).  Still no sound, but my XP drive is working as before.  

On my ALsa mixer my 'surround' scale is set a 00  and has no scaling like the  outputs on my other system - how do I change that?

Use pulseaudio volume control ...I think. Are you using ubuntu or lubuntu?

---

### Post by Sworddragon on 2010-12-20
I made a look at [this](https://wiki.ubuntu.com/PulseAudio) page and installed PulseAudio and created the asound.conf. After a restart and starting an application as root I still here no sound. All bars in the volume control of PulseAudio are set to 100% and the PulseAudio Volume Meter is increasing both signal bars if I play a sound file.

---

### Post by alvinmoneypit on 2010-12-21
Lidex,

I'm running Ubuntu 10.10

Applications > Sound & Video > Pulse volume control shows 6 channels on.


But Alsa mixer in terminal shows many channels truncated.
```
&#9474; Card: VIA 8237                                                                                     F1:  Help               &#9474;
&#9474; Chip: C-Media Electronics CMI9761A+                                                                F2:  System information &#9474;
&#9474; View: F3:[Playback] F4: Capture  F5: All                                                           F6:  Select sound card  &#9474;
&#9474; Item: LFE [dB gain: -16.50]                                                                        Esc: Exit               &#9474;
&#9474;                                                                                                                            &#9474;
&#9474;                                                                                                                            &#9474;
&#9474;                                                                                                                            &#9474;
&#9474;                                                                                                                            &#9474;
&#9474;                                                                                                                            &#9474;
&#9474;      &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;                       &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;                                          &#9474;
&#9474;      &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;                       &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;                                          &#9474;
&#9474;      &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;                       &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;                                          &#9474;
&#9474;      &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;                       &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;                                          &#9474;
&#9474;      &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;                       &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;                                          >
&#9474;      &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;                       &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;                                          >
&#9474;      &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;                       &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;                                          >
&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                       &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                                          >
&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                       &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                                          >
&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                       &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                                          >
&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                       &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                                          >
&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                       &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                                          >
&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                       &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                                          >
&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                       &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                                          >
&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                       &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                                          >
&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                       &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                                          &#9474;
&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                       &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                                          &#9474;
&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                       &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                                          &#9474;
&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                       &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                                          &#9474;
&#9474;      &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;     &#9484;&#9472;&#9472;&#9488;   Independ   &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;     &#9484;&#9472;&#9472;&#9488;     Mic1     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;      &#9474;
&#9474;      &#9474;OO&#9474;     &#9474;OO&#9474;     &#9474;OO&#9474;              &#9474;OO&#9474;     &#9474;OO&#9474;     &#9474;OO&#9474;     &#9474;OO&#9474;     &#9474;MM&#9474;     &#9474;MM&#9474;              &#9474;OO&#9474;     &#9474;MM&#9474;      &#9474;
&#9474;      &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;              &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;              &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;      &#9474;
&#9474;     65<>65  100<>100                      65       65    100<>100  81<>81   61<>61                                         &#9474;
&#9474;     Master    PCM    Surround Surround  Center <  LFE   >  Line      CD      Mic    Mic Boos Mic Sele  S/PDIF  S/PDIF C    &#9474;
&#9474;                                                                                                                            &#9474;
&#9474;                                                                                                                            &#9474;
&#9474;                                                                                                                            &#9474;
&#9474;                                                                                                                            &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;

```

---

### Post by Sworddragon on 2010-12-22
I upgraded yesterday back to natty but the sound was not working. I made today over ssh a few preperations for a backup and decided to install Ubuntu complete new. On the ssh session I made a last few things that I wanted to try before the new installation of Ubuntu. I removed the asound.conf, purged alsa-utils and linux-sound-base, installed them again and called dpkg-reconfigure --linux-sound base and choosed ALSA and at the last I generated with alsactl restore a new asound.state as I did so many times before.

As I got home and made a restart I heard sound. I have undo then all steps and removed pulseaudio and the other things I configured during the tests. I have even disabled dbus and other things that I don't need because I want a very minimalistic system. After a reboot the sound is still working. I don't exactly know which steps of them solved the problem. Maybe it was even one of the new packages in the last ~24 hours.

---

### Post by alvinmoneypit on 2010-12-27
I put in a soundblaster 5.1 live card.  Rebooted, now I have 2.0 sound at least (maybe more only have a 2 speaker system here).  Looks like what I have missing now is my speaker icon only.

---

