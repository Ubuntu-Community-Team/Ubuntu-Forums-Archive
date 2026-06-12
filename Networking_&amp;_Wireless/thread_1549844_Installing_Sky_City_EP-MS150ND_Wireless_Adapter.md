---
title: "Installing Sky City EP-MS150ND Wireless Adapter"
date: 2010-08-10
forum: Networking &amp; Wireless
---

### Post by ssemegran on 2010-08-10
I purchased a Sky City EP-MS150ND USB Wireless Adapter and it came with Linux drivers on a CD. I'm new to Ubuntu. I installed Ubuntu 10.04 on a Dell Inspiron laptop. How do you install this wireless adapter? Is there a useful instruction post for installing USB wireless adapters? Any help for a Ubuntu newbie would be much appreciated. Thanks!

Scott

---

### Post by rogergs on 2010-12-28
Hi Scott,

I just configured the USB adapter following the instructions for Fedora contained in the ppt file "RTL8712(8188_8191_8192SU)_usb_quick_installation_guide.ppt" in the CD folder: "RTL8188SU_Driver/Linux/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/document/".

For Ubuntu 10.10 I uncompressed the .tar.gz driver file and next I using a terminal I accessed to the driver folder and typed the next commands:
[I]
whatever_you_have$ [/I]**make**
*whatever_you_have$ ***sudo ./clean**
*whatever_you_have$ ***sudo insmod 8712u.ko***whatever_you_have$***sudo ifconfig wlan0 up**
*whatever_you_have$ ***sudo ifconfig wlan0 192.168.1.100**

*whatever_you_have$ ***sudo iwlist wlan0 scan**
*whatever_you_have$ ***sudo iwconfig wlan0 essid "*chosed_ESSID*"**

Maybe you don't need last two commands. Check first if you are allowed to connect to wireless network using the NetworkManager application in the Ubuntu top menu bar.

Hope this helps you!
Roger

---

