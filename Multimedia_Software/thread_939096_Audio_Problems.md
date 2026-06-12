---
title: "Audio Problems"
date: 2008-10-05
forum: Multimedia Software
---

### Post by DarkC on 2008-10-05
Today I bought a new sound card, it is Sound Blaster X-fi XtremeGamer. I followed the guide here to change from ALSA to OSS: [https://help.ubuntu.com/community/OpenSound#Building%20OSS](https://help.ubuntu.com/community/OpenSound#Building%20OSS)

I am still getting no sound. The only time I hear something is when I run the command "osstest" in the terminal. Even then I only hear sound out of two of my five speakers. I only hear sound out of the left, and right ones that are infront of me. I don't hear any sound out of my center, or left and right speakers, that are behind me.(the center one is infront of me) I am using Ubuntu 8.04.

I tried watching a music video using FireFox3 and it didn't have any sound, just like everything else I try that is supposed to have sound.

Here is what I get when I run the 'uname -r' command:
```
2.6.24-19-generic
```

Here is what I get when I run the 'ossmix' command:
```
Selected mixer 0/ICH AC97 Mixer (AD1981B)
Known controls are:
vol [<leftvol>:<rightvol>] (currently 75:75)
vol.rec ON|OFF (currently OFF)
pcm [<leftvol>:<rightvol>] (currently 75:75)
speaker <monovol> (currently 0)
line [<leftvol>:<rightvol>] (currently 32:32)
line.rec ON|OFF (currently ON)
mic <monovol> (currently 0)
mic.rec ON|OFF (currently OFF)
cd [<leftvol>:<rightvol>] (currently 75:75)
cd.rec ON|OFF (currently OFF)
igain [<leftvol>:<rightvol>] (currently 75:75)
aux1 [<leftvol>:<rightvol>] (currently 32:32)
aux1.rec ON|OFF (currently OFF)
phone [<leftvol>:<rightvol>] (currently 0:0)
phone.rec ON|OFF (currently OFF)
mono <monovol> (currently 75)
mono.rec ON|OFF (currently OFF)
video [<leftvol>:<rightvol>] (currently 0:0)
video.rec ON|OFF (currently OFF)
spdout.enable ON|OFF (currently OFF)
spdout.adc/dac ON|OFF (currently OFF)
spdout.pro <Consumer> (currently Consumer)
spdout.audio <AUDIO> (currently AUDIO)
spdout.copy ON|OFF (currently OFF)
spdout.pre-emph ON|OFF (currently OFF)
spdout.rate <48000> (currently 48000)
spdout.vbit ON|OFF (currently OFF)
vmix0-enable ON|OFF (currently ON)
vmix0-rate <decimal> (currently 48000) (Read-only)
vmix0-channels <Stereo> (currently Stereo)
vmix0-src <Fast> (currently Fast)
vmix0-outvol <monovol> (currently 25.0 dB)
vmix0-invol <monovol> (currently 25.0 dB)
vmix0.pcm1 [<leftvol>:<rightvol>] (currently 25.0:25.0 dB)
vmix0.pcm2 [<leftvol>:<rightvol>] (currently 25.0:25.0 dB)
vmix0.pcm3 [<leftvol>:<rightvol>] (currently 25.0:25.0 dB)
vmix0.pcm4 [<leftvol>:<rightvol>] (currently 25.0:25.0 dB)

```

here is what I get when I run the 'ossinfo -v3' command:
```
Version info: OSS 4.1 (b rc2/200810051859) (0x00040090) 
Hg revision: changeset: 470:350cb38bd0d1, tag: tip, date: Fri Oct 03 11:29:14 2008 +0300, summary: Addeed CS5536 support to oss_geode
Platform: Linux/i686 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 (bobo-desktop)

Number of audio devices:	3
Number of audio engines:	12
Number of mixer devices:	2


Device objects
 0: osscore0 OSS core services
 1: oss_ich0 Intel ICH6 (266E) interrupts=276430 (283995)
 2: oss_sbxfi0 Sound Blaster X-Fi (SB073x) interrupts=287376 (287376)
    PCI device 1102:0005, subdevice 1102:0031
 3: oss_usb0 USB audio core services


Mixer devices
 0: ICH AC97 Mixer (AD1981B) (Mixer 0 of device object 1)
    Device file /dev/oss/oss_ich0/mix0, Legacy device /dev/mixer0
    Priority: 10
    Caps: 
    Device handle: PCI01791028-0000:00:1e.2-mx01
    Device priority: 10

 1: Sound Blaster X-Fi (SB073x) (Mixer 0 of device object 2)
    Device file /dev/oss/oss_sbxfi0/mix0, Legacy device /dev/mixer1
    Priority: 1
    Caps: 
    Device handle: PCI00311102-0000:04:00.0-mx01
    Device priority: 1


Audio devices
Intel ICH6 (266E)                 /dev/oss/oss_ich0/pcm0  (device index 0)
    Legacy device /dev/dsp0
    Caps: DUPLEX TRIGGER MMAP 
    Modes: IN/OUT 
      Engine      1: 0/Intel ICH6 (266E)
                     Busy (IN/OUT) label 'VMIX' 
      Engine      2: 1/Intel ICH6 (266E) (vmix)
                     Busy (OUT) by PID 5480 / esd label 'esd' 
      Engine      3: 2/Intel ICH6 (266E) (vmix)
                     Available for use 
      Engine      4: 3/Intel ICH6 (266E) (vmix)
                     Available for use 
      Engine      5: 4/Intel ICH6 (266E) (vmix)
                     Available for use 
      Engine      6: 5/Intel ICH6 (266E)
                     Available for use 
    Input formats (0x00000410):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_AC3		- AC3 (Dolby Digital) encoded audio
    Output formats (0x00000410):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_AC3		- AC3 (Dolby Digital) encoded audio
    Device handle: PCI01791028-0000:00:1e.2-au01
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 6
    Native sample rates (min - max): 5000 - 48000
    HW Type: Not indicated.
    Minimum latency: Not indicated

Sound Blaster X-Fi (SB073x) output  /dev/oss/oss_sbxfi0/pcm0  (device index 1)
    Legacy device /dev/dsp1
    Caps: DUPLEX TRIGGER MMAP 
    Modes: IN/OUT 
      Out engine  1: 6/Sound Blaster X-Fi (SB073x) output
                     Available for use 
      Engine      2: 8/Sound Blaster X-Fi (SB073x) output (vmix)
                     Available for use 
      Engine      3: 9/Sound Blaster X-Fi (SB073x) output (vmix)
                     Available for use 
      Engine      4: 10/Sound Blaster X-Fi (SB073x) output (vmix)
                     Available for use 
      Engine      5: 11/Sound Blaster X-Fi (SB073x) output (vmix)
                     Available for use 
    Input formats (0x00000010):
      AFMT_S16_LE	- 16 bit signed little endian
    Output formats (0x00000010):
      AFMT_S16_LE	- 16 bit signed little endian
    Device handle: PCI00311102-0000:04:00.0-au01
    Related mixer dev: 1
    Sample rate source: 6
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 2
    Native sample rates (min - max): 48000 - 92600
    HW Type: Not indicated.
    Minimum latency: Not indicated

Sound Blaster X-Fi (SB073x) input  /dev/oss/oss_sbxfi0/pcmin0  (device index 2)
    Legacy device /dev/dsp2
    Caps: DUPLEX TRIGGER MMAP 
    Modes: IN/OUT 
      In engine   1: 7/Sound Blaster X-Fi (SB073x) input
                     Available for use 
      Engine      2: 8/Sound Blaster X-Fi (SB073x) output (vmix)
                     Available for use 
      Engine      3: 9/Sound Blaster X-Fi (SB073x) output (vmix)
                     Available for use 
      Engine      4: 10/Sound Blaster X-Fi (SB073x) output (vmix)
                     Available for use 
      Engine      5: 11/Sound Blaster X-Fi (SB073x) output (vmix)
                     Available for use 
    Input formats (0x00000010):
      AFMT_S16_LE	- 16 bit signed little endian
    Output formats (0x00000010):
      AFMT_S16_LE	- 16 bit signed little endian
    Device handle: PCI00311102-0000:04:00.0-au02
    Related mixer dev: 1
    Sample rate source: 6
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 2
    Native sample rates (min - max): 48000 - 96000
    HW Type: Not indicated.
    Minimum latency: Not indicated

```

If there is anything else you need to know to help me out with this please tell me. I would like to at least get my center and two front speakers to work right.

Thank you in advance!

---

### Post by erikthedrink on 2009-09-08
I've got logitech usb speakers.  In Xubuntu, go to Applications, then Accessories, then Terminal.  In Terminal, type

[FONT=Georgia][SIZE=4]asoundconf set-default-card 1[/SIZE][/FONT]

Then close and re-open your browser (Mozilla Firefox) or restart your system.
:P
Note, if you unplug your usb speakers, your laptop speakers will take over.  In order to re-establish contact with the usb speakers, you will need to (plug them back in) restart the system.

---

