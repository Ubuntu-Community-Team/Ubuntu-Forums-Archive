---
title: "What is the Difference Between ALSA:hdmi, :hw: and :plughw"
date: 2013-06-24
forum: Mythbuntu
---

### Post by HDTimeshifter on 2013-06-24
I was setting up my audio and can get 5.1 sound through all of the below options, but don't know the difference:
ALSA:hdmi:CARD=NVidia, DEV=1
ALSA:hw:CARD=NVidia, DEV=7
ALSA:plughw:CARD=NVidia, DEV=7

---

### Post by newlinux on 2013-06-24
Not my area of expertise and others can correct me but, I believe hw will give you direct kernel access to the audio device with no layered on processing. plughw does add a layer of software processing that is sometimes necessary. Not sure about the first one, it would appear to reference a different device, but more than likely is actually the same physical output mapped to a different device. That's not uncommon with HDMI devices. I'd avoid using hw: wherever possible. For more info I'd need to know more about your hardware...

---

