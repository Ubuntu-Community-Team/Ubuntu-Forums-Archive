---
title: "Sound devices mixed up."
date: 2008-09-23
forum: Multimedia Software
---

### Post by gregbzh on 2008-09-23
Kia ora.  I'm having a small problem with my sound devices.  I can play music through my speakers no worries, but for some reason any internet radio and thunderbird mail notification sounds play through my Logitech USB headset.

This is more frustrating than anything, but I'd like to sort it out.  Am I overlooking something?

Cheers.

---

### Post by markbuntu on 2008-09-23
If you are using pulsaudio then you can change the default sound card easily and direct any sound application to any device. The Pulseaudio Volume Control will have your sound card and usb headphones as separate devices in the Output Devices section. Your playing applications will appear in the Playback section. You can change any playing application to your headest by right clicking on it and choosing move stream and choosing the other device.

If you would like all your applications to use pulseaudio so you can control them like this you can read my guide here:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

If you do not have the Pulseaudio volume control in Applications/Sound & Video you can get it with synaptic:

pavucontrol

---

### Post by gregbzh on 2008-09-27
Thanks.

---

