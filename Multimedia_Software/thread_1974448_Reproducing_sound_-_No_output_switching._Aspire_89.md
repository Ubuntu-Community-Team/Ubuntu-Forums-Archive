---
title: "Reproducing sound - No output switching. Aspire 8935g"
date: 2012-05-06
forum: Multimedia Software
---

### Post by Graham C Williams on 2012-05-06
Reproducing sound - No output switching. Aspire 8935g
Acer Aspire 8935G. ubuntu 12.04 64bit

Dear Sirs.
Any audio O/P appears at the headphone socket and the computer speakers together. Please see attached result of amixer in the hope that it'll help.
G.

monique@monique-Aspire-8935G:~$ amixer
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 51 [80%] [-13.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 253 [99%] [0.40dB]
  Front Right: Playback 253 [99%] [0.40dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 62 [97%] [0.00dB] [on]
  Front Right: Playback 62 [97%] [0.00dB] [on]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 62 [97%] [0.00dB] [on]
  Front Right: Playback 62 [97%] [0.00dB] [on]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 62 [97%] [0.00dB] [on]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 62 [97%] [0.00dB] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 21 [68%] [-3.00dB] [off]
  Front Right: Playback 21 [68%] [-3.00dB] [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 23 [74%] [0.00dB] [off]
  Front Right: Playback 23 [74%] [0.00dB] [off]
Simple mixer control 'Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Beep',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 21 [68%] [-3.00dB] [on]
  Front Right: Playback 21 [68%] [-3.00dB] [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 46
  Front Left: Capture 0 [0%] [-16.00dB] [on]
  Front Right: Capture 0 [0%] [-16.00dB] [on]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 46
  Front Left: Capture 0 [0%] [-16.00dB] [on]
  Front Right: Capture 0 [0%] [-16.00dB] [on]
Simple mixer control 'Capture',2
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 46
  Front Left: Capture 0 [0%] [-16.00dB] [on]
  Front Right: Capture 0 [0%] [-16.00dB] [on]
Simple mixer control 'Channel Mode',0
  Capabilities: enum
  Items: '2ch' '4ch' '6ch'
  Item0: '2ch'
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Mic' 'Line' 'CD' 'Front Mic' 'Input Mix'
  Item0: 'Front Mic'
Simple mixer control 'Input Source',1
  Capabilities: cenum
  Items: 'Mic' 'Line' 'CD' 'Input Mix'
  Item0: 'Mic'
Simple mixer control 'Input Source',2
  Capabilities: cenum
  Items: 'Mic' 'Line' 'CD' 'Input Mix'
  Item0: 'Mic'

---

### Post by Graham C Williams on 2012-05-06
Last time I had a problem with this computer one of the team suggested the following:
echo "options snd-hda-intel model=acer-aspire-8930g" | sudo tee -a /etc/modprobe.d/alsa-base.conf

I have tried this in relation to this problem with little joy.
I notive that this audio system uses the multi speaker system much better (I'm reluctant to call it 5.1).

Thanks again
Graham.

---

### Post by Graham C Williams on 2012-05-08
I now have one of 2 modes that I can run in.
1) If I install the PulseAudio Volume Control the system will only play out of the headphone socket.
2) If I remove the  mixer it will play from the speakers and the Headphone all together.

I've noticed a thread setup for people with sound problems ref 12.04. I'll abandon this thread and move onto that.

G.

---

