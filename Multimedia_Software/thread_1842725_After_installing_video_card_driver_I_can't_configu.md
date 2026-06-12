---
title: "After installing video card driver I can't configure multiple monitors..."
date: 2011-09-12
forum: Multimedia Software
---

### Post by shnura on 2011-09-12
Hi there,
I've just started using Ubuntu 10.04. and I have this strange problem.


 In windows I use 2 monitors - the main laptop display and Samsung Sync Master. My computer is Asus x73sl.


 When I boot Ubuntu, both monitors are working, but in very low  resolution and only in mirror mode. After I install the nVidia driver,  suggested by Ubuntu, and restart the machine, my laptop screen  resolution becomes significantly higher and I can use the full visual  effects option. But I'm not able to use the second monitor anymore.


 NVIDIA X Server seems to refuse to apply and save any change I try to  make in the settings. In X Server Display Configuration I'm able to set  the second monitor properly, but when I try to apply the changes, an  error message appears. When I try to save  the changes to the X  Configuration File (and restart the program and/or the computer), no  changes take place at all.


 Here's what NVIDIA X Server Settings says about the Graphics Card Information:
 Graphics Processor: GeForce 9300M GS
VBIOS Version: 62.98.3c.00.54
Memory: 512 MB
Bus Type: PCI Express x16
Bus ID: ?@?:?:?
PCI Device ID: Unknown
PCI Vendor ID: Unknown
IRQ: 16
X Screens: Screen 0
Display Devices: LGD (DFP-0), Samsung SyncMaster (CRT-0)


Do you guys have any idea what the problem might be and how could I possibly solve it?


Thank you in advance!


Best regards,
Svetlin Kolev

---

### Post by realzippy on 2011-09-12
Can you post your xorg.conf file?

---

### Post by shnura on 2011-09-12
I apologize if I sound profane, but where should I look for this file and how to post it here? :sad:

:( I feel like a noob... ](*,) Damn, all these years using Windows have obviously made an absolute idiot out of me... :cry: :cry: :cry:

---

### Post by realzippy on 2011-09-12
open terminal,run
```
gedit /etc/X11/xorg.conf
```

---

