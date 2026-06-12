---
title: "Question about 2 sound cards"
date: 2012-09-26
forum: Multimedia Software
---

### Post by tesla.coil on 2012-09-26
Hi,

I have 2 USB headsets connected to my pc and i see both of them when i do ```
cat /proc/asound/cards
``` ,i tested to see if both are working or not by running a ```
speaker-test
``` for both the cards.

What id like to do is,when i speak from the microphone on the first headset,id like the audio output to come from the secondary headset.Is it possible ? Do i need to create some sort of ALSA loop-back device for this ?

Thanks

---

