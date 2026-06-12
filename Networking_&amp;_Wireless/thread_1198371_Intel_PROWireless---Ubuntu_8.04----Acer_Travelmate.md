---
title: "Intel PRO/Wireless---Ubuntu 8.04----Acer Travelmate 4500 Laptop"
date: 2009-06-27
forum: Networking &amp; Wireless
---

### Post by thefunks on 2009-06-27
**This post is based on the HOWTO post a Wireless issue (ticket). It's been filled in like a worksheet.**             


**1 ) Machine Brand and Model (PC/Laptop)**: 

Acer Travelmate 4500 Series Model ZL1

**2 ) Wireless Brand, Model and Wireless Chipset:** 

Intel Corporation PRO/Wireless 2200BG Network Connection
[B]
3 ) check interface:[/B]
[B]
Not sure what I'm checking here :

lo no wireless extensions.

eth0 no wireless extensions

eth1 radio off ESSID:" "
Mode: Managed Frequency: 2.462 GHz Access Point: 00:22:3F:84:2C:14
Bit Rate: 0 kb/s Tx-Power=off Sensitivity=8/0 
Retry Limit:7 RTS thr:off Fragment thr:off
Power Management:off
Link Quality:0 SIgnal level:0 Noise Level:0
Rx invalid nwid:0 Rx invalid crypt:1 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

4 ) Check for modules:[/B]

[FONT=monospace]Can't find one for the wireless card.

[/FONT]**5 ) Kernel boot messages**e

eth1: no IPv6 routers present
eth1: link becomes ready
NET: registered protocol family 17
ieee80211_crypt: registered algorithm 'TKIP'
ipw2200: Failed to send RSN_Capabilities: Command timed out.
ipw2200: Failed to send SSID: Command timed out.
eth1: no IPv6 routers present
ipw2200: Failed to send CARD_DISABLE: Command timed out.
ADDRCONF (NETDEV_UP): eth1: link is not ready
ADDRCONF (NETDEV_UP): eth0: link is not ready
ADDRCONF (NETDEV_UP): eth1: link is not ready
ADDRCONF (NETDEV_UP): eth1: link is not ready
ADDRCONF (NETDEV_UP): eth1: link is not ready

**6 ) Network configuration**
*-network:0
description: ethernet interface
product: BCM4401 100Base-T
vendor: Broadcom Corporation
physical id: 2
bus info: pci@0000:02:02.0
logical name: eth0
version: 01
serial: 00:c0:9f:61:70:2d
size: 10MB/s
capacity: 100MB/s
width: 32 bits
clcok: 33MHz
capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no module=ssb multicast=yes port=twisted pair speed=10MB/s

*-network:1 DISABLED
description: Wireless Interface
product: PRO/Wireless 2200BG Network Connection
vendor: Intel Corporation
physical id: 4
bus info: pci@0000:02:04.0
logical name: eth1
version: 05
serial: 00:0e:35:67:d6:05
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=64 link=no maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=radio off

**7 ) Scan for networks:**
[FONT=monospace]
lo    Interface doesn't support scanning.
eth0  Interface doesn't support scanning.
eth1  No scan results

[/FONT]**8 ) Ubuntu Version: **

Ubuntu 8.04.2

**9 ) Kernel/architecture (including 32 vs. 64 bit): **

2.6.24-23-generic i686

**10 ) Restarting the network:**

listening on lpf/eth0 several times but never on eth1, which would be the wireless card.

No DHCPOFFERS recieved.
No working leases in persistent database - sleeping.
grep: /etc/resolv.conf: No such file or directory


----------------------------------------------------------------------------------------------------------

So normally in Windows my wireless card works but my wired device does not. It's probably disabled or something and I just don't know how to enable it. The wireless card is definitely disabled in Ubuntu. I try to physically turn it on via the button in front of the laptop, but it does not respond when I am in Ubuntu (though it does in windows - it lights up when it is enabled and glows with a red backlight).

When I visit the network manager in Ubuntu the only option a left click allows is "Manual Network Configuration." From the wireless part of this window it looks like the wireless card is picking up networks around here with various signal strengths but won't connect to them; even though to my knowledge the wireless network card is currently disabled (no glowing backlight like in windows) and it shouldn't be able to detect those networks at all.


Thanks in advance for any help :)

---

