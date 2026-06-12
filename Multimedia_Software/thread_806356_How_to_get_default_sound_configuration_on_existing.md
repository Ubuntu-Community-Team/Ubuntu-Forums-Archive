---
title: "How to get default sound configuration on existing installation."
date: 2008-05-24
forum: Multimedia Software
---

### Post by tiggerntatie on 2008-05-24
I have a PC with optical audio output on the motherboard, and it used to work beautifully under Gutsy (great 5.1 sound on DVDs, etc.). One day I was messing with the sound configuration and the sound stopped working. I have since upgraded to Hardy and still no sound. 

If I boot into windows, it works fine without any intervention. If I boot from the Hardy live CD, it also works fine, without having to set a thing! 

I tried to copy all the alsa mixer settings from what they are in the live CD boot, and it still doesn't work. I have followed the sticky advice for uninstalling (and purging) ALSA and re-installing to recover default settings, to no avail. Also tried wiping out .alsa stuff in the home folder. No good.. 

Are there any other tips for getting the sound system back into a virgin/default state on this installation? I really don't want to wipe the system and start over just for the sake of sweet sound.

.. figured this out finally: 

Boot into working live CD and execute ```
sudo alsactl store
```
save the generated file: /var/lib/alsa/asound.state

Boot into the non-working installation and copy the saved asound.state file to the same location as before. Then execute ```
alsactl restore
```
Reboot and all is fine.

---

### Post by tiggerntatie on 2008-05-25
added to original post..

---

