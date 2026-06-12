---
title: "Recording via ethernet connection"
date: 2015-01-25
forum: Multimedia Software
---

### Post by Autodave on 2015-01-25
We have a new sound board at out church that has an ethernet output for outputting sound from the board to a PC.  What do I need to do / download for Linux to recognize an ethernet audio input?

---

### Post by Autodave on 2015-01-25
Reading further in the manual, it states that it also has USB output for recording.  Anyone know how I would input that to Linux?

---

### Post by Dennis N on 2015-01-25
> **Autodave said:**
> Reading further in the manual, it states that it also has USB output for recording.  Anyone know how I would input that to Linux?

I would get a USB to mini stereo adapter. The adapter (with an additional cable) will be connected to the computer line-in for recording.

Example product: This one does mini-usb to 3.5 mm mini-stereo. If standard usb, get another adapter cable. You also need an male-to-male mini-usb cable to go from this to the computer line-in.

[http://www.amazon.com/95554-Stereo-Adapter-Mini-3-5mm/dp/B0022NHQ9Q](http://www.amazon.com/95554-Stereo-Adapter-Mini-3-5mm/dp/B0022NHQ9Q)

---

### Post by Autodave on 2015-01-25
Thanks for the reply.  I had thought of that, but supposedly you can USB direct into the PC.  I was wondering if there is a program for allowing me to do that.

---

### Post by SeijiSensei on 2015-01-25
The drivers for USB audio are part of the basic Advanced Linux Sound Architecture (ALSA) which Ubuntu uses via a presentation layer called PulseAudio.  Try installing **pavucontrol**, then connect the sound device.  Now run the pavucontrol application itself.  If you're lucky you'll see the sound device as one of the input channels.

---

### Post by Autodave on 2015-01-27
I will try that: THANKS!  I may be back again with more questions though. :-)

---

