---
title: "Ubuntu 12.04 isnt connecting to internet !"
date: 2013-02-26
forum: Networking &amp; Wireless
---

### Post by h3lp on 2013-02-26
I came here for some help, and hopefully thats what you guys can give. 

All my computers in my house are connected to my wifi connection perfectly but I recently installed Ubuntu 12.04 LTS & its really frustrating me. I know some basic linux commands but cant seem to connect to my wifi. 

I tried this tutorial - [http://www.myapitips.com/2012/10/19/how-to-install-broadcom-wireless-driver-in-ubuntu-12-10/](http://www.myapitips.com/2012/10/19/how-to-install-broadcom-wireless-driver-in-ubuntu-12-10/)

That failed. 

I also went to System Settings > Additional Drivers 

& when I go there it says "Downloading package indexes failed, please check your network status. Most drivers will not be available." 

Then it searches for available drivers & when it shows the menu there are no drivers to be enabled. 

So, I decided to get a "USB Wireless Adapter". So, I got the, "Belkin Dual-band wifi USB Adapter N600 DB" 

I put it in the USB port & absolutely nothing happend. It just stayed the same as last time. I tryed going to System Settings > Additional Drivers, again. 

But it did the same exact thing as I said before. Please, help me get connected to the internet UbuntuForums :) 

Thanks for the hopefully, upcoming help. 

Also my computer is a, "Dell Inspiron 1545" & I use to have Windows Vista installed onto the computer ti'll I changed to Ubuntu 12.04. 

EDIT: I just found a CD in my box with the USB Wifi Adapter but it says its for Windows XP/Vista/7 ... So, I was thinking maybe should I download wine to a USB & run the driver CD?

---

### Post by bellaseem on 2013-02-27
First you might want to check that your USB port is working (trying using a usb flash drive to check it)... 

Other than that, search online for drivers for your USB (look up what chipset your adapter uses and search for drivers for that chipset, then download and install them)

If that doesn't work, then search for a tutorial on how to use ndiswrapper to install the windows drivers that you got on the CD for your card...

---

### Post by varunendra on 2013-02-27
Welcome to the forums h3lp !

To let us see exactly what chips your internal and usb adapters are using, please post the outputs of -
```
lspci -nnk | grep -iA2 net
lsusb
```
..while the usb adapter is plugged in.

---

### Post by albandy on 2013-02-27
> **h3lp said:**
> I came here for some help, and hopefully thats what you guys can give. 

All my computers in my house are connected to my wifi connection perfectly but I recently installed Ubuntu 12.04 LTS & its really frustrating me. I know some basic linux commands but cant seem to connect to my wifi. 

I tried this tutorial - [http://www.myapitips.com/2012/10/19/how-to-install-broadcom-wireless-driver-in-ubuntu-12-10/](http://www.myapitips.com/2012/10/19/how-to-install-broadcom-wireless-driver-in-ubuntu-12-10/)

That failed. 

I also went to System Settings > Additional Drivers 

& when I go there it says "Downloading package indexes failed, please check your network status. Most drivers will not be available." 

Then it searches for available drivers & when it shows the menu there are no drivers to be enabled. 

So, I decided to get a "USB Wireless Adapter". So, I got the, "Belkin Dual-band wifi USB Adapter N600 DB" 

I put it in the USB port & absolutely nothing happend. It just stayed the same as last time. I tryed going to System Settings > Additional Drivers, again. 

But it did the same exact thing as I said before. Please, help me get connected to the internet UbuntuForums :) 

Thanks for the hopefully, upcoming help. 

Also my computer is a, "Dell Inspiron 1545" & I use to have Windows Vista installed onto the computer ti'll I changed to Ubuntu 12.04. 

EDIT: I just found a CD in my box with the USB Wifi Adapter but it says its for Windows XP/Vista/7 ... So, I was thinking maybe should I download wine to a USB & run the driver CD?

Plug a network cable and install the drivers. Then your wifi adapter should work.

---

