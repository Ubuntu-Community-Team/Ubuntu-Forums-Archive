---
title: "wireless on dv1000 not working"
date: 2009-08-03
forum: Networking &amp; Wireless
---

### Post by redsoxrules on 2009-08-03
Hello:
 
I have installed ubuntu 9.04 on hp dv1000 and have tried everything that I googled for the problem with no success yet. Any pointers to the problem will be greatly appreciated.
 
Internet with the ethernet cable works very well.
 
Thanks for your help!

---

### Post by Crafty Kisses on 2009-08-03
Hey there! I need some more information before I and others can help you. What are the results of this command?
```
lspci
```

---

### Post by redsoxrules on 2009-08-03
Here is the response to the command: Thanks for your help!


00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:06.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
02:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
02:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
02:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
02:09.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller

---

### Post by Crafty Kisses on 2009-08-03
So according to **lspci**, this is the card you have:
```
02:06.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
```
So with your ethernet card plugged in, you need to run:
```
sudo apt-get install ndiswrapper-common
```
Once you have ndiswrapper installed, you now need to grab the driver, which I've attached at the bottom of this post. Then you need to extract this file, so once you have extracted this file, I'm guessing to your desktop, you then need to run:
```
ndiswrapper -i bcmwl5
ndiswrapper -m
```
Now you need to make sure ndiswrapper installed the driver correctly, so run the following to make sure:
```
ndiswrapper -l 
```
If the driver installed correctly, you should get an output similar to this:
```
Installed ndis drivers
driver present, hardware present 
```
Now you need to load the actual ndiswrapper module, so as root run:
```
modprobe ndiswrapper
```
Then you can run:
```
ifconfig wlan0 down
ifconfig wlan0 up
```
Then if that doesn't work you may have to reboot your whole machine after you followed my instructions, you can do this by running:
```
shutdown -r now
```
Once you have rebooted, you may have noticed it is still not working, but no need to panic, try loading the module again by running:
```
modprobe ndiswrapper
```
To make sure the ndiswrapper module is running, you can always run:
```
lsmod | grep ndis
```
That should tell you if the module is running, but if you follow my instructions, this should work to perfection.

---

### Post by redsoxrules on 2009-08-04
Thank you so much! It works!

Regards.

---

