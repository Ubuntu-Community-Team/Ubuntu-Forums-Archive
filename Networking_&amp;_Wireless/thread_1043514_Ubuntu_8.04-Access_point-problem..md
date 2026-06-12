---
title: "Ubuntu 8.04-Access point-problem."
date: 2009-01-18
forum: Networking &amp; Wireless
---

### Post by darek_jestem on 2009-01-18
Hi everyone!
I have ubuntu 8.04,my wireless device is:Atheros 242x....
from lspci:
```
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
```
I have internet connection from dhcp.
output from ifconfig eth0:

```
eth0      Link encap:Ethernet  HWaddr 78:35:7f:68:1e:00
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::7a35:7fff:fe68:1e00/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:33786 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30170 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:42188542 (40.2 MB)  TX bytes:3778710 (3.6 MB)
          Interrupt:18 Base address:0x6000
```
iwconfig showing:
```

lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"szatan11"  Nickname:""
          Mode:Master  Frequency:2.447 GHz  Access Point: 06:1F:E2:A7:E5:C2
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:21257  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

And i would like to set up access point on my system.

I try to set up like this:
1.Destroy the old settings:
```
wlanconfig ath0 destroy
```
2.set the essid:
```
iwconfig ath0 essid something
```
3.channel:
```
iwconfig ath0 channel 8
```
4.and up the interface:
 

```
ifconfig ath0 10.11.2.1 netmask 255.255.255.0 up
```

5.This is all about ath0;
6.Now I must set the NAT arrays so:
6.1.clear the arrays:
 

```
iptables -F -t nat

iptables -X -t nat

iptables -F -t filter

iptables -X -t filter
```
6.2.We don't want to forwarding the packets so:
```
iptables -t filter -P FORWARD DROP
```
6.3.next..
```
iptables -t filter -A FORWARD -s 10.11.2.0/255.255.255.0 -d 0/0 -j ACCEPT

iptables -t filter -A FORWARD -s 0/0 -d 10.11.2.0/255.255.255.0 -j ACCEPT

```
6.4.and :```
iptables -t nat -A POSTROUTING -s 10.11.2.0/24 -d 0/0 -j MASQUERADE
```

7.Now I would like to connect to AP from other pc(with Windows Vista)
and i have the Limited connection.I see my computer(with AP) but i have not internet....

If you don't now how to help me.I will be very happy if you give my any good "HowTo" if you have.

---

