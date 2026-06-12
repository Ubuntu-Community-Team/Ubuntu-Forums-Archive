---
title: "Need help with Toshiba Satellite L855"
date: 2013-06-05
forum: Networking &amp; Wireless
---

### Post by mabz1121 on 2013-06-05
I have a brand new Toshiba Satellite and I wiped Windows 8 and installed Ubuntu 12.04 LTS, and now I have absolutely no internet connection (the obvious has been tried...wifi turned on, ethernet cable plugged in). I have been familiarizing myself with Terminal and have no problems understanding how to work it, I just need to know what I need to install them manually. I'm not sure specifically what to look for. Here is my lspci.. Help.. please and thank you :-k

mabz@BELL:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Device 9903
00:01.1 Audio device: Advanced Micro Devices [AMD] nee ATI Device 9902
00:04.0 PCI bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Root Port
00:05.0 PCI bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Root Port
00:10.0 USB controller: Advanced Micro Devices [AMD] Hudson USB XHCI Controller (rev 03)
00:11.0 SATA controller: Advanced Micro Devices [AMD] Hudson SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
00:12.2 USB controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11)
00:13.0 USB controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
00:13.2 USB controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11)
00:14.0 SMBus: Advanced Micro Devices [AMD] Hudson SMBus Controller (rev 14)
00:14.2 Audio device: Advanced Micro Devices [AMD] Hudson Azalia Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] Hudson LPC Bridge (rev 11)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] Hudson PCI Bridge (rev 40)
00:14.5 USB controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
00:14.7 SD Host controller: Advanced Micro Devices [AMD] Hudson SD Flash Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Function 5
01:00.0 Ethernet controller: Atheros Communications Inc. AR8162 Fast Ethernet (rev 10)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8723

---

### Post by oldos2er on 2013-06-05
Moved to Networking & Wireless.

---

### Post by mabz1121 on 2013-06-07
Downloaded Ubuntu 13.04. Everything works fine!

---

