---
title: "Wifi Networks- Device Not Ready (Firmware missing) - Ralink RT5390 Card"
date: 2013-06-07
forum: Networking &amp; Wireless
---

### Post by JRBalu on 2013-06-07
Hi,

I've installed Xubuntu 13.04 in my HP dm1 Pavilion having RT5390 as wifi card. As per my understanding, the driver rt2800pci is built-in in kernel for wifi but it was too slow. So among the steps I tried, I installed RT5390 driver from the official website and loaded the module. But later I found that, the real issue was with the hardware encryption and it was solved by disabling it using following commands:

```

sudo modprobe -r rt2800pci
sudo modprobe rt2800pci nohwcrypt=1

```

Now the issue was solved. I got the same speed for wifi as that with windows 8. So I thought the additional RT5390 driver will be useless. So I unloaded it by typing:

```

sudo modprobe -r RT5390sta

``` 

Still no further issues. But when I restarted the computer, I am unable to connect to the wifi networks. It doesnot even lists the available wifi connections. What it shows is
> Device not ready. Firmware missing

Additional details:
```

sudo lshw -C network 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168 PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 06
       serial: 68:b5:99:d4:61:0a
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.7 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:40 ioport:2000(size=256) memory:90004000-90004fff memory:90000000-90003fff
  *-network DISABLED
       description: Wireless interface
       product: RT5390 [802.11 b/g/n 1T1R G-band PCI Express Single Chip]
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 90:00:4e:0e:02:3b
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=3.8.0-23-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:90100000-9010ffff



```

Can anybody help me please?

---

### Post by JRBalu on 2013-06-07
Thank God! I found solution in this thread --> [http://ubuntuforums.org/showthread.php?t=1864392](http://ubuntuforums.org/showthread.php?t=1864392).

Many many thanks to the user chilli555. his solution worked like a charm! saved many hours for me!

---

