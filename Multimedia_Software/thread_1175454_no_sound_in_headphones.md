---
title: "no sound in headphones?"
date: 2009-06-01
forum: Multimedia Software
---

### Post by rashby3 on 2009-06-01
I have a laptop running Ubuntu 8.04.

The built-in speakers work, but when I plug in a headset I get no sound. (The microphone does work. The headphones do not.) The same headset works fine in a Windows Vista desktop.

Can this be a software problem?

(I run ONLY Ubuntu on this laptop, so I cannot boot Windows on it to see if the headset works in Windows.)

If it can be a software problem, please suggest an approach to solving it.

Thanks very much.

---

### Post by madverb on 2009-06-01
Is the volume turned up for the headphone out?

---

### Post by rashby3 on 2009-06-01
> **madverb said:**
> Is the volume turned up for the headphone out?

I don't see any physical button/switch on the laptop that does this.

Is that done in software? I cant find anything in the application or system menus that does that.

The volume on the headset itself is all the way up.

Thanks.

---

### Post by madverb on 2009-06-01
Right click Speaker icon and select Open Volume Control

---

### Post by rashby3 on 2009-06-01
> **madverb said:**
> Right click Speaker icon and select Open Volume Control

Thank you.

Volume control just has a switch (checkbox) for headphones. No sound is heard in headphones whether box is checked or unchecked. (For everything with a volume control, I turned them all up to max.)

Thanks.

---

### Post by rashby3 on 2009-06-01
This is what I get from "aplay -l"

card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Everything seems to work fine, sound-wise, except for headphones. Only result from plugging in headphone jack is to mute the built-in speakers. Could this be a driver problem?

Thanks.

---

### Post by rashby3 on 2009-06-02
I believe this is actually an ALC883 problem. I found references to the same headphone problem elsewhere.

---

