---
title: "Various issues spawing from having spdif audio"
date: 2006-11-07
forum: Multimedia &amp; Video
---

### Post by obleak on 2006-11-07
Hi All,

I'm having some trouble with my intel hda card - it's not that the card doesn't work it's that I can't use it the way I expect.
[SIZE="1"](FYI I am an audio engineer, I understand digital audio)[/SIZE]

first some specs
$ cat /proc/asound/cards
```
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xf8000000 irq 58
```

$ cat /proc/asound/devices
```
  2:        : timer
  3: [ 0- 2]: digital audio capture
  4: [ 0- 1]: digital audio playback
  5: [ 0- 1]: digital audio capture
  6: [ 0- 0]: digital audio playback
  7: [ 0- 0]: digital audio capture
  8: [ 0]   : control
```

$ cat /proc/asound/modules
```
0 snd_hda_intel
```

$ amixer
```
Simple mixer control 'Headphone',0
  Capabilities: pswitch
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [off]
  Front Right: Playback [off]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 217 [85%]
  Front Right: Playback 217 [85%]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 26 [84%] [on]
  Front Right: Playback 26 [84%] [on]
Simple mixer control 'Front Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [off]
  Front Right: Playback 0 [0%] [off]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [off]
  Front Right: Playback 0 [0%] [off]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [off]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [off]
Simple mixer control 'Side',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [off]
  Front Right: Playback 0 [0%] [off]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 29 [94%] [on]
  Front Right: Playback 29 [94%] [on]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 29 [94%] [on]
  Front Right: Playback 29 [94%] [on]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [off]
  Front Right: Playback 0 [0%] [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined cswitch cswitch-joined
  Playback channels: Mono
  Capture channels: Mono
  Mono: Playback [on] Capture [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 0 [0%] [off]
  Front Right: Capture 0 [0%] [off]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 0 [0%] [off]
  Front Right: Capture 0 [0%] [off]
Simple mixer control 'Input Source',0
  Capabilities: enum
  Items: 'Mic' 'Front Mic' 'Line' 'CD'
  Item0: 'Line'
Simple mixer control 'Input Source',1
  Capabilities: enum
  Items: 'Mic' 'Front Mic' 'Line' 'CD'
  Item0: 'CD'
```



The problems can be boiled down into 2 categories:

_#1 ALSA presentation_
[LIST]
[*]First off check out the IEC958 (aka spdif) entry in the amixer output above - note how it lists it as mono. This is not true, spdif is stereo.
[*]spdif clock / lock details - where are they? I have been through every file in /proc/asound and there is nothing listed. I should be able to see the following with the spdif in:[LIST=1]
[*]Lock indication (ie the spdif in has locked to a signal)
[*]Clock source (internal or external)
[*]Clock Frequency (44.1khz or 48khz)
[*]Bit depth (16 or 24 bits a sample)
[/LIST]
[*] analogue clock source - since the card has two devices there must be some sort of option to clock the analogue device off the digital clock - this is mandatory if I want to direct the spdif in to the analogue outs (say through jack). At the moment I get obvious clocking errors as my spdif  in is clocking off the source, and my analogue device is clocking internally. Because of this I am forced to treat the two devices as two different cards that can never be used at the same time.
[/LIST]
 


_#2 Gnome utilization _
This is where I really start pulling my hair out.
First off I should mention that the card works fine - in that I can use arecord to record from any capture device and aplay to send sound out to any device. I can even pipe one into the other (apart from the occasional glitch due to different clock sources). 
[LIST]
[*]System -> preferences -> multimedia systems selector. no option to select which device I want to use
[*]There is not a single gnome sound (alsa) application that can record from the spdif in (ie does not give me a choice). Every gnome alsa sound application that produces output gives me the choice somewhere of which device (analogue or digital). 
[*] The "Sound Recorder" application looks like it will - but as soon as I hit record it switches to one of the analogue capture sources....
[*] The "Recording Level Monitor" application doesn't let me choose what to monitor - I have three choices  
[*] The "GNUSound" application lets me enter the source (hw:0,1) but crashes as soon as I hit record
```
alsa_open:630: initializing playback device
set_hwparams:420: format: 2, channels: 2, rate: 44100, access: 3
set_hwparams:457: rate: 44100
set_hwparams:466: rrate: 44100
set_hwparams:474: buffer time: 100000
set_hwparams:502: buffer size: 4410
set_hwparams:524: period_size: 210
alsa_open:649: initializing record device
set_hwparams:420: format: 2, channels: 1, rate: 44100, access: 3
FAIL : player_alsa.c:set_hwparams:452: Channels count (1) not available for (null): Invalid argument
FAIL : player_alsa.c:alsa_init_device:568: Setting of hwparams failed: Invalid argument
FAIL : player_alsa.c:alsa_open:662: Initialization error on record device spdif: Invalid argument
```
Looks to me like it's confused about that mono spdif  
[/LIST] 

In a convoluted way I can use jack to access the spdif from gui apps but I have to run three different things, setup all the connections, start a project, just to record (then do it all over again to play back)

All I want to do is fire up an app, choose the spdif in, hit record, watch the meters go up and down, hit stop when done.
If I can't redirect that to the analogue out due to the clock mismatch then I can live without hearing it, I can listen to the analogue outs of the device producing the spdif instead. 

If anyone has some tips or recommendations I'd love to hear from you. I can post more info if required.

for now I'll just keep doing 
arecord -d 1500 -f cd -t wav -D spdif file.wav

---

