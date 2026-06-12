---
title: "Cant use my trendnet stick"
date: 2012-05-24
forum: Networking &amp; Wireless
---

### Post by rogerdv on 2012-05-24
I recently got a Trendnet wifi stick with a SiS chipset. I googled about and found [this guide]("http://www.ehow.com/how_7288747_install-trendnet-tew_424ub-ubuntu.html"), but I get an error in sudo modprobe ndiswrapper, saying that module ndiswrapper can not be found. Im using precise, and noticed that a small detail has changed (ndiswrapper is installed in a single step, not two) and perhaps I missed something else. Is there some way to make this stick work?

---

### Post by chili555 on 2012-05-24
Let's try to install what's missing. With an ethernet connection, open a terminal and do:```
sudo apt-get install --reinstall ndiswrapper-common ndiswrapper-utils-1.9 ndiswrapper-dkms
```After it's done, then do:```
sudo modprobe ndiswrapper
```It it working now?

---

### Post by rogerdv on 2012-05-24
Made a quick test here and seems that this time an extra package was installed and the module was created. will try at home tonight with the actual stick to see what happens.

---

### Post by rogerdv on 2012-05-25
Ok, I completed the process without errors, I insert the stick, and nothing happens. should I get some signal of hardware being detected, even if I dont have wireless networks available?

---

### Post by chili555 on 2012-05-25
> should I get some signal of hardware being detected, even if I dont have wireless networks available?Do you mean some kind of pop-up? No. You can check under the hood in the terminal:```
iwconfig
```Do you have a wireless interface wlan0?```
dmesg | grep ndis
```Any errors or warnings?

---

### Post by rogerdv on 2012-05-25
Nop, no wlan0 interface, and also some errors in dmesg: 

> [  157.979204] ndiswrapper (load_sys_files:199): couldn't prepare driver 'sis163u'
[  157.979251] ndiswrapper (load_wrap_driver:121): couldn't load driver 'sis163u'


---

### Post by chili555 on 2012-05-25
Let's go back to the beginning. Please insert the device and post:```
lsusb
```Where did you get the .inf file? What else is available? Both .inf and .sys files? XP files? Vista files?

---

### Post by rogerdv on 2012-05-25
> Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 001 Device 008: ID 0457:0163 Silicon Integrated Systems Corp. 802.11 Wireless LAN Adapter


Copied the whole Windows XP folder from original CD, also I have to mention that Im using a 64 bits Ubuntu.

---

### Post by chili555 on 2012-05-25
I hope this doesn't come back to be a 64-bit issue. Please see this: [http://ubuntuforums.org/showthread.php?t=1238204](http://ubuntuforums.org/showthread.php?t=1238204)> After a long time trying to get my SiS163u wireless card working via Windows Wireless Drivers utility, I thought that I would try the XP drivers. The .inf file didn't work - was still getting the Hardware Not Found/Present dialogue box. **Rooted around and found a Windows '98 sis163u.inf driver and it installed and worked immediately.**The 98 driver is in the XP drivers folder BTW.I suggest you remove the XP files and install the 98 in their place. Do you need some guidance?

---

### Post by rogerdv on 2012-05-25
My mistake, I missed the most important part:

> [  157.691574] ndiswrapper version 1.57 loaded (smp=yes, preempt=no)
[  157.979196] ndiswrapper (check_nt_hdr:141): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[  157.979204] ndiswrapper (load_sys_files:199): couldn't prepare driver 'sis163u'
[  157.979251] ndiswrapper (load_wrap_driver:121): couldn't load driver 'sis163u'
[  157.979343] usbcore: registered new interface driver ndiswrapper
[ 8727.052877] ndiswrapper (check_nt_hdr:141): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[ 8727.052885] ndiswrapper (load_sys_files:199): couldn't prepare driver 'sis163u'
[ 8727.052937] ndiswrapper (load_wrap_driver:121): couldn't load driver 'sis163u'


As  you can see, in both cases the problem seems to be that the system is 64 bits, but the driver isnt. I guess the 7 driver wont work, isnt it?

---

### Post by chili555 on 2012-05-25
> As you can see, in both cases the problem seems to be that the system is 64 bits, but the driver isnt. I guess the 7 driver wont work, isnt it?No, the 7 driver will not work. I think your options are down to two. Buy a supported wireless device or install 32-bit.

---

### Post by rogerdv on 2012-05-25
Damn, I saved for 2 months to get that one (things are quite hard here).  Anyway, I have dual boot, I can use that while I get a a more linux friendly stick.

---

### Post by chili555 on 2012-05-25
Sorry about that. If you Google for 64-bit and sis163u, you will see many questions and no answers. You could also install 32-bit triple-boot, yes?

---

### Post by rogerdv on 2012-05-25
It is not worth to waste space just to have wifi under linux. Eventually I will sell this one and get another or we will get massive internet service for everyone, making wifi pointless.

---

