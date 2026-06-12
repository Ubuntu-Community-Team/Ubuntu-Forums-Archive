---
title: "rtl8185 cannot get IP address"
date: 2009-07-20
forum: Networking &amp; Wireless
---

### Post by garibaldino on 2009-07-20
hi,

I am trying to connect my rtl8185 to a WEP network (that worked on the last openSuse).

Considering the various logs, everything works but the IP addressing.

What's wrong? thanks.
dmesg| grep wlan0

```

[18855.200382] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[18855.232020] wlan0: direct probe to AP 00:14:51:6f:d6:07 try 1
[18855.233619] wlan0 direct probe responded
[18855.233623] wlan0: authenticate with AP 00:14:51:6f:d6:07
[COLOR="Red"][18855.235419] wlan0: authenticated[/COLOR]
[18855.235421] wlan0: associate with AP 00:14:51:6f:d6:07
[18855.237547] wlan0: RX AssocResp from 00:14:51:6f:d6:07 (capab=0x411 status=0 aid=1)
[18855.237551] wlan0: associated
[18855.237937] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[18866.072010] wlan0: no IPv6 routers present
```

/etc/network/interfaces
```
auto lo
iface lo inet loopback

iface eth0 inet dhcp

iface wlan0 inet dhcp
wireless_essid 9999
wireless_key s:XXXXXXXXXXXXX 
wireless_keymode open
wireless_mode Managed
```

ifup wlan0
```
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:19:cb:a3:4d:e6
Sending on   LPF/wlan0/00:19:cb:a3:4d:e6
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
 * Stopping the Firestarter firewall...
   ...done.
 * Starting the Firestarter firewall...
   ...done.

```



lshw -C network
```
*-network
       description: Ethernet interface
       product: L1e Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: b0
       serial: 00:24:8c:3c:1e:3b
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI firmware=L1e ip=192.168.1.3 latency=0 module=atl1e multicast=yes
  *-network
       description: Wireless interface
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:05:01.0
       logical name: wmaster0
       version: 20
       serial: 00:19:cb:a3:4d:e6
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rtl8180 latency=64 maxlatency=64 mingnt=32 module=rtl8180 multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: b2:fe:11:3b:d4:bb
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
```

---

### Post by Venlaar on 2009-09-13
I'm having basically the same problem.

Here is some of the configuration: 

```


phil@phil-laptop:/etc/network$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:03:25:3f:9b:9d
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 duplex=full firmware=N/A ip=192.168.1.107 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 9
       bus info: pci@0000:08:09.0
       logical name: wmaster0
       version: 20
       serial: 00:c0:a8:cc:56:b4
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rtl8180 latency=64 maxlatency=64 mingnt=32 module=rtl8180 multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: ee:0b:61:39:00:1f
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

lspci | grep -i rtl
08:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)

dmesg | grep wlan
[   25.513265] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

I then checked /etc/network/interfaces and only saw:
```

phil@phil-laptop:/etc/network$ cat interfaces
auto lo
iface lo inet loopback

```

So I tried adding the lines: 

```

iface eth0 inet dhcp

iface wlan0 inet dhcp

```

But then I get this when trying to bring it up. 

```

phil@phil-laptop:/etc/network$ sudo ifup wlan0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:c0:a8:cc:56:b4
Sending on   LPF/wlan0/00:c0:a8:cc:56:b4
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


```

I see no wireless networks with the Network Manager GUI. 

I have another laptop in the house with a different wireless card that works out of the box and sees all the networks. 

According to [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek#PCI]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek#PCI") this wireless card should work out of the box in earlier versions.

Oh I guess that begs the question, "What version are you running?"

```

phil@phil-laptop:/etc/network$ uname -a
Linux phil-laptop 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 i686 GNU/Linux

```

I've search the forums quite a bit and haven't found much info. Any help is much appreciated.

---

### Post by garibaldino on 2009-09-14
> **Venlaar said:**
> I'm having basically the same problem.


I somewhat solve the problem using wicd (& WPA2 protocol not WEP).

I note that wicd has to reconnect often. Too the transfer is rate is quite erratic and overall much slower what I pay for. The more active wireless in my blocks and the more sluggish my wlan.

I guess rtl 8185 isn't the more consistent wlan chipcard for linux.

---

