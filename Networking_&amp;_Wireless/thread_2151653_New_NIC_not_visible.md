---
title: "New NIC not visible"
date: 2013-06-05
forum: Networking &amp; Wireless
---

### Post by Bruno von Troba on 2013-06-05
Problem: Can't add new NIC Card
Ubuntu: 12.04 LTS x64 server
MB: Intel with Intel Core2Duo
After fresh installation of 12.04 system can see all installed NIC (ex. RTL8139 and marvel)
When i try to install a new NIC (RTL8168) it cannot be seen (persistent-net.rules is not changed, NIC is not visible on lspci list)
udevadm trigger --action=add changes nothing
Tryed to install original drivers from REALTEK site - fails to recognize NIC
The only way to install NIC is reinstall the system with NIC already inserted in PCIe slot. In this case i can add next NIC of the same kind.

Tryed also on another, different machines - AMD FX with AMD Chipset (2 different), tryed to add marvell based NIC - with the same result

Strange thing - USB NIC can be discovered properly and adds to persistent-net.rules after udevadm trigger

This is problem since 12.04 LTS, 10.04 LTS works fine

Any suggestions?

EDIT:
Just added next RTL8139 NIC - did not show automaticaly in persistent-net.rules, have had to use "udevadm trigger --action=add" to add it

---

### Post by praseodym on 2013-06-05
BIOS-reset after adding the new NIC?

---

### Post by Bruno von Troba on 2013-06-06
> **praseodym said:**
> BIOS-reset after adding the new NIC?

Please be serious...
As I mentioned before, in 10.04 version with THE SAME NICs everything works fine, adding 6 new different NICs after installation is just a plug...

---

### Post by praseodym on 2013-06-07
Try:
```

sudo udevadm trigger
sudo service udev reload
sudo service udev restart
```

---

