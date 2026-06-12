---
title: "Tp-Link USB dongle: Very erratic Wifi connection in Ubuntu 12.04"
date: 2013-05-28
forum: Networking &amp; Wireless
---

### Post by guilleing on 2013-05-28
Hello, Ubuntu beginner here.
I have dual boot with Ubuntu 12.04 x64 and my old Windows 7 partition. I have a USB dongle: Tp-Link TL-WN722N, and a Tp-Link PCI Wifi adapter; but I use the USB dongle(wlan1), since with the usb extension cable, it gets better reception.
I have a Wifi connection with WPA2-AES encryption. In my Windows partition and other devices works fine, but it has a very erratic behaviour in Ubuntu. It connects and reconnects constantly, or works well for a couple of minutes and then very slowly (It's happening right now, lol). Sometimes, the Wicd manager freezes while "disconnecting active connections" or "obtaining IP adress". 

I tried:
Fixing the Wifi channel and adjusting the beacon interval (at the beginning I thought it was a router's problem).
Disabling IPv6.
Using Wicd (I still use it, since I like it more than Network Manager)
Disabling wlan0 (the PCI adapter).
... and other random fixes(sorry, I don't really remember) I found online that seem to have worked with other people, but not with me :(


Although I have disabled wlan0, I think that the connection works better when that adapter is unplugged (anyway, the connection is still erratic using only the USB dongle).

Sometimes the connection doesn't work at all, but does after a reboot. Also, whenever I boot with a Live CD, it just works. It might be a driver's problem?.



Outputs that might be helpfull:

```
04:05.0 Network controller [0280]: Atheros Communications Inc. AR5416 Wireless Network Adapter [AR5008 802.11(a)bgn] [168c:0023] (rev 01)
    Subsystem: Atheros Communications Inc. Device [168c:3071]
    Kernel driver in use: ath9k
--
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Subsystem: ASUSTeK Computer Inc. P8P67 and other motherboards [1043:8432]
    Kernel driver in use: r8169


```

ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 20:cf:30:ad:fc:26  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:48 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5768 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5768 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:505187 (505.1 KB)  TX bytes:505187 (505.1 KB)

wlan0     Link encap:Ethernet  HWaddr f8:d1:11:74:5e:64  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:428653 errors:0 dropped:0 overruns:0 frame:0
          TX packets:442102 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:355995605 (355.9 MB)  TX bytes:68748746 (68.7 MB)

wlan1     Link encap:Ethernet  HWaddr d8:5d:4c:99:fb:61  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:25290 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3490 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3940602 (3.9 MB)  TX bytes:563218 (563.2 KB)


```

Iwconfig:
```
lo        no wireless extensions.

wlan1     IEEE 802.11bgn  ESSID:"MyESSID"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: 74:EA:3A:AE:F3:08   
          Bit Rate=135 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=46/70  Signal level=-64 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1   Missed beacon:0

wlan0     IEEE 802.11bgn  ESSID:"MyESSID"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: 74:EA:3A:AE:F3:08   
          Bit Rate=11 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=28/70  Signal level=-82 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:3  Invalid misc:1013   Missed beacon:0

eth0      no wireless extensions.


```

sudo lshw -C network:
```
 *-network               
       description: Wireless interface
       product: AR5416 Wireless Network Adapter [AR5008 802.11(a)bgn]
       vendor: Atheros Communications Inc.
       physical id: 5
       bus info: pci@0000:04:05.0
       logical name: wlan0
       version: 01
       serial: f8:d1:11:74:5e:64
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-44-generic firmware=N/A ip=192.168.1.104 latency=168 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:20 memory:febe0000-febeffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 06
       serial: 20:cf:30:ad:fc:26
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168e-2.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:48 ioport:e800(size=256) memory:fdfff000-fdffffff memory:fdff8000-fdffbfff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@3:2
       logical name: wlan1
       serial: d8:5d:4c:99:fb:61
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ath9k_htc driverversion=3.2.0-44-generic firmware=1.3 ip=192.168.1.103 link=yes multicast=yes wireless=IEEE 802.11bgn


```

---

### Post by guilleing on 2013-06-01
Anyone? :s

---

### Post by wildmanne39 on 2013-06-01
Hi, please try:
```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```
Thanks

---

