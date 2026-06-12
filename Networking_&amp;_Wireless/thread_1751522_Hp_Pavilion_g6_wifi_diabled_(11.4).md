---
title: "Hp Pavilion g6 wifi diabled (11.4)"
date: 2011-05-06
forum: Networking &amp; Wireless
---

### Post by Memischap on 2011-05-06
Hi i need help bad i installed Ubuntu 11.4 on a hp pavilion g6 and all seemed good until i realized the wireless on/off toggle switch( that is integrated into f12) wouldn't toggle so it is stuck on off. so now i have been fores to the basement to use an Ethernet cable. please help i am brand new to Linux and have no idea how to fix this.

thanks in advance

---

### Post by Supergnu on 2011-06-03
Open a terminal and type:
```
lspci
```press enter and post the result

---

### Post by rokikish on 2012-04-26
Hi I have a HP Pavilion dv7 can you help me?

~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] Device 1705
00:01.0 VGA compatible controller: ATI Technologies Inc Device 9647
00:01.1 Audio device: ATI Technologies Inc Device 1714
00:04.0 PCI bridge: Advanced Micro Devices [AMD] Device 1709
00:05.0 PCI bridge: Advanced Micro Devices [AMD] Device 170a
00:06.0 PCI bridge: Advanced Micro Devices [AMD] Device 170b
00:10.0 USB Controller: Advanced Micro Devices [AMD] Hudson USB XHCI Controller (rev 03)
00:10.1 USB Controller: Advanced Micro Devices [AMD] Hudson USB XHCI Controller (rev 03)
00:11.0 SATA controller: Advanced Micro Devices [AMD] Hudson SATA Controller [AHCI mode]
00:12.0 USB Controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
00:12.2 USB Controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11)
00:13.0 USB Controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
00:13.2 USB Controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11)
00:14.0 SMBus: Advanced Micro Devices [AMD] Hudson SMBus Controller (rev 13)
00:14.1 IDE interface: Advanced Micro Devices [AMD] Hudson IDE Controller (rev 40)
00:14.2 Audio device: Advanced Micro Devices [AMD] Hudson Azalia Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] Hudson LPC Bridge (rev 11)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] Hudson PCI Bridge (rev 40)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6
00:18.6 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5
00:18.7 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
02:00.0 Network controller: Ralink corp. Device 5390
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5209 (rev 01)

---

### Post by ts3 on 2012-04-26
I'd suggest 

```
rfkill list all
```

If there are any yes answers then

```
sudo rfkill unblock all
```

If the switch still shows as disabled (on my hp dm1z it's an orange light) try to toggle the switch (press just once) and run sudo rfkill unblock all again.  

In my experience with hp, switching off the wireless with F12 and then rebooting with the wireless off messes up the switch so I try to avoid it :)  If I forget sudo rfkill unblock all usually works.

---

