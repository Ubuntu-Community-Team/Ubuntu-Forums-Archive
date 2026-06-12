---
title: "[SOLVED] frustrated,ready to through computer out the window"
date: 2008-12-31
forum: Networking &amp; Wireless
---

### Post by amanda hill on 2008-12-31
Please help.I have a new dell inspiron mini loaded with Ubuntu 8.04. i cannot connect it to my wireless internet it works fine on ethernet,I have been reading through these forums and none of this makes sense to me.We are talking VERY BASIC answers here please.HEEEEELP!!!!!!!!!!!:confused:yes I realise now i spelt throw wrong Thanks,

---

### Post by shane8002 on 2008-12-31
Go to places-administration-hardware drivers  You should be able to turn on your wireless card. its best to plug your computer into a wired connection update it, and then go to add remove under the start menu and get a program called network manager so u can choose wireless networks with your laptop. Thats the easiest way.

---

### Post by cdtech on 2008-12-31
I just wanted to know which window?

Just kiddn'. If shane8002's suggestion dosen't work report back, lets see what we can do for ya.

Remember, it's just a computer. Take a deap breath.........

---

### Post by darkstaar on 2008-12-31
> **amanda hill said:**
> yes I realise now i spelt throw wrong Thanks,

Wee take corect speling and gramar very siriously hear so try too use a spelcheker. And wellcome too the ubuntu forms.

--Leisa

---

### Post by cdtech on 2008-12-31
Listing the device could help troubleshoot the issue:
```
lspci
```

---

### Post by amanda hill on 2008-12-31
> **shane8002 said:**
> Go to places-administration-hardware drivers  You should be able to turn on your wireless card. its best to plug your computer into a wired connection update it, and then go to add remove under the start menu and get a program called network manager so u can choose wireless networks with your laptop. Thats the easiest way.

went to systems-admin-hardware drivers.Nothing there for wireless.said driver enabled in use.I already have network manager downloaded.Then the code lspci long list of STUFF means nothing to me.

---

### Post by amanda hill on 2008-12-31
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 System peripheral: JMicron Technologies, Inc. Unknown device 2382
02:00.2 SD Host controller: JMicron Technologies, Inc. Unknown device 2381
02:00.3 System peripheral: JMicron Technologies, Inc. Unknown device 2383
03:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 02)


Sorry now I know what you meant I told you i am need of very basic help

---

### Post by jrusso2 on 2008-12-31
I would post in the Dell forum if this is new this should be working out of the box.

---

### Post by amanda hill on 2008-12-31
trying to communicate with dell has proved worthless.

---

### Post by shane8002 on 2008-12-31
Try downloading ndiswrapper and then get the driver for your wireless. Go to administration and click on windows wireless drivers and then browse for your .inf file and the rest is simple it should work then.

---

### Post by jrusso2 on 2008-12-31
Here is the ndiswrapper instructions

[http://www.paralaptop.com/lenovo-laptops/step-by-step-installing-broadcom-bcm4310-into-ubuntu.html](http://www.paralaptop.com/lenovo-laptops/step-by-step-installing-broadcom-bcm4310-into-ubuntu.html)

---

### Post by cdtech on 2008-12-31
Same card I have. I have to go now but it's an idswrapper:
```
bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: ssb)
```

---

### Post by amanda hill on 2009-01-06
thankyou all my fault was using the wrong encryption key

---

### Post by Iowan on 2009-01-06
> **amanda hill said:**
> trying to communicate with dell has proved worthless.[This]("http://ubuntuforums.org/forumdisplay.php?f=342") Dell forum ;) 
Glad you got it solved!

---

