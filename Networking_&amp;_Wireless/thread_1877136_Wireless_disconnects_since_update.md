---
title: "Wireless disconnects since update"
date: 2011-11-07
forum: Networking &amp; Wireless
---

### Post by Speedwagon on 2011-11-07
Since I updated to 11.10, I keep getting wireless disconnects after awhile.  A reboot always fixes the problem, though a logout does not.

The symptoms:
I'll come back to the computer, and it will just be disconnected from the network.  Attempting to reconnect doesn't work, it tries, but just keeps trying and never connects.  If I disable wireless, and re-enable, it says device not ready.

This started on 11.10, and I'm running a D-link card.

```
eth0      Link encap:Ethernet  HWaddr 6c:f0:49:0d:0b:9f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:46 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

wlan0     Link encap:Ethernet  HWaddr 1c:bd:b9:d2:ee:e0  
          inet addr:192.168.0.182  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::1ebd:b9ff:fed2:eee0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2802 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2714 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2313008 (2.3 MB)  TX bytes:597015 (597.0 KB)

```
```
*-network               
       description: Wireless interface
       product: AR5008 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 1c:bd:b9:d2:ee:e0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.0.0-12-generic firmware=N/A ip=192.168.0.182 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:fdef0000-fdefffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 03
       serial: 6c:f0:49:0d:0b:9f
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168d-2.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:46 ioport:9e00(size=256) memory:fdfff000-fdffffff memory:fdff8000-fdffbfff memory:fdf00000-fdf1ffff

```

---

### Post by praseodym on 2011-11-07
Hi,

shut off the hardware encryption of the driver:

```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```
I recommend WPA2-encryption if possible, not mixed WPA/WPA2.

---

### Post by Speedwagon on 2011-11-07
I'll give that a shot, and see what happens.  Thanks.

---

### Post by Speedwagon on 2011-11-09
So far, it seems to be working fine.  I'll post back in a few days, to update if it returns.

---

### Post by Speedwagon on 2011-11-09
Not fixed.  This morning, I went to my computer to find it asking for a network password.  When I hit connect, it just sits there again.

---

### Post by Speedwagon on 2011-11-13
Any other suggestions?

---

