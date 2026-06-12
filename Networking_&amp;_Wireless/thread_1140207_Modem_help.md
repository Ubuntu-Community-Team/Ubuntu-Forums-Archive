---
title: "Modem help"
date: 2009-04-27
forum: Networking &amp; Wireless
---

### Post by AdarshN on 2009-04-27
Hiya guys, I have decided to start using Ubuntu as my main OS.

Ok, before diving into my current problem, some general info of my laptop : 

OS : Dual booting Vista and Ubuntu
RAM : 1 GB
Graphics : nVidia GeforceGo 7400
HDD : 160 GB
Space alloted to Ubuntu : 15 GB
Modem : HDAUDIO Soft Data Fax Modem with SmartCP
Kernel version : 2.6.24-19-generic

I used scanModem to find out which chipset is in use. From what I understand, I think it's hsfmodem. Because this came up in the Modem.txt 
> 
Support type needed or chipset:	hsfmodem


Now, I went to the Linuxant download page : 
[http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php](http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php), 

pointing to hsfmodems and opted to download the package corresponding to my kernel version.
But when I try installing the package, after unzipping the package, I cannot install the package, because it gives me an error :
> 
Error : Dependency is not satisfiable: alsa-driver-linuxant


I think it got installed partially on my first attempt, but when I rebooted, and tried installing it again (just tried, I know you're not supposed to do that), it said that my system had broken dependencies. So I fixed that with **sudo apt-get install -f**.

I'm really stuck here, could you kindly help me out?
Please note that I'm a linux newbie...

---

### Post by hazza96 on 2009-05-05
Scroll ALL the way to the bottom of the page you linked to, it links to the package you need to install first.

---

