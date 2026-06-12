---
title: "How to enable internal speaker"
date: 2010-02-09
forum: Multimedia Software
---

### Post by waddinxveen on 2010-02-09
Can someone explain to me how to get sound through the internal speaker of my computer. Everything else works fine. IE, if I plug in a headset or boxes, they work fine.

Thanks in advance

---

### Post by HappyFeet on 2010-02-09
Try
```
alsamixer
```
then with your right arrow key, go all the way to the left, (window will scroll) and you will see the beep control. Raise the volume with the up arrow.

---

### Post by Manyette on 2010-02-09
> Can someone explain to me how to get sound through the internal speaker of my computer. Everything else works fine. IE, if I plug in a headset or boxes, they work fine.
Some details of your computer would  help?

---

### Post by waddinxveen on 2010-02-10
Thanks for the quick reactions.

HappyFeet: I just tried your alsamixer suggestion (with the headset plugged out), but it did not help. I also experimented a bit with pulseaudio, bud I am no hero with that.

Manyette: I have a MSI P6N SLI motherboard with onboard Realtec ALC888 audio.

The gnome sound preferences lists two devices, internal sound en webcam (only input). Should a pc speaker be a third device in this list?

btw, this is no hardware malfunction, it beeps normally during the bios.

---

### Post by Manyette on 2010-02-10
> **waddinxveen said:**
> Thanks for the quick reactions.

HappyFeet: I just tried your alsamixer suggestion (with the headset plugged out), but it did not help. I also experimented a bit with pulseaudio, bud I am no hero with that.

Manyette: I have a MSI P6N SLI motherboard with onboard Realtec ALC888 audio.

The gnome sound preferences lists two devices, internal sound en webcam (only input). Should a pc speaker be a third device in this list?

btw, this is no hardware malfunction, it beeps normally during the bios.

Have you loaded "gnome-alsamixer" from Synaptic.  Those setting might solve your problem for you.

---

