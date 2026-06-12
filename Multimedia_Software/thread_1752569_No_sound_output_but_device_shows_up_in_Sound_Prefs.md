---
title: "No sound output but device shows up in Sound Prefs"
date: 2011-05-08
forum: Multimedia Software
---

### Post by johnnyoc3 on 2011-05-08
I have a fresh install of Natty and i'm having some issues getting sound to work. My laptop has a built in sound card which works just fine. However, i also have a usb 5.1 sound card which isn't working at all. Both devices show up in 'Sound Preferences' but when i select the 5.1 device as the output device sound doesnt work. 

I ran the alsa-info.sh script and the output can be found here. any help is greatly appreciated


[http://www.alsa-project.org/db/?f=eaf0bcf0994752ef2b692716ecb5a9582948be51](http://www.alsa-project.org/db/?f=eaf0bcf0994752ef2b692716ecb5a9582948be51)

---

### Post by johnnyoc3 on 2011-05-08
just to clarify, the device in question is 

'Bus 001 Device 019: ID 0d8c:0006 C-Media Electronics, Inc. Storm HP-USB500 5.1 Headset'

In 'pavucontrol' i can set the output to the 'Storm HP-USB500 5.1 Headset' device and the volume bar below the device moves as if audio is being played. However, no sound comes out.

---

### Post by johnnyoc3 on 2011-05-13
bump

---

### Post by lidex on 2011-05-14
What profile is selected for that card in 'Sound Preferences'?
Have you used alsamixer to make sure the outputs are not muted?
```
Card hw:1 'Audio'/'USB Audio at usb-0000:00:1d.7-8.1.4, full speed'
  Mixer name	: 'USB Mixer'
  Components	: 'USB0d8c:0006'
  Controls      : 12
  Simple ctrls  : 7
Simple mixer control 'Speaker',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 37
  Mono: Playback 0 [0%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 16
  Front Left: Capture 8 [50%] [7.99dB]
  Front Right: Capture 8 [50%] [7.99dB]
Simple mixer control 'PCM Capture Source',0
  Capabilities: enum
  Items: 'Mic' 'Line' 'IEC958 In' 'Mixer'
  Item0: 'Mic'
Simple mixer control 'Line',0
  Capabilities: pvolume cvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 8191 Capture 0 - 16
  [COLOR="Red"]Front Left: Playback 2048 [25%] [7.99dB] [off][/COLOR] Capture 8 [50%] [7.99dB]
  [COLOR="Red"]Front Right: Playback 2048 [25%] [7.99dB] [off][/COLOR] Capture 8 [50%] [7.99dB]
Simple mixer control 'Mic',0
  Capabilities: pvolume cvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 32 Capture 0 - 16
  Front Left: Playback 8 [25%] [7.99dB] [off] Capture 0 [0%] [0.00dB]
  Front Right: Playback 8 [25%] [7.99dB] [off] Capture 0 [0%] [0.00dB]
Simple mixer control 'IEC958 In',0
  Capabilities: cswitch cswitch-joined penum
  Capture channels: Mono
  Mono: Capture [on]
Simple mixer control 'Auto Gain Control',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]

```

---

### Post by johnnyoc3 on 2011-05-19
just and update on this. I had previously tried your suggestions to no avail. 

However, I decided to try the USB Sound Card with a friends computer and it looks like the actual hardware is broken. Not a Ubuntu issue at all

regardless, thanks for the help!

---

