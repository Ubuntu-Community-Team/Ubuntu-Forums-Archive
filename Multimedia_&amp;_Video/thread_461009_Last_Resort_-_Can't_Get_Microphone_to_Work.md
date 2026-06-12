---
title: "Last Resort - Can't Get Microphone to Work"
date: 2007-06-01
forum: Multimedia &amp; Video
---

### Post by mattmueller on 2007-06-01
Hey guys, I hate to dirty the forums with another please help me post but after spending the past few hours scouring these and other forums, I just can't get an answer to my problem.

I am trying to get my microphone to work under feisty...sound output works fine, but I can't get anything captured from my mic no matter what I do.  I have tried enabling everything that might even have anything remotely to do with recording, toggling all of the various settings combinations, etc. all to no avail.  I can't even hear myself through the speakers when I try to record...sound recorder acts like it is recording but then when I hit play there is nothing to play.

Hopefully someone can help me, I am adding a few outputs here that might be of use (I'm not sure).

Thanks in advance, I really appreciate it.

Output of lspci | grep -i audio:
```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

```

Out put of amixer command:
```
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
  Limits: Playback 0 - 39
  Mono:
  Front Left: Playback 36 [92%] [-4.50dB] [on]
  Front Right: Playback 36 [92%] [-4.50dB] [on]
Simple mixer control 'Front Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [12.00dB] [on]
  Front Right: Playback 31 [100%] [12.00dB] [on]
Simple mixer control 'Front Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 3 [100%]
  Front Right: 3 [100%]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 39
  Mono:
  Front Left: Playback 0 [0%] [-58.50dB] [off]
  Front Right: Playback 0 [0%] [-58.50dB] [off]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 39
  Mono: Playback 0 [0%] [-58.50dB] [off]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 39
  Mono: Playback 0 [0%] [-58.50dB] [off]
Simple mixer control 'Side',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 39
  Mono:
  Front Left: Playback 0 [0%] [-58.50dB] [off]
  Front Right: Playback 0 [0%] [-58.50dB] [off]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [12.00dB] [on]
  Front Right: Playback 31 [100%] [12.00dB] [on]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [12.00dB] [on]
  Front Right: Playback 31 [100%] [12.00dB] [on]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [12.00dB] [on]
  Front Right: Playback 31 [100%] [12.00dB] [on]
Simple mixer control 'Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 3 [100%]
  Front Right: 3 [100%]
Simple mixer control 'IEC958',0
  Capabilities: pvolume cvolume pswitch pswitch-joined cswitch cswitch-joined
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 39 Capture 0 - 31
  Front Left: Playback 39 [100%] [0.00dB] [on] Capture 30 [97%] [10.50dB] [on]
  Front Right: Playback 39 [100%] [0.00dB] [on] Capture 30 [97%] [10.50dB] [on]
Simple mixer control 'IEC958 Playback Source',0
  Capabilities: enum
  Items: 'PCM' 'ADC1' 'ADC2' 'ADC3'
  Item0: 'PCM'
Simple mixer control 'Mono',0
  Capabilities: pswitch
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [off]
  Front Right: Playback [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 54
  Front Left: Capture 0 [0%] [-58.50dB] [off]
  Front Right: Capture 0 [0%] [-58.50dB] [off]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 54
  Front Left: Capture 41 [76%] [3.00dB] [on]
  Front Right: Capture 41 [76%] [3.00dB] [on]
Simple mixer control 'Capture',2
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 54
  Front Left: Capture 38 [70%] [-1.50dB] [on]
  Front Right: Capture 38 [70%] [-1.50dB] [on]
Simple mixer control 'Analog Mix',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [off]
  Front Right: Playback 31 [100%] [0.00dB] [off]
Simple mixer control 'Beep',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 15
  Mono:
  Front Left: Playback 8 [53%] [-21.00dB] [off]
  Front Right: Playback 6 [40%] [-27.00dB] [on]
Simple mixer control 'Input Source',0
  Capabilities: enum
  Items: 'Front Mic' 'Line' 'Mic' 'CD' 'Mix'
  Item0: 'Front Mic'
Simple mixer control 'Input Source',1
  Capabilities: enum
  Items: 'Front Mic' 'Line' 'Mic' 'CD' 'Mix'
  Item0: 'Mic'
Simple mixer control 'Input Source',2
  Capabilities: enum
  Items: 'Front Mic' 'Line' 'Mic' 'CD' 'Mix'
  Item0: 'Line'

```

Anyone have any ideas?  I'm getting desperate at this point heh, but refuse to switch to windows just to get this to work...

Thanks,
Matt

---

### Post by icechen1 on 2007-06-01
You are not the only one,lots if people have problem with microphone, including me.
Maybe you can put ```
# HDA-INTEL fix
options snd-hda-intel model=ref probe_mask=1
```
in [HTML]gksudo gedit /etc/modprobe.d/alsa-base
[/HTML]
I heard some people fixed it with this.

---

### Post by NilsE on 2007-06-01
Here is a couple of other things to try that worked for me with and Intel chip.

In a terminal run: asoundconf  list

This should return a list of cards.  Yours should be Intel
In a terminal run: asoundconf set-default-card Intel

Then again with sudo: sudo asoundconf set-default-card Intel
  
This will set the defaults for the card and create a config file. If yours is not Intel replace it with the name you found in list. In sound preferences "ALSA - Advanced Linux Sound Architecture" should be the choice except mixer should be Sigmatel.

In the volume control turn on as many options as you can to show up in the panel. Make sure none are muted.

---

### Post by mattmueller on 2007-06-02
Thanks for the suggestions, but so far nothing has worked ::sigh:::

---

