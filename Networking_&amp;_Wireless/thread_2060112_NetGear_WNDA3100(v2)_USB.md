---
title: "NetGear WNDA3100(v2) USB?"
date: 2012-09-19
forum: Networking &amp; Wireless
---

### Post by Cam! on 2012-09-19
I had to get a USB WiFi adapter due to a new router, and it won't work on my 64-bit 12.04 installation.

I know that I have to get the drivers from within Windows and do something with "ndiswrappers", but I'm not sure the exact method. I tried doing it on Linux Mint to no avail.

---

### Post by Cam! on 2012-09-19
Nothing?

---

### Post by Joseph Rinaldi on 2012-10-24
Hi,
I spent hours on this but found a simply way to get this working flawlessly.
1. From the Ubuntu Software Centre, install Windows Wireless Drivers (NDISWrapper) and the two add-ons, [FONT=Calibri]ndiswrapper-dkms and ndiswrapper-source.[/FONT]
[FONT=Calibri]2. I installed the latest drivers from Netgear on a Windows XP computer. (Just a VM will do, can be on a Linux Box). You may need to install the 64 bit version.[/FONT]
[FONT=Calibri]3. This creates a folder in C:\Program Files\NETGEAR\WNDA3100v2\Driver, called WinXP2000. This contains the latest drivers for this adapter. The .sys file should be version 5.100.68.46.[/FONT]
[FONT=Calibri]4. Copy the folder to your Ubuntu (or Xubuntu) computer.[/FONT]
[FONT=Calibri]5. Run the Windows Wireless Drivers software and point to the inf file in this folder.[/FONT]
[FONT=Calibri]6. Reboot. All done![/FONT]

---

