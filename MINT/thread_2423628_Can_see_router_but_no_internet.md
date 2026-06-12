---
title: "Can see router but no internet"
date: 2019-07-26
forum: MINT
---

### Post by triplemaya on 2019-07-26
Pc can see the router just fine but no internet. All other boxes on the network seeing the internet just fine. 

Running Linux Mint MATE 17

I can ping 8.8.8.8 ok
I cannot ping any external site.

This is all the commands I know to do to get information:


 ```
# ifconfig -a
eth1      Link encap:Ethernet  HWaddr 74:d4:35:70:08:07  
          inet addr:192.168.0.6  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: 2a02:c7d:916:a000:76d4:35ff:fe70:807/64 Scope:Global
          inet6 addr: fdc4:199f:b47f:0:76d4:35ff:fe70:807/64 Scope:Global
          inet6 addr: fe80::76d4:35ff:fe70:807/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:903 errors:0 dropped:0 overruns:0 frame:0
          TX packets:704 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:877887 (857.3 KiB)  TX bytes:113898 (111.2 KiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:6201 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6201 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:495923 (484.2 KiB)  TX bytes:495923 (484.2 KiB)


 # lshw -c network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 06
       serial: 74:d4:35:70:08:07
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=192.168.0.6 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:42 ioport:d000(size=256) memory:f3804000-f3804fff memory:f3800000-f3803fff






Sky Hub Status

This page shows the current settings for your Sky Hub. We have preconfigured your Sky Hub with the optimum settings. This is a read only summary page, if you wish to change settings use the menus at the top of this page.

    Select Show Statistics to see your Sky Hub performance statistics such as the number of packets sent and number of packets received for each port
    Select Connection Status to see information about your current connection


Systems Details
help
Manufacturer Sky
Model SR102
Firmware Version 2.92.2508.R
DSL Firmware VersionA2pv6F039m1.d24m
Modem
help
Modem StatusConnected
DownStream Connection Speed19892
UpStream Connection Speed1184
VPI0
VCI38
IPv6 Loopback Address2a02:c7d:916:a000::1/128
Broadband Port
help
MAC Address7c:4c:a5:e6:c0:5e
IPv4 Address90.219.125.251
Network TypePPPoA
IPv4 Subnet Mask255.255.255.255
Gateway IPv4 Address2.127.238.111
IPv4 Domain Name Server90.207.238.97, 90.207.238.99
Gateway IPv6 Addressfe80::a2f3:e4ff:fe47:8630
IPv6 Domain Name Server 
IPv6 Global Address2a02:c7d:916:a000::1/64
IPv6 Link Local Addressfe80::7e4c:a5ff:fee6:c05e
IPv6 Delegated Prefix2a02:c7d:916:a000::/56
LAN Port
help
MAC Address7c:4c:a5:e6:c0:5c
IPv4 Address192.168.0.1
DHCPv4On
IPv4 Subnet Mask255.255.255.0
IPv6 ULAfdc4:199f:b47f:0:7e4c:a5ff:fee6:c05c/64
IPv6 Global Address2a02:c7d:916:a000::1
IPv6 Link Local Addressfe80::7e4c:a5ff:fee6:c05c
DHCPv6On
Wireless Port
help
Name (SSID) SKY57769
Region Europe
Current Channel 1
Wireless APEnabled
Broadcast NameYes
Attached Devices
help
linCabled
pc0Wireless
Connection Status Show Statistics
```

---

### Post by wildmanne39 on 2019-07-26
*Thread moved to **MINT a more appropriate sub-forum**.*

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by SeijiSensei on 2019-07-26
Umm, 8.8.8.8 is a remote address. It's the address for Google's DNS server farm.

---

### Post by triplemaya on 2019-07-26
Huh! So I can ping, but no web pages.
Thanks.

---

### Post by ajgreeny on 2019-07-26
I suspect a DNS problem so please show us what you get from ```
ping google.com
ping 216.58.213.14
``` the second being the IP of google.com.

What primary and secondary DNS are you currently using? You can get this from right clicking on the network icon in the panel, "Connection information"

---

### Post by triplemaya on 2019-07-26
Thanks
```
pc@lin ~ $ ping google.com
ping: unknown host google.com
pc@lin ~ $ ping 216.58.213.14
PING 216.58.213.14 (216.58.213.14) 56(84) bytes of data.
64 bytes from 216.58.213.14: icmp_seq=1 ttl=57 time=26.1 ms
64 bytes from 216.58.213.14: icmp_seq=2 ttl=57 time=21.7 ms
64 bytes from 216.58.213.14: icmp_seq=3 ttl=57 time=21.5 ms
64 bytes from 216.58.213.14: icmp_seq=4 ttl=57 time=21.7 ms
64 bytes from 216.58.213.14: icmp_seq=5 ttl=57 time=20.5 ms
^C
--- 216.58.213.14 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4006ms
rtt min/avg/max/mdev = 20.587/22.333/26.113/1.940 ms

```

 What primary and secondary DNS are you currently using? You can get this from right clicking on the network icon in the panel, "Connection information" 

There is only primiary 

IPv4 Primary is 192.168.0.1
IPv6 Primary is fdc4:199f:b47f:0:7e4c:a5ff:fee6:c05c

On checking I find that these are the same as on my laptop which is connecting fine.

---

### Post by jeremy31 on 2019-07-26
If you are actually using Linux Mint 17, please switch to a newer version as 17 went EOL back in April

---

### Post by triplemaya on 2019-07-26
Thanks. I get that. I would just like to revive this install enough to reinstall in my own time on a new drive. Always takes me ages and I get stressed up about it!

---

### Post by jeremy31 on 2019-07-26
Did you change the /etc/NetworkManager/interfaces file or make manual entries in the Network Manager settings for the ethernet connection or change the machines hostname?

---

### Post by triplemaya on 2019-07-27
No. Due to a hardware cockup I had to reinstall grub but that is the only change made.

---

