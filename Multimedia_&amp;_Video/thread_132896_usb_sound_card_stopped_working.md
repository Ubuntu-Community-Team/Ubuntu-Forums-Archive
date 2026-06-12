---
title: "usb sound card stopped working?"
date: 2006-02-19
forum: Multimedia &amp; Video
---

### Post by LazyP on 2006-02-19
My external usb sound card just stopped working for unkown reason. Sometime between february 6th (then it worked) and february 11th (then it had stopped working). and between these dates I didn't fiddle with the audio settings at all.

The sound card still works perfectly if I boot up with windows xp so the card is not broken.

This is on my laptop. Dell inspiron 6000 with an Intel onboard sound card. The onboard sound still works and I usually use the onboard sound as primary card and the usb as secondary. All applications still see the usb sound card, sometimes they even claim to send sound to it but there is no sound out.

The usb card is a Terratec Aureon 5.1 usb.

Output of aplay -l for info:

**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Audio [USB Audio], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I've tried everything I've found on the forums but I can't get it to work again. Have any security or kernel updates been made during this period affecting usb? I always keep my laptop up to date with all security updates.

---

### Post by Teroedni on 2006-02-19
It may be that the esd server are using the wrong card

How do you switch between the cards?

---

### Post by LazyP on 2006-02-19
I use esd for the internal card and Alsa for the external card. Never esd for both. I actually use both at the same time when I use the computer for DJing. Preview on the internal and output on the external USB.

---

