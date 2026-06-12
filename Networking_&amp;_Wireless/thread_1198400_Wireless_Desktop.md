---
title: "Wireless Desktop"
date: 2009-06-27
forum: Networking &amp; Wireless
---

### Post by gedumer on 2009-06-27
Ubuntu 8.04

I have a desktop with a wireless card installed. Ubuntu indicated it didn't have proper drivers to support it. I purchased a new card and installed it. Ubuntu doesn't seem to see it. Is there something I need to do for Ubuntu to see it? Do I have to install some software to look for a wireless network? I'm sort of lost with this problem.

Please help?

---

### Post by mhgsys on 2009-06-27
could you open up a terminal and post the outcome of:

```

lspci

```

---

### Post by gedumer on 2009-06-28
Sorry for the delay...

```
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation 82915G Integrated Graphics Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)

```

I hope this helps.

BTW... The devise is: Linksys Wireless G USB Network Adapter W/ Speed Booster Model WUSB54GSC

---

### Post by mhgsys on 2009-06-28
Ah, it's a usb device.. that's why it's not showing with lspci.
My bad.


you'll find it with;

```

lsusb

```

However; 
A quick google search showed me more people with this card have not luck with it on linux.
Maybe other people know more about this then me;

I wish you good luck.


[http://www.google.nl/search?hl=nl&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aunofficial&hs=IJh&q=Linksys+Wireless+G+USB+Network+Adapter+W%2F+SpeedBooster+Model+WUSB54GSC+ubuntu&btnG=Zoeken&meta=](http://www.google.nl/search?hl=nl&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aunofficial&hs=IJh&q=Linksys+Wireless+G+USB+Network+Adapter+W%2F+SpeedBooster+Model+WUSB54GSC+ubuntu&btnG=Zoeken&meta=)

---

