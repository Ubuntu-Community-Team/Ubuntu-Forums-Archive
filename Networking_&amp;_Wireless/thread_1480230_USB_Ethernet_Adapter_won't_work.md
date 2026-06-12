---
title: "USB Ethernet Adapter won't work"
date: 2010-05-11
forum: Networking &amp; Wireless
---

### Post by unckybob on 2010-05-11
Please help me out with this if you can. I'm just a noob and I can't get this to work. 

Cisco Linksys USB300M USB Ethernet Adapter 
under Ubuntu 10.04 

#lsusb 
Bus 001 Device 003: ID 0b95:7720 ASIX Electronincs Corp. AX88772 

I bought this because some reviews at newegg, 

[http://www.newegg.com/Product/ProductReview.aspx?Item=N82E16833124335](http://www.newegg.com/Product/ProductReview.aspx?Item=N82E16833124335)

said adapter was pretty much plug and play under Ubuntu. But it won't do a thing for any of my computers. 

A search on Google: "AX88772 linux driver" gives a download link to a driver on the ASIX site. 

[http://www.asix.com.tw/products.php?op=pItemdetail&PItemID=97;71;101](http://www.asix.com.tw/products.php?op=pItemdetail&PItemID=97;71;101)

On the site, just above the download links for all the drivers it says: 

"All these AX88772A drivers are qualified with ASIX AX88772A demo board. If these drivers could not work with your AX88772A device, please contact your AX88772A device manufacturer to get a correct driver." 

Which says to me that even after you've done all the work of building and installing this driver, it still might not work. 

However the README file that comes with it requires that one rebuild the driver from scratch using the kernel source code. I've never done anything even like that. Here's part of the README file. 

<- Begin README file 

================
Prerequisites
================

Prepare to build the AX88772/AX88772A/AX88178 driver, you need the Linux kernel sources 
installed on the build machine, and make sure that the version of the running kernel 
must match the installed kernel sources.
If you don't have the kernel sources, you can get it from [www.kernel.org](www.kernel.org) or contact to 
your Linux distributor. If you don't know how to do, please refer to KERNEL-HOWTO.

Note1: Please make sure the kernel is built with one of the "Support for Host-side, 
       EHCI, OHCI, or UHCI" option support.

Note2: Please make sure the kernel is built with "Multi-purpose USB Networking Framework" 
       option support.

Note3: Check the necessary header file "usbnet.h" for building this driver. Without 
       this file, the driver compilation will fail and encounter hundreds of errors 
       all throuhout the souces. This file was located in different directory 
       according to your kernel version:

       1. Linux kernel versions from 2.6.14 to 2.6.21
          /Path-to-your-Linux-kernel-sources/drivers/usb/net/usbnet.h

       2. Linux kernel versions from 2.6.22 to 2.6.24
          /Path-to-your-Linux-kernel-sources/drivers/net/usb/usbnet.h

       3. Linux kernel versions from 2.6.25 and later
          /Path-to-your-Linux-kernel-sources/include/linux/usb/usbnet.h


================
Getting Start
================

1. Extract the compressed driver source file to your template directory by the following command:

	[root@localhost home]# tar -xf AX88772_772A_178_LINUX2.6.25_REV106_20080901.tar.bz2

2. Now, the AX88772_772A_178_LINUX2.6.25_REV106_20080901/ driver directory should be extracted
   under current directory. Go to the driver directory, and executing the following command to
   compiler the AX88772/AX88772A/AX88178 driver.
 
	[root@localhost AX88772_772A_178_LINUX2.6.25_REV106_20080901]# make
			
3. If the compilation is well, the asix.ko will be created under the current directory.
 
4. If you want to use modprobe command to mount the AX88772/AX88772A/AX88178 driver, executing
   the following command to install the driver into your Linux.

	[root@localhost AX88772/AX88772A/AX88178]# make install

End README file -> 

The people who wrote the reviews on newegg seemed to have no problems getting this adapter to work under Ubuntu. I really don't want to go through this build process. It sound like a wild goose chase for someone with as little experience as me. I wonder if I'm doing something wrong to get this thing working an easy way. Can anyone see a simple solution to this problem. Please help.

---

### Post by unckybob on 2010-05-11
I just bought another adapter, a Belkin USB 10/100 Ethernet Adapter version 2101, Part number F5D5050. With a lifetime warranty you can't go wrong. It works like a dream. It's plug and play under linux and it's easy to install the driver in Windows 7. 

I don't recommend the Cisco adapter.I returned the first one I bought. The one they replaced it with wouldn't work under linux or Windows 7 either. Not even with their tech support on the phone. The Belkin costs less and I'm tired of waiting for replacements in the mail from Cisco. 

I would caution anyone against buying the Cisco adapter.

---

### Post by bobd27 on 2010-05-28
I've been using the Belkin adapter since 6.75 and it worked fine, however, when I upgraded to Lynx it stopped seeing the adapter. Any help??

---

### Post by justforsp on 2010-07-04
> **bobd27 said:**
> I've been using the Belkin adapter since 6.75 and it worked fine, however, when I upgraded to Lynx it stopped seeing the adapter. Any help??
what is the version of kernel are you using ? 
I have started to  have problem with my usb adapter 
check [http://ubuntuforums.org/showthread.php?p=9545973](http://ubuntuforums.org/showthread.php?p=9545973)

---

### Post by FedoraUser42 on 2013-03-22
> **unckybob said:**
> I just bought another adapter, a Belkin USB 10/100 Ethernet Adapter version 2101, Part number F5D5050. With a lifetime warranty you can't go wrong. It works like a dream. It's plug and play under linux and it's easy to install the driver in Windows 7. 

I don't recommend the Cisco adapter.I returned the first one I bought. The one they replaced it with wouldn't work under linux or Windows 7 either. Not even with their tech support on the phone. The Belkin costs less and I'm tired of waiting for replacements in the mail from Cisco. 

I would caution anyone against buying the Cisco adapter.

I just tried the Belkin adapter based on the above comment.  I want to confirm that the Belkin adapter worked on Fedora 14 Linux straight out of the box.

Belkin - USB 2.0 Ethernet Network Adapter
Model: F4U061-BBY

---

### Post by oldos2er on 2013-03-22
Old thread closed, please don't bump old threads.

---

