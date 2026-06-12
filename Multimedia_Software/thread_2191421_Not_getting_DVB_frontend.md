---
title: "Not getting DVB frontend"
date: 2013-12-02
forum: Multimedia Software
---

### Post by bigwolf227 on 2013-12-02
I have a Kworld UB-445-U USB TV adapter. At first linux was having trouble getting the proper ID for this adapter. 
The lsusb program shows this:
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 003: ID 046d:c064 Logitech, Inc. 
Bus 008 Device 002: ID 046d:c31c Logitech, Inc. Keyboard K120 for Business
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 07d1:3300 D-Link System DWA-130 802.11n Wireless N Adapter(rev.E) [Realtek RTL8191SU]
Bus 001 Device 002: ID 1b80:e43f Afatech  **<- That's my TV adapter**
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 002: ID 1004:61f1 LG Electronics, Inc. Optimus Android Phone [LG Software mode]
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

I'm running the Linux Kernel 3.12.1-generic because the cx231xx code for the UB-445 was included in the kernel source.
This is what the cx231xx-cards.c code shows: 
[744]("http://lxr.free-electrons.com/source/drivers/media/usb/cx231xx/cx231xx-cards.c#L744")         {[USB_DEVICE]("http://lxr.free-electrons.com/ident?i=USB_DEVICE")(0x1b80, 0xe421),
[745]("http://lxr.free-electrons.com/source/drivers/media/usb/cx231xx/cx231xx-cards.c#L745")          .[driver_info]("http://lxr.free-electrons.com/ident?i=driver_info") = [CX231XX_BOARD_KWORLD_UB445_USB_HYBRID]("http://lxr.free-electrons.com/ident?i=CX231XX_BOARD_KWORLD_UB445_USB_HYBRID")},

I modified the address to reflect the 0x43f in the code and re-compiled the modules. After rebooting, everything seemed to be working fine, except that I'm getting these annoying errors.
[   10.572149] cx231xx #0: UsbInterface::sendCommand, failed with status --32
[   10.572153] s5h1411_readreg: readreg error (ret == -32)
[   10.572185] cx231xx: Failed to attach s5h1411 front end

Naturally, the frontend is needed for the DVB to work... Could someone please help me out here?

Thanks,

Bigwolf227

---

