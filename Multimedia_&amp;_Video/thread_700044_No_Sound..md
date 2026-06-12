---
title: "No Sound."
date: 2008-02-18
forum: Multimedia &amp; Video
---

### Post by nodnarb on 2008-02-18
I cannot get any sound to work on any apps or the sound test. My on board sound card is being detected and I have made sure that it is not muted. I have looked through other post with no help. Any ideas would be helpful so I could find somewhere to start. 

Here is a screen shot of my info. 


[IMG]http://i131.photobucket.com/albums/p304/bkskaggs/Screenshot.png[/IMG]

---

### Post by xc3RnbFO8P on 2008-02-18
Try to unmute **PCM** and **Line-in**

---

### Post by nodnarb on 2008-02-18
I did with no luck. I hooked up the speakers to my laptop which is running xp just to make sure the hardware worked. I also checked my motherboard, the sound outputs can be unplugged from it and they are attached correctly.

---

### Post by chavanak on 2008-02-18
somehow i can relate this problem to the other post where another person with a toshiba is facing!!! Did you do any recent update to your system??

---

### Post by xc3RnbFO8P on 2008-02-18
Show the output of > amixer in terminal.

---

### Post by BLKMGK on 2008-02-18
> **chavanak said:**
> somehow i can relate this problem to the other post where another person with a toshiba is facing!!! Did you do any recent update to your system??

I have a slightly different problem in that sound worked perfectly and then suddenly stopped on the digital output only. I did do an update, an Intel video driver that it turns out I'm not using. Has some update been trashing sound? I'm just now trying to fix this and your response caught my eye.

As for this issue - open alsamixer in console. Out of the box the GUI mixer might not show all outputs. Alsamixer from the commandline will show them and you can scroll side to side to see them all. The M key will mute or unmute items, I've foudn that just installed things are muted that I do not want to be so I have to go through and fix them. Hopefully for this issue it's as simple as that...

---

### Post by nodnarb on 2008-02-18
This is a new install of Ubuntu, I applied all the updates after installation. 


> Show the output of
Quote:
amixer
in terminal.


Sorry, new to this. How do I show the output of amixer?

I did make sure all volume controls were not muted.

---

### Post by xc3RnbFO8P on 2008-02-18
Application > Accessories > Terminal   write **amixer** then return
Copy / paste

> rig@rig-desktop:~$ amixer
Simple mixer control 'Headphone',0
  Capabilities: pswitch
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [on]
  Front Right: Playback [on]
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
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]


---

### Post by nodnarb on 2008-02-19
Thanks for the help.


> brandon@Phaytel:~$ amixer
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
  Mono: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [12.00dB] [on]
  Front Right: Playback 31 [100%] [12.00dB] [on]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Surround Jack Mode',0
  Capabilities: enum
  Items: 'Shared' 'Independent'
  Item0: 'Shared'
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 31 [100%] [12.00dB] [on] Capture [on]
  Front Right: Playback 31 [100%] [12.00dB] [on] Capture [on]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 31 [100%] [12.00dB] [on] Capture [off]
  Front Right: Playback 31 [100%] [12.00dB] [on] Capture [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [12.00dB] [on]
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Mic Boost (+20dB)',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Mic Front Input',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Mic Select',0
  Capabilities: enum
  Items: 'Mic1' 'Mic2'
  Item0: 'Mic1'
Simple mixer control 'Video',0
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Phone',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [12.00dB] [on]
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined cswitch cswitch-joined
  Playback channels: Mono
  Capture channels: Mono
  Mono: Playback [on] Capture [off]
Simple mixer control 'IEC958 Playback AC97-SPSA',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 3
  Mono: 3 [100%]
Simple mixer control 'IEC958 Playback Source',0
  Capabilities: enum
  Items: 'PCM' 'Analog In' 'IEC958 In'
  Item0: 'PCM'
Simple mixer control 'PC Speaker',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 15
  Mono: Playback 15 [100%] [0.00dB] [on]
Simple mixer control 'Aux',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
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
Simple mixer control 'Channel Mode',0
  Capabilities: enum
  Items: '2ch' '4ch' '6ch'
  Item0: '2ch'
Simple mixer control 'Duplicate Front',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'External Amplifier',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
brandon@Phaytel:~$ 


---

### Post by Yellow Pasque on 2008-02-19
Try the OSS4 install if you can't get sound working (link in my sig).

---

### Post by xc3RnbFO8P on 2008-02-19
In teminal:

> amixer set ''Master',0 90%, 90% on

---

### Post by nodnarb on 2008-02-20
> **Temüjin said:**
> Try the OSS4 install if you can't get sound working (link in my sig).


I installed OSS4 but still no sound. 

Here is my info

ossdetect -v
> brandon@Phaytel:~$ sudo ossdetect -v
Detected Nvidia nForce4
Detected Generic USB audio device (BETA)
Detected OSS Transparent Virtual Mixing Architecture



ossinfo
> Version info: OSS 4.0 (b1013/200802012036) (0x00040003) 
Platform: Linux/x86_64 2.6.22-14-generic #1 SMP Tue Feb 12 02:46:46 UTC 2008 (Phaytel)

Number of audio devices:        2
Number of audio engines:        11
Number of mixer devices:        1


Device objects
 0: osscore0 OSS core services
 1: ich0 Nvidia nForce4 interrupts=19350 (47409)
 2: ossusb0 USB audio core services
 3: vmix0 OSS transparent virtual support


Mixer devices
 0: ICH AC97 Mixer (ALC850) (Mixer 0 of device object 1)

Audio devices
Nvidia nForce4                    /dev/oss/ich0/pcm0  (device index 0)
Nvidia nForce4 S/PDIF out         /dev/oss/ich0/spdout  (device index 1)
brandon@Phaytel:~$ 





I'm beginning to believe this may be a hardware issue. :(

---

