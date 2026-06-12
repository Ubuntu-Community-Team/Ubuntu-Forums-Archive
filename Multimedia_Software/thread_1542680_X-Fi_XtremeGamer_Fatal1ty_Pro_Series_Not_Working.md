---
title: "X-Fi XtremeGamer Fatal1ty Pro Series Not Working"
date: 2010-07-30
forum: Multimedia Software
---

### Post by CypherSTL on 2010-07-30
Ubuntu 10.04 64-bit AMD64 with ALSA 1.0.23

Alright.  I have the "**                     X-Fi XtremeGamer Fatal1ty Pro Series**" Sound Card and I cannot for the life me get this working.

From looking at `lspci` the card is installed, and the module is loaded in to the kernel.
```

00:0c.0 Multimedia audio controller: Creative Labs SB X-Fi
    Subsystem: Creative Labs Device 002c
    Flags: medium devsel, IRQ 17
    I/O ports at ec00 [size=32]
    Memory at fea00000 (64-bit, non-prefetchable) [size=2M]
    Memory at f8000000 (64-bit, non-prefetchable) [size=64M]
    Capabilities: <access denied>
    Kernel modules: snd-ctxfi

``````

patrick@Cerebellum:~$ lsmod | grep snd
snd_hda_codec_atihdmi     3023  1 
snd_hda_intel          25677  0 
snd_usb_audio          92747  1 
snd_ctxfi             100843  0 
snd_hda_codec          85759  2 snd_hda_codec_atihdmi,snd_hda_intel
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87882  5 snd_hda_intel,snd_usb_audio,snd_ctxfi,snd_hda_codec,snd_pcm_oss
snd_usb_lib            19193  1 snd_usb_audio
snd_seq_dummy           1782  0 
snd_seq_oss            31219  0 
snd_seq_midi            5829  0 
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23649  2 snd_pcm,snd_seq
snd_rawmidi            23420  2 snd_usb_lib,snd_seq_midi
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
snd_hwdep               6924  2 snd_usb_audio,snd_hda_codec
snd                    71106  15 snd_hda_intel,snd_usb_audio,snd_ctxfi,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_seq,snd_timer,snd_rawmidi,snd_seq_device,snd_hwdep
soundcore               8052  1 snd
snd_page_alloc          8500  3 snd_hda_intel,snd_ctxfi,snd_pcm

```[B]ALSA Sound Cards Present:
[/B]```

patrick@Cerebellum:~$ cat /proc/asound/cards
 0 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xf66ec000 irq 17
 1 [U0x93a0x2621   ]: USB-Audio - USB Device 0x93a:0x2621
                      USB Device 0x93a:0x2621 at usb-0000:00:10.1-1, full speed

```Any ideas?  Been trying to figure this out all day.  So far, this is the only thing stopping me from replacing Windows with Ubuntu.

---

### Post by CypherSTL on 2010-07-31
Alright.  I did some more digging here.

I booted up into the Ubuntu 10.04 x86 LiveCD, and my sound works.  So, it seems like this is only an issue with the x86_64 release of Ubuntu.

**lnspci from LiveCD** (32bit)
```

00:0c.0 Multimedia audio controller: Creative Labs SB X-Fi
    Subsystem: Creative Labs Device 002c
    Flags: bus master, medium devsel, latency 64, IRQ 17
    I/O ports at ec00 [size=32]
    Memory at fea00000 (64-bit, non-prefetchable) [size=2M]
    Memory at f8000000 (64-bit, non-prefetchable) [size=64M]
    Capabilities: <access denied>
    Kernel driver in use: SB-XFi
    Kernel modules: snd-ctxfi

```**From LiveCD** (32bit)
```

ubuntu@ubuntu:~$ cat /proc/asound/cards
 0 [XFi            ]: SB-XFi - Creative X-Fi
                      Creative X-Fi 20K1 Unknown
 1 [U0x93a0x2621   ]: USB-Audio - USB Device 0x93a:0x2621
                      USB Device 0x93a:0x2621 at usb-0000:00:10.1-1, full speed
 2 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xf66ec000 irq 17

```So now I'm just trying to find some insight on getting this working on 64-bit.

---

### Post by CypherSTL on 2010-08-02
Anyone have any ideas?

---

### Post by CypherSTL on 2010-08-08
Bump.  Still haven't gotten any further on this.

---

### Post by v1ad on 2010-08-08
it should be an alsa driver, and once you boot in x64 try opening up the sound panel and changing the input and output devices.

---

### Post by CypherSTL on 2010-08-08
> **v1ad said:**
> it should be an alsa driver, and once you boot in x64 try opening up the sound panel and changing the input and output devices.
The only devices that appear in the sound panel in x64 is the webcam, and my video cards HDMI port.  The X-Fi isn't listed.

---

### Post by v1ad on 2010-08-08
wheee search ftw.

[http://ubuntuforums.org/showthread.php?p=8401010](http://ubuntuforums.org/showthread.php?p=8401010)

[http://www.google.com/search?sourceid=chrome&ie=UTF-8&q=snd-ctxfi](http://www.google.com/search?sourceid=chrome&ie=UTF-8&q=snd-ctxfi)

---

### Post by CypherSTL on 2010-08-10
If searching for a week actually helped me out, I wouldn't have posted here.  I know how to friggin search.

---

### Post by Arpagiator on 2010-08-10
Hmm.. kind of wierd. My XFi-Xtreme Gamer works correctly under 10.04x64. Don't see any reason why your's wouldn't. Though, hopefully this will help in some way...

```
05:02.0 Multimedia audio controller: Creative Labs SB X-Fi
    Subsystem: Creative Labs Device 0031
    Flags: bus master, medium devsel, latency 64, IRQ 18
    I/O ports at ec00 [size=32]
    Memory at fea00000 (64-bit, non-prefetchable) [size=2M]
    Memory at f8000000 (64-bit, non-prefetchable) [size=64M]
    Capabilities: <access denied>
    Kernel driver in use: SB-XFi
    Kernel modules: snd-ctxfi
``````
arpagiator@MusicBox:~$ lsmod | grep snd
snd_usb_audio          92747  0 
snd_usb_lib            19193  1 snd_usb_audio
snd_hwdep               6924  1 snd_usb_audio
snd_ctxfi             100843  5 
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87882  5 snd_usb_audio,snd_ctxfi,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31219  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  10 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23649  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    71106  21 snd_usb_audio,snd_hwdep,snd_ctxfi,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_ctxfi,snd_pcm

```

```
arpagiator@MusicBox:~$ cat /proc/asound/cards
 0 [XFi            ]: SB-XFi - Creative X-Fi
                      Creative X-Fi 20K1 SB073x
```

I'm a complete noob in codes, but maybe you (or another) can see a difference that will help.

---

### Post by simosx on 2010-08-10
Again, you should both produce the alsa-info.sh output, then compared them.

---

### Post by Arpagiator on 2010-08-11
> **simosx said:**
> Again, you should both produce the alsa-info.sh output, then compared them.

My output has just been uploaded to 
[http://www.alsa-project.org/db/?f=0210b0b445368be702524173e5ca29398a09d525](http://www.alsa-project.org/db/?f=0210b0b445368be702524173e5ca29398a09d525)
here's the outcome...
```
!!################################
!!ALSA Information Script v 0.4.59
!!################################

!!Script ran on: Wed Aug 11 23:38:55 UTC 2010


!!Linux Distribution
!!------------------

Ubuntu 10.04.1 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"


!!DMI Information
!!---------------

Manufacturer:      System manufacturer
Product Name:      P5E


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

snd_ctxfi


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

 0 [XFi            ]: SB-XFi - Creative X-Fi
                      Creative X-Fi 20K1 SB073x


!!PCI Soundcards installed in the system
!!--------------------------------------

05:02.0 Multimedia audio controller: Creative Labs SB X-Fi


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

05:02.0 0401: 1102:0005
	Subsystem: 1102:0031


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

!!Module: snd_ctxfi
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
	index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	multiple : 2
	reference_rate : 48000
	use_system_timer : N


!!ALSA Device nodes
!!-----------------

crw-rw----  1 root audio 116, 10 Aug 12 01:17 /dev/snd/controlC0
crw-rw----  1 root audio 116,  9 Aug 12 01:17 /dev/snd/pcmC0D0c
crw-rw----  1 root audio 116,  8 Aug 12 01:38 /dev/snd/pcmC0D0p
crw-rw----  1 root audio 116,  7 Aug 12 01:17 /dev/snd/pcmC0D1p
crw-rw----  1 root audio 116,  6 Aug 12 01:17 /dev/snd/pcmC0D2p
crw-rw----  1 root audio 116,  5 Aug 12 01:17 /dev/snd/pcmC0D3p
crw-rw----  1 root audio 116,  4 Aug 12 01:17 /dev/snd/pcmC0D4p
crw-rw----  1 root audio 116,  3 Aug 12 01:17 /dev/snd/seq
crw-rw----  1 root audio 116,  2 Aug 12 01:17 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Aug 12 01:17 .
drwxr-xr-x 3 root root 240 Aug 12 01:17 ..
lrwxrwxrwx 1 root root  12 Aug 12 01:17 pci-0000:05:02.0 -> ../controlC0


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: XFi [Creative X-Fi], device 0: ctxfi [Front/WaveIn]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: XFi [Creative X-Fi], device 1: ctxfi [Surround]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: XFi [Creative X-Fi], device 2: ctxfi [Center/LFE]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: XFi [Creative X-Fi], device 3: ctxfi [Side]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: XFi [Creative X-Fi], device 4: ctxfi [IEC958 Non-audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: XFi [Creative X-Fi], device 0: ctxfi [Front/WaveIn]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [XFi]

Card hw:0 'XFi'/'Creative X-Fi 20K1 SB073x'
  Mixer name	: '20K1'
  Components	: ''
  Controls      : 29
  Simple ctrls  : 10
Simple mixer control 'Master',0
  Capabilities: pvolume cvolume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 256 Capture 0 - 256
  Front Left: Playback 107 [42%] [-37.25dB] Capture 205 [80%] [-12.75dB]
  Front Right: Playback 107 [42%] [-37.25dB] Capture 205 [80%] [-12.75dB]
Simple mixer control 'PCM',0
  Capabilities: pvolume cvolume cswitch cswitch-joined penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 256 Capture 0 - 256
  Front Left: Playback 256 [100%] [0.00dB] Capture 256 [100%] [0.00dB] [off]
  Front Right: Playback 256 [100%] [0.00dB] Capture 256 [100%] [0.00dB] [off]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 256
  Mono:
  Front Left: Playback 256 [100%] [0.00dB] [on]
  Front Right: Playback 256 [100%] [0.00dB] [on]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 256
  Mono:
  Front Left: Playback 256 [100%] [0.00dB] [on]
  Front Right: Playback 256 [100%] [0.00dB] [on]
Simple mixer control 'Center/LFE',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 256
  Mono:
  Front Left: Playback 0 [0%] [-99999.99dB] [on]
  Front Right: Playback 0 [0%] [-99999.99dB] [on]
Simple mixer control 'Side',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 256
  Mono:
  Front Left: Playback 256 [100%] [0.00dB] [on]
  Front Right: Playback 256 [100%] [0.00dB] [on]
Simple mixer control 'Line-in',0
  Capabilities: pvolume cvolume pswitch pswitch-joined cswitch cswitch-joined penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 256 Capture 0 - 256
  Front Left: Playback 0 [0%] [-99999.99dB] [on] Capture 256 [100%] [0.00dB] [off]
  Front Right: Playback 0 [0%] [-99999.99dB] [on] Capture 256 [100%] [0.00dB] [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume cvolume cswitch cswitch-joined penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 256 Capture 0 - 256
  Front Left: Playback 154 [60%] [-25.50dB] Capture 240 [94%] [-4.00dB] [on]
  Front Right: Playback 154 [60%] [-25.50dB] Capture 240 [94%] [-4.00dB] [on]
Simple mixer control 'S/PDIF-in',0
  Capabilities: pvolume cvolume pswitch pswitch-joined cswitch cswitch-joined penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 256 Capture 0 - 256
  Front Left: Playback 0 [0%] [-99999.99dB] [on] Capture 256 [100%] [0.00dB] [on]
  Front Right: Playback 0 [0%] [-99999.99dB] [on] Capture 256 [100%] [0.00dB] [on]
Simple mixer control 'S/PDIF-out',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 256
  Mono:
  Front Left: Playback 0 [0%] [-99999.99dB] [off]
  Front Right: Playback 0 [0%] [-99999.99dB] [off]


!!Alsactl output
!!-------------

--startcollapse--
state.XFi {
	control.1 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 256'
		comment.dbmin -6400
		comment.dbmax 0
		iface MIXER
		name 'Master Playback Volume'
		value.0 107
		value.1 107
	}
	control.2 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 256'
		comment.dbmin -6400
		comment.dbmax 0
		iface MIXER
		name 'PCM Playback Volume'
		value.0 256
		value.1 256
	}
	control.3 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 256'
		comment.dbmin -6400
		comment.dbmax 0
		iface MIXER
		name 'Line-in Playback Volume'
		value.0 0
		value.1 0
	}
	control.4 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 256'
		comment.dbmin -6400
		comment.dbmax 0
		iface MIXER
		name 'Mic Playback Volume'
		value.0 154
		value.1 154
	}
	control.5 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 256'
		comment.dbmin -6400
		comment.dbmax 0
		iface MIXER
		name 'S/PDIF-in Playback Volume'
		value.0 0
		value.1 0
	}
	control.6 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 256'
		comment.dbmin -6400
		comment.dbmax 0
		iface MIXER
		name 'S/PDIF-out Playback Volume'
		value.0 0
		value.1 0
	}
	control.7 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 256'
		comment.dbmin -6400
		comment.dbmax 0
		iface MIXER
		name 'Front Playback Volume'
		value.0 256
		value.1 256
	}
	control.8 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 256'
		comment.dbmin -6400
		comment.dbmax 0
		iface MIXER
		name 'Surround Playback Volume'
		value.0 256
		value.1 256
	}
	control.9 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 256'
		comment.dbmin -6400
		comment.dbmax 0
		iface MIXER
		name 'Center/LFE Playback Volume'
		value.0 0
		value.1 0
	}
	control.10 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 256'
		comment.dbmin -6400
		comment.dbmax 0
		iface MIXER
		name 'Side Playback Volume'
		value.0 256
		value.1 256
	}
	control.11 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 256'
		comment.dbmin -6400
		comment.dbmax 0
		iface MIXER
		name 'Master Capture Volume'
		value.0 205
		value.1 205
	}
	control.12 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 256'
		comment.dbmin -6400
		comment.dbmax 0
		iface MIXER
		name 'PCM Capture Volume'
		value.0 256
		value.1 256
	}
	control.13 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 256'
		comment.dbmin -6400
		comment.dbmax 0
		iface MIXER
		name 'Line-in Capture Volume'
		value.0 256
		value.1 256
	}
	control.14 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 256'
		comment.dbmin -6400
		comment.dbmax 0
		iface MIXER
		name 'Mic Capture Volume'
		value.0 240
		value.1 240
	}
	control.15 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 256'
		comment.dbmin -6400
		comment.dbmax 0
		iface MIXER
		name 'S/PDIF-in Capture Volume'
		value.0 256
		value.1 256
	}
	control.16 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'PCM Capture Switch'
		value false
	}
	control.17 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Line-in Capture Switch'
		value false
	}
	control.18 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Mic Capture Switch'
		value true
	}
	control.19 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'S/PDIF-in Capture Switch'
		value true
	}
	control.20 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Line-in Playback Switch'
		value true
	}
	control.21 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'S/PDIF-out Playback Switch'
		value false
	}
	control.22 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'S/PDIF-in Playback Switch'
		value true
	}
	control.23 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Front Playback Switch'
		value true
	}
	control.24 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Surround Playback Switch'
		value true
	}
	control.25 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Center/LFE Playback Switch'
		value true
	}
	control.26 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Side Playback Switch'
		value true
	}
	control.27 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface PCM
		device 4
		name 'IEC958 Playback Mask'
		value ffffffff00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
	}
	control.28 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface PCM
		device 4
		name 'IEC958 Playback Default'
		value '0082000200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.29 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface PCM
		device 4
		name 'IEC958 Playback PCM Stream'
		value '0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
xt_limit
xt_tcpudp
ipt_LOG
ipt_MASQUERADE
xt_DSCP
ipt_REJECT
nf_conntrack_irc
nf_conntrack_ftp
xt_state
binfmt_misc
ppdev
snd_ctxfi
snd_pcm_oss
snd_mixer_oss
snd_pcm
iptable_nat
nf_nat
nf_conntrack_ipv4
snd_seq_dummy
nf_conntrack
nf_defrag_ipv4
snd_seq_oss
snd_seq_midi
snd_rawmidi
iptable_mangle
snd_seq_midi_event
snd_seq
snd_timer
snd_seq_device
snd
iptable_filter
ip_tables
x_tables
fbcon
tileblit
font
bitblit
softcursor
asus_atk0110
soundcore
snd_page_alloc
x38_edac
serio_raw
edac_core
nvidia
vga16fb
vgastate
lp
parport
floppy
usbhid
hid
pata_jmicron
sky2


!!ALSA/HDA dmesg
!!------------------


```


CypherSTL:go here: [https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems) follow the instructions under "**Automatic Sound Information Collection**". Save the file to your home directory and in terminal type ```
bash ./utils_alsa-info.sh
```

---

