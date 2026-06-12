---
title: "Wireless Configuration"
date: 2010-03-07
forum: Networking &amp; Wireless
---

### Post by Thomas_Bates on 2010-03-07
Hello, I've been working with Ubuntu for awhile now, but always through an ethernet connection, and today, I'm proud to say that I removed that last thread of Microsoft in my life. But now, I've got Ubuntu on my laptop, but no wireless.

I've read many guides and still can't seem to do anything to help it, I'll post the necessary info (all that I know is necessary at least) and hopefully I can get some help.

>                                   thomas@thomas-laptop:~$ lspci  
 00:00.0 Host bridge: Intel Corporation System Controller Hub (SCH Poulsbo) (rev 07)  
 00:02.0 VGA compatible controller: Intel Corporation System Controller Hub (SCH Poulsbo) Graphics Controller (rev 07)  
 00:1b.0 Audio device: Intel Corporation System Controller Hub (SCH Poulsbo) HD Audio Controller (rev 07)  
 00:1c.0 PCI bridge: Intel Corporation System Controller Hub (SCH Poulsbo) PCI Express Port 1 (rev 07)  
 00:1c.1 PCI bridge: Intel Corporation System Controller Hub (SCH Poulsbo) PCI Express Port 2 (rev 07)  
 00:1d.0 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #1 (rev 07)  
 00:1d.1 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #2 (rev 07)  
 00:1d.2 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #3 (rev 07)  
 00:1d.7 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB EHCI #1 (rev 07)  
 00:1f.0 ISA bridge: Intel Corporation System Controller Hub (SCH Poulsbo) LPC Bridge (rev 07)  
 00:1f.1 IDE interface: Intel Corporation System Controller Hub (SCH Poulsbo) IDE Controller (rev 07)  
 02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)  
 03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)  
 thomas@thomas-laptop:~$ lspci | grep Network  
 03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)  
 thomas@thomas-laptop:~$  
 

 

 thomas@thomas-laptop:~$ iwconfig  
 lo        no wireless extensions.  
 

 eth0      no wireless extensions.
 

---

### Post by Thomas_Bates on 2010-03-07
I'm able to connect the laptop to an ethernet connection, so if I need to download anything I can do that, but I don't know much else about it.

Although I can smell NDISwrapper's involvement soon.

---

### Post by chili555 on 2010-03-07
> Although I can smell NDISwrapper's involvement soon.I thought you wanted to be free of Windows. Doesn't that include their drivers?

Please hook up the ethernet cable and go to System -Administration -Hardware Drivers and see if ole Chili has a surprise for you.

---

### Post by Thomas_Bates on 2010-03-07
I'm going to have to use the drivers, it has to do with the card being installed inside the computer and it was running windows, I'm not sure if there are any free drivers for the card I have.

looks like two drivers, Broadcom B43 wireless driver and Broadcom STA wireless driver, downloading and installing both.

---

### Post by Thomas_Bates on 2010-03-07
WOW!
Thanks a huge amount chili555, I post here and in under 20 minutes my problem is solved!

AMAZING.

I knew I loved linux and the community for a reason...

TAKE THAT YOU MICROSOFT TECH SUPPORT REPS!

:)

---

### Post by chili555 on 2010-03-07
> it has to do with the card being installed inside the computer and it was running windows,I guess you showed them!! Glad it's working. Enjoy.

---

