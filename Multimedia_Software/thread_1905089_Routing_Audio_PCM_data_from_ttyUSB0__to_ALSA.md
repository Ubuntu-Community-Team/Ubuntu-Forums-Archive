---
title: "Routing Audio PCM data from ttyUSB0  to ALSA"
date: 2012-01-06
forum: Multimedia Software
---

### Post by kishoreinme on 2012-01-06
Hello

I have a ttyUSB0 serial device which gives signed 16 bit PCM data at 8000 hz.  I am able to capture this data by  


cat /dev/ttyUSB0 > capture.raw 

in the terminal and play it using audacity.


How do I redirect the sound directly to an audio device using ALSA or any other mode?

---

