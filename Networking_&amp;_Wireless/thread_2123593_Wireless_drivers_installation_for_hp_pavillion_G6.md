---
title: "Wireless drivers installation for hp pavillion G6"
date: 2013-03-08
forum: Networking &amp; Wireless
---

### Post by abhi411 on 2013-03-08
The output for lspci is

abhi@abhi-HP-Pavilion-g6-Notebook-PC:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Trinity [Radeon HD 7520G]
00:01.1 Audio device: Advanced Micro Devices [AMD] nee ATI Device 9902
00:04.0 PCI bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Root Port
00:10.0 USB controller: Advanced Micro Devices [AMD] Hudson USB XHCI Controller (rev 03)
00:10.1 USB controller: Advanced Micro Devices [AMD] Hudson USB XHCI Controller (rev 03)
00:11.0 SATA controller: Advanced Micro Devices [AMD] Hudson SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
00:12.2 USB controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11)
00:13.0 USB controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
00:13.2 USB controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11)
00:14.0 SMBus: Advanced Micro Devices [AMD] Hudson SMBus Controller (rev 14)
00:14.2 Audio device: Advanced Micro Devices [AMD] Hudson Azalia Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] Hudson LPC Bridge (rev 11)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] Hudson PCI Bridge (rev 40)
00:15.0 PCI bridge: Advanced Micro Devices [AMD] Device 43a0
00:15.1 PCI bridge: Advanced Micro Devices [AMD] Device 43a1
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Function 5
02:00.0 Network controller: Ralink corp. Device 3290
02:00.1 Bluetooth: Ralink corp. Device 3298
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader (rev 01)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)

wireless device is rt 3290

I have tried every single step in the forum [http://askubuntu.com/questions/229195/wireless-driver-how-to-load-manufacturers-sta-file-ralink-3290/229198#229198](http://askubuntu.com/questions/229195/wireless-driver-how-to-load-manufacturers-sta-file-ralink-3290/229198#229198) to install this driver but it still doesnt work .

So anyone who has solved this issue help out...!!

---

### Post by Bucky Ball on 2013-03-08
Give the output of:

```
sudo lshw -C network
```

And please use code tags. ;)

You know for certain wireless device is rt 3290? How? '02:00.0 Network controller: Ralink corp. Device 3290' does not necessarily = rt 3290.

* After reading your link it appears it is that wireless chip.

** Try this for a workaround:

[http://rricketts.com/installing-ralink-rt3290-wireless-drivers-in-ubuntu-12-04/](http://rricketts.com/installing-ralink-rt3290-wireless-drivers-in-ubuntu-12-04/)

If that doesn't work dig through here for anything promising:

[http://www.dogpile.com/info.dogpl/search/web?fcoid=417&fcop=topnav&fpid=2&q=Ralink+Device+3290&ql=](http://www.dogpile.com/info.dogpl/search/web?fcoid=417&fcop=topnav&fpid=2&q=Ralink+Device+3290&ql=)

---

