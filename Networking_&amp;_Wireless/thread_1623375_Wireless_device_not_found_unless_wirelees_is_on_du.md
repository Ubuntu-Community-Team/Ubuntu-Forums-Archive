---
title: "Wireless device not found unless wirelees is on during boot"
date: 2010-11-16
forum: Networking &amp; Wireless
---

### Post by oblidor on 2010-11-16
I first upgraded 10.04 to 10.10 and it worked fine with wireless. Then I needed to do a reinstall due to harddisk change, and now I have a problem with the wireless.

The problem is that if I leave the wireless device off while booting, then I cannot get it to work again. I mean the led light goes on, but no kernel modules are loaded and no wireless interface comes up. 

If I leave the wireless device on during boot, then everything works.

I have tested with both network-manager and wicd, and both fail.

If I run lspci when the wireless device is off during boot, I do not see it in the lspci output. If I activate the device I still do not see it. If the wireless is on during boot then I see it in lspci.

I have also tested kernel 2.6.37-020637rc2-generic, and it is the same problem there.

Question is, is this a kernel bug or is there some other program that fails?

Thanks in advance

System is Asus Eee 1000H, Ralink RT2860 wireless device

---

