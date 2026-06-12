---
title: "Issues with xorg.conf getting reverted"
date: 2013-01-20
forum: Multimedia Software
---

### Post by jba6511 on 2013-01-20
I upgraded to Ubuntu 12.04 recently and have noticed that my resolution is getting automatically changed when launching some apps like thunderbird. It does not happen all of the time and simply copying the old xorg.cong backup file to xorg.conf and restarting X temporarily resolves the issue. However, I would to fix this so that a restart of X is no longer needed. I am running dual acer monitors with a nvidia geforce 8600 GT card. One of the monitors is attached to a KVM via VGA and the other is attached directly to the system. I did not have this issue in 11.10 with the exact same setup. Any thoughts on where to begin troubleshooting?


$ lspci -v | grep -i "nvidia"
01:00.0 VGA compatible controller: NVIDIA Corporation G84 [GeForce 8600 GT] (rev a1) (prog-if 00 [VGA controller])
	Kernel driver in use: nvidia
	Kernel modules: nvidia_current, nouveau, nvidiafb

---

