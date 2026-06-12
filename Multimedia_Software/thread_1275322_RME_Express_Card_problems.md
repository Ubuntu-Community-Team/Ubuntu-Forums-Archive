---
title: "RME Express Card problems"
date: 2009-09-25
forum: Multimedia Software
---

### Post by mjertin on 2009-09-25
Hi!

I have a weird problem with my new ExpressCard. Maybe someone can help me with this?

My setup:
RME HDSPe ExpressCard
RME Multiface I
Lenovo T400, 3.7 GiB Memory, 2x 2,4 GHz
Ubuntu 9.04 (amd64)

Everytime I plug in my ExpressCard and run "dmesg" I get the following:
```

[  266.618504] pciehp 0000:00:1c.3:pcie02: Card not present on Slot(3)
[  266.631059] pciehp 0000:00:1c.3:pcie02: Card present on Slot(3)
[  266.739662] pciehp 0000:00:1c.3:pcie02: Card not present on Slot(3)
[  266.752186] pciehp 0000:00:1c.3:pcie02: Card present on Slot(3)

...this goes on for a while... and finally:

[  270.356596] pciehp 0000:00:1c.3:pcie02: No new device found
[  270.356603] pciehp 0000:00:1c.3:pcie02: Cannot add device at 0000:05:00

...and then again like above...

```
It doesn't affect the result whether I hotplug it or plug it in before I launch the laptop.

Has anyone else experienced something like this? Any suggestions?

Thank you very much!

Martin

---

### Post by mjertin on 2009-10-04
bump

---

