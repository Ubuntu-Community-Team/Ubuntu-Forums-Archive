---
title: "Headphones disconnected when I change volume"
date: 2010-06-09
forum: Multimedia Software
---

### Post by haecceitas on 2010-06-09
I have my laptop at a place that is a bit unaccessible (using USB keyboard, mouse and external monitor).
I'm using the latest stable version of Ubuntu and have the problem that whenever I change the master volume, my headphones stop working and sound comes from the laptop speakers instead. I then have to remove the headphones from the speaker jack, and replug them.

Is there any way to make the system keep the connection with the headphones, even when altering the system sound?

Can someone help me with this? Thanks!

---

### Post by lidex on 2010-06-09
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by haecceitas on 2010-06-09
```
Linux Lappie 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 i686 GNU/Linux

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1

Advanced Linux Sound Architecture Driver Version 1.0.21.

Codec: VIA VT1708S


```My laptop is an ASUS X5DAB (MB: K50AB)

---

### Post by lidex on 2010-06-09
OK. Try upgrading your alsa install via the upgrade link in my sig.

---

