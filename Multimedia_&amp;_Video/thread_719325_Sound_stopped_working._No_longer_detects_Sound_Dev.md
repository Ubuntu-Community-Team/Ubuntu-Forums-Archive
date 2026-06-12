---
title: "Sound stopped working. No longer detects Sound Devices"
date: 2008-03-09
forum: Multimedia &amp; Video
---

### Post by Omni-X on 2008-03-09
I was trying to get my mic to work, and I happened upon the Sound Trouble-shooting page. I followed some suggestions on the page to see if everything was working, but once I got to the part where it said to find my driver on the ALSA page, things started to go wrong. I found the driver I needed, but when I tried to install it, my sound completely stopped working, and now it no longer detects my sound devices. I tried following the support page again, but it still is not working. It is getting really aggravating not being able to hear my music. Can I just roll back to previous settings without having to reinstall ubuntu? (The guide helped me, but when I get to modprobe snd-via82xx command, I get an error message.)
```
# modprobe snd-via82xx
WARNING: Error inserting snd_ac97_codec (/lib/modules/2.6.22-14-generic/updates/alsa/pci/ac97/snd-ac97-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_ac97_codec (/lib/modules/2.6.22-14-generic/updates/alsa/pci/ac97/snd-ac97-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_via82xx (/lib/modules/2.6.22-14-generic/updates/alsa/pci/snd-via82xx.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error running install command for snd_via82xx

```

---

### Post by Yellow Pasque on 2008-03-09
You could try this script to build ALSA 1.0.16 (It was originally for hda-intel, but I've modified to use the via82xx driver).

If that doesn't work, I would try reinstalling the alsa-base package in Synaptic.

If you reall get to the end of your rope, try the OSS4 howto in my sig before doing a complete reinstall.

---

