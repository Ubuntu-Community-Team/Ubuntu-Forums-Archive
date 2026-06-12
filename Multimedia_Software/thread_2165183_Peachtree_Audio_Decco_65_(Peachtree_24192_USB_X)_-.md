---
title: "Peachtree Audio Decco 65 (Peachtree 24/192 USB X) - No Sound"
date: 2013-08-03
forum: Multimedia Software
---

### Post by danny-rosen on 2013-08-03
Hi there,
I'm unable to get sound to play out of my Peachtree Audio Decco 65 integrated amplifier USB DAC. The device comes up as Peachtree 24/192 USB X and is in /proc/asound/cards as:

```
 1 [X              ]: USB-Audio - Peachtree 24/192 USB X
                      Peachtree 24/192 Peachtree 24/192 USB X at usb-0000:00:1a.7-6, high speed

```

But I'm unable to play audio through USB (Optical from my HDA-Intel onboard works as does USB from Windows, it's not a device issue.)

Any ideas around how to troubleshoot?

---

### Post by danny-rosen on 2013-10-28
Figured this one out.
To get the Peachtree Audio Decco 65 to work you'll need to run alsamixer and make sure both clock selectors are not muted:


[IMG]http://i.imgur.com/Ry9qUNz.jpg[/IMG]

---

