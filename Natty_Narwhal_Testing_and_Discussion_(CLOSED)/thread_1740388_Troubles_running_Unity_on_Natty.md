---
title: "Troubles running Unity on Natty"
date: 2011-04-27
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by csevcik on 2011-04-27
I'm having troubles upgrading from 10.10 to 11.04. So far I have upgraded 4 machines OK (some bugs as expected from a beta), but a 4th machine (Identical to one of the 3 mentioned above) an HP Pavillion All In One MS200 refuses to use the new Ubuntu desktop and defaults to Classic Ubuntu with a message stating that "the hardware does not support the Ubuntu mode", which works perfectly in the other identical machine. Both HP's have the same ATI drivers installed and are equally updated, the xorg.conf files seems identical too. The HPs have AMD 64 processors.

A similar message is produced by a 5th machine a Dell Precission 610 with two 2.4 MHz Xeon cores and and nVidia 173.14.30 driver and an NVIDIA GPU Quadro FX 500/FX 600 (NV34GL) agp graphic card.

I have 3 more machines to upgrade, Any suggestions on how to solve the problems with the 2nd HP and the Dell?

On the HP from Xorg.0.log I get:

**Adapter ATI Radeon HD 3200 Graphics has 2 configurable heads and 1 displays connected**

Still, its the same in both machines, both HPs are relatively recent, from the same file I get:

[B]Connected Display0: LVDS
Display0 EDID data
Manufacturer: HWP Model: 4105 Serial#: 257
Year: 2009 Week: 19[/B]

---

### Post by grahammechanical on 2011-04-27
You are looking for differences between the two machines. This is what I am thinking of.

Is there a BIOS setting that is different. In my motherboard BIOS there is a setting, Initiate Graphic Adapter [PEG/PCI]. Apparently PEG = PCI Express Graphics. So, if you have a PCI Express card this should be set to PEG/PCI and not PCI/PEG. Compare these settings on both machines. If you ahve them in your BIOS.

Is there a configuration utility for the graphic adapter? I have one for my Nvidia card and driver. Are there differences in the settings between the two computers.

What works on one machine should work on another machine if they have the same specification. Looks for differences in settings.

Regards.

---

