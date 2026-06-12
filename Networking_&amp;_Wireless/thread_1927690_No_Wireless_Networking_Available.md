---
title: "No Wireless Networking Available"
date: 2012-02-18
forum: Networking &amp; Wireless
---

### Post by RyonMS on 2012-02-18
I just decided to install Ubuntu 11.10 onto my Gateway M-1617 laptop last night and everything went fine until it came to setting up my WiFi. I have tried everything but it appears Ubuntu isn't recognizing the card at all or I'm missing a driver. I went to the networking tab in system settings and there isn't even a wireless tab. If you could offer any help for this problem that would be great since I'm new to Ubuntu and don't know what I'm doing.

---

### Post by ajgreeny on 2012-02-18
First thing to do is connect with a wired connection for this one time, then run ```
sudo apt-get update
sudo apt-get upgrade
```then see if any drivers are made available in the additional drivers dialog (not sure where that is in 11.10)

That may be all that is needed, but if still not connecting wirelessly, show us the output of ```
lspci
``` in terminal.

---

### Post by RyonMS on 2012-02-18
Sorry for delayed reply, I went paintballing and have been gone all day. I tried updating and upgrading but nothing, I'll copy and paste the results in a second.(I'm on a Mac right now, not my laptop)

---

### Post by RyonMS on 2012-02-18
Results for lspci:

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
ryon@RyonUbuntu:~$ sudo apt-get remove bcmwl-kernel-source

---

### Post by RyonMS on 2012-02-20
Anyone else got any ideas on how to fix this problem?

---

