---
title: "Wireless Authentication Error"
date: 2010-06-27
forum: Networking &amp; Wireless
---

### Post by Xybrik on 2010-06-27
Hi, I am new to linux. I just installed Ubuntu 10.04 LTS 64 bit. I use a D-Link DWA-130 wireless adapter on my desktop to connect to my router. The wireless networks display but it cannot authenticate. I have tried several different wireless networks both secured and unsecured. It works when I boot to windows 7 and works when I use the same version of ubuntu as a virtual machine running in windows but not when I boot to ubuntu. Here is some basic info on my computer. Let me know if any other information would be helpful in solving this problem.

peter@peter-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSIDff/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=4 dBm   
          Retry  long limit:7   RTS thrff   Fragment thrff
          Power Managementn

peter@peter-desktop:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
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
01:00.0 VGA compatible controller: ATI Technologies Inc RV790 [Radeon HD 4800 Series]
01:00.1 Audio device: ATI Technologies Inc HD48x0 audio
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
03:08.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)

---

### Post by Xybrik on 2010-06-27
bump

---

### Post by Talon2 on 2010-06-27
Bumping with less that 24 hours having passed is not a good idea.  Bumping can also hide posts that might otherwise get attention.

It can be important to know the type of wireless adapter and the chipset it contains.

A quick google search (D-Link DWA-130 chipset) tells me your adapter is a USB adapter.  In this case, "lsusb" is the command you are looking for.

The google search also told me this adapter likely has a Marvell Semiconductor Inc. chipset and it is capable of b. g and n.

I'm not familiar with Marvell chipsets so I'll bow out at this point.

---

### Post by Xybrik on 2010-06-28
Apologies for the quick bump, I will keep that in mind in the future. Here is the info from the lsusb command

peter@peter-desktop:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 005: ID 046d:c222 Logitech, Inc. G15 Keyboard / LCD
Bus 003 Device 004: ID 046d:c221 Logitech, Inc. G15 Keyboard / Keyboard
Bus 003 Device 003: ID 046d:c051 Logitech, Inc. G3 (MX51 Optical Mouse
Bus 003 Device 002: ID 046d:c223 Logitech, Inc. G15 Keyboard / USB Hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 07d1:3c13 D-Link System 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 04f2:a13c Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


The above poster was correct about the details of my wireless adapter. Here is a link to the product page if there is more info that you need to solve the problem...

[http://www.dlink.com/products/?pid=566](http://www.dlink.com/products/?pid=566)

Thanks

---

### Post by Xybrik on 2010-06-29
bump

---

### Post by Xybrik on 2010-07-01
bump

---

### Post by Xybrik on 2010-07-03
bump

---

### Post by SoFl W on 2010-07-03
If you goto your network manager does it list the available connections?


If you right click -> edit connections, and wireless connections it doesn't have anything.

---

### Post by Xybrik on 2010-07-04
It lists four of the connections in the wireless tab, not all of them. Each of the four are listed in the form "Auto 'Wireless Network Name'"

---

### Post by Xybrik on 2010-07-05
bump

---

### Post by Xybrik on 2010-07-06
bump

---

