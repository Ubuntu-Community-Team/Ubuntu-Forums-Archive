---
title: "How to set sound device system wide"
date: 2013-01-20
forum: Mythbuntu
---

### Post by Cerin on 2013-01-20
How do I set the default sound device to HDMI system wide?

I have Myth installed on a computer using an HDMI tv as a monitor. To get sound to work with Myth, I had to select the "ALSA:HDMI" device under settings. However, when I exit Myth, and try to run Pandora or a music player, I have no sound, and I can find no program to adjust the sound device.

---

### Post by nickrout on 2013-01-21
you need to write a file called /etc/asound.conf to set the default alsa sound device to the hdmi sound device. [http://alsa-project.org/main/index.php/Asoundrc](http://alsa-project.org/main/index.php/Asoundrc)

It will look something like this:

```
pcm.!default {
	type hw
	card 1
        device 3
}

ctl.!default {
	type hw           
	card 1
        device 3
}
```Where the numbers 1 and 3 depend on your hardware, alsa version, and the phase of the moon.

---

### Post by Cerin on 2013-01-21
> **nickrout said:**
> you need to write a file called /etc/asound.conf to set the default alsa sound device to the hdmi sound device. [http://alsa-project.org/main/index.php/Asoundrc](http://alsa-project.org/main/index.php/Asoundrc)

It will look something like this:

```
pcm.!default {
	type hw
	card 1
        device 3
}

ctl.!default {
	type hw           
	card 1
        device 3
}
```Where the numbers 1 and 3 depend on your hardware, alsa version, and the phase of the moon.

Thanks. That fixed it.

---

