---
title: "Sound card out of control"
date: 2011-09-20
forum: Multimedia Software
---

### Post by jczernia on 2011-09-20
Hi
I wanted to show my kid how the music scores work so installed NtEd. Unfortunately the sound was not produced, the only way to workaround was to export to midi and play using some MidiPlayer (tmidity or sth.). I tried to fix the problem so installed ALSA mixer and some other stuff available through Ubuntu SW Center, even tried GNU Denemo. It all failed, so uninstalled all of that (I suppose, I went through history in software Center), but a strange thing occurs. Now, once OS loads I hear white noise out of speaker, and can not control it through standard volume control app which comes with Ubuntu (11.04 using). Mute does not work (on both mic and speakers), and it looks signal from mic is directly routed to speaker (when I am closing the laptop I can hear feedback at high frequencies.
Any idea how to disable it and back to normal ?
Thanks in advance.
jacek

---

### Post by khelben1979 on 2011-09-20
Make a backup and reinstall would be the easiest way, and less painful. Recommended solution, I think.

Otherwise you could try and configure up and install the whole [ALSA]("http://en.wikipedia.org/wiki/Advanced_Linux_Sound_Architecture") system from source code and when doing that you get the latest version of ALSA available which might even be newer than what your Ubuntu system can offer, thereby removing bugs and/or adding some new ones in the process.

To truly understand why you're having these issues with your sound chip/card it would help us to know about what sound hardware is being used, and what version of ALSA which Ubuntu is using, this to find out if it's a bug or if it's just badly configured. Hard to know what it is right now.

```
lspci
``` (shows what sound hardware you got among other things).

---

### Post by jczernia on 2011-09-20
Hi
Sounds no easy workaround at all :(
My HW 
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)

---

### Post by khelben1979 on 2011-09-20
Is this a laptop that you're using?

---

### Post by jczernia on 2011-09-20
it's netbook Toshiba NB 305

---

### Post by jczernia on 2011-09-20
And by the way ALSA mixer shows *HDA Intel: Realtek ALC272*

---

### Post by lidex on 2011-09-21
What is your amixer output:
```
amixer
```

---

### Post by jczernia on 2011-09-21
There is the output
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 36 [56%] [-28.00dB] [off]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [off]
  Front Right: Playback 64 [100%] [0.00dB] [off]
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [off]
  Front Right: Playback 64 [100%] [0.00dB] [off]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 252 [99%] [0.60dB]
  Front Right: Playback 252 [99%] [0.60dB]
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
  Front Left: 2 [67%] [20.00dB]
  Front Right: 2 [67%] [20.00dB]
Simple mixer control 'Beep',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 23 [74%] [0.00dB] [off]
  Front Right: Playback 23 [74%] [0.00dB] [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 21 [68%] [15.00dB] [on]
  Front Right: Capture 21 [68%] [15.00dB] [on]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 11 [35%] [0.00dB] [off]
  Front Right: Capture 11 [35%] [0.00dB] [off]
Simple mixer control 'Internal Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 23 [74%] [0.00dB] [on]
  Front Right: Playback 23 [74%] [0.00dB] [on]
Simple mixer control 'Internal Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 3 [100%] [30.00dB]
  Front Right: 3 [100%] [30.00dB]
emila@emila-TOSHIBA-NB305:~$

---

### Post by jczernia on 2011-09-22
Ok so using amixer I muted 'Internal Mic' which was responsible for this issue. now I have control back through standard ubuntu "Sound preferences" app. I noticed that 'Master' and 'Capture'0 are the ones controlled by "Sound Preferences". Hope that's it and battery consumption will back to reasonable level. With this issue battery was dead after two hours.

---

### Post by lidex on 2011-09-22
So we're good here?

---

### Post by jczernia on 2011-09-23
lidex - you are great! Just love you guys  ;-)

---

