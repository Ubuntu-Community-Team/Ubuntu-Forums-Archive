---
title: "Teletext and FM in USB HDTV tuners"
date: 2011-08-26
forum: Multimedia Software
---

### Post by Machacz on 2011-08-26
Does anybody use USB HDTV (digital or hybrid) tuner ?

Write please:

1) does teletext  work in digital TV ?
- Do teletext pages appear immediately after page numbers entering   or
- must you wait every time because of counter rewinding ?

2) Does analog FM radio (88 - 108 MHz) work in that kind tuners ?

There are mostly no such infos on linuxtv.org.

---

### Post by BicyclerBoy on 2011-08-27
I'm using a nova-500-t PCI but there is a USB version that is almost identical.

All below is in my corner:
Analogue TV switch off is in couple of years.
The certified dvb-t/s set-top boxes must provide teletext.
The teletext data is a digital datastream along with channels.
Some multiplexes/channels do not carry it.

Teletext works fine & fast (instant page navigation) with MythTV.
The 'proper' captions work better than teletext ones.
Teletext is to be switched off & replaced when analogue switch-off occurs.
Advertising most likely..

FM radio tuner would be a separate feature..some PCI/PCIe cards have this..
Internet radio replaces this for many folks..

---

### Post by Machacz on 2011-08-30
Thank you very much for answer !

Excuse my english.
> **BicyclerBoy said:**
> Teletext works fine & fast (instant page navigation) with MythTV.
Are you talking about colour links (red, green, yellow, blue) or about every three-digits directly entered number (from 100 - 899) ?

> The 'proper' captions work better than teletext ones.What are 'proper' captions ?

---

### Post by BicyclerBoy on 2011-08-30
Both colour button links & page numbers work with MythTV..you need to map the "colour buttons" to some real remote button..

Real captions are closed captions or sub-titles (& other languages audio streams), part of the original program & transmitted as a stream with the audio & video..just like DVD & Bluray.

Teletext subtitles still seem more common with local content & news etc.
But it will be turned off..

---

### Post by Machacz on 2011-08-31
I just chase a feature refering to your words after "&" :
> **BicyclerBoy said:**
> Both colour button links & page numbers work with MythTV
does every page 100-899 (if exists) appear _immediately_ when you enter number ?

---

### Post by BicyclerBoy on 2011-08-31
Yes..immediately instantly..
Please be aware that this applies to a small corner of the world using PAL & dvb-t/s OTA TV.

I think teletext is only available in "live TV" mode of MythTV (not recordings).
The other streamed data (EPG etc) is recorded.
I use MythTV to avoid live TV.

There could be a cache loading time from starting live TV but it is less than my menu/button pressing delay.

---

