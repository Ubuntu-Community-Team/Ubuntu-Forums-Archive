---
title: "Wireless Connection is slower than wired - Ubuntu 12.04"
date: 2013-02-24
forum: Networking &amp; Wireless
---

### Post by delangeloh on 2013-02-24
Since I replaced Windows 7 with Ubuntu **12.04.2 LTS (3.2.0-38-generic x86_64) **my wireless speeds have decreased dramatically. However, the wired connection works just fine. I thought that maybe my laptop or the wireless card was at fault, but when I use it at work it works fine (I get up to 10 Mb/s down, which is the max)... 
At my house, when wired, speedtest.net reports download speeds of up to **20 Mb/s** and up to** 5** up. On the other hand, when using WiFi I get at best **800 Kb/s to 1 Mb/s** down, but still** 5 Mb/s** up.
I don't know what else to do. I've changed the DNS settings, disabled IPv6 and followed some suggestions in the forum and have yet to find success. By the way, my ISP is Comcast.

Here are are my specs:

HP G42-243CL Notebook PC ([http://goo.gl/27se6](http://goo.gl/27se6))

```
lspci output
``````

02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

``````
lsusb output
``````

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04f2:b1aa Chicony Electronics Co., Ltd Webcam-101
Bus 005 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver

``````
ifconfig output
``````

eth0      Link encap:Ethernet  HWaddr c8:0a:a9:a1:d9:89  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:42 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3788 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3788 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:384359 (384.3 KB)  TX bytes:384359 (384.3 KB)

wlan0     Link encap:Ethernet  HWaddr 78:e4:00:af:f7:02  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::7ae4:ff:feaf:f702/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:32589 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33903 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:29675587 (29.6 MB)  TX bytes:7166674 (7.1 MB)

``````
iwconfig output
``````

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"LaCosaNostra"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 10:0D:7F:88:77:14   
          Bit Rate=65 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=58/70  Signal level=-52 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:11700   Missed beacon:0

eth0      no wireless extensions.

``````
lsmod output
``````

ath9k                 132428  0 
mac80211              506862  2 iwlwifi,ath9k
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
ath9k_common           14053  1 ath9k
ath9k_hw              411239  2 ath9k,ath9k_common
ath                    24067  3 ath9k,ath9k_common,ath9k_hw
wmi                    19256  1 hp_wmi
cfg80211              205774  4 iwlwifi,ath9k,mac80211,ath

``````
dmesg | grep "Atheros" output
``````

[   13.586985] ieee80211 phy0: Atheros AR9285 Rev:2 mem=0xffffc90002980000, irq=17

``````
sudo lshw -C network output
``````

izzy@masterpc:~$ sudo lshw -C network
[sudo] password for izzy: 
  *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 78:e4:00:af:f7:02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-38-generic firmware=N/A ip=192.168.1.3 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f0100000-f010ffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: c8:0a:a9:a1:d9:89
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=N/A latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:42 ioport:2000(size=256) memory:f0010000-f0010fff memory:f0000000-f000ffff memory:f0020000-f002ffff

``````
Restarting the network output
``````

 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                   [ OK ]

```

---

### Post by carl4926 on 2013-02-24
> but when I use it at work it works fineThis part intrigues me.

Do you mean, the same machine running Ubuntu with wireless?

---

### Post by delangeloh on 2013-02-25
> **carl4926 said:**
> This part intrigues me.

Do you mean, the same machine running Ubuntu with wireless?


Yes, same machine... but I finally found the solution: I turned off WMM under QoS menu. See, I have a Netgear 3500L wireless router, and after all this freaking time this is what kept my wireless so slow.

---

### Post by carl4926 on 2013-02-25
> **delangeloh said:**
> Yes, same machine... but I finally found the solution: I turned off WMM under QoS menu. See, I have a Netgear 3500L wireless router, and after all this freaking time this is what kept my wireless so slow.

Netgear.. me too
QoS is not enabled by default in mine

Anyway, happy you found the culprit

---

