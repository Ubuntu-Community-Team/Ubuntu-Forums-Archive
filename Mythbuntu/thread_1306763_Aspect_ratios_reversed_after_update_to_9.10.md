---
title: "Aspect ratios reversed after update to 9.10"
date: 2009-10-30
forum: Mythbuntu
---

### Post by AKADAP on 2009-10-30
After updating my system to 9.10, and updating my ATI graphics driver to 9.10, myth TV now squeezes 16x9 content into a 4x3 window and stretches 4x3 content to fill a 16x9 screen.
Messing with the aspect ratio & zoom settings tweaks the aspect ratio a little bit, but it is not possible to get it correct for either 16x9 or 4x3 content.

---

### Post by AKADAP on 2009-10-30
I tried uninstalling the ATI 9.10 driver so I could go back to the version number free driver that came with the update. Unfortunately, after uninstalling the ATI 9.10 driver, I was left with a system that would boot to the monitor in sleep mode and a dead keyboard.

I was only able to recover by logging in via SSH and re-installing the ATI 9.10 driver.

---

### Post by AKADAP on 2009-11-05
My problem was that I had tried to install ATI's 9.10 driver from their web site. 
This version does NOT work with Ubuntu 9.10. Worse, it screws up your system making it very difficult to fix.
After many attempts I have finally gotten rid of the broken version, and have the version available from "Hardware Drivers" installed. Once this was done, MythTV started showing video correctly.

---

