---
title: "(SOLVED) 10.04 pvr-250, pvr-350 remote dont work"
date: 2010-05-07
forum: Mythbuntu
---

### Post by elgordo123 on 2010-05-07
I got lucky finding an answer to this.  My remote wouldn't work and I luckily found a post "lirc_dev" at 80%... post a couple pages back.  This was the same problem I had.  It is a known bug and here is where you go to fix it: 

[https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/550369](https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/550369)

It's probably low on the totem pole because there aren't many of us "SD" TV viewers out there... 

Thanks to Julian and Benjamin for the answers!

---

### Post by Don Giovanni on 2010-05-11
Just wanted to say thanks elgordo123 for posting this, as the one issue I had after the upgrade was that both my PVR-350 remote and custom built serial IR blaster no longer worked after the upgrade, I have been running off a cloned backup of my old 9.10 install until I could find a fix.

I'll try this tonight.

Thanks!

*update*
Confirmed working after installing the lirc and lirc-modules-source in lucid proposed as per above link.

---

