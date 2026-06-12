---
title: "Realtek Semiconductor Corp. RTL8191SU 802.11n WLAN Adapter"
date: 2013-04-19
forum: Networking &amp; Wireless
---

### Post by fizz55 on 2013-04-19
Hello,

I have a usb wireless adapter, it does show up in linux and "attempts" to connect to networks, but it either takes a long time to connect or (usually) won't connect at all.

lsusb tells me it's called "Realtek Semiconductor Corp. RTL8191SU 802.11n WLAN Adapter".  It did come with a linux driver but it will only work for an older kernel (The website says it will work with Linux Kernel 2.6.18~2.6.38 and Kernel 3.0.2). 

It does work fine on windows after I install the driver, so I know the device works.  

When I try to compile it there's a missing header file (which apparently doesn't exist in linux anymore). 
"rtl871x_io.h:35:28: fatal error: linux/smp_lock.h: No such file or directory compilation terminated."  

Is there some workaround to make this work on the kernel I'm running (3.5.0-27-generic)?

  By the way I'm running fully updated Lubuntu 12.10.  

Thanks, fizz55  

EDIT:  
Machine Brand and Model (PC/Laptop) - HP Compaq 8710p
Architecture - 3.5.0-27-generic x86_64

---

