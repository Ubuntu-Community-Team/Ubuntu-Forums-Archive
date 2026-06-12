---
title: "Wireless trouble with the Realtek Chipset ..please help !"
date: 2010-09-01
forum: Networking &amp; Wireless
---

### Post by folglaive on 2010-09-01
Hello everyone ,

I'm not super-good at english so please forgive in advance my poor mastership of the language :)

here is the thing : I'm trying for days to connect lucid lynx 10.04 to the internet .
It will not because i have the famous Realtek RTL8192SU chipset on my usb wifi .
So i tried and tried many solutions and none worked .I tested this one : [http://samiux.blogspot.com/2010/05/howt](http://samiux.blogspot.com/2010/05/howt) … ongle.html

But after having found the right driver and all ,sudo make install and >>no such file or directory .i tried to apply many changes on this thing and none worked too .

I tried this thing too :  [http://ubuntuforums.org/showthread.php?t=1491058](http://ubuntuforums.org/showthread.php?t=1491058)

But i don't know for you but i don't have windows wireless drivers in system-admin …

I tried ndiswrapper and ndisgtk ,nothing .I tried WIcd ..nothing .

So i 'm here with my problem and i hope that you will be able to help me !

When i type iwconfig :

quentin@quentin-desktop:~$ iwconfig&#8232;lo* * * * no wireless extensions.&#8232;&#8232;eth0* * * no wireless extensions.&#8232;&#8232;quentin@quentin-desktop:~$ &#8232;&#8232;&#8232;And  lspci :

&#8232;quentin@quentin-desktop:~$ lspci&#8232;00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge&#8232;00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)&#8232;00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)&#8232;00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)&#8232;00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)&#8232;00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]&#8232;00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller&#8232;00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller&#8232;00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller&#8232;00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller&#8232;00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller&#8232;00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller&#8232;00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)&#8232;00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller&#8232;00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)&#8232;00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller&#8232;00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge&#8232;00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller&#8232;00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration&#8232;00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map&#8232;00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller&#8232;00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control&#8232;00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control&#8232;01:05.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3200 Graphics&#8232;01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller&#8232;02:00.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3870&#8232;02:00.1 Audio device: ATI Technologies Inc Radeon HD 3870 Audio device&#8232;03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)&#8232;04:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller&#8232;quentin@quentin-desktop:~$ &#8232;&#8232;&#8232;

---

### Post by folglaive on 2010-09-02
Please ..This topic is going to sink on ubuntu fr too ..:(

---

