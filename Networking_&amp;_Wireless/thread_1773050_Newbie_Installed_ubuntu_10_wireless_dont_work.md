---
title: "Newbie Installed ubuntu 10 wireless dont work"
date: 2011-06-01
forum: Networking &amp; Wireless
---

### Post by davequig on 2011-06-01
Hi,
Just did a full install of Ubuntu 10LTS the 64bit version on a HP Pavilion dv2.
netwoking enabled but i can't see my wireless connection
Can anyone help?

Thanks,
Dave

---

### Post by Pictor on 2011-06-01
Maybe you need to "Activate" the "Additional driver".
I have an HP laptop (it's a TouchSmart instead of a Pavillion) but I guess the chipset is from the same manufacter: Broadcom.

Broadcom didn't release opensource drivers, so these cannot be activated cause of the license type of their use.
So you have to manually specify you want to use the proprietary driver from Broadcom.

You can try to activate B43 driver or STA driver from the "Additional driver" tools, rachable by the top menu:

System->Administration->Additional drivers


I don't assure you that is the solution, but it could be.
Just try.

---

### Post by baarn on 2011-06-01
what does
```
lspci -v
```
output?
(try to find your wireless card and just post that section)

---

