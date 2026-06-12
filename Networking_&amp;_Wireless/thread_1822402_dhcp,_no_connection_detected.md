---
title: "dhcp, no connection detected"
date: 2011-08-10
forum: Networking &amp; Wireless
---

### Post by fkh_63 on 2011-08-10
Hello,
After ubuntu did some updates, I restarted and then no wired connection was detected. 

The following may partly clarify the problem:



------------------------------------------------------------------------
**[SIZE=3]sudo dmesg | grep eth[/SIZE]**
(I dont get anything for this)
-----------------------------------------------------------------------
[SIZE=3]**ifconfig**[/SIZE]

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:128 errors:0 dropped:0 overruns:0 frame:0
          TX packets:128 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10344 (10.3 KB)  TX bytes:10344 (10.3 KB)
---------------------------------------------------------------------

[SIZE=3]**lspci**[/SIZE]
00:00.0 Host bridge: Intel Corporation Device 0100 (rev 09)
00:01.0 PCI bridge: Intel Corporation Sandy Bridge PCI Express Root Port (rev 09)
00:16.0 Communication controller: Intel Corporation Cougar Point HECI Controller #1 (rev 04)
00:16.3 Serial controller: Intel Corporation Cougar Point KT Controller (rev 04)
00:19.0 Ethernet controller: Intel Corporation Device 1502 (rev 04)
00:1a.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Cougar Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 1 (rev b4)
00:1c.2 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 3 (rev b4)
00:1d.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #1 (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a4)
00:1f.0 ISA bridge: Intel Corporation Device 1c4e (rev 04)
00:1f.2 SATA controller: Intel Corporation Cougar Point 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation Cougar Point SMBus Controller (rev 04)
01:00.0 VGA compatible controller: ATI Technologies Inc Device 68f9
03:00.0 USB Controller: NEC Corporation Device 0194 (rev 03)
------------------------------------------------------------------------------------
------------------------------------------------------------------------------------

Thanks,

---

### Post by chili555 on 2011-08-10
What does this tell us?```
sudo modprobe e1000e
dmesg | grep e100
lspci -nn | grep 0200
```Thanks.

---

### Post by fkh_63 on 2011-08-11
So the following is the result,

[SIZE=3]**sudo modprobe e1000e**[/SIZE]
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist-modem, it will be ignored in a future release.

[SIZE=3]**dmesg | grep e100**[/SIZE]
[58542.311120] e1000e: Intel(R) PRO/1000 Network Driver - 1.0.2-k2
[58542.311125] e1000e: Copyright (c) 1999-2008 Intel Corporation.

[SIZE=3]**lspci -nn | grep 0200**[/SIZE]
00:19.0 Ethernet controller [0200]: Intel Corporation Device [8086:1502] (rev 04)

[SIZE=3]**dmesg | grep 00:19**[/SIZE]
[    1.505413] pci 0000:00:19.0: reg 10 32bit mmio: [0xe1500000-0xe151ffff]
[    1.505418] pci 0000:00:19.0: reg 14 32bit mmio: [0xe1580000-0xe1580fff]
[    1.505423] pci 0000:00:19.0: reg 18 io port: [0x4040-0x405f]
[    1.505458] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    1.505461] pci 0000:00:19.0: PME# disabled


[SIZE=3]**lsb_release -a**[/SIZE]
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 10.04.3 LTS
Release:    10.04
Codename:    lucid

---

### Post by chili555 on 2011-08-11
The module e1000e is correct for your device, but it's not covered by the version or e1000e in 10.04 LTS, which is version 1.0.2-k2. In Natty, the driver version 1.2.20-k2 covers your device. You could upgrade to Natty or you could compile a later driver version. [http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=15817](http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=15817)

Do you have wireless availability? Downloading and installing this file and the necessary build tools without any connectivity will be daunting but possible.

I will be glad to help you in either case.

---

### Post by fkh_63 on 2011-08-11
I don´t have wireless, but I´ll try to figure it out in some way. If not, surely I´ll be back to ask for more ideas. 

Thanks

---

### Post by chili555 on 2011-08-11
I'll be very glad to help in either case. Post back and let me know.

---

