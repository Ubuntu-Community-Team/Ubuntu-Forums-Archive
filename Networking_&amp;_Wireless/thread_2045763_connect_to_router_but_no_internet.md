---
title: "connect to router but no internet"
date: 2012-08-21
forum: Networking &amp; Wireless
---

### Post by gracias on 2012-08-21
I installed ubuntu 12.04 by wubi but found some problems with wireless connection.  I can connect to my router but that does not connect me to the Internet.  The router itself should be fine, because I can connect to the Internet via the router in Windows and by mobile devices.  More strangely, if I set up a hot-spot from my mobile phone, I can connect to the Internet via the hot-spot in Ubuntu, so I guess the wireless card should be fine as well.  I suspect there is something wrong with the configuration but it was a fresh system install.  Can anyone help me please?  Thanks.

Here are some information from ifconfig, iwconfig, etc.  

ifconfig
```


eth0      Link encap:Ethernet  HWaddr 00:1f:16:2d:7a:30
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:f2600000-f2620000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:76 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:4664 (4.6 KB)  TX bytes:4664 (4.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1e:65:ea:45:2e
          inet addr:192.168.0.103  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:65ff:feea:452e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19 errors:0 dropped:0 overruns:0 frame:0
          TX packets:140 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1705 (1.7 KB)  TX bytes:18545 (18.5 KB)


```
iwconfig


```


lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"HKBN_918343"
          Mode:Managed  Frequency:2.472 GHz  Access Point: 00:0C:43:91:83:43
          Bit Rate=57.8 Mb/s   Tx-Power=15 dBm
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=56/70  Signal level=-54 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:135   Missed beacon:0

eth0      no wireless extensions.


```
sudo lshw -C network
```


  *-network
       description: Ethernet interface
       product: 82567LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:1f:16:2d:7a:30
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.5.1-k firmware=1.8-3 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:44 memory:f2600000-f261ffff memory:f2625000-f2625fff ioport:1840(size=32)
  *-network
       description: Wireless interface
       product: PRO/Wireless 5100 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 00:1e:65:ea:45:2e
       width: 64 bits
       clo  *-network
       description: Ethernet interface
       product: 82567LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:1f:16:2d:7a:30
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.5.1-k firmware=1.8-3 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:44 memory:f2600000-f261ffff memory:f2625000-f2625fff ioport:1840(size=32)
  *-network
       description: Wireless interface
       product: PRO/Wireless 5100 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 00:1e:65:ea:45:2e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-23-generic firmware=8.83.5.1 build 33692 ip=192.168.0.103 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:47 memory:f2500000-f2501fff
ck: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-23-generic firmware=8.83.5.1 build 33692 ip=192.168.0.103 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:47 memory:f2500000-f2501fff


```
nm-tool
```

NetworkManager Tool

State: connected (global)

- Device: wlan0  [HKBN_918343] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        00:1E:65:EA:45:2E

  Capabilities:
    Speed:           1 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *HKBN_918343:    Infra, 00:0C:43:91:83:43, Freq 2472 MHz, Rate 54 Mb/s, Strength 67 WPA
    PPHome:          Infra, 00:1F:A4:82:E2:44, Freq 2412 MHz, Rate 54 Mb/s, Strength 70 WPA

  IPv4 Settings:
    Address:         192.168.0.103
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        00:1F:16:2D:7A:30

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


```

---

### Post by chili555 on 2012-08-22
I suggest that this may help: [http://ubuntuforums.org/showthread.php?t=2042332&highlight=11n_disable](http://ubuntuforums.org/showthread.php?t=2042332&highlight=11n_disable)

---

### Post by gracias on 2012-08-22
> **chili555 said:**
> I suggest that this may help: [http://ubuntuforums.org/showthread.php?t=2042332&highlight=11n_disable](http://ubuntuforums.org/showthread.php?t=2042332&highlight=11n_disable)

Amazing!  It works!  I've checked out some other posts but missed this one...  Thank you very much.

---

