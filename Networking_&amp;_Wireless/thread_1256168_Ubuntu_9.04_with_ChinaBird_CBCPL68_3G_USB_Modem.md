---
title: "Ubuntu 9.04 with ChinaBird CBCPL68 3G USB Modem"
date: 2009-09-02
forum: Networking &amp; Wireless
---

### Post by Blackneron on 2009-09-02
Hi everybody,
 
I tried to install a **ChinaBird CBCPL68 3G USB modem** (broadband modem) on a **Ubuntu Linux 9.04** box and it took me a whole week because there exist no Linux drivers and nearly no documentation from the manufacturer, but now the modem works great !

After that I wrote some installation instructions and put them on my [**[COLOR=Blue]website[/COLOR]**]("http://www.pb-soft.com/index.php/home/29-modem") for those people who want to install such a modem. All the example configuration files are also available.

Maybe if you have another type of broadband modem with the "ZeroCD" feature (I think it's not really a feature !) you also could use the installation instructions but you have to adjust some of the settings.

[**[COLOR=Blue]Feel free to try it ![/COLOR]**]("http://www.pb-soft.com/index.php/home/29-modem")
 
Have a nice day  and good luck :) with your installation !

---

### Post by Blackneron on 2009-09-08
Updated version of the installation instructions available.

Now covers also kernel versions without the built in usbserial driver.

Because after running the automatic update of Ubuntu 9.04 the kernel is updated (In my case from 2.6.28-11 to 2.6.28-15) and the device does not switch from "storage" to the "modem" mode. In other words the modem does not work anymore !

I think that is a general problem not only with this type of modem :(

**[COLOR=blue][[COLOR=blue]Download Installation-Instructions[/COLOR]]("http://pb-soft.com/index.php/home/29-modem.html")[/COLOR]**

Best regards !

---

### Post by ieduarte73 on 2009-10-01
I am running Ubuntu Netbook Remix on an ASUS 1000He, I have followed carefully every step outlined on the Installation Instructions, however, the usb_switchmode never triggers, and when I do it manually I get the following:

Looking for target devices ...
 No devices in target mode or class found
Looging for default devices ...
 Found default devices (1)
Accesing device 000 on bus 003
Using endpoints 0x01 (out) and 0x84 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 No driver found. Either detached before or never attached
 Could not claim interace (error -1). Skipping device inquiry
Error: could not get description string "manufacturer"
.
.
.


However my device is connected to Bus 003 ID 003 according to lsusb.

Any ideas ?

---

