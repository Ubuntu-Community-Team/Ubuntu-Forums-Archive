---
title: "Problem with logitech E3500 and intrepid"
date: 2008-12-26
forum: Multimedia Software
---

### Post by mod-jkl on 2008-12-26
Hi,

I'm using this webcam with intrepid ibex and skype and have the following problem: it doesn't work all the time, sometime skype can use the webcam, sometime it doesn't...

is there something that can be done to solve this problem ?

Thanks for any help

ps: I already use LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

---

### Post by mod-jkl on 2008-12-26
Found the problem: this webcam has a micro, skype was configured to use the mic connected to the sound card. I configured skype to use the webcam mic (usb mic) and now it's ok, skype can use the webcam for video.

---

### Post by stuples on 2009-01-10
Would you be able to tell me how you did this, as I am having the same problem?

I am general having trouble getting the mic working.

---

### Post by mod-jkl on 2009-01-10
I had a microphone (not the E3500 mic) that was plugged to the soundcard. So there was 2 mics in the system, this one (soundcard) and the E3500 integrated mic.
I think that this was the problem because when I unplugged the first mic from the soundcard, the E3500 started to work fine (before that, it worked 50% of the time).

---

