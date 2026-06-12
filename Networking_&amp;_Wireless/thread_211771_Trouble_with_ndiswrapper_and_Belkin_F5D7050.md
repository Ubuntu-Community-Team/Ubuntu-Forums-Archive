---
title: "Trouble with ndiswrapper and Belkin F5D7050"
date: 2006-07-08
forum: Networking &amp; Wireless
---

### Post by absaroka42 on 2006-07-08
I'm newish with Ubuntu, but think I crashed ndiswrapper.
I've been trying to install a Belkin F5D7050 usb wireless adapter on a Toshiba laptop.
I initially tried using ndiswrapper, but couldn't get it to recognize the device.  Then I installed ndisgtk, trying both the driver on the CD and the driver downloaded from Belkin.  The driver loaded, and ndisgtk said the hardware was recognized, but window that comes up after selecting 'configure network' just hangs.  If I remove the device from the USB slot, it will stop hanging, showing that I have an installed wireless device.  But no connection is made. With lspci, the device doesn't show under the usb ports, and when I tried to manually remove the driver with ndiswrapper from the terminal, the terminal itself hung up.  I'm stumped.  

I've already uninstalled and reinstalled ndisgtk and ndiswrapper, and even wiped my hard drive and reinstalled ubuntu.  I had previously tried a D-link PC card, but had different (but also interesting) problems, and no success.

Can anyone help?

---

### Post by Clyde McLennan on 2006-07-11
Hi,
  I received my 'Live CD' today of version 5.10 and like absaroka42 above I too have a Toshiba Laptop and Belkin USB wireless adapter (F5D7050).  

  It ran well, and looks great, and I like the GNOME interface.  However, it does not seem to recognise the USB wireless connection.
   
  I'm new to Linux, (but used to use Xenix & Unix many years ago), and so struggle with anything that goes beyond a simple install. 

  I will be interested in any help that can be given.

     Clyde

---

