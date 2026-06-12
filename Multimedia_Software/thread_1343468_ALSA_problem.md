---
title: "ALSA problem"
date: 2009-12-01
forum: Multimedia Software
---

### Post by varaahan on 2009-12-01
I ran the following commands:

sudo alsamixer
sudo alsactl store

This worked fine so long until I reboot.
When I reboot all controls except Master / Headphone / PCM are muted.
Everytime I have to r-run the above commands to have sound.
Please advice.

I have Ubuntu 9.10 Karmic Koala on Asus A8V-VM VIA board.

---

### Post by Ulysses361 on 2009-12-02
Hi,

Please try this workaround procedure:

1. Open Terminal from "Applications->Accessories->Terminal"

2. copy-paste the following command into the Terminal:

gksudo gedit /etc/init.d/alsa-utils

3. Replace the following line (which is line 372 in the /etc/init.d/alsa-utils file):

mute_and_zero_levels "$TARGET_CARD" || EXITSTATUS=1

with the following line:

# mute_and_zero_levels "$TARGET_CARD" || EXITSTATUS=1

So you need to comment out that line to prevent the script from muting your soundcard during boot.

4. Reboot and recheck mixer settings

Hope it helps,

Regards,

Mark

---

### Post by varaahan on 2009-12-03
That didn't help.
Again the controls remain muted.

Is ubuntu too restrictive ?

---

