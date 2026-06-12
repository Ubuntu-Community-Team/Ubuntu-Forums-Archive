---
title: "NETGEAR WNDA3100 on 10.10 amd64"
date: 2011-04-13
forum: Networking &amp; Wireless
---

### Post by jameswelle on 2011-04-13
Hi, I am trying to get my NETGEAR WNDA3100 wireless USB adapter to work on Ubuntu 10.10 amd64.

I was able to install the ndisgtk package and use that to install the bcmwlhigh6.inf driver. I got the .inf file from my Windows 7 amd64 install where the adapter is working.

I used "ndiswrapper -l" and "lsusb" to verify everything was installed.

However, I still appear to have no wireless network connection available.

I installed gnome-network-admin and ran that and I do not have a "Connections" tab in the UI.

Is there any way to get this working? Would installing Ubuntu 11.04 help?

Thanks!
James

---

### Post by chili555 on 2011-04-13
> I got the .inf file from my Windows 7 amd64 install where the adapter is working.This is from *man ndiswrapper-1.9*:> DESCRIPTION
       ndiswrapper is two parts: user space tool that is used to install ***Windows XP*** drivers and kernel module to load the Windows XP drivers. Both are called ndiswrapper.I suspect the Windows 7 .inf and .sys file are not going to work.

---

### Post by jameswelle on 2011-04-13
Thanks, do you know if 11.04 will have any better support for this our would my best option be to try find some XP amd64 drivers?

---

### Post by chili555 on 2011-04-13
There are a couple of versions, if my googling skills are accurate. So we know what we're working with, please run and post:```
lsusb
```If it is in fact a Broadcom, it may simply need firmware. In my own opinion, ndiswrapper is no remedy for missing firmware.

11.04 is not going to include proprietary firmware, codecs or anything else proprietary. There is no reason we can't decide to download it and install it after the base install however.

---

### Post by jameswelle on 2011-04-13
Here is the output of lsusb.
 
```
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 011: ID 045e:0723 Microsoft Corp. LifeCam VX-7000 (UVC-compliant)
Bus 001 Device 010: ID 413c:3016 Dell Computer Corp. Optical 5-Button Wheel Mouse
Bus 001 Device 009: ID 047f:0410 Plantronics, Inc. 
Bus 001 Device 008: ID 045e:00dd Microsoft Corp. Comfort Curve Keyboard 2000 V1.0
Bus 001 Device 007: ID 0846:9011 NetGear, Inc. WNDA3100(v2) 802.11n
Bus 001 Device 006: ID 05dc:a788 Lexar Media, Inc. 
Bus 001 Device 005: ID 0424:2504 Standard Microsystems Corp. USB 2.0 Hub
Bus 001 Device 004: ID 0424:2504 Standard Microsystems Corp. USB 2.0 Hub
Bus 001 Device 003: ID 03f0:2a12 Hewlett-Packard 
Bus 001 Device 002: ID 059f:100a LaCie, Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by chili555 on 2011-04-14
> ID 0846:9011 NetGear, Inc. WNDA3100(v2) 802.11nThere is no native Linux driver for this chipset quite yet. Your best and perhaps only solution is ndiswrapper. Do you have the Netgear install CD that came with the device? We ought to be able to find the 64-bit XP .inf and .sys files there.

---

### Post by jameswelle on 2011-04-14
The latest software is at [http://kb.netgear.com/app/products/model/a_id/2610](http://kb.netgear.com/app/products/model/a_id/2610)
 
I tried installing that software on a Windows Server 2003 R2 machine to get a 64-bit XP driver, but the software wouldn't install on that OS.
 
There is an article about which drivers have Vista x64 support. Maybe XP x64 is not supported at all.
 
[http://kb.netgear.com/app/answers/detail/a_id/2731/session/L2F2LzEvc2lkL0V6bktOc3Jr](http://kb.netgear.com/app/answers/detail/a_id/2731/session/L2F2LzEvc2lkL0V6bktOc3Jr)
 
If that is the case, is there a similar adapter I could buy that would work in Ubuntu 10.10 amd64?

---

### Post by jameswelle on 2011-04-14
For example, would this PCI wireless card work?
 
[http://www.newegg.com/Product/Product.aspx?Item=N82E16833122163](http://www.newegg.com/Product/Product.aspx?Item=N82E16833122163)

---

### Post by chili555 on 2011-04-14
See if this helps.

---

### Post by jawilljr on 2011-04-14
Read [this thread.](http://ubuntuforums.org/showthread.php?t=1383708)

Jerry

---

### Post by jameswelle on 2011-04-15
I think the difference between my setup and the other thread is I am trying to run on an am64 install.
 
I tried the drivers that were posted in the .zip file in this thread and after installing using ndisgtk and rebooting, lsusb, ndisgtk, and ndiswrapper all just hang when I try to launch them.

---

### Post by chili555 on 2011-04-15
Were the .cat files in the folder where you loaded the .inf? Did you delete the 32-bit .sys and .cat files first?

---

### Post by jameswelle on 2011-04-16
All the files are there. I didn't delete the 32-bit versions. Should I try that?

---

### Post by chili555 on 2011-04-16
yes, I suggest you do. Remove the installed driver first:```
sudo ndiswrapper -e bcmwlhigh5
```Then delete the 32-bit parts and reinstall with ndisgtk. Any improvement?

---

### Post by jameswelle on 2011-04-16
No, it still hangs after installing with only the 64-bit drivers available. The hang is gone when I uninstall the driver.
 
The location where the drivers are when I install with ndisgtk does not matter, right? Installing should copy them to whatever location the OS needs them at, right?

I may just install the 32-bit OS to see if I can get wireless working that way.

---

### Post by chili555 on 2011-04-16
> The location where the drivers are when I install with ndisgtk does not matter, right? Installing should copy them to whatever location the OS needs them at, right?Right; in /etc/ndiswrapper.> I may just install the 32-bit OS to see if I can get wireless working that way. I hope it works; I am out of ideas.

---

### Post by jameswelle on 2011-04-24
I was able to get the adapter working by installing the x86 version of 10.10, installing the drivers you supplied with ndisgtk, and turning off WPA2 on my router. I am only able to connect with my wireless router open. There are a couple of threads about getting WPA2 to work with the Broadcom driver but they did not work for me. Thanks for all your help.

---

### Post by lookabout on 2011-07-17
> **jameswelle said:**
> The latest software is at [http://kb.netgear.com/app/products/model/a_id/2610](http://kb.netgear.com/app/products/model/a_id/2610)
 
I tried installing that software on a Windows Server 2003 R2 machine to get a 64-bit XP driver, but the software wouldn't install on that OS.
 
There is an article about which drivers have Vista x64 support. Maybe XP x64 is not supported at all.
 
[http://kb.netgear.com/app/answers/detail/a_id/2731/session/L2F2LzEvc2lkL0V6bktOc3Jr](http://kb.netgear.com/app/answers/detail/a_id/2731/session/L2F2LzEvc2lkL0V6bktOc3Jr)
 
If that is the case, is there a similar adapter I could buy that would work in Ubuntu 10.10 amd64?

just saw a new version of the WNDA3100v2 software on the netgear site:[http://support.netgear.com/app/answers/detail/a_id/18580/kw/wnda3100v2](http://support.netgear.com/app/answers/detail/a_id/18580/kw/wnda3100v2)

extract: 
      ***WNDA3100v2* Software Version 1.3**

       
                   **[SIZE=3][COLOR=#330066]Driver Details:[/COLOR][/SIZE]**
 Windows XP(32/64): Driver version 5.60.180.11  and utility version 1.0.3.15

HTH
Carl

---

