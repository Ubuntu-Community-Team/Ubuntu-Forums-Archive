---
title: "XBVA GPU acceleration"
date: 2013-08-09
forum: Multimedia Software
---

### Post by mayagrafix on 2013-08-09
Was wondering if Hardware Acceleration has matured yet and/or will be available anytime soon, or is it still only experimental for ATI/AMD GPU's. This PC works great with the stock Ubuntu Gallium 0.4 drivers., and the one time I tried the proprietary drivers from ATI/AMD, I almost had a nervous breakdown. But I would be willing to try again if Hardware Acceleration is available.

Thanks for ur answers :KS

---

### Post by Mark Phelps on 2013-08-09
Hardware acceleration is, and has been, available for YEARS for a variety of ATI/AMD GPUs -- but AMD regularly discontinues Linux support, rendering older chipsets stuck with using open-source drivers.

It would help if you would tell us the make and model of the ATI/AMD video chipset on your PC.

---

### Post by papibe on 2013-08-09
Hi mayagrafix.

AMD cards offer video acceleration through the VAAPI library and not directly over XVBA.

In general you would need to:
[LIST]
[*]Have a relatively modern card.
[*]Install the proprietary driver.
[*]Install these two libraries:
[LIST]
[*]xvba-va-driver
[*]libva1
[/LIST]
[*]Use a player that supports acceleration using the VAAPI library (VLC for instance).
[/LIST]
Hope it helps.
Regards.

---

### Post by Yellow Pasque on 2013-08-10
The open-source driver is getting to the point where it does playback accel. I'm hoping it works out of the box on Ubuntu 13.10: [http://www.phoronix.com/scan.php?page=news_item&px=MTM1NDk](http://www.phoronix.com/scan.php?page=news_item&px=MTM1NDk)

---

