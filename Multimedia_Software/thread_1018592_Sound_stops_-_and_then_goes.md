---
title: "Sound stops - and then goes"
date: 2008-12-22
forum: Multimedia Software
---

### Post by radox1912 on 2008-12-22
my problem is folowing:

when i listen to mp3 in rhythmbox (also tried banshee and some others), sometimes happens, that the sound stops playing for 6-7 seconds (but the mp3 is still going forward) and then it plays again.this happens also while watching video. it is very annoying. here is my terminal output:

```
radox@radox-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SIS966 [HDA SIS966], device 0: ALC660-VD Analog [ALC660-VD Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: SIS966 [HDA SIS966], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
radox@radox-laptop:~$ cat /proc/asound/cards
 0 [SIS966         ]: HDA-Intel - HDA SIS966
                      HDA SIS966 at 0xfebf8000 irq 18
radox@radox-laptop:~$ lspci | grep -i audio
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
radox@radox-laptop:~$ amixer info
Card default 'pulse'/'PulseAudio'
  Mixer name	: 'PulseAudio'
  Components	: ''
  Controls      : 4
  Simple ctrls  : 2

```

---

