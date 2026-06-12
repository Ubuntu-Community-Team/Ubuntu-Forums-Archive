---
title: "Wireless disabled."
date: 2010-08-11
forum: Networking &amp; Wireless
---

### Post by armandointer on 2010-08-11
Hello everyone,

I had Ubuntu 9.04 and upgraded to Ubuntu 9.10 and the wireless icon is there but there is it doesnt show any wireless available. Any solutions ? 

Thank you in advance

---

### Post by realzippy on 2010-08-11
Are there any drivers available in System/Administration/hardware drivers  ?


Which wlan card do you use?If you do not know,open [terminal]("https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/terminals.html"),type:

```
lspci
```

and post output here.

---

### Post by armandointer on 2010-08-11
Check screenshot please

[http://www.mypicx.com/uploadimg/335735215_08112010_1.png](http://www.mypicx.com/uploadimg/335735215_08112010_1.png)

---

### Post by realzippy on 2010-08-11
So have you tried to deactivate/reinstall the driver after upgrading?

Still do not know which (atheros) wlan adapter you are using....
...please run the above suggested command **lspci**

---

### Post by armandointer on 2010-08-11
this is what i get from lspci


00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
05:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
06:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

---

### Post by realzippy on 2010-08-11
Why did you enable the "madwifi" instead of the "ath5k" driver?

Try deactivating the madwife driver and enabling the other..

---

### Post by armandointer on 2010-08-11
Thank You. Solved

---

