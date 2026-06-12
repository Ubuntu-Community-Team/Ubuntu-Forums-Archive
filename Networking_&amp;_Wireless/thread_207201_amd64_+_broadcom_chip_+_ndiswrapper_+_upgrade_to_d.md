---
title: "amd64 + broadcom chip + ndiswrapper + upgrade to dapper = no work"
date: 2006-07-01
forum: Networking &amp; Wireless
---

### Post by onlynone on 2006-07-01
I installed Breezy Badger a few months ago on my laptop and everything worked very well. I have a 64 bit laptop with a broadcom wireless chip, I got it working with ndiswrapper without too many issues. I then noticed the other day that an upgrade to Dapper was available, so I went through with it. Upon rebooting wireless no longer worked.

I searched through the forums and help pages and found out about the new broadcom drivers included in Dapper. I didn't want to use the new drivers since ndiswrapper was working well for me. So I blacklisted the bcm43xx module and ndiswrapper seemed to start working again. But I can't set the essid, when I try to, nothing happens.

For reference, here's some info that may help:

My kernel version:
```
swillis@mira:~>uname -a
Linux mira 2.6.15-23-amd64-generic #1 SMP PREEMPT Tue May 23 13:45:47 UTC 2006 x86_64 GNU/Linux
```

Broadcom hardware info:
```
swillis@mira:~>lspci | grep Broad
0000:02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
```

My ndiswrapper drivers:
```
swillis@mira:~>ndiswrapper -l
Installed ndis drivers:
netbc564                driver present, hardware present
```

dmesg after inserting ndiswrapper:
```
swillis@mira:~>sudo modprobe ndiswrapper
swillis@mira:~>sudo dmesg -c
[  926.886782] ndiswrapper version 1.8 loaded (preempt=yes,smp=yes)
[  926.889867] ndiswrapper (load_pe_images:571): fixing KI_USER_SHARED_DATA address in the driver
[  926.891352] ndiswrapper: driver netbc564 (,10/01/2002,3.70.17.5) loaded
[  926.891664] ACPI: PCI Interrupt 0000:02:02.0[A] -> Link [LNK3] -> GSI 17 (level, low) -> IRQ 225
[  926.894010] ndiswrapper: using irq 225
[  927.339523] wlan0: vendor: ''
[  927.339529] wlan0: ndiswrapper ethernet device 00:90:4b:55:aa:79 using driver netbc564, 14E4:4320.5.conf
[  927.339544] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA

```

Taking wlan0 down:
```
swillis@mira:~>sudo ifdown wlan0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/wlan0/00:90:4b:55:aa:79
Sending on   LPF/wlan0/00:90:4b:55:aa:79
Sending on   Socket/fallback
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Invalid argument.
```

dmesg after taking wlan0 down:
```
swillis@mira:~>sudo dmesg -c
[  931.970536] wlan0: no IPv6 routers present
[  958.048262] ndiswrapper (iw_set_encr:893): removing encryption key 0 failed (C0010015)
```

bringing wlan0 up:
```
swillis@mira:~>sudo ifup wlan0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/wlan0/00:90:4b:55:aa:79
Sending on   LPF/wlan0/00:90:4b:55:aa:79
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
...
```

Any ideas?

---

### Post by onlynone on 2006-07-11
I just wanted to see if anyone might have some input into this. I haven't gotten any replies so I thought I would try to bump this up to the top of the forum.

---

### Post by blackdahliamurder on 2006-07-11
```
sudo iwconfig wlan0 essid YOURESSIDHERE
```

---

