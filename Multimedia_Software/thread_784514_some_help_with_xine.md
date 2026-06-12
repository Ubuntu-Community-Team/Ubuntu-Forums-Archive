---
title: "some help with xine"
date: 2008-05-06
forum: Multimedia Software
---

### Post by netpumber on 2008-05-06
Hi every one ;) i have delete the audio.device.alsa_passthrough_device value by a fault in xine setup (audio tab) and i don't remember the old value of this. Is there any way to learn what it was before ? cauz now i cant listen music :P thanx in advance :)

i run this :
> 
cat ~/.xine/config | grep passthrough 


and it gives me back :

> audio.device.alsa_passthrough_device:
# offset for digital passthrough
#audio.synchronization.passthrough_offset:0

---

