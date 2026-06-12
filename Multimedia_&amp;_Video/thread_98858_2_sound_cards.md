---
title: "2 sound cards"
date: 2005-12-04
forum: Multimedia &amp; Video
---

### Post by smsmith050 on 2005-12-04
I have an NFORCE3-250 chipset with on board sound. I would like to use a SoundBlaster for analog sound and the on board SPDIF out for digital sound. The on board sound works fine if the SoundBlaster is not installed. When the SoundBlaster is installed the on board sound stops working. 
I tried the 2 sound cards config:
[http://ubuntuforums.org/showthread.php?t=27186&highlight=sound+cards](http://ubuntuforums.org/showthread.php?t=27186&highlight=sound+cards)
but this did not work. When I look at lsmod it appears the on board sound modules don't load if the the SoundBlaster is in.

Has anyone got 2 sound cards working?

thanks
Steve

---

### Post by smsmith050 on 2005-12-04
I could not see the on board sound device from lspci. The Asus K8N BIOS was turning off the on board sound when I plugged in the sound blaster. 
I changed the on board AC97 codec setting in the BIOS from AUTO to ENABLE.
Now I have two sound cards working. 
Hope this helps someone.

Steve

---

