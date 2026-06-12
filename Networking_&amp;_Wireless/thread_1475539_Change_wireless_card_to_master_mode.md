---
title: "Change wireless card to master mode"
date: 2010-05-07
forum: Networking &amp; Wireless
---

### Post by vksingh on 2010-05-07
Hi, 

I am using ubuntu 9.10 on my desktop having a belkin wireless usb card. I want to change the mode of it to master mode. How can I do it?

Kindly help.

Thanks,


Vivek

---

### Post by iponeverything on 2010-05-07
use lspci, lshw and google to determine the hardware used in your belkin card. Once you determine the hardware use google to find out if the linux driver for that hardware supports master mode. After that, use google to find out how use hostapd to configure master mode and how to set it up as an AP.

If you run into problems post back with specific questions.

---

### Post by vksingh on 2010-05-10
> **iponeverything said:**
> use lspci, lshw and google to determine the hardware used in your belkin card. Once you determine the hardware use google to find out if the linux driver for that hardware supports master mode. After that, use google to find out how use hostapd to configure master mode and how to set it up as an AP.
 
If you run into problems post back with specific questions.
 
 
Hi , I am using belkin network card. 
 
Can you suggest which card will help me to solve my purpose to convert easily to master mode.
 
If there are some standard procedure to change the mode, then please give reference to the same.
 
 
Thanks,
 
Vivek

---

### Post by Crio on 2010-05-10
"Standard" way to put wifi card into the master mode is to issue command

sudo iwconfig wlan0 mode master

(substitute your device instead of wlan0).
But one thing I learned while setting up AP (just finished; using D-Link DWA-510 PCI card, which is based on RaLink RT2561/RT61 rev B chipset, if you wonder) is that if that command fails that DOES NOT mean that the card would not work in the master mode. In my case it did fail ("invalid argument"), but after I set up and run hostapd, iwconfig showed that the card IS in the master mode.

As was suggested above, google chipset of your card (exact name of the product or, better, some kind of vendor id + "chipset") then google hostapd support for the chipset.

---

