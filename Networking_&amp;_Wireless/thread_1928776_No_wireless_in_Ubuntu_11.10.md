---
title: "No wireless in Ubuntu 11.10"
date: 2012-02-20
forum: Networking &amp; Wireless
---

### Post by RyonMS on 2012-02-20
Over the weekend I replaced Windows Vista on my Gateway M-1617 laptop with Ubuntu 11.10 64-bit. Everything went smoothly until I tried to set up my wireless network. It appears Ubuntu doesn't recognize that I have a wireless card inside my laptop. I tried many different tutorials but none helped. If anyone could offer assistance to me on this problem it would be really appreciated. (Sorry if this is something simple I know almost nothing about Ubuntu or Linux)

---

### Post by Lisiano on 2012-02-20
Could you please give us some more information? To be more precise, open a terminal (Ctrl+Alt+T) and type the following ```
lspci
```

---

### Post by RyonMS on 2012-02-20
Yeah one sec im on a different computer

---

### Post by RyonMS on 2012-02-20
ryon@RyonUbuntu:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
01:05.2 Audio device: ATI Technologies Inc Radeon X1200 Series Audio Controller
08:00.0 Ethernet controller: Marvell Technology Group Ltd. 88W8362e [TopDog] 802.11a/b/g/n Wireless (rev 03)
0e:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
ryon@RyonUbuntu:~$

---

### Post by Lisiano on 2012-02-20
Your WiFi adapter chipset is a Marvell 88W8362e, sadly there seems to be no native Linux support for it (as far as I see), still try to go to the Dash (Press Super/Windows key or the Ubuntu logo in the launcher at the top) and find Additional Drivers. Maybe I'm mistaking and there is one for it. If I'm not mistaking, you will have to play with ndiswrapper, sadly I can't help with that as I have never set it up due to using Linux friendly adapters. Try googling and searching around the forum, in short you will need the Windows driver for your WiFi adapter and you are going to tell ndiswrapper to use it, I don't know how though. A good place to start is Google.

---

### Post by RyonMS on 2012-02-20
I tried looking for additional drivers but nothing showed up, bu thanks for your help.

---

### Post by Lisiano on 2012-02-20
Ignore Google, found a guide [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
Don't be afraid to ask for help on this thread if you don't understand a certain step, don't forget to mention what step you mean.

EDIT: Though I won't be able to respond, going to bed as it's almost 1:52 in the morning.

---

### Post by RyonMS on 2012-02-20
Thanks a lot you have been very helpful.

---

