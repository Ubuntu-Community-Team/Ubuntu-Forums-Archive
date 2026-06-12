---
title: "No sound -  Realtek ALC850, ASUS P5N32, 10.10"
date: 2011-02-02
forum: Multimedia Software
---

### Post by Dahlgar on 2011-02-02
[FONT=Arial]Hi everyone. First time user of Linux and Ubuntu. I am trying to create a media center box for my home theater (Boxee, MythTV, etc). I like it so far but cannot get my onboard sound to play anything. My computer used to have XP installed and the sound worked great. I originally installed an older version of Ubuntu onto my computer and upgraded through each release until I got to 10.10. 

I've scoured the forum and tried a lot of different things to no avail. Does anyone know what I am missing or how to fix my problem? Thanks in advance for looking!

Specs:
*Ubuntu 10.10 (installed last week)
*Mobo: Asus P5N32 SLI Deluxe
*On board sound: nVidia CK804, Realtek ALC850
*home built 

What I've tried:
*checked to ensure levels weren't muted in alsamixer
*reinstalled alsa 
*ensured I was in audio group
*added extra line to alsa-base.conf file (options snd-hda-intel model=3stack-6ch-dig, options snd-hda-intel model=auto index=0, etc...)
*tested speakers on all outputs
*tested with known working headphones
*completed Sound Troubleshooting Guide

lspci - v 
```
00:0d.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
    Subsystem: ASUSTeK Computer Inc. K8N4-E or A8N-E Mainboard
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
    I/O ports at b400 [size=256]
    I/O ports at b000 [size=256]
    Memory at f0ffd000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0
```aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```ALSA sound report
[/FONT][FONT=Arial]http://www.alsa-project.org/db/?f=7461e211ee27c6fdfe9887af084d15c308c5c640
[/FONT]

---

### Post by lidex on 2011-02-02
These items:
```
Simple mixer control 'Channel Mode',0
  Capabilities: enum
  Items: '2ch' '4ch' '6ch' '8ch'
  Item0: '2ch'
Simple mixer control 'Duplicate Front',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'External Amplifier',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
```
Try playing around with them. Your chipset supports 8-channel sound, so try switching to that and toggling the other two elements.

---

### Post by Dahlgar on 2011-02-03
Thanks so much for the input! I tried all 16 combinations but still wasn't able to get any sound. I changed the parameters with this code:

```
$ amixer -c 0 sset 'Channel Mode',0 '4ch'
Simple mixer control 'Channel Mode',0
  Capabilities: enum
  Items: '2ch' '4ch' '6ch' '8ch'
  Item0: '4ch'

$ amixer -c 0 sset 'External Amplifier',0 off
Simple mixer control 'External Amplifier',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]

$ amixer -c 0 sset 'Duplicate Front',0 off
Simple mixer control 'Duplicate Front',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
```and tested the audio with this code:
```
$ aplay /usr/share/sounds/alsa/Front_Center.wav
Playing WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono
$ aplay -Dplughw:0,0 /usr/share/sounds/alsa/Front_Center.wav
Playing WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono
$ aplay -Dplughw:0,2 /usr/share/sounds/alsa/Front_Center.wav
Playing WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono
```I also played with the test speaker button for each of the profiles in the Sound Preferences -> Hardware tab. Any other thoughts or are you as stumped as me?

---

