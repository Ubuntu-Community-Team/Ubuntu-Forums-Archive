---
title: "Problems with the microphone"
date: 2011-12-30
forum: Multimedia Software
---

### Post by Edward256 on 2011-12-30
Hi.
I've been all over the place trying to find a solution for this. I've just installed Ubuntu 11.10, then added xubuntu for a nicer look. I managed to get the microphone to work in Audacity because it allowed me to select all possible inputs. However, in another application that doesn't allow this menu I can't record any sound. I'm guessing it used the system default so I click on the speaker icon (task tray), click on Sound Settings, click the Input tab, and see that the Connector is on "Analog Line-In". I tried plugging the microphone into the other ports with no luck. I took a look at the drop down list for the Connector and found "Analog Microphone". I chose that and a second later it reset itself to "Analog Line-In".
The options in Audacity are as follows:
*SB Audigy 2 [SB0240]: Mic Capture (hw:0,1)
 SB Audigy 2 [SB0240]: Multichannel Capture/PT Playback (hw:0,2)
 SB Audigy 2 [SB0240]: p16v (hw:0,4)
 pulse
 default
(* selected)

The options in the Sound Settings are as follows:
Analog Video
Analog Input
Analog Line-In
Analog Microphone / Microphone 2
Analog Microphone / Microphone 1

No matter what I select it always resets itself to Analog Line-In.
Is there any way to unlock this?

/Edward

---

### Post by inobe on 2011-12-30
run alsamixer in terminal, look for something muted, lowered volumes.

[IMG]http://www.gentoo.org/images/docs/alsa-mixermuted.png[/IMG]

if that doesn't work install pavucontrol and look in inputs or recording, at bottom select apps.

[IMG]http://img692.imageshack.us/img692/5086/pavucontrol2.png[/IMG]

---

### Post by Edward256 on 2011-12-30
I've opened alsamixer and turned up everything. Now I get a very loud feedback from the mic into the headset.
I've installed pavucontrol, clicked on the Input Devices tab, clicked on Port and a second after selecting "Analog Microphone / Microphone 1" it resets itself to "Analog Line-In".

/Edward

---

### Post by inobe on 2011-12-30
toy with the levels a bit, too much volume is, well, too much :P

take your time, no rush.

---

### Post by Edward256 on 2011-12-30
Ok, I found that AMIX was what gave the loud feedback. Still able to record sound in Audacity, but I still can't set the Input Connector/Port to "Analog Microphone".

/Edward

---

### Post by inobe on 2011-12-30
no mention of the' other application :)

---

### Post by lidex on 2011-12-31
Can you post output of amixer:
```
amixer
```

---

### Post by Edward256 on 2012-01-01
```

:~$ amixer
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined cvolume cswitch cswitch-joined penum
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 31
  Mono: Playback 16 [16%] [-33.60dB]
  Front Left: Capture 31 [100%] [0.00dB] [on]
  Front Right: Capture 31 [100%] [0.00dB] [on]
Simple mixer control 'Tone',0
  Capabilities: pswitch penum
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [on]
  Front Right: Playback [on]
Simple mixer control 'Bass',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 40
  Front Left: 20 [50%]
  Front Right: 20 [50%]
Simple mixer control 'Treble',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 40
  Front Left: 20 [50%]
  Front Right: 20 [50%]
Simple mixer control '3D Control Sigmatel - Depth',0
  Capabilities: volume volume-joined penum
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 3
  Mono: 3 [100%]
Simple mixer control 'PCM',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 100
  Front Left: Capture 100 [100%] [0.00dB]
  Front Right: Capture 100 [100%] [0.00dB]
Simple mixer control 'PCM Center',0
  Capabilities: pvolume pvolume-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 100
  Mono: Playback 100 [100%] [0.00dB]
Simple mixer control 'PCM Front',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100
  Mono:
  Front Left: Playback 100 [100%] [0.00dB]
  Front Right: Playback 100 [100%] [0.00dB]
Simple mixer control 'PCM LFE',0
  Capabilities: pvolume pvolume-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 100
  Mono: Playback 100 [100%] [0.00dB]
Simple mixer control 'PCM Side',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100
  Mono:
  Front Left: Playback 100 [100%] [0.00dB]
  Front Right: Playback 100 [100%] [0.00dB]
Simple mixer control 'PCM Surround',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100
  Mono:
  Front Left: Playback 100 [100%] [0.00dB]
  Front Right: Playback 100 [100%] [0.00dB]
Simple mixer control 'Front',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100
  Mono:
  Front Left: Playback 100 [100%] [0.00dB]
  Front Right: Playback 100 [100%] [0.00dB]
Simple mixer control 'Surround',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100
  Mono:
  Front Left: Playback 100 [100%] [0.00dB]
  Front Right: Playback 100 [100%] [0.00dB]
Simple mixer control 'Surround Phase Inversion',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 100
  Mono: Playback 100 [100%] [0.00dB]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 100
  Mono: Playback 100 [100%] [0.00dB]
Simple mixer control 'Side',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100
  Mono:
  Front Left: Playback 100 [100%] [0.00dB]
  Front Right: Playback 100 [100%] [0.00dB]
Simple mixer control 'Synth',0
  Capabilities: pvolume cvolume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 50 [50%] [-20.00dB] Capture 100 [100%] [0.00dB]
  Front Right: Playback 50 [50%] [-20.00dB] Capture 100 [100%] [0.00dB]
Simple mixer control 'Wave',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100
  Mono:
  Front Left: Playback 100 [100%] [0.00dB]
  Front Right: Playback 100 [100%] [0.00dB]
Simple mixer control 'Line',0
  Capabilities: cvolume cswitch cswitch-joined penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 31 [100%] [12.00dB] [on]
  Front Right: Capture 31 [100%] [12.00dB] [on]
Simple mixer control 'CD',0
  Capabilities: cvolume cswitch cswitch-joined penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 31 [100%] [12.00dB] [off]
  Front Right: Capture 31 [100%] [12.00dB] [off]
Simple mixer control 'Mic',0
  Capabilities: cvolume cvolume-joined cswitch cswitch-joined penum
  Capture channels: Mono
  Limits: Capture 0 - 31
  Mono: Capture 31 [100%] [12.00dB] [off]
Simple mixer control 'Mic Boost (+20dB)',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Mic Select',0
  Capabilities: enum
  Items: 'Mic1' 'Mic2'
  Item0: 'Mic1'
Simple mixer control 'Video',0
  Capabilities: cvolume cswitch cswitch-joined penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 31 [100%] [12.00dB] [off]
  Front Right: Capture 31 [100%] [12.00dB] [off]
Simple mixer control 'Phone',0
  Capabilities: cvolume cvolume-joined cswitch cswitch-joined penum
  Capture channels: Mono
  Limits: Capture 0 - 31
  Mono: Capture 31 [100%] [12.00dB] [off]
Simple mixer control 'IEC958 Optical',0
  Capabilities: pvolume cvolume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 100 [100%] [0.00dB] Capture 100 [100%] [0.00dB]
  Front Right: Playback 100 [100%] [0.00dB] Capture 100 [100%] [0.00dB]
Simple mixer control 'IEC958 Optical Raw',0
  Capabilities: pswitch penum
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [off]
  Front Right: Playback [off]
Simple mixer control 'Beep',0
  Capabilities: cvolume cvolume-joined cswitch cswitch-joined penum
  Capture channels: Mono
  Limits: Capture 0 - 15
  Mono: Capture 0 [0%] [-45.00dB] [off]
Simple mixer control 'Aux',0
  Capabilities: cvolume cswitch cswitch-joined penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 31 [100%] [12.00dB] [off]
  Front Right: Capture 31 [100%] [12.00dB] [off]
Simple mixer control 'Aux2',0
  Capabilities: pvolume cvolume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 100 [100%] [0.00dB] Capture 100 [100%] [0.00dB]
  Front Right: Playback 100 [100%] [0.00dB] Capture 100 [100%] [0.00dB]
Simple mixer control 'Mono Output Select',0
  Capabilities: enum
  Items: 'Mix' 'Mic'
  Item0: 'Mix'
Simple mixer control 'AMic',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100
  Mono:
  Front Left: Playback 0 [0%] [-99999.99dB]
  Front Right: Playback 0 [0%] [-99999.99dB]
Simple mixer control 'Analog Capture Boost',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Analog Mix',0
  Capabilities: pvolume cvolume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 100 [100%] [0.00dB] Capture 100 [100%] [0.00dB]
  Front Right: Playback 100 [100%] [0.00dB] Capture 100 [100%] [0.00dB]
Simple mixer control 'Audigy Analog/Digital Output Jack',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Audigy CD',0
  Capabilities: pvolume cvolume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 100 [100%] [0.00dB] Capture 100 [100%] [0.00dB]
  Front Right: Playback 100 [100%] [0.00dB] Capture 100 [100%] [0.00dB]
Simple mixer control 'External Amplifier',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'HD Analog Center/LFE',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 207 [81%] [0.00dB]
  Front Right: Playback 207 [81%] [0.00dB]
Simple mixer control 'HD Analog Front',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 207 [81%] [0.00dB]
  Front Right: Playback 207 [81%] [0.00dB]
Simple mixer control 'HD Analog Rear',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 207 [81%] [0.00dB]
  Front Right: Playback 207 [81%] [0.00dB]
Simple mixer control 'HD Analog Side',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 207 [81%] [0.00dB]
  Front Right: Playback 207 [81%] [0.00dB]
Simple mixer control 'HD SPDIF Center/LFE',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 207 [81%] [0.00dB]
  Front Right: Playback 207 [81%] [0.00dB]
Simple mixer control 'HD SPDIF Front',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 207 [81%] [0.00dB]
  Front Right: Playback 207 [81%] [0.00dB]
Simple mixer control 'HD SPDIF Rear',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 207 [81%] [0.00dB]
  Front Right: Playback 207 [81%] [0.00dB]
Simple mixer control 'HD SPDIF Side',0
  Capabilities: pvolume penum
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
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]

```

---

### Post by lidex on 2012-01-02
You may want to play around with these elements in alsamixer:
```
Simple mixer control 'Audigy Analog/Digital Output Jack',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'HD channel Capture',0
  Capabilities: enum
  Items: '0' '1' '2' '3'
  Item0: '0'
Simple mixer control 'HD source Capture',0
  Capabilities: enum
  Items: 'SPDIF' 'I2S' 'SRC48' 'SRCMulti_SPDIF' 'SRCMulti_I2S' 'CDIF' 'FX' 'AC97'
  Item0: 'SPDIF'

```

---

### Post by Edward256 on 2012-01-02
Ok, I played with those elements but nothing seemed to register (at least on the Sound Settings Input Meter). I then remembered that there were a few blanks in the Capture view (F4) and managed to find out how to turn them on. I set "Mic" to Capture and I could record sound! What fun! :D
```

:~$ amixer
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined cvolume cswitch cswitch-joined penum
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 31
  Mono: Playback 32 [32%] [-27.20dB]
  Front Left: Capture 31 [100%] [0.00dB] [on]
  Front Right: Capture 31 [100%] [0.00dB] [on]
Simple mixer control 'Tone',0
  Capabilities: pswitch penum
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [on]
  Front Right: Playback [on]
Simple mixer control 'Bass',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 40
  Front Left: 20 [50%]
  Front Right: 20 [50%]
Simple mixer control 'Treble',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 40
  Front Left: 20 [50%]
  Front Right: 20 [50%]
Simple mixer control '3D Control Sigmatel - Depth',0
  Capabilities: volume volume-joined penum
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 3
  Mono: 3 [100%]
Simple mixer control 'PCM',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 100
  Front Left: Capture 100 [100%] [0.00dB]
  Front Right: Capture 100 [100%] [0.00dB]
Simple mixer control 'PCM Center',0
  Capabilities: pvolume pvolume-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 100
  Mono: Playback 100 [100%] [0.00dB]
Simple mixer control 'PCM Front',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100
  Mono:
  Front Left: Playback 100 [100%] [0.00dB]
  Front Right: Playback 100 [100%] [0.00dB]
Simple mixer control 'PCM LFE',0
  Capabilities: pvolume pvolume-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 100
  Mono: Playback 100 [100%] [0.00dB]
Simple mixer control 'PCM Side',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100
  Mono:
  Front Left: Playback 100 [100%] [0.00dB]
  Front Right: Playback 100 [100%] [0.00dB]
Simple mixer control 'PCM Surround',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100
  Mono:
  Front Left: Playback 100 [100%] [0.00dB]
  Front Right: Playback 100 [100%] [0.00dB]
Simple mixer control 'Front',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100
  Mono:
  Front Left: Playback 100 [100%] [0.00dB]
  Front Right: Playback 100 [100%] [0.00dB]
Simple mixer control 'Surround',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100
  Mono:
  Front Left: Playback 100 [100%] [0.00dB]
  Front Right: Playback 100 [100%] [0.00dB]
Simple mixer control 'Surround Phase Inversion',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 100
  Mono: Playback 100 [100%] [0.00dB]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 100
  Mono: Playback 100 [100%] [0.00dB]
Simple mixer control 'Side',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100
  Mono:
  Front Left: Playback 100 [100%] [0.00dB]
  Front Right: Playback 100 [100%] [0.00dB]
Simple mixer control 'Synth',0
  Capabilities: pvolume cvolume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 50 [50%] [-20.00dB] Capture 100 [100%] [0.00dB]
  Front Right: Playback 50 [50%] [-20.00dB] Capture 100 [100%] [0.00dB]
Simple mixer control 'Wave',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100
  Mono:
  Front Left: Playback 100 [100%] [0.00dB]
  Front Right: Playback 100 [100%] [0.00dB]
Simple mixer control 'Line',0
  Capabilities: cvolume cswitch cswitch-joined penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 31 [100%] [12.00dB] [on]
  Front Right: Capture 31 [100%] [12.00dB] [on]
Simple mixer control 'CD',0
  Capabilities: cvolume cswitch cswitch-joined penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 31 [100%] [12.00dB] [on]
  Front Right: Capture 31 [100%] [12.00dB] [on]
Simple mixer control 'Mic',0
  Capabilities: cvolume cvolume-joined cswitch cswitch-joined penum
  Capture channels: Mono
  Limits: Capture 0 - 31
  Mono: Capture 31 [100%] [12.00dB] [on]
Simple mixer control 'Mic Boost (+20dB)',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Mic Select',0
  Capabilities: enum
  Items: 'Mic1' 'Mic2'
  Item0: 'Mic1'
Simple mixer control 'Video',0
  Capabilities: cvolume cswitch cswitch-joined penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 31 [100%] [12.00dB] [on]
  Front Right: Capture 31 [100%] [12.00dB] [on]
Simple mixer control 'Phone',0
  Capabilities: cvolume cvolume-joined cswitch cswitch-joined penum
  Capture channels: Mono
  Limits: Capture 0 - 31
  Mono: Capture 31 [100%] [12.00dB] [on]
Simple mixer control 'IEC958 Optical',0
  Capabilities: pvolume cvolume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 100 [100%] [0.00dB] Capture 100 [100%] [0.00dB]
  Front Right: Playback 100 [100%] [0.00dB] Capture 100 [100%] [0.00dB]
Simple mixer control 'IEC958 Optical Raw',0
  Capabilities: pswitch penum
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [off]
  Front Right: Playback [off]
Simple mixer control 'Beep',0
  Capabilities: cvolume cvolume-joined cswitch cswitch-joined penum
  Capture channels: Mono
  Limits: Capture 0 - 15
  Mono: Capture 0 [0%] [-45.00dB] [off]
Simple mixer control 'Aux',0
  Capabilities: cvolume cswitch cswitch-joined penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 31 [100%] [12.00dB] [on]
  Front Right: Capture 31 [100%] [12.00dB] [on]
Simple mixer control 'Aux2',0
  Capabilities: pvolume cvolume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 100 [100%] [0.00dB] Capture 100 [100%] [0.00dB]
  Front Right: Playback 100 [100%] [0.00dB] Capture 100 [100%] [0.00dB]
Simple mixer control 'Mono Output Select',0
  Capabilities: enum
  Items: 'Mix' 'Mic'
  Item0: 'Mix'
Simple mixer control 'AMic',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100
  Mono:
  Front Left: Playback 0 [0%] [-99999.99dB]
  Front Right: Playback 0 [0%] [-99999.99dB]
Simple mixer control 'Analog Capture Boost',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Analog Mix',0
  Capabilities: pvolume cvolume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 100 [100%] [0.00dB] Capture 100 [100%] [0.00dB]
  Front Right: Playback 100 [100%] [0.00dB] Capture 100 [100%] [0.00dB]
Simple mixer control 'Audigy Analog/Digital Output Jack',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Audigy CD',0
  Capabilities: pvolume cvolume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 100 [100%] [0.00dB] Capture 100 [100%] [0.00dB]
  Front Right: Playback 100 [100%] [0.00dB] Capture 100 [100%] [0.00dB]
Simple mixer control 'External Amplifier',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'HD Analog Center/LFE',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 207 [81%] [0.00dB]
  Front Right: Playback 207 [81%] [0.00dB]
Simple mixer control 'HD Analog Front',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 207 [81%] [0.00dB]
  Front Right: Playback 207 [81%] [0.00dB]
Simple mixer control 'HD Analog Rear',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 207 [81%] [0.00dB]
  Front Right: Playback 207 [81%] [0.00dB]
Simple mixer control 'HD Analog Side',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 207 [81%] [0.00dB]
  Front Right: Playback 207 [81%] [0.00dB]
Simple mixer control 'HD SPDIF Center/LFE',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 207 [81%] [0.00dB]
  Front Right: Playback 207 [81%] [0.00dB]
Simple mixer control 'HD SPDIF Front',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 207 [81%] [0.00dB]
  Front Right: Playback 207 [81%] [0.00dB]
Simple mixer control 'HD SPDIF Rear',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 207 [81%] [0.00dB]
  Front Right: Playback 207 [81%] [0.00dB]
Simple mixer control 'HD SPDIF Side',0
  Capabilities: pvolume penum
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
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]

```

However.... When I restarted the computer (full shutdown and reboot) the "Mic" had turned itself off completely.
```

:~$ amixer
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined cvolume cswitch cswitch-joined penum
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 31
  Mono: Playback 32 [32%] [-27.20dB]
  Front Left: Capture 31 [100%] [0.00dB] [on]
  Front Right: Capture 31 [100%] [0.00dB] [on]
Simple mixer control 'Tone',0
  Capabilities: pswitch penum
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [on]
  Front Right: Playback [on]
Simple mixer control 'Bass',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 40
  Front Left: 20 [50%]
  Front Right: 20 [50%]
Simple mixer control 'Treble',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 40
  Front Left: 20 [50%]
  Front Right: 20 [50%]
Simple mixer control '3D Control Sigmatel - Depth',0
  Capabilities: volume volume-joined penum
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 3
  Mono: 3 [100%]
Simple mixer control 'PCM',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 100
  Front Left: Capture 100 [100%] [0.00dB]
  Front Right: Capture 100 [100%] [0.00dB]
Simple mixer control 'PCM Center',0
  Capabilities: pvolume pvolume-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 100
  Mono: Playback 100 [100%] [0.00dB]
Simple mixer control 'PCM Front',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100
  Mono:
  Front Left: Playback 100 [100%] [0.00dB]
  Front Right: Playback 100 [100%] [0.00dB]
Simple mixer control 'PCM LFE',0
  Capabilities: pvolume pvolume-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 100
  Mono: Playback 100 [100%] [0.00dB]
Simple mixer control 'PCM Side',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100
  Mono:
  Front Left: Playback 100 [100%] [0.00dB]
  Front Right: Playback 100 [100%] [0.00dB]
Simple mixer control 'PCM Surround',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100
  Mono:
  Front Left: Playback 100 [100%] [0.00dB]
  Front Right: Playback 100 [100%] [0.00dB]
Simple mixer control 'Front',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100
  Mono:
  Front Left: Playback 100 [100%] [0.00dB]
  Front Right: Playback 100 [100%] [0.00dB]
Simple mixer control 'Surround',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100
  Mono:
  Front Left: Playback 100 [100%] [0.00dB]
  Front Right: Playback 100 [100%] [0.00dB]
Simple mixer control 'Surround Phase Inversion',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 100
  Mono: Playback 100 [100%] [0.00dB]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 100
  Mono: Playback 100 [100%] [0.00dB]
Simple mixer control 'Side',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100
  Mono:
  Front Left: Playback 100 [100%] [0.00dB]
  Front Right: Playback 100 [100%] [0.00dB]
Simple mixer control 'Synth',0
  Capabilities: pvolume cvolume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 50 [50%] [-20.00dB] Capture 100 [100%] [0.00dB]
  Front Right: Playback 50 [50%] [-20.00dB] Capture 100 [100%] [0.00dB]
Simple mixer control 'Wave',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100
  Mono:
  Front Left: Playback 100 [100%] [0.00dB]
  Front Right: Playback 100 [100%] [0.00dB]
Simple mixer control 'Line',0
  Capabilities: cvolume cswitch cswitch-joined penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 31 [100%] [12.00dB] [on]
  Front Right: Capture 31 [100%] [12.00dB] [on]
Simple mixer control 'CD',0
  Capabilities: cvolume cswitch cswitch-joined penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 31 [100%] [12.00dB] [on]
  Front Right: Capture 31 [100%] [12.00dB] [on]
Simple mixer control 'Mic',0
  Capabilities: cvolume cvolume-joined cswitch cswitch-joined penum
  Capture channels: Mono
  Limits: Capture 0 - 31
  Mono: Capture 0 [0%] [-34.50dB] [off]
Simple mixer control 'Mic Boost (+20dB)',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Mic Select',0
  Capabilities: enum
  Items: 'Mic1' 'Mic2'
  Item0: 'Mic1'
Simple mixer control 'Video',0
  Capabilities: cvolume cswitch cswitch-joined penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 0 [0%] [-34.50dB] [off]
  Front Right: Capture 0 [0%] [-34.50dB] [off]
Simple mixer control 'Phone',0
  Capabilities: cvolume cvolume-joined cswitch cswitch-joined penum
  Capture channels: Mono
  Limits: Capture 0 - 31
  Mono: Capture 31 [100%] [12.00dB] [on]
Simple mixer control 'IEC958 Optical',0
  Capabilities: pvolume cvolume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 100 [100%] [0.00dB] Capture 100 [100%] [0.00dB]
  Front Right: Playback 100 [100%] [0.00dB] Capture 100 [100%] [0.00dB]
Simple mixer control 'IEC958 Optical Raw',0
  Capabilities: pswitch penum
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [off]
  Front Right: Playback [off]
Simple mixer control 'Beep',0
  Capabilities: cvolume cvolume-joined cswitch cswitch-joined penum
  Capture channels: Mono
  Limits: Capture 0 - 15
  Mono: Capture 0 [0%] [-45.00dB] [off]
Simple mixer control 'Aux',0
  Capabilities: cvolume cswitch cswitch-joined penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 0 [0%] [-34.50dB] [off]
  Front Right: Capture 0 [0%] [-34.50dB] [off]
Simple mixer control 'Aux2',0
  Capabilities: pvolume cvolume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 100 [100%] [0.00dB] Capture 100 [100%] [0.00dB]
  Front Right: Playback 100 [100%] [0.00dB] Capture 100 [100%] [0.00dB]
Simple mixer control 'Mono Output Select',0
  Capabilities: enum
  Items: 'Mix' 'Mic'
  Item0: 'Mix'
Simple mixer control 'AMic',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100
  Mono:
  Front Left: Playback 0 [0%] [-99999.99dB]
  Front Right: Playback 0 [0%] [-99999.99dB]
Simple mixer control 'Analog Capture Boost',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Analog Mix',0
  Capabilities: pvolume cvolume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 100 [100%] [0.00dB] Capture 100 [100%] [0.00dB]
  Front Right: Playback 100 [100%] [0.00dB] Capture 100 [100%] [0.00dB]
Simple mixer control 'Audigy Analog/Digital Output Jack',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Audigy CD',0
  Capabilities: pvolume cvolume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 100 [100%] [0.00dB] Capture 100 [100%] [0.00dB]
  Front Right: Playback 100 [100%] [0.00dB] Capture 100 [100%] [0.00dB]
Simple mixer control 'External Amplifier',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'HD Analog Center/LFE',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 207 [81%] [0.00dB]
  Front Right: Playback 207 [81%] [0.00dB]
Simple mixer control 'HD Analog Front',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 207 [81%] [0.00dB]
  Front Right: Playback 207 [81%] [0.00dB]
Simple mixer control 'HD Analog Rear',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 207 [81%] [0.00dB]
  Front Right: Playback 207 [81%] [0.00dB]
Simple mixer control 'HD Analog Side',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 207 [81%] [0.00dB]
  Front Right: Playback 207 [81%] [0.00dB]
Simple mixer control 'HD SPDIF Center/LFE',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 207 [81%] [0.00dB]
  Front Right: Playback 207 [81%] [0.00dB]
Simple mixer control 'HD SPDIF Front',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 207 [81%] [0.00dB]
  Front Right: Playback 207 [81%] [0.00dB]
Simple mixer control 'HD SPDIF Rear',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 207 [81%] [0.00dB]
  Front Right: Playback 207 [81%] [0.00dB]
Simple mixer control 'HD SPDIF Side',0
  Capabilities: pvolume penum
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
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]

```

So what is it that might be locking it, and any way to either unlock or relock to "Mic"?

/Edward

---

### Post by lidex on 2012-01-03
Mic Select, maybe? Have you tried changing the status of 'Audigy Analog/Digital Output Jack' - that has been responsible for various audio issues. Let's see your full info. Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by Edward256 on 2012-01-03
Tried muting "Audigy Analog/Digital Output Jack", changing "Mic1" to "Mic2", and unmuted the "Mic", but after the reboot "Mic2" went back to "Mic1", "Mic" got muted, but "Audigy Analog/Digital Output Jack" stayed muted.
Here's the alsa-info:
[http://www.alsa-project.org/db/?f=521c1cd82bdf0cf2a0cd7141d9e5c23d383c8cae](http://www.alsa-project.org/db/?f=521c1cd82bdf0cf2a0cd7141d9e5c23d383c8cae)

/Edward

---

### Post by lidex on 2012-01-03
Try resetting your pulse configuration. ```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```

Now set alsamixer up to where it does record, escape that and save the setting with:
```
sudo alsactl store 0
```

Reboot

---

### Post by Edward256 on 2012-01-03
Ok, I did all that and now the mic volume stays, BUT the speaker icon in the task bar is greyed out (looks like mute). I click for Sound Settings and all sliders are greyed out and there are no devices in the Hardware tab.

/Edward

---

### Post by lidex on 2012-01-04
> **Edward256 said:**
> Ok, I did all that and now the mic volume stays, BUT the speaker icon in the task bar is greyed out (looks like mute). I click for Sound Settings and all sliders are greyed out and there are no devices in the Hardware tab.

/Edward

What about alsamixer?

I think pulse is to blame. Try reinstalling it. ```
sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio
```
```
sudo apt-get install pulseaudio gstreamer0.10-pulseaudio
```
**Reboot.**

---

### Post by Edward256 on 2012-01-04
In alsamixer everything looked ok. Correct card selected, volumes high.

Now, after purging and reinstalling PulseAudio the speaker icon has vanished and no sound from anywhere.

I load pavucontrol and it says "Connection to PulseAudio failed. Automatic retry in 5s"
"In this case this is likely because PULSE_SERVER in the Environment/X11 Root Window Properties or default-server in client.conf is misconfigured. This situation can also arrise when PulseAudio crashed and left stale details in the X11 Root Window. If this is the case, then PulseAudio should autospawn again, or if this is not configured you should run start-pulseaudio-x11 manually."

I did what it suggested:
```

:~$ start-pulseaudio-x11
Connection failure: Connection refused
pa_context_connect() failed: Connection refused

```

Alsamixer still looks fine.

/Edward

---

### Post by lidex on 2012-01-04
> **Edward256 said:**
> In alsamixer everything looked ok. Correct card selected, volumes high.

Now, after purging and reinstalling PulseAudio the speaker icon has vanished and no sound from anywhere.

I load pavucontrol and it says "Connection to PulseAudio failed. Automatic retry in 5s"
"In this case this is likely because PULSE_SERVER in the Environment/X11 Root Window Properties or default-server in client.conf is misconfigured. This situation can also arrise when PulseAudio crashed and left stale details in the X11 Root Window. If this is the case, then PulseAudio should autospawn again, or if this is not configured you should run start-pulseaudio-x11 manually."

I did what it suggested:
```

:~$ start-pulseaudio-x11
Connection failure: Connection refused
pa_context_connect() failed: Connection refused

```

Alsamixer still looks fine.

/Edward
I would try purging your pulse config again:

```
rm -r ~/.pulse ~/.pulse-cookie 
```
Restart then this command:
```
pkill pulseaudio; sleep 2; pulseaudio -vv
```

---

### Post by Edward256 on 2012-01-04
Did those commands exactly and now the terminal is full of text and paused.
I opened YouTube to test and got some more text but no sound, closed YouTube, more text was printed.
Did the same for Skype and here's the terminal log (forgot to unset the history limit):
```

I: [pulseaudio] source.c:     device.product.id = "0004"
I: [pulseaudio] source.c:     device.product.name = "SB Audigy"
I: [pulseaudio] source.c:     device.string = "hw:0"
I: [pulseaudio] source.c:     device.buffering.buffer_size = "65536"
I: [pulseaudio] source.c:     device.buffering.fragment_size = "32768"
I: [pulseaudio] source.c:     device.access_mode = "mmap+timer"
I: [pulseaudio] source.c:     device.profile.name = "analog-stereo"
I: [pulseaudio] source.c:     device.profile.description = "Analog Stereo"
I: [pulseaudio] source.c:     device.description = "SB Audigy Analog Stereo"
I: [pulseaudio] source.c:     alsa.mixer_name = "SigmaTel STAC9721,23"
I: [pulseaudio] source.c:     alsa.components = "AC97a:83847609"
I: [pulseaudio] source.c:     module-udev-detect.discovered = "1"
I: [pulseaudio] source.c:     device.icon_name = "audio-card-pci"
I: [pulseaudio] alsa-source.c: Using 2.0 fragments of size 32768 bytes (185.76ms), buffer size is 65536 bytes (371.52ms)
I: [pulseaudio] alsa-source.c: Time scheduling watermark is 20.00ms
D: [pulseaudio] alsa-source.c: hwbuf_unused=0
D: [pulseaudio] alsa-source.c: setting avail_min=15502
D: [pulseaudio] alsa-mixer.c: Activating path analog-input-microphone
D: [pulseaudio] alsa-mixer.c: Path analog-input-microphone (Analog Microphone), direction=2, priority=87, probed=yes, supported=yes, has_mute=yes, has_volume=yes, has_dB=yes, min_volume=0, max_volume=31, min_dB=-34.5, max_dB=12
D: [pulseaudio] alsa-mixer.c: Element Mic, direction=2, switch=1, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=4, required_absent=0, mask=0x7ffffffffffff, n_channels=1, override_map=yes
D: [pulseaudio] alsa-mixer.c: Element Mic Select, direction=2, switch=0, volume=0, volume_limit=-1, enumeration=1, required=0, required_any=0, required_absent=0, mask=0x0, n_channels=0, override_map=no
D: [pulseaudio] alsa-mixer.c: Option Mic1 (input-microphone-1/Microphone 1) index=0, priority=20
D: [pulseaudio] alsa-mixer.c: Option Mic2 (input-microphone-2/Microphone 2) index=1, priority=19
D: [pulseaudio] alsa-mixer.c: Element Line, direction=2, switch=2, volume=2, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x6, n_channels=2, override_map=no
D: [pulseaudio] alsa-mixer.c: Element Aux, direction=2, switch=2, volume=2, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x6, n_channels=2, override_map=no
D: [pulseaudio] alsa-mixer.c: Element Video, direction=2, switch=2, volume=2, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x6, n_channels=2, override_map=no
D: [pulseaudio] alsa-mixer.c: Setting input-microphone-1 (Microphone 1) priority=20
D: [pulseaudio] alsa-mixer.c: Setting input-microphone-2 (Microphone 2) priority=19
I: [pulseaudio] alsa-source.c: Successfully enabled synchronous volume.
I: [pulseaudio] alsa-source.c: Hardware volume ranges from -34.50 dB to 12.00 dB.
I: [pulseaudio] alsa-source.c: Fixing base volume to -12.00 dB
I: [pulseaudio] alsa-source.c: Using hardware volume control. Hardware dB scale supported.
I: [pulseaudio] alsa-source.c: Using hardware mute control.
D: [pulseaudio] alsa-util.c: snd_pcm_dump():
D: [pulseaudio] alsa-util.c: Hardware PCM card 0 'SB Audigy 2 [SB0240]' device 0 subdevice 0
D: [pulseaudio] alsa-util.c: Its setup is:
D: [pulseaudio] alsa-util.c:   stream       : CAPTURE
D: [pulseaudio] alsa-util.c:   access       : MMAP_INTERLEAVED
D: [pulseaudio] alsa-util.c:   format       : S16_LE
D: [pulseaudio] alsa-util.c:   subformat    : STD
D: [pulseaudio] alsa-util.c:   channels     : 2
D: [pulseaudio] alsa-util.c:   rate         : 44100
D: [pulseaudio] alsa-util.c:   exact rate   : 44100 (44100/1)
D: [pulseaudio] alsa-util.c:   msbits       : 16
D: [pulseaudio] alsa-util.c:   buffer_size  : 16384
D: [pulseaudio] alsa-util.c:   period_size  : 8192
D: [pulseaudio] alsa-util.c:   period_time  : 185759
D: [pulseaudio] alsa-util.c:   tstamp_mode  : ENABLE
D: [pulseaudio] alsa-util.c:   period_step  : 1
D: [pulseaudio] alsa-util.c:   avail_min    : 15502
D: [pulseaudio] alsa-util.c:   period_event : 0
D: [pulseaudio] alsa-util.c:   start_threshold  : -1
D: [pulseaudio] alsa-util.c:   stop_threshold   : 1073741824
D: [pulseaudio] alsa-util.c:   silence_threshold: 0
D: [pulseaudio] alsa-util.c:   silence_size : 0
D: [pulseaudio] alsa-util.c:   boundary     : 1073741824
D: [pulseaudio] alsa-util.c:   appl_ptr     : 0
D: [pulseaudio] alsa-util.c:   hw_ptr       : 0
D: [pulseaudio] alsa-source.c: Read hardware volume: 0: 100% 1: 100%
D: [pulseaudio] alsa-source.c:                in dB: 0: 0.00 dB 1: 0.00 dB
D: [alsa-source] alsa-source.c: Thread starting up
D: [alsa-source] core-util.c: RealtimeKit worked.
I: [alsa-source] core-util.c: Successfully enabled SCHED_RR scheduling for thread, with priority 5.
I: [alsa-source] alsa-source.c: Starting capture.
I: [pulseaudio] module.c: Loaded "module-alsa-card" (index: #4; argument: "device_id="0" name="pci-0000_03_0d.0" card_name="alsa_card.pci-0000_03_0d.0" namereg_fail=false tsched=yes ignore_dB=no deferred_volume=yes card_properties="module-udev-detect.discovered=1"").
I: [pulseaudio] module-udev-detect.c: Card /devices/pci0000:00/0000:00:1e.0/0000:03:0d.0/sound/card0 (alsa_card.pci-0000_03_0d.0) module loaded.
I: [pulseaudio] module-udev-detect.c: Found 1 cards.
I: [pulseaudio] module.c: Loaded "module-udev-detect" (index: #5; argument: "").
D: [pulseaudio] cli-command.c: Checking for existence of '/usr/lib/pulse-1.0/modules/module-jackdbus-detect.so': failure
D: [pulseaudio] cli-command.c: Checking for existence of '/usr/lib/pulse-1.0/modules/module-bluetooth-discover.so': failure
D: [pulseaudio] cli-command.c: Checking for existence of '/usr/lib/pulse-1.0/modules/module-esound-protocol-unix.so': success
I: [pulseaudio] module.c: Loaded "module-esound-protocol-unix" (index: #6; argument: "").
D: [pulseaudio] authkey.c: Got 0 bytes from cookie file '/home/isabel/.pulse-cookie', expected 256
I: [pulseaudio] module.c: Loaded "module-native-protocol-unix" (index: #7; argument: "").
D: [pulseaudio] cli-command.c: Checking for existence of '/usr/lib/pulse-1.0/modules/module-zeroconf-discover.so': failure
D: [pulseaudio] cli-command.c: Checking for existence of '/usr/lib/pulse-1.0/modules/module-raop-discover.so': failure
D: [pulseaudio] cli-command.c: Checking for existence of '/usr/lib/pulse-1.0/modules/module-gconf.so': failure
I: [pulseaudio] module.c: Loaded "module-default-device-restore" (index: #8; argument: "").
I: [pulseaudio] module.c: Loaded "module-rescue-streams" (index: #9; argument: "").
I: [pulseaudio] module.c: Loaded "module-always-sink" (index: #10; argument: "").
I: [pulseaudio] module.c: Loaded "module-intended-roles" (index: #11; argument: "").
D: [pulseaudio] module-suspend-on-idle.c: Sink alsa_output.pci-0000_03_0d.0.analog-stereo becomes idle, timeout in 5 seconds.
D: [pulseaudio] module-suspend-on-idle.c: Source alsa_input.pci-0000_03_0d.0.analog-stereo becomes idle, timeout in 5 seconds.
I: [pulseaudio] module.c: Loaded "module-suspend-on-idle" (index: #12; argument: "").
D: [pulseaudio] cli-command.c: Checking for existence of '/usr/lib/pulse-1.0/modules/module-console-kit.so': success
D: [pulseaudio] dbus-util.c: Successfully connected to D-Bus system bus bfa17933ce9b1ce11e1affc90000000f as :1.61
I: [pulseaudio] client.c: Created 0 "ConsoleKit Session /org/freedesktop/ConsoleKit/Session2"
D: [pulseaudio] module-console-kit.c: Added new session /org/freedesktop/ConsoleKit/Session2
I: [pulseaudio] module.c: Loaded "module-console-kit" (index: #13; argument: "").
I: [pulseaudio] module.c: Loaded "module-position-event-sounds" (index: #14; argument: "").
I: [pulseaudio] module.c: Loaded "module-filter-heuristics" (index: #15; argument: "").
I: [pulseaudio] module.c: Loaded "module-filter-apply" (index: #16; argument: "").
D: [pulseaudio] cli-command.c: Checking for existence of '/usr/lib/pulse-1.0/modules/module-dbus-protocol.so': success
D: [pulseaudio] core-subscribe.c: Dropped redundant event due to change event.
D: [pulseaudio] core-subscribe.c: Dropped redundant event due to change event.
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Memstats added for object /org/pulseaudio/core1/memstats
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.CardProfile added for object /org/pulseaudio/core1/card0/profile0
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.CardProfile added for object /org/pulseaudio/core1/card0/profile1
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.CardProfile added for object /org/pulseaudio/core1/card0/profile2
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.CardProfile added for object /org/pulseaudio/core1/card0/profile3
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.CardProfile added for object /org/pulseaudio/core1/card0/profile4
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.CardProfile added for object /org/pulseaudio/core1/card0/profile5
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.CardProfile added for object /org/pulseaudio/core1/card0/profile6
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.CardProfile added for object /org/pulseaudio/core1/card0/profile7
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.CardProfile added for object /org/pulseaudio/core1/card0/profile8
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.CardProfile added for object /org/pulseaudio/core1/card0/profile9
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.CardProfile added for object /org/pulseaudio/core1/card0/profile10
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.CardProfile added for object /org/pulseaudio/core1/card0/profile11
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.CardProfile added for object /org/pulseaudio/core1/card0/profile12
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.CardProfile added for object /org/pulseaudio/core1/card0/profile13
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.CardProfile added for object /org/pulseaudio/core1/card0/profile14
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.CardProfile added for object /org/pulseaudio/core1/card0/profile15
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.CardProfile added for object /org/pulseaudio/core1/card0/profile16
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.CardProfile added for object /org/pulseaudio/core1/card0/profile17
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.CardProfile added for object /org/pulseaudio/core1/card0/profile18
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.CardProfile added for object /org/pulseaudio/core1/card0/profile19
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.CardProfile added for object /org/pulseaudio/core1/card0/profile20
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.CardProfile added for object /org/pulseaudio/core1/card0/profile21
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.CardProfile added for object /org/pulseaudio/core1/card0/profile22
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.CardProfile added for object /org/pulseaudio/core1/card0/profile23
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.CardProfile added for object /org/pulseaudio/core1/card0/profile24
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.CardProfile added for object /org/pulseaudio/core1/card0/profile25
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.CardProfile added for object /org/pulseaudio/core1/card0/profile26
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.CardProfile added for object /org/pulseaudio/core1/card0/profile27
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.CardProfile added for object /org/pulseaudio/core1/card0/profile28
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Card added for object /org/pulseaudio/core1/card0
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.DevicePort added for object /org/pulseaudio/core1/sink0/port0
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.DevicePort added for object /org/pulseaudio/core1/sink0/port1
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Device added for object /org/pulseaudio/core1/sink0
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Sink added for object /org/pulseaudio/core1/sink0
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Device added for object /org/pulseaudio/core1/source0
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Source added for object /org/pulseaudio/core1/source0
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.DevicePort added for object /org/pulseaudio/core1/source1/port0
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.DevicePort added for object /org/pulseaudio/core1/source1/port1
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.DevicePort added for object /org/pulseaudio/core1/source1/port2
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.DevicePort added for object /org/pulseaudio/core1/source1/port3
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.DevicePort added for object /org/pulseaudio/core1/source1/port4
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Device added for object /org/pulseaudio/core1/source1
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Source added for object /org/pulseaudio/core1/source1
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Module added for object /org/pulseaudio/core1/module0
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Module added for object /org/pulseaudio/core1/module1
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Module added for object /org/pulseaudio/core1/module2
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Module added for object /org/pulseaudio/core1/module3
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Module added for object /org/pulseaudio/core1/module4
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Module added for object /org/pulseaudio/core1/module5
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Module added for object /org/pulseaudio/core1/module6
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Module added for object /org/pulseaudio/core1/module7
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Module added for object /org/pulseaudio/core1/module8
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Module added for object /org/pulseaudio/core1/module9
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Module added for object /org/pulseaudio/core1/module10
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Module added for object /org/pulseaudio/core1/module11
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Module added for object /org/pulseaudio/core1/module12
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Module added for object /org/pulseaudio/core1/module13
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Module added for object /org/pulseaudio/core1/module14
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Module added for object /org/pulseaudio/core1/module15
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Module added for object /org/pulseaudio/core1/module16
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Client added for object /org/pulseaudio/core1/client0
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1 added for object /org/pulseaudio/core1
I: [pulseaudio] module.c: Loaded "module-dbus-protocol" (index: #17; argument: "").
I: [pulseaudio] module.c: Loaded "module-switch-on-port-available" (index: #18; argument: "").
D: [pulseaudio] main.c: Got org.PulseAudio1!
D: [pulseaudio] main.c: Got org.pulseaudio.Server!
I: [pulseaudio] main.c: Daemon startup complete.
D: [pulseaudio] module-console-kit.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
D: [pulseaudio] module-device-restore.c: Database contains invalid data for key: sink:alsa_output.pci-0000_03_0d.0.analog-stereo (probably pre-v1.0 data)
D: [pulseaudio] module-device-restore.c: Attempting to load legacy (pre-v1.0) data for key: sink:alsa_output.pci-0000_03_0d.0.analog-stereo
D: [pulseaudio] module-device-restore.c: Size does not match.
D: [pulseaudio] module-device-restore.c: Unable to load legacy (pre-v1.0) data for key: sink:alsa_output.pci-0000_03_0d.0.analog-stereo. Ignoring.
D: [pulseaudio] module-device-restore.c: Database contains invalid data for key: sink:alsa_output.pci-0000_03_0d.0.analog-stereo:null
I: [pulseaudio] module-device-restore.c: Storing port for device sink:alsa_output.pci-0000_03_0d.0.analog-stereo.
I: [pulseaudio] module-device-restore.c: Storing volume/mute for device+port sink:alsa_output.pci-0000_03_0d.0.analog-stereo:analog-output;output-amplifier-on.
D: [pulseaudio] module-device-restore.c: Database contains invalid data for key: source:alsa_output.pci-0000_03_0d.0.analog-stereo.monitor (probably pre-v1.0 data)
D: [pulseaudio] module-device-restore.c: Attempting to load legacy (pre-v1.0) data for key: source:alsa_output.pci-0000_03_0d.0.analog-stereo.monitor
D: [pulseaudio] module-device-restore.c: Size does not match.
D: [pulseaudio] module-device-restore.c: Unable to load legacy (pre-v1.0) data for key: source:alsa_output.pci-0000_03_0d.0.analog-stereo.monitor. Ignoring.
D: [pulseaudio] module-device-restore.c: Database contains invalid data for key: source:alsa_output.pci-0000_03_0d.0.analog-stereo.monitor:null
I: [pulseaudio] module-device-restore.c: Storing port for device source:alsa_output.pci-0000_03_0d.0.analog-stereo.monitor.
I: [pulseaudio] module-device-restore.c: Storing volume/mute for device+port source:alsa_output.pci-0000_03_0d.0.analog-stereo.monitor:null.
D: [pulseaudio] module-device-restore.c: Database contains invalid data for key: source:alsa_input.pci-0000_03_0d.0.analog-stereo (probably pre-v1.0 data)
D: [pulseaudio] module-device-restore.c: Attempting to load legacy (pre-v1.0) data for key: source:alsa_input.pci-0000_03_0d.0.analog-stereo
D: [pulseaudio] module-device-restore.c: Size does not match.
D: [pulseaudio] module-device-restore.c: Unable to load legacy (pre-v1.0) data for key: source:alsa_input.pci-0000_03_0d.0.analog-stereo. Ignoring.
D: [pulseaudio] module-device-restore.c: Database contains invalid data for key: source:alsa_input.pci-0000_03_0d.0.analog-stereo:null
I: [pulseaudio] module-device-restore.c: Storing port for device source:alsa_input.pci-0000_03_0d.0.analog-stereo.
I: [pulseaudio] module-device-restore.c: Storing volume/mute for device+port source:alsa_input.pci-0000_03_0d.0.analog-stereo:analog-input-microphone;input-microphone-1.
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Module added for object /org/pulseaudio/core1/module17
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Module added for object /org/pulseaudio/core1/module18
D: [pulseaudio] module-udev-detect.c: /dev/snd/controlC0 is accessible: yes
I: [pulseaudio] module-suspend-on-idle.c: Source alsa_input.pci-0000_03_0d.0.analog-stereo idle for too long, suspending ...
D: [pulseaudio] source.c: Suspend cause of source alsa_input.pci-0000_03_0d.0.analog-stereo is 0x0004, suspending
I: [alsa-source] alsa-source.c: Device suspended...
D: [pulseaudio] core.c: Hmm, no streams around, trying to vacuum.
I: [pulseaudio] module-suspend-on-idle.c: Sink alsa_output.pci-0000_03_0d.0.analog-stereo idle for too long, suspending ...
D: [pulseaudio] sink.c: Suspend cause of sink alsa_output.pci-0000_03_0d.0.analog-stereo is 0x0004, suspending
I: [alsa-sink] alsa-sink.c: Device suspended...
D: [pulseaudio] core.c: Hmm, no streams around, trying to vacuum.
D: [pulseaudio] reserve-wrap.c: Device lock status of reserve-monitor-wrapper@Audio0 changed: not busy
D: [pulseaudio] module-udev-detect.c: /dev/snd/controlC0 is accessible: yes
I: [pulseaudio] module-device-restore.c: Synced.
I: [pulseaudio] client.c: Created 1 "Native client (UNIX socket client)"
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Client added for object /org/pulseaudio/core1/client1
I: [pulseaudio] client.c: Freed 1 "Native client (UNIX socket client)"
I: [pulseaudio] protocol-native.c: Connection died.
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Client removed from object /org/pulseaudio/core1/client1
I: [pulseaudio] client.c: Created 2 "Native client (UNIX socket client)"
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Client added for object /org/pulseaudio/core1/client2
D: [pulseaudio] protocol-native.c: Protocol version: remote 24, local 24
I: [pulseaudio] protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
D: [pulseaudio] protocol-native.c: SHM possible: yes
D: [pulseaudio] protocol-native.c: Negotiated SHM: yes
D: [pulseaudio] module-augment-properties.c: Looking for .desktop file for plugin-container
D: [pulseaudio] module-stream-restore.c: Database contains invalid data for key: sink-input-by-application-name:ALSA plug-in [plugin-container] (probably pre-v1.0 data)
D: [pulseaudio] module-stream-restore.c: Attempting to load legacy (pre-v1.0) data for key: sink-input-by-application-name:ALSA plug-in [plugin-container]
D: [pulseaudio] module-stream-restore.c: Size does not match.
D: [pulseaudio] module-stream-restore.c: Unable to load legacy (pre-v1.0) data for key: sink-input-by-application-name:ALSA plug-in [plugin-container]. Ignoring.
D: [pulseaudio] module-intended-roles.c: Not setting device for stream ALSA Playback, because it lacks role.
D: [pulseaudio] module-stream-restore.c: Database contains invalid data for key: sink-input-by-application-name:ALSA plug-in [plugin-container] (probably pre-v1.0 data)
D: [pulseaudio] module-stream-restore.c: Attempting to load legacy (pre-v1.0) data for key: sink-input-by-application-name:ALSA plug-in [plugin-container]
D: [pulseaudio] module-stream-restore.c: Size does not match.
D: [pulseaudio] module-stream-restore.c: Unable to load legacy (pre-v1.0) data for key: sink-input-by-application-name:ALSA plug-in [plugin-container]. Ignoring.
D: [pulseaudio] sink.c: Suspend cause of sink alsa_output.pci-0000_03_0d.0.analog-stereo is 0x0000, resuming
D: [pulseaudio] reserve-wrap.c: Successfully acquired reservation lock on device 'Audio0'
I: [alsa-sink] alsa-sink.c: Trying resume...
I: [alsa-sink] alsa-util.c: cannot disable ALSA period wakeups
D: [alsa-sink] alsa-util.c: Maximum hw buffer size is 371 ms
D: [alsa-sink] alsa-util.c: Set buffer size first (to 16384 samples), period size second (to 16384 samples).
I: [alsa-sink] alsa-util.c: ALSA period wakeups were not disabled
D: [alsa-sink] alsa-sink.c: hwbuf_unused=0
D: [alsa-sink] alsa-sink.c: setting avail_min=15502
I: [alsa-sink] alsa-sink.c: Resumed successfully...
I: [alsa-sink] alsa-sink.c: Starting playback.
D: [alsa-sink] alsa-sink.c: Cutting sleep time for the initial iterations by half.
D: [alsa-sink] alsa-sink.c: Cutting sleep time for the initial iterations by half.
D: [pulseaudio] module-suspend-on-idle.c: Sink alsa_output.pci-0000_03_0d.0.analog-stereo becomes idle, timeout in 5 seconds.
D: [alsa-sink] alsa-sink.c: Cutting sleep time for the initial iterations by half.
D: [alsa-sink] alsa-sink.c: Cutting sleep time for the initial iterations by half.
D: [pulseaudio] module-suspend-on-idle.c: Sink alsa_output.pci-0000_03_0d.0.analog-stereo becomes busy.
D: [pulseaudio] memblockq.c: memblockq requested: maxlength=33554432, tlength=0, base=4, prebuf=0, minreq=1 maxrewind=0
D: [pulseaudio] memblockq.c: memblockq sanitized: maxlength=33554432, tlength=33554432, base=4, prebuf=0, minreq=4 maxrewind=0
I: [pulseaudio] sink-input.c: Created input 0 "ALSA Playback" on alsa_output.pci-0000_03_0d.0.analog-stereo with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: [pulseaudio] sink-input.c:     media.name = "ALSA Playback"
I: [pulseaudio] sink-input.c:     application.name = "ALSA plug-in [plugin-container]"
I: [pulseaudio] sink-input.c:     native-protocol.peer = "UNIX socket client"
I: [pulseaudio] sink-input.c:     native-protocol.version = "24"
I: [pulseaudio] sink-input.c:     application.process.id = "1841"
I: [pulseaudio] sink-input.c:     application.process.user = "isabel"
I: [pulseaudio] sink-input.c:     application.process.host = "Ferynia"
I: [pulseaudio] sink-input.c:     application.process.binary = "plugin-container"
I: [pulseaudio] sink-input.c:     window.x11.display = ":0.0"
I: [pulseaudio] sink-input.c:     application.language = "en_US.UTF-8"
I: [pulseaudio] sink-input.c:     application.process.machine_id = "6c3707d606b7dc3ec5d9457000000008"
I: [pulseaudio] sink-input.c:     application.process.session_id = "6c3707d606b7dc3ec5d9457000000008-1325703628.691010-1990453158"
I: [pulseaudio] sink-input.c:     module-stream-restore.id = "sink-input-by-application-name:ALSA plug-in [plugin-container]"
I: [pulseaudio] protocol-native.c: Requested tlength=500.00 ms, minreq=20.00 ms
D: [pulseaudio] protocol-native.c: Early requests mode enabled, configuring sink latency to minreq.
D: [alsa-sink] alsa-sink.c: Cutting sleep time for the initial iterations by half.
D: [alsa-sink] alsa-sink.c: Cutting sleep time for the initial iterations by half.
D: [pulseaudio] memblockq.c: memblockq requested: maxlength=4194304, tlength=88200, base=4, prebuf=84672, minreq=3528 maxrewind=0
D: [pulseaudio] memblockq.c: memblockq sanitized: maxlength=4194304, tlength=88200, base=4, prebuf=84672, minreq=3528 maxrewind=0
I: [pulseaudio] protocol-native.c: Final latency 520.00 ms = 460.00 ms + 2*20.00 ms + 20.00 ms
D: [alsa-sink] alsa-sink.c: Cutting sleep time for the initial iterations by half.
D: [alsa-sink] alsa-sink.c: Latency set to 20.00ms
D: [alsa-sink] alsa-sink.c: hwbuf_unused=62008
D: [alsa-sink] alsa-sink.c: setting avail_min=15944
D: [alsa-sink] alsa-sink.c: Requesting rewind due to latency change.
D: [alsa-sink] alsa-sink.c: Requested volume: 0:  54% 1:  54%
D: [alsa-sink] alsa-sink.c:            in dB: 0: -16.00 dB 1: -16.00 dB
D: [alsa-sink] alsa-sink.c: Got hardware volume: 0:  54% 1:  54%
D: [alsa-sink] alsa-sink.c:               in dB: 0: -16.00 dB 1: -16.00 dB
D: [alsa-sink] alsa-sink.c: Calculated software volume: 0: 100% 1: 100% (accurate-enough=yes)
D: [alsa-sink] alsa-sink.c:                      in dB: 0: 0.00 dB 1: 0.00 dB
D: [alsa-sink] sink.c: Volume not changing
D: [alsa-sink] alsa-sink.c: Requested to rewind 65536 bytes.
D: [alsa-sink] alsa-sink.c: Limited to 64888 bytes.
D: [alsa-sink] alsa-sink.c: before: 16222
D: [alsa-sink] alsa-sink.c: after: 16222
D: [alsa-sink] alsa-sink.c: Rewound 64888 bytes.
D: [alsa-sink] sink.c: Processing rewind...
D: [alsa-sink] sink.c: latency = 1331
D: [alsa-sink] sink-input.c: Have to rewind 64888 bytes on render memblockq.
D: [alsa-sink] source.c: Processing rewind...
D: [pulseaudio] core-subscribe.c: Dropped redundant event due to change event.
D: [pulseaudio] reserve-wrap.c: Device lock status of reserve-monitor-wrapper@Audio0 changed: not busy
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Stream added for object /org/pulseaudio/core1/playback_stream0
D: [pulseaudio] module-stream-restore.c: Database contains invalid data for key: sink-input-by-application-name:ALSA plug-in [plugin-container] (probably pre-v1.0 data)
D: [pulseaudio] module-stream-restore.c: Attempting to load legacy (pre-v1.0) data for key: sink-input-by-application-name:ALSA plug-in [plugin-container]
D: [pulseaudio] module-stream-restore.c: Size does not match.
D: [pulseaudio] module-stream-restore.c: Unable to load legacy (pre-v1.0) data for key: sink-input-by-application-name:ALSA plug-in [plugin-container]. Ignoring.
I: [pulseaudio] module-stream-restore.c: Storing volume/mute/device for stream sink-input-by-application-name:ALSA plug-in [plugin-container].
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry added for object /org/pulseaudio/stream_restore1/entry0
D: [alsa-sink] protocol-native.c: Requesting rewind due to end of underrun.
D: [alsa-sink] alsa-sink.c: Requested to rewind 65536 bytes.
D: [alsa-sink] alsa-sink.c: Limited to 2756 bytes.
D: [alsa-sink] alsa-sink.c: before: 689
D: [alsa-sink] alsa-sink.c: after: 689
D: [alsa-sink] alsa-sink.c: Rewound 2756 bytes.
D: [alsa-sink] sink.c: Processing rewind...
D: [alsa-sink] sink.c: latency = 1332
D: [alsa-sink] sink-input.c: Have to rewind 2756 bytes on render memblockq.
D: [alsa-sink] source.c: Processing rewind...
D: [alsa-sink] protocol-native.c: Underrun on 'ALSA Playback', 0 bytes in queue.
D: [alsa-sink] protocol-native.c: Requesting rewind due to end of underrun.
D: [alsa-sink] alsa-sink.c: Requested to rewind 1912 bytes.
D: [alsa-sink] alsa-sink.c: Limited to 1912 bytes.
D: [alsa-sink] alsa-sink.c: before: 478
D: [alsa-sink] alsa-sink.c: after: 478
D: [alsa-sink] alsa-sink.c: Rewound 1912 bytes.
D: [alsa-sink] sink.c: Processing rewind...
D: [alsa-sink] sink.c: latency = 4633
D: [alsa-sink] sink-input.c: Have to rewind 1912 bytes on render memblockq.
D: [alsa-sink] source.c: Processing rewind...
I: [pulseaudio] module-stream-restore.c: Synced.
D: [alsa-sink] sink-input.c: Requesting rewind due to corking
D: [alsa-sink] alsa-sink.c: Requested to rewind 65536 bytes.
D: [alsa-sink] alsa-sink.c: Limited to 3132 bytes.
D: [alsa-sink] alsa-sink.c: before: 783
D: [alsa-sink] alsa-sink.c: after: 783
D: [alsa-sink] alsa-sink.c: Rewound 3132 bytes.
D: [alsa-sink] sink.c: Processing rewind...
D: [alsa-sink] sink.c: latency = 1314
D: [alsa-sink] sink-input.c: Have to rewind 3132 bytes on render memblockq.
D: [alsa-sink] sink-input.c: Have to rewind 3132 bytes on implementor.
D: [alsa-sink] source.c: Processing rewind...
D: [pulseaudio] module-suspend-on-idle.c: Sink alsa_output.pci-0000_03_0d.0.analog-stereo becomes idle, timeout in 5 seconds.
D: [alsa-sink] alsa-sink.c: hwbuf_unused=0
D: [alsa-sink] alsa-sink.c: setting avail_min=15943
D: [alsa-sink] alsa-sink.c: Requested volume: 0:  54% 1:  54%
D: [alsa-sink] alsa-sink.c:            in dB: 0: -16.00 dB 1: -16.00 dB
D: [alsa-sink] alsa-sink.c: Got hardware volume: 0:  54% 1:  54%
D: [alsa-sink] alsa-sink.c:               in dB: 0: -16.00 dB 1: -16.00 dB
D: [alsa-sink] alsa-sink.c: Calculated software volume: 0: 100% 1: 100% (accurate-enough=yes)
D: [alsa-sink] alsa-sink.c:                      in dB: 0: 0.00 dB 1: 0.00 dB
D: [alsa-sink] sink.c: Volume not changing
D: [alsa-sink] alsa-sink.c: Requested to rewind 65536 bytes.
D: [alsa-sink] alsa-sink.c: Limited to 2480 bytes.
D: [alsa-sink] alsa-sink.c: before: 620
D: [alsa-sink] alsa-sink.c: after: 620
D: [alsa-sink] alsa-sink.c: Rewound 2480 bytes.
D: [alsa-sink] sink.c: Processing rewind...
D: [alsa-sink] sink.c: latency = 1284
D: [alsa-sink] source.c: Processing rewind...
D: [pulseaudio] module-suspend-on-idle.c: Sink alsa_output.pci-0000_03_0d.0.analog-stereo becomes idle, timeout in 5 seconds.
D: [pulseaudio] core.c: Hmm, no streams around, trying to vacuum.
I: [pulseaudio] client.c: Freed 2 "ALSA plug-in [plugin-container]"
I: [pulseaudio] protocol-native.c: Connection died.
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Stream removed from object /org/pulseaudio/core1/playback_stream0
I: [pulseaudio] sink-input.c: Freeing input 0 "ALSA Playback"
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Client removed from object /org/pulseaudio/core1/client2
D: [pulseaudio] flist.c: pulsecore/hashmap.c: entries flist is full (don't worry)
D: [pulseaudio] flist.c: pulsecore/hashmap.c: entries flist is full (don't worry)
D: [pulseaudio] flist.c: pulsecore/hashmap.c: entries flist is full (don't worry)
D: [pulseaudio] flist.c: pulsecore/hashmap.c: entries flist is full (don't worry)
D: [pulseaudio] flist.c: pulsecore/hashmap.c: entries flist is full (don't worry)
D: [pulseaudio] flist.c: pulsecore/hashmap.c: entries flist is full (don't worry)
I: [pulseaudio] module-suspend-on-idle.c: Sink alsa_output.pci-0000_03_0d.0.analog-stereo idle for too long, suspending ...
D: [pulseaudio] sink.c: Suspend cause of sink alsa_output.pci-0000_03_0d.0.analog-stereo is 0x0004, suspending
D: [pulseaudio] flist.c: pulsecore/hashmap.c: entries flist is full (don't worry)
I: [alsa-sink] alsa-sink.c: Device suspended...
D: [pulseaudio] core.c: Hmm, no streams around, trying to vacuum.
D: [pulseaudio] reserve-wrap.c: Device lock status of reserve-monitor-wrapper@Audio0 changed: not busy
D: [pulseaudio] module-udev-detect.c: /dev/snd/controlC0 is accessible: yes
I: [pulseaudio] client.c: Created 3 "Native client (UNIX socket client)"
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Client added for object /org/pulseaudio/core1/client3
D: [pulseaudio] protocol-native.c: Protocol version: remote 24, local 24
I: [pulseaudio] protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
D: [pulseaudio] protocol-native.c: SHM possible: yes
D: [pulseaudio] protocol-native.c: Negotiated SHM: yes
D: [pulseaudio] module-augment-properties.c: Looking for .desktop file for skype
D: [pulseaudio] module-augment-properties.c: Found /usr/share/applications/skype.desktop.
D: [pulseaudio] module-stream-restore.c: Database contains invalid data for key: sink-input-by-media-role:event (probably pre-v1.0 data)
D: [pulseaudio] module-stream-restore.c: Attempting to load legacy (pre-v1.0) data for key: sink-input-by-media-role:event
D: [pulseaudio] module-stream-restore.c: Size does not match.
D: [pulseaudio] module-stream-restore.c: Unable to load legacy (pre-v1.0) data for key: sink-input-by-media-role:event. Ignoring.
D: [pulseaudio] module-stream-restore.c: Database contains invalid data for key: sink-input-by-media-role:event (probably pre-v1.0 data)
D: [pulseaudio] module-stream-restore.c: Attempting to load legacy (pre-v1.0) data for key: sink-input-by-media-role:event
D: [pulseaudio] module-stream-restore.c: Size does not match.
D: [pulseaudio] module-stream-restore.c: Unable to load legacy (pre-v1.0) data for key: sink-input-by-media-role:event. Ignoring.
D: [pulseaudio] sink.c: Suspend cause of sink alsa_output.pci-0000_03_0d.0.analog-stereo is 0x0000, resuming
D: [pulseaudio] reserve-wrap.c: Successfully acquired reservation lock on device 'Audio0'
I: [alsa-sink] alsa-sink.c: Trying resume...
I: [alsa-sink] alsa-util.c: cannot disable ALSA period wakeups
D: [alsa-sink] alsa-util.c: Maximum hw buffer size is 371 ms
D: [alsa-sink] alsa-util.c: Set buffer size first (to 16384 samples), period size second (to 16384 samples).
I: [alsa-sink] alsa-util.c: ALSA period wakeups were not disabled
D: [alsa-sink] alsa-sink.c: hwbuf_unused=0
D: [alsa-sink] alsa-sink.c: setting avail_min=15943
I: [alsa-sink] alsa-sink.c: Resumed successfully...
D: [pulseaudio] module-suspend-on-idle.c: Sink alsa_output.pci-0000_03_0d.0.analog-stereo becomes idle, timeout in 5 seconds.
I: [alsa-sink] alsa-sink.c: Starting playback.
D: [alsa-sink] alsa-sink.c: Cutting sleep time for the initial iterations by half.
D: [alsa-sink] alsa-sink.c: Cutting sleep time for the initial iterations by half.
D: [pulseaudio] module-suspend-on-idle.c: Sink alsa_output.pci-0000_03_0d.0.analog-stereo becomes busy.
D: [alsa-sink] alsa-sink.c: Cutting sleep time for the initial iterations by half.
D: [pulseaudio] resampler.c: Channel matrix:
D: [pulseaudio] resampler.c:        I00 
D: [pulseaudio] resampler.c:     +------
D: [pulseaudio] resampler.c: O00 | 1.000
D: [pulseaudio] resampler.c: O01 | 1.000
I: [pulseaudio] remap_sse.c: Using SSE mono to stereo remapping
I: [pulseaudio] resampler.c: Using resampler 'speex-float-1'
I: [pulseaudio] resampler.c: Using float32le as working format.
I: [pulseaudio] resampler.c: Choosing speex quality setting 1.
D: [pulseaudio] memblockq.c: memblockq requested: maxlength=33554432, tlength=0, base=4, prebuf=0, minreq=1 maxrewind=0
D: [pulseaudio] memblockq.c: memblockq sanitized: maxlength=33554432, tlength=33554432, base=4, prebuf=0, minreq=4 maxrewind=0
I: [pulseaudio] sink-input.c: Created input 1 "Event Sound" on alsa_output.pci-0000_03_0d.0.analog-stereo with sample spec s16le 1ch 48000Hz and channel map mono
I: [pulseaudio] sink-input.c:     window.icon_name = "skype"
I: [pulseaudio] sink-input.c:     application.icon_name = "skype"
I: [pulseaudio] sink-input.c:     media.role = "event"
I: [pulseaudio] sink-input.c:     media.name = "Event Sound"
I: [pulseaudio] sink-input.c:     application.name = "Skype"
I: [pulseaudio] sink-input.c:     native-protocol.peer = "UNIX socket client"
I: [pulseaudio] sink-input.c:     native-protocol.version = "24"
I: [pulseaudio] sink-input.c:     application.process.id = "1862"
I: [pulseaudio] sink-input.c:     application.process.user = "isabel"
I: [pulseaudio] sink-input.c:     application.process.host = "Ferynia"
I: [pulseaudio] sink-input.c:     application.process.binary = "skype"
I: [pulseaudio] sink-input.c:     window.x11.display = ":0.0"
I: [pulseaudio] sink-input.c:     application.language = "en_US.UTF-8"
I: [pulseaudio] sink-input.c:     application.process.machine_id = "6c3707d606b7dc3ec5d9457000000008"
I: [pulseaudio] sink-input.c:     application.process.session_id = "6c3707d606b7dc3ec5d9457000000008-1325703628.691010-1990453158"
I: [pulseaudio] sink-input.c:     module-stream-restore.id = "sink-input-by-media-role:event"
I: [pulseaudio] protocol-native.c: Requested tlength=20.02 ms, minreq=20.00 ms
D: [pulseaudio] protocol-native.c: Adjust latency mode enabled, configuring sink latency to half of overall latency.
D: [alsa-sink] alsa-sink.c: Cutting sleep time for the initial iterations by half.
D: [alsa-sink] alsa-sink.c: Cutting sleep time for the initial iterations by half.
D: [pulseaudio] memblockq.c: memblockq requested: maxlength=4194304, tlength=3888, base=2, prebuf=1970, minreq=1920 maxrewind=0
D: [pulseaudio] memblockq.c: memblockq sanitized: maxlength=4194304, tlength=3888, base=2, prebuf=1970, minreq=1920 maxrewind=0
I: [pulseaudio] protocol-native.c: Final latency 41.00 ms = 0.50 ms + 2*20.00 ms + 0.50 ms
D: [alsa-sink] alsa-sink.c: Cutting sleep time for the initial iterations by half.
D: [alsa-sink] alsa-sink.c: Latency set to 0.50ms
D: [alsa-sink] alsa-sink.c: hwbuf_unused=65448
D: [alsa-sink] alsa-sink.c: setting avail_min=16374
D: [alsa-sink] alsa-sink.c: Requesting rewind due to latency change.
D: [alsa-sink] alsa-sink.c: Requested volume: 0:  54% 1:  54%
D: [alsa-sink] alsa-sink.c:            in dB: 0: -16.00 dB 1: -16.00 dB
D: [alsa-sink] alsa-sink.c: Got hardware volume: 0:  54% 1:  54%
D: [alsa-sink] alsa-sink.c:               in dB: 0: -16.00 dB 1: -16.00 dB
D: [alsa-sink] alsa-sink.c: Calculated software volume: 0: 100% 1: 100% (accurate-enough=yes)
D: [alsa-sink] alsa-sink.c:                      in dB: 0: 0.00 dB 1: 0.00 dB
D: [alsa-sink] sink.c: Volume not changing
D: [alsa-sink] alsa-sink.c: Requested to rewind 65536 bytes.
D: [alsa-sink] alsa-sink.c: Limited to 64924 bytes.
D: [alsa-sink] alsa-sink.c: before: 16231
D: [alsa-sink] alsa-sink.c: after: 16231
D: [alsa-sink] alsa-sink.c: Rewound 64924 bytes.
D: [alsa-sink] sink.c: Processing rewind...
D: [alsa-sink] sink.c: latency = 1278
D: [alsa-sink] sink-input.c: Have to rewind 64924 bytes on render memblockq.
D: [alsa-sink] source.c: Processing rewind...
D: [alsa-sink] alsa-sink.c: Cutting sleep time for the initial iterations by half.
D: [alsa-sink] alsa-sink.c: Cutting sleep time for the initial iterations by half.
D: [pulseaudio] reserve-wrap.c: Device lock status of reserve-monitor-wrapper@Audio0 changed: not busy
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Stream added for object /org/pulseaudio/core1/playback_stream1
D: [pulseaudio] module-stream-restore.c: Database contains invalid data for key: sink-input-by-media-role:event (probably pre-v1.0 data)
D: [pulseaudio] module-stream-restore.c: Attempting to load legacy (pre-v1.0) data for key: sink-input-by-media-role:event
D: [pulseaudio] module-stream-restore.c: Size does not match.
D: [pulseaudio] module-stream-restore.c: Unable to load legacy (pre-v1.0) data for key: sink-input-by-media-role:event. Ignoring.
I: [pulseaudio] module-stream-restore.c: Storing volume/mute/device for stream sink-input-by-media-role:event.
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry added for object /org/pulseaudio/stream_restore1/entry1
D: [alsa-sink] sink-input.c: Requesting rewind due to uncorking
D: [alsa-sink] alsa-sink.c: Requested to rewind 65536 bytes.
D: [alsa-sink] alsa-sink.c: Mhmm, actually there is nothing to rewind.
D: [pulseaudio] module-suspend-on-idle.c: Sink alsa_output.pci-0000_03_0d.0.analog-stereo becomes busy.
D: [alsa-sink] protocol-native.c: Requesting rewind due to end of underrun.
D: [alsa-sink] alsa-sink.c: Requested to rewind 65536 bytes.
D: [alsa-sink] alsa-sink.c: Mhmm, actually there is nothing to rewind.
D: [alsa-sink] memblock.c: Pool full
D: [alsa-sink] memblock.c: Pool full
D: [alsa-sink] memblock.c: Pool full
D: [alsa-sink] sink-input.c: Requesting rewind due to corking
D: [alsa-sink] alsa-sink.c: Requested to rewind 65536 bytes.
D: [alsa-sink] alsa-sink.c: Mhmm, actually there is nothing to rewind.
D: [pulseaudio] module-suspend-on-idle.c: Sink alsa_output.pci-0000_03_0d.0.analog-stereo becomes idle, timeout in 5 seconds.
D: [alsa-sink] alsa-sink.c: hwbuf_unused=0
D: [alsa-sink] alsa-sink.c: setting avail_min=16209
D: [alsa-sink] alsa-sink.c: Requested volume: 0:  54% 1:  54%
D: [alsa-sink] alsa-sink.c:            in dB: 0: -16.00 dB 1: -16.00 dB
D: [alsa-sink] alsa-sink.c: Got hardware volume: 0:  54% 1:  54%
D: [alsa-sink] alsa-sink.c:               in dB: 0: -16.00 dB 1: -16.00 dB
D: [alsa-sink] alsa-sink.c: Calculated software volume: 0: 100% 1: 100% (accurate-enough=yes)
D: [alsa-sink] alsa-sink.c:                      in dB: 0: 0.00 dB 1: 0.00 dB
D: [alsa-sink] sink.c: Volume not changing
D: [alsa-sink] alsa-sink.c: Requested to rewind 65536 bytes.
D: [alsa-sink] alsa-sink.c: Mhmm, actually there is nothing to rewind.
D: [pulseaudio] module-suspend-on-idle.c: Sink alsa_output.pci-0000_03_0d.0.analog-stereo becomes idle, timeout in 5 seconds.
D: [pulseaudio] core.c: Hmm, no streams around, trying to vacuum.
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Stream removed from object /org/pulseaudio/core1/playback_stream1
I: [pulseaudio] sink-input.c: Freeing input 1 "Event Sound"
D: [pulseaudio] module-stream-restore.c: Database contains invalid data for key: source-output-by-media-role:phone (probably pre-v1.0 data)
D: [pulseaudio] module-stream-restore.c: Attempting to load legacy (pre-v1.0) data for key: source-output-by-media-role:phone
D: [pulseaudio] module-stream-restore.c: Size does not match.
D: [pulseaudio] module-stream-restore.c: Unable to load legacy (pre-v1.0) data for key: source-output-by-media-role:phone. Ignoring.
D: [pulseaudio] module-stream-restore.c: Database contains invalid data for key: source-output-by-media-role:phone (probably pre-v1.0 data)
D: [pulseaudio] module-stream-restore.c: Attempting to load legacy (pre-v1.0) data for key: source-output-by-media-role:phone
D: [pulseaudio] module-stream-restore.c: Size does not match.
D: [pulseaudio] module-stream-restore.c: Unable to load legacy (pre-v1.0) data for key: source-output-by-media-role:phone. Ignoring.
D: [pulseaudio] source.c: Suspend cause of source alsa_input.pci-0000_03_0d.0.analog-stereo is 0x0000, resuming
I: [alsa-source] alsa-source.c: Trying resume...
I: [alsa-source] alsa-util.c: cannot disable ALSA period wakeups
D: [alsa-source] alsa-util.c: Maximum hw buffer size is 371 ms
D: [alsa-source] alsa-util.c: Set buffer size first (to 16384 samples), period size second (to 8192 samples).
I: [alsa-source] alsa-util.c: ALSA period wakeups were not disabled
D: [alsa-source] alsa-source.c: hwbuf_unused=0
D: [alsa-source] alsa-source.c: setting avail_min=15502
I: [alsa-source] alsa-source.c: Resumed successfully...
I: [alsa-source] alsa-source.c: Starting capture.
D: [pulseaudio] module-suspend-on-idle.c: Source alsa_input.pci-0000_03_0d.0.analog-stereo becomes idle, timeout in 5 seconds.
D: [pulseaudio] module-suspend-on-idle.c: Source alsa_input.pci-0000_03_0d.0.analog-stereo becomes busy.
D: [pulseaudio] resampler.c: Channel matrix:
D: [pulseaudio] resampler.c:        I00   I01 
D: [pulseaudio] resampler.c:     +------------
D: [pulseaudio] resampler.c: O00 | 1.000 1.000
I: [pulseaudio] remap.c: Using generic matrix remapping
I: [pulseaudio] resampler.c: Using resampler 'speex-float-1'
I: [pulseaudio] resampler.c: Using float32le as working format.
I: [pulseaudio] resampler.c: Choosing speex quality setting 1.
D: [pulseaudio] memblockq.c: memblockq requested: maxlength=33554432, tlength=0, base=4, prebuf=0, minreq=1 maxrewind=0
D: [pulseaudio] memblockq.c: memblockq sanitized: maxlength=33554432, tlength=33554432, base=4, prebuf=0, minreq=4 maxrewind=0
I: [pulseaudio] source-output.c: Created output 0 "Input" on alsa_input.pci-0000_03_0d.0.analog-stereo with sample spec s16le 1ch 48000Hz and channel map mono
I: [pulseaudio] source-output.c:     window.icon_name = "skype"
I: [pulseaudio] source-output.c:     application.icon_name = "skype"
I: [pulseaudio] source-output.c:     media.role = "phone"
I: [pulseaudio] source-output.c:     media.name = "Input"
I: [pulseaudio] source-output.c:     application.name = "Skype"
I: [pulseaudio] source-output.c:     native-protocol.peer = "UNIX socket client"
I: [pulseaudio] source-output.c:     native-protocol.version = "24"
I: [pulseaudio] source-output.c:     application.process.id = "1862"
I: [pulseaudio] source-output.c:     application.process.user = "isabel"
I: [pulseaudio] source-output.c:     application.process.host = "Ferynia"
I: [pulseaudio] source-output.c:     application.process.binary = "skype"
I: [pulseaudio] source-output.c:     window.x11.display = ":0.0"
I: [pulseaudio] source-output.c:     application.language = "en_US.UTF-8"
I: [pulseaudio] source-output.c:     application.process.machine_id = "6c3707d606b7dc3ec5d9457000000008"
I: [pulseaudio] source-output.c:     application.process.session_id = "6c3707d606b7dc3ec5d9457000000008-1325703628.691010-1990453158"
I: [pulseaudio] source-output.c:     module-stream-restore.id = "source-output-by-media-role:phone"
D: [pulseaudio] memblockq.c: memblockq requested: maxlength=4194304, tlength=0, base=2, prebuf=1, minreq=0 maxrewind=0
D: [pulseaudio] memblockq.c: memblockq sanitized: maxlength=4194304, tlength=4194304, base=2, prebuf=2, minreq=2 maxrewind=0
I: [pulseaudio] protocol-native.c: Final latency 10.00 ms = 5.00 ms + 5.00 ms
D: [alsa-source] alsa-source.c: latency set to 5.00ms
D: [alsa-source] alsa-source.c: hwbuf_unused=64656
D: [alsa-source] alsa-source.c: setting avail_min=111
D: [alsa-source] alsa-source.c: latency set to 5.00ms
D: [alsa-source] alsa-source.c: hwbuf_unused=64656
D: [alsa-source] alsa-source.c: setting avail_min=111
D: [alsa-source] alsa-source.c: Requested volume: 0: 100% 1: 100%
D: [alsa-source] alsa-source.c:            in dB: 0: 0.00 dB 1: 0.00 dB
D: [alsa-source] alsa-source.c: Got hardware volume: 0: 100% 1: 100%
D: [alsa-source] alsa-source.c:               in dB: 0: 0.00 dB 1: 0.00 dB
D: [alsa-source] alsa-source.c: Calculated software volume: 0: 100% 1: 100% (accurate-enough=yes)
D: [alsa-source] alsa-source.c:                      in dB: 0: 0.00 dB 1: 0.00 dB
D: [alsa-source] source.c: Volume not changing
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Stream added for object /org/pulseaudio/core1/record_stream0
D: [pulseaudio] module-stream-restore.c: Database contains invalid data for key: source-output-by-media-role:phone (probably pre-v1.0 data)
D: [pulseaudio] module-stream-restore.c: Attempting to load legacy (pre-v1.0) data for key: source-output-by-media-role:phone
D: [pulseaudio] module-stream-restore.c: Size does not match.
D: [pulseaudio] module-stream-restore.c: Unable to load legacy (pre-v1.0) data for key: source-output-by-media-role:phone. Ignoring.
I: [pulseaudio] module-stream-restore.c: Storing volume/mute/device for stream source-output-by-media-role:phone.
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry added for object /org/pulseaudio/stream_restore1/entry2
D: [pulseaudio] module-suspend-on-idle.c: Source alsa_input.pci-0000_03_0d.0.analog-stereo becomes busy.
D: [pulseaudio] module-suspend-on-idle.c: Source alsa_input.pci-0000_03_0d.0.analog-stereo becomes idle, timeout in 5 seconds.
D: [alsa-source] alsa-source.c: hwbuf_unused=0
D: [alsa-source] alsa-source.c: setting avail_min=16209
D: [alsa-source] alsa-source.c: Requested volume: 0: 100% 1: 100%
D: [alsa-source] alsa-source.c:            in dB: 0: 0.00 dB 1: 0.00 dB
D: [alsa-source] alsa-source.c: Got hardware volume: 0: 100% 1: 100%
D: [alsa-source] alsa-source.c:               in dB: 0: 0.00 dB 1: 0.00 dB
D: [alsa-source] alsa-source.c: Calculated software volume: 0: 100% 1: 100% (accurate-enough=yes)
D: [alsa-source] alsa-source.c:                      in dB: 0: 0.00 dB 1: 0.00 dB
D: [alsa-source] source.c: Volume not changing
D: [pulseaudio] module-suspend-on-idle.c: Source alsa_input.pci-0000_03_0d.0.analog-stereo becomes idle, timeout in 5 seconds.
D: [pulseaudio] core.c: Hmm, no streams around, trying to vacuum.
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Stream removed from object /org/pulseaudio/core1/record_stream0
I: [pulseaudio] source-output.c: Freeing output 0 "Input"
D: [pulseaudio] module-stream-restore.c: Database contains invalid data for key: sink-input-by-media-role:phone (probably pre-v1.0 data)
D: [pulseaudio] module-stream-restore.c: Attempting to load legacy (pre-v1.0) data for key: sink-input-by-media-role:phone
D: [pulseaudio] module-stream-restore.c: Size does not match.
D: [pulseaudio] module-stream-restore.c: Unable to load legacy (pre-v1.0) data for key: sink-input-by-media-role:phone. Ignoring.
D: [pulseaudio] module-stream-restore.c: Database contains invalid data for key: sink-input-by-media-role:phone (probably pre-v1.0 data)
D: [pulseaudio] module-stream-restore.c: Attempting to load legacy (pre-v1.0) data for key: sink-input-by-media-role:phone
D: [pulseaudio] module-stream-restore.c: Size does not match.
D: [pulseaudio] module-stream-restore.c: Unable to load legacy (pre-v1.0) data for key: sink-input-by-media-role:phone. Ignoring.
D: [pulseaudio] module-suspend-on-idle.c: Sink alsa_output.pci-0000_03_0d.0.analog-stereo becomes busy.
I: [pulseaudio] resampler.c: Using resampler 'speex-float-1'
I: [pulseaudio] resampler.c: Using float32le as working format.
I: [pulseaudio] resampler.c: Choosing speex quality setting 1.
D: [pulseaudio] memblockq.c: memblockq requested: maxlength=33554432, tlength=0, base=4, prebuf=0, minreq=1 maxrewind=0
D: [pulseaudio] memblockq.c: memblockq sanitized: maxlength=33554432, tlength=33554432, base=4, prebuf=0, minreq=4 maxrewind=0
I: [pulseaudio] sink-input.c: Created input 2 "Output" on alsa_output.pci-0000_03_0d.0.analog-stereo with sample spec s16le 2ch 48000Hz and channel map front-left,front-right
I: [pulseaudio] sink-input.c:     window.icon_name = "skype"
I: [pulseaudio] sink-input.c:     application.icon_name = "skype"
I: [pulseaudio] sink-input.c:     media.role = "phone"
I: [pulseaudio] sink-input.c:     media.name = "Output"
I: [pulseaudio] sink-input.c:     application.name = "Skype"
I: [pulseaudio] sink-input.c:     native-protocol.peer = "UNIX socket client"
I: [pulseaudio] sink-input.c:     native-protocol.version = "24"
I: [pulseaudio] sink-input.c:     application.process.id = "1862"
I: [pulseaudio] sink-input.c:     application.process.user = "isabel"
I: [pulseaudio] sink-input.c:     application.process.host = "Ferynia"
I: [pulseaudio] sink-input.c:     application.process.binary = "skype"
I: [pulseaudio] sink-input.c:     window.x11.display = ":0.0"
I: [pulseaudio] sink-input.c:     application.language = "en_US.UTF-8"
I: [pulseaudio] sink-input.c:     application.process.machine_id = "6c3707d606b7dc3ec5d9457000000008"
I: [pulseaudio] sink-input.c:     application.process.session_id = "6c3707d606b7dc3ec5d9457000000008-1325703628.691010-1990453158"
I: [pulseaudio] sink-input.c:     module-stream-restore.id = "sink-input-by-media-role:phone"
I: [pulseaudio] protocol-native.c: Requested tlength=20.02 ms, minreq=20.00 ms
D: [pulseaudio] protocol-native.c: Adjust latency mode enabled, configuring sink latency to half of overall latency.
D: [pulseaudio] memblockq.c: memblockq requested: maxlength=4194304, tlength=7776, base=4, prebuf=3940, minreq=3840 maxrewind=0
D: [pulseaudio] memblockq.c: memblockq sanitized: maxlength=4194304, tlength=7776, base=4, prebuf=3940, minreq=3840 maxrewind=0
I: [pulseaudio] protocol-native.c: Final latency 41.00 ms = 0.50 ms + 2*20.00 ms + 0.50 ms
D: [alsa-sink] alsa-sink.c: Latency set to 0.50ms
D: [alsa-sink] alsa-sink.c: hwbuf_unused=65448
D: [alsa-sink] alsa-sink.c: setting avail_min=16374
D: [alsa-sink] alsa-sink.c: Requesting rewind due to latency change.
D: [alsa-sink] alsa-sink.c: Requested volume: 0:  54% 1:  54%
D: [alsa-sink] alsa-sink.c:            in dB: 0: -16.00 dB 1: -16.00 dB
D: [alsa-sink] alsa-sink.c: Got hardware volume: 0:  54% 1:  54%
D: [alsa-sink] alsa-sink.c:               in dB: 0: -16.00 dB 1: -16.00 dB
D: [alsa-sink] alsa-sink.c: Calculated software volume: 0: 100% 1: 100% (accurate-enough=yes)
D: [alsa-sink] alsa-sink.c:                      in dB: 0: 0.00 dB 1: 0.00 dB
D: [alsa-sink] sink.c: Volume not changing
D: [alsa-sink] alsa-sink.c: Requested to rewind 65536 bytes.
D: [alsa-sink] alsa-sink.c: Limited to 38136 bytes.
D: [alsa-sink] alsa-sink.c: before: 9534
D: [alsa-sink] alsa-sink.c: after: 9534
D: [alsa-sink] alsa-sink.c: Rewound 38136 bytes.
D: [alsa-sink] sink.c: Processing rewind...
D: [alsa-sink] sink.c: latency = 1307
D: [alsa-sink] sink-input.c: Have to rewind 38136 bytes on render memblockq.
D: [alsa-sink] source.c: Processing rewind...
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Stream added for object /org/pulseaudio/core1/playback_stream2
D: [pulseaudio] module-stream-restore.c: Database contains invalid data for key: sink-input-by-media-role:phone (probably pre-v1.0 data)
D: [pulseaudio] module-stream-restore.c: Attempting to load legacy (pre-v1.0) data for key: sink-input-by-media-role:phone
D: [pulseaudio] module-stream-restore.c: Size does not match.
D: [pulseaudio] module-stream-restore.c: Unable to load legacy (pre-v1.0) data for key: sink-input-by-media-role:phone. Ignoring.
I: [pulseaudio] module-stream-restore.c: Storing volume/mute/device for stream sink-input-by-media-role:phone.
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry added for object /org/pulseaudio/stream_restore1/entry3
D: [alsa-sink] sink-input.c: Requesting rewind due to uncorking
D: [alsa-sink] alsa-sink.c: Requested to rewind 65536 bytes.
D: [pulseaudio] module-suspend-on-idle.c: Sink alsa_output.pci-0000_03_0d.0.analog-stereo becomes busy.
D: [alsa-sink] alsa-sink.c: Mhmm, actually there is nothing to rewind.
D: [alsa-sink] protocol-native.c: Requesting rewind due to end of underrun.
D: [alsa-sink] alsa-sink.c: Requested to rewind 65536 bytes.
D: [alsa-sink] alsa-sink.c: Mhmm, actually there is nothing to rewind.
D: [alsa-sink] sink-input.c: Requesting rewind due to corking
D: [alsa-sink] alsa-sink.c: Requested to rewind 88 bytes.
D: [alsa-sink] alsa-sink.c: Mhmm, actually there is nothing to rewind.
D: [alsa-sink] sink-input.c: Have to rewind 8 bytes on implementor.
D: [pulseaudio] module-suspend-on-idle.c: Sink alsa_output.pci-0000_03_0d.0.analog-stereo becomes idle, timeout in 5 seconds.
D: [alsa-sink] alsa-sink.c: hwbuf_unused=0
D: [alsa-sink] alsa-sink.c: setting avail_min=16209
D: [alsa-sink] alsa-sink.c: Requested volume: 0:  54% 1:  54%
D: [alsa-sink] alsa-sink.c:            in dB: 0: -16.00 dB 1: -16.00 dB
D: [alsa-sink] alsa-sink.c: Got hardware volume: 0:  54% 1:  54%
D: [alsa-sink] alsa-sink.c:               in dB: 0: -16.00 dB 1: -16.00 dB
D: [alsa-sink] alsa-sink.c: Calculated software volume: 0: 100% 1: 100% (accurate-enough=yes)
D: [alsa-sink] alsa-sink.c:                      in dB: 0: 0.00 dB 1: 0.00 dB
D: [alsa-sink] sink.c: Volume not changing
D: [alsa-sink] alsa-sink.c: Requested to rewind 65536 bytes.
D: [pulseaudio] module-suspend-on-idle.c: Sink alsa_output.pci-0000_03_0d.0.analog-stereo becomes idle, timeout in 5 seconds.
D: [alsa-sink] alsa-sink.c: Mhmm, actually there is nothing to rewind.
D: [pulseaudio] core.c: Hmm, no streams around, trying to vacuum.
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Stream removed from object /org/pulseaudio/core1/playback_stream2
I: [pulseaudio] sink-input.c: Freeing input 2 "Output"
I: [pulseaudio] module-stream-restore.c: Synced.
I: [pulseaudio] module-suspend-on-idle.c: Source alsa_input.pci-0000_03_0d.0.analog-stereo idle for too long, suspending ...
D: [pulseaudio] source.c: Suspend cause of source alsa_input.pci-0000_03_0d.0.analog-stereo is 0x0004, suspending
I: [alsa-source] alsa-source.c: Device suspended...
D: [pulseaudio] core.c: Hmm, no streams around, trying to vacuum.
D: [pulseaudio] module-udev-detect.c: /dev/snd/controlC0 is accessible: yes
I: [pulseaudio] module-suspend-on-idle.c: Sink alsa_output.pci-0000_03_0d.0.analog-stereo idle for too long, suspending ...
D: [pulseaudio] sink.c: Suspend cause of sink alsa_output.pci-0000_03_0d.0.analog-stereo is 0x0004, suspending
I: [alsa-sink] alsa-sink.c: Device suspended...
D: [pulseaudio] core.c: Hmm, no streams around, trying to vacuum.
D: [pulseaudio] reserve-wrap.c: Device lock status of reserve-monitor-wrapper@Audio0 changed: not busy
D: [pulseaudio] module-udev-detect.c: /dev/snd/controlC0 is accessible: yes
I: [pulseaudio] client.c: Freed 3 "Skype"
I: [pulseaudio] protocol-native.c: Connection died.
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Client removed from object /org/pulseaudio/core1/client3

```

What now?

---

### Post by lidex on 2012-01-04
Does pavucontrol work now?

Check these links:
[http://ubuntuforums.org/showthread.php?p=5068487](http://ubuntuforums.org/showthread.php?p=5068487)
[http://ubuntuforums.org/showthread.php?p=11426210](http://ubuntuforums.org/showthread.php?p=11426210)

---

### Post by Edward256 on 2012-01-04
Ok, I went into pavucontrol and things seemed ok. I looked at your links and installed indicator-sound-gtk2. I then rebooted (closing the terminal with the pulseaudio -vv) and the speaker icon came back.
I tried a YouTube video, no sound. I went into Sound Settings and under Input the meter was bouncing to my voice. Ok, Mic seems to work now. I loaded pavucontrol and the output meter was working ok with the YouTube video, though the input meter seemed to be working for about a second then stopped dead in its tracks. Didn't disappear, just stopped.
Small note, this is the output as soon as I load pavucontrol:
```

:~$ pavucontrol 
** (pavucontrol:3022): DEBUG: Failed to initialize device manager extension: No such extension

```
I looked in  /etc/default/pulseaudio and set PULSEAUDIO_SYSTEM_START=1, and DISALLOW_MODULE_LOADING=0, rebooted and the speaker icon was gone. Still no sound and pavucontrol couldn't load. I set DISALLOW_MODULE_LOADING=1, rebooted, and the speaker icon was grey. No Hardware detected. I set PULSEAUDIO_SYSTEM_START=0, rebooted and everything returned to the previous state (meters bouncing but couldn't hear any sound).
I replugged the headphones into all ports just to make sure but still no sound. Volumes were full on alsamixer (turning up "Amix" I got the mic feedback), Sound Settings, pavucontrol, and even played with the keyboard volume (up, down, mute).
Double checking Sound Settings with YouTube playing I get under Applications "ALSA plug-in [plugin-container]", Volume full.
Tried aplay and no sound from there (Application says "ALSA plug-in [aplay]").

What step shall I try next? I'm rather inexperienced and don't want to do anything that will permanently break anything.

/Edward

---

### Post by Edward256 on 2012-04-14
Ok, with the help from someone else, we managed to solve the problem. After looking through it all, we decided to take out the extra sound card and just use the internal. I guess there was a conflict somewhere.

---

