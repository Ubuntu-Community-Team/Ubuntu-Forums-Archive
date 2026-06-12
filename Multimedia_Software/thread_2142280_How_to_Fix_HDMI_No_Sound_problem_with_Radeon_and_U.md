---
title: "How to Fix HDMI No Sound problem with Radeon and Ubuntu 13.04"
date: 2013-05-05
forum: Multimedia Software
---

### Post by Sparkythepenguin on 2013-05-05
I had upgraded to Ubuntu 13.04 and amongst other problems, i had no sound from HDMI output. It didn't even see it in sound settings! So what to do? Some research found that **updating to the 3.8.8 kernel worked** along with making sure you have **propietary drivers for Radeon**, *13.4 version will do*, manually installed in terminal of course. then reboot, pop back into sound settings and select HDMI Cypress for the 5800 sound card for instance.

Updating to 3.8.8 also avoids compiz breaking. **DO NOT UPGRADE to 3.9 kernel!** not only will that likely break your compiz with radeon, you will be unable to fix it without a total reinstall of Ubuntu. I promise this is true.

So use the 3.8.8 kernel.

You will have to research this fix on google, it will tell all. Its to lengthy to put it all here but this will put you in the right direction for it. Either wait for the next kernal update, or use this fix if you simply can't wait, much like myself.

If you have any questions, message me, then i will happily give more Detail. :guitar:

Sincerely,

Sparky the Penguin.

---

### Post by markMDW on 2013-05-20
Ubuntu 13.04 installation:  I have an Intel Next Unit of Computing (NUC) with Intel integrated graphics and an i3 processor.  No HDMI sound for me either.  I'm going to Ubuntu 12.04.2 LTS for my solution.

---

