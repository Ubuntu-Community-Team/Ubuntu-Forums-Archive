---
title: "Not able to turn on wireless radio in my Acer Aspire 4710z"
date: 2011-06-18
forum: Networking &amp; Wireless
---

### Post by arindamlala on 2011-06-18
Hi All,

I have just installed Ubuntu 11.04 in my acer aspire 4710z laptop. After logging in, I am not able to turn on Wireless Radio, hence not able to connect to my wireless router. I am new to ubuntu and step by step guidance will be appreciated. 

arindam@arindam-ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


arindam@arindam-ubuntu:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 064e:a101 Suyin Corp. Acer CrystalEye Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


arindam@arindam-ubuntu:~$ ls -ltr /sys/devices/platform/acer-wmi/
total 0
-rw-r--r-- 1 root root 4096 2011-06-18 20:34 uevent
lrwxrwxrwx 1 root root    0 2011-06-18 20:34 subsystem -> ../../../bus/platform
drwxr-xr-x 4 root root    0 2011-06-18 20:34 rfkill
-rw-r--r-- 1 root root 4096 2011-06-18 20:38 threeg
drwxr-xr-x 2 root root    0 2011-06-18 20:38 power
-r--r--r-- 1 root root 4096 2011-06-18 20:38 modalias
-r--r--r-- 1 root root 4096 2011-06-18 20:38 interface
lrwxrwxrwx 1 root root    0 2011-06-18 20:38 driver -> ../../../bus/platform/drivers/acer-wmi
arindam@arindam-ubuntu:~$ 


Thanks,
Arindam

---

### Post by chili555 on 2011-06-18
We'd like to also see:```
lspci -nn
rfkill list all
```Thanks.

---

### Post by arindamlala on 2011-06-19
Hi...

The problem is solved now. I have followed the instructions from the below thread and its working now. Thanks a lot.. a great forum. 

[http://ubuntuforums.org/showthread.php?p=10720776#post10720776](http://ubuntuforums.org/showthread.php?p=10720776#post10720776)

---

