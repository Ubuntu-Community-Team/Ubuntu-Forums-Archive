---
title: "Need RealTek HD Audio for Ubuntu"
date: 2014-12-14
forum: Multimedia Software
---

### Post by Rick St. George on 2014-12-14
New Re-Build with AMD 8 core CPU, 16 GB Ram, Nvida GeForce 610 2GB video, 250 GB SSD, on MSI 990FXAGD65v2 mobo.

MSI only has RealTek files for Windows System - and nothing for Linux systems.

Is there not anything we can do about sound on this Mobo for Ubuntu?

If I run Windows in VitualBox, will I then be able to install the drivers in Win under a VM?


Any help will be appreciated.
Thanks
Rick

---

### Post by Yellow Pasque on 2014-12-14
You cannot use Windows sound drivers in Linux, nor should you need to. The drivers should be pre-installed (in the kernel).
I've got a similar system (AMD 890 chipset board) and the Realtek ALC892 has worked out of the box since Ubuntu 12.10.

If sound isn't working for you and you want to try a driver update, see: [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)
Also, give more info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by Rick St. George on 2014-12-15
My apologies. Apparently one should not forget to "plug it in". 
I failed to plug the audio cables back into the sub-woofer control box, after I had unplugged them to reroute behind the desk.
I do in fact have sound! Isn't Ubuntu great .... Goodbye Gates Monopoly ! ! ! 

Case closed.

---

