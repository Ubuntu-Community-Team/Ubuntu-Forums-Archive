---
title: "Ubuntu 12.04 cannot connect to network using Ralink 2500"
date: 2012-09-15
forum: Networking &amp; Wireless
---

### Post by PlanoAlto on 2012-09-15
I have a Dell Inspiron 530 which just recently saw an installation of Ubuntu 12.04. While I could connect to the Internet through the wireless card during the install process, the actual installation afforded me no such luck. I am running an unsecured network, but eventually plan to up the security to WPA2 or WEP.

Relevant output of "sudo lshw":
```
           *-network
                description: Wireless interface
                product: RT2500 Wireless 802.11bg
                vendor: Ralink corp.
                physical id: 1
                bus info: pci@0000:02:01.0
                logical name: wlan0
                version: 01
                serial: 00:0f:66:f2:dd:09
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rt2500pci driverversion=3.2.0-29-generic firmware=N/A ip=192.168.1.117 latency=64 link=yes multicast=yes wireless=IEEE 802.11bg
                resources: irq:16 memory:fddfc000-fddfdfff
```Relevant output of "sudo lspci":
```
02:01.0 Network controller: Ralink corp. RT2500 Wireless 802.11bg (rev 01)
```Attempt to run "ping -I wlan0 google.com":
```
PING google.com (74.125.226.193) from 192.168.1.144 wlan0: 56(84) bytes of data.
From joe-pc-ubuntu (192.168.1.117) icmp_seq=1 Destination Host Unreachable
From joe-pc-ubuntu (192.168.1.117) icmp_seq=2 Destination Host Unreachable
From joe-pc-ubuntu (192.168.1.117) icmp_seq=3 Destination Host Unreachable
^C
--- google.com ping statistics ---
5 packets transmitted, 0 received, +3 errors, 100% packet loss, time 4022ms
pipe 3
```Result of "cat /etc/network/interfaces"
```
auto lo
iface lo inet loopback
```I feel like my issue should be as simple as adding it to the configuration file, but somehow I'm not convinced. Right now I am able to ssh to this box using the 192.168.1.144 address (ostensibly for wlan0), and it has a wall connection set up as well. I even checked Ralink's site for a driver, but I had to compile it from source and it expected me to be running either of the geriatric kernels 2.4 or 2.6.

Please let me know if I should paste the output of any other commands here as I attempt to get this machine connected to the Internet wirelessly :)

---

