---
title: "Laptop speakers not working: Dell Inspiron 700m"
date: 2011-01-08
forum: Multimedia Software
---

### Post by skut on 2011-01-08
Hi - I'm a total linux beginner and so far enjoying my new install of Ubuntu 10.10

The only problem I've had so far seems to be a common one but I haven't found a specific solution for a dell inspiron 700m. I have sound through the headphones but not through the laptop internal speakers. 

I've played with the alsamixer settings endlessly but no success, and I'm 99% sure that it's not an issue with the hardware or speaker wiring.

I suspect I need to add an 'options snd-hda-intel model=xxxxx' line to alsa-base but not sure what argument to use.

Grateful if anyone has any suggestions..

Thanks

PS lspci -v output

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
    Subsystem: Dell Inspiron 700m/710m [SigmaTel STAC9750,51]
    Flags: bus master, medium devsel, latency 0, IRQ 10
    I/O ports at 1c00 [size=256]
    I/O ports at 18c0 [size=64]
    Memory at e0100c00 (32-bit, non-prefetchable) [size=512]
    Memory at e0100800 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0

---

### Post by BicyclerBoy on 2011-01-08
What output devices show up under gnome-menu system preferences sound: output tab ?

Install gnome alsa mixer check you get all the sliders ..

---

### Post by lidex on 2011-01-09
More info would be helpful. Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by skut on 2011-01-10
Hi Lidex

Thanks for helping me. I ran the script a couple of times, but it didn't give me a link. Output pasted below...

___________________________________________________________________________

tim@Skut:~$ wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh
--2011-01-10 22:23:52--  [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh)
Resolving [www.alsa-project.org](www.alsa-project.org)... 77.48.224.243
Connecting to [www.alsa-project.org|77.48.224.243|:80](www.alsa-project.org|77.48.224.243|:80)... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh](http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh) [following]
--2011-01-10 22:23:53--  [http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh](http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh)
Resolving git.alsa-project.org... 77.48.224.243
Reusing existing connection to [www.alsa-project.org:80](www.alsa-project.org:80).
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/plain]
Saving to: `alsa-info.sh'

    [  <=>                                                        ] 27,025      55.4K/s   in 0.5s    

2011-01-10 22:23:54 (55.4 KB/s) - `alsa-info.sh' saved [27025]

ALSA Information Script v 0.4.59
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactl
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)

See 'alsa-info.sh --help' for command line options.

Automatically upload ALSA information to [www.alsa-project.org?](www.alsa-project.org?) [y/N] : y
Uploading information to [www.alsa-project.org](www.alsa-project.org) ...  Done!

Your ALSA information is located at 
Please inform the person helping you.

---

### Post by lidex on 2011-01-13
That's no good. Try running it again, this time enter n at the prompt instead of y. It will save to your /tmp directory. Open it in your text editor, copy the text, then paste it into your next post enclosed in code tags. Easy way - just press the # in the toolbar and the tags will come up with the cursor inside them and all you need to do is press <Ctrl>+<v>

---

### Post by skut on 2011-01-13
OK, thanks. Here it is....

```
upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Fri Jan 14 00:26:56 UTC 2011


!!Linux Distribution
!!------------------

Ubuntu 10.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.10"


!!DMI Information
!!---------------

Manufacturer:      Dell Inc.
Product Name:      Inspiron 700m      
Product Version:   -1             


!!Kernel Information
!!------------------

Kernel release:    2.6.35-24-generic
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

snd_intel8x0


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

 0 [I82801DBICH4   ]: ICH4 - Intel 82801DB-ICH4
                      Intel 82801DB-ICH4 with STAC9750,51 at irq 10


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

00:1f.5 0401: 8086:24c5 (rev 03)
    Subsystem: 1028:018d


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

!!Module: snd_intel8x0
    ac97_clock : 0
    ac97_quirk : (null)
    buggy_irq : N
    buggy_semaphore : N
    enable : N
    id : (null)
    index : -1
    joystick : 0
    spdif_aclink : 0
    xbox : N


!!AC97 Codec information
!!---------------------------
--startcollapse--

0-0/0: SigmaTel STAC9750,51

PCI Subsys Vendor: 0x1028
PCI Subsys Device: 0x018d

Flags: 0
Capabilities     : -headphone out-
DAC resolution   : 20-bit
ADC resolution   : 20-bit
3D enhancement   : SigmaTel 3D Enhancement

Current setup
Mic gain         : +0dB [+0dB]
POP path         : pre 3D
Sim. stereo      : off
3D enhancement   : off
Loudness         : off
Mono output      : MIX
Mic select       : Mic1
ADC/DAC loopback : off
Extended ID      : codec=0 rev=1 AMAP DSA=0 VRA
Extended status  : VRA
PCM front DAC    : 44100Hz
PCM ADC          : 44100Hz

0:00 = 6a90
0:02 = 1a1a
0:04 = 0000
0:06 = 801f
0:08 = 0000
0:0a = 801e
0:0c = 801f
0:0e = 801f
0:10 = 9f1f
0:12 = 0606
0:14 = 9f1f
0:16 = 9f1f
0:18 = 0808
0:1a = 0000
0:1c = 0000
0:1e = 0000
0:20 = 0000
0:22 = 0000
0:24 = 0000
0:26 = 000f
0:28 = 0601
0:2a = 0001
0:2c = ac44
0:2e = 0000
0:30 = 0000
0:32 = ac44
0:34 = 0000
0:36 = 0000
0:38 = 0000
0:3a = 0000
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
0:7e = 7650
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116, 10 Jan 11 18:17 /dev/snd/controlC0
crw-rw----+ 1 root audio 116,  9 Jan 11 18:22 /dev/snd/pcmC0D0c
crw-rw----+ 1 root audio 116,  8 Jan 13 18:55 /dev/snd/pcmC0D0p
crw-rw----+ 1 root audio 116,  7 Jan 11 18:17 /dev/snd/pcmC0D1c
crw-rw----+ 1 root audio 116,  6 Jan 11 18:17 /dev/snd/pcmC0D2c
crw-rw----+ 1 root audio 116,  5 Jan 11 18:17 /dev/snd/pcmC0D3c
crw-rw----+ 1 root audio 116,  4 Jan 11 18:17 /dev/snd/pcmC0D4p
crw-rw----+ 1 root audio 116,  3 Jan 11 18:17 /dev/snd/seq
crw-rw----+ 1 root audio 116,  2 Jan 11 18:17 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Jan 11 18:17 .
drwxr-xr-x 3 root root 240 Jan 11 18:17 ..
lrwxrwxrwx 1 root root  12 Jan 11 18:17 pci-0000:00:1f.5 -> ../controlC0


!!Aplay/Arecord output
!!------------

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

Card hw:0 'I82801DBICH4'/'Intel 82801DB-ICH4 with STAC9750,51 at irq 10'
  Mixer name    : 'SigmaTel STAC9750,51'
  Components    : 'AC97a:83847650'
  Controls      : 33
  Simple ctrls  : 22
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 5 [16%] [-39.00dB] [on]
  Front Right: Playback 5 [16%] [-39.00dB] [on]
Simple mixer control 'Master Mono',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-46.50dB] [off]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control '3D Control - Center',0
  Capabilities: volume volume-joined penum
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 15
  Mono: 0 [0%]
Simple mixer control '3D Control - Depth',0
  Capabilities: volume volume-joined penum
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 15
  Mono: 0 [0%]
Simple mixer control '3D Control - Switch',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 23 [74%] [0.00dB] [on]
  Front Right: Playback 23 [74%] [0.00dB] [on]
Simple mixer control 'PCM Out Path & Mute',0
  Capabilities: enum
  Items: 'pre 3D' 'post 3D'
  Item0: 'pre 3D'
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [-34.50dB] [off] Capture [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off] Capture [off]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 25 [81%] [3.00dB] [on] Capture [off]
  Front Right: Playback 25 [81%] [3.00dB] [on] Capture [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-34.50dB] [off]
  Front Left: Capture [on]
  Front Right: Capture [on]
Simple mixer control 'Mic Boost (+20dB)',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Mic Select',0
  Capabilities: enum
  Items: 'Mic1' 'Mic2'
  Item0: 'Mic1'
Simple mixer control 'Video',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [-34.50dB] [off] Capture [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off] Capture [off]
Simple mixer control 'Phone',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-34.50dB] [off]
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Beep',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 15
  Mono: Playback 0 [0%] [-45.00dB] [off]
Simple mixer control 'Aux',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [-34.50dB] [off] Capture [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off] Capture [off]
Simple mixer control 'Mono Output Select',0
  Capabilities: enum
  Items: 'Mix' 'Mic'
  Item0: 'Mix'
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
  Mono: Playback [on]


!!Alsactl output
!!-------------

--startcollapse--
state.I82801DBICH4 {
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
        value.0 5
        value.1 5
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
        name 'Master Mono Playback Switch'
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
        name 'Master Mono Playback Volume'
        value 0
    }
    control.7 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Beep Playback Switch'
        value false
    }
    control.8 {
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
    control.9 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Phone Playback Switch'
        value false
    }
    control.10 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'Phone Playback Volume'
        value 0
    }
    control.11 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Mic Playback Switch'
        value false
    }
    control.12 {
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
    control.13 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Mic Boost (+20dB)'
        value false
    }
    control.14 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Line Playback Switch'
        value false
    }
    control.15 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'Line Playback Volume'
        value.0 0
        value.1 0
    }
    control.16 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'CD Playback Switch'
        value true
    }
    control.17 {
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
    control.18 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Video Playback Switch'
        value false
    }
    control.19 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'Video Playback Volume'
        value.0 0
        value.1 0
    }
    control.20 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Aux Playback Switch'
        value false
    }
    control.21 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'Aux Playback Volume'
        value.0 0
        value.1 0
    }
    control.22 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'PCM Playback Switch'
        value true
    }
    control.23 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'PCM Playback Volume'
        value.0 23
        value.1 23
    }
    control.24 {
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
    control.25 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Capture Switch'
        value true
    }
    control.26 {
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
    control.27 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 1
        comment.item.0 'pre 3D'
        comment.item.1 'post 3D'
        iface MIXER
        name 'PCM Out Path & Mute'
        value 'pre 3D'
    }
    control.28 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name '3D Control - Switch'
        value false
    }
    control.29 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 1
        comment.item.0 Mix
        comment.item.1 Mic
        iface MIXER
        name 'Mono Output Select'
        value Mix
    }
    control.30 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 1
        comment.item.0 Mic1
        comment.item.1 Mic2
        iface MIXER
        name 'Mic Select'
        value Mic1
    }
    control.31 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 15'
        iface MIXER
        name '3D Control - Center'
        value 0
    }
    control.32 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 15'
        iface MIXER
        name '3D Control - Depth'
        value 0
    }
    control.33 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'External Amplifier'
        value true
    }
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
lib80211_crypt_ccmp
aes_i586
aes_generic
binfmt_misc
dm_crypt
joydev
snd_intel8x0
snd_ac97_codec
ac97_bus
snd_pcm
snd_seq_midi
pcmcia
snd_rawmidi
snd_seq_midi_event
ipw2200
snd_seq
libipw
snd_timer
snd_seq_device
cfg80211
tifm_7xx1
dell_wmi_aio
tifm_core
snd
yenta_socket
pcmcia_rsrc
dell_laptop
psmouse
dcdbas
serio_raw
lib80211
pcmcia_core
soundcore
shpchp
snd_page_alloc
ppdev
parport_pc
lp
parport
i915
drm_kms_helper
drm
i2c_algo_bit
b44
intel_agp
firewire_ohci
ssb
video
firewire_core
crc_itu_t
mii
output
agpgart


!!ALSA/HDA dmesg
!!------------------


```

---

### Post by lidex on 2011-01-13
So have you tried switching off the external amplifier (EAPD)?I can also see some values that are low, try boosting them-with eapd off and on.
```
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback [COLOR="Red"]0 - 31[/COLOR]
  Mono:
  Front Left: [COLOR="Red"]Playback 5[/COLOR] [16%] [-39.00dB] [on]
  Front Right: [COLOR="Red"]Playback 5[/COLOR] [16%] [-39.00dB] [on]
Simple mixer control 'Master Mono',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: [COLOR="Red"]Playback 0 [0%] [-46.50dB] [off][/COLOR]

```

---

### Post by skut on 2011-01-14
H i - I tried both your suggestions but still no luck I'm afraid. This is the latest output.

```

!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Sat Jan 15 00:36:06 UTC 2011


!!Linux Distribution
!!------------------

Ubuntu 10.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.10"


!!DMI Information
!!---------------

Manufacturer:      Dell Inc.
Product Name:      Inspiron 700m      
Product Version:   -1             


!!Kernel Information
!!------------------

Kernel release:    2.6.35-24-generic
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

snd_intel8x0


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

 0 [I82801DBICH4   ]: ICH4 - Intel 82801DB-ICH4
                      Intel 82801DB-ICH4 with STAC9750,51 at irq 10


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

00:1f.5 0401: 8086:24c5 (rev 03)
    Subsystem: 1028:018d


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

!!Module: snd_intel8x0
    ac97_clock : 0
    ac97_quirk : (null)
    buggy_irq : N
    buggy_semaphore : N
    enable : N
    id : (null)
    index : -1
    joystick : 0
    spdif_aclink : 0
    xbox : N


!!AC97 Codec information
!!---------------------------
--startcollapse--

0-0/0: SigmaTel STAC9750,51

PCI Subsys Vendor: 0x1028
PCI Subsys Device: 0x018d

Flags: 0
Capabilities     : -headphone out-
DAC resolution   : 20-bit
ADC resolution   : 20-bit
3D enhancement   : SigmaTel 3D Enhancement

Current setup
Mic gain         : +0dB [+0dB]
POP path         : pre 3D
Sim. stereo      : off
3D enhancement   : on
Loudness         : off
Mono output      : MIX
Mic select       : Mic1
ADC/DAC loopback : off
Extended ID      : codec=0 rev=1 AMAP DSA=0 VRA
Extended status  : VRA
PCM front DAC    : 44100Hz
PCM ADC          : 44100Hz

0:00 = 6a90
0:02 = 0000
0:04 = 0000
0:06 = 0000
0:08 = 0000
0:0a = 801e
0:0c = 801f
0:0e = 801f
0:10 = 9f1f
0:12 = 0606
0:14 = 0202
0:16 = 0000
0:18 = 0000
0:1a = 0000
0:1c = 0000
0:1e = 0000
0:20 = 2000
0:22 = 000c
0:24 = 0000
0:26 = 000f
0:28 = 0601
0:2a = 0001
0:2c = ac44
0:2e = 0000
0:30 = 0000
0:32 = ac44
0:34 = 0000
0:36 = 0000
0:38 = 0000
0:3a = 0000
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
0:7e = 7650
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116, 10 Jan 14 17:38 /dev/snd/controlC0
crw-rw----+ 1 root audio 116,  9 Jan 14 19:33 /dev/snd/pcmC0D0c
crw-rw----+ 1 root audio 116,  8 Jan 14 17:40 /dev/snd/pcmC0D0p
crw-rw----+ 1 root audio 116,  7 Jan 14 17:38 /dev/snd/pcmC0D1c
crw-rw----+ 1 root audio 116,  6 Jan 14 17:38 /dev/snd/pcmC0D2c
crw-rw----+ 1 root audio 116,  5 Jan 14 17:38 /dev/snd/pcmC0D3c
crw-rw----+ 1 root audio 116,  4 Jan 14 17:38 /dev/snd/pcmC0D4p
crw-rw----+ 1 root audio 116,  3 Jan 14 17:38 /dev/snd/seq
crw-rw----+ 1 root audio 116,  2 Jan 14 17:38 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Jan 14 17:38 .
drwxr-xr-x 3 root root 240 Jan 14 17:38 ..
lrwxrwxrwx 1 root root  12 Jan 14 17:38 pci-0000:00:1f.5 -> ../controlC0


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 0/1
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

Card hw:0 'I82801DBICH4'/'Intel 82801DB-ICH4 with STAC9750,51 at irq 10'
  Mixer name    : 'SigmaTel STAC9750,51'
  Components    : 'AC97a:83847650'
  Controls      : 33
  Simple ctrls  : 22
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Master Mono',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control '3D Control - Center',0
  Capabilities: volume volume-joined penum
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 15
  Mono: 15 [100%]
Simple mixer control '3D Control - Depth',0
  Capabilities: volume volume-joined penum
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 15
  Mono: 15 [100%]
Simple mixer control '3D Control - Switch',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch pswitch-joined penum
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
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [-34.50dB] [off] Capture [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off] Capture [off]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 25 [81%] [3.00dB] [on] Capture [off]
  Front Right: Playback 25 [81%] [3.00dB] [on] Capture [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-34.50dB] [off]
  Front Left: Capture [on]
  Front Right: Capture [on]
Simple mixer control 'Mic Boost (+20dB)',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Mic Select',0
  Capabilities: enum
  Items: 'Mic1' 'Mic2'
  Item0: 'Mic1'
Simple mixer control 'Video',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 29 [94%] [9.00dB] [on] Capture [off]
  Front Right: Playback 29 [94%] [9.00dB] [on] Capture [off]
Simple mixer control 'Phone',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-34.50dB] [off]
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Beep',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 15
  Mono: Playback 0 [0%] [-45.00dB] [off]
Simple mixer control 'Aux',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 31 [100%] [12.00dB] [on] Capture [off]
  Front Right: Playback 31 [100%] [12.00dB] [on] Capture [off]
Simple mixer control 'Mono Output Select',0
  Capabilities: enum
  Items: 'Mix' 'Mic'
  Item0: 'Mix'
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
  Mono: Playback [on]


!!Alsactl output
!!-------------

--startcollapse--
state.I82801DBICH4 {
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
        value.0 31
        value.1 31
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
        name 'Master Mono Playback Switch'
        value true
    }
    control.6 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 31'
        comment.dbmin -4650
        comment.dbmax 0
        iface MIXER
        name 'Master Mono Playback Volume'
        value 31
    }
    control.7 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Beep Playback Switch'
        value false
    }
    control.8 {
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
    control.9 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Phone Playback Switch'
        value false
    }
    control.10 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'Phone Playback Volume'
        value 0
    }
    control.11 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Mic Playback Switch'
        value false
    }
    control.12 {
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
    control.13 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Mic Boost (+20dB)'
        value false
    }
    control.14 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Line Playback Switch'
        value false
    }
    control.15 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'Line Playback Volume'
        value.0 0
        value.1 0
    }
    control.16 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'CD Playback Switch'
        value true
    }
    control.17 {
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
    control.18 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Video Playback Switch'
        value true
    }
    control.19 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'Video Playback Volume'
        value.0 29
        value.1 29
    }
    control.20 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Aux Playback Switch'
        value true
    }
    control.21 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'Aux Playback Volume'
        value.0 31
        value.1 31
    }
    control.22 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'PCM Playback Switch'
        value true
    }
    control.23 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'PCM Playback Volume'
        value.0 31
        value.1 31
    }
    control.24 {
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
    control.25 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Capture Switch'
        value true
    }
    control.26 {
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
    control.27 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 1
        comment.item.0 'pre 3D'
        comment.item.1 'post 3D'
        iface MIXER
        name 'PCM Out Path & Mute'
        value 'pre 3D'
    }
    control.28 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name '3D Control - Switch'
        value true
    }
    control.29 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 1
        comment.item.0 Mix
        comment.item.1 Mic
        iface MIXER
        name 'Mono Output Select'
        value Mix
    }
    control.30 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 1
        comment.item.0 Mic1
        comment.item.1 Mic2
        iface MIXER
        name 'Mic Select'
        value Mic1
    }
    control.31 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 15'
        iface MIXER
        name '3D Control - Center'
        value 15
    }
    control.32 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 15'
        iface MIXER
        name '3D Control - Depth'
        value 15
    }
    control.33 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'External Amplifier'
        value true
    }
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
lib80211_crypt_ccmp
aes_i586
aes_generic
binfmt_misc
dm_crypt
joydev
snd_intel8x0
snd_ac97_codec
ac97_bus
pcmcia
snd_pcm
snd_seq_midi
snd_rawmidi
ipw2200
snd_seq_midi_event
snd_seq
libipw
snd_timer
snd_seq_device
cfg80211
tifm_7xx1
yenta_socket
tifm_core
dell_wmi_aio
pcmcia_rsrc
dell_laptop
snd
psmouse
dcdbas
lib80211
pcmcia_core
soundcore
serio_raw
shpchp
snd_page_alloc
ppdev
parport_pc
lp
parport
i915
drm_kms_helper
drm
b44
firewire_ohci
intel_agp
ssb
i2c_algo_bit
firewire_core
video
agpgart
mii
crc_itu_t
output


!!ALSA/HDA dmesg
!!------------------


```

---

### Post by lidex on 2011-01-15
Try this in a terminal (to edit alsa-base.conf):
```
echo "options snd-intel8x0 inv_eapd=1" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---

### Post by skut on 2011-01-15
Hi - I tried as you suggested and now there is no sound at all, not even through the headphones. The speaker icon has disappeared from the top bar, and I can't open alsamixer from the terminal.

```
tim@Skut:~$ alsamixer
cannot open mixer: No such file or directory

```

Sorry - I'm sure there is a simple way to restore alsamixer, but I'm not too sure how?

Thank you for your patience with a newbie.

---

### Post by lidex on 2011-01-16
> **skut said:**
> Hi - I tried as you suggested and now there is no sound at all, not even through the headphones. The speaker icon has disappeared from the top bar, and I can't open alsamixer from the terminal.

```
tim@Skut:~$ alsamixer
cannot open mixer: No such file or directory

```

Sorry - I'm sure there is a simple way to restore alsamixer, but I'm not too sure how?

Thank you for your patience with a newbie.
It's not patience, it's drugs ;)
But I kid. I'm kinda making this up as I go along as there is no reference for this particular codec/hardware/problem. Open alsa-base.conf:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
``` and edit this line:
```
options snd-intel8x0 inv_eapd=1
```
Change the 1 to 0 and reboot. If still no joy re-open file and remove entire line.

---

### Post by skut on 2011-01-16
No luck with changing the setting to 0 I'm afraid. I removed the line and the headphones work again, but still nothing on the speakers.

Any other ideas gratefully received!! :)  Thnx

---

### Post by esilva on 2011-11-06
Sound not coming out of speakers, only headphones, on laptop FIXED.

The speakers on my laptop Dell Studio XPS 1640 were not working after experimenting with several modules and models, I decided to give it a try on Windows (should've try it sooner, try it first if you are doing double boot), I was expecting them to work but they did not, which meant it was a problem in the hardware not the codecs, module or model.

The codec of my sound card is using on ubuntu 11.10 is 'STAC92HD73', I added the following option to my alsa-base.conf file and rebooted.

#add this at the end of /etc/modprobe.d/alsa-base.conf
options snd-hda-intel model=no-jd

After reboot sound is comming out from both laptop speakers and headphone jacks (at the same time, but no biggie just go to sound settings and select 'analog headphones' for output when only listening to headphones), it seems the headphone jack-detection broke and that is why sound was not comming out of the speakers. Adding the no-jd (no jack detection) fixed the issue.

Hope this helps, it was driving me nuts for the last two weeks.

---

### Post by andypag on 2011-12-31
Hi there. I have the same sound card and the same problem in a panasonic toughbook. Did you ever solve this?

---

### Post by MoreOrLess on 2011-12-31
andypag, please provide your alsa info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

