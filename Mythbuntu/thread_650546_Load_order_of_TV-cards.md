---
title: "Load order of TV-cards"
date: 2007-12-26
forum: Mythbuntu
---

### Post by erland on 2007-12-26
Is there some way I can configure which /dev/video* device each TV-card is going to get ?

The problem I have is that I have two cards in the computer:
- PVR-150 (analoge)
- Technotrend C-2300 (DVB-C card, same as Nexus CA)

As long as the Technotrend card is loaded first everything is correct, the Technotrend card gets /dev/video0 and the PVR-150 gets /dev/video1. However, sometimes the order is reversed if the ivtv driver for the PVR-150 finish loading first at boot. The result is of course that the mythtv backend no longer works since the wrong cards are connected to the wrong devices.

What I basically would like to do is to hardcode the PVR-150 card (ivtv driver) so it always gets /dev/video0. Is there some way to do this ?

I've already tried putting both drivers in /etc/modules, but that didn't seem to help.

---

### Post by p$y on 2007-12-26
Similar problem here, I've 2 DVB-T USB Cards, which sometimes change their ID. It was the same with my Soundcards (PCI & OnBoard) but for this I found a solution described in the forum, I had to set the standard Audio-Device.

---

### Post by murchball on 2007-12-26
I believe this is covered in the MythTV documentation here:
[http://www.mythtv.org/wiki/index.php/Device_Filenames_and_udev]("http://www.mythtv.org/wiki/index.php/Device_Filenames_and_udev")

---

### Post by erland on 2007-12-31
I didn't get the udev stuff to work, but adding this to /etc/modprobe.d/aliases solved the problem:
```

options ivtv ivtv_first_minor=1

```
This makes the ivtv driver for the PVR-150 always to get /dev/video1 even if /dev/video0 is free.

---

### Post by p$y on 2008-03-20
sorry to push this thread, but will this problem get solved with 8.04? because the how-to is too complicated for me.

---

