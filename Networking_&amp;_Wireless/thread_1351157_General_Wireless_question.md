---
title: "General Wireless question"
date: 2009-12-10
forum: Networking &amp; Wireless
---

### Post by Porter200el on 2009-12-10
Hi all, this is general wireless question, I have used linux for about 5 years, love the stability, but I am not well versed in where drivers are stored in linux.  I know how to do things in good ole windoze with device manager, but linux is a bit more intimidating when it comes to drivers.  

On to the question:  How do I install drivers for a wireless card I bought?  Here is the [card]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833166021"), I got it for $10 shipped!  It comes with a driver disk and has drivers for windoze and linux.  Now, this is where I am looking for the great support from the ubnutu community.  I installed this on a old Gateway 500 Mhz with 384 MB of RAM, the card works in #! from the ubuntu family, but #! is still a pit pokey on that box.  Now, there is a distro SliTaz which is lightning fast on this box, but I am having trouble installing the driver for this card through there wireless manager.  [Here]("http://forum.slitaz.org/index.php/discussion/293/rosewill-rnx-g300lx-how-to-install/#Item_5") is a link to what they posted in their forum.  My ultimate question is, no matter what distro, how do I go about installing a driver in linux?  Where are there stored and how can I verify I installed the driver correctly and it is working?

I know this is a reltively noobish type question, but I want to find the answer so I can install drivers on whatever distro I am trying/using at the time.  Plus, I can help someone if I see a similar question somewhere.  I appreciate your time in reading and responding and please try and walk me through this gently (if possible).  Thanks to all and enjoy your day!!!

---

### Post by puppywhacker on 2009-12-10
The network card you have is an "Rosewill RNX-G300LX". That is the marketing name for the board, but the chip it uses is a RaLink RT2561/RT61

With 'lspci' it will show you the name as stated in the file /usr/share/misc/pci.ids by matching the vendor-id and product-id. Where 'lspci -n' will show you the actual id's after the bus number.

Now the linux kernel can use the modules (read: drivers) to support your card. With 'lsmod' you can list all the loaded modules, although they can theoretically also be included the actual kernel. With 'modprobe' or 'insmod' you can load the modules. With 'modprobe -r' or 'rmmod' you can unload the drivers. In /etc/modprobe.d they can be listed so they load every time you boot. if the driver is loaded you can check the kernel messages with 'dmesg' it should have a few lines on your card.

Only one of the modules is relevant for you.
/lib/modules/2.6.31-16-generic/kernel/drivers/net/wireless/rt2x00/rt2500pci.ko
/lib/modules/2.6.31-16-generic/kernel/drivers/net/wireless/rt2x00/rt61pci.ko

These drivers are included with the linux kernel. Development is always ongoing so the newer the kernel the better the support will be. Not all manufacturers give full support for linux modules, so some are created by the community (some real heroes!)

Once the module is loaded it will probably need some firmware to run, that is what has to be downloaded from the manufecturer of the chip (RaLink). 
/lib/firmware/rt2561.bin

After that the wireless framework (something like ieee803.11) will allow the card to be configured with iwconfig.

Alternatively you can use the windows driver using an ndiswrapper, emulating the windows driver subsystem. I find that a very dirty way of working

---

