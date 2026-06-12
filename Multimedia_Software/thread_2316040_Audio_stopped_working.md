---
title: "Audio stopped working"
date: 2016-03-04
forum: Multimedia Software
---

### Post by fall2 on 2016-03-04
I just tuned on my laptop and there is no audio. It worked the last time the laptop was on before I shut it off yesterday. Speakers nor headsets work. volume is not muted. I don't know because I never changed anything, it just stopped. Its as if there is no power to the audio.

All I know is,
Turned it off, it was working.
Turned it on and no more audio.


UPDATE: March 17 2016:

OS updates for my laptop now made a new problem.
When I try to open pulseaudio volume control I get a fatal error.

"Fatal Error: Unable to connect to PulseAudio: OK"

---

### Post by fall2 on 2016-03-04
This may be a update issue, since it was updated yesterday.
This maybe a hardware issue because I tried a usb boot of xubuntu and still no audio.
I do not understand how to go about to figure out the cause and if its the OS or how to limit possible causes. 
any suggestions?


Maybe this helps?


:~$ sudo aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


:~$ lspci -v | grep -A7 -i "audio"
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
    Subsystem: Gateway, Inc. Device 0402
    Flags: bus master, medium devsel, latency 0, IRQ 10
    I/O ports at 1c00 [size=256]
    I/O ports at 1880 [size=64]
    Memory at e0100c00 (32-bit, non-prefetchable) [size=512]
    Memory at e0100800 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>

---

### Post by fall2 on 2016-03-05
I have xubuntu 14.04 32bit.

Do you think if I reset pulse audio or maybe edited it that would fix it?

---

### Post by fall2 on 2016-03-05
Whats the command line to get user privileges to change a pulse audio file in xubuntu 14.04?


it is something close to this. "leafpad /ect/pulse/default.pa" or "???? leafpad /ect/pulse/default.pa"

I am trying to edit and save the file but don't have access to save.

---

### Post by fall2 on 2016-03-07
All the hardware seems to be in working order. It has to be a software bug.

---

### Post by Yellow Pasque on 2016-03-08
Before you edit anything, try this first:
```
rm -r ~/.config/pulse; pulseaudio -k
```

If it doesn't work, get more info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by florian16 on 2016-03-08
Hello,
Well, I am in the same situation, between yesterday and today, my sound stopped working totally.
And I don't recall doing any update.
I already reset/reinstall pulseaudio but no luck.
In pavucontrol, I can see the sound is detected, but I can't hear anything.
in alsamixer, everything looks fine, nothing is mute...

If it can help, here are my alsa informations : 
[http://www.alsa-project.org/db/?f=9ecf69fafe82ce18889e4c891e31d8690e8403af](http://www.alsa-project.org/db/?f=9ecf69fafe82ce18889e4c891e31d8690e8403af)

---

### Post by Yellow Pasque on 2016-03-08
Did you cutoff this part of the text or was there none given by the script?
```
!!ALSA/HDA dmesg
!!--------------
```

---

### Post by florian16 on 2016-03-10
I did not cut anything, so, none given by the script I guess.
But the problem is really strange. Yesterday my sound was back, today, gone again. After stopping, then starting, back once again!
Finally, it seems my problem is different than fall2's problem.

---

### Post by fall2 on 2016-03-10
I also tried typing in  alsamixer to make sure everything was on.
 Then tried speaker-test -c2 -t wav but no sound.
 I went through all possible options in Pulseaudio volume control with no success.
I tried HDA jack retasking from the ubuntu software center but I could not use it for my laptop, it had no codecs for it. 
I tried modifying one line in the /etc/pulse/default.pa file, from "load-module module-switch-on-port-available" to "#load-module module-switch-on-port-available". That did nothing so I put it back to its original text. - I think this should of forced my headset jack off and put sound to my internal speakers?

Its weird, everything says that its playing sound and nothing points to broken hardware.

---

### Post by fall2 on 2016-03-11
Thanks [**[COLOR=#000000]Temüjin[/COLOR]**]("http://ubuntuforums.org/member.php?u=327594") for that link, it identified the problem for me. I uploaded it but I Don't think I needed to.

It told me that pulseaudio was running but the jack was OFF.

!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

Jack:
      Installed - Yes (/usr/bin/jackd)
      Running - No


If the jack was disconnected the internal speakers would still work. 
I don't know if that indicates a problem with the jack?


>  upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.64
!!################################

!!Script ran on: Fri Mar 11 04:56:18 UTC 2016


!!Linux Distribution
!!------------------

Ubuntu 14.04.4 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 14.04.4 LTS" NAME="Ubuntu" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu 14.04.4 LTS" HOME_URL="http://www.ubuntu.com/" SUPPORT_URL="http://help.ubuntu.com/" BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"


!!DMI Information
!!---------------

Manufacturer:      Gateway                         
Product Name:      Gateway 400VTX                  
Product Version:   Rev 1                   
Firmware Version:  38.00.35


!!Kernel Information
!!------------------

Kernel release:    3.19.0-51-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         i686
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     k3.19.0-51-generic
Library version:    1.0.27.2
Utilities version:  1.0.27.2


!!Loaded ALSA modules
!!-------------------

snd_intel8x0


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

Jack:
      Installed - Yes (/usr/bin/jackd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [I82801DBICH4   ]: ICH4 - Intel 82801DB-ICH4
                      Intel 82801DB-ICH4 with STAC9752,53 at irq 10


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!-------------------------------------------------------

    Subsystem: 107b:0402
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
--
    Subsystem: 107b:0402
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
--
    Subsystem: 107b:0402
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
--
    Subsystem: 107b:0402
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
--
    Subsystem: 107b:0402
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
--
    Subsystem: 107b:0402
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
--
    Subsystem: 107b:0402
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
--
    Subsystem: 107b:0402
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
--
    Subsystem: 107b:0402
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
--
    Subsystem: 107b:0402
    Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
--
00:1f.5 0401: 8086:24c5 (rev 03)
    Subsystem: 107b:0402
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
--
    Subsystem: 107b:0402
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping+ SERR- FastB2B- DisINTx-
--
    Subsystem: 107b:0402
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-


!!Modprobe options (Sound related)
!!--------------------------------

snd_atiixp_modem: index=-2
snd_intel8x0m: index=-2
snd_via82xx_modem: index=-2
snd_usb_audio: index=-2
snd_usb_caiaq: index=-2
snd_usb_ua101: index=-2
snd_usb_us122l: index=-2
snd_usb_usx2y: index=-2
snd_cmipci: mpu_port=0x330 fm_port=0x388
snd_pcsp: index=-2
snd_usb_audio: index=-2


!!Loaded sound module options
!!---------------------------

!!Module: snd_intel8x0
    ac97_clock : 0
    ac97_quirk : (null)
    buggy_irq : 0
    buggy_semaphore : N
    enable : N
    id : (null)
    index : -1
    inside_vm : -1
    joystick : 0
    spdif_aclink : 0
    xbox : N


!!AC97 Codec information
!!----------------------
--startcollapse--

0-0/0: SigmaTel STAC9752,53

PCI Subsys Vendor: 0x107b
PCI Subsys Device: 0x0402

Flags: 0
Revision         : 0x02
Compat. Class    : 0x12
Subsys. Vendor ID: 0xffff
Subsys. ID       : 0xffff

Capabilities     : -headphone out-
DAC resolution   : 20-bit
ADC resolution   : 20-bit
3D enhancement   : SigmaTel 3D Enhancement

Current setup
Mic gain         : +20dB [+20dB]
POP path         : pre 3D
Sim. stereo      : off
3D enhancement   : on
Loudness         : off
Mono output      : MIX
Mic select       : Mic1
ADC/DAC loopback : off
Extended ID      : codec=0 rev=2 AMAP DSA=0 SPDIF VRA
Extended status  : SPDIF=3/4 VRA
PCM front DAC    : 44100Hz
PCM ADC          : 44100Hz
SPDIF Control    : Consumer PCM Category=0x2 Generation=1 Rate=48kHz

                    Gain     Inverted  Buffer delay  Location
Master Out       :   0.0 dBV    -       0/fs         Rear I/O Panel
AUX Out          :   0.0 dBV    -       0/fs         Rear I/O Panel
Mic 1            :   0.0 dBV    -       0/fs         Rear I/O Panel
Mic 2            :   0.0 dBV    -       0/fs         Rear I/O Panel
Line In          :   0.0 dBV    -       0/fs         Rear I/O Panel
Mono Out         :   0.0 dBV    -       0/fs         Rear I/O Panel

0:00 = 6a90
0:02 = 0000
0:04 = 0000
0:06 = 801f
0:08 = 0000
0:0a = 001e
0:0c = 001f
0:0e = 005f
0:10 = 1f1f
0:12 = 1f1f
0:14 = 1f1f
0:16 = 1f1f
0:18 = 0000
0:1a = 0303
0:1c = 0000
0:1e = 0000
0:20 = 2000
0:22 = 0000
0:24 = 0000
0:26 = 000f
0:28 = 0a05
0:2a = 0001
0:2c = ac44
0:2e = 0000
0:30 = 0000
0:32 = ac44
0:34 = 0000
0:36 = 0000
0:38 = 0000
0:3a = 2824
0:3c = 0000
0:3e = 0100
0:40 = 0000
0:42 = 0000
0:44 = 0000
0:46 = 0000
0:48 = 0000
0:4a = 0000
0:4c = 0003
0:4e = ffff
0:50 = 0000
0:52 = 0000
0:54 = 0000
0:56 = 0000
0:58 = 0000
0:5a = 0000
0:5c = 0000
0:5e = 0000
0:60 = 0000
0:62 = 0000
0:64 = 0000
0:66 = 0000
0:68 = 0000
0:6a = 0000
0:6c = 0002
0:6e = 1000
0:70 = 0000
0:72 = 0000
0:74 = 0800
0:76 = 0000
0:78 = 0000
0:7a = 0000
0:7c = 8384
0:7e = 7652
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116,  2 Mar 10 14:57 /dev/snd/controlC0
crw-rw----+ 1 root audio 116,  4 Mar 10 21:41 /dev/snd/pcmC0D0c
crw-rw----+ 1 root audio 116,  3 Mar 10 21:44 /dev/snd/pcmC0D0p
crw-rw----+ 1 root audio 116,  5 Mar 10 14:57 /dev/snd/pcmC0D1c
crw-rw----+ 1 root audio 116,  6 Mar 10 14:57 /dev/snd/pcmC0D2c
crw-rw----+ 1 root audio 116,  7 Mar 10 14:57 /dev/snd/pcmC0D3c
crw-rw----+ 1 root audio 116,  8 Mar 10 21:41 /dev/snd/pcmC0D4p
crw-rw----+ 1 root audio 116,  1 Mar 10 14:57 /dev/snd/seq
crw-rw----+ 1 root audio 116, 33 Mar 10 14:57 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Mar 10 14:57 .
drwxr-xr-x 3 root root 240 Mar 10 14:57 ..
lrwxrwxrwx 1 root root  12 Mar 10 14:57 pci-0000:00:1f.5 -> ../controlC0


!!Aplay/Arecord output
!!--------------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 1: Intel ICH - MIC ADC [Intel 82801DB-ICH4 - MIC ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 2: Intel ICH - MIC2 ADC [Intel 82801DB-ICH4 - MIC2 ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 3: Intel ICH - ADC2 [Intel 82801DB-ICH4 - ADC2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [I82801DBICH4]

Card hw:0 'I82801DBICH4'/'Intel 82801DB-ICH4 with STAC9752,53 at irq 10'
  Mixer name    : 'SigmaTel STAC9752,53'
  Components    : 'AC97a:83847652'
  Controls      : 39
  Simple ctrls  : 24
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Master Mono',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-46.50dB] [off]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control '3D Control - Center',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 15
  Mono: 0 [0%]
Simple mixer control '3D Control - Depth',0
  Capabilities: pvolume pvolume-joined
  Playback channels: Mono
  Limits: Playback 0 - 15
  Mono: Playback 0 [0%]
Simple mixer control '3D Control - Switch',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [12.00dB] [on]
  Front Right: Playback 31 [100%] [12.00dB] [on]
Simple mixer control 'PCM Out Path & Mute',0
  Capabilities: enum
  Items: 'pre 3D' 'post 3D'
  Item0: 'pre 3D'
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [-34.50dB] [on] Capture [off]
  Front Right: Playback 0 [0%] [-34.50dB] [on] Capture [off]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [-34.50dB] [on] Capture [off]
  Front Right: Playback 0 [0%] [-34.50dB] [on] Capture [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-34.50dB] [on]
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Mic Boost (+20dB)',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Mic Select',0
  Capabilities: enum
  Items: 'Mic1' 'Mic2'
  Item0: 'Mic1'
Simple mixer control 'Video',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [-34.50dB] [on] Capture [off]
  Front Right: Playback 0 [0%] [-34.50dB] [on] Capture [off]
Simple mixer control 'Phone',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-34.50dB] [on]
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 Playback AC97-SPSA',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 3
  Mono: 0 [0%]
Simple mixer control 'Beep',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 15
  Mono: Playback 0 [0%] [-45.00dB] [on]
Simple mixer control 'Aux',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [-34.50dB] [on] Capture [on]
  Front Right: Playback 0 [0%] [-34.50dB] [on] Capture [on]
Simple mixer control 'Mono Output Select',0
  Capabilities: enum
  Items: 'Mix' 'Mic'
  Item0: 'Mix'
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch cswitch-joined
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 0 [0%] [0.00dB] [on]
  Front Right: Capture 0 [0%] [0.00dB] [on]
Simple mixer control 'Mix',0
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Mix Mono',0
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'External Amplifier',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]


!!Alsactl output
!!--------------

--startcollapse--
state.I82801DBICH4 {
    control.1 {
        iface MIXER
        name 'Master Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.2 {
        iface MIXER
        name 'Master Playback Volume'
        value.0 31
        value.1 31
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 31'
            dbmin -4650
            dbmax 0
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.3 {
        iface MIXER
        name 'Headphone Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.4 {
        iface MIXER
        name 'Headphone Playback Volume'
        value.0 31
        value.1 31
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 31'
            dbmin -4650
            dbmax 0
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.5 {
        iface MIXER
        name 'Master Mono Playback Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.6 {
        iface MIXER
        name 'Master Mono Playback Volume'
        value 0
        comment {
            access 'read write'
            type INTEGER
            count 1
            range '0 - 31'
            dbmin -4650
            dbmax 0
            dbvalue.0 -4650
        }
    }
    control.7 {
        iface MIXER
        name 'Beep Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.8 {
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
    control.9 {
        iface MIXER
        name 'Phone Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.10 {
        iface MIXER
        name 'Phone Playback Volume'
        value 0
        comment {
            access 'read write'
            type INTEGER
            count 1
            range '0 - 31'
            dbmin -3450
            dbmax 1200
            dbvalue.0 -3450
        }
    }
    control.11 {
        iface MIXER
        name 'Mic Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.12 {
        iface MIXER
        name 'Mic Playback Volume'
        value 0
        comment {
            access 'read write'
            type INTEGER
            count 1
            range '0 - 31'
            dbmin -3450
            dbmax 1200
            dbvalue.0 -3450
        }
    }
    control.13 {
        iface MIXER
        name 'Mic Boost (+20dB)'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.14 {
        iface MIXER
        name 'Line Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.15 {
        iface MIXER
        name 'Line Playback Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 31'
            dbmin -3450
            dbmax 1200
            dbvalue.0 -3450
            dbvalue.1 -3450
        }
    }
    control.16 {
        iface MIXER
        name 'CD Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.17 {
        iface MIXER
        name 'CD Playback Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 31'
            dbmin -3450
            dbmax 1200
            dbvalue.0 -3450
            dbvalue.1 -3450
        }
    }
    control.18 {
        iface MIXER
        name 'Video Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.19 {
        iface MIXER
        name 'Video Playback Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 31'
            dbmin -3450
            dbmax 1200
            dbvalue.0 -3450
            dbvalue.1 -3450
        }
    }
    control.20 {
        iface MIXER
        name 'Aux Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.21 {
        iface MIXER
        name 'Aux Playback Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 31'
            dbmin -3450
            dbmax 1200
            dbvalue.0 -3450
            dbvalue.1 -3450
        }
    }
    control.22 {
        iface MIXER
        name 'PCM Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.23 {
        iface MIXER
        name 'PCM Playback Volume'
        value.0 31
        value.1 31
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 31'
            dbmin -3450
            dbmax 1200
            dbvalue.0 1200
            dbvalue.1 1200
        }
    }
    control.24 {
        iface MIXER
        name 'Capture Source'
        value.0 Aux
        value.1 Aux
        comment {
            access 'read write'
            type ENUMERATED
            count 2
            item.0 Mic
            item.1 CD
            item.2 Video
            item.3 Aux
            item.4 Line
            item.5 Mix
            item.6 'Mix Mono'
            item.7 Phone
        }
    }
    control.25 {
        iface MIXER
        name 'Capture Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.26 {
        iface MIXER
        name 'Capture Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 15'
            dbmin 0
            dbmax 2250
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.27 {
        iface MIXER
        name 'PCM Out Path & Mute'
        value 'pre 3D'
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 'pre 3D'
            item.1 'post 3D'
        }
    }
    control.28 {
        iface MIXER
        name '3D Control - Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.29 {
        iface MIXER
        name 'Mono Output Select'
        value Mix
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Mix
            item.1 Mic
        }
    }
    control.30 {
        iface MIXER
        name 'Mic Select'
        value Mic1
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Mic1
            item.1 Mic2
        }
    }
    control.31 {
        iface MIXER
        name '3D Control - Center'
        value 0
        comment {
            access 'read write'
            type INTEGER
            count 1
            range '0 - 15'
        }
    }
    control.32 {
        iface MIXER
        name '3D Control - Depth'
        value 0
        comment {
            access 'read write'
            type INTEGER
            count 1
            range '0 - 15'
        }
    }
    control.33 {
        iface MIXER
        name 'IEC958 Playback Con Mask'
        value '0fff000f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.34 {
        iface MIXER
        name 'IEC958 Playback Pro Mask'
        value cf00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.35 {
        iface MIXER
        name 'IEC958 Playback Default'
        value '0082000200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access 'read write'
            type IEC958
            count 1
        }
    }
    control.36 {
        iface MIXER
        name 'IEC958 Playback Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.37 {
        iface MIXER
        name 'IEC958 Playback AC97-SPSA'
        value 0
        comment {
            access 'read write'
            type INTEGER
            count 1
            range '0 - 3'
        }
    }
    control.38 {
        iface MIXER
        name 'External Amplifier'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.39 {
        iface PCM
        name 'Playback Channel Map'
        value.0 0
        value.1 0
        comment {
            access read
            type INTEGER
            count 2
            range '0 - 36'
        }
    }
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
snd_intel8x0
snd_ac97_codec
ac97_bus
snd_pcm
snd_seq_midi
snd_seq_midi_event
snd_rawmidi
snd_seq
snd_seq_device
snd_timer
ipw2200
snd
libipw
joydev
serio_raw
lib80211
soundcore
i915
pcmcia
rfcomm
bnep
bluetooth
lpc_ich
yenta_socket
drm_kms_helper
cfg80211
pcmcia_rsrc
pcmcia_core
drm
shpchp
i2c_algo_bit
8250_fintek
video
mac_hid
parport_pc
ppdev
lp
parport
uas
usb_storage
e100
psmouse
mii
pata_acpi


!!ALSA/HDA dmesg
!!--------------

[   28.020480] audit: type=1400 audit(1457643421.348:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=701 comm="apparmor_parser"
[   28.632136] snd_intel8x0 0000:00:1f.5: intel8x0_measure_ac97_clock: measured 55315 usecs (2665 samples)
[   28.632145] snd_intel8x0 0000:00:1f.5: clocking to 48000
[   28.785690] [drm:i9xx_check_fifo_underruns [i915]] *ERROR* pipe B underrun


  

---

### Post by Yellow Pasque on 2016-03-11
> If the jack was disconnected the internal speakers would still work.
I don't know if that indicates a problem with the jack?

No. It's referring to JACK software: [https://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit](https://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit)

This line puzzles me:
```
Loaded sound module options
!!---------------------------

!!Module: snd_intel8x0
...
enable : N
```

I would think it should be Yes ('Y'). Try this and reboot:
```
echo "options snd-intel-8x0 enable=1" | sudo tee -a /etc/modprobe.d/alsa-base.conf
```

If it doesn't work, maybe you should get a pulseaudio log:
[https://wiki.ubuntu.com/PulseAudio/Log](https://wiki.ubuntu.com/PulseAudio/Log)

---

### Post by fall2 on 2016-03-11
The code was a no go so here is the log.




```
  (   0.000|   0.000) I: [pulseaudio] main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
(   0.000|   0.000) I: [pulseaudio] main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
(   0.000|   0.000) D: [pulseaudio] core-rtclock.c: Timer slack is set to 50 us.
(   0.018|   0.017) D: [pulseaudio] core-util.c: RealtimeKit worked.
(   0.018|   0.000) I: [pulseaudio] core-util.c: Successfully gained nice level -11.
(   0.018|   0.000) I: [pulseaudio] main.c: This is PulseAudio 4.0
(   0.018|   0.000) D: [pulseaudio] main.c: Compilation host: i686-pc-linux-gnu
(   0.018|   0.000) D: [pulseaudio] main.c: Compilation CFLAGS: -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Werror=format-security -Wall -W -Wextra -pipe -Wno-long-long -Wno-overlength-strings -Wunsafe-loop-optimizations -Wundef -Wformat=2 -Wlogical-op -Wsign-compare -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wpointer-arith -Winit-self -Wdeclaration-after-statement -Wfloat-equal -Wmissing-prototypes -Wredundant-decls -Wmissing-declarations -Wmissing-noreturn -Wshadow -Wendif-labels -Wcast-align -Wstrict-aliasing -Wwrite-strings -Wno-unused-parameter -ffast-math -Wp,-D_FORTIFY_SOURCE=2 -fno-common -fdiagnostics-show-option
(   0.018|   0.000) D: [pulseaudio] main.c: Running on host: Linux i686 3.19.0-51-generic #58~14.04.1-Ubuntu SMP Fri Feb 26 22:03:27 UTC 2016
(   0.018|   0.000) D: [pulseaudio] main.c: Found 1 CPUs.
(   0.018|   0.000) I: [pulseaudio] main.c: Page size is 4096 bytes
(   0.018|   0.000) D: [pulseaudio] main.c: Compiled with Valgrind support: no
(   0.019|   0.000) D: [pulseaudio] main.c: Running in valgrind mode: no
(   0.019|   0.000) D: [pulseaudio] main.c: Running in VM: no
(   0.019|   0.000) D: [pulseaudio] main.c: Optimized build: yes
(   0.019|   0.000) D: [pulseaudio] main.c: FASTPATH defined, only fast path asserts disabled.
(   0.019|   0.000) I: [pulseaudio] main.c: Machine ID is b99c79403e26b29193156cd95679c2ae.
(   0.019|   0.000) I: [pulseaudio] main.c: Session ID is c1.
(   0.019|   0.000) I: [pulseaudio] main.c: Using runtime directory /run/user/1000/pulse.
(   0.019|   0.000) I: [pulseaudio] main.c: Using state directory /home/fall/.config/pulse.
(   0.020|   0.000) I: [pulseaudio] main.c: Using modules directory /usr/lib/pulse-4.0/modules.
(   0.020|   0.000) I: [pulseaudio] main.c: Running in system mode: no
(   0.020|   0.000) I: [pulseaudio] main.c: Fresh high-resolution timers available! Bon appetit!
(   0.020|   0.000) D: [pulseaudio] memblock.c: Using shared memory pool with 1024 slots of size 64.0 KiB each, total size is 64.0 MiB, maximum usable slot size is 65496
(   0.021|   0.000) I: [pulseaudio] cpu-x86.c: CPU flags: CMOV MMX SSE SSE2 
(   0.021|   0.000) I: [pulseaudio] svolume_mmx.c: Initialising MMX optimized volume functions.
(   0.021|   0.000) I: [pulseaudio] remap_mmx.c: Initialising MMX optimized remappers.
(   0.021|   0.000) I: [pulseaudio] svolume_sse.c: Initialising SSE2 optimized volume functions.
(   0.021|   0.000) I: [pulseaudio] remap_sse.c: Initialising SSE2 optimized remappers.
(   0.021|   0.000) I: [pulseaudio] sconv_sse.c: Initialising SSE2 optimized conversions.
(   0.021|   0.000) I: [pulseaudio] svolume_orc.c: Initialising ORC optimized volume functions.
(   0.024|   0.002) D: [pulseaudio] database-tdb.c: Opened TDB database '/home/fall/.config/pulse/b99c79403e26b29193156cd95679c2ae-device-volumes.tdb'
(   0.024|   0.000) I: [pulseaudio] module-device-restore.c: Successfully opened database file '/home/fall/.config/pulse/b99c79403e26b29193156cd95679c2ae-device-volumes'.
(   0.025|   0.000) I: [pulseaudio] module.c: Loaded "module-device-restore" (index: #0; argument: "").
(   0.026|   0.001) D: [pulseaudio] database-tdb.c: Opened TDB database '/home/fall/.config/pulse/b99c79403e26b29193156cd95679c2ae-stream-volumes.tdb'
(   0.026|   0.000) I: [pulseaudio] module-stream-restore.c: Successfully opened database file '/home/fall/.config/pulse/b99c79403e26b29193156cd95679c2ae-stream-volumes'.
(   0.027|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1 added for object /org/pulseaudio/stream_restore1
(   0.027|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry added for object /org/pulseaudio/stream_restore1/entry0
(   0.027|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry added for object /org/pulseaudio/stream_restore1/entry1
(   0.027|   0.000) I: [pulseaudio] module.c: Loaded "module-stream-restore" (index: #1; argument: "").
(   0.029|   0.001) D: [pulseaudio] database-tdb.c: Opened TDB database '/home/fall/.config/pulse/b99c79403e26b29193156cd95679c2ae-card-database.tdb'
(   0.029|   0.000) I: [pulseaudio] module-card-restore.c: Successfully opened database file '/home/fall/.config/pulse/b99c79403e26b29193156cd95679c2ae-card-database'.
(   0.029|   0.000) I: [pulseaudio] module.c: Loaded "module-card-restore" (index: #2; argument: "").
(   0.030|   0.001) I: [pulseaudio] module.c: Loaded "module-augment-properties" (index: #3; argument: "").
(   0.031|   0.001) I: [pulseaudio] module.c: Loaded "module-switch-on-port-available" (index: #4; argument: "").
(   0.032|   0.000) D: [pulseaudio] cli-command.c: Checking for existence of '/usr/lib/pulse-4.0/modules/module-udev-detect.so': success
(   0.037|   0.005) D: [pulseaudio] module-udev-detect.c: /dev/snd/controlC0 is accessible: yes
(   0.039|   0.002) D: [pulseaudio] module-udev-detect.c: /devices/pci0000:00/0000:00:1f.5/sound/card0 is busy: no
(   0.039|   0.000) D: [pulseaudio] module-udev-detect.c: Loading module-alsa-card with arguments 'device_id="0" name="pci-0000_00_1f.5" card_name="alsa_card.pci-0000_00_1f.5" namereg_fail=false tsched=yes fixed_latency_range=no ignore_dB=no deferred_volume=yes use_ucm=yes card_properties="module-udev-detect.discovered=1"'
(   0.048|   0.008) D: [pulseaudio] dbus-util.c: Successfully connected to D-Bus session bus 3ec1f8f5b73a7239e484c1ee56e33f6c as :1.54
(   0.051|   0.002) D: [pulseaudio] reserve-wrap.c: Successfully acquired reservation lock on device 'Audio0'
(   0.051|   0.000) I: [pulseaudio] (alsa-lib)utils.c: could not open configuration file /usr/share/alsa/ucm/Intel 82801DB-ICH4/Intel 82801DB-ICH4.conf
(   0.051|   0.000) I: [pulseaudio] (alsa-lib)parser.c: error: could not parse configuration for card Intel 82801DB-ICH4
(   0.051|   0.000) I: [pulseaudio] (alsa-lib)main.c: error: failed to import Intel 82801DB-ICH4 use case configuration -2
(   0.051|   0.000) I: [pulseaudio] alsa-ucm.c: UCM not available for card Intel 82801DB-ICH4
(   0.054|   0.003) D: [pulseaudio] alsa-mixer.c: Looking at profile input:analog-mono
(   0.055|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for recording on Analog Mono (analog-mono)
(   0.055|   0.000) D: [pulseaudio] alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.060|   0.005) D: [pulseaudio] alsa-util.c: Managed to open hw:0
(   0.061|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
(   0.061|   0.000) D: [pulseaudio] alsa-util.c: Trying hw:0 without SND_PCM_NO_AUTO_FORMAT ...
(   0.062|   0.000) D: [pulseaudio] alsa-util.c: Managed to open hw:0
(   0.062|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
(   0.062|   0.000) D: [pulseaudio] alsa-util.c: Trying plug:hw:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.063|   0.000) D: [pulseaudio] alsa-util.c: Managed to open plug:hw:0
(   0.063|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
(   0.063|   0.000) D: [pulseaudio] alsa-util.c: Trying plug:hw:0 without SND_PCM_NO_AUTO_FORMAT ...
(   0.064|   0.000) D: [pulseaudio] alsa-util.c: Managed to open plug:hw:0
(   0.065|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
(   0.065|   0.000) I: [pulseaudio] alsa-util.c: Failed to set hardware parameters on plug:hw:0: Invalid argument
(   0.065|   0.000) D: [pulseaudio] alsa-mixer.c: Caching failure to open input:analog-mono
(   0.065|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile input:analog-stereo
(   0.065|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for recording on Analog Stereo (analog-stereo)
(   0.065|   0.000) D: [pulseaudio] alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.072|   0.006) D: [pulseaudio] alsa-util.c: Managed to open front:0
(   0.072|   0.000) D: [pulseaudio] alsa-util.c: Maximum hw buffer size is 371 ms
(   0.073|   0.000) D: [pulseaudio] alsa-util.c: Set buffer size first (to 3528 samples), period size second (to 441 samples).
(   0.073|   0.000) D: [pulseaudio] alsa-mixer.c: Profile input:analog-stereo supported.
(   0.086|   0.013) I: [pulseaudio] (alsa-lib)control.c: Invalid CTL front:0
(   0.086|   0.000) I: [pulseaudio] alsa-util.c: Unable to attach to mixer front:0: No such file or directory
(   0.087|   0.001) I: [pulseaudio] alsa-util.c: Successfully attached to mixer 'hw:0'
(   0.087|   0.000) D: [pulseaudio] alsa-mixer.c: Probing path 'analog-input-microphone-front'
(   0.088|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Front Mic Jack' succeeded (not found)
(   0.088|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Front Mic Phantom Jack' succeeded (not found)
(   0.088|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Front Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.088|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Front Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.088|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Capture' succeeded (volume=1, switch=1, enumeration=0).
(   0.088|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Input Source' succeeded (volume=0, switch=0, enumeration=0).
(   0.088|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Capture Source' succeeded (volume=0, switch=0, enumeration=0).
(   0.088|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic' succeeded (volume=0, switch=2, enumeration=0).
(   0.088|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Internal Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.088|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Rear Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.088|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Dock Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.088|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.088|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Dock Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.088|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Internal Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.088|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Rear Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.088|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Line' succeeded (volume=0, switch=2, enumeration=0).
(   0.088|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Line Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.088|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Aux' succeeded (volume=0, switch=2, enumeration=0).
(   0.088|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Video' succeeded (volume=0, switch=2, enumeration=0).
(   0.088|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic/Line' succeeded (volume=0, switch=0, enumeration=0).
(   0.089|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'TV Tuner' succeeded (volume=0, switch=0, enumeration=0).
(   0.089|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'FM' succeeded (volume=0, switch=0, enumeration=0).
(   0.089|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Inverted Internal Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.089|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic Jack Mode' succeeded (volume=0, switch=0, enumeration=0).
(   0.089|   0.000) D: [pulseaudio] alsa-mixer.c: Skipping path 'analog-input-microphone-front', none of required-any elements preset.
(   0.089|   0.000) D: [pulseaudio] alsa-mixer.c: Probing path 'analog-input-microphone-rear'
(   0.089|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Rear Mic Jack' succeeded (not found)
(   0.089|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Rear Mic Phantom Jack' succeeded (not found)
(   0.089|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Rear Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.089|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Rear Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.089|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Capture' succeeded (volume=1, switch=1, enumeration=0).
(   0.089|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Input Source' succeeded (volume=0, switch=0, enumeration=0).
(   0.089|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Capture Source' succeeded (volume=0, switch=0, enumeration=0).
(   0.089|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic' succeeded (volume=0, switch=2, enumeration=0).
(   0.089|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Internal Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.089|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Front Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.089|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Dock Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.089|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.089|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Dock Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.089|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Internal Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.090|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Front Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.090|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Line' succeeded (volume=0, switch=2, enumeration=0).
(   0.090|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Line Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.090|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Aux' succeeded (volume=0, switch=2, enumeration=0).
(   0.090|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Video' succeeded (volume=0, switch=2, enumeration=0).
(   0.090|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic/Line' succeeded (volume=0, switch=0, enumeration=0).
(   0.090|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'TV Tuner' succeeded (volume=0, switch=0, enumeration=0).
(   0.090|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'FM' succeeded (volume=0, switch=0, enumeration=0).
(   0.090|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Inverted Internal Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.090|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic Jack Mode' succeeded (volume=0, switch=0, enumeration=0).
(   0.090|   0.000) D: [pulseaudio] alsa-mixer.c: Skipping path 'analog-input-microphone-rear', none of required-any elements preset.
(   0.090|   0.000) D: [pulseaudio] alsa-mixer.c: Probing path 'analog-input-microphone-internal'
(   0.090|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Mic Jack' succeeded (not found)
(   0.090|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Dock Mic Jack' succeeded (not found)
(   0.090|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Front Mic Jack' succeeded (not found)
(   0.090|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Rear Mic Jack' succeeded (not found)
(   0.090|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Internal Mic Phantom Jack' succeeded (not found)
(   0.090|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Internal Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.090|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Int Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.091|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Internal Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.091|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Int Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.091|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Capture' succeeded (volume=1, switch=1, enumeration=0).
(   0.091|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Input Source' succeeded (volume=0, switch=0, enumeration=0).
(   0.091|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Capture Source' succeeded (volume=0, switch=0, enumeration=0).
(   0.091|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic' succeeded (volume=0, switch=2, enumeration=0).
(   0.091|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Dock Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.091|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Front Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.091|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Rear Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.091|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Headphone Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.091|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Headphone Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.091|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.091|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Dock Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.091|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Front Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.091|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Rear Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.091|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Line' succeeded (volume=0, switch=2, enumeration=0).
(   0.091|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Line Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.091|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Aux' succeeded (volume=0, switch=2, enumeration=0).
(   0.091|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Video' succeeded (volume=0, switch=2, enumeration=0).
(   0.091|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic/Line' succeeded (volume=0, switch=0, enumeration=0).
(   0.091|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'TV Tuner' succeeded (volume=0, switch=0, enumeration=0).
(   0.092|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'FM' succeeded (volume=0, switch=0, enumeration=0).
(   0.092|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Inverted Internal Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.092|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic Jack Mode' succeeded (volume=0, switch=0, enumeration=0).
(   0.092|   0.000) D: [pulseaudio] alsa-mixer.c: Skipping path 'analog-input-microphone-internal', none of required-any elements preset.
(   0.092|   0.000) D: [pulseaudio] alsa-mixer.c: Probing path 'analog-input-microphone-dock'
(   0.092|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Dock Mic Jack' succeeded (not found)
(   0.092|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Dock Mic Phantom Jack' succeeded (not found)
(   0.092|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Dock Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.092|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Dock Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.092|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Capture' succeeded (volume=1, switch=1, enumeration=0).
(   0.092|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Input Source' succeeded (volume=0, switch=0, enumeration=0).
(   0.092|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Capture Source' succeeded (volume=0, switch=0, enumeration=0).
(   0.092|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic' succeeded (volume=0, switch=2, enumeration=0).
(   0.092|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Internal Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.092|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Front Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.092|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Rear Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.092|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.092|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Internal Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.092|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Front Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.092|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Rear Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.092|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Line' succeeded (volume=0, switch=2, enumeration=0).
(   0.093|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Line Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.093|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Aux' succeeded (volume=0, switch=2, enumeration=0).
(   0.093|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Video' succeeded (volume=0, switch=2, enumeration=0).
(   0.093|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic/Line' succeeded (volume=0, switch=0, enumeration=0).
(   0.093|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'TV Tuner' succeeded (volume=0, switch=0, enumeration=0).
(   0.093|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'FM' succeeded (volume=0, switch=0, enumeration=0).
(   0.093|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Inverted Internal Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.093|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic Jack Mode' succeeded (volume=0, switch=0, enumeration=0).
(   0.093|   0.000) D: [pulseaudio] alsa-mixer.c: Skipping path 'analog-input-microphone-dock', none of required-any elements preset.
(   0.093|   0.000) D: [pulseaudio] alsa-mixer.c: Probing path 'analog-input'
(   0.093|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Capture' succeeded (volume=1, switch=1, enumeration=0).
(   0.093|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic' failed.
(   0.093|   0.000) D: [pulseaudio] alsa-mixer.c: Probing path 'analog-input-microphone'
(   0.093|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Mic Jack' succeeded (not found)
(   0.093|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Mic Phantom Jack' succeeded (not found)
(   0.093|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.093|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic' succeeded (volume=0, switch=1, enumeration=0).
(   0.093|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Capture' succeeded (volume=1, switch=1, enumeration=0).
(   0.093|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Input Source' succeeded (volume=0, switch=0, enumeration=0).
(   0.093|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Capture Source' succeeded (volume=0, switch=0, enumeration=0).
(   0.093|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic Select' succeeded (volume=0, switch=0, enumeration=1).
(   0.094|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic Boost (+20dB)' succeeded (volume=0, switch=0, enumeration=0).
(   0.094|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Front Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.094|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Internal Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.094|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Rear Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.094|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Dock Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.094|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Dock Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.094|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Internal Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.094|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Front Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.094|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Rear Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.094|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Line' succeeded (volume=0, switch=2, enumeration=0).
(   0.094|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Line Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.094|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Aux' succeeded (volume=0, switch=2, enumeration=0).
(   0.094|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Video' succeeded (volume=0, switch=2, enumeration=0).
(   0.094|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic/Line' succeeded (volume=0, switch=0, enumeration=0).
(   0.094|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'TV Tuner' succeeded (volume=0, switch=0, enumeration=0).
(   0.094|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'FM' succeeded (volume=0, switch=0, enumeration=0).
(   0.094|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Inverted Internal Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.094|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic Jack Mode' succeeded (volume=0, switch=0, enumeration=0).
(   0.095|   0.000) D: [pulseaudio] alsa-mixer.c: Probing path 'analog-input-linein'
(   0.095|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Line Jack' succeeded (not found)
(   0.095|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Line Phantom Jack' succeeded (not found)
(   0.095|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Capture' succeeded (volume=1, switch=1, enumeration=0).
(   0.095|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Line Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.095|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Line' succeeded (volume=0, switch=1, enumeration=0).
(   0.095|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Input Source' succeeded (volume=0, switch=0, enumeration=0).
(   0.095|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Capture Source' succeeded (volume=0, switch=0, enumeration=0).
(   0.095|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic' succeeded (volume=0, switch=2, enumeration=0).
(   0.095|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Dock Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.095|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Internal Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.095|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Front Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.095|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Rear Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.095|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.095|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Dock Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.095|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Internal Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.095|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Front Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.095|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Rear Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.095|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Aux' succeeded (volume=0, switch=2, enumeration=0).
(   0.095|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Video' succeeded (volume=0, switch=2, enumeration=0).
(   0.095|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic/Line' succeeded (volume=0, switch=0, enumeration=0).
(   0.096|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'TV Tuner' succeeded (volume=0, switch=0, enumeration=0).
(   0.096|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'FM' succeeded (volume=0, switch=0, enumeration=0).
(   0.096|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic Jack Mode' succeeded (volume=0, switch=0, enumeration=0).
(   0.096|   0.000) D: [pulseaudio] alsa-mixer.c: Probing path 'analog-input'
(   0.096|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Capture' succeeded (volume=1, switch=1, enumeration=0).
(   0.096|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic' succeeded (volume=0, switch=2, enumeration=0).
(   0.096|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Internal Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.096|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Line' succeeded (volume=0, switch=2, enumeration=0).
(   0.096|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Aux' succeeded (volume=0, switch=1, enumeration=0).
(   0.096|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Video' succeeded (volume=0, switch=2, enumeration=0).
(   0.096|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic/Line' succeeded (volume=0, switch=0, enumeration=0).
(   0.096|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'TV Tuner' succeeded (volume=0, switch=0, enumeration=0).
(   0.096|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'FM' succeeded (volume=0, switch=0, enumeration=0).
(   0.097|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Input Source Select' succeeded (volume=0, switch=0, enumeration=0).
(   0.097|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Input Source' succeeded (volume=0, switch=0, enumeration=0).
(   0.097|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Capture Source' succeeded (volume=0, switch=0, enumeration=0).
(   0.097|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic Jack Mode' succeeded (volume=0, switch=0, enumeration=0).
(   0.097|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Digital Input Source' succeeded (volume=0, switch=0, enumeration=0).
(   0.097|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Analog Source' succeeded (volume=0, switch=0, enumeration=0).
(   0.097|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Shared Mic/Line in' succeeded (volume=0, switch=0, enumeration=0).
(   0.097|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Capture Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.097|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Auto Gain Control' succeeded (volume=0, switch=0, enumeration=0).
(   0.097|   0.000) D: [pulseaudio] alsa-mixer.c: Probing path 'analog-input-video'
(   0.097|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Capture' succeeded (volume=1, switch=1, enumeration=0).
(   0.097|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic' succeeded (volume=0, switch=2, enumeration=0).
(   0.097|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Internal Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.097|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Line' succeeded (volume=0, switch=2, enumeration=0).
(   0.097|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Aux' succeeded (volume=0, switch=2, enumeration=0).
(   0.097|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Video' succeeded (volume=0, switch=1, enumeration=0).
(   0.097|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic/Line' succeeded (volume=0, switch=0, enumeration=0).
(   0.097|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'TV Tuner' succeeded (volume=0, switch=0, enumeration=0).
(   0.097|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'FM' succeeded (volume=0, switch=0, enumeration=0).
(   0.098|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Input Source Select' succeeded (volume=0, switch=0, enumeration=0).
(   0.098|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Input Source' succeeded (volume=0, switch=0, enumeration=0).
(   0.098|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Capture Source' succeeded (volume=0, switch=0, enumeration=0).
(   0.098|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic Jack Mode' succeeded (volume=0, switch=0, enumeration=0).
(   0.098|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Digital Input Source' succeeded (volume=0, switch=0, enumeration=0).
(   0.098|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Analog Source' succeeded (volume=0, switch=0, enumeration=0).
(   0.098|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Shared Mic/Line in' succeeded (volume=0, switch=0, enumeration=0).
(   0.098|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Capture Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.098|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Auto Gain Control' succeeded (volume=0, switch=0, enumeration=0).
(   0.098|   0.000) D: [pulseaudio] alsa-mixer.c: Probing path 'analog-input-video'
(   0.098|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Capture' succeeded (volume=1, switch=1, enumeration=0).
(   0.098|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic' succeeded (volume=0, switch=2, enumeration=0).
(   0.098|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Internal Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.098|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Line' succeeded (volume=0, switch=2, enumeration=0).
(   0.098|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Aux' succeeded (volume=0, switch=2, enumeration=0).
(   0.098|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Video' succeeded (volume=0, switch=2, enumeration=0).
(   0.098|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic/Line' succeeded (volume=0, switch=0, enumeration=0).
(   0.098|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'TV Tuner' failed.
(   0.099|   0.000) D: [pulseaudio] alsa-mixer.c: Probing path 'analog-input-radio'
(   0.099|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Capture' succeeded (volume=1, switch=1, enumeration=0).
(   0.099|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic' succeeded (volume=0, switch=2, enumeration=0).
(   0.099|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Internal Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.099|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Line' succeeded (volume=0, switch=2, enumeration=0).
(   0.099|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Aux' succeeded (volume=0, switch=2, enumeration=0).
(   0.099|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Video' succeeded (volume=0, switch=2, enumeration=0).
(   0.099|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic/Line' succeeded (volume=0, switch=0, enumeration=0).
(   0.099|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'TV Tuner' succeeded (volume=0, switch=0, enumeration=0).
(   0.099|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'FM' failed.
(   0.099|   0.000) D: [pulseaudio] alsa-mixer.c: Probing path 'analog-input'
(   0.099|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Capture' succeeded (volume=1, switch=1, enumeration=0).
(   0.099|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic' succeeded (volume=0, switch=2, enumeration=0).
(   0.099|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Internal Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.099|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Line' succeeded (volume=0, switch=2, enumeration=0).
(   0.099|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Line Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.099|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Aux' succeeded (volume=0, switch=2, enumeration=0).
(   0.099|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Video' succeeded (volume=0, switch=2, enumeration=0).
(   0.099|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic/Line' failed.
(   0.099|   0.000) D: [pulseaudio] alsa-mixer.c: Probing path 'analog-input-microphone'
(   0.099|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Headphone Mic Jack' succeeded (not found)
(   0.100|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Headphone Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.100|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Headphone Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.100|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Capture' succeeded (volume=1, switch=1, enumeration=0).
(   0.100|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Input Source' succeeded (volume=0, switch=0, enumeration=0).
(   0.100|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Capture Source' succeeded (volume=0, switch=0, enumeration=0).
(   0.100|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Auto-Mute Mode' succeeded (volume=0, switch=0, enumeration=0).
(   0.100|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Front Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.100|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Internal Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.100|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Rear Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.100|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Dock Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.100|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Dock Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.100|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Internal Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.100|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Front Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.100|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Rear Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.100|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Line' succeeded (volume=0, switch=2, enumeration=0).
(   0.100|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Line Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.100|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Aux' succeeded (volume=0, switch=2, enumeration=0).
(   0.100|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Video' succeeded (volume=0, switch=2, enumeration=0).
(   0.100|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic/Line' succeeded (volume=0, switch=0, enumeration=0).
(   0.100|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'TV Tuner' succeeded (volume=0, switch=0, enumeration=0).
(   0.100|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'FM' succeeded (volume=0, switch=0, enumeration=0).
(   0.100|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Inverted Internal Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.101|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic Jack Mode' succeeded (volume=0, switch=0, enumeration=0).
(   0.101|   0.000) D: [pulseaudio] alsa-mixer.c: Skipping path 'analog-input-microphone', none of required-any elements preset.
(   0.101|   0.000) D: [pulseaudio] alsa-mixer.c: Probing path 'analog-input-microphone-headset'
(   0.101|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Headset Mic Jack' succeeded (not found)
(   0.101|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Headset Mic Phantom Jack' succeeded (not found)
(   0.101|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Headphone Jack' succeeded (not found)
(   0.101|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Headphone Mic Jack' succeeded (not found)
(   0.101|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Headset Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.101|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Headset Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.101|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Headset' succeeded (volume=0, switch=0, enumeration=0).
(   0.101|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Capture' succeeded (volume=1, switch=1, enumeration=0).
(   0.101|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Input Source' succeeded (volume=0, switch=0, enumeration=0).
(   0.101|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Capture Source' succeeded (volume=0, switch=0, enumeration=0).
(   0.101|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Front Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.101|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Internal Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.101|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Rear Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.101|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Dock Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.101|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Dock Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.101|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Internal Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.101|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Front Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.101|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Rear Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.102|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Line' succeeded (volume=0, switch=2, enumeration=0).
(   0.102|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Line Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.102|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Aux' succeeded (volume=0, switch=2, enumeration=0).
(   0.102|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Video' succeeded (volume=0, switch=2, enumeration=0).
(   0.102|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic/Line' succeeded (volume=0, switch=0, enumeration=0).
(   0.102|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'TV Tuner' succeeded (volume=0, switch=0, enumeration=0).
(   0.102|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'FM' succeeded (volume=0, switch=0, enumeration=0).
(   0.102|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Inverted Internal Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.102|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic Jack Mode' succeeded (volume=0, switch=0, enumeration=0).
(   0.102|   0.000) D: [pulseaudio] alsa-mixer.c: Skipping path 'analog-input-microphone-headset', none of required-any elements preset.
(   0.102|   0.000) D: [pulseaudio] alsa-mixer.c: Available mixer paths (after tidying):
(   0.102|   0.000) D: [pulseaudio] alsa-mixer.c: Path Set 0x8629af0, direction=2
(   0.102|   0.000) D: [pulseaudio] alsa-mixer.c: Path analog-input-microphone (Microphone), direction=2, priority=87, probed=yes, supported=yes, has_mute=yes, has_volume=yes, has_dB=yes, min_volume=0, max_volume=15, min_dB=0, max_dB=22.5
(   0.102|   0.000) D: [pulseaudio] alsa-mixer.c: Element Mic, direction=2, switch=1, volume=0, volume_limit=-1, enumeration=0, required=0, required_any=4, required_absent=0, mask=0x0, n_channels=0, override_map=yes
(   0.102|   0.000) D: [pulseaudio] alsa-mixer.c: Element Capture, direction=2, switch=1, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
(   0.102|   0.000) D: [pulseaudio] alsa-mixer.c: Element Mic Select, direction=2, switch=0, volume=0, volume_limit=-1, enumeration=1, required=0, required_any=0, required_absent=0, mask=0x0, n_channels=0, override_map=no
(   0.103|   0.000) D: [pulseaudio] alsa-mixer.c: Option Mic1 (input-microphone-1/Microphone 1) index=0, priority=20
(   0.103|   0.000) D: [pulseaudio] alsa-mixer.c: Option Mic2 (input-microphone-2/Microphone 2) index=1, priority=19
(   0.103|   0.000) D: [pulseaudio] alsa-mixer.c: Element Line, direction=2, switch=2, volume=0, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x0, n_channels=0, override_map=no
(   0.103|   0.000) D: [pulseaudio] alsa-mixer.c: Element Aux, direction=2, switch=2, volume=0, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x0, n_channels=0, override_map=no
(   0.103|   0.000) D: [pulseaudio] alsa-mixer.c: Element Video, direction=2, switch=2, volume=0, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x0, n_channels=0, override_map=no
(   0.103|   0.000) D: [pulseaudio] alsa-mixer.c: Jack Mic, alsa_name='Mic Jack', detection unavailable
(   0.103|   0.000) D: [pulseaudio] alsa-mixer.c: Jack Mic Phantom, alsa_name='Mic Phantom Jack', detection unavailable
(   0.103|   0.000) D: [pulseaudio] alsa-mixer.c: Setting input-microphone-1 (Microphone 1) priority=20
(   0.103|   0.000) D: [pulseaudio] alsa-mixer.c: Setting input-microphone-2 (Microphone 2) priority=19
(   0.103|   0.000) D: [pulseaudio] alsa-mixer.c: Path analog-input-linein (Line In), direction=2, priority=81, probed=yes, supported=yes, has_mute=yes, has_volume=yes, has_dB=yes, min_volume=0, max_volume=15, min_dB=0, max_dB=22.5
(   0.103|   0.000) D: [pulseaudio] alsa-mixer.c: Element Capture, direction=2, switch=1, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
(   0.103|   0.000) D: [pulseaudio] alsa-mixer.c: Element Line, direction=2, switch=1, volume=0, volume_limit=-1, enumeration=0, required=0, required_any=4, required_absent=0, mask=0x0, n_channels=0, override_map=yes
(   0.103|   0.000) D: [pulseaudio] alsa-mixer.c: Element Mic, direction=2, switch=2, volume=0, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x0, n_channels=0, override_map=no
(   0.103|   0.000) D: [pulseaudio] alsa-mixer.c: Element Aux, direction=2, switch=2, volume=0, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x0, n_channels=0, override_map=no
(   0.103|   0.000) D: [pulseaudio] alsa-mixer.c: Element Video, direction=2, switch=2, volume=0, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x0, n_channels=0, override_map=no
(   0.103|   0.000) D: [pulseaudio] alsa-mixer.c: Jack Line, alsa_name='Line Jack', detection unavailable
(   0.103|   0.000) D: [pulseaudio] alsa-mixer.c: Jack Line Phantom, alsa_name='Line Phantom Jack', detection unavailable
(   0.103|   0.000) D: [pulseaudio] alsa-mixer.c: Path analog-input (Analog Input), direction=2, priority=80, probed=yes, supported=yes, has_mute=yes, has_volume=yes, has_dB=yes, min_volume=0, max_volume=15, min_dB=0, max_dB=22.5
(   0.103|   0.000) D: [pulseaudio] alsa-mixer.c: Element Capture, direction=2, switch=1, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
(   0.103|   0.000) D: [pulseaudio] alsa-mixer.c: Element Mic, direction=2, switch=2, volume=0, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x0, n_channels=0, override_map=no
(   0.103|   0.000) D: [pulseaudio] alsa-mixer.c: Element Line, direction=2, switch=2, volume=0, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x0, n_channels=0, override_map=no
(   0.104|   0.000) D: [pulseaudio] alsa-mixer.c: Element Aux, direction=2, switch=1, volume=0, volume_limit=-1, enumeration=0, required=4, required_any=0, required_absent=0, mask=0x0, n_channels=0, override_map=yes
(   0.104|   0.000) D: [pulseaudio] alsa-mixer.c: Element Video, direction=2, switch=2, volume=0, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x0, n_channels=0, override_map=no
(   0.104|   0.000) D: [pulseaudio] alsa-mixer.c: Path analog-input-video (Video), direction=2, priority=70, probed=yes, supported=yes, has_mute=yes, has_volume=yes, has_dB=yes, min_volume=0, max_volume=15, min_dB=0, max_dB=22.5
(   0.104|   0.000) D: [pulseaudio] alsa-mixer.c: Element Capture, direction=2, switch=1, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
(   0.104|   0.000) D: [pulseaudio] alsa-mixer.c: Element Mic, direction=2, switch=2, volume=0, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x0, n_channels=0, override_map=no
(   0.104|   0.000) D: [pulseaudio] alsa-mixer.c: Element Line, direction=2, switch=2, volume=0, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x0, n_channels=0, override_map=no
(   0.104|   0.000) D: [pulseaudio] alsa-mixer.c: Element Aux, direction=2, switch=2, volume=0, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x0, n_channels=0, override_map=no
(   0.104|   0.000) D: [pulseaudio] alsa-mixer.c: Element Video, direction=2, switch=1, volume=0, volume_limit=-1, enumeration=0, required=4, required_any=0, required_absent=0, mask=0x0, n_channels=0, override_map=yes
(   0.104|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile input:iec958-stereo
(   0.104|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for recording on Digital Stereo (IEC958) (iec958-stereo)
(   0.104|   0.000) D: [pulseaudio] alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.105|   0.001) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D4c' failed (-2)
(   0.105|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device iec958:0: No such file or directory
(   0.105|   0.000) D: [pulseaudio] alsa-mixer.c: Caching failure to open input:iec958-stereo
(   0.106|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-mono
(   0.106|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Analog Mono (analog-mono)
(   0.106|   0.000) D: [pulseaudio] alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.106|   0.000) D: [pulseaudio] alsa-util.c: Managed to open hw:0
(   0.106|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
(   0.107|   0.000) D: [pulseaudio] alsa-util.c: Trying hw:0 without SND_PCM_NO_AUTO_FORMAT ...
(   0.108|   0.000) D: [pulseaudio] alsa-util.c: Managed to open hw:0
(   0.108|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
(   0.108|   0.000) D: [pulseaudio] alsa-util.c: Trying plug:hw:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.108|   0.000) D: [pulseaudio] alsa-util.c: Managed to open plug:hw:0
(   0.109|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
(   0.109|   0.000) D: [pulseaudio] alsa-util.c: Trying plug:hw:0 without SND_PCM_NO_AUTO_FORMAT ...
(   0.109|   0.000) D: [pulseaudio] alsa-util.c: Managed to open plug:hw:0
(   0.110|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
(   0.110|   0.000) I: [pulseaudio] alsa-util.c: Failed to set hardware parameters on plug:hw:0: Invalid argument
(   0.110|   0.000) D: [pulseaudio] alsa-mixer.c: Caching failure to open output:analog-mono
(   0.111|   0.000) D: [pulseaudio] alsa-mixer.c: Skipping profile output:analog-mono+input:analog-mono - will not be able to open output:analog-mono
(   0.111|   0.000) D: [pulseaudio] alsa-mixer.c: Skipping profile output:analog-mono+input:analog-stereo - will not be able to open output:analog-mono
(   0.111|   0.000) D: [pulseaudio] alsa-mixer.c: Skipping profile output:analog-mono+input:iec958-stereo - will not be able to open output:analog-mono
(   0.111|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-stereo
(   0.111|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Analog Stereo (analog-stereo)
(   0.111|   0.000) D: [pulseaudio] alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.112|   0.001) D: [pulseaudio] alsa-util.c: Managed to open front:0
(   0.112|   0.000) D: [pulseaudio] alsa-util.c: Maximum hw buffer size is 371 ms
(   0.112|   0.000) D: [pulseaudio] alsa-util.c: Set buffer size first (to 3528 samples), period size second (to 441 samples).
(   0.112|   0.000) D: [pulseaudio] alsa-mixer.c: Profile output:analog-stereo supported.
(   0.116|   0.003) I: [pulseaudio] (alsa-lib)control.c: Invalid CTL front:0
(   0.116|   0.000) I: [pulseaudio] alsa-util.c: Unable to attach to mixer front:0: No such file or directory
(   0.118|   0.001) I: [pulseaudio] alsa-util.c: Successfully attached to mixer 'hw:0'
(   0.118|   0.000) D: [pulseaudio] alsa-mixer.c: Probing path 'analog-output'
(   0.118|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Line Out Jack' succeeded (not found)
(   0.118|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Line Out Phantom Jack' succeeded (not found)
(   0.118|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Hardware Master' succeeded (volume=0, switch=0, enumeration=0).
(   0.118|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Master' succeeded (volume=1, switch=1, enumeration=0).
(   0.119|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Master Mono' succeeded (volume=2, switch=2, enumeration=0).
(   0.119|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Line HP Swap' succeeded (volume=0, switch=0, enumeration=0).
(   0.119|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Headphone' succeeded (volume=3, switch=1, enumeration=0).
(   0.119|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Headphone2' succeeded (volume=0, switch=0, enumeration=0).
(   0.119|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Speaker' succeeded (volume=0, switch=0, enumeration=0).
(   0.119|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Desktop Speaker' succeeded (volume=0, switch=0, enumeration=0).
(   0.119|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Front' succeeded (volume=0, switch=0, enumeration=0).
(   0.119|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Rear' succeeded (volume=0, switch=0, enumeration=0).
(   0.119|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Surround' succeeded (volume=0, switch=0, enumeration=0).
(   0.119|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Side' succeeded (volume=0, switch=0, enumeration=0).
(   0.119|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Center' succeeded (volume=0, switch=0, enumeration=0).
(   0.119|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'LFE' succeeded (volume=0, switch=0, enumeration=0).
(   0.119|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'CLFE' succeeded (volume=0, switch=0, enumeration=0).
(   0.119|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'PCM' succeeded (volume=1, switch=1, enumeration=0).
(   0.119|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'External Amplifier' succeeded (volume=0, switch=4, enumeration=0).
(   0.119|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Bass Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.119|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'IEC958' succeeded (volume=0, switch=2, enumeration=0).
(   0.119|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'IEC958 Optical Raw' succeeded (volume=0, switch=0, enumeration=0).
(   0.119|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Analog Output' succeeded (volume=0, switch=0, enumeration=0).
(   0.119|   0.000) D: [pulseaudio] alsa-mixer.c: Probing path 'analog-output-speaker'
(   0.120|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Headphone Jack' succeeded (not found)
(   0.120|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Front Headphone Jack' succeeded (not found)
(   0.120|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Speaker Phantom Jack' succeeded (not found)
(   0.120|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Hardware Master' succeeded (volume=0, switch=0, enumeration=0).
(   0.120|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Master' succeeded (volume=1, switch=1, enumeration=0).
(   0.120|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Master Mono' succeeded (volume=2, switch=2, enumeration=0).
(   0.120|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Headphone' succeeded (volume=3, switch=1, enumeration=0).
(   0.120|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Headphone2' succeeded (volume=0, switch=0, enumeration=0).
(   0.120|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Speaker' succeeded (volume=0, switch=0, enumeration=0).
(   0.120|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Desktop Speaker' succeeded (volume=0, switch=0, enumeration=0).
(   0.120|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Front' succeeded (volume=0, switch=0, enumeration=0).
(   0.120|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Front Speaker' succeeded (volume=0, switch=0, enumeration=0).
(   0.120|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Rear' succeeded (volume=0, switch=0, enumeration=0).
(   0.120|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Surround' succeeded (volume=0, switch=0, enumeration=0).
(   0.120|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Surround Speaker' succeeded (volume=0, switch=0, enumeration=0).
(   0.120|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Side' succeeded (volume=0, switch=0, enumeration=0).
(   0.120|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Center' succeeded (volume=0, switch=0, enumeration=0).
(   0.120|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Center Speaker' succeeded (volume=0, switch=0, enumeration=0).
(   0.120|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'LFE' succeeded (volume=0, switch=0, enumeration=0).
(   0.120|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'LFE Speaker' succeeded (volume=0, switch=0, enumeration=0).
(   0.121|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Bass Speaker' succeeded (volume=0, switch=0, enumeration=0).
(   0.121|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'CLFE' succeeded (volume=0, switch=0, enumeration=0).
(   0.121|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'PCM' succeeded (volume=1, switch=1, enumeration=0).
(   0.121|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'External Amplifier' succeeded (volume=0, switch=4, enumeration=0).
(   0.121|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Bass Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.121|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'IEC958' succeeded (volume=0, switch=2, enumeration=0).
(   0.121|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'IEC958 Optical Raw' succeeded (volume=0, switch=0, enumeration=0).
(   0.121|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Analog Output' succeeded (volume=0, switch=0, enumeration=0).
(   0.121|   0.000) D: [pulseaudio] alsa-mixer.c: Skipping path 'analog-output-speaker', none of required-any elements preset.
(   0.121|   0.000) D: [pulseaudio] alsa-mixer.c: Probing path 'analog-output-speaker'
(   0.121|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Hardware Master' succeeded (volume=0, switch=0, enumeration=0).
(   0.121|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Master' succeeded (volume=1, switch=1, enumeration=0).
(   0.121|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Master Mono' succeeded (volume=2, switch=2, enumeration=0).
(   0.121|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Headphone' succeeded (volume=3, switch=1, enumeration=0).
(   0.121|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Headphone2' succeeded (volume=0, switch=0, enumeration=0).
(   0.121|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Speaker' succeeded (volume=0, switch=0, enumeration=0).
(   0.121|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Desktop Speaker' failed.
(   0.121|   0.000) D: [pulseaudio] alsa-mixer.c: Probing path 'analog-output-headphones'
(   0.121|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Front Headphone Jack' succeeded (not found)
(   0.121|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Front Headphone Phantom Jack' succeeded (not found)
(   0.121|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Headphone Jack' succeeded (not found)
(   0.122|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Headphone Phantom Jack' succeeded (not found)
(   0.122|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Headphone Mic Jack' succeeded (not found)
(   0.122|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Hardware Master' succeeded (volume=0, switch=0, enumeration=0).
(   0.122|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Master' succeeded (volume=1, switch=1, enumeration=0).
(   0.122|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Master Mono' succeeded (volume=2, switch=2, enumeration=0).
(   0.122|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Headphone' succeeded (volume=1, switch=1, enumeration=0).
(   0.122|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Headset' succeeded (volume=0, switch=0, enumeration=0).
(   0.122|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Line HP Swap' succeeded (volume=0, switch=0, enumeration=0).
(   0.122|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Headphone2' succeeded (volume=0, switch=0, enumeration=0).
(   0.122|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Speaker' succeeded (volume=0, switch=0, enumeration=0).
(   0.122|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Desktop Speaker' succeeded (volume=0, switch=0, enumeration=0).
(   0.122|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Front' succeeded (volume=0, switch=0, enumeration=0).
(   0.122|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Rear' succeeded (volume=0, switch=0, enumeration=0).
(   0.122|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Surround' succeeded (volume=0, switch=0, enumeration=0).
(   0.122|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Side' succeeded (volume=0, switch=0, enumeration=0).
(   0.122|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Center' succeeded (volume=0, switch=0, enumeration=0).
(   0.122|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'LFE' succeeded (volume=0, switch=0, enumeration=0).
(   0.122|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'PCM' succeeded (volume=1, switch=1, enumeration=0).
(   0.122|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'External Amplifier' succeeded (volume=0, switch=4, enumeration=0).
(   0.123|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Bass Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.123|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'IEC958' succeeded (volume=0, switch=2, enumeration=0).
(   0.123|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'IEC958 Optical Raw' succeeded (volume=0, switch=0, enumeration=0).
(   0.123|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Analog Output' succeeded (volume=0, switch=0, enumeration=0).
(   0.123|   0.000) D: [pulseaudio] alsa-mixer.c: Probing path 'analog-output-headphones'
(   0.123|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Hardware Master' succeeded (volume=0, switch=0, enumeration=0).
(   0.123|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Master' succeeded (volume=1, switch=1, enumeration=0).
(   0.123|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Master Mono' succeeded (volume=2, switch=2, enumeration=0).
(   0.123|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Headphone' succeeded (volume=3, switch=1, enumeration=0).
(   0.123|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Headphone2' failed.
(   0.123|   0.000) D: [pulseaudio] alsa-mixer.c: Removing path 'analog-output' as it is a subset of 'analog-output-headphones'.
(   0.123|   0.000) D: [pulseaudio] alsa-mixer.c: Available mixer paths (after tidying):
(   0.123|   0.000) D: [pulseaudio] alsa-mixer.c: Path Set 0x862e7e8, direction=1
(   0.123|   0.000) D: [pulseaudio] alsa-mixer.c: Path analog-output-headphones (Headphones), direction=1, priority=90, probed=yes, supported=yes, has_mute=yes, has_volume=yes, has_dB=yes, min_volume=0, max_volume=31, min_dB=-127.5, max_dB=12
(   0.123|   0.000) D: [pulseaudio] alsa-mixer.c: Element Master, direction=1, switch=1, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
(   0.123|   0.000) D: [pulseaudio] alsa-mixer.c: Element Master Mono, direction=1, switch=2, volume=2, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x7ffffffffffff, n_channels=1, override_map=no
(   0.123|   0.000) D: [pulseaudio] alsa-mixer.c: Element Headphone, direction=1, switch=1, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=4, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
(   0.124|   0.000) D: [pulseaudio] alsa-mixer.c: Element PCM, direction=1, switch=1, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
(   0.124|   0.000) D: [pulseaudio] alsa-mixer.c: Element External Amplifier, direction=1, switch=4, volume=0, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x0, n_channels=0, override_map=no
(   0.124|   0.000) D: [pulseaudio] alsa-mixer.c: Option on (output-amplifier-on/Amplifier) index=1, priority=10
(   0.124|   0.000) D: [pulseaudio] alsa-mixer.c: Option off (output-amplifier-off/No Amplifier) index=0, priority=0
(   0.124|   0.000) D: [pulseaudio] alsa-mixer.c: Element IEC958, direction=1, switch=2, volume=0, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x0, n_channels=0, override_map=no
(   0.124|   0.000) D: [pulseaudio] alsa-mixer.c: Jack Front Headphone, alsa_name='Front Headphone Jack', detection unavailable
(   0.124|   0.000) D: [pulseaudio] alsa-mixer.c: Jack Front Headphone Phantom, alsa_name='Front Headphone Phantom Jack', detection unavailable
(   0.124|   0.000) D: [pulseaudio] alsa-mixer.c: Jack Headphone, alsa_name='Headphone Jack', detection unavailable
(   0.124|   0.000) D: [pulseaudio] alsa-mixer.c: Jack Headphone Phantom, alsa_name='Headphone Phantom Jack', detection unavailable
(   0.124|   0.000) D: [pulseaudio] alsa-mixer.c: Jack Headphone Mic, alsa_name='Headphone Mic Jack', detection unavailable
(   0.124|   0.000) D: [pulseaudio] alsa-mixer.c: Setting output-amplifier-on (Amplifier) priority=10
(   0.124|   0.000) D: [pulseaudio] alsa-mixer.c: Setting output-amplifier-off (No Amplifier) priority=0
(   0.124|   0.000) D: [pulseaudio] alsa-mixer.c: Skipping profile output:analog-stereo+input:analog-mono - will not be able to open input:analog-mono
(   0.124|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-stereo+input:analog-stereo
(   0.124|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for recording on Analog Stereo (analog-stereo)
(   0.124|   0.000) D: [pulseaudio] alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.125|   0.001) D: [pulseaudio] alsa-util.c: Managed to open front:0
(   0.126|   0.000) D: [pulseaudio] alsa-util.c: Maximum hw buffer size is 371 ms
(   0.126|   0.000) D: [pulseaudio] alsa-util.c: Set buffer size first (to 3528 samples), period size second (to 441 samples).
(   0.126|   0.000) D: [pulseaudio] alsa-mixer.c: Profile output:analog-stereo+input:analog-stereo supported.
(   0.126|   0.000) D: [pulseaudio] alsa-mixer.c: Skipping profile output:analog-stereo+input:iec958-stereo - will not be able to open input:iec958-stereo
(   0.126|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-surround-40
(   0.126|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Analog Surround 4.0 (analog-surround-40)
(   0.126|   0.000) D: [pulseaudio] alsa-util.c: Trying surround40:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.128|   0.001) D: [pulseaudio] alsa-util.c: Managed to open surround40:0
(   0.128|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
(   0.128|   0.000) D: [pulseaudio] alsa-util.c: Trying surround40:0 without SND_PCM_NO_AUTO_FORMAT ...
(   0.130|   0.001) D: [pulseaudio] alsa-util.c: Managed to open surround40:0
(   0.130|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
(   0.130|   0.000) D: [pulseaudio] alsa-util.c: Trying plug:surround40:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.132|   0.001) D: [pulseaudio] alsa-util.c: Managed to open plug:surround40:0
(   0.132|   0.000) I: [pulseaudio] (alsa-lib)pcm_params.c: Slave PCM not usable
(   0.132|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
(   0.132|   0.000) D: [pulseaudio] alsa-util.c: Trying plug:surround40:0 without SND_PCM_NO_AUTO_FORMAT ...
(   0.134|   0.001) D: [pulseaudio] alsa-util.c: Managed to open plug:surround40:0
(   0.134|   0.000) I: [pulseaudio] (alsa-lib)pcm_params.c: Slave PCM not usable
(   0.134|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
(   0.134|   0.000) I: [pulseaudio] alsa-util.c: Failed to set hardware parameters on plug:surround40:0: Invalid argument
(   0.134|   0.000) D: [pulseaudio] alsa-mixer.c: Caching failure to open output:analog-surround-40
(   0.134|   0.000) D: [pulseaudio] alsa-mixer.c: Skipping profile output:analog-surround-40+input:analog-mono - will not be able to open output:analog-surround-40
(   0.134|   0.000) D: [pulseaudio] alsa-mixer.c: Skipping profile output:analog-surround-40+input:analog-stereo - will not be able to open output:analog-surround-40
(   0.134|   0.000) D: [pulseaudio] alsa-mixer.c: Skipping profile output:analog-surround-40+input:iec958-stereo - will not be able to open output:analog-surround-40
(   0.134|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-surround-41
(   0.134|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Analog Surround 4.1 (analog-surround-41)
(   0.134|   0.000) D: [pulseaudio] alsa-util.c: Trying surround41:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.136|   0.001) D: [pulseaudio] alsa-util.c: Managed to open surround41:0
(   0.136|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
(   0.136|   0.000) D: [pulseaudio] alsa-util.c: Trying surround41:0 without SND_PCM_NO_AUTO_FORMAT ...
(   0.138|   0.001) D: [pulseaudio] alsa-util.c: Managed to open surround41:0
(   0.138|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
(   0.138|   0.000) D: [pulseaudio] alsa-util.c: Trying plug:surround41:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.140|   0.001) D: [pulseaudio] alsa-util.c: Managed to open plug:surround41:0
(   0.140|   0.000) I: [pulseaudio] (alsa-lib)pcm_params.c: Slave PCM not usable
(   0.140|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
(   0.140|   0.000) D: [pulseaudio] alsa-util.c: Trying plug:surround41:0 without SND_PCM_NO_AUTO_FORMAT ...
(   0.142|   0.002) D: [pulseaudio] alsa-util.c: Managed to open plug:surround41:0
(   0.143|   0.000) I: [pulseaudio] (alsa-lib)pcm_params.c: Slave PCM not usable
(   0.143|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
(   0.143|   0.000) I: [pulseaudio] alsa-util.c: Failed to set hardware parameters on plug:surround41:0: Invalid argument
(   0.143|   0.000) D: [pulseaudio] alsa-mixer.c: Caching failure to open output:analog-surround-41
(   0.143|   0.000) D: [pulseaudio] alsa-mixer.c: Skipping profile output:analog-surround-41+input:analog-mono - will not be able to open output:analog-surround-41
(   0.143|   0.000) D: [pulseaudio] alsa-mixer.c: Skipping profile output:analog-surround-41+input:analog-stereo - will not be able to open output:analog-surround-41
(   0.143|   0.000) D: [pulseaudio] alsa-mixer.c: Skipping profile output:analog-surround-41+input:iec958-stereo - will not be able to open output:analog-surround-41
(   0.143|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-surround-50
(   0.143|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Analog Surround 5.0 (analog-surround-50)
(   0.143|   0.000) D: [pulseaudio] alsa-util.c: Trying surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.145|   0.001) D: [pulseaudio] alsa-util.c: Managed to open surround50:0
(   0.145|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
(   0.145|   0.000) D: [pulseaudio] alsa-util.c: Trying surround50:0 without SND_PCM_NO_AUTO_FORMAT ...
(   0.147|   0.001) D: [pulseaudio] alsa-util.c: Managed to open surround50:0
(   0.147|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
(   0.147|   0.000) D: [pulseaudio] alsa-util.c: Trying plug:surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.149|   0.001) D: [pulseaudio] alsa-util.c: Managed to open plug:surround50:0
(   0.149|   0.000) I: [pulseaudio] (alsa-lib)pcm_params.c: Slave PCM not usable
(   0.149|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
(   0.149|   0.000) D: [pulseaudio] alsa-util.c: Trying plug:surround50:0 without SND_PCM_NO_AUTO_FORMAT ...
(   0.151|   0.001) D: [pulseaudio] alsa-util.c: Managed to open plug:surround50:0
(   0.151|   0.000) I: [pulseaudio] (alsa-lib)pcm_params.c: Slave PCM not usable
(   0.151|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
(   0.151|   0.000) I: [pulseaudio] alsa-util.c: Failed to set hardware parameters on plug:surround50:0: Invalid argument
(   0.151|   0.000) D: [pulseaudio] alsa-mixer.c: Caching failure to open output:analog-surround-50
(   0.151|   0.000) D: [pulseaudio] alsa-mixer.c: Skipping profile output:analog-surround-50+input:analog-mono - will not be able to open output:analog-surround-50
(   0.152|   0.000) D: [pulseaudio] alsa-mixer.c: Skipping profile output:analog-surround-50+input:analog-stereo - will not be able to open output:analog-surround-50
(   0.152|   0.000) D: [pulseaudio] alsa-mixer.c: Skipping profile output:analog-surround-50+input:iec958-stereo - will not be able to open output:analog-surround-50
(   0.152|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-surround-51
(   0.152|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Analog Surround 5.1 (analog-surround-51)
(   0.152|   0.000) D: [pulseaudio] alsa-util.c: Trying surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.153|   0.001) D: [pulseaudio] alsa-util.c: Managed to open surround51:0
(   0.153|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
(   0.154|   0.000) D: [pulseaudio] alsa-util.c: Trying surround51:0 without SND_PCM_NO_AUTO_FORMAT ...
(   0.155|   0.001) D: [pulseaudio] alsa-util.c: Managed to open surround51:0
(   0.155|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
(   0.155|   0.000) D: [pulseaudio] alsa-util.c: Trying plug:surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.157|   0.001) D: [pulseaudio] alsa-util.c: Managed to open plug:surround51:0
(   0.157|   0.000) I: [pulseaudio] (alsa-lib)pcm_params.c: Slave PCM not usable
(   0.157|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
(   0.157|   0.000) D: [pulseaudio] alsa-util.c: Trying plug:surround51:0 without SND_PCM_NO_AUTO_FORMAT ...
(   0.159|   0.001) D: [pulseaudio] alsa-util.c: Managed to open plug:surround51:0
(   0.159|   0.000) I: [pulseaudio] (alsa-lib)pcm_params.c: Slave PCM not usable
(   0.159|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
(   0.159|   0.000) I: [pulseaudio] alsa-util.c: Failed to set hardware parameters on plug:surround51:0: Invalid argument
(   0.159|   0.000) D: [pulseaudio] alsa-mixer.c: Caching failure to open output:analog-surround-51
(   0.159|   0.000) D: [pulseaudio] alsa-mixer.c: Skipping profile output:analog-surround-51+input:analog-mono - will not be able to open output:analog-surround-51
(   0.160|   0.000) D: [pulseaudio] alsa-mixer.c: Skipping profile output:analog-surround-51+input:analog-stereo - will not be able to open output:analog-surround-51
(   0.160|   0.000) D: [pulseaudio] alsa-mixer.c: Skipping profile output:analog-surround-51+input:iec958-stereo - will not be able to open output:analog-surround-51
(   0.160|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-surround-71
(   0.160|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Analog Surround 7.1 (analog-surround-71)
(   0.160|   0.000) D: [pulseaudio] alsa-util.c: Trying surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.160|   0.000) I: [pulseaudio] (alsa-lib)conf.c: Unknown parameters 0
(   0.160|   0.000) I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM surround71:0
(   0.160|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device surround71:0: Invalid argument
(   0.160|   0.000) D: [pulseaudio] alsa-mixer.c: Caching failure to open output:analog-surround-71
(   0.160|   0.000) D: [pulseaudio] alsa-mixer.c: Skipping profile output:analog-surround-71+input:analog-mono - will not be able to open output:analog-surround-71
(   0.160|   0.000) D: [pulseaudio] alsa-mixer.c: Skipping profile output:analog-surround-71+input:analog-stereo - will not be able to open output:analog-surround-71
(   0.160|   0.000) D: [pulseaudio] alsa-mixer.c: Skipping profile output:analog-surround-71+input:iec958-stereo - will not be able to open output:analog-surround-71
(   0.160|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:iec958-stereo
(   0.160|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Stereo (IEC958) (iec958-stereo)
(   0.160|   0.000) D: [pulseaudio] alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.162|   0.001) D: [pulseaudio] alsa-util.c: Managed to open iec958:0
(   0.162|   0.000) D: [pulseaudio] alsa-util.c: Maximum hw buffer size is 341 ms
(   0.163|   0.000) D: [pulseaudio] alsa-util.c: Set buffer size first (to 3840 samples), period size second (to 480 samples).
(   0.163|   0.000) I: [pulseaudio] alsa-util.c: Device iec958:0 doesn't support 44100 Hz, changed to 48000 Hz.
(   0.163|   0.000) D: [pulseaudio] alsa-mixer.c: Profile output:iec958-stereo supported.
(   0.163|   0.000) I: [pulseaudio] (alsa-lib)control.c: Invalid CTL iec958:0
(   0.163|   0.000) I: [pulseaudio] alsa-util.c: Unable to attach to mixer iec958:0: No such file or directory
(   0.164|   0.001) I: [pulseaudio] alsa-util.c: Successfully attached to mixer 'hw:0'
(   0.164|   0.000) D: [pulseaudio] alsa-mixer.c: Probing path 'iec958-stereo-output'
(   0.164|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'IEC958' succeeded (volume=0, switch=1, enumeration=0).
(   0.165|   0.000) D: [pulseaudio] alsa-mixer.c: Available mixer paths (after tidying):
(   0.165|   0.000) D: [pulseaudio] alsa-mixer.c: Path Set 0x8659870, direction=1
(   0.165|   0.000) D: [pulseaudio] alsa-mixer.c: Path iec958-stereo-output (Digital Output (S/PDIF)), direction=1, priority=0, probed=yes, supported=yes, has_mute=yes, has_volume=no, has_dB=no, min_volume=0, max_volume=0, min_dB=inf, max_dB=-inf
(   0.165|   0.000) D: [pulseaudio] alsa-mixer.c: Element IEC958, direction=1, switch=1, volume=0, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x0, n_channels=0, override_map=no
(   0.165|   0.000) D: [pulseaudio] alsa-mixer.c: Skipping profile output:iec958-stereo+input:analog-mono - will not be able to open input:analog-mono
(   0.165|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:iec958-stereo+input:analog-stereo
(   0.165|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for recording on Analog Stereo (analog-stereo)
(   0.165|   0.000) D: [pulseaudio] alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.166|   0.001) D: [pulseaudio] alsa-util.c: Managed to open front:0
(   0.166|   0.000) D: [pulseaudio] alsa-util.c: Maximum hw buffer size is 371 ms
(   0.167|   0.000) D: [pulseaudio] alsa-util.c: Set buffer size first (to 3528 samples), period size second (to 441 samples).
(   0.167|   0.000) D: [pulseaudio] alsa-mixer.c: Profile output:iec958-stereo+input:analog-stereo supported.
(   0.167|   0.000) D: [pulseaudio] alsa-mixer.c: Skipping profile output:iec958-stereo+input:iec958-stereo - will not be able to open input:iec958-stereo
(   0.167|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:iec958-ac3-surround-40
(   0.167|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958/AC3) (iec958-ac3-surround-40)
(   0.167|   0.000) D: [pulseaudio] alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.167|   0.000) I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM a52:0
(   0.167|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device a52:0: No such file or directory
(   0.167|   0.000) D: [pulseaudio] alsa-mixer.c: Caching failure to open output:iec958-ac3-surround-40
(   0.167|   0.000) D: [pulseaudio] alsa-mixer.c: Skipping profile output:iec958-ac3-surround-40+input:analog-mono - will not be able to open output:iec958-ac3-surround-40
(   0.167|   0.000) D: [pulseaudio] alsa-mixer.c: Skipping profile output:iec958-ac3-surround-40+input:analog-stereo - will not be able to open output:iec958-ac3-surround-40
(   0.168|   0.000) D: [pulseaudio] alsa-mixer.c: Skipping profile output:iec958-ac3-surround-40+input:iec958-stereo - will not be able to open output:iec958-ac3-surround-40
(   0.168|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:iec958-ac3-surround-51
(   0.168|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Surround 5.1 (IEC958/AC3) (iec958-ac3-surround-51)
(   0.168|   0.000) D: [pulseaudio] alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.168|   0.000) I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM a52:0
(   0.168|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device a52:0: No such file or directory
(   0.168|   0.000) D: [pulseaudio] alsa-mixer.c: Caching failure to open output:iec958-ac3-surround-51
(   0.168|   0.000) D: [pulseaudio] alsa-mixer.c: Skipping profile output:iec958-ac3-surround-51+input:analog-mono - will not be able to open output:iec958-ac3-surround-51
(   0.168|   0.000) D: [pulseaudio] alsa-mixer.c: Skipping profile output:iec958-ac3-surround-51+input:analog-stereo - will not be able to open output:iec958-ac3-surround-51
(   0.168|   0.000) D: [pulseaudio] alsa-mixer.c: Skipping profile output:iec958-ac3-surround-51+input:iec958-stereo - will not be able to open output:iec958-ac3-surround-51
(   0.168|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:iec958-dts-surround-51
(   0.168|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Surround 5.1 (IEC958/DTS) (iec958-dts-surround-51)
(   0.168|   0.000) D: [pulseaudio] alsa-util.c: Trying dca:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.168|   0.000) I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM dca:0
(   0.168|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device dca:0: No such file or directory
(   0.168|   0.000) D: [pulseaudio] alsa-mixer.c: Caching failure to open output:iec958-dts-surround-51
(   0.168|   0.000) D: [pulseaudio] alsa-mixer.c: Skipping profile output:iec958-dts-surround-51+input:analog-mono - will not be able to open output:iec958-dts-surround-51
(   0.168|   0.000) D: [pulseaudio] alsa-mixer.c: Skipping profile output:iec958-dts-surround-51+input:analog-stereo - will not be able to open output:iec958-dts-surround-51
(   0.168|   0.000) D: [pulseaudio] alsa-mixer.c: Skipping profile output:iec958-dts-surround-51+input:iec958-stereo - will not be able to open output:iec958-dts-surround-51
(   0.169|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:hdmi-stereo
(   0.169|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Stereo (HDMI) (hdmi-stereo)
(   0.169|   0.000) D: [pulseaudio] alsa-util.c: Trying hdmi:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.169|   0.000) I: [pulseaudio] (alsa-lib)conf.c: Unknown parameters 0
(   0.169|   0.000) I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM hdmi:0
(   0.169|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0: Invalid argument
(   0.169|   0.000) D: [pulseaudio] alsa-mixer.c: Caching failure to open output:hdmi-stereo
(   0.169|   0.000) D: [pulseaudio] alsa-mixer.c: Skipping profile output:hdmi-stereo+input:analog-mono - will not be able to open output:hdmi-stereo
(   0.169|   0.000) D: [pulseaudio] alsa-mixer.c: Skipping profile output:hdmi-stereo+input:analog-stereo - will not be able to open output:hdmi-stereo
(   0.169|   0.000) D: [pulseaudio] alsa-mixer.c: Skipping profile output:hdmi-stereo+input:iec958-stereo - will not be able to open output:hdmi-stereo
(   0.169|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:hdmi-surround
(   0.169|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Surround 5.1 (HDMI) (hdmi-surround)
(   0.169|   0.000) D: [pulseaudio] alsa-util.c: Trying hdmi:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.169|   0.000) I: [pulseaudio] (alsa-lib)conf.c: Unknown parameters 0
(   0.169|   0.000) I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM hdmi:0
(   0.169|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0: Invalid argument
(   0.169|   0.000) D: [pulseaudio] alsa-mixer.c: Caching failure to open output:hdmi-surround
(   0.169|   0.000) D: [pulseaudio] alsa-mixer.c: Skipping profile output:hdmi-surround+input:analog-mono - will not be able to open output:hdmi-surround
(   0.169|   0.000) D: [pulseaudio] alsa-mixer.c: Skipping profile output:hdmi-surround+input:analog-stereo - will not be able to open output:hdmi-surround
(   0.170|   0.000) D: [pulseaudio] alsa-mixer.c: Skipping profile output:hdmi-surround+input:iec958-stereo - will not be able to open output:hdmi-surround
(   0.170|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:hdmi-stereo-extra1
(   0.170|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Stereo (HDMI) (hdmi-stereo-extra1)
(   0.170|   0.000) D: [pulseaudio] alsa-util.c: Trying hdmi:0,1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.170|   0.000) I: [pulseaudio] (alsa-lib)conf.c: Unknown parameters 0,1
(   0.170|   0.000) I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM hdmi:0,1
(   0.170|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0,1: Invalid argument
(   0.170|   0.000) D: [pulseaudio] alsa-mixer.c: Caching failure to open output:hdmi-stereo-extra1
(   0.170|   0.000) D: [pulseaudio] alsa-mixer.c: Skipping profile output:hdmi-stereo-extra1+input:analog-mono - will not be able to open output:hdmi-stereo-extra1
(   0.170|   0.000) D: [pulseaudio] alsa-mixer.c: Skipping profile output:hdmi-stereo-extra1+input:analog-stereo - will not be able to open output:hdmi-stereo-extra1
(   0.170|   0.000) D: [pulseaudio] alsa-mixer.c: Skipping profile output:hdmi-stereo-extra1+input:iec958-stereo - will not be able to open output:hdmi-stereo-extra1
(   0.170|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:hdmi-surround-extra1
(   0.170|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Surround 5.1 (HDMI) (hdmi-surround-extra1)
(   0.170|   0.000) D: [pulseaudio] alsa-util.c: Trying hdmi:0,1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.170|   0.000) I: [pulseaudio] (alsa-lib)conf.c: Unknown parameters 0,1
(   0.170|   0.000) I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM hdmi:0,1
(   0.171|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0,1: Invalid argument
(   0.171|   0.000) D: [pulseaudio] alsa-mixer.c: Caching failure to open output:hdmi-surround-extra1
(   0.171|   0.000) D: [pulseaudio] alsa-mixer.c: Skipping profile output:hdmi-surround-extra1+input:analog-mono - will not be able to open output:hdmi-surround-extra1
(   0.171|   0.000) D: [pulseaudio] alsa-mixer.c: Skipping profile output:hdmi-surround-extra1+input:analog-stereo - will not be able to open output:hdmi-surround-extra1
(   0.171|   0.000) D: [pulseaudio] alsa-mixer.c: Skipping profile output:hdmi-surround-extra1+input:iec958-stereo - will not be able to open output:hdmi-surround-extra1
(   0.171|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:hdmi-stereo-extra2
(   0.171|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Stereo (HDMI) (hdmi-stereo-extra2)
(   0.171|   0.000) D: [pulseaudio] alsa-util.c: Trying hdmi:0,2 with SND_PCM_NO_AUTO_FORMAT ...
(   0.171|   0.000) I: [pulseaudio] (alsa-lib)conf.c: Unknown parameters 0,2
(   0.171|   0.000) I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM hdmi:0,2
(   0.171|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0,2: Invalid argument
(   0.171|   0.000) D: [pulseaudio] alsa-mixer.c: Caching failure to open output:hdmi-stereo-extra2
(   0.171|   0.000) D: [pulseaudio] alsa-mixer.c: Skipping profile output:hdmi-stereo-extra2+input:analog-mono - will not be able to open output:hdmi-stereo-extra2
(   0.171|   0.000) D: [pulseaudio] alsa-mixer.c: Skipping profile output:hdmi-stereo-extra2+input:analog-stereo - will not be able to open output:hdmi-stereo-extra2
(   0.171|   0.000) D: [pulseaudio] alsa-mixer.c: Skipping profile output:hdmi-stereo-extra2+input:iec958-stereo - will not be able to open output:hdmi-stereo-extra2
(   0.171|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:hdmi-surround-extra2
(   0.171|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Surround 5.1 (HDMI) (hdmi-surround-extra2)
(   0.171|   0.000) D: [pulseaudio] alsa-util.c: Trying hdmi:0,2 with SND_PCM_NO_AUTO_FORMAT ...
(   0.171|   0.000) I: [pulseaudio] (alsa-lib)conf.c: Unknown parameters 0,2
(   0.171|   0.000) I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM hdmi:0,2
(   0.172|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0,2: Invalid argument
(   0.172|   0.000) D: [pulseaudio] alsa-mixer.c: Caching failure to open output:hdmi-surround-extra2
(   0.172|   0.000) D: [pulseaudio] alsa-mixer.c: Skipping profile output:hdmi-surround-extra2+input:analog-mono - will not be able to open output:hdmi-surround-extra2
(   0.172|   0.000) D: [pulseaudio] alsa-mixer.c: Skipping profile output:hdmi-surround-extra2+input:analog-stereo - will not be able to open output:hdmi-surround-extra2
(   0.172|   0.000) D: [pulseaudio] alsa-mixer.c: Skipping profile output:hdmi-surround-extra2+input:iec958-stereo - will not be able to open output:hdmi-surround-extra2
(   0.172|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:hdmi-stereo-extra3
(   0.172|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Stereo (HDMI) (hdmi-stereo-extra3)
(   0.172|   0.000) D: [pulseaudio] alsa-util.c: Trying hdmi:0,3 with SND_PCM_NO_AUTO_FORMAT ...
(   0.172|   0.000) I: [pulseaudio] (alsa-lib)conf.c: Unknown parameters 0,3
(   0.172|   0.000) I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM hdmi:0,3
(   0.172|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0,3: Invalid argument
(   0.172|   0.000) D: [pulseaudio] alsa-mixer.c: Caching failure to open output:hdmi-stereo-extra3
(   0.172|   0.000) D: [pulseaudio] alsa-mixer.c: Skipping profile output:hdmi-stereo-extra3+input:analog-mono - will not be able to open output:hdmi-stereo-extra3
(   0.172|   0.000) D: [pulseaudio] alsa-mixer.c: Skipping profile output:hdmi-stereo-extra3+input:analog-stereo - will not be able to open output:hdmi-stereo-extra3
(   0.172|   0.000) D: [pulseaudio] alsa-mixer.c: Skipping profile output:hdmi-stereo-extra3+input:iec958-stereo - will not be able to open output:hdmi-stereo-extra3
(   0.173|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:hdmi-surround-extra3
(   0.173|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Surround 5.1 (HDMI) (hdmi-surround-extra3)
(   0.173|   0.000) D: [pulseaudio] alsa-util.c: Trying hdmi:0,3 with SND_PCM_NO_AUTO_FORMAT ...
(   0.173|   0.000) I: [pulseaudio] (alsa-lib)conf.c: Unknown parameters 0,3
(   0.173|   0.000) I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM hdmi:0,3
(   0.173|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0,3: Invalid argument
(   0.173|   0.000) D: [pulseaudio] alsa-mixer.c: Caching failure to open output:hdmi-surround-extra3
(   0.173|   0.000) D: [pulseaudio] alsa-mixer.c: Skipping profile output:hdmi-surround-extra3+input:analog-mono - will not be able to open output:hdmi-surround-extra3
(   0.173|   0.000) D: [pulseaudio] alsa-mixer.c: Skipping profile output:hdmi-surround-extra3+input:analog-stereo - will not be able to open output:hdmi-surround-extra3
(   0.173|   0.000) D: [pulseaudio] alsa-mixer.c: Skipping profile output:hdmi-surround-extra3+input:iec958-stereo - will not be able to open output:hdmi-surround-extra3
(   0.174|   0.001) D: [pulseaudio] alsa-mixer.c: Profile set 0x85f1150, auto_profiles=yes, probed=yes, n_mappings=2, n_profiles=5, n_decibel_fixes=0
(   0.175|   0.000) D: [pulseaudio] alsa-mixer.c: Mapping analog-stereo (Analog Stereo), priority=60, channel_map=front-left,front-right, supported=yes, direction=0
(   0.175|   0.000) D: [pulseaudio] alsa-mixer.c: Mapping iec958-stereo (Digital Stereo (IEC958)), priority=55, channel_map=front-left,front-right, supported=yes, direction=0
(   0.175|   0.000) D: [pulseaudio] alsa-mixer.c: Profile input:analog-stereo (Analog Stereo Input), priority=60, supported=yes n_input_mappings=1, n_output_mappings=0
(   0.175|   0.000) D: [pulseaudio] alsa-mixer.c: Input analog-stereo
(   0.175|   0.000) D: [pulseaudio] alsa-mixer.c: Profile output:analog-stereo (Analog Stereo Output), priority=6000, supported=yes n_input_mappings=0, n_output_mappings=1
(   0.175|   0.000) D: [pulseaudio] alsa-mixer.c: Output analog-stereo
(   0.175|   0.000) D: [pulseaudio] alsa-mixer.c: Profile output:analog-stereo+input:analog-stereo (Analog Stereo Duplex), priority=6060, supported=yes n_input_mappings=1, n_output_mappings=1
(   0.175|   0.000) D: [pulseaudio] alsa-mixer.c: Input analog-stereo
(   0.175|   0.000) D: [pulseaudio] alsa-mixer.c: Output analog-stereo
(   0.175|   0.000) D: [pulseaudio] alsa-mixer.c: Profile output:iec958-stereo (Digital Stereo (IEC958) Output), priority=5500, supported=yes n_input_mappings=0, n_output_mappings=1
(   0.175|   0.000) D: [pulseaudio] alsa-mixer.c: Output iec958-stereo
(   0.175|   0.000) D: [pulseaudio] alsa-mixer.c: Profile output:iec958-stereo+input:analog-stereo (Digital Stereo (IEC958) Output + Analog Stereo Input), priority=5560, supported=yes n_input_mappings=1, n_output_mappings=1
(   0.175|   0.000) D: [pulseaudio] alsa-mixer.c: Input analog-stereo
(   0.175|   0.000) D: [pulseaudio] alsa-mixer.c: Output iec958-stereo
(   0.176|   0.001) I: [pulseaudio] module-card-restore.c: Restoring port latency offsets for card alsa_card.pci-0000_00_1f.5.
(   0.177|   0.000) I: [pulseaudio] card.c: Created 0 "alsa_card.pci-0000_00_1f.5"
(   0.177|   0.000) D: [pulseaudio] module-alsa-card.c: Found 0 jacks.
(   0.177|   0.000) D: [pulseaudio] alsa-extcon.c: Cannot open '/sys/class/switch/h2w/state'. Skipping.
(   0.179|   0.001) D: [pulseaudio] reserve-wrap.c: Successfully create reservation lock monitor for device 'Audio0'
(   0.179|   0.000) D: [pulseaudio] alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.180|   0.001) D: [pulseaudio] alsa-util.c: Managed to open front:0
(   0.180|   0.000) I: [pulseaudio] alsa-util.c: cannot disable ALSA period wakeups
(   0.180|   0.000) D: [pulseaudio] alsa-util.c: Maximum hw buffer size is 371 ms
(   0.181|   0.000) D: [pulseaudio] alsa-util.c: Set buffer size first (to 88200 samples), period size second (to 88200 samples).
(   0.181|   0.000) I: [pulseaudio] alsa-util.c: ALSA period wakeups were not disabled
(   0.181|   0.000) I: [pulseaudio] alsa-sink.c: Successfully opened device front:0.
(   0.181|   0.000) I: [pulseaudio] alsa-sink.c: Selected mapping 'Analog Stereo' (analog-stereo).
(   0.181|   0.000) I: [pulseaudio] alsa-sink.c: Successfully enabled mmap() mode.
(   0.181|   0.000) I: [pulseaudio] alsa-sink.c: Successfully enabled timer-based scheduling mode.
(   0.181|   0.000) I: [pulseaudio] (alsa-lib)control.c: Invalid CTL front:0
(   0.181|   0.000) I: [pulseaudio] alsa-util.c: Unable to attach to mixer front:0: No such file or directory
(   0.182|   0.001) I: [pulseaudio] alsa-util.c: Successfully attached to mixer 'hw:0'
(   0.184|   0.001) D: [pulseaudio] alsa-mixer.c: Added 2 ports
(   0.185|   0.000) I: [pulseaudio] sink.c: Created sink 0 "alsa_output.pci-0000_00_1f.5.analog-stereo" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
(   0.185|   0.000) I: [pulseaudio] sink.c:     alsa.resolution_bits = "16"
(   0.185|   0.000) I: [pulseaudio] sink.c:     device.api = "alsa"
(   0.185|   0.000) I: [pulseaudio] sink.c:     device.class = "sound"
(   0.185|   0.000) I: [pulseaudio] sink.c:     alsa.class = "generic"
(   0.185|   0.000) I: [pulseaudio] sink.c:     alsa.subclass = "generic-mix"
(   0.185|   0.000) I: [pulseaudio] sink.c:     alsa.name = "Intel 82801DB-ICH4"
(   0.185|   0.000) I: [pulseaudio] sink.c:     alsa.id = "Intel ICH"
(   0.185|   0.000) I: [pulseaudio] sink.c:     alsa.subdevice = "0"
(   0.185|   0.000) I: [pulseaudio] sink.c:     alsa.subdevice_name = "subdevice #0"
(   0.185|   0.000) I: [pulseaudio] sink.c:     alsa.device = "0"
(   0.185|   0.000) I: [pulseaudio] sink.c:     alsa.card = "0"
(   0.185|   0.000) I: [pulseaudio] sink.c:     alsa.card_name = "Intel 82801DB-ICH4"
(   0.185|   0.000) I: [pulseaudio] sink.c:     alsa.long_card_name = "Intel 82801DB-ICH4 with STAC9752,53 at irq 10"
(   0.185|   0.000) I: [pulseaudio] sink.c:     alsa.driver_name = "snd_intel8x0"
(   0.185|   0.000) I: [pulseaudio] sink.c:     device.bus_path = "pci-0000:00:1f.5"
(   0.185|   0.000) I: [pulseaudio] sink.c:     sysfs.path = "/devices/pci0000:00/0000:00:1f.5/sound/card0"
(   0.185|   0.000) I: [pulseaudio] sink.c:     device.bus = "pci"
(   0.185|   0.000) I: [pulseaudio] sink.c:     device.vendor.id = "8086"
(   0.185|   0.000) I: [pulseaudio] sink.c:     device.vendor.name = "Intel Corporation"
(   0.185|   0.000) I: [pulseaudio] sink.c:     device.product.id = "24c5"
(   0.185|   0.000) I: [pulseaudio] sink.c:     device.product.name = "82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller"
(   0.185|   0.000) I: [pulseaudio] sink.c:     device.form_factor = "internal"
(   0.185|   0.000) I: [pulseaudio] sink.c:     device.string = "front:0"
(   0.185|   0.000) I: [pulseaudio] sink.c:     device.buffering.buffer_size = "65536"
(   0.185|   0.000) I: [pulseaudio] sink.c:     device.buffering.fragment_size = "65536"
(   0.185|   0.000) I: [pulseaudio] sink.c:     device.access_mode = "mmap+timer"
(   0.185|   0.000) I: [pulseaudio] sink.c:     device.profile.name = "analog-stereo"
(   0.185|   0.000) I: [pulseaudio] sink.c:     device.profile.description = "Analog Stereo"
(   0.185|   0.000) I: [pulseaudio] sink.c:     device.description = "Built-in Audio Analog Stereo"
(   0.185|   0.000) I: [pulseaudio] sink.c:     alsa.mixer_name = "SigmaTel STAC9752,53"
(   0.185|   0.000) I: [pulseaudio] sink.c:     alsa.components = "AC97a:83847652"
(   0.185|   0.000) I: [pulseaudio] sink.c:     module-udev-detect.discovered = "1"
(   0.185|   0.000) I: [pulseaudio] sink.c:     device.icon_name = "audio-card-pci"
(   0.186|   0.001) D: [pulseaudio] core-subscribe.c: Dropped redundant event due to change event.
(   0.186|   0.000) I: [pulseaudio] source.c: Created source 0 "alsa_output.pci-0000_00_1f.5.analog-stereo.monitor" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
(   0.186|   0.000) I: [pulseaudio] source.c:     device.description = "Monitor of Built-in Audio Analog Stereo"
(   0.186|   0.000) I: [pulseaudio] source.c:     device.class = "monitor"
(   0.186|   0.000) I: [pulseaudio] source.c:     alsa.card = "0"
(   0.186|   0.000) I: [pulseaudio] source.c:     alsa.card_name = "Intel 82801DB-ICH4"
(   0.186|   0.000) I: [pulseaudio] source.c:     alsa.long_card_name = "Intel 82801DB-ICH4 with STAC9752,53 at irq 10"
(   0.186|   0.000) I: [pulseaudio] source.c:     alsa.driver_name = "snd_intel8x0"
(   0.186|   0.000) I: [pulseaudio] source.c:     device.bus_path = "pci-0000:00:1f.5"
(   0.186|   0.000) I: [pulseaudio] source.c:     sysfs.path = "/devices/pci0000:00/0000:00:1f.5/sound/card0"
(   0.186|   0.000) I: [pulseaudio] source.c:     device.bus = "pci"
(   0.186|   0.000) I: [pulseaudio] source.c:     device.vendor.id = "8086"
(   0.186|   0.000) I: [pulseaudio] source.c:     device.vendor.name = "Intel Corporation"
(   0.186|   0.000) I: [pulseaudio] source.c:     device.product.id = "24c5"
(   0.186|   0.000) I: [pulseaudio] source.c:     device.product.name = "82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller"
(   0.186|   0.000) I: [pulseaudio] source.c:     device.form_factor = "internal"
(   0.186|   0.000) I: [pulseaudio] source.c:     device.string = "0"
(   0.186|   0.000) I: [pulseaudio] source.c:     module-udev-detect.discovered = "1"
(   0.186|   0.000) I: [pulseaudio] source.c:     device.icon_name = "audio-card-pci"
(   0.187|   0.000) I: [pulseaudio] alsa-sink.c: Using 1.0 fragments of size 65536 bytes (371.52ms), buffer size is 65536 bytes (371.52ms)
(   0.187|   0.000) I: [pulseaudio] alsa-sink.c: Time scheduling watermark is 20.00ms
(   0.187|   0.000) D: [pulseaudio] alsa-sink.c: hwbuf_unused=0
(   0.187|   0.000) D: [pulseaudio] alsa-sink.c: setting avail_min=15502
(   0.187|   0.000) D: [pulseaudio] alsa-mixer.c: Activating path analog-output-headphones
(   0.187|   0.000) D: [pulseaudio] alsa-mixer.c: Path analog-output-headphones (Headphones), direction=1, priority=90, probed=yes, supported=yes, has_mute=yes, has_volume=yes, has_dB=yes, min_volume=0, max_volume=31, min_dB=-127.5, max_dB=12
(   0.187|   0.000) D: [pulseaudio] alsa-mixer.c: Element Master, direction=1, switch=1, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
(   0.187|   0.000) D: [pulseaudio] alsa-mixer.c: Element Master Mono, direction=1, switch=2, volume=2, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x7ffffffffffff, n_channels=1, override_map=no
(   0.187|   0.000) D: [pulseaudio] alsa-mixer.c: Element Headphone, direction=1, switch=1, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=4, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
(   0.187|   0.000) D: [pulseaudio] alsa-mixer.c: Element PCM, direction=1, switch=1, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
(   0.188|   0.000) D: [pulseaudio] alsa-mixer.c: Element External Amplifier, direction=1, switch=4, volume=0, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x0, n_channels=0, override_map=no
(   0.188|   0.000) D: [pulseaudio] alsa-mixer.c: Option on (output-amplifier-on/Amplifier) index=1, priority=10
(   0.188|   0.000) D: [pulseaudio] alsa-mixer.c: Option off (output-amplifier-off/No Amplifier) index=0, priority=0
(   0.188|   0.000) D: [pulseaudio] alsa-mixer.c: Element IEC958, direction=1, switch=2, volume=0, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x0, n_channels=0, override_map=no
(   0.188|   0.000) D: [pulseaudio] alsa-mixer.c: Jack Front Headphone, alsa_name='Front Headphone Jack', detection unavailable
(   0.188|   0.000) D: [pulseaudio] alsa-mixer.c: Jack Front Headphone Phantom, alsa_name='Front Headphone Phantom Jack', detection unavailable
(   0.188|   0.000) D: [pulseaudio] alsa-mixer.c: Jack Headphone, alsa_name='Headphone Jack', detection unavailable
(   0.188|   0.000) D: [pulseaudio] alsa-mixer.c: Jack Headphone Phantom, alsa_name='Headphone Phantom Jack', detection unavailable
(   0.188|   0.000) D: [pulseaudio] alsa-mixer.c: Jack Headphone Mic, alsa_name='Headphone Mic Jack', detection unavailable
(   0.188|   0.000) D: [pulseaudio] alsa-mixer.c: Setting output-amplifier-on (Amplifier) priority=10
(   0.188|   0.000) D: [pulseaudio] alsa-mixer.c: Setting output-amplifier-off (No Amplifier) priority=0
(   0.188|   0.000) I: [pulseaudio] alsa-sink.c: Successfully enabled deferred volume.
(   0.188|   0.000) I: [pulseaudio] alsa-sink.c: Hardware volume ranges from -127.50 dB to 12.00 dB.
(   0.188|   0.000) I: [pulseaudio] alsa-sink.c: Fixing base volume to -12.00 dB
(   0.188|   0.000) I: [pulseaudio] alsa-sink.c: Using hardware volume control. Hardware dB scale supported.
(   0.188|   0.000) I: [pulseaudio] alsa-sink.c: Using hardware mute control.
(   0.188|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_dump():
(   0.188|   0.000) D: [pulseaudio] alsa-util.c: Hardware PCM card 0 'Intel 82801DB-ICH4' device 0 subdevice 0
(   0.188|   0.000) D: [pulseaudio] alsa-util.c: Its setup is:
(   0.188|   0.000) D: [pulseaudio] alsa-util.c:   stream       : PLAYBACK
(   0.188|   0.000) D: [pulseaudio] alsa-util.c:   access       : MMAP_INTERLEAVED
(   0.188|   0.000) D: [pulseaudio] alsa-util.c:   format       : S16_LE
(   0.188|   0.000) D: [pulseaudio] alsa-util.c:   subformat    : STD
(   0.188|   0.000) D: [pulseaudio] alsa-util.c:   channels     : 2
(   0.188|   0.000) D: [pulseaudio] alsa-util.c:   rate         : 44100
(   0.188|   0.000) D: [pulseaudio] alsa-util.c:   exact rate   : 44100 (44100/1)
(   0.188|   0.000) D: [pulseaudio] alsa-util.c:   msbits       : 16
(   0.188|   0.000) D: [pulseaudio] alsa-util.c:   buffer_size  : 16384
(   0.188|   0.000) D: [pulseaudio] alsa-util.c:   period_size  : 16384
(   0.188|   0.000) D: [pulseaudio] alsa-util.c:   period_time  : 371519
(   0.188|   0.000) D: [pulseaudio] alsa-util.c:   tstamp_mode  : ENABLE
(   0.188|   0.000) D: [pulseaudio] alsa-util.c:   period_step  : 1
(   0.188|   0.000) D: [pulseaudio] alsa-util.c:   avail_min    : 16384
(   0.188|   0.000) D: [pulseaudio] alsa-util.c:   period_event : 0
(   0.188|   0.000) D: [pulseaudio] alsa-util.c:   start_threshold  : -1
(   0.188|   0.000) D: [pulseaudio] alsa-util.c:   stop_threshold   : 1073741824
(   0.188|   0.000) D: [pulseaudio] alsa-util.c:   silence_threshold: 0
(   0.188|   0.000) D: [pulseaudio] alsa-util.c:   silence_size : 0
(   0.188|   0.000) D: [pulseaudio] alsa-util.c:   boundary     : 1073741824
(   0.188|   0.000) D: [pulseaudio] alsa-util.c:   appl_ptr     : 0
(   0.188|   0.000) D: [pulseaudio] alsa-util.c:   hw_ptr       : 0
(   0.189|   0.000) D: [pulseaudio] alsa-sink.c: Read hardware volume: 0: 100% 1: 100%
(   0.190|   0.000) D: [pulseaudio] alsa-sink.c:                in dB: 0: 0.00 dB 1: 0.00 dB
(   0.190|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Thread starting up
(   0.208|   0.017) D: [alsa-sink-Intel ICH] core-util.c: RealtimeKit worked.
(   0.208|   0.000) I: [alsa-sink-Intel ICH] core-util.c: Successfully enabled SCHED_RR scheduling for thread, with priority 5.
(   0.208|   0.000) I: [alsa-sink-Intel ICH] alsa-sink.c: Starting playback.
(   0.208|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Cutting sleep time for the initial iterations by half.
(   0.209|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Cutting sleep time for the initial iterations by half.
(   0.209|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Cutting sleep time for the initial iterations by half.
(   0.209|   0.000) D: [pulseaudio] module-device-restore.c: Could not set format on sink alsa_output.pci-0000_00_1f.5.analog-stereo
(   0.210|   0.000) D: [pulseaudio] alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.211|   0.001) D: [pulseaudio] alsa-util.c: Managed to open front:0
(   0.211|   0.000) I: [pulseaudio] alsa-util.c: cannot disable ALSA period wakeups
(   0.211|   0.000) D: [pulseaudio] alsa-util.c: Maximum hw buffer size is 371 ms
(   0.212|   0.000) D: [pulseaudio] alsa-util.c: Set buffer size first (to 88200 samples), period size second (to 88200 samples).
(   0.212|   0.000) I: [pulseaudio] alsa-util.c: ALSA period wakeups were not disabled
(   0.212|   0.000) I: [pulseaudio] alsa-source.c: Successfully opened device front:0.
(   0.212|   0.000) I: [pulseaudio] alsa-source.c: Selected mapping 'Analog Stereo' (analog-stereo).
(   0.212|   0.000) I: [pulseaudio] alsa-source.c: Successfully enabled mmap() mode.
(   0.212|   0.000) I: [pulseaudio] alsa-source.c: Successfully enabled timer-based scheduling mode.
(   0.212|   0.000) I: [pulseaudio] (alsa-lib)control.c: Invalid CTL front:0
(   0.212|   0.000) I: [pulseaudio] alsa-util.c: Unable to attach to mixer front:0: No such file or directory
(   0.213|   0.001) I: [pulseaudio] alsa-util.c: Successfully attached to mixer 'hw:0'
(   0.218|   0.004) D: [pulseaudio] alsa-mixer.c: Added 5 ports
(   0.218|   0.000) D: [pulseaudio] core-subscribe.c: Dropped redundant event due to change event.
(   0.218|   0.000) I: [pulseaudio] source.c: Created source 1 "alsa_input.pci-0000_00_1f.5.analog-stereo" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
(   0.218|   0.000) I: [pulseaudio] source.c:     alsa.resolution_bits = "16"
(   0.218|   0.000) I: [pulseaudio] source.c:     device.api = "alsa"
(   0.218|   0.000) I: [pulseaudio] source.c:     device.class = "sound"
(   0.218|   0.000) I: [pulseaudio] source.c:     alsa.class = "generic"
(   0.218|   0.000) I: [pulseaudio] source.c:     alsa.subclass = "generic-mix"
(   0.218|   0.000) I: [pulseaudio] source.c:     alsa.name = "Intel 82801DB-ICH4"
(   0.218|   0.000) I: [pulseaudio] source.c:     alsa.id = "Intel ICH"
(   0.218|   0.000) I: [pulseaudio] source.c:     alsa.subdevice = "0"
(   0.218|   0.000) I: [pulseaudio] source.c:     alsa.subdevice_name = "subdevice #0"
(   0.218|   0.000) I: [pulseaudio] source.c:     alsa.device = "0"
(   0.218|   0.000) I: [pulseaudio] source.c:     alsa.card = "0"
(   0.218|   0.000) I: [pulseaudio] source.c:     alsa.card_name = "Intel 82801DB-ICH4"
(   0.218|   0.000) I: [pulseaudio] source.c:     alsa.long_card_name = "Intel 82801DB-ICH4 with STAC9752,53 at irq 10"
(   0.218|   0.000) I: [pulseaudio] source.c:     alsa.driver_name = "snd_intel8x0"
(   0.218|   0.000) I: [pulseaudio] source.c:     device.bus_path = "pci-0000:00:1f.5"
(   0.218|   0.000) I: [pulseaudio] source.c:     sysfs.path = "/devices/pci0000:00/0000:00:1f.5/sound/card0"
(   0.218|   0.000) I: [pulseaudio] source.c:     device.bus = "pci"
(   0.218|   0.000) I: [pulseaudio] source.c:     device.vendor.id = "8086"
(   0.218|   0.000) I: [pulseaudio] source.c:     device.vendor.name = "Intel Corporation"
(   0.218|   0.000) I: [pulseaudio] source.c:     device.product.id = "24c5"
(   0.218|   0.000) I: [pulseaudio] source.c:     device.product.name = "82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller"
(   0.218|   0.000) I: [pulseaudio] source.c:     device.form_factor = "internal"
(   0.218|   0.000) I: [pulseaudio] source.c:     device.string = "front:0"
(   0.218|   0.000) I: [pulseaudio] source.c:     device.buffering.buffer_size = "65536"
(   0.218|   0.000) I: [pulseaudio] source.c:     device.buffering.fragment_size = "65536"
(   0.218|   0.000) I: [pulseaudio] source.c:     device.access_mode = "mmap+timer"
(   0.218|   0.000) I: [pulseaudio] source.c:     device.profile.name = "analog-stereo"
(   0.218|   0.000) I: [pulseaudio] source.c:     device.profile.description = "Analog Stereo"
(   0.218|   0.000) I: [pulseaudio] source.c:     device.description = "Built-in Audio Analog Stereo"
(   0.218|   0.000) I: [pulseaudio] source.c:     alsa.mixer_name = "SigmaTel STAC9752,53"
(   0.218|   0.000) I: [pulseaudio] source.c:     alsa.components = "AC97a:83847652"
(   0.218|   0.000) I: [pulseaudio] source.c:     module-udev-detect.discovered = "1"
(   0.218|   0.000) I: [pulseaudio] source.c:     device.icon_name = "audio-card-pci"
(   0.219|   0.000) I: [pulseaudio] alsa-source.c: Using 1.0 fragments of size 65536 bytes (371.52ms), buffer size is 65536 bytes (371.52ms)
(   0.219|   0.000) I: [pulseaudio] alsa-source.c: Time scheduling watermark is 20.00ms
(   0.219|   0.000) D: [pulseaudio] alsa-source.c: hwbuf_unused=0
(   0.219|   0.000) D: [pulseaudio] alsa-source.c: setting avail_min=15502
(   0.219|   0.000) D: [pulseaudio] alsa-mixer.c: Activating path analog-input-microphone
(   0.219|   0.000) D: [pulseaudio] alsa-mixer.c: Path analog-input-microphone (Microphone), direction=2, priority=87, probed=yes, supported=yes, has_mute=yes, has_volume=yes, has_dB=yes, min_volume=0, max_volume=15, min_dB=0, max_dB=22.5
(   0.220|   0.000) D: [pulseaudio] alsa-mixer.c: Element Mic, direction=2, switch=1, volume=0, volume_limit=-1, enumeration=0, required=0, required_any=4, required_absent=0, mask=0x0, n_channels=0, override_map=yes
(   0.220|   0.000) D: [pulseaudio] alsa-mixer.c: Element Capture, direction=2, switch=1, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
(   0.220|   0.000) D: [pulseaudio] alsa-mixer.c: Element Mic Select, direction=2, switch=0, volume=0, volume_limit=-1, enumeration=1, required=0, required_any=0, required_absent=0, mask=0x0, n_channels=0, override_map=no
(   0.220|   0.000) D: [pulseaudio] alsa-mixer.c: Option Mic1 (input-microphone-1/Microphone 1) index=0, priority=20
(   0.220|   0.000) D: [pulseaudio] alsa-mixer.c: Option Mic2 (input-microphone-2/Microphone 2) index=1, priority=19
(   0.220|   0.000) D: [pulseaudio] alsa-mixer.c: Element Line, direction=2, switch=2, volume=0, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x0, n_channels=0, override_map=no
(   0.220|   0.000) D: [pulseaudio] alsa-mixer.c: Element Aux, direction=2, switch=2, volume=0, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x0, n_channels=0, override_map=no
(   0.220|   0.000) D: [pulseaudio] alsa-mixer.c: Element Video, direction=2, switch=2, volume=0, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x0, n_channels=0, override_map=no
(   0.220|   0.000) D: [pulseaudio] alsa-mixer.c: Jack Mic, alsa_name='Mic Jack', detection unavailable
(   0.220|   0.000) D: [pulseaudio] alsa-mixer.c: Jack Mic Phantom, alsa_name='Mic Phantom Jack', detection unavailable
(   0.220|   0.000) D: [pulseaudio] alsa-mixer.c: Setting input-microphone-1 (Microphone 1) priority=20
(   0.220|   0.000) D: [pulseaudio] alsa-mixer.c: Setting input-microphone-2 (Microphone 2) priority=19
(   0.220|   0.000) I: [pulseaudio] alsa-source.c: Successfully enabled deferred volume.
(   0.220|   0.000) I: [pulseaudio] alsa-source.c: Hardware volume ranges from 0.00 dB to 22.50 dB.
(   0.220|   0.000) I: [pulseaudio] alsa-source.c: Fixing base volume to -22.50 dB
(   0.220|   0.000) I: [pulseaudio] alsa-source.c: Using hardware volume control. Hardware dB scale supported.
(   0.220|   0.000) I: [pulseaudio] alsa-source.c: Using hardware mute control.
(   0.220|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_dump():
(   0.220|   0.000) D: [pulseaudio] alsa-util.c: Hardware PCM card 0 'Intel 82801DB-ICH4' device 0 subdevice 0
(   0.220|   0.000) D: [pulseaudio] alsa-util.c: Its setup is:
(   0.220|   0.000) D: [pulseaudio] alsa-util.c:   stream       : CAPTURE
(   0.220|   0.000) D: [pulseaudio] alsa-util.c:   access       : MMAP_INTERLEAVED
(   0.220|   0.000) D: [pulseaudio] alsa-util.c:   format       : S16_LE
(   0.220|   0.000) D: [pulseaudio] alsa-util.c:   subformat    : STD
(   0.220|   0.000) D: [pulseaudio] alsa-util.c:   channels     : 2
(   0.220|   0.000) D: [pulseaudio] alsa-util.c:   rate         : 44100
(   0.220|   0.000) D: [pulseaudio] alsa-util.c:   exact rate   : 44100 (44100/1)
(   0.220|   0.000) D: [pulseaudio] alsa-util.c:   msbits       : 16
(   0.220|   0.000) D: [pulseaudio] alsa-util.c:   buffer_size  : 16384
(   0.220|   0.000) D: [pulseaudio] alsa-util.c:   period_size  : 16384
(   0.220|   0.000) D: [pulseaudio] alsa-util.c:   period_time  : 371519
(   0.220|   0.000) D: [pulseaudio] alsa-util.c:   tstamp_mode  : ENABLE
(   0.220|   0.000) D: [pulseaudio] alsa-util.c:   period_step  : 1
(   0.220|   0.000) D: [pulseaudio] alsa-util.c:   avail_min    : 16384
(   0.220|   0.000) D: [pulseaudio] alsa-util.c:   period_event : 0
(   0.220|   0.000) D: [pulseaudio] alsa-util.c:   start_threshold  : -1
(   0.220|   0.000) D: [pulseaudio] alsa-util.c:   stop_threshold   : 1073741824
(   0.220|   0.000) D: [pulseaudio] alsa-util.c:   silence_threshold: 0
(   0.220|   0.000) D: [pulseaudio] alsa-util.c:   silence_size : 0
(   0.220|   0.000) D: [pulseaudio] alsa-util.c:   boundary     : 1073741824
(   0.220|   0.000) D: [pulseaudio] alsa-util.c:   appl_ptr     : 0
(   0.220|   0.000) D: [pulseaudio] alsa-util.c:   hw_ptr       : 0
(   0.221|   0.000) D: [pulseaudio] alsa-source.c: Read hardware volume: 0:  42% 1:  42%
(   0.221|   0.000) D: [pulseaudio] alsa-source.c:                in dB: 0: -22.50 dB 1: -22.50 dB
(   0.221|   0.000) D: [alsa-source-Intel ICH] alsa-source.c: Thread starting up
(   0.232|   0.011) D: [alsa-source-Intel ICH] core-util.c: RealtimeKit worked.
(   0.233|   0.000) I: [alsa-source-Intel ICH] core-util.c: Successfully enabled SCHED_RR scheduling for thread, with priority 5.
(   0.233|   0.000) I: [alsa-source-Intel ICH] alsa-source.c: Starting capture.
(   0.233|   0.000) I: [pulseaudio] module.c: Loaded "module-alsa-card" (index: #5; argument: "device_id="0" name="pci-0000_00_1f.5" card_name="alsa_card.pci-0000_00_1f.5" namereg_fail=false tsched=yes fixed_latency_range=no ignore_dB=no deferred_volume=yes use_ucm=yes card_properties="module-udev-detect.discovered=1"").
(   0.233|   0.000) I: [pulseaudio] module-udev-detect.c: Card /devices/pci0000:00/0000:00:1f.5/sound/card0 (alsa_card.pci-0000_00_1f.5) module loaded.
(   0.233|   0.000) I: [pulseaudio] module-udev-detect.c: Found 1 cards.
(   0.233|   0.000) I: [pulseaudio] module.c: Loaded "module-udev-detect" (index: #6; argument: "").
(   0.233|   0.000) D: [pulseaudio] cli-command.c: Checking for existence of '/usr/lib/pulse-4.0/modules/module-android-audio-hal.so': failure
(   0.233|   0.000) D: [pulseaudio] cli-command.c: Checking for existence of '/usr/lib/pulse-4.0/modules/module-jackdbus-detect.so': failure
(   0.233|   0.000) D: [pulseaudio] cli-command.c: Checking for existence of '/usr/lib/pulse-4.0/modules/module-bluetooth-policy.so': failure
(   0.233|   0.000) D: [pulseaudio] cli-command.c: Checking for existence of '/usr/lib/pulse-4.0/modules/module-bluetooth-discover.so': failure
(   0.233|   0.000) D: [pulseaudio] cli-command.c: Checking for existence of '/usr/lib/pulse-4.0/modules/module-esound-protocol-unix.so': failure
(   0.234|   0.001) I: [pulseaudio] module.c: Loaded "module-native-protocol-unix" (index: #7; argument: "").
(   0.235|   0.000) D: [pulseaudio] cli-command.c: Checking for existence of '/usr/lib/pulse-4.0/modules/module-gconf.so': failure
(   0.235|   0.000) D: [pulseaudio] core-subscribe.c: Dropped redundant event due to change event.
(   0.235|   0.000) I: [pulseaudio] module-default-device-restore.c: Restored default sink 'alsa_output.pci-0000_00_1f.5.analog-stereo'.
(   0.235|   0.000) D: [pulseaudio] core-subscribe.c: Dropped redundant event due to change event.
(   0.236|   0.000) I: [pulseaudio] module-default-device-restore.c: Restored default source 'alsa_input.pci-0000_00_1f.5.analog-stereo'.
(   0.236|   0.000) I: [pulseaudio] module.c: Loaded "module-default-device-restore" (index: #8; argument: "").
(   0.236|   0.000) I: [pulseaudio] module.c: Loaded "module-rescue-streams" (index: #9; argument: "").
(   0.237|   0.000) I: [pulseaudio] module.c: Loaded "module-always-sink" (index: #10; argument: "").
(   0.237|   0.000) I: [pulseaudio] module.c: Loaded "module-intended-roles" (index: #11; argument: "").
(   0.238|   0.000) D: [pulseaudio] module-suspend-on-idle.c: Sink alsa_output.pci-0000_00_1f.5.analog-stereo becomes idle, timeout in 5 seconds.
(   0.238|   0.000) D: [pulseaudio] module-suspend-on-idle.c: Source alsa_input.pci-0000_00_1f.5.analog-stereo becomes idle, timeout in 5 seconds.
(   0.238|   0.000) I: [pulseaudio] module.c: Loaded "module-suspend-on-idle" (index: #12; argument: "").
(   0.241|   0.003) D: [pulseaudio] cli-command.c: Checking for existence of '/usr/lib/pulse-4.0/modules/module-console-kit.so': failure
(   0.241|   0.000) D: [pulseaudio] cli-command.c: Checking for existence of '/usr/lib/pulse-4.0/modules/module-systemd-login.so': success
(   0.243|   0.001) I: [pulseaudio] client.c: Created 0 "Login Session c1"
(   0.243|   0.000) D: [pulseaudio] module-systemd-login.c: Added new session c1
(   0.243|   0.000) I: [pulseaudio] module.c: Loaded "module-systemd-login" (index: #13; argument: "").
(   0.244|   0.000) I: [pulseaudio] module.c: Loaded "module-position-event-sounds" (index: #14; argument: "").
(   0.245|   0.000) I: [pulseaudio] module.c: Loaded "module-filter-heuristics" (index: #15; argument: "").
(   0.245|   0.000) I: [pulseaudio] module.c: Loaded "module-filter-apply" (index: #16; argument: "").
(   0.247|   0.001) D: [pulseaudio] main.c: Got org.PulseAudio1!
(   0.250|   0.002) D: [pulseaudio] main.c: Got org.pulseaudio.Server!
(   0.250|   0.000) I: [pulseaudio] main.c: Daemon startup complete.
(   0.251|   0.000) I: [pulseaudio] client.c: Created 1 "Native client (UNIX socket client)"
(   0.251|   0.000) D: [pulseaudio] module-udev-detect.c: /dev/snd/controlC0 is accessible: yes
(   0.251|   0.000) D: [pulseaudio] module-udev-detect.c: Resuming all sinks and sources of card alsa_card.pci-0000_00_1f.5.
(   0.251|   0.000) D: [pulseaudio] protocol-native.c: Protocol version: remote 28, local 28
(   0.251|   0.000) I: [pulseaudio] protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
(   0.251|   0.000) D: [pulseaudio] protocol-native.c: SHM possible: yes
(   0.251|   0.000) D: [pulseaudio] protocol-native.c: Negotiated SHM: yes
(   0.253|   0.001) D: [pulseaudio] module-augment-properties.c: Looking for .desktop file for indicator-sound-service
(   0.256|   0.002) D: [alsa-sink-Intel ICH] alsa-sink.c: Cutting sleep time for the initial iterations by half.
(   0.256|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Cutting sleep time for the initial iterations by half.
(   0.256|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Cutting sleep time for the initial iterations by half.
(   0.256|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Cutting sleep time for the initial iterations by half.
(   0.952|   0.695) D: [alsa-sink-Intel ICH] alsa-sink.c: Wakeup from ALSA!
(   0.952|   0.000) I: [alsa-sink-Intel ICH] alsa-sink.c: Underrun!
(   0.952|   0.000) I: [alsa-sink-Intel ICH] alsa-sink.c: Increasing wakeup watermark to 30.00 ms
(   1.695|   0.743) D: [alsa-sink-Intel ICH] alsa-sink.c: Wakeup from ALSA!
(   1.695|   0.000) I: [alsa-sink-Intel ICH] alsa-sink.c: Underrun!
(   1.695|   0.000) I: [alsa-sink-Intel ICH] alsa-sink.c: Increasing wakeup watermark to 40.00 ms
(   3.182|   1.486) I: [alsa-sink-Intel ICH] alsa-sink.c: Increasing wakeup watermark to 50.00 ms
(   3.925|   0.743) I: [alsa-sink-Intel ICH] alsa-sink.c: Increasing wakeup watermark to 60.00 ms
(   3.950|   0.024) I: [alsa-source-Intel ICH] alsa-source.c: Increasing wakeup watermark to 30.00 ms
(   4.693|   0.743) I: [alsa-source-Intel ICH] alsa-source.c: Increasing wakeup watermark to 40.00 ms
(   5.040|   0.347) I: [alsa-sink-Intel ICH] alsa-sink.c: Increasing wakeup watermark to 70.00 ms
(   5.242|   0.202) I: [pulseaudio] module-suspend-on-idle.c: Source alsa_input.pci-0000_00_1f.5.analog-stereo idle for too long, suspending ...
(   5.242|   0.000) D: [pulseaudio] source.c: Suspend cause of source alsa_input.pci-0000_00_1f.5.analog-stereo is 0x0004, suspending
(   5.243|   0.000) I: [alsa-source-Intel ICH] alsa-source.c: Device suspended...
(   5.243|   0.000) D: [pulseaudio] core.c: Hmm, no streams around, trying to vacuum.
(   5.243|   0.000) I: [pulseaudio] module-suspend-on-idle.c: Sink alsa_output.pci-0000_00_1f.5.analog-stereo idle for too long, suspending ...
(   5.243|   0.000) D: [pulseaudio] sink.c: Suspend cause of sink alsa_output.pci-0000_00_1f.5.analog-stereo is 0x0004, suspending
(   5.245|   0.001) I: [alsa-sink-Intel ICH] alsa-sink.c: Device suspended...
(   5.245|   0.000) D: [pulseaudio] core.c: Hmm, no streams around, trying to vacuum.
(   5.246|   0.000) D: [pulseaudio] module-udev-detect.c: /dev/snd/controlC0 is accessible: yes
(   5.246|   0.000) D: [pulseaudio] module-udev-detect.c: Resuming all sinks and sources of card alsa_card.pci-0000_00_1f.5.
(  67.836|  62.590) I: [pulseaudio] client.c: Created 2 "Native client (UNIX socket client)"
(  67.842|   0.006) I: [pulseaudio] client.c: Freed 2 "Native client (UNIX socket client)"
(  67.842|   0.000) I: [pulseaudio] protocol-native.c: Connection died.
(  67.857|   0.014) I: [pulseaudio] client.c: Created 3 "Native client (UNIX socket client)"
(  67.862|   0.005) D: [pulseaudio] protocol-native.c: Protocol version: remote 28, local 28
(  67.862|   0.000) I: [pulseaudio] protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
(  67.862|   0.000) D: [pulseaudio] protocol-native.c: SHM possible: yes
(  67.863|   0.000) D: [pulseaudio] protocol-native.c: Negotiated SHM: yes
(  67.865|   0.002) D: [pulseaudio] module-augment-properties.c: Looking for .desktop file for plugin-container
(  67.866|   0.001) D: [pulseaudio] module-intended-roles.c: Not setting device for stream ALSA Playback, because it lacks role.
(  67.866|   0.000) D: [pulseaudio] module-suspend-on-idle.c: Sink alsa_output.pci-0000_00_1f.5.analog-stereo becomes busy, resuming.
(  67.866|   0.000) D: [pulseaudio] sink.c: Suspend cause of sink alsa_output.pci-0000_00_1f.5.analog-stereo is 0x0000, resuming
(  67.868|   0.001) D: [pulseaudio] reserve-wrap.c: Successfully acquired reservation lock on device 'Audio0'
(  67.868|   0.000) I: [alsa-sink-Intel ICH] alsa-sink.c: Trying resume...
(  67.869|   0.000) I: [alsa-sink-Intel ICH] alsa-util.c: cannot disable ALSA period wakeups
(  67.869|   0.000) D: [alsa-sink-Intel ICH] alsa-util.c: Maximum hw buffer size is 371 ms
(  67.869|   0.000) D: [alsa-sink-Intel ICH] alsa-util.c: Set buffer size first (to 16384 samples), period size second (to 16384 samples).
(  67.869|   0.000) I: [alsa-sink-Intel ICH] alsa-util.c: ALSA period wakeups were not disabled
(  67.869|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: hwbuf_unused=0
(  67.870|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: setting avail_min=13297
(  67.870|   0.000) I: [alsa-sink-Intel ICH] alsa-sink.c: Time scheduling watermark is 20.00ms
(  67.870|   0.000) I: [alsa-sink-Intel ICH] alsa-sink.c: Resumed successfully...
(  67.870|   0.000) I: [alsa-sink-Intel ICH] alsa-sink.c: Starting playback.
(  67.870|   0.000) D: [alsa-sink-Intel ICH] ratelimit.c: 10 events suppressed
(  67.870|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Cutting sleep time for the initial iterations by half.
(  67.870|   0.000) D: [pulseaudio] module-suspend-on-idle.c: Sink alsa_output.pci-0000_00_1f.5.analog-stereo becomes idle, timeout in 5 seconds.
(  67.870|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Cutting sleep time for the initial iterations by half.
(  67.870|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Cutting sleep time for the initial iterations by half.
(  67.870|   0.000) D: [pulseaudio] module-suspend-on-idle.c: Sink alsa_output.pci-0000_00_1f.5.analog-stereo becomes idle, timeout in 5 seconds.
(  67.870|   0.000) D: [pulseaudio] memblockq.c: memblockq requested: maxlength=33554432, tlength=0, base=4, prebuf=0, minreq=1 maxrewind=0
(  67.870|   0.000) D: [pulseaudio] memblockq.c: memblockq sanitized: maxlength=33554432, tlength=33554432, base=4, prebuf=0, minreq=4 maxrewind=0
(  67.870|   0.000) I: [pulseaudio] sink-input.c: Created input 0 "ALSA Playback" on alsa_output.pci-0000_00_1f.5.analog-stereo with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
(  67.870|   0.000) I: [pulseaudio] sink-input.c:     media.name = "ALSA Playback"
(  67.870|   0.000) I: [pulseaudio] sink-input.c:     application.name = "ALSA plug-in [plugin-container]"
(  67.870|   0.000) I: [pulseaudio] sink-input.c:     native-protocol.peer = "UNIX socket client"
(  67.870|   0.000) I: [pulseaudio] sink-input.c:     native-protocol.version = "28"
(  67.870|   0.000) I: [pulseaudio] sink-input.c:     application.process.id = "1884"
(  67.870|   0.000) I: [pulseaudio] sink-input.c:     application.process.user = "fall"
(  67.870|   0.000) I: [pulseaudio] sink-input.c:     application.process.host = "fall-Gateway-400VTX"
(  67.870|   0.000) I: [pulseaudio] sink-input.c:     application.process.binary = "plugin-container"
(  67.870|   0.000) I: [pulseaudio] sink-input.c:     application.language = "en_US.UTF-8"
(  67.870|   0.000) I: [pulseaudio] sink-input.c:     window.x11.display = ":0.0"
(  67.870|   0.000) I: [pulseaudio] sink-input.c:     application.process.machine_id = "b99c79403e26b29193156cd95679c2ae"
(  67.870|   0.000) I: [pulseaudio] sink-input.c:     application.process.session_id = "c1"
(  67.870|   0.000) I: [pulseaudio] sink-input.c:     module-stream-restore.id = "sink-input-by-application-name:ALSA plug-in [plugin-container]"
(  67.871|   0.000) I: [pulseaudio] protocol-native.c: Requested tlength=500.00 ms, minreq=20.00 ms
(  67.871|   0.000) D: [pulseaudio] protocol-native.c: Early requests mode enabled, configuring sink latency to minreq.
(  67.871|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Cutting sleep time for the initial iterations by half.
(  67.871|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Cutting sleep time for the initial iterations by half.
(  67.871|   0.000) D: [pulseaudio] protocol-native.c: Requested latency=20.00 ms, Received latency=20.00 ms
(  67.871|   0.000) D: [pulseaudio] memblockq.c: memblockq requested: maxlength=4194304, tlength=88200, base=4, prebuf=3528, minreq=3528 maxrewind=0
(  67.871|   0.000) D: [pulseaudio] memblockq.c: memblockq sanitized: maxlength=4194304, tlength=88200, base=4, prebuf=3528, minreq=3528 maxrewind=0
(  67.871|   0.000) I: [pulseaudio] protocol-native.c: Final latency 520.00 ms = 460.00 ms + 2*20.00 ms + 20.00 ms
(  67.871|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Cutting sleep time for the initial iterations by half.
(  67.871|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Latency set to 20.00ms
(  67.871|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: hwbuf_unused=62008
(  67.871|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: setting avail_min=15944
(  67.871|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Requesting rewind due to latency change.
(  67.871|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Requested volume: 0: 100% 1: 100%
(  67.871|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c:            in dB: 0: 0.00 dB 1: 0.00 dB
(  67.871|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Got hardware volume: 0: 100% 1: 100%
(  67.871|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c:               in dB: 0: 0.00 dB 1: 0.00 dB
(  67.871|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Calculated software volume: 0: 100% 1: 100% (accurate-enough=yes)
(  67.871|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c:                      in dB: 0: 0.00 dB 1: 0.00 dB
(  67.872|   0.000) D: [alsa-sink-Intel ICH] sink.c: Volume not changing
(  67.872|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Requested to rewind 65536 bytes.
(  67.872|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Limited to 64904 bytes.
(  67.872|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: before: 16226
(  67.872|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: after: 16226
(  67.872|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Rewound 64904 bytes.
(  67.872|   0.000) D: [alsa-sink-Intel ICH] sink.c: Processing rewind...
(  67.872|   0.000) D: [alsa-sink-Intel ICH] sink.c: latency = 1590
(  67.872|   0.000) D: [alsa-sink-Intel ICH] sink-input.c: Have to rewind 64904 bytes on render memblockq.
(  67.872|   0.000) D: [alsa-sink-Intel ICH] source.c: Processing rewind...
(  67.872|   0.000) D: [pulseaudio] core-subscribe.c: Dropped redundant event due to change event.
(  67.879|   0.007) D: [alsa-sink-Intel ICH] protocol-native.c: Requesting rewind due to end of underrun.
(  67.879|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Requested to rewind 65536 bytes.
(  67.879|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Limited to 3220 bytes.
(  67.880|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: before: 805
(  67.880|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: after: 805
(  67.880|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Rewound 3220 bytes.
(  67.880|   0.000) D: [alsa-sink-Intel ICH] sink.c: Processing rewind...
(  67.880|   0.000) D: [alsa-sink-Intel ICH] sink.c: latency = 1573
(  67.880|   0.000) D: [alsa-sink-Intel ICH] sink-input.c: Have to rewind 3220 bytes on render memblockq.
(  67.880|   0.000) D: [alsa-sink-Intel ICH] source.c: Processing rewind...
(  67.890|   0.010) D: [alsa-sink-Intel ICH] protocol-native.c: Implicit underrun of 'ALSA Playback'
(  67.890|   0.000) D: [alsa-sink-Intel ICH] sink.c: Found underrun 1564 bytes ago (1900 bytes ahead in playback buffer)
(  67.891|   0.000) D: [alsa-sink-Intel ICH] sink.c: Found underrun 1564 bytes ago (1792 bytes ahead in playback buffer)
(  67.891|   0.000) D: [alsa-sink-Intel ICH] sink.c: Found underrun 1564 bytes ago (1768 bytes ahead in playback buffer)
(  67.893|   0.001) D: [alsa-sink-Intel ICH] sink.c: Found underrun 1564 bytes ago (1452 bytes ahead in playback buffer)
(  67.893|   0.000) D: [alsa-sink-Intel ICH] sink.c: Found underrun 1564 bytes ago (1428 bytes ahead in playback buffer)
(  67.895|   0.002) D: [alsa-sink-Intel ICH] sink.c: Found underrun 2496 bytes ago (1020 bytes ahead in playback buffer)
(  67.895|   0.000) D: [alsa-sink-Intel ICH] protocol-native.c: Requesting rewind due to end of underrun.
(  67.895|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Requested to rewind 2496 bytes.
(  67.895|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Limited to 2496 bytes.
(  67.895|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: before: 624
(  67.895|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: after: 624
(  67.895|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Rewound 2496 bytes.
(  67.895|   0.000) D: [alsa-sink-Intel ICH] sink.c: Processing rewind...
(  67.896|   0.000) D: [alsa-sink-Intel ICH] sink.c: latency = 5672
(  67.896|   0.000) D: [alsa-sink-Intel ICH] sink-input.c: Have to rewind 2496 bytes on render memblockq.
(  67.896|   0.000) D: [alsa-sink-Intel ICH] source.c: Processing rewind...
(  80.924|  13.028) D: [alsa-sink-Intel ICH] sink-input.c: Requesting rewind due to corking
(  80.924|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Requested to rewind 65536 bytes.
(  80.924|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Limited to 3092 bytes.
(  80.924|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: before: 773
(  80.924|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: after: 773
(  80.924|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Rewound 3092 bytes.
(  80.924|   0.000) D: [alsa-sink-Intel ICH] sink.c: Processing rewind...
(  80.924|   0.000) D: [alsa-sink-Intel ICH] sink.c: latency = 1274
(  80.925|   0.000) D: [alsa-sink-Intel ICH] sink-input.c: Have to rewind 3092 bytes on render memblockq.
(  80.925|   0.000) D: [alsa-sink-Intel ICH] sink-input.c: Have to rewind 3092 bytes on implementor.
(  80.925|   0.000) D: [alsa-sink-Intel ICH] source.c: Processing rewind...
(  80.925|   0.000) D: [alsa-sink-Intel ICH] sink.c: Found underrun 3324 bytes ago (200 bytes ahead in playback buffer)
(  80.925|   0.000) D: [alsa-sink-Intel ICH] sink.c: Found underrun 3324 bytes ago (164 bytes ahead in playback buffer)
(  80.925|   0.000) D: [alsa-sink-Intel ICH] sink.c: Found underrun 3324 bytes ago (152 bytes ahead in playback buffer)
(  80.925|   0.000) D: [pulseaudio] module-suspend-on-idle.c: Sink alsa_output.pci-0000_00_1f.5.analog-stereo becomes idle, timeout in 5 seconds.
(  80.926|   0.000) D: [alsa-sink-Intel ICH] sink.c: Found underrun 3324 bytes ago (4 bytes ahead in playback buffer)
(  80.933|   0.007) D: [alsa-sink-Intel ICH] alsa-sink.c: hwbuf_unused=0
(  80.933|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: setting avail_min=15943
(  80.933|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Requested volume: 0: 100% 1: 100%
(  80.933|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c:            in dB: 0: 0.00 dB 1: 0.00 dB
(  80.933|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Got hardware volume: 0: 100% 1: 100%
(  80.933|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c:               in dB: 0: 0.00 dB 1: 0.00 dB
(  80.933|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Calculated software volume: 0: 100% 1: 100% (accurate-enough=yes)
(  80.933|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c:                      in dB: 0: 0.00 dB 1: 0.00 dB
(  80.933|   0.000) D: [alsa-sink-Intel ICH] sink.c: Volume not changing
(  80.933|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Requested to rewind 65536 bytes.
(  80.933|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Limited to 2696 bytes.
(  80.933|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: before: 674
(  80.933|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: after: 674
(  80.933|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Rewound 2696 bytes.
(  80.933|   0.000) D: [alsa-sink-Intel ICH] sink.c: Processing rewind...
(  80.933|   0.000) D: [alsa-sink-Intel ICH] sink.c: latency = 1323
(  80.933|   0.000) D: [alsa-sink-Intel ICH] source.c: Processing rewind...
(  80.934|   0.000) D: [pulseaudio] module-suspend-on-idle.c: Sink alsa_output.pci-0000_00_1f.5.analog-stereo becomes idle, timeout in 5 seconds.
(  80.934|   0.000) D: [pulseaudio] core.c: Hmm, no streams around, trying to vacuum.
(  80.934|   0.000) I: [pulseaudio] sink-input.c: Freeing input 0 "ALSA Playback"
(  80.934|   0.000) I: [pulseaudio] client.c: Freed 3 "ALSA plug-in [plugin-container]"
(  80.934|   0.000) I: [pulseaudio] protocol-native.c: Connection died.
(  81.243|   0.309) D: [alsa-sink-Intel ICH] alsa-sink.c: Wakeup from ALSA!
(  81.244|   0.000) I: [alsa-sink-Intel ICH] alsa-sink.c: Underrun!
(  81.244|   0.000) I: [alsa-sink-Intel ICH] alsa-sink.c: Increasing wakeup watermark to 20.00 ms
(  84.215|   2.971) D: [alsa-sink-Intel ICH] alsa-sink.c: Wakeup from ALSA!
(  84.216|   0.000) I: [alsa-sink-Intel ICH] alsa-sink.c: Underrun!
(  84.216|   0.000) I: [alsa-sink-Intel ICH] alsa-sink.c: Increasing wakeup watermark to 30.00 ms
(  84.958|   0.742) D: [alsa-sink-Intel ICH] alsa-sink.c: Wakeup from ALSA!
(  84.959|   0.000) I: [alsa-sink-Intel ICH] alsa-sink.c: Underrun!
(  84.959|   0.000) I: [alsa-sink-Intel ICH] alsa-sink.c: Increasing wakeup watermark to 40.00 ms
(  85.938|   0.979) I: [pulseaudio] module-suspend-on-idle.c: Sink alsa_output.pci-0000_00_1f.5.analog-stereo idle for too long, suspending ...
(  85.938|   0.000) D: [pulseaudio] sink.c: Suspend cause of sink alsa_output.pci-0000_00_1f.5.analog-stereo is 0x0004, suspending
(  85.940|   0.001) I: [alsa-sink-Intel ICH] alsa-sink.c: Device suspended...
(  85.940|   0.000) D: [pulseaudio] core.c: Hmm, no streams around, trying to vacuum.
(  85.941|   0.000) D: [pulseaudio] module-udev-detect.c: /dev/snd/controlC0 is accessible: yes
(  85.941|   0.000) D: [pulseaudio] module-udev-detect.c: Resuming all sinks and sources of card alsa_card.pci-0000_00_1f.5.
(  86.293|   0.352) I: [pulseaudio] client.c: Created 4 "Native client (UNIX socket client)"
(  86.302|   0.009) D: [pulseaudio] protocol-native.c: Protocol version: remote 28, local 28
(  86.303|   0.000) I: [pulseaudio] protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
(  86.303|   0.000) D: [pulseaudio] protocol-native.c: SHM possible: yes
(  86.303|   0.000) D: [pulseaudio] protocol-native.c: Negotiated SHM: yes
(  86.304|   0.001) D: [pulseaudio] module-augment-properties.c: Looking for .desktop file for plugin-container
(  86.305|   0.000) D: [pulseaudio] module-intended-roles.c: Not setting device for stream ALSA Playback, because it lacks role.
(  86.305|   0.000) D: [pulseaudio] module-suspend-on-idle.c: Sink alsa_output.pci-0000_00_1f.5.analog-stereo becomes busy, resuming.
(  86.305|   0.000) D: [pulseaudio] sink.c: Suspend cause of sink alsa_output.pci-0000_00_1f.5.analog-stereo is 0x0000, resuming
(  86.307|   0.001) D: [pulseaudio] reserve-wrap.c: Successfully acquired reservation lock on device 'Audio0'
(  86.307|   0.000) I: [alsa-sink-Intel ICH] alsa-sink.c: Trying resume...
(  86.308|   0.000) I: [alsa-sink-Intel ICH] alsa-util.c: cannot disable ALSA period wakeups
(  86.308|   0.000) D: [alsa-sink-Intel ICH] alsa-util.c: Maximum hw buffer size is 371 ms
(  86.308|   0.000) D: [alsa-sink-Intel ICH] alsa-util.c: Set buffer size first (to 16384 samples), period size second (to 16384 samples).
(  86.308|   0.000) I: [alsa-sink-Intel ICH] alsa-util.c: ALSA period wakeups were not disabled
(  86.308|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: hwbuf_unused=0
(  86.308|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: setting avail_min=14620
(  86.308|   0.000) I: [alsa-sink-Intel ICH] alsa-sink.c: Time scheduling watermark is 20.00ms
(  86.308|   0.000) I: [alsa-sink-Intel ICH] alsa-sink.c: Resumed successfully...
(  86.309|   0.000) I: [alsa-sink-Intel ICH] alsa-sink.c: Starting playback.
(  86.309|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Cutting sleep time for the initial iterations by half.
(  86.309|   0.000) D: [pulseaudio] module-suspend-on-idle.c: Sink alsa_output.pci-0000_00_1f.5.analog-stereo becomes idle, timeout in 5 seconds.
(  86.309|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Cutting sleep time for the initial iterations by half.
(  86.309|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Cutting sleep time for the initial iterations by half.
(  86.309|   0.000) D: [pulseaudio] module-suspend-on-idle.c: Sink alsa_output.pci-0000_00_1f.5.analog-stereo becomes idle, timeout in 5 seconds.
(  86.309|   0.000) D: [pulseaudio] memblockq.c: memblockq requested: maxlength=33554432, tlength=0, base=4, prebuf=0, minreq=1 maxrewind=0
(  86.309|   0.000) D: [pulseaudio] memblockq.c: memblockq sanitized: maxlength=33554432, tlength=33554432, base=4, prebuf=0, minreq=4 maxrewind=0
(  86.309|   0.000) I: [pulseaudio] sink-input.c: Created input 1 "ALSA Playback" on alsa_output.pci-0000_00_1f.5.analog-stereo with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
(  86.309|   0.000) I: [pulseaudio] sink-input.c:     media.name = "ALSA Playback"
(  86.309|   0.000) I: [pulseaudio] sink-input.c:     application.name = "ALSA plug-in [plugin-container]"
(  86.309|   0.000) I: [pulseaudio] sink-input.c:     native-protocol.peer = "UNIX socket client"
(  86.309|   0.000) I: [pulseaudio] sink-input.c:     native-protocol.version = "28"
(  86.309|   0.000) I: [pulseaudio] sink-input.c:     application.process.id = "1884"
(  86.309|   0.000) I: [pulseaudio] sink-input.c:     application.process.user = "fall"
(  86.309|   0.000) I: [pulseaudio] sink-input.c:     application.process.host = "fall-Gateway-400VTX"
(  86.309|   0.000) I: [pulseaudio] sink-input.c:     application.process.binary = "plugin-container"
(  86.309|   0.000) I: [pulseaudio] sink-input.c:     application.language = "en_US.UTF-8"
(  86.309|   0.000) I: [pulseaudio] sink-input.c:     window.x11.display = ":0.0"
(  86.309|   0.000) I: [pulseaudio] sink-input.c:     application.process.machine_id = "b99c79403e26b29193156cd95679c2ae"
(  86.309|   0.000) I: [pulseaudio] sink-input.c:     application.process.session_id = "c1"
(  86.309|   0.000) I: [pulseaudio] sink-input.c:     module-stream-restore.id = "sink-input-by-application-name:ALSA plug-in [plugin-container]"
(  86.309|   0.000) I: [pulseaudio] protocol-native.c: Requested tlength=500.00 ms, minreq=20.00 ms
(  86.309|   0.000) D: [pulseaudio] protocol-native.c: Early requests mode enabled, configuring sink latency to minreq.
(  86.310|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Cutting sleep time for the initial iterations by half.
(  86.310|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Cutting sleep time for the initial iterations by half.
(  86.310|   0.000) D: [pulseaudio] protocol-native.c: Requested latency=20.00 ms, Received latency=20.00 ms
(  86.310|   0.000) D: [pulseaudio] memblockq.c: memblockq requested: maxlength=4194304, tlength=88200, base=4, prebuf=3528, minreq=3528 maxrewind=0
(  86.310|   0.000) D: [pulseaudio] memblockq.c: memblockq sanitized: maxlength=4194304, tlength=88200, base=4, prebuf=3528, minreq=3528 maxrewind=0
(  86.310|   0.000) I: [pulseaudio] protocol-native.c: Final latency 520.00 ms = 460.00 ms + 2*20.00 ms + 20.00 ms
(  86.310|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Cutting sleep time for the initial iterations by half.
(  86.310|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Latency set to 20.00ms
(  86.310|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: hwbuf_unused=62008
(  86.310|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: setting avail_min=15944
(  86.310|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Requesting rewind due to latency change.
(  86.310|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Requested volume: 0: 100% 1: 100%
(  86.310|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c:            in dB: 0: 0.00 dB 1: 0.00 dB
(  86.310|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Got hardware volume: 0: 100% 1: 100%
(  86.310|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c:               in dB: 0: 0.00 dB 1: 0.00 dB
(  86.310|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Calculated software volume: 0: 100% 1: 100% (accurate-enough=yes)
(  86.310|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c:                      in dB: 0: 0.00 dB 1: 0.00 dB
(  86.310|   0.000) D: [alsa-sink-Intel ICH] sink.c: Volume not changing
(  86.310|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Requested to rewind 65536 bytes.
(  86.310|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Limited to 64920 bytes.
(  86.310|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: before: 16230
(  86.310|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: after: 16230
(  86.310|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Rewound 64920 bytes.
(  86.310|   0.000) D: [alsa-sink-Intel ICH] sink.c: Processing rewind...
(  86.311|   0.000) D: [alsa-sink-Intel ICH] sink.c: latency = 1570
(  86.311|   0.000) D: [alsa-sink-Intel ICH] sink-input.c: Have to rewind 64920 bytes on render memblockq.
(  86.311|   0.000) D: [alsa-sink-Intel ICH] source.c: Processing rewind...
(  86.311|   0.000) D: [pulseaudio] core-subscribe.c: Dropped redundant event due to change event.
(  86.348|   0.037) D: [alsa-sink-Intel ICH] protocol-native.c: Requesting rewind due to end of underrun.
(  86.348|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Requested to rewind 65536 bytes.
(  86.348|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Limited to 3224 bytes.
(  86.348|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: before: 806
(  86.348|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: after: 806
(  86.348|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Rewound 3224 bytes.
(  86.348|   0.000) D: [alsa-sink-Intel ICH] sink.c: Processing rewind...
(  86.349|   0.000) D: [alsa-sink-Intel ICH] sink.c: latency = 1572
(  86.349|   0.000) D: [alsa-sink-Intel ICH] sink-input.c: Have to rewind 3224 bytes on render memblockq.
(  86.349|   0.000) D: [alsa-sink-Intel ICH] source.c: Processing rewind...
(  86.355|   0.006) D: [alsa-sink-Intel ICH] protocol-native.c: Implicit underrun of 'ALSA Playback'
(  86.355|   0.000) D: [alsa-sink-Intel ICH] sink.c: Found underrun 840 bytes ago (2656 bytes ahead in playback buffer)
(  86.355|   0.000) D: [alsa-sink-Intel ICH] protocol-native.c: Requesting rewind due to end of underrun.
(  86.355|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Requested to rewind 840 bytes.
(  86.355|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Limited to 840 bytes.
(  86.355|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: before: 210
(  86.355|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: after: 210
(  86.355|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Rewound 840 bytes.
(  86.355|   0.000) D: [alsa-sink-Intel ICH] sink.c: Processing rewind...
(  86.355|   0.000) D: [alsa-sink-Intel ICH] sink.c: latency = 15074
(  86.355|   0.000) D: [alsa-sink-Intel ICH] sink-input.c: Have to rewind 840 bytes on render memblockq.
(  86.355|   0.000) D: [alsa-sink-Intel ICH] source.c: Processing rewind...
(  88.271|   1.915) D: [alsa-sink-Intel ICH] sink-input.c: Requesting rewind due to corking
(  88.271|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Requested to rewind 65536 bytes.
(  88.271|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Limited to 3048 bytes.
(  88.271|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: before: 762
(  88.271|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: after: 762
(  88.271|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Rewound 3048 bytes.
(  88.271|   0.000) D: [alsa-sink-Intel ICH] sink.c: Processing rewind...
(  88.271|   0.000) D: [alsa-sink-Intel ICH] sink.c: latency = 1327
(  88.271|   0.000) D: [alsa-sink-Intel ICH] sink-input.c: Have to rewind 3048 bytes on render memblockq.
(  88.271|   0.000) D: [alsa-sink-Intel ICH] sink-input.c: Have to rewind 3048 bytes on implementor.
(  88.271|   0.000) D: [alsa-sink-Intel ICH] source.c: Processing rewind...
(  88.271|   0.000) D: [alsa-sink-Intel ICH] sink.c: Found underrun 3316 bytes ago (208 bytes ahead in playback buffer)
(  88.272|   0.000) D: [alsa-sink-Intel ICH] sink.c: Found underrun 3316 bytes ago (164 bytes ahead in playback buffer)
(  88.272|   0.000) D: [alsa-sink-Intel ICH] sink.c: Found underrun 3316 bytes ago (156 bytes ahead in playback buffer)
(  88.272|   0.000) D: [pulseaudio] module-suspend-on-idle.c: Sink alsa_output.pci-0000_00_1f.5.analog-stereo becomes idle, timeout in 5 seconds.
(  88.272|   0.000) D: [alsa-sink-Intel ICH] sink.c: Found underrun 3316 bytes ago (20 bytes ahead in playback buffer)
(  88.279|   0.006) D: [alsa-sink-Intel ICH] alsa-sink.c: hwbuf_unused=0
(  88.279|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: setting avail_min=15943
(  88.279|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Requested volume: 0: 100% 1: 100%
(  88.279|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c:            in dB: 0: 0.00 dB 1: 0.00 dB
(  88.279|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Got hardware volume: 0: 100% 1: 100%
(  88.279|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c:               in dB: 0: 0.00 dB 1: 0.00 dB
(  88.280|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Calculated software volume: 0: 100% 1: 100% (accurate-enough=yes)
(  88.280|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c:                      in dB: 0: 0.00 dB 1: 0.00 dB
(  88.280|   0.000) D: [alsa-sink-Intel ICH] sink.c: Volume not changing
(  88.280|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Requested to rewind 65536 bytes.
(  88.280|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Limited to 2704 bytes.
(  88.280|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: before: 676
(  88.280|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: after: 676
(  88.280|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Rewound 2704 bytes.
(  88.280|   0.000) D: [alsa-sink-Intel ICH] sink.c: Processing rewind...
(  88.280|   0.000) D: [alsa-sink-Intel ICH] sink.c: latency = 1312
(  88.280|   0.000) D: [alsa-sink-Intel ICH] source.c: Processing rewind...
(  88.280|   0.000) D: [pulseaudio] module-suspend-on-idle.c: Sink alsa_output.pci-0000_00_1f.5.analog-stereo becomes idle, timeout in 5 seconds.
(  88.280|   0.000) D: [pulseaudio] core.c: Hmm, no streams around, trying to vacuum.
(  88.280|   0.000) I: [pulseaudio] sink-input.c: Freeing input 1 "ALSA Playback"
(  88.280|   0.000) I: [pulseaudio] client.c: Freed 4 "ALSA plug-in [plugin-container]"
(  88.280|   0.000) I: [pulseaudio] protocol-native.c: Connection died.
(  88.537|   0.256) D: [alsa-sink-Intel ICH] alsa-sink.c: Wakeup from ALSA!
(  88.538|   0.000) I: [alsa-sink-Intel ICH] alsa-sink.c: Underrun!
(  88.538|   0.000) I: [alsa-sink-Intel ICH] alsa-sink.c: Increasing wakeup watermark to 20.00 ms
(  91.138|   2.600) D: [alsa-sink-Intel ICH] alsa-sink.c: Wakeup from ALSA!
(  91.138|   0.000) I: [alsa-sink-Intel ICH] alsa-sink.c: Underrun!
(  91.138|   0.000) I: [alsa-sink-Intel ICH] alsa-sink.c: Increasing wakeup watermark to 30.00 ms
(  92.624|   1.485) D: [alsa-sink-Intel ICH] alsa-sink.c: Wakeup from ALSA!
(  92.624|   0.000) I: [alsa-sink-Intel ICH] alsa-sink.c: Underrun!
(  92.624|   0.000) I: [alsa-sink-Intel ICH] alsa-sink.c: Increasing wakeup watermark to 40.00 ms
(  93.284|   0.659) I: [pulseaudio] module-suspend-on-idle.c: Sink alsa_output.pci-0000_00_1f.5.analog-stereo idle for too long, suspending ...
(  93.284|   0.000) D: [pulseaudio] sink.c: Suspend cause of sink alsa_output.pci-0000_00_1f.5.analog-stereo is 0x0004, suspending
(  93.286|   0.001) I: [alsa-sink-Intel ICH] alsa-sink.c: Device suspended...
(  93.286|   0.000) D: [pulseaudio] core.c: Hmm, no streams around, trying to vacuum.
(  93.287|   0.000) D: [pulseaudio] module-udev-detect.c: /dev/snd/controlC0 is accessible: yes
(  93.287|   0.000) D: [pulseaudio] module-udev-detect.c: Resuming all sinks and sources of card alsa_card.pci-0000_00_1f.5.
(  96.562|   3.275) I: [pulseaudio] client.c: Created 5 "Native client (UNIX socket client)"
(  96.567|   0.005) D: [pulseaudio] protocol-native.c: Protocol version: remote 28, local 28
(  96.567|   0.000) I: [pulseaudio] protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
(  96.567|   0.000) D: [pulseaudio] protocol-native.c: SHM possible: yes
(  96.567|   0.000) D: [pulseaudio] protocol-native.c: Negotiated SHM: yes
(  96.568|   0.000) D: [pulseaudio] module-augment-properties.c: Looking for .desktop file for firefox
(  96.568|   0.000) D: [pulseaudio] module-augment-properties.c: Found /usr/share/applications/firefox.desktop.
(  96.571|   0.002) D: [pulseaudio] module-intended-roles.c: Not setting device for stream AudioStream, because it lacks role.
(  96.571|   0.000) I: [pulseaudio] sink-input.c: Trying to change sample rate
(  96.571|   0.000) D: [pulseaudio] sink.c: Suspending sink alsa_output.pci-0000_00_1f.5.analog-stereo due to changing the sample rate.
(  96.571|   0.000) I: [pulseaudio] alsa-sink.c: Updating rate for device front:0, new rate is 48000
(  96.571|   0.000) I: [pulseaudio] sink.c: Changed sampling rate successfully
(  96.571|   0.000) I: [pulseaudio] sink-input.c: Rate changed to 48000 Hz
(  96.571|   0.000) I: [pulseaudio] module-stream-restore.c: Restoring volume for sink input sink-input-by-application-name:CubebUtils.
(  96.571|   0.000) D: [pulseaudio] module-suspend-on-idle.c: Sink alsa_output.pci-0000_00_1f.5.analog-stereo becomes busy, resuming.
(  96.571|   0.000) D: [pulseaudio] sink.c: Suspend cause of sink alsa_output.pci-0000_00_1f.5.analog-stereo is 0x0000, resuming
(  96.573|   0.001) D: [pulseaudio] reserve-wrap.c: Successfully acquired reservation lock on device 'Audio0'
(  96.573|   0.000) I: [alsa-sink-Intel ICH] alsa-sink.c: Trying resume...
(  96.574|   0.000) I: [alsa-sink-Intel ICH] alsa-util.c: cannot disable ALSA period wakeups
(  96.574|   0.000) D: [alsa-sink-Intel ICH] alsa-util.c: Maximum hw buffer size is 341 ms
(  96.574|   0.000) D: [alsa-sink-Intel ICH] alsa-util.c: Set buffer size first (to 16384 samples), period size second (to 16384 samples).
(  96.574|   0.000) I: [alsa-sink-Intel ICH] alsa-util.c: ALSA period wakeups were not disabled
(  96.574|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: hwbuf_unused=0
(  96.574|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: setting avail_min=14620
(  96.574|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: hwbuf_unused=0
(  96.574|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: setting avail_min=15502
(  96.574|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: hwbuf_unused=0
(  96.575|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: setting avail_min=15502
(  96.575|   0.000) I: [alsa-sink-Intel ICH] alsa-sink.c: Time scheduling watermark is 18.38ms
(  96.575|   0.000) I: [alsa-sink-Intel ICH] alsa-sink.c: Resumed successfully...
(  96.575|   0.000) I: [alsa-sink-Intel ICH] alsa-sink.c: Starting playback.
(  96.575|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Cutting sleep time for the initial iterations by half.
(  96.575|   0.000) D: [pulseaudio] module-suspend-on-idle.c: Sink alsa_output.pci-0000_00_1f.5.analog-stereo becomes idle, timeout in 5 seconds.
(  96.575|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Cutting sleep time for the initial iterations by half.
(  96.575|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Cutting sleep time for the initial iterations by half.
(  96.575|   0.000) D: [pulseaudio] module-suspend-on-idle.c: Sink alsa_output.pci-0000_00_1f.5.analog-stereo becomes idle, timeout in 5 seconds.
(  96.575|   0.000) I: [pulseaudio] resampler.c: Forcing resampler 'copy', because of fixed, identical sample rates.
(  96.575|   0.000) I: [pulseaudio] resampler.c: Using resampler 'copy'
(  96.575|   0.000) I: [pulseaudio] resampler.c: Using s16le as working format.
(  96.575|   0.000) D: [pulseaudio] resampler.c: Resampler:
(  96.575|   0.000) D: [pulseaudio] resampler.c:   rate 48000 -> 48000 (method copy),
(  96.575|   0.000) D: [pulseaudio] resampler.c:   format float32le -> s16le (intermediate s16le),
(  96.575|   0.000) D: [pulseaudio] resampler.c:   channels 2 -> 2 (resampling 2)
(  96.575|   0.000) D: [pulseaudio] memblockq.c: memblockq requested: maxlength=33554432, tlength=0, base=4, prebuf=0, minreq=1 maxrewind=0
(  96.575|   0.000) D: [pulseaudio] memblockq.c: memblockq sanitized: maxlength=33554432, tlength=33554432, base=4, prebuf=0, minreq=4 maxrewind=0
(  96.575|   0.000) I: [pulseaudio] sink-input.c: Created input 2 "AudioStream" on alsa_output.pci-0000_00_1f.5.analog-stereo with sample spec float32le 2ch 48000Hz and channel map front-left,front-right
(  96.575|   0.000) I: [pulseaudio] sink-input.c:     media.name = "AudioStream"
(  96.575|   0.000) I: [pulseaudio] sink-input.c:     application.name = "CubebUtils"
(  96.575|   0.000) I: [pulseaudio] sink-input.c:     native-protocol.peer = "UNIX socket client"
(  96.575|   0.000) I: [pulseaudio] sink-input.c:     native-protocol.version = "28"
(  96.575|   0.000) I: [pulseaudio] sink-input.c:     application.process.id = "1684"
(  96.575|   0.000) I: [pulseaudio] sink-input.c:     application.process.user = "fall"
(  96.575|   0.000) I: [pulseaudio] sink-input.c:     application.process.host = "fall-Gateway-400VTX"
(  96.575|   0.000) I: [pulseaudio] sink-input.c:     application.process.binary = "firefox"
(  96.575|   0.000) I: [pulseaudio] sink-input.c:     application.language = "en_US.UTF-8"
(  96.575|   0.000) I: [pulseaudio] sink-input.c:     window.x11.display = ":0.0"
(  96.575|   0.000) I: [pulseaudio] sink-input.c:     application.process.machine_id = "b99c79403e26b29193156cd95679c2ae"
(  96.575|   0.000) I: [pulseaudio] sink-input.c:     application.process.session_id = "c1"
(  96.575|   0.000) I: [pulseaudio] sink-input.c:     application.icon_name = "firefox"
(  96.575|   0.000) I: [pulseaudio] sink-input.c:     module-stream-restore.id = "sink-input-by-application-name:CubebUtils"
(  96.576|   0.000) I: [pulseaudio] protocol-native.c: Requested tlength=100.00 ms, minreq=25.00 ms
(  96.576|   0.000) D: [pulseaudio] protocol-native.c: Traditional mode enabled, modifying sink usec only for compat with minreq.
(  96.576|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Cutting sleep time for the initial iterations by half.
(  96.576|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Cutting sleep time for the initial iterations by half.
(  96.576|   0.000) D: [pulseaudio] protocol-native.c: Requested latency=50.00 ms, Received latency=50.00 ms
(  96.576|   0.000) D: [pulseaudio] memblockq.c: memblockq requested: maxlength=4194304, tlength=38400, base=8, prebuf=28808, minreq=9600 maxrewind=0
(  96.576|   0.000) D: [pulseaudio] memblockq.c: memblockq sanitized: maxlength=4194304, tlength=38400, base=8, prebuf=28808, minreq=9600 maxrewind=0
(  96.576|   0.000) I: [pulseaudio] protocol-native.c: Final latency 150.00 ms = 50.00 ms + 2*25.00 ms + 50.00 ms
(  96.576|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Cutting sleep time for the initial iterations by half.
(  96.576|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Latency set to 50.00ms
(  96.576|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: hwbuf_unused=55936
(  96.576|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: setting avail_min=15503
(  96.576|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Requesting rewind due to latency change.
(  96.576|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Requested volume: 0: 100% 1: 100%
(  96.576|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c:            in dB: 0: 0.00 dB 1: 0.00 dB
(  96.576|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Got hardware volume: 0: 100% 1: 100%
(  96.576|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c:               in dB: 0: 0.00 dB 1: 0.00 dB
(  96.577|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Calculated software volume: 0: 100% 1: 100% (accurate-enough=yes)
(  96.577|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c:                      in dB: 0: 0.00 dB 1: 0.00 dB
(  96.577|   0.000) D: [alsa-sink-Intel ICH] sink.c: Volume not changing
(  96.577|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Requested to rewind 65536 bytes.
(  96.577|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Limited to 64880 bytes.
(  96.577|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: before: 16220
(  96.577|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: after: 16220
(  96.577|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Rewound 64880 bytes.
(  96.577|   0.000) D: [alsa-sink-Intel ICH] sink.c: Processing rewind...
(  96.577|   0.000) D: [alsa-sink-Intel ICH] sink.c: latency = 1421
(  96.577|   0.000) D: [alsa-sink-Intel ICH] sink-input.c: Have to rewind 64880 bytes on render memblockq.
(  96.577|   0.000) D: [alsa-sink-Intel ICH] source.c: Processing rewind...
(  96.581|   0.003) D: [alsa-sink-Intel ICH] protocol-native.c: Requesting rewind due to end of underrun.
(  96.583|   0.001) D: [pulseaudio] protocol-native.c: Client firefox changes volume of sink input AudioStream.
(  96.583|   0.000) I: [pulseaudio] module-stream-restore.c: Storing volume/mute/device for stream sink-input-by-application-name:CubebUtils.
(  96.585|   0.002) D: [alsa-sink-Intel ICH] protocol-native.c: Requesting rewind due to end of underrun.
(  96.586|   0.000) D: [alsa-sink-Intel ICH] sink-input.c: Requesting rewind due to uncorking
(  96.586|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Requested to rewind 65536 bytes.
(  96.586|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Limited to 7652 bytes.
(  96.586|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: before: 1913
(  96.586|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: after: 1913
(  96.586|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Rewound 7652 bytes.
(  96.586|   0.000) D: [alsa-sink-Intel ICH] sink.c: Processing rewind...
(  96.586|   0.000) D: [alsa-sink-Intel ICH] sink.c: latency = 1409
(  96.586|   0.000) D: [alsa-sink-Intel ICH] source.c: Processing rewind...
(  96.587|   0.001) D: [pulseaudio] module-suspend-on-idle.c: Sink alsa_output.pci-0000_00_1f.5.analog-stereo becomes busy, resuming.
( 106.583|   9.995) I: [pulseaudio] module-stream-restore.c: Synced.
( 119.873|  13.290) D: [alsa-sink-Intel ICH] sink-input.c: Requesting rewind due to corking
( 119.873|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Requested to rewind 65536 bytes.
( 119.873|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Limited to 9032 bytes.
( 119.873|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: before: 2258
( 119.873|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: after: 2258
( 119.873|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Rewound 9032 bytes.
( 119.873|   0.000) D: [alsa-sink-Intel ICH] sink.c: Processing rewind...
( 119.873|   0.000) D: [alsa-sink-Intel ICH] sink.c: latency = 1202
( 119.874|   0.000) D: [alsa-sink-Intel ICH] sink-input.c: Have to rewind 9032 bytes on render memblockq.
( 119.874|   0.000) D: [alsa-sink-Intel ICH] sink-input.c: Have to rewind 18064 bytes on implementor.
( 119.874|   0.000) D: [alsa-sink-Intel ICH] source.c: Processing rewind...
( 119.874|   0.000) D: [alsa-sink-Intel ICH] sink.c: Found underrun 9400 bytes ago (192 bytes ahead in playback buffer)
( 119.874|   0.000) D: [alsa-sink-Intel ICH] sink.c: Found underrun 9400 bytes ago (148 bytes ahead in playback buffer)
( 119.874|   0.000) D: [alsa-sink-Intel ICH] sink.c: Found underrun 9400 bytes ago (136 bytes ahead in playback buffer)
( 119.874|   0.000) D: [pulseaudio] module-suspend-on-idle.c: Sink alsa_output.pci-0000_00_1f.5.analog-stereo becomes idle, timeout in 5 seconds.
( 124.875|   5.001) I: [pulseaudio] module-suspend-on-idle.c: Sink alsa_output.pci-0000_00_1f.5.analog-stereo idle for too long, suspending ...
( 124.875|   0.000) D: [pulseaudio] sink.c: Suspend cause of sink alsa_output.pci-0000_00_1f.5.analog-stereo is 0x0004, suspending
( 124.877|   0.001) I: [alsa-sink-Intel ICH] alsa-sink.c: Device suspended...
( 124.877|   0.000) I: [pulseaudio] core.c: All sinks and sources are suspended, vacuuming memory
( 124.878|   0.000) D: [pulseaudio] module-udev-detect.c: /dev/snd/controlC0 is accessible: yes
( 124.879|   0.000) D: [pulseaudio] module-udev-detect.c: Resuming all sinks and sources of card alsa_card.pci-0000_00_1f.5.
( 149.119|  24.240) D: [alsa-sink-Intel ICH] protocol-native.c: Requesting rewind due to end of underrun.
( 149.119|   0.000) D: [alsa-sink-Intel ICH] sink-input.c: Requesting rewind due to uncorking
( 149.119|   0.000) D: [pulseaudio] module-suspend-on-idle.c: Sink alsa_output.pci-0000_00_1f.5.analog-stereo becomes busy, resuming.
( 149.119|   0.000) D: [pulseaudio] sink.c: Suspend cause of sink alsa_output.pci-0000_00_1f.5.analog-stereo is 0x0000, resuming
( 149.120|   0.001) D: [pulseaudio] reserve-wrap.c: Successfully acquired reservation lock on device 'Audio0'
( 149.121|   0.000) I: [alsa-sink-Intel ICH] alsa-sink.c: Trying resume...
( 149.121|   0.000) I: [alsa-sink-Intel ICH] alsa-util.c: cannot disable ALSA period wakeups
( 149.122|   0.000) D: [alsa-sink-Intel ICH] alsa-util.c: Maximum hw buffer size is 341 ms
( 149.122|   0.000) D: [alsa-sink-Intel ICH] alsa-util.c: Set buffer size first (to 16384 samples), period size second (to 16384 samples).
( 149.122|   0.000) I: [alsa-sink-Intel ICH] alsa-util.c: ALSA period wakeups were not disabled
( 149.122|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Latency set to 50.00ms
( 149.122|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: hwbuf_unused=55936
( 149.122|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: setting avail_min=15503
( 149.122|   0.000) I: [alsa-sink-Intel ICH] alsa-sink.c: Time scheduling watermark is 18.38ms
( 149.122|   0.000) I: [alsa-sink-Intel ICH] alsa-sink.c: Resumed successfully...
( 149.122|   0.000) I: [alsa-sink-Intel ICH] alsa-sink.c: Starting playback.
( 149.122|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Cutting sleep time for the initial iterations by half.
( 149.122|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Cutting sleep time for the initial iterations by half.
( 149.123|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Cutting sleep time for the initial iterations by half.
( 149.124|   0.001) D: [alsa-sink-Intel ICH] alsa-sink.c: Cutting sleep time for the initial iterations by half.
( 149.124|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Cutting sleep time for the initial iterations by half.
( 149.124|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Cutting sleep time for the initial iterations by half.
( 149.124|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Cutting sleep time for the initial iterations by half.
( 149.125|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Cutting sleep time for the initial iterations by half.
( 149.125|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Cutting sleep time for the initial iterations by half.
( 149.125|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Cutting sleep time for the initial iterations by half.
( 149.125|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Cutting sleep time for the initial iterations by half.
( 159.309|  10.183) D: [alsa-sink-Intel ICH] sink-input.c: Requesting rewind due to corking
( 159.309|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Requested to rewind 65536 bytes.
( 159.309|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Limited to 9064 bytes.
( 159.309|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: before: 2266
( 159.309|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: after: 2266
( 159.309|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Rewound 9064 bytes.
( 159.309|   0.000) D: [alsa-sink-Intel ICH] sink.c: Processing rewind...
( 159.309|   0.000) D: [alsa-sink-Intel ICH] sink.c: latency = 1177
( 159.309|   0.000) D: [alsa-sink-Intel ICH] sink-input.c: Have to rewind 9064 bytes on render memblockq.
( 159.309|   0.000) D: [alsa-sink-Intel ICH] sink-input.c: Have to rewind 18128 bytes on implementor.
( 159.309|   0.000) D: [alsa-sink-Intel ICH] source.c: Processing rewind...
( 159.309|   0.000) D: [alsa-sink-Intel ICH] sink.c: Found underrun 9404 bytes ago (192 bytes ahead in playback buffer)
( 159.311|   0.001) D: [pulseaudio] module-suspend-on-idle.c: Sink alsa_output.pci-0000_00_1f.5.analog-stereo becomes idle, timeout in 5 seconds.
( 164.312|   5.001) I: [pulseaudio] module-suspend-on-idle.c: Sink alsa_output.pci-0000_00_1f.5.analog-stereo idle for too long, suspending ...
( 164.312|   0.000) D: [pulseaudio] sink.c: Suspend cause of sink alsa_output.pci-0000_00_1f.5.analog-stereo is 0x0004, suspending
( 164.314|   0.001) I: [alsa-sink-Intel ICH] alsa-sink.c: Device suspended...
( 164.314|   0.000) I: [pulseaudio] core.c: All sinks and sources are suspended, vacuuming memory
( 164.315|   0.001) D: [pulseaudio] module-udev-detect.c: /dev/snd/controlC0 is accessible: yes
( 164.315|   0.000) D: [pulseaudio] module-udev-detect.c: Resuming all sinks and sources of card alsa_card.pci-0000_00_1f.5.
( 166.203|   1.887) D: [alsa-sink-Intel ICH] alsa-sink.c: Requested volume: 0: 100% 1: 100%
( 166.203|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c:            in dB: 0: 0.00 dB 1: 0.00 dB
( 166.203|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Got hardware volume: 0: 100% 1: 100%
( 166.203|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c:               in dB: 0: 0.00 dB 1: 0.00 dB
( 166.203|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Calculated software volume: 0: 100% 1: 100% (accurate-enough=yes)
( 166.203|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c:                      in dB: 0: 0.00 dB 1: 0.00 dB
( 166.203|   0.000) D: [alsa-sink-Intel ICH] sink.c: Volume not changing
( 166.204|   0.000) D: [pulseaudio] module-suspend-on-idle.c: Sink alsa_output.pci-0000_00_1f.5.analog-stereo becomes idle, timeout in 5 seconds.
( 166.204|   0.000) D: [pulseaudio] core.c: Hmm, no streams around, trying to vacuum.
( 166.204|   0.000) I: [pulseaudio] sink-input.c: Freeing input 2 "AudioStream"
( 203.000|  36.796) I: [pulseaudio] main.c: Got signal SIGINT.
( 203.000|   0.000) I: [pulseaudio] main.c: Exiting.
( 203.001|   0.000) I: [pulseaudio] main.c: Daemon shutdown initiated.
( 203.001|   0.000) I: [pulseaudio] module.c: Unloading "module-filter-apply" (index: #16).
( 203.001|   0.000) I: [pulseaudio] module.c: Unloaded "module-filter-apply" (index: #16).
( 203.001|   0.000) I: [pulseaudio] module.c: Unloading "module-filter-heuristics" (index: #15).
( 203.001|   0.000) I: [pulseaudio] module.c: Unloaded "module-filter-heuristics" (index: #15).
( 203.001|   0.000) I: [pulseaudio] module.c: Unloading "module-position-event-sounds" (index: #14).
( 203.001|   0.000) I: [pulseaudio] module.c: Unloaded "module-position-event-sounds" (index: #14).
( 203.001|   0.000) I: [pulseaudio] module.c: Unloading "module-systemd-login" (index: #13).
( 203.001|   0.000) D: [pulseaudio] module-systemd-login.c: Removing session c1
( 203.001|   0.000) I: [pulseaudio] client.c: Freed 0 "Login Session c1"
( 203.001|   0.000) I: [pulseaudio] module.c: Unloaded "module-systemd-login" (index: #13).
( 203.001|   0.000) I: [pulseaudio] module.c: Unloading "module-suspend-on-idle" (index: #12).
( 203.001|   0.000) I: [pulseaudio] module.c: Unloaded "module-suspend-on-idle" (index: #12).
( 203.001|   0.000) I: [pulseaudio] module.c: Unloading "module-intended-roles" (index: #11).
( 203.002|   0.000) I: [pulseaudio] module.c: Unloaded "module-intended-roles" (index: #11).
( 203.002|   0.000) I: [pulseaudio] module.c: Unloading "module-always-sink" (index: #10).
( 203.002|   0.000) I: [pulseaudio] module.c: Unloaded "module-always-sink" (index: #10).
( 203.002|   0.000) I: [pulseaudio] module.c: Unloading "module-rescue-streams" (index: #9).
( 203.002|   0.000) I: [pulseaudio] module.c: Unloaded "module-rescue-streams" (index: #9).
( 203.002|   0.000) I: [pulseaudio] module.c: Unloading "module-default-device-restore" (index: #8).
( 203.002|   0.000) I: [pulseaudio] module.c: Unloaded "module-default-device-restore" (index: #8).
( 203.002|   0.000) I: [pulseaudio] module.c: Unloading "module-native-protocol-unix" (index: #7).
( 203.003|   0.000) I: [pulseaudio] client.c: Freed 1 "Ubuntu Audio Settings"
( 203.003|   0.000) I: [pulseaudio] client.c: Freed 5 "CubebUtils"
( 203.004|   0.000) I: [pulseaudio] module.c: Unloaded "module-native-protocol-unix" (index: #7).
( 203.004|   0.000) I: [pulseaudio] module.c: Unloading "module-udev-detect" (index: #6).
( 203.004|   0.000) I: [pulseaudio] module.c: Unloaded "module-udev-detect" (index: #6).
( 203.004|   0.000) I: [pulseaudio] module.c: Unloading "module-alsa-card" (index: #5).
( 203.005|   0.000) D: [alsa-sink-Intel ICH] alsa-sink.c: Thread shutting down
( 203.005|   0.000) I: [pulseaudio] sink.c: Freeing sink 0 "alsa_output.pci-0000_00_1f.5.analog-stereo"
( 203.005|   0.000) I: [pulseaudio] source.c: Freeing source 0 "alsa_output.pci-0000_00_1f.5.analog-stereo.monitor"
( 203.005|   0.000) D: [pulseaudio] core-subscribe.c: Dropped redundant event due to change event.
( 203.006|   0.000) D: [alsa-source-Intel ICH] alsa-source.c: Thread shutting down
( 203.006|   0.000) I: [pulseaudio] source.c: Freeing source 1 "alsa_input.pci-0000_00_1f.5.analog-stereo"
( 203.010|   0.004) I: [pulseaudio] card.c: Freed 0 "alsa_card.pci-0000_00_1f.5"
( 203.011|   0.000) D: [pulseaudio] ratelimit.c: 44 events suppressed
( 203.011|   0.000) D: [pulseaudio] flist.c: pulsecore/hashmap.c: entries flist is full (don't worry)
( 203.011|   0.000) D: [pulseaudio] flist.c: pulsecore/hashmap.c: entries flist is full (don't worry)
( 203.011|   0.000) D: [pulseaudio] flist.c: pulsecore/hashmap.c: entries flist is full (don't worry)
( 203.011|   0.000) D: [pulseaudio] flist.c: pulsecore/hashmap.c: entries flist is full (don't worry)
( 203.011|   0.000) D: [pulseaudio] flist.c: pulsecore/hashmap.c: entries flist is full (don't worry)
( 203.011|   0.000) D: [pulseaudio] flist.c: pulsecore/hashmap.c: entries flist is full (don't worry)
( 203.011|   0.000) D: [pulseaudio] flist.c: pulsecore/hashmap.c: entries flist is full (don't worry)
( 203.011|   0.000) D: [pulseaudio] flist.c: pulsecore/hashmap.c: entries flist is full (don't worry)
( 203.011|   0.000) D: [pulseaudio] flist.c: pulsecore/hashmap.c: entries flist is full (don't worry)
( 203.011|   0.000) D: [pulseaudio] flist.c: pulsecore/hashmap.c: entries flist is full (don't worry)
( 203.011|   0.000) D: [pulseaudio] flist.c: pulsecore/hashmap.c: entries flist is full (don't worry)
( 203.013|   0.001) I: [pulseaudio] module.c: Unloaded "module-alsa-card" (index: #5).
( 203.014|   0.000) I: [pulseaudio] module.c: Unloading "module-switch-on-port-available" (index: #4).
( 203.014|   0.000) I: [pulseaudio] module.c: Unloaded "module-switch-on-port-available" (index: #4).
( 203.014|   0.000) I: [pulseaudio] module.c: Unloading "module-augment-properties" (index: #3).
( 203.014|   0.000) I: [pulseaudio] module.c: Unloaded "module-augment-properties" (index: #3).
( 203.014|   0.000) I: [pulseaudio] module.c: Unloading "module-card-restore" (index: #2).
( 203.015|   0.000) I: [pulseaudio] module.c: Unloaded "module-card-restore" (index: #2).
( 203.015|   0.000) I: [pulseaudio] module.c: Unloading "module-stream-restore" (index: #1).
( 203.015|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1 removed from object /org/pulseaudio/stream_restore1
( 203.015|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry removed from object /org/pulseaudio/stream_restore1/entry0
( 203.015|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry removed from object /org/pulseaudio/stream_restore1/entry1
( 203.015|   0.000) I: [pulseaudio] module.c: Unloaded "module-stream-restore" (index: #1).
( 203.015|   0.000) I: [pulseaudio] module.c: Unloading "module-device-restore" (index: #0).
( 203.015|   0.000) I: [pulseaudio] module.c: Unloaded "module-device-restore" (index: #0).
( 203.016|   0.000) I: [pulseaudio] main.c: Daemon terminated.
  
```

---

### Post by walterramjet on 2016-03-12
this also happened to me, after several updates.  I found that by clicking on "system settings" (the little gear and wrench icon), my sound returned, but every time I login, I have to click on "system settings" before my sound works.  I can close system settings and my sound continues to work.   It was not just the most recent update, but on several other updates, as well.

---

### Post by eezacque on 2016-03-13
> **walterramjet said:**
> this also happened to me, after several updates.  I found that by clicking on "system settings" (the little gear and wrench icon), my sound returned, but every time I login, I have to click on "system settings" before my sound works.  I can close system settings and my sound continues to work.   It was not just the most recent update, but on several other updates, as well.

Could you be more specific about updates, version numbers, kernels, etc?

---

### Post by fall2 on 2016-03-17
A update made the problem worse!!!

Now after a system update I get a error when I try to open pulseaudio volume control.

"Fatal Error: Unable to connect to PulseAudio: OK"



Xubuntu OS Update broke my sound. I just got a USB sound card and I can't try it because now its more screwed up than before.

I am pretty mad, can someone please help me?

---

### Post by fall2 on 2016-03-17
I typed in the terminal commands again to test and they are different now.

~$ sudo aplay -l
**** List of PLAYBACK Hardware Devices ****
Home directory not accessible: Permission denied
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0




~$ lspci -v | grep -A7 -i "audio"
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
    Subsystem: Gateway, Inc. Device 0402
    Flags: bus master, medium devsel, latency 0, IRQ 10
    I/O ports at 1c00 [size=256]
    I/O ports at 1880 [size=64]
    Memory at e0100c00 (32-bit, non-prefetchable) [size=512]
    Memory at e0100800 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>


 ~$ killall pulseaudio; rm -r ~/.config/pulse; pulseaudio -k
pulseaudio: no process found
E: [pulseaudio] main.c: Failed to kill daemon: No such process



~$ rm -r ~/.config/pulse; pulseaudio -k
rm: cannot remove &#8216;/home/fall/.config/pulse&#8217;: No such file or directory
E: [pulseaudio] main.c: Failed to kill daemon: No such process

---

### Post by fall2 on 2016-03-18
I can open Pulse Audio now, I had to reset my laptop. The laptop still has no sound but I went and bought a USB sound card and I am now able to get sound through that.

---

### Post by walterramjet on 2016-03-20
eezacque,

sorry I did not reply sooner.  I thought I would get a notification if someone replied so I just waited for an email.  I will have to figure that out, later.  Anyway, I am using linux-image-4.2.0-35-generic.  beyond that, I dont know.  However, the sound problem I had, persists.  If I log out or restart my computer, upon returning, my sound will not work without starting "System Settings".  Thanks for the help.
Walt

---

