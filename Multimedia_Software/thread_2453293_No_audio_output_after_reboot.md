---
title: "No audio output after reboot"
date: 2020-11-06
forum: Multimedia Software
---

### Post by The Cog on 2020-11-06
Today, for some reason my laptop decided I don't have any sound cards - the system tray sound control only shows **Dummy Output** option.
**asound -l** lists cards, but it seems they don't make it into pulse audio's list. This command fixes it temporarily:
```
speaker-test --device hw:1,0
```
after which the sound control indicates that I'm changing the volume, and then it lists an option of headphone or speakers. But obviously, I would prefer if it showed the choice without manual intervention every time I boot.

Does anyone have any idea how I can correct this? It only just started happening, and I don't recall doing any updates since I last used the speakers two days ago. Grrr!

P.S. I got the card,device from the output of **aplay -l**:
```
**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic_1 [HD-Audio Generic], device 0: ALC255 Analog [ALC255 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

PPS: Sometimes the card is card 2 instead of card 1 so I have to change the hw in speaker-test to match. It never successfully plays a sound though - resource busy, but at least it gets the sound working..

---

