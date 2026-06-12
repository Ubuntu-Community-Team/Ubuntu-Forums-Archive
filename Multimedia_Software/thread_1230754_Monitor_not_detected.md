---
title: "Monitor not detected"
date: 2009-08-03
forum: Multimedia Software
---

### Post by tajreed on 2009-08-03
Using nvidia 180.44 with 9.04 does not detect my Acer monitor. Hence, resolutions are well off. I'm using a vga connection. On my other box with the dvi connection everything works perfectly.

Anyone have a solution for this issue?

Thanks

---

### Post by xc3RnbFO8P on 2009-08-03
Did you check System> preferences> Display, choose NO

---

### Post by Joherrer on 2009-08-03
My Nvidia GEForce 7300 doesn't work with my two monitors (ViweSonic E70f and Samsung Syncmaster 226BW).  No enough resolution neither two displays. 
It just shows same image on both.
What's wrong?
I have just installed UBuntu 9.04.

---

### Post by tajreed on 2009-08-04
Tried system/preferences/monitor----no. No luck

---

### Post by realzippy on 2009-08-04
nvidia-settings
do not work?

---

### Post by tajreed on 2009-08-04
Nvidia settings does not recognize the monitor. Therefore the resolutions are way off.

---

### Post by realzippy on 2009-08-04
..did you install the nvidiadriver with the ubuntu restricted driver tool?
what does:

**glxinfo**
say?

---

### Post by tajreed on 2009-08-06
The VGA cable that I was using was not allowing the monitor i.d info to the Nvidia driver. I switched cables and all is well. Had a new vga cable from a local vendor. But found the vga cable that came with the monitor. Don't know one worked and the other did not.

---

