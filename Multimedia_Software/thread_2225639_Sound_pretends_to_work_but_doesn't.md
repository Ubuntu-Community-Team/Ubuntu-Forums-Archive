---
title: "Sound pretends to work but doesn't"
date: 2014-05-22
forum: Multimedia Software
---

### Post by kyrawertho on 2014-05-22
Hello,

I have a new install of Lubuntu on an older computer. I just can't get the sound to work.
I tried reinstalling alsa and pulseaudio.
If I play music/video and look at the volume settings, the blue bar is moving, suggesting the sound is working fine, but there is no audible sound. I tried some of the avaiable settings in the configuration tab, but found nothing that works.

In other forums I found aplay may be helpful (it seems to recognize the right sound card):

**** Lijst van PLAYBACK hardware-apparaten ****
Home directory not accessible: Toegang geweigerd
kaart 0: Audigy2 [SB Audigy 2 [SB0240]], apparaat 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Sub-apparaten: 30/32
  Sub-apparaat #0: subdevice #0
  Sub-apparaat #1: subdevice #1
  Sub-apparaat #2: subdevice #2
  Sub-apparaat #3: subdevice #3
  Sub-apparaat #4: subdevice #4
  Sub-apparaat #5: subdevice #5
  Sub-apparaat #6: subdevice #6
  Sub-apparaat #7: subdevice #7
  Sub-apparaat #8: subdevice #8
  Sub-apparaat #9: subdevice #9
  Sub-apparaat #10: subdevice #10
  Sub-apparaat #11: subdevice #11
  Sub-apparaat #12: subdevice #12
  Sub-apparaat #13: subdevice #13
  Sub-apparaat #14: subdevice #14
  Sub-apparaat #15: subdevice #15
  Sub-apparaat #16: subdevice #16
  Sub-apparaat #17: subdevice #17
  Sub-apparaat #18: subdevice #18
  Sub-apparaat #19: subdevice #19
  Sub-apparaat #20: subdevice #20
  Sub-apparaat #21: subdevice #21
  Sub-apparaat #22: subdevice #22
  Sub-apparaat #23: subdevice #23
  Sub-apparaat #24: subdevice #24
  Sub-apparaat #25: subdevice #25
  Sub-apparaat #26: subdevice #26
  Sub-apparaat #27: subdevice #27
  Sub-apparaat #28: subdevice #28
  Sub-apparaat #29: subdevice #29
  Sub-apparaat #30: subdevice #30
  Sub-apparaat #31: subdevice #31
kaart 0: Audigy2 [SB Audigy 2 [SB0240]], apparaat 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Sub-apparaten: 8/8
  Sub-apparaat #0: subdevice #0
  Sub-apparaat #1: subdevice #1
  Sub-apparaat #2: subdevice #2
  Sub-apparaat #3: subdevice #3
  Sub-apparaat #4: subdevice #4
  Sub-apparaat #5: subdevice #5
  Sub-apparaat #6: subdevice #6
  Sub-apparaat #7: subdevice #7
kaart 0: Audigy2 [SB Audigy 2 [SB0240]], apparaat 3: emu10k1 [Multichannel Playback]
  Sub-apparaten: 1/1
  Sub-apparaat #0: subdevice #0
kaart 0: Audigy2 [SB Audigy 2 [SB0240]], apparaat 4: p16v [p16v]
  Sub-apparaten: 1/1
  Sub-apparaat #0: subdevice #0

Any ideas how I can proceed? I also run Win XP on this machine without audio problems.

Thanks

---

### Post by Yellow Pasque on 2014-05-22
More info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

Actually, the first thing you should try is running alsamixer and making sure IEC958/Digital output is not selected (toggle with spacebar):
```
alsamixer
```

---

### Post by kyrawertho on 2014-05-22
In alsamixer, you mean to switch with F6? SD Audigy is selected, it's the only device there.
I ran the script, not sure what I should look for but here's most of it:

```

upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.63
!!################################

!!Script ran on: Thu May 22 16:25:56 UTC 2014


!!Linux Distribution
!!------------------

Ubuntu 14.04 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 14.04 LTS" NAME="Ubuntu" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu 14.04 LTS" HOME_URL="http://www.ubuntu.com/" SUPPORT_URL="http://help.ubuntu.com/" BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"


!!DMI Information
!!---------------

Manufacturer:      MICRO-STAR INTERNATIONAL CO., LTD
Product Name:      MS-7104
Product Version:   3.0
Firmware Version:   V5.1 


!!Kernel Information
!!------------------

Kernel release:    3.13.0-24-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         i686
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     k3.13.0-24-generic
Library version:    1.0.27.2
Utilities version:  1.0.27.2


!!Loaded ALSA modules
!!-------------------

snd_emu10k1


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [Audigy2        ]: Audigy2 - SB Audigy 2 [SB0240]
                      SB Audigy 2 [SB0240] (rev.4, serial:0x10071102) at 0xfc00, irq 16


!!PCI Soundcards installed in the system
!!--------------------------------------

00:05.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!-------------------------------------------------------

00:05.0 0401: 1102:0004 (rev 04)
    Subsystem: 1102:1007


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

!!Module: snd_emu10k1
    delay_pcm_irq : 2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2
    enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
    enable_ir : N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N
    extin : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    extout : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    high_res_gpr_volume : N
    id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    max_buffer_size : 128,128,128,128,128,128,128,128,128,128,128,128,128,128,128,128,128,128,128,128,128,128,128,128,128,128,128,128,128,128,128,128
    max_synth_voices : 64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64
    seq_ports : 4,4,4,4,4,4,4,4,4,4,4,4,4,4,4,4,4,4,4,4,4,4,4,4,4,4,4,4,4,4,4,4
    subsystem : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0


!!AC97 Codec information
!!----------------------
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
0:02 = 0000
0:04 = 8000
0:06 = 801f
0:08 = 0000
0:0a = 801e
0:0c = 801f
0:0e = 801f
0:10 = 9f1f
0:12 = 9f1f
0:14 = 9f1f
0:16 = 9f1f
0:18 = 9f1f
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
0:6c = 00c4
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

crw-rw----+ 1 root audio 116, 13 May 22 17:14 /dev/snd/controlC0
crw-rw----+ 1 root audio 116,  2 May 22 17:14 /dev/snd/hwC0D0
crw-rw----+ 1 root audio 116, 14 May 22 17:14 /dev/snd/hwC0D2
crw-rw----+ 1 root audio 116,  4 May 22 17:14 /dev/snd/midiC0D0
crw-rw----+ 1 root audio 116,  3 May 22 17:14 /dev/snd/midiC0D1
crw-rw----+ 1 root audio 116, 15 May 22 17:14 /dev/snd/midiC0D2
crw-rw----+ 1 root audio 116, 16 May 22 17:14 /dev/snd/midiC0D3
crw-rw----+ 1 root audio 116, 12 May 22 17:48 /dev/snd/pcmC0D0c
crw-rw----+ 1 root audio 116, 11 May 22 17:48 /dev/snd/pcmC0D0p
crw-rw----+ 1 root audio 116, 10 May 22 17:14 /dev/snd/pcmC0D1c
crw-rw----+ 1 root audio 116,  9 May 22 17:14 /dev/snd/pcmC0D2c
crw-rw----+ 1 root audio 116,  8 May 22 17:14 /dev/snd/pcmC0D2p
crw-rw----+ 1 root audio 116,  7 May 22 17:14 /dev/snd/pcmC0D3p
crw-rw----+ 1 root audio 116,  6 May 22 17:14 /dev/snd/pcmC0D4c
crw-rw----+ 1 root audio 116,  5 May 22 17:14 /dev/snd/pcmC0D4p
crw-rw----+ 1 root audio 116,  1 May 22 17:14 /dev/snd/seq
crw-rw----+ 1 root audio 116, 33 May 22 17:14 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 May 22 17:14 .
drwxr-xr-x 3 root root 400 May 22 17:14 ..
lrwxrwxrwx 1 root root  12 May 22 17:14 pci-0000:00:05.0 -> ../controlC0


!!Aplay/Arecord output
!!--------------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: Audigy2 [SB Audigy 2 [SB0240]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
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
card 0: Audigy2 [SB Audigy 2 [SB0240]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Audigy2 [SB Audigy 2 [SB0240]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Audigy2 [SB Audigy 2 [SB0240]], device 4: p16v [p16v]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: Audigy2 [SB Audigy 2 [SB0240]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Audigy2 [SB Audigy 2 [SB0240]], device 1: emu10k1 mic [Mic Capture]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Audigy2 [SB Audigy 2 [SB0240]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Audigy2 [SB Audigy 2 [SB0240]], device 4: p16v [p16v]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [Audigy2]

Card hw:0 'Audigy2'/'SB Audigy 2 [SB0240] (rev.4, serial:0x10071102) at 0xfc00, irq 16'
  Mixer name    : 'SigmaTel STAC9721,23'
  Components    : 'AC97a:83847609'
  Controls      : 214
  Simple ctrls  : 49
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined cvolume cswitch cswitch-joined
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 31
  Mono: Playback 100 [100%] [0.00dB]
  Front Left: Capture 31 [100%] [0.00dB] [on]
  Front Right: Capture 31 [100%] [0.00dB] [on]
Simple mixer control 'Tone',0
  Capabilities: pswitch
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [off]
  Front Right: Playback [off]
Simple mixer control 'Bass',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 40
  Front Left: 20 [50%]
  Front Right: 20 [50%]
Simple mixer control 'Treble',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 40
  Front Left: 20 [50%]
  Front Right: 20 [50%]
Simple mixer control '3D Control Sigmatel - Depth',0
  Capabilities: pvolume pvolume-joined
  Playback channels: Mono
  Limits: Playback 0 - 3
  Mono: Playback 0 [0%]
Simple mixer control 'PCM',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 100
  Front Left: Capture 0 [0%] [-99999.99dB]
  Front Right: Capture 0 [0%] [-99999.99dB]
Simple mixer control 'PCM Center',0
  Capabilities: pvolume pvolume-joined
  Playback channels: Mono
  Limits: Playback 0 - 100
  Mono: Playback 100 [100%] [0.00dB]
Simple mixer control 'PCM Front',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100
  Mono:
  Front Left: Playback 100 [100%] [0.00dB]
  Front Right: Playback 100 [100%] [0.00dB]
Simple mixer control 'PCM LFE',0
  Capabilities: pvolume pvolume-joined
  Playback channels: Mono
  Limits: Playback 0 - 100
  Mono: Playback 100 [100%] [0.00dB]
Simple mixer control 'PCM Side',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100
  Mono:
  Front Left: Playback 100 [100%] [0.00dB]
  Front Right: Playback 100 [100%] [0.00dB]
Simple mixer control 'PCM Surround',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100
  Mono:
  Front Left: Playback 100 [100%] [0.00dB]
  Front Right: Playback 100 [100%] [0.00dB]
Simple mixer control 'Front',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100
  Mono:
  Front Left: Playback 100 [100%] [0.00dB]
  Front Right: Playback 100 [100%] [0.00dB]
Simple mixer control 'Surround',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100
  Mono:
  Front Left: Playback 100 [100%] [0.00dB]
  Front Right: Playback 100 [100%] [0.00dB]
Simple mixer control 'Surround Phase Inversion',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined
  Playback channels: Mono
  Limits: Playback 0 - 100
  Mono: Playback 100 [100%] [0.00dB]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined
  Playback channels: Mono
  Limits: Playback 0 - 100
  Mono: Playback 100 [100%] [0.00dB]
Simple mixer control 'Side',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100
  Mono:
  Front Left: Playback 100 [100%] [0.00dB]
  Front Right: Playback 100 [100%] [0.00dB]
Simple mixer control 'Synth',0
  Capabilities: pvolume cvolume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 50 [50%] [-20.00dB] Capture 0 [0%] [-99999.99dB]
  Front Right: Playback 50 [50%] [-20.00dB] Capture 0 [0%] [-99999.99dB]
Simple mixer control 'Wave',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100
  Mono:
  Front Left: Playback 100 [100%] [0.00dB]
  Front Right: Playback 100 [100%] [0.00dB]
Simple mixer control 'Line',0
  Capabilities: cvolume cswitch cswitch-joined
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 0 [0%] [-34.50dB] [off]
  Front Right: Capture 0 [0%] [-34.50dB] [off]
Simple mixer control 'CD',0
  Capabilities: cvolume cswitch cswitch-joined
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 0 [0%] [-34.50dB] [off]
  Front Right: Capture 0 [0%] [-34.50dB] [off]
Simple mixer control 'Mic',0
  Capabilities: cvolume cvolume-joined cswitch cswitch-joined
  Capture channels: Mono
  Limits: Capture 0 - 31
  Mono: Capture 0 [0%] [-34.50dB] [off]
Simple mixer control 'Mic Boost (+20dB)',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Mic Select',0
  Capabilities: enum
  Items: 'Mic1' 'Mic2'
  Item0: 'Mic1'
Simple mixer control 'Video',0
  Capabilities: cvolume cswitch cswitch-joined
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 0 [0%] [-34.50dB] [off]
  Front Right: Capture 0 [0%] [-34.50dB] [off]
Simple mixer control 'Phone',0
  Capabilities: cvolume cvolume-joined cswitch cswitch-joined
  Capture channels: Mono
  Limits: Capture 0 - 31
  Mono: Capture 0 [0%] [-34.50dB] [off]
Simple mixer control 'IEC958 Optical',0
  Capabilities: pvolume cvolume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 0 [0%] [-99999.99dB] Capture 0 [0%] [-99999.99dB]
  Front Right: Playback 0 [0%] [-99999.99dB] Capture 0 [0%] [-99999.99dB]
Simple mixer control 'IEC958 Optical Raw',0
  Capabilities: pswitch
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [off]
  Front Right: Playback [off]
Simple mixer control 'Beep',0
  Capabilities: cvolume cvolume-joined cswitch cswitch-joined
  Capture channels: Mono
  Limits: Capture 0 - 15
  Mono: Capture 0 [0%] [-45.00dB] [off]
Simple mixer control 'Aux',0
  Capabilities: cvolume cswitch cswitch-joined
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 0 [0%] [-34.50dB] [off]
  Front Right: Capture 0 [0%] [-34.50dB] [off]
Simple mixer control 'Aux2',0
  Capabilities: pvolume cvolume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 0 [0%] [-99999.99dB] Capture 0 [0%] [-99999.99dB]
  Front Right: Playback 0 [0%] [-99999.99dB] Capture 0 [0%] [-99999.99dB]
Simple mixer control 'Mono Output Select',0
  Capabilities: enum
  Items: 'Mix' 'Mic'
  Item0: 'Mix'
Simple mixer control 'AMic',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100
  Mono:
  Front Left: Playback 0 [0%] [-99999.99dB]
  Front Right: Playback 0 [0%] [-99999.99dB]
Simple mixer control 'Analog Capture Boost',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Analog Mix',0
  Capabilities: pvolume cvolume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 0 [0%] [-99999.99dB] Capture 0 [0%] [-99999.99dB]
  Front Right: Playback 0 [0%] [-99999.99dB] Capture 0 [0%] [-99999.99dB]
Simple mixer control 'Audigy Analog/Digital Output Jack',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Audigy CD',0
  Capabilities: pvolume cvolume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 0 [0%] [-99999.99dB] Capture 0 [0%] [-99999.99dB]
  Front Right: Playback 0 [0%] [-99999.99dB] Capture 0 [0%] [-99999.99dB]
Simple mixer control 'External Amplifier',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'HD Analog Center/LFE',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 207 [81%] [0.00dB]
  Front Right: Playback 207 [81%] [0.00dB]
Simple mixer control 'HD Analog Front',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 207 [81%] [0.00dB]
  Front Right: Playback 207 [81%] [0.00dB]
Simple mixer control 'HD Analog Rear',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 207 [81%] [0.00dB]
  Front Right: Playback 207 [81%] [0.00dB]
Simple mixer control 'HD Analog Side',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 207 [81%] [0.00dB]
  Front Right: Playback 207 [81%] [0.00dB]
Simple mixer control 'HD SPDIF Center/LFE',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 207 [81%] [0.00dB]
  Front Right: Playback 207 [81%] [0.00dB]
Simple mixer control 'HD SPDIF Front',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 207 [81%] [0.00dB]
  Front Right: Playback 207 [81%] [0.00dB]
Simple mixer control 'HD SPDIF Rear',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 207 [81%] [0.00dB]
  Front Right: Playback 207 [81%] [0.00dB]
Simple mixer control 'HD SPDIF Side',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 207 [81%] [0.00dB]
  Front Right: Playback 207 [81%] [0.00dB]
Simple mixer control 'HD channel Capture',0
  Capabilities: enum
  Items: '0' '1' '2' '3'
  Item0: '0'
Simple mixer control 'HD source Capture',0
  Capabilities: enum
  Items: 'SPDIF' 'I2S' 'SRC48' 'SRCMulti_SPDIF' 'SRCMulti_I2S' 'CDIF' 'FX' 'AC97'
  Item0: 'SPDIF'
Simple mixer control 'Sigmatel 4-Speaker Stereo',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]

```

---

### Post by Yellow Pasque on 2014-05-22
For future reference, please post stuff like logs using code tags instead of quote tags.

I want you to change this control to 'on' (toggle on/off using spacebar)
```
Simple mixer control 'Audigy Analog/Digital Output Jack',0
Capabilities: pswitch pswitch-joined
Playback channels: Mono
Mono: Playback [off]
```

The logic on the Audigy2 cards may be inverted, but only some models got patched apparently: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1097479](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1097479)

---

### Post by kyrawertho on 2014-05-22
Ah I found it. Thanks very much it works now! The switch was muted..

---

### Post by Yellow Pasque on 2014-05-22
You're welcome. Please mark thread solved.

---

