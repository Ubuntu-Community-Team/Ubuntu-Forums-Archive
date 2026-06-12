---
title: "Need some help with wireless info and setup"
date: 2006-01-20
forum: Networking &amp; Wireless
---

### Post by motardist on 2006-01-20
Straight to business. I can't connect to my router via wireless pcmcia card.
Need some help setting up the system.
Wiring to the same router is no problem.

Wireless connection is both found and activated.
Edited to add: Driver used is latest XP-driver for the device.
Router DHCP is activated.
Router is running no access control at the moment.

Here are some terminal printouts.
(top line being the command)

```
ndiswrapper -l:

Installed ndis drivers:
net8180 driver present, hardware present
```
```
lspci:

0000:02:00.0 Ethernet controller: Abocom Systems Inc ADMtek Centaur-C rev 17 [D-Link DFE-680TX] CardBus Fast Ethernet Adapter (rev 11)
0000:06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC (rev 20)
```
```
sudo lshw -C network:

  *-network
       description: Fast Ethernet
       product: V1.0
       vendor: CardBus
       physical id: 0
       slot: Socket 0
       resources: irq:9
  *-network
       description: Realtek
       physical id: 0
       version: Rtl8139
       slot: Socket 1
       resources: irq:9
  *-network:0
       description: Ethernet interface
       product: ADMtek Centaur-C rev 17 [D-Link DFE-680TX] CardBus Fast Ethernet Adapter
       vendor: Abocom Systems Inc
       physical id: 3
       bus info: pci@02:00.0
       logical name: eth0
       version: 11
       serial: 00:e0:98:8b:cf:9a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tulip driverversion=1.1.13 ip=192.168.1.101 multicast=yes
       resources: ioport:4000-40ff iomemory:18800000-188003ff irq:9
  *-network:1
       description: Wireless interface
       product: RTL8180L 802.11b MAC
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@06:00.0
       logical name: wlan0
       version: 20
       serial: 00:02:72:47:6b:33
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper link=no multicast=yes wireless=IEEE 802.11b
       resources: ioport:4800-48ff iomemory:19000000-190001ff irq:9
```
```
iwconfig:

lo        no wireless extensions.

wlan0     IEEE 802.11b  ESSID:off/any
          Mode:Auto  Frequency:2.412 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:11 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3
          RTS thr:2432 B   Fragment thr:2432 B
          Power Management:off
          Link Quality:100/100  Signal level:-95 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.
```
```
ifconfig:

wlan0     Link encap:Ethernet  HWaddr 00:02:72:47:6B:33
          inet6 addr: fe80::202:72ff:fe47:6b33/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Memory:19000000-190000ff

```
```
route -n:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0
```
It shows nothing for wlan0, so I tried adding a gateway for it.
```
sudo route add default gw 192.168.1.254 dev wlan0:

SIOCADDRT: Network is unreachable
```
```
sudo ifup wlan0:

*removed irrelevant code*
sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:02:72:47:6b:33
Sending on   LPF/wlan0/00:02:72:47:6b:33
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```
```
iwlist wlan0 scan:

wlan0	No scan results
```
```
cat /etc/network/interfaces:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wireless-essid ubuntunet
wireless-key s:*************

iface eth0 inet dhcp



auto eth0

```


I'd really appreciate it if someone took their time looking over this and tell me what they see.
Also, let me know if there are some additional terminal prints that may be helpful.

---

### Post by hajk on 2006-01-20
You can't have two gateways (default route), so if you want to use wlan0 as gateway, you must first remove eth0 as gateway. I would take out the "auto" lines in /etc/network/interfaces. I find this sort of thing easiest to set up in System/Administration/Network -- you should see both the eth0 and wlan0 devices, and they can both be configured in Properties. Once set up, deactivate the one and activate the other is all you ever need.

---

### Post by Lambert on 2006-01-20
What protocol is your router broadcasting in?

802.11b
or
802.11g

The line ap:00:00:00:...when you run iwconfig says you're not even associated with the router.

When you scan there are no results so it's not even seeing the router currently. And looking at iwconfig results, your card is in 802.11b mode only. If router broadcasts in .11g then there is one problem I see.

Step 1 before anything else is associating router. Then after that comes step two, that is getting an ip assigned to the device. If using dhcp, all the other necessary things will also set up such as gw etc...

I see you're using an ascii key. Is it an open or shared key setting?

---

### Post by motardist on 2006-01-20
Thank you for the quick response!

@Hajk:
It seems that when setting wlan0 as default gateway, it won't stick.
I also marked out the "auto" in /etc/network/interfaces, but it doesn't really seem to make a difference.

@Lambert:
Router is also 802.11b.
How do I associate router to the NIC? I've tried a bunch of times to add the MAC of my router, but nothing happens.
The key auth is open system. Should I set it to auto in router?


The prints in my first post are not in any particular order, btw.

Thanks again!

---

### Post by motardist on 2006-01-20
It probably doesn't matter, but in the "Network Connection", wlan0 shows a signal strength of 100%.
Does that mean nothing, or does it imply that at least the nic radio is working (it did work a week ago in winxp).

---

