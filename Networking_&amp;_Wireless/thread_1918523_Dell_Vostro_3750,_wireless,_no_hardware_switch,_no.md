---
title: "Dell Vostro 3750, wireless, no hardware switch, no connectivity"
date: 2012-02-01
forum: Networking &amp; Wireless
---

### Post by profhof on 2012-02-01
Hi There

I've been using the wireless network fine, but I switched it off with gnome-control-center and now I can't switch it back on. There is no physical hardware switch, but Ubuntu is reporting that the wireless is disabled by hardware switch.

I have the following parameters:


root@romainlap:~# lshw -C network
  *-network DISABLED      
       description: Wireless interface
       product: Centrino Wireless-N 1030
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 34
       serial: 4c:80:93:0d:33:e7
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=3.0.0-14-generic firmware=17.168.5.1 build 33993 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:51 memory:f2a00000-f2a01fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 06
       serial: 84:8f:69:b7:3d:c2
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168e-2.fw ip=192.168.10.32 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:49 ioport:3000(size=256) memory:f1804000-f1804fff memory:f1800000-f1803fff


root@romainlap:~# rfkill list
0: dell-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

root@romainlap:~# cat /var/lib/NetworkManager/NetworkManager.state

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


root@romainlap:~# uname -a
Linux romainlap 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:34:47 UTC 2011 i686 i686 i386 GNU/Linux


rfkill unblock doesn't do anything

root@romainlap:~# ifconfig wlan0 up
SIOCSIFFLAGS: Operation not possible due to RF-kill


I've downgraded the kernel from 3.0.0-15-generic in the hopes that this would magically fix my problem. So it looks like ubuntu is emulating the hardware switch, but I need the mechanism to switch this back on.

Any help on this would be greatly appreciated.

Thanks a lot

---

### Post by drpjkurian on 2012-02-01
To turn wireless off/on it's the blue "FN" key next to the windows key and "F2" at the same time. (You should see the green LED next to the power button go off/on as well)

If you hold down the "FN" key you can then use any of the "Blue" keys !!

---

### Post by critter42 on 2012-02-09
Inspiron 2200, same issue as OP - there is no hardware switch and the FN+F2 sequence does NOT work

---

### Post by chili555 on 2012-02-09
A Dell, you say? Please check posts #5 and following here: [http://ubuntuforums.org/showthread.php?t=1745681](http://ubuntuforums.org/showthread.php?t=1745681)

---

