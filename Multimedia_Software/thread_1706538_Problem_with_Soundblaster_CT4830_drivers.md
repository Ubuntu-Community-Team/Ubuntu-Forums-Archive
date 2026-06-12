---
title: "Problem with Soundblaster CT4830 drivers"
date: 2011-03-14
forum: Multimedia Software
---

### Post by johnson094 on 2011-03-14
Just completed a fresh install of Ubuntu 10.10.1 with all updates completed.  I am running an Asus computer, Pentium 4 processor on an old Asus P4B266 motherboard.  I have 2 gigs of RAM and a 160 Gb hard drive.  I have a Soundblaster Live CT4830 sound card.   I am running Windows XP in front of and alongside Ubuntu
on the same hard drive.  

I have spent the whole day working on setting up my preferences and all updates have been completed.  When I started loading my music files I realized I had no sound when in Ubuntu.  I then checked my system alert sounds and these were also not functioning.  When in Windows all sound works fine.

I have googled and searched the forums for Linux drivers for this hardware without luck.  I read that Alsa drivers were preloaded on Ubuntu 10.04 and covered almost every sound card.  I read something about editing my /etc/modprobe.d/alsa-base.conf  and adding the line "options snd-hda-intel model=ref" to the end of this script in order to activate the sound.  I did this without success and then re-edited the file and removed it.

I looked at the Synaptic Package Manager and installed a couple of Alsa packages, one being alsa-firmware-loaders but, being really new at this I had no idea what to do with it.  I checked Harware Drivers and found no proprietary drivers installed which led me to believe that I could just download and install the regular drivers for my card.  I did this but was unable to open the zip files.

Long story short I have done all I can do within my skill level to solve this problem.  I would appreciate if one of you guys could verify whether or not this sound card will even work in Ubuntu.  I would also appreciate someone steering me to some guidelines, tutorials, etc that might be of use to me.

I will enclose a copy of my /etc/modprobe.d/alsa-base.conf file in a new post to follow.

Thanks in advance for your help

David   ](*,)

---

### Post by johnson094 on 2011-03-14
Here is a copy of my /etc/modprobe.d/alsa-base.conf file just in case it may show what is going on.  Again having come over from Windows just last year, all I know about code is that I click on it and it happens and in the event it doesn't happen, a box opens up to tell me what to do next.

```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2

```

Thanks

David

---

### Post by johnson094 on 2011-03-14
I wanted to also make my Alsa Information Script available in case it is needed.  I did notice that I have a second sound controller.  I'm checking now to see if it is installed and if there might be a conflict.  I am going to also change over to the onboard to see if that makes a difference.

```
upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Mon Mar 14 06:15:14 UTC 2011


!!Linux Distribution
!!------------------

Ubuntu 10.04.2 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.04.2 LTS"


!!DMI Information
!!---------------

Manufacturer:      System Manufacturer
Product Name:      System Name
Product Version:   System Version


!!Kernel Information
!!------------------

Kernel release:    2.6.32-29-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.21
Library version:    1.0.22
Utilities version:  1.0.22


!!Loaded ALSA modules
!!-------------------

snd_emu10k1
snd_cmipci


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

 0 [Live           ]: EMU10K1 - SB Live! Value [CT4831]
                      SB Live! Value [CT4831] (rev.7, serial:0x80311102) at 0xd400, irq 23
 1 [CMI8738        ]: CMI8738-MC6 - C-Media CMI8738
                      C-Media CMI8738 (model 55) at 0xd800, irq 21


!!PCI Soundcards installed in the system
!!--------------------------------------

02:03.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
02:0b.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

02:03.0 0401: 13f6:0111 (rev 10)
    Subsystem: 1043:80e2
--
02:0b.0 0401: 1102:0002 (rev 07)
    Subsystem: 1102:8031


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

!!Module: snd_emu10k1
    delay_pcm_irq : 2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2
    enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
    enable_ir : N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N
    extin : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    extout : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
    index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    max_buffer_size : 128,128,128,128,128,128,128,128,128,128,128,128,128,128,128,128,128,128,128,128,128,128,128,128,128,128,128,128,128,128,128,128
    max_synth_voices : 64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64
    seq_ports : 4,4,4,4,4,4,4,4,4,4,4,4,4,4,4,4,4,4,4,4,4,4,4,4,4,4,4,4,4,4,4,4
    subsystem : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0

!!Module: snd_cmipci
    enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
    fm_port : 904,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1
    id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
    index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    joystick_port : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    mpu_port : 816,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    soft_ac3 : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y


!!AC97 Codec information
!!---------------------------
--startcollapse--

0-0/0: SigmaTel STAC9721,23

PCI Subsys Vendor: 0x0000
PCI Subsys Device: 0x0000

Flags: 0
Capabilities     :
DAC resolution   : 18-bit
ADC resolution   : 18-bit
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
Extended ID      : codec=0 rev=0 AMAP DSA=0
Extended status  : PRJ

0:00 = 6940
0:02 = 0606
0:04 = 8000
0:06 = 801f
0:08 = 0000
0:0a = 801e
0:0c = 801f
0:0e = 801f
0:10 = 9f1f
0:12 = 0606
0:14 = 9f1f
0:16 = 9f1f
0:18 = 0606
0:1a = 0000
0:1c = 0000
0:1e = 0000
0:20 = 0000
0:22 = 0000
0:24 = 0000
0:26 = 000f
0:28 = 0200
0:2a = 1000
0:2c = 0000
0:2e = 0000
0:30 = 0000
0:32 = 0000
0:34 = 0000
0:36 = 0000
0:38 = 0000
0:3a = 0000
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
0:5c = 0000
0:5e = 0000
0:60 = 0000
0:62 = 0000
0:64 = 0000
0:66 = 0000
0:68 = 0000
0:6a = 0000
0:6c = 0082
0:6e = 0000
0:70 = 0000
0:72 = 0000
0:74 = 0380
0:76 = 0000
0:78 = 8380
0:7a = 0000
0:7c = 8384
0:7e = 7609
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116, 12 Mar 14 01:39 /dev/snd/controlC0
crw-rw----+ 1 root audio 116, 20 Mar 14 01:39 /dev/snd/controlC1
crw-rw----+ 1 root audio 116,  4 Mar 14 01:39 /dev/snd/hwC0D0
crw-rw----+ 1 root audio 116, 21 Mar 14 01:39 /dev/snd/hwC0D2
crw-rw----+ 1 root audio 116, 19 Mar 14 01:39 /dev/snd/hwC1D0
crw-rw----+ 1 root audio 116,  5 Mar 14 01:39 /dev/snd/midiC0D0
crw-rw----+ 1 root audio 116, 22 Mar 14 01:39 /dev/snd/midiC0D1
crw-rw----+ 1 root audio 116, 23 Mar 14 01:39 /dev/snd/midiC0D2
crw-rw----+ 1 root audio 116, 13 Mar 14 01:39 /dev/snd/midiC1D0
crw-rw----+ 1 root audio 116, 11 Mar 14 01:40 /dev/snd/pcmC0D0c
crw-rw----+ 1 root audio 116, 10 Mar 14 01:40 /dev/snd/pcmC0D0p
crw-rw----+ 1 root audio 116,  9 Mar 14 01:39 /dev/snd/pcmC0D1c
crw-rw----+ 1 root audio 116,  8 Mar 14 01:39 /dev/snd/pcmC0D2c
crw-rw----+ 1 root audio 116,  7 Mar 14 01:40 /dev/snd/pcmC0D2p
crw-rw----+ 1 root audio 116,  6 Mar 14 01:39 /dev/snd/pcmC0D3p
crw-rw----+ 1 root audio 116, 18 Mar 14 01:40 /dev/snd/pcmC1D0c
crw-rw----+ 1 root audio 116, 17 Mar 14 00:41 /dev/snd/pcmC1D0p
crw-rw----+ 1 root audio 116, 16 Mar 14 01:40 /dev/snd/pcmC1D1p
crw-rw----+ 1 root audio 116, 15 Mar 14 01:40 /dev/snd/pcmC1D2c
crw-rw----+ 1 root audio 116, 14 Mar 14 01:40 /dev/snd/pcmC1D2p
crw-rw----+ 1 root audio 116,  3 Mar 14 01:39 /dev/snd/seq
crw-rw----+ 1 root audio 116,  2 Mar 14 01:39 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  80 Mar 14 01:39 .
drwxr-xr-x 3 root root 500 Mar 14 01:39 ..
lrwxrwxrwx 1 root root  12 Mar 14 01:39 pci-0000:02:03.0 -> ../controlC1
lrwxrwxrwx 1 root root  12 Mar 14 01:39 pci-0000:02:0b.0 -> ../controlC0


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: Live [SB Live! Value [CT4831]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 0: Live [SB Live! Value [CT4831]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Live [SB Live! Value [CT4831]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CMI8738 [C-Media CMI8738], device 0: CMI8738-MC6 [C-Media PCI DAC/ADC]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: CMI8738 [C-Media CMI8738], device 1: CMI8738-MC6 [C-Media PCI 2nd DAC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CMI8738 [C-Media CMI8738], device 2: CMI8738-MC6 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: Live [SB Live! Value [CT4831]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Live [SB Live! Value [CT4831]], device 1: emu10k1 mic [Mic Capture]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Live [SB Live! Value [CT4831]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CMI8738 [C-Media CMI8738], device 0: CMI8738-MC6 [C-Media PCI DAC/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CMI8738 [C-Media CMI8738], device 2: CMI8738-MC6 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [Live]

Card hw:0 'Live'/'SB Live! Value [CT4831] (rev.7, serial:0x80311102) at 0xd400, irq 23'
  Mixer name    : 'SigmaTel STAC9721,23'
  Components    : 'AC97a:83847609'
  Controls      : 220
  Simple ctrls  : 42
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 25 [81%] [-9.00dB] [on]
  Front Right: Playback 25 [81%] [-9.00dB] [on]
Simple mixer control 'Headphone LFE',1
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Headphone',1
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100
  Mono:
  Front Left: Playback 80 [80%] [-8.00dB]
  Front Right: Playback 80 [80%] [-8.00dB]
Simple mixer control 'Headphone Center',1
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Tone',0
  Capabilities: pswitch penum
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [off]
  Front Right: Playback [off]
Simple mixer control 'Bass',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 40
  Front Left: 20 [50%]
  Front Right: 20 [50%]
Simple mixer control 'Treble',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 40
  Front Left: 20 [50%]
  Front Right: 20 [50%]
Simple mixer control '3D Control - Switch',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control '3D Control Sigmatel - Depth',0
  Capabilities: volume volume-joined penum
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 3
  Mono: 0 [0%]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 25 [81%] [3.00dB] [on]
  Front Right: Playback 25 [81%] [3.00dB] [on]
Simple mixer control 'Front',0
  Capabilities: cvolume cswitch cswitch-joined penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 100
  Front Left: Capture 80 [80%] [-8.00dB] [off]
  Front Right: Capture 80 [80%] [-8.00dB] [off]
Simple mixer control 'Surround',0
  Capabilities: pvolume cvolume cswitch penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 100 [100%] [0.00dB] Capture 0 [0%] [-99999.99dB] [off]
  Front Right: Playback 100 [100%] [0.00dB] Capture 0 [0%] [-99999.99dB] [off]
Simple mixer control 'Surround Phase Inversion',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 100
  Mono: Playback 100 [100%] [0.00dB]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 100
  Mono: Playback 100 [100%] [0.00dB]
Simple mixer control 'Synth',0
  Capabilities: pvolume cvolume cswitch penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 80 [80%] [-8.00dB] Capture 80 [80%] [-8.00dB] [off]
  Front Right: Playback 80 [80%] [-8.00dB] Capture 80 [80%] [-8.00dB] [off]
Simple mixer control 'Wave',0
  Capabilities: pvolume cvolume cswitch penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 80 [80%] [-8.00dB] Capture 80 [80%] [-8.00dB] [off]
  Front Right: Playback 80 [80%] [-8.00dB] Capture 80 [80%] [-8.00dB] [off]
Simple mixer control 'Wave Center',0
  Capabilities: pvolume pvolume-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 100
  Mono: Playback 0 [0%] [-99999.99dB]
Simple mixer control 'Wave LFE',0
  Capabilities: pvolume pvolume-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 100
  Mono: Playback 0 [0%] [-99999.99dB]
Simple mixer control 'Wave Surround',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100
  Mono:
  Front Left: Playback 0 [0%] [-99999.99dB]
  Front Right: Playback 0 [0%] [-99999.99dB]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [-34.50dB] [off] Capture [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off] Capture [off]
Simple mixer control 'Line LiveDrive',0
  Capabilities: pvolume cvolume cswitch penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 0 [0%] [-99999.99dB] Capture 0 [0%] [-99999.99dB] [off]
  Front Right: Playback 0 [0%] [-99999.99dB] Capture 0 [0%] [-99999.99dB] [off]
Simple mixer control 'Line2 LiveDrive',1
  Capabilities: pvolume cvolume cswitch penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 0 [0%] [-99999.99dB] Capture 0 [0%] [-99999.99dB] [off]
  Front Right: Playback 0 [0%] [-99999.99dB] Capture 0 [0%] [-99999.99dB] [off]
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
Simple mixer control 'IEC958 Coaxial',0
  Capabilities: pvolume cvolume cswitch penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 0 [0%] [-99999.99dB] Capture 0 [0%] [-99999.99dB] [off]
  Front Right: Playback 0 [0%] [-99999.99dB] Capture 0 [0%] [-99999.99dB] [off]
Simple mixer control 'IEC958 LiveDrive',0
  Capabilities: pvolume cvolume cswitch penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 0 [0%] [-99999.99dB] Capture 0 [0%] [-99999.99dB] [off]
  Front Right: Playback 0 [0%] [-99999.99dB] Capture 0 [0%] [-99999.99dB] [off]
Simple mixer control 'IEC958 Optical Raw',0
  Capabilities: pswitch penum
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [off]
  Front Right: Playback [off]
Simple mixer control 'IEC958 TTL',0
  Capabilities: pvolume cvolume cswitch penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 0 [0%] [-99999.99dB] Capture 0 [0%] [-99999.99dB] [off]
  Front Right: Playback 0 [0%] [-99999.99dB] Capture 0 [0%] [-99999.99dB] [off]
Simple mixer control 'PC Speaker',0
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
Simple mixer control 'AC97',0
  Capabilities: pvolume cvolume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 80 [80%] [-8.00dB] Capture 80 [80%] [-8.00dB]
  Front Right: Playback 80 [80%] [-8.00dB] Capture 80 [80%] [-8.00dB]
Simple mixer control 'External Amplifier',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'SB Live Analog/Digital Output Jack',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Sigmatel 4-Speaker Stereo',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]

!!-------Mixer controls for card 1 [CMI8738]

Card hw:1 'CMI8738'/'C-Media CMI8738 (model 55) at 0xd800, irq 21'
  Mixer name    : 'CMedia PCI'
  Components    : ''
  Controls      : 41
  Simple ctrls  : 22
Simple mixer control 'Master',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 25 [81%]
  Front Right: Playback 25 [81%]
Simple mixer control '3D Control - Switch',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch pswitch-joined cswitch penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 25 [81%] [on] Capture [off]
  Front Right: Playback 25 [81%] [on] Capture [off]
Simple mixer control 'Synth',0
  Capabilities: pvolume pswitch pswitch-joined cswitch penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 25 [81%] [on] Capture [off]
  Front Right: Playback 25 [81%] [on] Capture [off]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch cswitch penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [off] Capture [off]
  Front Right: Playback 0 [0%] [off] Capture [off]
Simple mixer control 'Line-In Mode',0
  Capabilities: enum
  Items: 'Line-In' 'Rear Output' 'Bass Output'
  Item0: 'Line-In'
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch cswitch penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 25 [81%] [on] Capture [off]
  Front Right: Playback 25 [81%] [on] Capture [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pvolume-joined cvolume cvolume-joined pswitch pswitch-joined cswitch cswitch-joined penum
  Playback channels: Mono
  Capture channels: Mono
  Limits: Playback 0 - 31 Capture 0 - 7
  Mono: Playback 0 [0%] [off] Capture 0 [0%] [off]
Simple mixer control 'Mic Boost',0
  Capabilities: pswitch pswitch-joined cswitch cswitch-joined penum
  Playback channels: Mono
  Capture channels: Mono
  Mono: Playback [off] Capture [on]
Simple mixer control 'Mic-In Mode',0
  Capabilities: enum
  Items: 'Mic-In' 'Center/LFE Output'
  Item0: 'Center/LFE Output'
Simple mixer control 'Phone',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 7
  Mono: Playback 0 [0%] [off]
Simple mixer control 'IEC958 5V',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958 Copyright',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 In Monitor',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 In Phase Inverse',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 In Select',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 In Valid',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 Loop',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 Output',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'PC Speaker',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 3
  Mono: Playback 2 [67%] [on]
Simple mixer control 'Aux',0
  Capabilities: pvolume pswitch cswitch penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 15
  Front Left: Playback 0 [0%] [off] Capture [off]
  Front Right: Playback 0 [0%] [off] Capture [off]
Simple mixer control 'Four Channel Mode',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]


!!Alsactl output
!!-------------

--startcollapse--
state.Live {
    control.1 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 100'
        comment.dbmin -4000
        comment.dbmax 0
        iface MIXER
        name 'Wave Playback Volume'
        value.0 80
        value.1 80
    }
    control.2 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 100'
        comment.dbmin -4000
        comment.dbmax 0
        iface MIXER
        name 'Wave Surround Playback Volume'
        value.0 0
        value.1 0
    }
    control.3 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 100'
        comment.dbmin -4000
        comment.dbmax 0
        iface MIXER
        name 'Wave Center Playback Volume'
        value 0
    }
    control.4 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 100'
        comment.dbmin -4000
        comment.dbmax 0
        iface MIXER
        name 'Wave LFE Playback Volume'
        value 0
    }
    control.5 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 100'
        comment.dbmin -4000
        comment.dbmax 0
        iface MIXER
        name 'Wave Capture Volume'
        value.0 80
        value.1 80
    }
    control.6 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Wave Capture Switch'
        value.0 false
        value.1 false
    }
    control.7 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 100'
        comment.dbmin -4000
        comment.dbmax 0
        iface MIXER
        name 'Synth Playback Volume'
        value.0 80
        value.1 80
    }
    control.8 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 100'
        comment.dbmin -4000
        comment.dbmax 0
        iface MIXER
        name 'Synth Capture Volume'
        value.0 80
        value.1 80
    }
    control.9 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Synth Capture Switch'
        value.0 false
        value.1 false
    }
    control.10 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 100'
        comment.dbmin -4000
        comment.dbmax 0
        iface MIXER
        name 'Surround Playback Volume'
        value.0 100
        value.1 100
    }
    control.11 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 100'
        comment.dbmin -4000
        comment.dbmax 0
        iface MIXER
        name 'Surround Capture Volume'
        value.0 0
        value.1 0
    }
    control.12 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Surround Capture Switch'
        value.0 false
        value.1 false
    }
    control.13 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 100'
        comment.dbmin -4000
        comment.dbmax 0
        iface MIXER
        name 'Center Playback Volume'
        value 100
    }
    control.14 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 100'
        comment.dbmin -4000
        comment.dbmax 0
        iface MIXER
        name 'LFE Playback Volume'
        value 100
    }
    control.16 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 100'
        comment.dbmin -4000
        comment.dbmax 0
        iface MIXER
        name 'Front Capture Volume'
        value.0 80
        value.1 80
    }
    control.17 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Front Capture Switch'
        value false
    }
    control.18 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 100'
        comment.dbmin -4000
        comment.dbmax 0
        iface MIXER
        name 'AC97 Playback Volume'
        value.0 80
        value.1 80
    }
    control.19 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 100'
        comment.dbmin -4000
        comment.dbmax 0
        iface MIXER
        name 'AC97 Capture Volume'
        value.0 80
        value.1 80
    }
    control.20 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 100'
        comment.dbmin -4000
        comment.dbmax 0
        iface MIXER
        name 'IEC958 TTL Playback Volume'
        value.0 0
        value.1 0
    }
    control.21 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 100'
        comment.dbmin -4000
        comment.dbmax 0
        iface MIXER
        name 'IEC958 TTL Capture Volume'
        value.0 0
        value.1 0
    }
    control.22 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'IEC958 TTL Capture Switch'
        value.0 false
        value.1 false
    }
    control.23 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 100'
        comment.dbmin -4000
        comment.dbmax 0
        iface MIXER
        name 'IEC958 LiveDrive Playback Volume'
        value.0 0
        value.1 0
    }
    control.24 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 100'
        comment.dbmin -4000
        comment.dbmax 0
        iface MIXER
        name 'IEC958 LiveDrive Capture Volume'
        value.0 0
        value.1 0
    }
    control.25 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'IEC958 LiveDrive Capture Switch'
        value.0 false
        value.1 false
    }
    control.26 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 100'
        comment.dbmin -4000
        comment.dbmax 0
        iface MIXER
        name 'Line LiveDrive Playback Volume'
        value.0 0
        value.1 0
    }
    control.27 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 100'
        comment.dbmin -4000
        comment.dbmax 0
        iface MIXER
        name 'Line LiveDrive Capture Volume'
        value.0 0
        value.1 0
    }
    control.28 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Line LiveDrive Capture Switch'
        value.0 false
        value.1 false
    }
    control.29 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 100'
        comment.dbmin -4000
        comment.dbmax 0
        iface MIXER
        name 'IEC958 Coaxial Playback Volume'
        value.0 0
        value.1 0
    }
    control.30 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 100'
        comment.dbmin -4000
        comment.dbmax 0
        iface MIXER
        name 'IEC958 Coaxial Capture Volume'
        value.0 0
        value.1 0
    }
    control.31 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'IEC958 Coaxial Capture Switch'
        value.0 false
        value.1 false
    }
    control.32 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 100'
        comment.dbmin -4000
        comment.dbmax 0
        iface MIXER
        name 'Line2 LiveDrive Playback Volume'
        index 1
        value.0 0
        value.1 0
    }
    control.33 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 100'
        comment.dbmin -4000
        comment.dbmax 0
        iface MIXER
        name 'Line2 LiveDrive Capture Volume'
        index 1
        value.0 0
        value.1 0
    }
    control.34 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Line2 LiveDrive Capture Switch'
        index 1
        value.0 false
        value.1 false
    }
    control.35 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 40'
        iface MIXER
        name 'Tone Control - Bass'
        value.0 20
        value.1 20
    }
    control.36 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 40'
        iface MIXER
        name 'Tone Control - Treble'
        value.0 20
        value.1 20
    }
    control.37 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Tone Control - Switch'
        value.0 false
        value.1 false
    }
    control.38 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'IEC958 Optical Raw Playback Switch'
        value.0 false
        value.1 false
    }
    control.39 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 100'
        comment.dbmin -4000
        comment.dbmax 0
        iface MIXER
        name 'Headphone Playback Volume'
        index 1
        value.0 80
        value.1 80
    }
    control.40 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Headphone Center Playback Switch'
        index 1
        value false
    }
    control.41 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Headphone LFE Playback Switch'
        index 1
        value false
    }
    control.42 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 32
        iface PCM
        device 2
        name 'Captured FX8010 Outputs'
        value.0 false
        value.1 false
        value.2 false
        value.3 false
        value.4 false
        value.5 false
        value.6 false
        value.7 false
        value.8 false
        value.9 false
        value.10 false
        value.11 false
        value.12 false
        value.13 false
        value.14 false
        value.15 false
        value.16 true
        value.17 true
        value.18 true
        value.19 true
        value.20 true
        value.21 true
        value.22 true
        value.23 true
        value.24 true
        value.25 true
        value.26 true
        value.27 true
        value.28 true
        value.29 true
        value.30 true
        value.31 true
    }
    control.43 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Master Playback Switch'
        value true
    }
    control.44 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -4650
        comment.dbmax 0
        iface MIXER
        name 'Master Playback Volume'
        value.0 25
        value.1 25
    }
    control.47 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'PC Speaker Playback Switch'
        value false
    }
    control.48 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 15'
        comment.dbmin -4500
        comment.dbmax 0
        iface MIXER
        name 'PC Speaker Playback Volume'
        value 0
    }
    control.49 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Phone Playback Switch'
        value false
    }
    control.50 {
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
    control.51 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Mic Playback Switch'
        value false
    }
    control.52 {
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
    control.53 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Mic Boost (+20dB)'
        value false
    }
    control.54 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Line Playback Switch'
        value false
    }
    control.55 {
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
    control.56 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'CD Playback Switch'
        value true
    }
    control.57 {
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
    control.58 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Video Playback Switch'
        value false
    }
    control.59 {
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
    control.60 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Aux Playback Switch'
        value false
    }
    control.61 {
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
    control.62 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'PCM Playback Switch'
        value true
    }
    control.63 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'PCM Playback Volume'
        value.0 25
        value.1 25
    }
    control.64 {
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
    control.65 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Capture Switch'
        value true
    }
    control.66 {
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
    control.67 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name '3D Control - Switch'
        value false
    }
    control.69 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 1
        comment.item.0 Mic1
        comment.item.1 Mic2
        iface MIXER
        name 'Mic Select'
        value Mic1
    }
    control.70 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 3'
        iface MIXER
        name '3D Control Sigmatel - Depth'
        value 0
    }
    control.71 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Sigmatel 4-Speaker Stereo Playback Switch'
        value false
    }
    control.72 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Surround Phase Inversion Playback Switch'
        value false
    }
    control.73 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'External Amplifier'
        value true
    }
    control.218 {
        comment.access read
        comment.type IEC958
        comment.count 1
        iface PCM
        device 2
        name 'IEC958 Playback Mask'
        value ffffffff00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
    }
    control.219 {
        comment.access read
        comment.type IEC958
        comment.count 1
        iface PCM
        device 2
        name 'IEC958 Playback Mask'
        index 1
        value ffffffff00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
    }
    control.220 {
        comment.access read
        comment.type IEC958
        comment.count 1
        iface PCM
        device 2
        name 'IEC958 Playback Mask'
        index 2
        value ffffffff00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
    }
    control.221 {
        comment.access 'read write'
        comment.type IEC958
        comment.count 1
        iface PCM
        device 2
        name 'IEC958 Playback Default'
        value '0492100200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.222 {
        comment.access 'read write'
        comment.type IEC958
        comment.count 1
        iface PCM
        device 2
        name 'IEC958 Playback Default'
        index 1
        value '0492100200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.223 {
        comment.access 'read write'
        comment.type IEC958
        comment.count 1
        iface PCM
        device 2
        name 'IEC958 Playback Default'
        index 2
        value '0492100200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.224 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'SB Live Analog/Digital Output Jack'
        value false
    }
}
state.CMI8738 {
    control.1 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        iface MIXER
        name 'Master Playback Volume'
        value.0 25
        value.1 25
    }
    control.2 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name '3D Control - Switch'
        value false
    }
    control.3 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        iface MIXER
        name 'PCM Playback Volume'
        value.0 25
        value.1 25
    }
    control.4 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'PCM Playback Switch'
        value true
    }
    control.5 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'PCM Capture Switch'
        value.0 false
        value.1 false
    }
    control.6 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        iface MIXER
        name 'Synth Playback Volume'
        value.0 25
        value.1 25
    }
    control.7 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Synth Playback Switch'
        value true
    }
    control.8 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 4
        iface MIXER
        name 'Synth Capture Route'
        value.0 false
        value.1 false
        value.2 false
        value.3 false
    }
    control.9 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        iface MIXER
        name 'CD Playback Volume'
        value.0 25
        value.1 25
    }
    control.10 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'CD Playback Switch'
        value.0 true
        value.1 true
    }
    control.11 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 4
        iface MIXER
        name 'CD Capture Route'
        value.0 false
        value.1 false
        value.2 false
        value.3 false
    }
    control.12 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        iface MIXER
        name 'Line Playback Volume'
        value.0 0
        value.1 0
    }
    control.13 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Line Playback Switch'
        value.0 false
        value.1 false
    }
    control.14 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 4
        iface MIXER
        name 'Line Capture Route'
        value.0 false
        value.1 false
        value.2 false
        value.3 false
    }
    control.15 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 31'
        iface MIXER
        name 'Mic Playback Volume'
        value 0
    }
    control.16 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Mic Playback Switch'
        value false
    }
    control.17 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Mic Capture Switch'
        value false
    }
    control.18 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 3'
        iface MIXER
        name 'PC Speaker Playback Volume'
        value 2
    }
    control.19 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 15'
        iface MIXER
        name 'Aux Playback Volume'
        value.0 0
        value.1 0
    }
    control.20 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Aux Playback Switch'
        value.0 false
        value.1 false
    }
    control.21 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Aux Capture Switch'
        value.0 false
        value.1 false
    }
    control.22 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Mic Boost Playback Switch'
        value false
    }
    control.23 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 7'
        iface MIXER
        name 'Mic Capture Volume'
        value 0
    }
    control.24 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 7'
        iface MIXER
        name 'Phone Playback Volume'
        value 0
    }
    control.25 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Phone Playback Switch'
        value false
    }
    control.26 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'PC Speaker Playback Switch'
        value true
    }
    control.27 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Mic Boost Capture Switch'
        value true
    }
    control.28 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Four Channel Mode'
        value true
    }
    control.29 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 1
        comment.item.0 Line-In
        comment.item.1 'Rear Output'
        comment.item.2 'Bass Output'
        iface MIXER
        name 'Line-In Mode'
        value Line-In
    }
    control.30 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'IEC958 Output Switch'
        value false
    }
    control.31 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'IEC958 In Valid'
        value false
    }
    control.32 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'IEC958 Copyright'
        value false
    }
    control.33 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'IEC958 5V'
        value true
    }
    control.34 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'IEC958 Loop'
        value false
    }
    control.35 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'IEC958 In Monitor'
        value false
    }
    control.36 {
        comment.access 'read write'
        comment.type IEC958
        comment.count 1
        iface PCM
        device 2
        name 'IEC958 Playback Default'
        value '0082000200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.37 {
        comment.access read
        comment.type IEC958
        comment.count 1
        iface PCM
        device 2
        name 'IEC958 Playback Con Mask'
        value ffffffff00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
    }
    control.39 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'IEC958 In Select'
        value false
    }
    control.40 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'IEC958 In Phase Inverse'
        value false
    }
    control.41 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 1
        comment.item.0 Mic-In
        comment.item.1 'Center/LFE Output'
        iface MIXER
        name 'Mic-In Mode'
        value 'Center/LFE Output'
    }
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
nls_utf8
isofs
binfmt_misc
snd_emu10k1_synth
snd_emux_synth
snd_seq_virmidi
snd_seq_midi_emul
arc4
fbcon
tileblit
font
bitblit
softcursor
vga16fb
vgastate
snd_cmipci
snd_emu10k1
snd_ac97_codec
ac97_bus
snd_pcm_oss
snd_mixer_oss
snd_pcm
snd_page_alloc
snd_util_mem
snd_opl3_lib
snd_hwdep
snd_mpu401_uart
snd_seq_dummy
snd_seq_oss
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
snd_seq
radeon
ath9k
snd_timer
snd_seq_device
ttm
mac80211
drm_kms_helper
ath
ppdev
snd
emu10k1_gp
drm
cfg80211
i2c_algo_bit
soundcore
gameport
led_class
intel_agp
parport_pc
joydev
serio_raw
agpgart
shpchp
lp
parport
hid_microsoft
usbhid
hid
e100
mii


!!ALSA/HDA dmesg
!!------------------



```

I'll check back later, Thanks

---

### Post by johnson094 on 2011-03-14
Well, I activated the onboard sound card and it works fine with Ubuntu 10.04.  It's a C-Media Electronics, Inc CM8738.
Problem is I get no sound in Windows 95.  Ubuntu works with C-Media...Windows works with Sound Blaster. What a mess.  Read a post where one guy upgraded his C-Media driver and got it to work on Windows ME.  The driver he downloaded was also compatible with Windows 95. I tried to follow his directions but when I tried to update the driver, for some reason it would not see the downloaded drivers.  I've been trying for 2 hours now.  Going to bed.

Later

---

### Post by johnson094 on 2011-03-14
:lolflag: Got audio in both operating systems.. On board sound card worked from git go with Ubuntu, not in Windows XP.  After hours of reading, trying drivers, etc, I finally disabled the Sound Blaster sound card in Windows XP Hardware Management.  This fixed the problem immediately.  What a dumb rookie mistake.  Thanks anyway for those that viewed my thread.

---

