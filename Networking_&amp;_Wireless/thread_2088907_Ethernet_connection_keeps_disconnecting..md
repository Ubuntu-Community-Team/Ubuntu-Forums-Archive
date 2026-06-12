---
title: "Ethernet connection keeps disconnecting."
date: 2012-11-27
forum: Networking &amp; Wireless
---

### Post by Vermonster on 2012-11-27
Edit: I migrated to Fedora 17, instead of Ubuntu as the issues where still not fixed. Easier than not having any internet connection.

Constantly disconnects and reconnects. Also, its really slow as compared to Windows seven. I am currently running Ubuntu 12.10, as I had no internet connection with Ethernet with Lubuntu and various other distributions.

First before it drops the connection, the internet runs very slow. A few seconds later the internet drops and goes out for about 30 seconds. It than reconnects on its own and recycles. Any help would be appreciative, I am trying to stay away from Windows. 
> 
eth0      Link encap:Ethernet  HWaddr 50:e5:49:9d:83:cb  
          inet addr:10.0.0.2  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::52e5:49ff:fe9d:83cb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:307641 errors:0 dropped:0 overruns:0 frame:0
          TX packets:181953 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:396904238 (396.9 MB)  TX bytes:22227698 (22.2 MB)
          Interrupt:43 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8569 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8569 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:878642 (878.6 KB)  TX bytes:878642 (878.6 KB)

> 
PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 06
       serial: 50:e5:49:9d:83:cb
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=10.0.0.2 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:43 ioport:de00(size=256) memory:dfeff000-dfefffff memory:dfef8000-dfefbfff


Any ideas?

---

### Post by varunendra on 2012-11-29
> **Vermonster said:**
> Edit: I migrated to Fedora 17, instead of Ubuntu as the issues where still not fixed.
Was your problem fixed in fedora ? Would be interesting to know if it uses the same r8169 driver and is still more stable than Ubuntu.

If you want to give ubuntu another shot, try the proprietary r8168 driver by realtek - [http://ubuntuforums.org/showpost.php?p=12333294&postcount=5](http://ubuntuforums.org/showpost.php?p=12333294&postcount=5)

Regards,
Varun

---

### Post by Vermonster on 2012-12-03
> **varunendra said:**
> Was your problem fixed in fedora ? Would be interesting to know if it uses the same r8169 driver and is still more stable than Ubuntu.

If you want to give ubuntu another shot, try the proprietary r8168 driver by realtek - [http://ubuntuforums.org/showpost.php?p=12333294&postcount=5](http://ubuntuforums.org/showpost.php?p=12333294&postcount=5)

Regards,
Varun

Yes, the problem is fixed within Fedora, although I don't like Fedora as much. lubuntu was not giving me any internet connection, also.

---

