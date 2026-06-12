---
title: "lost sound (snd_hda_intel) after hibernate"
date: 2007-06-29
forum: Multimedia &amp; Video
---

### Post by fedutov on 2007-06-29
Hello!

Source: Laptop Asus w3j drived by Ubuntu Fiesty, with all updates and upgrades. 

After regular boot sound works fine, using snd_hda_intel. After hibernate i get no sound and muted channels in the mixer. After unmute them - no sound again. But all media players thinks all fine.  

Also i tried various things, like adding string  "snd_hda_intel snd_hda_codec" to /etc/default/acpi-support into MODULES and MODULES_WHITELIST variables, still no effect. 

Commands rmmod snd_hda_intel or snd_hda_codec is not working, they shown result error "module is in use". 

Restarting alsa_utils takes no effect. 

Please help! :)

---

