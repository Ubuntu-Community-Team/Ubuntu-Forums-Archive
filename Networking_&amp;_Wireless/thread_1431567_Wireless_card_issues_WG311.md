---
title: "Wireless card issues WG311"
date: 2010-03-16
forum: Networking &amp; Wireless
---

### Post by thundaraptor on 2010-03-16
I have followed a few different internet recipes to get this to work but I feel I am stuck.  I have used a 64bit ndiswrapper that I have installed with the gui and I think it is installed correctly.  Some command line output below should clear up what I have done but as I am pretty much and idiot, i can't figure out what to do next.  little help please thanks.

```
xxxx:~$ lpsci
No command 'lpsci' found, did you mean:
 Command 'lspci' from package 'pciutils' (main)
lpsci: command not found
xxxx:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: ASUSTeK Computer Inc. Device 9602
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon 3100 Graphics
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
03:06.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
xxxx-desktop:~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
wg311v3 : driver installed
	device (11AB:1FAA) present
xxxx-desktop:~$ sudo modprobe ndiswrapper
[sudo] password for blackness64: 
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
xxxx-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

xxxx-desktop:~$ sudo modprobe ndiswrapper
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
xxxx-desktop:~$ 


```

---

### Post by draperdt on 2010-03-16
Yeah, I have the same card still in my box with a 64bit and I have not been able to get it to work. I would like a real confirmation from someone who had it working. There is a tar with required windows drivers files floating around in the forums which some say is a working solution with ndiswrapper, but I cant get it to work.

---

### Post by thundaraptor on 2010-03-16
i like ubuntu but between not being able to make the simplest things work, like this, my ipod and pretty much anything else that is useful, i am going back to windows soon.  i am even paying for support from canonical, they suck.

---

### Post by draperdt on 2010-03-16
You will encounter the same issue with Win7 64bit aswell. 

Its the 64bit driver from the card manufacturer. You can still talk smack on canonical though. lol.

---

