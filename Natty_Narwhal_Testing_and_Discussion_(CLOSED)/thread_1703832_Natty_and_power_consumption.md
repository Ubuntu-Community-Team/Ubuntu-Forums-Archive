---
title: "Natty and power consumption"
date: 2011-03-09
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by joffe on 2011-03-09
I have been struggling with getting my notebook's battery last longer and finally gotten around to beat even Windows' power estimates. Now my question is: what are the devs doing to improve battery life out of the box? I couldn't find anything else than PowerNAP on the blueprints page.

In order to go down from 30 Watts to 8 Watts power consumption I had to do this:

1. Add the line osi_acpi=Linux to the grub default command line.

2. Turn of the unused Radeon 5650 card through vga_switcheroo.

3. Tweak the values in PowerTOP as seen in the second screenshot.





Now that's more like it! With these settings and the backlight set just a little lower it means I can get ~8 hours (instead of 2) of light work done on my machine:

---

