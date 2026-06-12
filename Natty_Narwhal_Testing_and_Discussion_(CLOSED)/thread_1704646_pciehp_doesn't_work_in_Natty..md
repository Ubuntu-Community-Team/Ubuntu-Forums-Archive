---
title: "pciehp doesn't work in Natty."
date: 2011-03-10
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by darkshadow on 2011-03-10
I have always had to add pciehp.pciehp_force=1 to my kernel options to make my card reader work when hot plugging and not just when in during boot. But it seams to have stopped working in Natty.

Does anyone know a fix?

I also think but not sure it is why I have to use nvidia-settings to turn on hdmi compared to all old Ubuntu versions that it would work by just plugging it in then cycling to it with fn+f5

---

### Post by darkshadow on 2011-03-26
I found a way to get it working but it sucks since it is not automatic (you have to manually do it once per boot after card is inserted) and requires root permissions.


To get the system to see the hot-plugged device after it is inserted run the following command. Only needed once per boot.

echo 1 | sudo tee /sys/bus/pci/rescan

---

