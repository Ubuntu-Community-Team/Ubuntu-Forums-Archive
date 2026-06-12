---
title: "Default audio device"
date: 2010-10-30
forum: Multimedia Software
---

### Post by riseringseeker on 2010-10-30
Is there a way to make Ubuntu recognize when I plug in a USB microphone, or a blue tooth?

I would very much like to not have to manually choose a mike after I plug it in.  In the case of the USB, if I have it plugged in at boot, it works fine, but it doesn't switch to when plugged in afterward.  I can always choose it, but it would be much handier if it automagically used it.

---

### Post by tristan on 2010-10-31
> **riseringseeker said:**
> Is there a way to make Ubuntu recognize when I plug in a USB microphone, or a blue tooth?

I would very much like to not have to manually choose a mike after I plug it in.  In the case of the USB, if I have it plugged in at boot, it works fine, but it doesn't switch to when plugged in afterward.  I can always choose it, but it would be much handier if it automagically used it.

Here's the solution that I stumbled across (I can't take any credit for it).

Create a file in /etc/udev/rules.d called 00-local-rules

Put this in the file:

```
KERNEL=="pcmC[D0-9cp]*", ACTION=="add", PROGRAM="/bin/sh -c 'K=%k; K=$${K#pcmC}; K=$${K%%D*}; echo defaults.ctl.card $$K > /etc/asound.conf; echo defaults.pcm.card $$K >>/etc/asound.conf'"
KERNEL=="pcmC[D0-9cp]*", ACTION=="remove", PROGRAM="/bin/sh -c 'echo defaults.ctl.card 0 > /etc/asound.conf; echo defaults.pcm.card 0 >>/etc/asound.conf'"
```


Et voila! If you plug in an external card, it immediately becomes the default. Works like a charm for me in Xubuntu 10.10 and Ubuntu 10.10. If the card has a mic, then that becomes default too.

---

