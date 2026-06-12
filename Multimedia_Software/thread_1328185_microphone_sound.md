---
title: "microphone sound?"
date: 2009-11-16
forum: Multimedia Software
---

### Post by proevofanatik on 2009-11-16
is it possible to speak into a mic and hear it come through the speakers as i am speaking. like the equipment a dj uses at parties? if yes then how would i do that? i couldnt see any options in the sound mixers. im wanting to transform my pc into a karaoke machine and also use it to be a dj at parties.

---

### Post by davidgagne80 on 2010-05-11
Same issue here, I'm getting desperate, I had windows xp on an old computer, and I did that all the time, take my computer to a party and start the karaoke right away. Then that pc crashed, bought a new one with vista, no way to make the sound of my microphone come through the speakers... So I installed Ubuntu (Intrepid or Jaunty I don't remember) Everything was perfect again, worked like a charm... So well that I removed windows from my laptop.... And now, even since I upgraded to Karmic, and then to Lucid, it doesn't work anymore! 

I really don't know what to try anymore, I tried removing pulseaudio and using alsa/oss ... But still nothing. I don't want to go back to Jaunty, Lucid works very well for everything else!

---

### Post by Zorael on 2010-05-11
You may have better luck on the [ALSA user mailing list](https://lists.sourceforge.net/lists/listinfo/alsa-user).

It works on my netbook with an Intel HDA chipset. In alsamixer Mic is listed as an output channel, so if I unmute it and raise its volume (and enable capture from the Mic input channel), it passes through sound from the mic to the speakers. I guess it varies from driver to driver (and model to model).

edit: This is on Kubuntu lucid, not using PulseAudio.
```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

See attached screenshot.

---

### Post by davidgagne80 on 2010-05-11
I also have an intel HDA chip and it doesn't work, thanks for the tip I'll take a look at that mailing list! 

This is what I get with aplay-l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

