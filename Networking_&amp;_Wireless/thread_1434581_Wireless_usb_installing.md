---
title: "Wireless usb installing"
date: 2010-03-20
forum: Networking &amp; Wireless
---

### Post by dagarshali on 2010-03-20
Hi,
I recently bought a wireless usb card from amazon.

[http://www.amazon.com/gp/product/B00333AW72/ref=oss_product](http://www.amazon.com/gp/product/B00333AW72/ref=oss_product)

On the website it said it has support for linux as well. I received the card and it came with disk which has source that that i need to compile.

On the usb card itself there was a sticker called RT2070

But when i got to the linux folder of source code and compile, i get a RT3070STA.ko

I further followed the instructions, where it says /sbin/insmod RT3070STA.ko

when i do that, i get
sudo /sbin/insmod rt2070sta.ko
insmod: error inserting 'rt2070sta.ko': -1 Unknown symbol in module


I am not sure on the first place how to find which chipset to use. When i used lsusb -v, i got ralink technology as the manufacturer.

Any help?

Regards,
Vishwa

---

### Post by 2hot6ft2 on 2010-03-20
[This tutorial is for USB WiFi Adapters that use the RT2870 or RT3070 chipsets by Ralink.]("http://ubuntuforums.org/showthread.php?t=1342593")

Should help.
And try it without the -v
> **dagarshali said:**
> 
I am not sure on the first place how to find which chipset to use. When i used lsusb -v, i got ralink technology as the manufacturer.

The chipset is identified by it's code which will be something like **obda:2070** I'm just making up numbers and letters there yours will be different.

---

### Post by dagarshali on 2010-03-20
HI,
Thanks for the reply... 
i did the lsusb and in the device id, i got
ID 148f:3070 and it thought it might have the rt3070 drivers. So i blacklisted 

blacklist rt2x00usb
blacklist rt2x00lib
blacklist rt2800usb
blacklist rt2870sta

i compiled the code as the tutorial suggests and ran sudo make install

when i tried
sudo insmod /lib/modules/`uname -r`/kernel/drivers/net/wireless/rt3070sta.ko

i get an error error insterting rt3070sta.kob: -1 unknown symbol in module.

I aslo saw in the tutorial where it compiled for the device id by putting 

{USB_DEVICE(0x1234,0x7777)}, /* Example WiFi Device Name */..where exactly do i need to insert this in the usb_main_dev.c file?

Regards,
Vishwa

---

### Post by timmynana on 2010-03-22
is there an easier way to do this? i have tried the above but not even lsusb finds anything

---

### Post by chili555 on 2010-03-23
> **dagarshali said:**
> HI,
Thanks for the reply... 
i did the lsusb and in the device id, i got
ID 148f:3070 and it thought it might have the rt3070 drivers. So i blacklisted 

blacklist rt2x00usb
blacklist rt2x00lib
blacklist rt2800usb
blacklist rt2870sta

i compiled the code as the tutorial suggests and ran sudo make install

when i tried
sudo insmod /lib/modules/`uname -r`/kernel/drivers/net/wireless/rt3070sta.ko

i get an error error insterting rt3070sta.kob: -1 unknown symbol in module.

I aslo saw in the tutorial where it compiled for the device id by putting 

{USB_DEVICE(0x1234,0x7777)}, /* Example WiFi Device Name */..where exactly do i need to insert this in the usb_main_dev.c file?

Regards,
VishwaWhat is wrong, after you do the blacklisting, with the built-in rt3070sta from:```
/lib/modules/2.6.31-20-generic/kernel/drivers/staging/rt3070/rt3070sta.ko
```It claims your device and should work. You might have to uninstall the module you built for it to work.

---

### Post by chili555 on 2010-03-23
> **timmynana said:**
> is there an easier way to do this? i have tried the above but not even lsusb finds anythingIf you cold-boot the machine, insert the device and run:```
lsusb
```Does the device appear? What is its usb.id code? Here is an example from the post above; this may or may not be your number:> ID 148f:3070

---

