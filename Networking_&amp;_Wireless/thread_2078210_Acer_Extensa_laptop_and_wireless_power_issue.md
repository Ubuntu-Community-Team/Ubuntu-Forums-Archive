---
title: "Acer Extensa laptop and wireless power issue"
date: 2012-10-30
forum: Networking &amp; Wireless
---

### Post by dburns on 2012-10-30
Wondering if someone can help me with this. 

I installed 12.04 LTS on my Acer Extensa 5420 laptop.  It runs flawlessly except I cannot run on battery with the onboard Broadcom 4312 wlan card enabled, which kind of defeats the whole purpose of a laptop.

I can select the generic pae kernel ( recovery mode ) from the grub menu and I can get it to run fine with Unity in 2D mode but will not run in 3D....it freezes everything but the cursor. If I reboot with an ethernet cable for network access i can run in 3D mode on battery but the second I pull the ethernet and go to wireless it freezes up again. I have to reboot and go to Unity in 2D using the recovery mode kernel again.

The WLAN card works fine in Unity 3D mode on AC power so it has me stumped. I'm thinking it's a power management issue, but why does it work fine in 2D mode?

I reinstalled 12.04 with the same results and then upgraded to 12.10 hoping the 3.5 kernel might have resolved it, but no joy....same issue. Even purchased a new battery but no change.

Thanks for any help provided.

---

### Post by dburns on 2012-11-09
> **chili555 said:**
> Perfect!

With a temporary ethernet connection, please do:```
sudo apt-get  install --reinstall bcmwl-kernel-source
```After it's done,  do:```
sudo modprobe wl
```If there is no error or warning, your  wireless should be working.

Worked for my problem!

Thanks

---

