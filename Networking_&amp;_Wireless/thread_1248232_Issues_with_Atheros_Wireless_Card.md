---
title: "Issues with Atheros Wireless Card"
date: 2009-08-23
forum: Networking &amp; Wireless
---

### Post by mlbizzle on 2009-08-23
Hi everyone,

I am very new to Ubuntu and have only used Netbook Remix 9.04 on 2 netbooks (on a Dell Mini 9 which worked flawlessly and a Sony VPC-W111XX/W which I am having minor issues with). The Sony has an **Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)** (supports wireless N and is fairly new I believe..). I installed linux-backports-modules-jaunty as I've read in other threads has fixed wireless issues with this card, and in part it has. 

My issue is this: when I go to connect to an encrypted network it just continually tries to connect but never establishes a connection. What do I need to do...? .. I am very new to this so I am not great with the terminal yet... 

Also, kind of weird, it shows me connect to an unsecure network in my panel but then when I connect it shows connection go to 0% (all white bars, even though it is in fact working). This is really annoying to me... I know it is minor but if anyone has a fix/is experiencing the same, I would appreciate any help!

lspci pulls this information:

michael@michael-netbook:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Attansic Technology Corp. Device 1062 (rev c0)
03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
0a:09.0 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
0a:09.1 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)

... Don't know if that helps? If not let me know what other info you may need! Thank you so much for any help, so far I love Ubuntu!!

---

