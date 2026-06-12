---
title: "Wireless, ipw2200, Thinkpad T42, Jaunty"
date: 2009-09-26
forum: Networking &amp; Wireless
---

### Post by TimGS on 2009-09-26
I have a T42 that originally had Fluxbuntu 7.10 - now upgraded via Hardy and Intrepid to Jaunty.

On neither Intrepid or Jaunty has the wireless worked. It was fine with Hardy.

I have been running wicd - it shows the networks available, but hangs on 'Obtaining an IP address'.

The hardware is recognised in lshw:
```
-network:1 DISABLED
                description: Wireless interface
                product: PRO/Wireless 2200BG [Calexico2] Network Connection
                vendor: Intel Corporation
                physical id: 2
                bus info: pci@0000:02:02.0
                logical name: eth0
                version: 05
                serial: 00:0e:35:61:88:ca
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=64 maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=unassociated

```

I did see this [https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.27/+bug/297390]("https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.27/+bug/297390") but I didn't have the backports modules installed anyway. Also, more curiously, I don't appear to have the ibm_cw_* modules anyway, and I cannot add them via sudo modprobe...

Any ideas?

-- Tim.

---

### Post by TimGS on 2009-09-27
Problem hopefully solved - in a manner of speaking. Am going to do re-install Hardy, with a normal Ubuntu desktop install.

It seems a few people have had problems with Jaunty and the ipw2200, not all solved.

-- Tim.

---

