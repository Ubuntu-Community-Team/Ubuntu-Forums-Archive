---
title: "ASUS USB-N13 Wireless Receiver Problems in Ubuntu 11.10"
date: 2012-02-24
forum: Networking &amp; Wireless
---

### Post by Aytaya on 2012-02-24
I purchased the ASUS N13 usb wireless adapter since it advertised itself as being compatible with linux. However when I plug it in nothing happens. I looked on this forum, but none of the solutions work since the device ID on this one is not 0b05:1784 but is instead: 0b05:17ab. If anyone could help I would much appreciate it.

The entire result of lsusb follow:
> Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 005 Device 002: ID 046d:c531 Logitech, Inc. 
Bus 001 Device 004: ID 0b05:17ab ASUSTek Computer, Inc. 
Bus 002 Device 003: ID 04d9:2013 Holtek Semiconductor, Inc. 
Bus 002 Device 004: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 005: ID 046d:0a1f Logitech, Inc. 


iwconfig returns:
> ~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

I am on a completely clean install with no updates. I can connect the computer via ethernet for short periods of time, but I would prefer to find a way to get this working without having to do that.

---

### Post by flash63 on 2012-02-24
Hello,
follow the instructions for rtl8192cu V 3.3.2-3192 with DKMS.

[http://forum.ubuntuusers.de/topic/mein-wlan-stick-150n-von-sitecom-spinnt/#Treiberversion-3-3-2-3192](http://forum.ubuntuusers.de/topic/mein-wlan-stick-150n-von-sitecom-spinnt/#Treiberversion-3-3-2-3192)

modinfo 8192cu | egrep 'versi|filen|17AB'
```
filename:       /lib/modules/2.6.32-38-generic/updates/dkms/8192cu.ko
version:        v3.3.2_3192.20120103
srcversion:     5B323C24BF8EB2D52BDB625
alias:          usb:v[COLOR="Red"]0B05[/COLOR]p[COLOR="Red"]17AB[/COLOR]d*dc*dsc*dp*ic*isc*ip*
vermagic:       2.6.32-38-generic SMP mod_unload modversions 
parm:           rtw_chip_version:int
```
(you need an internet connection via cable to install the tools, headers and the driver)

---

### Post by chili555 on 2012-02-24
I am not sure it will work for you with kerenel 3.0xx. Please try it and if not, I will have another suggestion.

---

### Post by flash63 on 2012-02-24
> **chili555 said:**
> I am not sure it will work for you with kerenel 3.0xx. Please try it and if not, I will have another suggestion.

It is also tested with kernel 3.x (Ubuntu 11.10)

---

### Post by Aytaya on 2012-02-24
That seemed to work. Thanks a ton.

I felt bad about not being able to find a solution but seeing as the page was in German I feel better about it.

---

### Post by Aytaya on 2012-02-25
When i updated to 3.0.0-16 the adapter stopped working again. If I boot to 3.0.0-12 it works fine. Any ideas?

uninstalling and re installing worked.

Thanks again

---

### Post by flash63 on 2012-02-25
Maybe the following package is missing
```
sudo apt-get install --reinstall linux-headers-generic
```
This will install/reinstall the required header-packages for an kernel update and the driver can be built automatically via dkms.

---

