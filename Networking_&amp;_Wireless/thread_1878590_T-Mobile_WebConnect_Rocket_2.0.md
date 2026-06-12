---
title: "T-Mobile WebConnect Rocket 2.0"
date: 2011-11-10
forum: Networking &amp; Wireless
---

### Post by Jessica Lares on 2011-11-10
I need help using my 4G stick under Ubuntu 11.10. A lot of the problems I'm having seem to be permission and ID related, here are all my ports/connections:

```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 001 Device 036: ID 19d2:1203 ONDA Communication S.p.A. **
Bus 003 Device 002: ID 1b96:0001 N-Trig Duosense Transparent Electromagnetic Digitizer
Bus 004 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 001 Device 040: ID 05ac:1297 Apple, Inc. iPhone 4

```I'm using usb_modeswitch and have been studying multiple guides such as this [http://www.fogel.ca/2010/10/05/t-mobile-webconnect-rocket-2-0-on-debianubuntu/](http://www.fogel.ca/2010/10/05/t-mobile-webconnect-rocket-2-0-on-debianubuntu/) but nothing's working for me. I tried sakis3g too, but it asked me about the actual numbers which I have no idea about.

When I connect to the stick under the menu on the right of the desktop, the device light is on, like it should be. However, when I try using the Internet it doesn't work.

Thanks in advanced.

---

### Post by SilvaRizla on 2011-11-10
Are u also connected via wifi or ethernet at the same time?

---

### Post by Jessica Lares on 2011-11-10
> **SilvaRizla said:**
> Are u also connected via wifi or ethernet at the same time?

No, and just to make sure, I turn off the Wi-Fi switch on the side of the laptop.

---

### Post by Jessica Lares on 2011-11-11
Finally got usb_modeswitch to see it, but it won't ping or load anything.

---

### Post by alexfish on 2011-11-11
Hi

usb_modeswitch only switches the device to modem mode

can read here 
[SIZE=1][Draisberghof - Software - *USB_ModeSwitch*]("http://www.google.co.uk/url?sa=t&rct=j&q=usb_modeswitch&source=web&cd=1&sqi=2&ved=0CCoQFjAA&url=http%3A%2F%2Fwww.draisberghof.de%2Fusb_modeswitch%2F&ei=ZN-9TvnzMo2p8APGxuikBA&usg=AFQjCNHXRDd_7g_A3ekgGQ2d_tARDOR6iA&cad=rja")[/SIZE]

 post the results of this command from the terminal

```
usb-devices
```locate the lines which indicate the device and post only those lines

---

### Post by pdc on 2011-11-11
if one googles on 

> 19d2:1203 usb_modeswitch

a variety of threads emerge:

eg

[http://latteye.com/2011/02/t-mobile-rocket2-4g.html](http://latteye.com/2011/02/t-mobile-rocket2-4g.html)

this how-to comments that **BEFORE FLIPPING** the device has an ID of 

> 1201

and **AFTER FLIPPING**, has an ID of

> 1203

so as you post the latter, we assume the device has already been flipped

if you copy and paste 

> dmesg | grep tty 

into a terminal you may see ttyACM0 or suchlike.......................

sometimes one has to check such tricky things as: is simcard correctly inserted,,,,,,,has one got the correct apn settings.....one has definitely paid up with provider......one is selecting the correct plan etc


> but it won't ping or load anything. 

perhaps you make clear to us how you have configured this device..and how you are attempting to connect..................

and tell us what country and network you want to connect to, and we can check all that for you

---

