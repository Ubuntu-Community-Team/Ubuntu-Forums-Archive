---
title: "HVR-1600 won't work after reboot"
date: 2008-10-07
forum: Mythbuntu
---

### Post by agent211 on 2008-10-07
I've had pretty good success getting the 1600 working, however there's one issue that is still eluding me:

When I reboot the machine, the MPEG2 decoder part of the card will fail to open unless I stop the backend, disable and re-enable the driver then start the backend back up.

Has anyone seen anything like this, or have any ideas how to fix it?

Mark

Mythbuntu 8.04
Athlon 3700+
ECS 755-a2
2GB RAM
160GB HDD
Hauppauge HVR-1600

---

### Post by ian dobson on 2008-10-07
Hi,

Sounds like a firmware loading problem. Maybe you can just automate the unloading/reloading of the driver.

It could also be a BIOS bug that's not reinitalising the card on reboot. I can remember something in the ivtv drivers with the firmware not loading on reboot.

Regards
Ian Dobson

---

### Post by agent211 on 2008-10-07
Thanks Ian,

I had a feeling it might be something like that.  I've been looking for ways to automate the button click I'm doing, but being linux literate but a Mythtv noob, I'm not having luck in my search.  Can you point me in the direction of the script I need?

I'll check out the potential BIOS issue, but the card comes up with the non-MPG2 side ok.  It's worth a look.  

Mark

---

