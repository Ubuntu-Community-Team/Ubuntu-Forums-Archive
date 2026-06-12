---
title: "Wirless Link Quality is always 0%"
date: 2009-05-18
forum: Networking &amp; Wireless
---

### Post by koala114 on 2009-05-18
I've compiled rt73 driver from source code rt73-cvs-daily.tar.gz.
make, make install, modprobe -v rt73 each step seemed ok.
and I could get ip via dhcp.
```

[   61.048009] eth1: no IPv6 routers present
[  229.052151] ppdev0: registered pardevice
[  229.100031] ppdev0: unregistered pardevice
[  230.444307] ppdev0: registered pardevice
[  230.492353] ppdev0: unregistered pardevice
[  231.979770] ppdev0: registered pardevice
[  232.028218] ppdev0: unregistered pardevice
[  304.239099] rt73: init
[  304.239895] rt73: idVendor = 0x14b2, idProduct = 0x3c20 
[  304.243442] firmware: requesting rt73.bin
[  304.485584] rt73: using permanent MAC addr
[  304.485594] rt73: Active MAC addr: 00:0f:a3:7f:ff:ed
[  304.485600] rt73: Local MAC = 00:0f:a3:7f:ff:ed
[  304.487104] usbcore: registered new interface driver rt73
[  704.788834] rt73: driver version - 1.0.3.6 CVS
[  704.820872] rt73: using net dev supplied MAC addr
[  704.820904] rt73: Active MAC addr: 00:0f:a3:7f:ff:ed
[  704.820913] rt73: Local MAC = 00:0f:a3:7f:ff:ed
[  715.492008] wlan0: no IPv6 routers present
[  758.273257] NOHZ: local_softirq_pending 08
[  758.274064] NOHZ: local_softirq_pending 08
[  758.274783] NOHZ: local_softirq_pending 08
[  758.275494] NOHZ: local_softirq_pending 08
[  759.944105] NOHZ: local_softirq_pending 08
[  759.944922] NOHZ: local_softirq_pending 08
[  759.945635] NOHZ: local_softirq_pending 08
[  759.946340] NOHZ: local_softirq_pending 08
[  759.947046] NOHZ: local_softirq_pending 08
[  759.947753] NOHZ: local_softirq_pending 08

```

---

