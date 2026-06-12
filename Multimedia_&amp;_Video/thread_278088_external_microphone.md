---
title: "external microphone"
date: 2006-10-15
forum: Multimedia &amp; Video
---

### Post by andrei.kouznetsov on 2006-10-15
Hi, everybody
I managed to get built-in microphone to work on my laptop. But when I plug my external microphone in my sound card Ubuntu still uses built-in microphone.

I'm not sure where the problem is. May be I should switch input source to another micro but I could not find where.

Any help will be appriciated.

---

### Post by andrei.kouznetsov on 2006-10-17
Here is more information:
I use my external microphone along with headphone. Headphone works but micro - not.

My laptop is MS-1034

<code>
and@and-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 2: ALC882 Digital [ALC882 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
</code>

---

