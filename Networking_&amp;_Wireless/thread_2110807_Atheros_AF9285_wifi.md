---
title: "Atheros AF9285 wifi"
date: 2013-01-31
forum: Networking &amp; Wireless
---

### Post by msjankovich on 2013-01-31
Hello everybody, I am new to this forum and linux in general. I searched for solution of this problem, but everything I tried didn't work. BTW sorry for my english.
I have Mint 14 KDE and need to enable wifi. I can connect to my network but cannot ping the router or any site. My wireless card is Atheros AF9285. Roter is D-Link N150. I don't think the problem is with the router or card because on windows it works fine. However, on Mint I see my network and can log with password (WPA/WPA2) but impossible to open any site or just ping the router.
I tried with backport compact drivers and some other stuff I googled, but no change. Here is some relevant output:


```
milos@fb ~ $ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
^C
--- 192.168.0.1 ping statistics ---
6 packets transmitted, 0 received, 100% packet loss, time 5041ms


milos@fb ~ $ uname -a
Linux fb 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:32:08 UTC 2012 i686 i686 i686 GNU/Linux


milos@fb ~ $ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:26:91:d2:59  
          inet6 addr: fe80::223:26ff:fe91:d259/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5404 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4459 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6000134 (6.0 MB)  TX bytes:548639 (548.6 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:568 errors:0 dropped:0 overruns:0 frame:0
          TX packets:568 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:81098 (81.0 KB)  TX bytes:81098 (81.0 KB)

wlan0     Link encap:Ethernet  HWaddr 5c:ac:4c:14:6b:37  
          inet addr:192.168.0.103  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::5eac:4cff:fe14:6b37/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:50 errors:0 dropped:0 overruns:0 frame:0
          TX packets:218 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9135 (9.1 KB)  TX bytes:36696 (36.6 KB)


milos@fb ~ $ sudo iwconfig
wlan0     IEEE 802.11bgn  ESSID:"alpinista"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 90:94:E4:AB:CE:1A   
          Bit Rate=65 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          Link Quality=70/70  Signal level=-29 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:2  Invalid misc:23   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.


milos@fb ~ $ rfkill list
0: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no
1: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no


milos@fb ~ $ sudo lshw -class network
  *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 5c:ac:4c:14:6b:37
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.5.0-17-generic firmware=N/A ip=192.168.0.103 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f0500000-f050ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 06
       serial: 00:23:26:91:d2:59
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168e-2.fw latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:42 ioport:5000(size=256) memory:f0a04000-f0a04fff memory:f0a00000-f0a03fff

```

I am writing using wired connection which works fine. But I would really like to make wifi work if possible at all with atheros.

---

