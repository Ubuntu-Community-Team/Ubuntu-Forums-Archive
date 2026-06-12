---
title: "USB external audio card settings"
date: 2010-05-24
forum: Multimedia Software
---

### Post by TryHarder on 2010-05-24
Good evening. 
I've purchased Creative sound blaster. It's external usb sound card, which worked well as I plugged it in. In sound preferences it was setted to 'Analog stereo output' in hardware, and I've accidently messed up with Connector droplist in Output bookmark. As a result - silence in my speakers. 
I wonder what went wrong and where to search for it. The card is worked and it is supported by ALSA. Just some settings went wrong.
Help please.

---

### Post by TryHarder on 2010-05-24
EDIT: 
problem solved by simple: alsactl init [cardNUM]
in my case it was alsactl init 1

---

