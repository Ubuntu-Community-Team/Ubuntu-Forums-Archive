---
title: "Problems enabling Atheros AR928X Wireless Card on 10.10 x64"
date: 2011-05-17
forum: Networking &amp; Wireless
---

### Post by lun7200 on 2011-05-17
Just started getting wireless card problems on 10.10 x64

after doing ```
lshw -class network 
```

I get

```
*-network DISABLED
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 01
       serial: 00:23:4d:c3:30:27
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.35-25-generic firmware=N/A latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:23 memory:c2000000-c200ffff
```

If I try to run ```
sudo ifconfig wlan0 up
```

I get ```
SIOCSIFFLAGS: Operation not possible due to RF-kill
```

Its an HP G60 laptop with the wireless switch, in this case its a button, next to power button on top. the light on the wifi is orange and not blue and will not enable when you press it. The wireless card works fine on Windows Vista but not on Ubuntu.

thanks

---

### Post by poolet on 2011-05-17
Your wireless card is not automatically detected.. Follow the link below and install it manually...

[https://help.ubuntu.com/community/WifiDocs/Device/Atheros/AR9285](https://help.ubuntu.com/community/WifiDocs/Device/Atheros/AR9285)

EDIT:: Also 

check the link below before you do anything with drivers::

[http://pkadetiloye.blogspot.com/2010/11/ubuntu-wireless-disabled-siocsifflags.html](http://pkadetiloye.blogspot.com/2010/11/ubuntu-wireless-disabled-siocsifflags.html)
[URL="http://pkadetiloye.blogspot.com/2010/11/ubuntu-wireless-disabled-siocsifflags.html"]
[FONT=&quot][/FONT][/URL]

---

