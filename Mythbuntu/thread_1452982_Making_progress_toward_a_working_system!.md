---
title: "Making progress toward a working system!"
date: 2010-04-12
forum: Mythbuntu
---

### Post by kdx7214 on 2010-04-12
Hey folks, I thought I would ask here for some final advice on getting my system working.  This has been a 2 week long ordeal so far and it's *almost* there.

For the record, the mythbuntu ISO does NOT work with IEC958 audio on some motherboards.   However, the Ubuntu 9.10 base installation works with the same board.  Not sure why this is, but there you go.  To get any audio I have to install Ubuntu 9.10 (then unmute, and so forth) and then install Mythbuntu from the web page (apturl and so on).

Note that I am using myth 0.21 as it is the last one with support for the Hauppauge PVR-350.

My problem is this.  I have an ASUS A8N-SLI Deluxe motherboard and am using the optical output.   I can get MythMusic to play music just fine, but playing videos results in no audio.

I found numerous howto's to get this working, yet not a single one has managed to get it going.

When I pick the sound output device in frontend config, I get the following options:

ALSA:default, ALSA:surround51, ALSA:digital, ALSA:analog, ALSA:digital-mixed, /dev/dsp, /dev/adsp, JUNK, NULL

I've tried all but JUNK/NULL and have yet to get any sound during playback.  As I said I've tried every article/howto/etc. I can find with no luck so I'd really love some relevant advice.

Thanks!
Mike

---

### Post by tgm4883 on 2010-04-12
> **kdx7214 said:**
> Note that I am using myth 0.21 as it is the last one with support for the Hauppauge PVR-350.

Why is that the last version that supports the PVR-350?

---

### Post by kdx7214 on 2010-04-12
> **tgm4883 said:**
> Why is that the last version that supports the PVR-350?

I'm not sure of the reasons, but according to the MythTV website 0.22 and beyond have discontinued the support for the PVR-350.  Since I'm using it I'm stuck.

Also, I have an update.  I CAN play an .avi file and get audio through the media library - just not an ISO file.   

Thanks!
Mike

---

### Post by tgm4883 on 2010-04-12
> **kdx7214 said:**
> I'm not sure of the reasons, but according to the MythTV website 0.22 and beyond have discontinued the support for the PVR-350.  Since I'm using it I'm stuck.

Also, I have an update.  I CAN play an .avi file and get audio through the media library - just not an ISO file.   

Thanks!
Mike

Ah i see. The video out capabilities are not supported anymore on it, you can still use it as a tuner.

---

### Post by ktmom on 2011-06-06
Old thread but I wanted to comment that I also have the ASUS A8N-SLI Deluxe motherboard.  I have been able to use the s/pdif output on every release since 8.4 (when I started) up to 10.4 (which is what I currently use).

The "trick I found is to ignore all of the threads discussing creating alsa config files of any type and just make sure the alsa settinsg in alsamixer are correct.  

Here is my amixer output (terminal version of alsamixer):
```
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 25 [81%] [-9.00dB] [on]
  Front Right: Playback 25 [81%] [-9.00dB] [on]
Simple mixer control 'Master Mono',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 25 [81%] [-9.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 25 [81%] [3.00dB] [on]
  Front Right: Playback 25 [81%] [3.00dB] [on]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 24 [77%] [-10.50dB] [on]
  Front Right: Playback 24 [77%] [-10.50dB] [on]
Simple mixer control [COLOR="Red"]**'Surround Jack Mode',0**[/COLOR]
  Capabilities: enum
  Items: 'Shared' 'Independent'
  [COLOR="Red"]Item0: 'Independent'[/COLOR]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 25 [81%] [-9.00dB] [on]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 22 [71%] [-13.50dB] [on]
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
Simple mixer control 'Mic Front Input',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Mic Select',0
  Capabilities: enum
  Items: 'Mic1' 'Mic2'
  Item0: 'Mic1'
Simple mixer control 'Video',0
  Capabilities: cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Phone',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-34.50dB] [on]
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control [COLOR="Red"]**'IEC958',0**[/COLOR] (S/PDIF - unmuted) 
  Capabilities: pswitch pswitch-joined cswitch cswitch-joined penum
  Playback channels: Mono
  Capture channels: Mono
  Mono: [COLOR="Red"]Playback [on] Capture [on][/COLOR]
Simple mixer control[COLOR="Red"]** 'IEC958 Playback AC97-SPSA',0**[/COLOR] (S/PDIF P - set to 0 - never works if this has a value other than 0)
  Capabilities: volume volume-joined penum
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 3
  [COLOR="Red"]Mono: 0 [0%][/COLOR]
Simple mixer control [COLOR="Red"]**'IEC958 Playback Source',0**[/COLOR] S/PDIF P)
  Capabilities: enum
  Items: 'PCM' 'Analog In' 'IEC958 In'
  [COLOR="Red"]Item0: 'PCM'[/COLOR]
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
Simple mixer control 'Mono Output Select',0
  Capabilities: enum
  Items: 'Mix' 'Mic'
  Item0: 'Mix'
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch cswitch-joined penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 4 [27%] [6.00dB] [on]
  Front Right: Capture 4 [27%] [6.00dB] [on]
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
Simple mixer control [COLOR="Red"]**'Channel Mode',0**[/COLOR] (Channel - never works if set to anything but 2ch)
  Capabilities: enum
  Items: '2ch' '4ch' '6ch' '8ch'
  [COLOR="Red"]Item0: '2ch'[/COLOR]
Simple mixer control 'Duplicate Front',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'External Amplifier',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]

```

The items in red are the settings I have to make sure are correct.  Then it's as simple as selecting ALSA:default in the audio setup under the General settings in the frontend setup.

The trick I have learned is to use VLC player to play a video while adjusting alsamixer.  When you get it right, the sound starts working for the video.  I do not have any alsa config files anywhere. 

It's the setting s/pdif p to 0 that always gets me.  I'ts counter-intuitive so these notes will help me remember next time ;-)

---

