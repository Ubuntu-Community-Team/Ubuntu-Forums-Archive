---
title: "Can mute but not unmute with amixer and alsactl"
date: 2010-04-05
forum: Multimedia Software
---

### Post by christer_f on 2010-04-05
Running 9.10 Karmic Koala.
I have full control over the sound using the Sound Preferences control panel, but need to be able to do programmatic control. Using either 'amixer' or 'alsactl -f' (with a saved configuration file) I can do all kinds of sound configuration changes, except unmute of the Speakers. For example:
 - amixer set Master 60% mute -> will mute and set the volume to 60%
However
 - amixer set Master 90% unmute -> will change the volume setting BUT NOT UNMUTE

Same thing if I set up the sound unmuted and save the configuration file with:
 - alsactl -f thefile store
then mute (and do all kind of other changes to both input and output sounds)
 - alsactl -f thefile restore
will restore all sound configurations except it will not unmute the speaker

Looks like a bug. Am I the only person having this problem? Any work arounds?

-- christer

---

### Post by digital_mariner on 2011-01-02
Running 10.10 Meerkat

Yes, this issue is 100% reproducible for me. What I don't understand is why it is not seen by anybody else? Does this need to be entered as a bug? 
It should not be complicated with levels. amixer does not unmute the master volume. The System->Preferences->Sound Master "mute" check box is also not unchecked. However amixer reports that the control is on. 
I don't understand why this is not treated as more serious. amixer is used in start up scripts to mute/unmute audio outputs. There are several threads discussing bugs with sound after hibernate/shut-down etc. The root cause of these issues is likely to be this fundamental issue with amixer. 

Method to repeat. 
Start State: Sound is enabled. 

>amixer -c 0 -- sset Master mute
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [0.00dB] [off]

Sound is muted (and System->Preferences->Sound Audio Output muted as expected)

>amixer -c 0 -- sset Master unmute
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [0.00dB] [on]
 
Sound is NOT unmuted  (and System->Preferences->Sound "Output Volume" "Mute" is still checked). 
However note that above states Master is "on" with 100%. Audio can be unmuted by clicking on the "Mute" check-box in System->Preferences->Sound. 

Also note that:
>amixer -c 0 -- sset Master toggle  
will mute Master audio output but will not unmute Master audio. 

System information:
>uname -a
Linux home-pc 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:36:48 UTC 2010 i686 GNU/Linux

>amixer -v
amixer version 1.0.23

Audio Cards:
>cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfe9f4000 irq 45
 2 [Live           ]: EMU10K1 - SB Live! Platinum [CT4760P]
                      SB Live! Platinum [CT4760P] (rev.7, serial:0x80401102) at 0xd880, irq 17
>amixer 
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pswitch penum
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [on]
  Front Right: Playback [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Front Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Front Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%]
  Front Right: 0 [0%]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Side',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 25 [81%] [3.00dB] [off]
  Front Right: Playback 25 [81%] [3.00dB] [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%]
  Front Right: 0 [0%]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined cswitch cswitch-joined penum
  Playback channels: Mono
  Capture channels: Mono
  Mono: Playback [on] Capture [on]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Beep',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 7 [23%] [-24.00dB] [off]
  Front Right: Playback 7 [23%] [-24.00dB] [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 0 [0%] [-16.50dB] [on]
  Front Right: Capture 0 [0%] [-16.50dB] [on]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 0 [0%] [-16.50dB] [on]
  Front Right: Capture 0 [0%] [-16.50dB] [on]
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Mic' 'Front Mic' 'Line'
  Item0: 'Mic'
Simple mixer control 'Input Source',1
  Capabilities: cenum
  Items: 'Mic' 'Front Mic' 'Line'
  Item0: 'Mic'

---

### Post by lidex on 2011-01-02
This worked perfectly for me:
```
lidex@dev-desktop:~$ amixer -c 0 -- set Master toggle 
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [0.00dB] [off]
lidex@dev-desktop:~$ amixer -c 0 -- set Master toggle 
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [0.00dB] [on]

```

---

