---
title: "help - enabling independent front panel audio"
date: 2007-10-25
forum: Multimedia &amp; Video
---

### Post by Asobi on 2007-10-25
i got front and rear panel both, both give the same sound, what i want is a seperate front and rear panel audio stream, like i had in windows. rearpanel (call it default device) for games/music/ect connected to my amp. the front panel got a headset plugged which i use for skype and such, so the sounds dont interfere. internally i guess that you get two devices on a single physical chip.

this is what i get returned from aplay -l in terminal

> card 0: NVidia [HDA NVidia], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


it shows two devices but it doesnt look like what im looking for. im pretty much clueless :confused:. if i could just find a way to first disable my frontpanel maybe that gets me closer to enable to on another stream.

the soundcard is a realtek ad1988 on a asus m2n-sli deluxe motherboard with a nvidia nforce 570 sli mcp chipset

if someone has any clue ..pls share

---

### Post by jerrek71 on 2008-06-17
I hate to be a 'me too' poster, but I could use some help with this too. It works straight out the box in windows with the RealTek drivers and I'd really love (indeed, need) to get this working under Ubuntu.

I downloaded X-Ten's Softphone for Linux but it seems it'll only use OSS sound drivers so I'm not expecting to get that working on the seperate independent front and rear audio streams.

If anyone can shed any light that'd be excellent. I've googled all morning and can't seem to find anything.

---

