---
title: "Sound control not working"
date: 2017-04-04
forum: Multimedia Software
---

### Post by kim15 on 2017-04-04
I can turn the sound up and down on websites, but not on the machine itself.  I press the buttons on the keyboard and the bar moves, but the sound is still the same loudness.  How do I sync it back up? Like on youtube I can use the volume control on the video, but I want to computer itself to turn down.

[IMG]http://i1305.photobucket.com/albums/s548/NintenIsAwesome/volume_zpsnzlq6y8n.png[/IMG]

---

### Post by kim15 on 2017-04-05
Hello?  I posted this yesterday.  Can someone help?

Please?

---

### Post by aclitchfield on 2017-04-17
I'm actually having the same problem after upgrading to 17.04. Anyone know what's going on?

---

### Post by dejitarob on 2017-04-18
> **aclitchfield said:**
> I'm actually having the same problem after upgrading to 17.04. Anyone know what's going on?
Same problem here as well.

---

### Post by dejitarob on 2017-04-18
This fixed it for me:
```
pulseaudio -k; rm -r ~/.config/pulse/*
``` 
If needed wait ten seconds then do another [FONT=courier new]pulseaudio -k[/FONT]

---

