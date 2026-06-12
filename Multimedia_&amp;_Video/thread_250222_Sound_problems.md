---
title: "Sound problems"
date: 2006-09-03
forum: Multimedia &amp; Video
---

### Post by claude05 on 2006-09-03
Well I am about to give up. I have been googling and searching for an answer now for hours with no progress. 

Here's my problem: Just yesterday I used Mplayer to watch a dvd of mine, at the time the 5.1 system I have played the movie perfectly. This morning I woke up and turned on the pc. The first strange thing that greeted me was the sound of the Ubuntu start up coming out of only one speaker. 

I proceded to try and play some files and another dvd as a test and sure enough the sound is only coming out of one of my speakers. Through some trial and error using alsamixer I am able to hear sound from the two front speakers (not really stereo though, more like one speaker is playing the front soundtrack and the other what would belong in the rear speakers) and my subwoofer. I have gone to the alsa website and read their how to's on installing my particular sound card(M-audio 5.1) but nothing has come of it. 

Just now as I am writing this it seems that firefox is able to interfere with the sound just by hitting the back and forward buttons....Needless to say I'm not happy, and this is enough to send me back to windows Xp despite my hate for the OS. I don't watch TV and my only way of watching my DVD's is on my PC.

here are the results of amixer on the terminal if it helps
> Simple mixer control 'IEC958',0
  Capabilities: enum
  Items: 'PCM Out' 'H/W In 0' 'H/W In 1' 'IEC958 In L' 'IEC958 In R'
  Item0: 'PCM Out'
Simple mixer control 'IEC958 Output',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958',1
  Capabilities: enum
  Items: 'PCM Out' 'H/W In 0' 'H/W In 1' 'IEC958 In L' 'IEC958 In R'
  Item0: 'PCM Out'
Simple mixer control 'DAC',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 255
  Mono: 255 [100%]
Simple mixer control 'DAC',1
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 255
  Mono: 255 [100%]
Simple mixer control 'DAC',2
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 255
  Mono: 255 [100%]
Simple mixer control 'DAC',3
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 255
  Mono: 255 [100%]
Simple mixer control 'DAC',4
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 255
  Mono: 255 [100%]
Simple mixer control 'DAC',5
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 255
  Mono: 255 [100%]
Simple mixer control 'Deemphasis',0
  Capabilities: enum
  Items: '44.1kHz' 'Off' '48kHz' '32kHz'
  Item0: 'Off'
Simple mixer control 'H/W',0
  Capabilities: enum
  Items: 'PCM Out' 'H/W In 0' 'H/W In 1' 'IEC958 In L' 'IEC958 In R'
  Item0: 'PCM Out'
Simple mixer control 'H/W',1
  Capabilities: enum
  Items: 'PCM Out' 'H/W In 0' 'H/W In 1' 'IEC958 In L' 'IEC958 In R'
  Item0: 'PCM Out'
Simple mixer control 'H/W',2
  Capabilities: enum
  Items: 'PCM Out' 'H/W In 0' 'H/W In 1' 'IEC958 In L' 'IEC958 In R'
  Item0: 'PCM Out'
Simple mixer control 'H/W',3
  Capabilities: enum
  Items: 'PCM Out' 'H/W In 0' 'H/W In 1' 'IEC958 In L' 'IEC958 In R'
  Item0: 'PCM Out'
Simple mixer control 'H/W',4
  Capabilities: enum
  Items: 'PCM Out' 'H/W In 0' 'H/W In 1' 'IEC958 In L' 'IEC958 In R'
  Item0: 'PCM Out'
Simple mixer control 'H/W',5
  Capabilities: enum
  Items: 'PCM Out' 'H/W In 0' 'H/W In 1' 'IEC958 In L' 'IEC958 In R'
  Item0: 'PCM Out'
Simple mixer control 'Multi Track Internal Clock',0
  Capabilities: enum
  Items: '8000' '9600' '11025' '12000' '16000' '22050' '24000' '32000' '44100' '48000' '64000' '88200' '96000' '176400' '192000' 'IEC958 Input'
  Item0: '48000'
Simple mixer control 'Multi Track Peak',0
  Capabilities: volume
  Playback channels: Front Left - Front Right - Rear Left - Rear Right - Front Center - Woofer - Side Left - Side Right - Rear Center - ? - ? - ? - ? - ? - ? - ? - ? - ? - ? - ? - ? - ?
  Capture channels: Front Left - Front Right - Rear Left - Rear Right - Front Center - Woofer - Side Left - Side Right - Rear Center - ? - ? - ? - ? - ? - ? - ? - ? - ? - ? - ? - ? - ?
  Limits: 0 - 255
  Front Left: 130 [51%]
  Front Right: 130 [51%]
  Rear Left: 0 [0%]
  Rear Right: 0 [0%]
  Front Center: 0 [0%]
  Woofer: 0 [0%]
  Side Left: 0 [0%]
  Side Right: 0 [0%]
  Rear Center: 0 [0%]
  ?: 0 [0%]
  ?: 0 [0%]
  ?: 0 [0%]
  ?: 0 [0%]
  ?: 0 [0%]
  ?: 0 [0%]
  ?: 0 [0%]
  ?: 0 [0%]
  ?: 0 [0%]
  ?: 0 [0%]
  ?: 0 [0%]
  ?: 0 [0%]
  ?: 0 [0%]
Simple mixer control 'Multi Track Rate Locking',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Multi Track Rate Reset',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958',0
  Capabilities: enum
  Items: 'PCM Out' 'H/W In 0' 'H/W In 1' 'IEC958 In L' 'IEC958 In R'
  Item0: 'PCM Out'
Simple mixer control 'IEC958 Output',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958',1
  Capabilities: enum
  Items: 'PCM Out' 'H/W In 0' 'H/W In 1' 'IEC958 In L' 'IEC958 In R'
  Item0: 'PCM Out'
Simple mixer control 'DAC',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 255
  Mono: 255 [100%]
Simple mixer control 'DAC',1
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 255
  Mono: 255 [100%]
Simple mixer control 'DAC',2
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 255
  Mono: 255 [100%]
Simple mixer control 'DAC',3
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 255
  Mono: 255 [100%]
Simple mixer control 'DAC',4
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 255
  Mono: 255 [100%]
Simple mixer control 'DAC',5
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 255
  Mono: 255 [100%]
Simple mixer control 'Deemphasis',0
  Capabilities: enum
  Items: '44.1kHz' 'Off' '48kHz' '32kHz'
  Item0: 'Off'
Simple mixer control 'H/W',0
  Capabilities: enum
  Items: 'PCM Out' 'H/W In 0' 'H/W In 1' 'IEC958 In L' 'IEC958 In R'
  Item0: 'PCM Out'
Simple mixer control 'H/W',1
  Capabilities: enum
  Items: 'PCM Out' 'H/W In 0' 'H/W In 1' 'IEC958 In L' 'IEC958 In R'
  Item0: 'PCM Out'
Simple mixer control 'H/W',2
  Capabilities: enum
  Items: 'PCM Out' 'H/W In 0' 'H/W In 1' 'IEC958 In L' 'IEC958 In R'
  Item0: 'PCM Out'
Simple mixer control 'H/W',3
  Capabilities: enum
  Items: 'PCM Out' 'H/W In 0' 'H/W In 1' 'IEC958 In L' 'IEC958 In R'
  Item0: 'PCM Out'
Simple mixer control 'H/W',4
  Capabilities: enum
  Items: 'PCM Out' 'H/W In 0' 'H/W In 1' 'IEC958 In L' 'IEC958 In R'
  Item0: 'PCM Out'
Simple mixer control 'H/W',5
  Capabilities: enum
  Items: 'PCM Out' 'H/W In 0' 'H/W In 1' 'IEC958 In L' 'IEC958 In R'
  Item0: 'PCM Out'
Simple mixer control 'Multi Track Internal Clock',0
  Capabilities: enum
  Items: '8000' '9600' '11025' '12000' '16000' '22050' '24000' '32000' '44100' '48000' '64000' '88200' '96000' '176400' '192000' 'IEC958 Input'
  Item0: '48000'
Simple mixer control 'Multi Track Peak',0
  Capabilities: volume
  Playback channels: Front Left - Front Right - Rear Left - Rear Right - Front Center - Woofer - Side Left - Side Right - Rear Center - ? - ? - ? - ? - ? - ? - ? - ? - ? - ? - ? - ? - ?
  Capture channels: Front Left - Front Right - Rear Left - Rear Right - Front Center - Woofer - Side Left - Side Right - Rear Center - ? - ? - ? - ? - ? - ? - ? - ? - ? - ? - ? - ? - ?
  Limits: 0 - 255
  Front Left: 130 [51%]
  Front Right: 130 [51%]
  Rear Left: 0 [0%]
  Rear Right: 0 [0%]
  Front Center: 0 [0%]
  Woofer: 0 [0%]
  Side Left: 0 [0%]
  Side Right: 0 [0%]
  Rear Center: 0 [0%]
  ?: 0 [0%]
  ?: 0 [0%]
  ?: 0 [0%]
  ?: 0 [0%]
  ?: 0 [0%]
  ?: 0 [0%]
  ?: 0 [0%]
  ?: 0 [0%]
  ?: 0 [0%]
  ?: 0 [0%]
  ?: 0 [0%]
  ?: 0 [0%]
  ?: 0 [0%]
Simple mixer control 'Multi Track Rate Locking',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Multi Track Rate Reset',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]

Now I've written alot already and I hope you all have patience enough to help me, but I have one more question. In reading the Alsa site they mention recompiling the Kernel as an alternative to doing a reinstall of the OS. Now is that a feasible answer to my problem or should I just go ahead and reinstall?

Thank you.

---

### Post by claude05 on 2006-09-04
Bump! I was able to get Mplayer to play 5.1 sound by going into the terminal and typing >  gmplayer -channels 6 -ao alsa:device=surround51 
so at least I can watch my dvd's finally, however, the problem of the rest of the system only using the right front speaker persists. Any ideas guys? I'm at a loss here.

---

