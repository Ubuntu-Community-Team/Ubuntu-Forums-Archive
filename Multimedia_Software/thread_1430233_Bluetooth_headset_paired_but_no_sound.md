---
title: "Bluetooth headset paired but no sound"
date: 2010-03-15
forum: Multimedia Software
---

### Post by zorgh on 2010-03-15
Hi,

I have successfully paired my Jabra Headset (Ubuntu Intrepid 64 bits) but no sound comes through the headset.

```
btsco -v -f -r -s 00:07:A4:07:3A:BB
btsco v0.42
Device is 3:0
Voice setting: 0x0060
RFCOMM channel 1 connected
Using interface hci0

```

```

aplay -B 1000000 -D plughw:Headset /usr/share/sounds/question.wav
ALSA lib pcm_hw.c:1429:(_snd_pcm_hw_open) Invalid value for card
aplay: main:583: audio open error: No such file or directory

```

```

aplay -l
**** List of PLAYBACK Hardware Devices ****
card  0: Intel [HDA Intel], périphérique 0 : AD198x Analog [AD198x Analog]
  Subdevices: 0/1
  Subdevice: #0: subdevice #0
card  0: Intel [HDA Intel], périphérique 1 : AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice: #0: subdevice #0

```

Thanks for your help.

---

### Post by gradinaruvasile on 2010-03-15
Upgrade Ubuntu to at least 9.10 - the bluetooth drivers work well with that version.

Also, PulseAudio is the only way i was able to make it work - bluetooth sound with ALSA worked only with aplay and mplayer, any other program crashed or it wasnt working at all.
I used blueman for managing the bluetooth devices - its really point and click affair with that, it automatically connects and sets up the bluetooth device to PulseAudio.
But you need PulseAudio 9.15 at least (Ubuntu 9.10 has something like 9.20) to get it work decently.

---

### Post by carstanje on 2010-03-31
You can check something first. Go to sound preferences (right mouse click volume item in panel) and check if for output the bluetooth device is selected. This worked for me.

The issue I am having is that the headset (motorola S9) only works when I load ubuntu and directly connect the headset. If I connect the headset after a while it will still pair but not appear in the list of devices. In that case there is no possible way to select this as the actual audiodevice.

---

