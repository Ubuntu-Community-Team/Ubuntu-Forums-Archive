---
title: "getting reduced resolution than available at startup"
date: 2009-10-10
forum: Multimedia Software
---

### Post by rakusson on 2009-10-10
hi,

I have Lenovo Thinkpad Sl-300 with Intel® GM45 Express Chipset with Ubuntu 9.04 (Jaunty). I get resolution of only 1024 x 768 at startup thus leaving empty space on both side of my monitor. My computer supports 1280 x 800 resolution and I want it. How do I solve this issue?

---

### Post by mikewhatever on 2009-10-10
And the graphics card is ...???

---

### Post by rakusson on 2009-10-10
> **mikewhatever said:**
> And the graphics card is ...???

sorry, forget to mention that...it is **Intel GMA X4500HD**

One strange thing is that it does not happen everytime but like once in three startup. I have also included the log file Xorg.0.log & xorg.conf of the normal state when I have resolution of 1280 x 800.

---

### Post by mikewhatever on 2009-10-11
Can you change to the correct resolution under System->Preferences->Display?

---

### Post by rakusson on 2009-10-12
> **mikewhatever said:**
> Can you change to the correct resolution under System->Preferences->Display?
Actually, previously, I used to get only that reduced display resolution option under System->preferences->Dsiplay and I had to reboot and hope to get normal resolution of 1280 x 800. However, after using **xrandr** command I get the option to change to higher resolution. 

I have included the Xorg.0.log & xrandr output when I get reduced resolution leaving a margin of black space on both side of my monitor.

---

