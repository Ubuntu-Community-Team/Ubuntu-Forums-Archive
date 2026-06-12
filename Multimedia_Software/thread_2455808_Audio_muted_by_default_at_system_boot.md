---
title: "Audio muted by default at system boot"
date: 2020-12-28
forum: Multimedia Software
---

### Post by crpz41 on 2020-12-28
I already opened alsamixer, and I noticed the every time I turn the PC on, the audio is muted
and I have to open alsamixer, select the output device and press M, every time to have audio working.
I already tried to save alsamixer settings by:
```
sudo alsactl store
```
but once I reboot I have still no audio.
I already disabled via pulseaudio the only other output device, a NVIDIA HDMI audio.
[B]

IMPORTANT UPDATES and SOLUTION
- this problem appears when you install nvidia drivers 455 but already happened in history with older versions of both ubuntu and nvidia drivers
- every time I reload pulseaudio and amixer, after I unmuted the audio, audio turns back muted, this is the same that happens if you reboot the system.
- this folder seems to contain really interesting settings: /usr/share/pulseaudio/alsa-mixer/paths/
[U][I][B]on this path there are many files, one of those is related to USB-Audio (my audio out), 
in my case this file was called analog-output-speaker.conf
[/B]if I set everything to ON inside (by default everything was on OFF or mute), the problem is fixed[/I][/U]

[/B]

---

### Post by #&amp;thj^% on 2020-12-28
Show us this please:
```
amixer | grep mixer
```

---

### Post by crpz41 on 2020-12-28
```

Simple mixer control 'IEC958',0
Simple mixer control 'IEC958',1
Simple mixer control 'IEC958',2
Simple mixer control 'IEC958',3
Simple mixer control 'IEC958',4
Simple mixer control 'IEC958',5
Simple mixer control 'IEC958',6


```

---

### Post by #&amp;thj^% on 2020-12-28
Something is very wrong with yours:
Mine shows:
```
Simple mixer control 'Master',0
Simple mixer control 'Headphone',0
Simple mixer control 'Speaker',0
Simple mixer control 'Bass Speaker',0
Simple mixer control 'Mic Boost',0
Simple mixer control 'Mic Mute-LED Mode',0
Simple mixer control 'IEC958',0
Simple mixer control 'IEC958',1
Simple mixer control 'IEC958',2
Simple mixer control 'Capture',0
Simple mixer control 'Auto-Mute Mode',0
Simple mixer control 'DAC1',0
Simple mixer control 'DAC2',0
Simple mixer control 'Dmic0',0
Simple mixer control 'Dmic1 2nd',0
Simple mixer control 'PGA1.0 1 Master',0
Simple mixer control 'PGA2.0 2 Master',0
Simple mixer control 'PGA3.0 3 Master',0
Simple mixer control 'PGA4.0 4 Master',0
Simple mixer control 'PGA7.0 7 Master',0
Simple mixer control 'PGA8.0 8 Master',0
Simple mixer control 'PGA9.0 9 Master',0

```
Also would you try this:
```
amixer -D pulse sset Master 80%
```
Report  the results

---

### Post by crpz41 on 2020-12-28
```

Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right - Rear Left
  Limits: Playback 0 - 65536
  Mono:
  Front Left: Playback 52429 [80%] [on]
  Front Right: Playback 52429 [80%] [on]
  Rear Left: Playback 52429 [80%] [on]



```

---

### Post by #&amp;thj^% on 2020-12-28
> **crpz41 said:**
> ```

Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right - Rear Left
  Limits: Playback 0 - 65536
  Mono:
  Front Left: Playback 52429 [80%] [on]
  Front Right: Playback 52429 [80%] [on]
  Rear Left: Playback 52429 [80%] [on]



```

Any Sound???
Also try a reboot now, if the sound works currently.

---

### Post by crpz41 on 2020-12-28
now the audio works... because was already working...(I have to enable every time the system is rebooted)
but If I reboot the audio may disappear. 
I'll update this post once I rebooted

EDIT:
after reboot no audio
this is the output of previous command
```


Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right - Rear Left
  Limits: Playback 0 - 65536
  Mono:
  Front Left: Playback 52429 [80%] [on]
  Front Right: Playback 52429 [80%] [on]
  Rear Left: Playback 52429 [80%] [on]


```

---

### Post by #&amp;thj^% on 2020-12-28
> **crpz41 said:**
> now the audio works... because was already working...(I have to enable every time the system is rebooted)
but If I reboot the audio may disappear. 
I'll update this post once I rebooted

EDIT:
after reboot no audio
this is the output of previous command
```


Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right - Rear Left
  Limits: Playback 0 - 65536
  Mono:
  Front Left: Playback 52429 [80%] [on]
  Front Right: Playback 52429 [80%] [on]
  Rear Left: Playback 52429 [80%] [on]


```

To make this permanent add this to "Startup Applications"
```
sleep 10 && amixer -c 0 set Speaker 80%
```
Now reboot again, is there now sound without you making changes???
**EDIT:** I added a delay, so your sound might not show instantly. ;) Just a Heads Up

---

### Post by crpz41 on 2020-12-29
it just says: 
amixer: Unable to find simple control 'Speaker',0

no solution for now

---

### Post by #&amp;thj^% on 2020-12-29
Sorry I just saw your reply, one more to try, >>>Change *only* <'_**Speaker**_' ,0> to <Master> in the Startup Applications.

---

### Post by crpz41 on 2021-01-02
I have no idea what to do.
in the startup application there is nothing related to audio
if I run:
```
pactl list short sinks

1    alsa_output.pci-0000_01_00.1.hdmi-stereo    module-alsa-card.c    s16le ch 2 44100 Hz    SUSPENDED
2    alsa_output.usb-Generic_USB_Audio-00.analog-stereo    module-alsa-card.c    s16le ch 2 48000 Hz    SUSPENDED
```

---

### Post by crpz41 on 2021-01-03
I added some updates related to this problem on top of the thread. please read those

---

### Post by #&amp;thj^% on 2021-01-03
I was referring to this>>"sleep 10 && amixer -c 0 set **Speaker **80%"
Change "Speaker" to "Master"

---

