---
title: "RT5370 wireless connected but cant browse internet"
date: 2011-12-30
forum: Networking &amp; Wireless
---

### Post by jeromegee on 2011-12-30
Hi guys! Im new with Ubuntu and Im very much decided to leave Microsoft Windows behind. It seems I have a problem with my wireless adapter, my router sees the wireless N adapter under the wireless clients list, DHCP has asigned it an IP, but yet, I cant get on the internet.

Here`s the relevant info you might need:


```
**jeromegee@jeromeski:~$ lspci**
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)

00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)

00:1a.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)

00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)

00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)

00:1c.6 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 7 (rev b5)

00:1d.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a5)

00:1f.0 ISA bridge: Intel Corporation H67 Express Chipset Family LPC Controller (rev 05)

00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller (rev 05)

00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
``````
**jeromegee@jeromeski:~$ iwconfig**
lo        no wireless extensions.
eth0      no wireless extensions.
ra0       Ralink STA  ESSID:"nIMR0d.skyNET"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:0F:01:1B:0E:37   
          Bit Rate=135 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-37 dBm  Noise level:-63 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
``````
**jeromegee@jeromeski:~$ lsusb**
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 09da:000a A4 Tech Co., Ltd Port Mouse
Bus 002 Device 003: ID 148f:5370 Ralink Technology, Corp. 
Bus 002 Device 004: ID 04d9:1503 Holtek Semiconductor, Inc. Shortboard Lefty
``````
**jeromegee@jeromeski:~$ ifconfig**
eth0      Link encap:Ethernet  HWaddr 1c:6f:65:d8:8e:bb  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::1e6f:65ff:fed8:8ebb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:25233 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29175 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:21007744 (21.0 MB)  TX bytes:6489188 (6.4 MB)
          Interrupt:40 Base address:0xe000 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:934 errors:0 dropped:0 overruns:0 frame:0
          TX packets:934 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:84952 (84.9 KB)  TX bytes:84952 (84.9 KB)

ra0       Link encap:Ethernet  HWaddr 00:0f:11:71:24:02  
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:11ff:fe71:2402/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:53 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4855886 (4.8 MB)  TX bytes:2011603 (2.0 MB)
``````
**jeromegee@jeromeski:~$ iwconfig**
lo        no wireless extensions.
eth0      no wireless extensions.
ra0       Ralink STA  ESSID:"nIMR0d.skyNET"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:0F:01:1B:0E:37   
          Bit Rate=135 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-37 dBm  Noise level:-63 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
``````
**jeromegee@jeromeski:~$ lsmod | grep rt**
parport_pc             36962  0 
rt5370sta             669039  1 
parport                46562  3 parport_pc,ppdev,lp
``````
**jeromegee@jeromeski:~$ sudo lshw -C network**
[sudo] password for jeromegee: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 06
       serial: 1c:6f:65:d8:8e:bb
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=192.168.0.101 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:40 ioport:ee00(size=256) memory:fbeff000-fbefffff memory:fbef8000-fbefbfff

  *-network
       description: Wireless interface
       physical id: 1
       logical name: ra0
       serial: 00:0f:11:71:24:02
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=RALINK WLAN ip=192.168.0.102 multicast=yes wireless=Ralink STA
``````
**jeromegee@jeromeski:~$ iwlist scan**
lo        Interface doesn't support scanning.
eth0      Interface doesn't support scanning.
ra0       Scan completed :
          Cell 01 - Address: 00:1A:EF:10:9B:92
                    Protocol:802.11b/g
                    ESSID:"Rameses"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality=13/100  Signal level=-85 dBm  Noise level=-93 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

          Cell 02 - Address: 00:0F:01:1B:0E:37
                    Protocol:802.11b/g/n
                    ESSID:"nIMR0d.skyNET"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality=100/100  Signal level=-37 dBm  Noise level=-92 dBm
                    Encryption key:on
                    Bit Rates:150 Mb/s
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
``````

**jeromegee@jeromeski:~$ lsb_release -d**
Description:    Ubuntu 11.10
``````
**jeromegee@jeromeski:~$ uname -mr**
3.0.0-14-generic x86_64
``````
**jeromegee@jeromeski:~$ sudo /etc/init.d/networking restart**
* Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                   [ OK ]
``````
**jeromegee@jeromeski:~$ route -n**
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 ra0
192.168.0.0     0.0.0.0         255.255.255.0   U     2      0        0 ra0
``````
**jeromegee@jeromeski:~$ ping -c3 8.8.8.8**
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_req=1 ttl=54 time=53.3 ms
64 bytes from 8.8.8.8: icmp_req=2 ttl=54 time=58.4 ms
64 bytes from 8.8.8.8: icmp_req=3 ttl=54 time=50.4 ms

--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 50.481/54.074/58.404/3.276 ms
```

---

### Post by jeromegee on 2011-12-30
Please help.. I`ve been working on this for almost a week now and New Year is around the corner.

---

