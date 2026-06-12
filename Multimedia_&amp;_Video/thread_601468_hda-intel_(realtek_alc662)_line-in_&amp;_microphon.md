---
title: "hda-intel (realtek alc662) line-in &amp; microphone problems"
date: 2007-11-03
forum: Multimedia &amp; Video
---

### Post by s4ncho on 2007-11-03
line-in isn't working on my new motherboard.i've got no sound when using tvtime.

i can only hear some sounds from tv when playing audacity 
(which should have recorded microphone sounds )

i've got realtek **alc662** sound card (build-in asus p5ld2-x). 
my tv card line-out is connected with sound card line-in.

my alsa driver :
```
~$ cat /etc/modprobe.d/alsa-base | grep model
options snd-hda-intel model=3stack-6ch-dig
```

my card's 3 jacks, but 6channels with s/pdif & **jack-detect** (which doesn't work on my kubuntu 7.10)

my amixer settings:
```
~$ amixer
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
  Front Left: Playback 243 [95%] [-2.40dB]
  Front Right: Playback 243 [95%] [-2.40dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 54 [84%] [-10.00dB] [on]
  Front Right: Playback 53 [83%] [-11.00dB] [on]
Simple mixer control 'Front Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 28 [90%] [7.50dB] [on]
  Front Right: Playback 28 [90%] [7.50dB] [on]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 29 [94%] [9.00dB] [on]
  Front Right: Playback 29 [94%] [9.00dB] [on]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 25 [81%] [3.00dB] [on]
  Front Right: Playback 25 [81%] [3.00dB] [on]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 27 [87%] [6.00dB] [on]
  Front Right: Playback 27 [87%] [6.00dB] [on]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined cswitch cswitch-joined
  Playback channels: Mono
  Capture channels: Mono
  Mono: Playback [on] Capture [off]
Simple mixer control 'PC Speaker',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 29 [94%] [9.00dB] [on]
  Front Right: Playback 29 [94%] [9.00dB] [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 31 [100%] [33.00dB] [on]
  Front Right: Capture 31 [100%] [33.00dB] [on]
Simple mixer control 'Channel Mode',0
  Capabilities: enum
  Items: '2ch' '6ch'
  Item0: '2ch'
Simple mixer control 'Digital',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 120
  Front Left: Capture 120 [100%] [30.00dB]
  Front Right: Capture 120 [100%] [30.00dB]
Simple mixer control 'Input Source',0
  Capabilities: enum
  Items: 'Mic' 'Front Mic' 'Line' 'CD'
  Item0: 'Line'

```

any ideas?nearly gived up:/been lookin for solution over few days
Martin

---

### Post by dadde on 2007-12-10
Did you solve the problem?
I have the identical one!

---

### Post by s4ncho on 2007-12-16
no :( gived up
i'm using old yamaha 724 now
but still looking around from time to time & searching for solution

---

### Post by tgalati4 on 2007-12-16
Try the different stack switches and also try different jacks.  Sometimes Mic and headphones gets switched.  They work on my machine (ALC880) but the microphone and headphone jacks are switched.

Try every combination and then try different jack combinations.  At the chip level, the inputs and outputs can be moved around so the drivers may not be perfect, but with a little experimenting you may be able to get them to work.

---

### Post by s4ncho on 2008-01-25
i've already tried mamy before 
with no luck :(

---

### Post by cthulhu666 on 2008-02-01
Have a look here: [https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

---

### Post by s4ncho on 2008-03-12
mic & line-in works fine after alsa update

---

### Post by j4ni on 2008-04-06
Hi s4ncho,

I'm about to purchase Asus P5LD2-X/GBL. So I would like to no how linux compatible it is.
Sound card works perfectly after alsa update? How about lan?

-j4ni

---

### Post by s4ncho on 2008-04-14
j4ni, no problems with lan. alfer update soundcard works fine.
i've some problems with skype which is recording voice from my tvcard not mic
but probably got something wrong in skype settings cause mic works fine in system

---

### Post by runnerch on 2008-06-06
S4ncho, I have the same problem as you had. My sound card is also Realtek alc 662, but the motherboard is different. Can you tell me what version of ubuntu is in your computer (what kernel) and what version of alsa driver you chosed to install?

---

