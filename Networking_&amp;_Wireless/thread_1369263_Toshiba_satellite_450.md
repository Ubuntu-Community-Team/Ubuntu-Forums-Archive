---
title: "Toshiba satellite 450"
date: 2009-12-31
forum: Networking &amp; Wireless
---

### Post by qwerty123321 on 2009-12-31
Ubuntu doesn't dectect my wireless card for some reason..
it works in windows 7 ( I installed ubuntu using wubi on same drive ) and it's really frusterating because I want to use ubuntu as my main OS ..but without wireless internet, ubuntu is literally useless to me

terminal 
```

howard@ubuntu:~$ ndiswrapper -l
net819xp : driver installed
howard@ubuntu:~$ lspci -n
00:00.0 0600: 1022:9600
00:01.0 0604: 1179:9602
00:06.0 0604: 1022:9606
00:07.0 0604: 1022:9607
00:11.0 0106: 1002:4391
00:12.0 0c03: 1002:4397
00:12.1 0c03: 1002:4398
00:12.2 0c03: 1002:4396
00:13.0 0c03: 1002:4397
00:13.1 0c03: 1002:4398
00:13.2 0c03: 1002:4396
00:14.0 0c05: 1002:4385 (rev 3a)
00:14.1 0101: 1002:439c
00:14.2 0403: 1002:4383
00:14.3 0601: 1002:439d
00:14.4 0604: 1002:4384
00:18.0 0600: 1022:1300 (rev 40)
00:18.1 0600: 1022:1301
00:18.2 0600: 1022:1302
00:18.3 0600: 1022:1303
00:18.4 0600: 1022:1304
01:05.0 0300: 1002:9613
0e:00.0 0280: 10ec:8172 (rev 10)
14:00.0 0200: 10ec:8136 (rev 02)
howard@ubuntu:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Toshiba America Info Systems Device 9602
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
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
00:18.0 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h [Turion X2, Athlon X2, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780MC [Radeon HD 3100 Graphics]
0e:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)
14:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
howard@ubuntu:~$ howard@ubuntu:~$ ndiswrapper -l
howard@ubuntu:~$: command not found
howard@ubuntu:~$ net819xp : driver installed

```

---

