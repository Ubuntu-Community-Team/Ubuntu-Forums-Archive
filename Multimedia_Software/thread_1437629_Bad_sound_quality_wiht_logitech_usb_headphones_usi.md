---
title: "Bad sound quality wiht logitech usb headphones using snd_usb_audio"
date: 2010-03-24
forum: Multimedia Software
---

### Post by ulrichard on 2010-03-24
I have an acer aspire netbook with intel graphics. To get the graphics fully working I had to execute the script from the following page: 
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)

That broke the audio. 
So, I bought a cheap USB soundcard. I plugged it in, it was recognized and worked immediately. But the sound quality was horrible. 
Next, I bought some reasonably expensive Logitech USB headphones. They also immediately worked. The sound quality is a bit better, but still bad. 
One weird thing is that the audio quality improves with increasing CPU usage.
What is also interesting is that the sound quality is perfect with bluetooth headphones.

So the jitter really seems to be associated with snd_usb_audio somehow. But I have no idea what to do about.

---

### Post by ulrichard on 2010-06-10
It had to do with the speed step power changes propagated to the USB, I guess. When I compiled something, ran some computer vision or otherwise made sure the CPU is at 100% load the sound was good. But as soon as the CPU load droped below say 50% usage, the sound became bad.
Now I put a powered USB hub in between, and the sound quality is good also with low CPU load. So, it has nothing to do with Ubuntu, but the Acer hardware design. Maybe a capacitor more in the Logitec headset would have been enough as well...

---

