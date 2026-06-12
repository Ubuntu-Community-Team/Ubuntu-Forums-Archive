---
title: "change fn+mute key corresponding mixer"
date: 2009-07-15
forum: Multimedia Software
---

### Post by scales on 2009-07-15
hi all.  i have an eee1000he and have installed eee-tray-tools.  my fn keys work however my fn+mute key just turns the PCM mixer way down to 0.  I would rather that fn+mute mutes the "LineOut" channel and toggle my "iSpeaker".  Does anyone know where i can change which mixer/channel my fn keys control or how to fix this?  i have only found the following...

> edit the /etc/acpi/mutebtn.sh so it contains:

#!/bin/bash

action= amixer set Front toggle

---

### Post by scales on 2009-07-15
well i have tried changing the contents of etc/acpi/mutebtn.sh so it reads:
> 
#!/bin/bash
action=amixer set LineOut toggle" "amixer set ${ALSA_MUTE_MIXER} toggle

but no luck :( any help?

---

