---
title: "Intel HDA Recording Mixer Settings Problem"
date: 2008-05-11
forum: Multimedia Software
---

### Post by mocha on 2008-05-11
There still seems to be issues with Intel HDA under Hardy.  The capture settings are still messed up, for example "Front Mic" actually records from the Line In.  There is still no way to only capture from the Analog Mix, meaning the sounds generated within the computer say from a webpage or a streaming audio program.  I'm using an Asus P5B-E motherboard with the AD1988 Intel HDA codec.  Basically it still has the same problems as it did under Fiesty.  I'm having a hell of a time trying to find other people with the same problems, perhaps it is difficult to find the proper search terms for these problems.  Isn't there anyone out there that records from the line in or the analog mix?  I like to record audio from an external radio, I make a cron entry using arecord.  I also like to do screen captures with audio.  Anyway, I keep looking for solutions but it doesn't seem like there are any out there.  If anyone has any tips I'd appreciate it.  Thanks.

---

### Post by evolved on 2008-06-24
Hello Ubuntu users! I'm having the same problem, with the same motherboard, not just in Ubuntu, but in all Linux distributions i've tried. I can hear myself when i speak in the microphone, but when i try to record, i hear only some noise. Skype doesn't work with my mic. Windows XP works perfect (with the drivers provided by ASUS, of course).

I'm using Linux as my main operating system for 3-4 years now and i tell you this: Windows XP just runs better on ASUS P5B-E Plus motherboard.

I don't have the time to do manual configurations. I just want my mic to work. ASUS is lame, Intel HDA is lame, ALSA is lame, and of course Linux is the worst Desktop OS ever!

---

### Post by jualin on 2008-06-24
> **evolved said:**
> I don't have the time to do manual configurations. I just want my mic to work. ASUS sucks, Intel HDA sucks, ALSA sucks big time, and of course Linux is the worst Desktop OS ever!
Sorry you feel that way mate, maybe if you ASK a question we might help you. Greetings from Miami, FL.

---

### Post by evolved on 2008-06-24
> **jualin said:**
> Sorry you feel that way mate, maybe if you ASK a question we might help you. Greetings from Miami, FL.

Please help, don't treat me like a bad person. I said i'm using Linux as my daily OS.

Please help if you know how to fix Intel HDA/AD1988 problem with the microphone.

---

### Post by Wulfrunner on 2008-06-26
I'm having a similar problem: I can't get anything from the line-in, and the front mic and rear mic seem to be switched. I have an Intel DG33TL Motherboard with a SigmaTel STAC9271D codec, and am running Hardy Heron 64bit. 

The Gnome Volume Control gives me several devices: two ALSA HDA Intel, one OSS Sigmatel, and three PulseAudio Sigmatel. Are they redundant? 

Also, my HDA Intel (ALSA mixer) gives me three "input sources" with three choices: Front Mic, Mic, and Line. I have all these things on the board, but what is the correct sequence for the sound system to pick up on the correct source? For example, "Front Mic"/"Mic"/"Line" gives me capture at the back, while "Mic"/"Front Mic"/"Line" gives me nothing. Both front and back have active inputs, so surely something would have been picked up?

---

### Post by zabzoo on 2008-08-01
Hello - this thread is the closest I could find to the same problems that I am experiencing.  

I have a Intel DP35DP Motherboard 

This command 

```
cat /proc/asound/card0/codec#* | grep Codec
```

Tells me I have the following Codec for my hda-intel device
```
SigmaTel STAC9271D
```

I also have a Winfast 2000XP TV Card in my pc which is really bt878 compatible device.  At a stage i thought that there might be a conflict - i took the TV card out and the problem persisted!

I've done ./configure; make; make install on the last version of alsa (downloaded from their site) - and this didn't solve the problem.  

I've tried the instuctions here  -

[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

And here 

[http://ubuntuforums.org/showthread.php?t=601468](http://ubuntuforums.org/showthread.php?t=601468)

And also here - 
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

But none of them delivered any success.

I know that the sound output works fine; I am not sure if the bt878 audio device detected by ALSA really works, because in Windows the only way for me to get sound from my TV card to my Operating System is through the Line-in Device.

I have played around with alsa-mixer, trying to enable all devices making them loud etc. but this delivered no results either.

I am posting the result of my alsa-info.sh script that i ran here 

I am hoping that someone with expert knowledge on the issue might be able to assist me resolve this problem - **thank you in advance!**

**A quick summary**

Hda-INTEL Card using Sigmatel STAC9271D on Intel DP35DP motherboard
Running Linux Hardy-Heron 8.04 (2.6.24-19-generic)

**Sound output** works fine
**Sound input on mic** >> worked once (with loopback enabled), but never again
**Sound input on Line-in** >> never worked
**Front panel mic / speakers** >> not tested!

EDIT:  I also found this post - it would seem it is a similar problem to my problem

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/151634](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/151634)

ALSA-INFO.TXT
```

name=magnus&type=33&description=/tmp/alsa-info.txt&expiry=&s=Submit+Post&content=
!!################################
!!ALSA Information Script v 0.4.48
!!################################

!!Script ran on: Fri Aug  1 22:29:55 SAST 2008


!!Linux Distribution
!!------------------

Ubuntu 8.04.1 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 8.04.1"


!!Kernel Information
!!------------------

Kernel release:    2.6.24-19-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.16
Library version:    1.0.17
Utilities version:  1.0.17


!!Loaded ALSA modules
!!-------------------

snd_hda_intel
snd_bt87x


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0x93320000 irq 23
 1 [Bt878          ]: Bt87x - Brooktree Bt878
                      Brooktree Bt878 at 0x93000000, irq 23


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
07:01.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
07:01.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:293e (rev 02)
	Subsystem: 8086:3001
--
01:00.0 0300: 10de:0402 (rev a1) (prog-if 00 [VGA controller])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-usx2y: index=-2
snd-usb-caiaq: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388


!!Loaded sound module options
!!--------------------------

!!Module: snd_hda_intel
enable : Y,Y,Y,Y,Y,Y,Y,Y
enable_msi : 0
id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
index : -1,-1,-1,-1,-1,-1,-1,-1
model : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
position_fix : 0,0,0,0,0,0,0,0
power_save : 0
power_save_controller : Y
probe_mask : -1,-1,-1,-1,-1,-1,-1,-1
single_cmd : N

!!Module: snd_bt87x
digital_rate : 0,0,0,0,0,0,0,0
enable : Y,Y,Y,Y,Y,Y,Y,Y
id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
index : -2,-2,-2,-2,-2,-2,-2,-2
load_all : N


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: SigmaTel STAC9271D
Address: 2
Vendor Id: 0x83847627
Subsystem Id: 0x80863001
Revision Id: 0x100201
No Modem Function Group found
Default PCM:
    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: ofs=0x00, nsteps=0x0e, stepsize=0x05, mute=0
Default Amp-Out caps: ofs=0x7f, nsteps=0x7f, stepsize=0x02, mute=1
GPIO: io=3, o=0, i=0, unsolicited=1, wake=1
  IO[0]: enable=1, dir=1, wake=0, sticky=0, data=1
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0
  IO[2]: enable=0, dir=0, wake=0, sticky=0, data=0
Node 0x02 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out R/L
  Amp-Out caps: N/A
  Amp-Out vals:  [0x5f 0x5f]
  Converter: stream=5, channel=0
  Power: setting=D0, actual=D0
  Delay: 13 samples
Node 0x03 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out R/L
  Amp-Out caps: N/A
  Amp-Out vals:  [0xef 0xef]
  Converter: stream=5, channel=0
  Power: setting=D0, actual=D0
  Delay: 13 samples
Node 0x04 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out R/L
  Amp-Out caps: N/A
  Amp-Out vals:  [0xef 0xef]
  Converter: stream=5, channel=0
  Power: setting=D0, actual=D0
  Delay: 13 samples
Node 0x05 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out R/L
  Amp-Out caps: N/A
  Amp-Out vals:  [0xef 0xef]
  Converter: stream=5, channel=0
  Power: setting=D0, actual=D0
  Delay: 13 samples
Node 0x06 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out R/L
  Amp-Out caps: N/A
  Amp-Out vals:  [0xff 0xff]
  Converter: stream=0, channel=0
  Power: setting=D3, actual=D3
  Delay: 13 samples
Node 0x07 [Audio Input] wcaps 0x1d0541: Stereo
  Converter: stream=0, channel=0
  SDI-Select: 0
  Power: setting=D0, actual=D0
  Delay: 13 samples
  Connection: 1
     0x1b
  Processing caps: benign=0, ncoeff=0
Node 0x08 [Audio Input] wcaps 0x1d0541: Stereo
  Converter: stream=0, channel=0
  SDI-Select: 0
  Power: setting=D0, actual=D0
  Delay: 13 samples
  Connection: 1
     0x1c
  Processing caps: benign=0, ncoeff=0
Node 0x09 [Audio Input] wcaps 0x1d0541: Stereo
  Converter: stream=0, channel=0
  SDI-Select: 0
  Power: setting=D0, actual=D0
  Delay: 13 samples
  Connection: 1
     0x1d
  Processing caps: benign=0, ncoeff=0
Node 0x0a [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x08173f: IN OUT HP Detect Trigger ImpSense
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x0221401f: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Green
    DefAssociation = 0x1, Sequence = 0xf
  Pin-ctls: 0xc0: OUT HP VREF_HIZ
  Unsolicited: tag=30, enabled=1
  Connection: 3
     0x02* 0x03 0x06
Node 0x0b [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x08173f: IN OUT HP Detect Trigger ImpSense
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x02a19040: [Jack] Mic at Ext Front
    Conn = 1/8, Color = Pink
    DefAssociation = 0x4, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Connection: 3
     0x02* 0x03 0x06
Node 0x0c [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x081737: IN OUT Detect Trigger ImpSense
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x0181302e: [Jack] Line In at Ext Rear
    Conn = 1/8, Color = Blue
    DefAssociation = 0x2, Sequence = 0xe
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x03
Node 0x0d [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x08173f: IN OUT HP Detect Trigger ImpSense
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x01114010: [Jack] Speaker at Ext Rear
    Conn = 1/8, Color = Green
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x02
Node 0x0e [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x081737: IN OUT Detect Trigger ImpSense
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x01a19020: [Jack] Mic at Ext Rear
    Conn = 1/8, Color = Pink
    DefAssociation = 0x2, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x04
Node 0x0f [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x081737: IN OUT Detect Trigger ImpSense
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x01111012: [Jack] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0x1, Sequence = 0x2
  Pin-ctls: 0x40: OUT VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x05
Node 0x10 [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x0837: IN OUT Detect Trigger ImpSense
  Pin Default 0x01116011: [Jack] Speaker at Ext Rear
    Conn = 1/8, Color = Orange
    DefAssociation = 0x1, Sequence = 0x1
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x04
Node 0x11 [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x0837: IN OUT Detect Trigger ImpSense
  Pin Default 0x400000fb: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0xb
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x03
Node 0x12 [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x0820: IN
  Pin Default 0x400000fc: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0xc
  Pin-ctls: 0x00:
Node 0x13 [Vendor Defined Widget] wcaps 0xf00001: Stereo
Node 0x14 [Vendor Defined Widget] wcaps 0xf00001: Stereo
Node 0x15 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x04, stepsize=0x27, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 9
     0x0e* 0x12 0x0f 0x0b 0x0c 0x0d 0x0a 0x10 0x11
Node 0x16 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x04, stepsize=0x27, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 9
     0x0e* 0x12 0x0f 0x0b 0x0c 0x0d 0x0a 0x10 0x11
Node 0x17 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x04, stepsize=0x27, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 9
     0x0e* 0x12 0x0f 0x0b 0x0c 0x0d 0x0a 0x10 0x11
Node 0x18 [Audio Selector] wcaps 0x300103: Stereo Amp-In
  Amp-In caps: N/A
  Amp-In vals:  [0x06 0x06]
  Connection: 1
     0x15
Node 0x19 [Audio Selector] wcaps 0x300103: Stereo Amp-In
  Amp-In caps: N/A
  Amp-In vals:  [0x06 0x06]
  Connection: 1
     0x16
Node 0x1a [Audio Selector] wcaps 0x300103: Stereo Amp-In
  Amp-In caps: N/A
  Amp-In vals:  [0x06 0x06]
  Connection: 1
     0x17
Node 0x1b [Audio Selector] wcaps 0x30090d: Stereo Amp-Out R/L
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Connection: 1
     0x18
Node 0x1c [Audio Selector] wcaps 0x30090d: Stereo Amp-Out R/L
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Connection: 1
     0x19
Node 0x1d [Audio Selector] wcaps 0x30090d: Stereo Amp-Out R/L
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Connection: 1
     0x1a
Node 0x1e [Audio Output] wcaps 0x40211: Stereo Digital
  Converter: stream=5, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Delay: 4 samples
Node 0x1f [Vendor Defined Widget] wcaps 0xf30201: Stereo Digital
  Delay: 3 samples
Node 0x20 [Audio Input] wcaps 0x140311: Stereo Digital
  Converter: stream=0, channel=0
  SDI-Select: 0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Delay: 4 samples
  Connection: 1
     0x22
Node 0x21 [Pin Complex] wcaps 0x400301: Stereo Digital
  Pincap 0x0810: OUT
  Pin Default 0x01452150: [Jack] SPDIF Out at Ext Rear
    Conn = Optical, Color = Grey
    DefAssociation = 0x5, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Connection: 5
     0x1e* 0x1f 0x1b 0x1c 0x1d
Node 0x22 [Pin Complex] wcaps 0x430681: Stereo Digital
  Pincap 0x0810024: IN EAPD Detect
  EAPD 0x0:
  Pin Default 0x400000fd: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0xd
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Delay: 3 samples
Node 0x23 [Beep Generator Widget] wcaps 0x70000c: Mono Amp-Out
  Amp-Out caps: ofs=0x03, nsteps=0x03, stepsize=0x17, mute=0
  Amp-Out vals:  [0x00]
Node 0x24 [Volume Knob Widget] wcaps 0x600000: Mono
  Volume-Knob: delta=1, steps=127, direct=1, val=127
  Connection: 5
     0x02* 0x03 0x04 0x05 0x06
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116,  0 2008-08-01 21:48 /dev/snd/controlC0
crw-rw----+ 1 root audio 116, 32 2008-08-01 21:48 /dev/snd/controlC1
crw-rw----+ 1 root audio 116,  6 2008-08-01 21:48 /dev/snd/hwC0D2
crw-rw----+ 1 root audio 116, 24 2008-08-01 21:48 /dev/snd/pcmC0D0c
crw-rw----+ 1 root audio 116, 16 2008-08-01 22:25 /dev/snd/pcmC0D0p
crw-rw----+ 1 root audio 116, 17 2008-08-01 21:48 /dev/snd/pcmC0D1p
crw-rw----+ 1 root audio 116, 56 2008-08-01 21:48 /dev/snd/pcmC1D0c
crw-rw----+ 1 root audio 116, 57 2008-08-01 21:48 /dev/snd/pcmC1D1c
crw-rw----+ 1 root audio 116,  1 2008-08-01 21:48 /dev/snd/seq
crw-rw----+ 1 root audio 116, 33 2008-08-01 21:48 /dev/snd/timer


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 3/3
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
card 1: Bt878 [Brooktree Bt878], device 0: Bt87x Digital [Bt87x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Bt878 [Brooktree Bt878], device 1: Bt87x Analog [Bt87x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [Intel]

Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 127
  Mono: Playback 111 [87%] [-12.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 127
  Mono:
  Front Left: Playback 111 [87%] [-12.00dB] [on]
  Front Right: Playback 111 [87%] [-12.00dB] [on]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 127
  Mono:
  Front Left: Playback 127 [100%] [0.00dB] [off]
  Front Right: Playback 127 [100%] [0.00dB] [off]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 127
  Mono: Playback 127 [100%] [0.00dB] [off]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 127
  Mono: Playback 127 [100%] [0.00dB] [off]
Simple mixer control 'Side',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 127
  Mono:
  Front Left: Playback 127 [100%] [0.00dB] [off]
  Front Right: Playback 127 [100%] [0.00dB] [off]
Simple mixer control 'Line In as Output',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 14
  Front Left: Capture 6 [43%] [9.00dB] [off]
  Front Right: Capture 6 [43%] [9.00dB] [off]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 14
  Front Left: Capture 6 [43%] [9.00dB] [off]
  Front Right: Capture 6 [43%] [9.00dB] [off]
Simple mixer control 'Capture',2
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 14
  Front Left: Capture 6 [43%] [9.00dB] [off]
  Front Right: Capture 6 [43%] [9.00dB] [off]
Simple mixer control 'Analog Loopback',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Digital',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 120
  Front Left: Capture 0 [0%] [-30.00dB]
  Front Right: Capture 0 [0%] [-30.00dB]
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Mic' 'Front Mic' 'Line'
  Item0: 'Mic'
Simple mixer control 'Input Source',1
  Capabilities: cenum
  Items: 'Mic' 'Front Mic' 'Line'
  Item0: 'Mic'
Simple mixer control 'Input Source',2
  Capabilities: cenum
  Items: 'Mic' 'Front Mic' 'Line'
  Item0: 'Mic'
Simple mixer control 'Mux',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 4
  Front Left: Capture 0 [0%] [0.00dB]
  Front Right: Capture 0 [0%] [0.00dB]
Simple mixer control 'Mux',1
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 4
  Front Left: Capture 0 [0%] [0.00dB]
  Front Right: Capture 0 [0%] [0.00dB]
Simple mixer control 'Mux',2
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 4
  Front Left: Capture 0 [0%] [0.00dB]
  Front Right: Capture 0 [0%] [0.00dB]
Simple mixer control 'Swap Center/LFE',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]

!!-------Mixer controls for card 1 [Bt878]

Simple mixer control 'FM',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Mono
  Mono: Capture [off]
Simple mixer control 'Mic/Line',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Mono
  Mono: Capture [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume
  Capture channels: Mono
  Limits: Capture 0 - 15
  Mono: Capture 0 [0%]
Simple mixer control 'Capture Boost',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'TV Tuner',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Mono
  Mono: Capture [on]


!!Alsactl output
!!-------------

--startcollapse--
state.Intel {
	control.1 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Mic
		comment.item.1 'Front Mic'
		comment.item.2 Line
		iface MIXER
		name 'Input Source'
		value Mic
	}
	control.2 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Mic
		comment.item.1 'Front Mic'
		comment.item.2 Line
		iface MIXER
		name 'Input Source'
		index 1
		value Mic
	}
	control.3 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Mic
		comment.item.1 'Front Mic'
		comment.item.2 Line
		iface MIXER
		name 'Input Source'
		index 2
		value Mic
	}
	control.4 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Analog Loopback'
		value false
	}
	control.5 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 14'
		comment.dbmin 0
		comment.dbmax 2100
		iface MIXER
		name 'Capture Volume'
		value.0 6
		value.1 6
	}
	control.6 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Capture Switch'
		value.0 false
		value.1 false
	}
	control.7 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 4'
		comment.dbmin 0
		comment.dbmax 4000
		iface MIXER
		name 'Mux Capture Volume'
		value.0 0
		value.1 0
	}
	control.8 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 14'
		comment.dbmin 0
		comment.dbmax 2100
		iface MIXER
		name 'Capture Volume'
		index 1
		value.0 6
		value.1 6
	}
	control.9 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Capture Switch'
		index 1
		value.0 false
		value.1 false
	}
	control.10 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 4'
		comment.dbmin 0
		comment.dbmax 4000
		iface MIXER
		name 'Mux Capture Volume'
		index 1
		value.0 0
		value.1 0
	}
	control.11 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 14'
		comment.dbmin 0
		comment.dbmax 2100
		iface MIXER
		name 'Capture Volume'
		index 2
		value.0 6
		value.1 6
	}
	control.12 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Capture Switch'
		index 2
		value.0 false
		value.1 false
	}
	control.13 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 4'
		comment.dbmin 0
		comment.dbmax 4000
		iface MIXER
		name 'Mux Capture Volume'
		index 2
		value.0 0
		value.1 0
	}
	control.14 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 127'
		comment.dbmin -9525
		comment.dbmax 0
		iface MIXER
		name 'Front Playback Volume'
		value.0 111
		value.1 111
	}
	control.15 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Front Playback Switch'
		value.0 true
		value.1 true
	}
	control.16 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 127'
		comment.dbmin -9525
		comment.dbmax 0
		iface MIXER
		name 'Surround Playback Volume'
		value.0 127
		value.1 127
	}
	control.17 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Surround Playback Switch'
		value.0 false
		value.1 false
	}
	control.18 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		comment.dbmin -9525
		comment.dbmax 0
		iface MIXER
		name 'Center Playback Volume'
		value 127
	}
	control.19 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Center Playback Switch'
		value false
	}
	control.20 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		comment.dbmin -9525
		comment.dbmax 0
		iface MIXER
		name 'LFE Playback Volume'
		value 127
	}
	control.21 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'LFE Playback Switch'
		value false
	}
	control.22 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Swap Center/LFE Playback Switch'
		value true
	}
	control.23 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 127'
		comment.dbmin -9525
		comment.dbmax 0
		iface MIXER
		name 'Side Playback Volume'
		value.0 127
		value.1 127
	}
	control.24 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Side Playback Switch'
		value.0 false
		value.1 false
	}
	control.25 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Line In as Output Switch'
		value false
	}
	control.26 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Con Mask'
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.27 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.28 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Default'
		value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.29 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Switch'
		value false
	}
	control.30 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		comment.dbmin -9525
		comment.dbmax 0
		iface MIXER
		name 'Master Playback Volume'
		value 111
	}
	control.31 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Master Playback Switch'
		value true
	}
	control.32 {
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
	control.33 {
		comment.access 'read write user'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 120'
		comment.tlv '0000000100000008fffff44800000032'
		comment.dbmin -3000
		comment.dbmax 3000
		iface MIXER
		name 'Digital Capture Volume'
		value.0 0
		value.1 0
	}
}
state.Bt878 {
	control.1 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 15'
		iface MIXER
		name 'Capture Volume'
		value 0
	}
	control.2 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Capture Boost'
		value false
	}
	control.3 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 'TV Tuner'
		comment.item.1 FM
		comment.item.2 Mic/Line
		iface MIXER
		name 'Capture Source'
		value 'TV Tuner'
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
ipv6
af_packet
vmnet
vmblock
vmmon
binfmt_misc
rfcomm
l2cap
bluetooth
ppdev
acpi_cpufreq
cpufreq_conservative
cpufreq_powersave
cpufreq_userspace
cpufreq_stats
cpufreq_ondemand
freq_table
sbs
dock
video
output
sbshc
container
battery
iptable_filter
ip_tables
x_tables
aes_i586
dm_crypt
dm_mod
ac
sbp2
parport_pc
lp
parport
snd_hda_intel
snd_bt87x
snd_pcm_oss
snd_mixer_oss
snd_pcm
snd_hwdep
snd_page_alloc
bt878
snd_seq_dummy
snd_seq_oss
snd_seq_midi
snd_rawmidi
tuner
snd_seq_midi_event
tea5767
tda8290
tuner_simple
mt20xx
tea5761
snd_seq
bttv
ir_common
usblp
snd_timer
compat_ioctl32
i2c_algo_bit
serio_raw
videobuf_dma_sg
videobuf_core
btcx_risc
nvidia
tveeprom
snd_seq_device
evdev
snd
e1000e
intel_agp
videodev
v4l2_common
i2c_core
pcspkr
psmouse
heci
v4l1_compat
button
iTCO_wdt
iTCO_vendor_support
shpchp
pci_hotplug
soundcore
agpgart
ext3
jbd
mbcache
sg
sr_mod
cdrom
sd_mod
pata_acpi
usb_storage
libusual
pata_marvell
ata_piix
usbhid
hid
ohci1394
ieee1394
ata_generic
libata
scsi_mod
ehci_hcd
uhci_hcd
usbcore
thermal
processor
fan
fbcon
tileblit
font
bitblit
softcursor
fuse

```

---

### Post by a1an on 2008-10-03
Hello, 
Similar problem here with:
Ubuntu 8.04 - kernel 2.6.24-19-generic
Motherboard: ASUSTeK P5B
Card is Intel AD1988
with Codec: Analog Devices AD1988

Microphone playback works fine but I've found no way to make capture working.

With almost everithing enabled at maximum levels in the recording tab of alsamixer,  "vumeter -r &" lights up just the first green icon when I tap the microphone, but could by any interference in my opinion.

Did anyone find a solution to get the mic working yet?
Regards
Alan

PS: There are "Front Mic Boost" and "Mic boost" options but they show up in the Playback tab as slide bars instead of +20dB switches in the switches tab of the mixer panel

---

### Post by markbuntu on 2008-10-03
Due to the myriad ways that OEMs configured the HDA sound chips on the mobos, it is somewhat of a chore to figure them out. Many of them have reconfigured the inputs and ouputs. As it turns out, the information about this is already on your computer here:

/user/share/doc/alsa-base/driver/ALSA-Configuration.tar.gz

This file lists every configuration option available for every ALSA sound driver. If you want a little help figuring out your hda options you can try these threads. Look through the threads, not just the OP as many people have found specific non-obvious solutions for their machines and posted them:

If you are having problems with the HDA card/chip on your laptop or one of these:

HD Audio (ICH6, ICH6M, ESB2, ICH7, ICH8 ),
		ATI SB450, SB600, RS600,
		VIA VT8251/VT8237A,
		SIS966, ULI M5461
you should look here:

[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

Start in Post #2 here:

[http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)

If you are having problems with headphone/speaker control with your HDA sound device you can try this thread:

[http://ubuntuforums.org/showthread.php?t=806620](http://ubuntuforums.org/showthread.php?t=806620)

GOOD LUCK!!

You can also look into getting ALSA 1.0.17.

---

