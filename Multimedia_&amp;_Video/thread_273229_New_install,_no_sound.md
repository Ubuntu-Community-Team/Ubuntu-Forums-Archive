---
title: "New install, no sound"
date: 2006-10-07
forum: Multimedia &amp; Video
---

### Post by maccam94 on 2006-10-07
I'm trying to configure Ubuntu to use my onboard SiS Si7012 sound chip, but even though it detects the chip and loads the driver. Previously there was also a Sound Blaster X-Fi in it too, but there's no Linux support and I never tried to get it to work. After the install process I went about trying to get the onboard sound to work, and ended up just removing the X-Fi to make sure it wasn't making issues. Still no sound, mixer levels look OK, intel8x0 is loaded. When I kill ESD and restart it, it doesn't let go of the terminal and it leaves:

```
$ esd
Audio device open for 44.1Khz, stereo, 16bit failed
Trying 44.1Khz, 8bit stereo.
Audio device open for 44.1Khz, stereo, 8bit failed
Trying 48Khz, 16bit stereo.
```

I've tried several configuration file changes to try and fix things, but I'm afraid that maybe they're just causing more problems now that they're there instead of fixing them. Is there any way to reset or remove any conf file that alsa or esd would pay attention to?

---

