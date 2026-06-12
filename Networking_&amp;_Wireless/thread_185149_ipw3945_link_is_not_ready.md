---
title: "ipw3945 link is not ready"
date: 2006-05-31
forum: Networking &amp; Wireless
---

### Post by stefanr on 2006-05-31
Hi all,

here on a Dell d820 I am working with Dapper, kernel 2.6.15-23, trying to get the wireless to work.

I get the same result, either using stock versions of ieee80211 and ipw3945, as well as with ieee80211-1.1.13 and ipw3945-1.0.5 (+firmware +ipw3945d). 

The device is mapped to wlan0 in /etc/iftab.

The modules load fine, and I can scan and detect networks. Iwconfig sets the network parameters alright, but whenever I do *ifup wlan0*, I get "**ADDRCONF(NETDEV_UP): wlan0: link is not ready**" and no dhcp lease.

The wireless is switched on in the bios and the associated led is blinking very fast.

Here are the relevant excerpts from syslog:

May 31 12:44:04 lowveld kernel: [4294677.831000] ieee80211_crypt: registered algorithm 'NULL'
May 31 12:44:04 lowveld kernel: [4294677.975000] ieee80211: 802.11 data/management/control stack, 1.1.13
May 31 12:44:04 lowveld kernel: [4294677.975000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
May 31 12:44:04 lowveld kernel: [4294678.264000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.0.5m
May 31 12:44:04 lowveld kernel: [4294678.264000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
May 31 12:44:04 lowveld kernel: [4294678.289000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
May 31 12:44:04 lowveld kernel: [4294679.735000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)

May 31 12:58:22 lowveld dhclient: Internet Systems Consortium DHCP Client V3.0.3
May 31 12:58:22 lowveld dhclient: Copyright 2004-2005 Internet Systems Consortium.
May 31 12:58:22 lowveld dhclient: All rights reserved.
May 31 12:58:22 lowveld dhclient: For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)
May 31 12:58:22 lowveld dhclient:
May 31 12:58:22 lowveld kernel: [4295542.340000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
May 31 12:58:23 lowveld dhclient: Listening on LPF/wlan0/00:13:02:46:ee:b9
May 31 12:58:23 lowveld dhclient: Sending on   LPF/wlan0/00:13:02:46:ee:b9
May 31 12:58:23 lowveld dhclient: Sending on   Socket/fallback
May 31 12:58:27 lowveld dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May 31 12:58:35 lowveld dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10

Any hints?

Regards,
Stefan.

---

### Post by stefanr on 2006-05-31
Solved!

Obviously, it was a problem with the configuration utilities rather than driver support.

regards,
Stefan.

---

### Post by eedrummer on 2006-07-18
Hey Stefan,

I also have a d820 and I am trying to get it to work with the bcm43xx module. I can get the wifi light to come on, and I can also scan for networks, but when I dhcp to get an IP, I also get the "link is not ready" message. What did you do to get rid of that?

---

### Post by MarkSheely on 2006-07-18
Hi eedrummer,

Forgive me if I'm wrong, but....

are you trying to use the bcm43xx driver with a ipw3495 wireless card?

---

### Post by eedrummer on 2006-07-20
According to lspci, my laptop is sporting a Broadcom BCM4310. 

I seemed to find some docs that indicated that the bcm43xx driver would only do 11mbps, and I ditched it.

I wound up going with the latest version ndiswrapper that I compiled myself and everything is working now.

---

### Post by Jason Spaceman on 2006-07-24
> **stefanr said:**
> Solved!

Obviously, it was a problem with the configuration utilities rather than driver support.

regards,
Stefan.

I have the same Intel 3945 wifi card, and I think I may have the same problem as you.  Can you post how you solved this problem?  Thanks.

---

### Post by josephmc on 2008-05-09
I know this is really old and i'm in hardy not dapper but i have the same problem! i've had this problem in gusty with a different laptop! I hate the GUI network tools so much.

Neither networkmanager or wicd will configure the network until i run "iwconfig wlan0 essid <ssid> enc <wep key>"

---

### Post by orastreet on 2008-05-25
Having the same problem.  I have a Netgear wirelss router at home in which after installed Hardy (I upgraded) I can not connect to my home wireless network.  I can however connect to any other one.  Ethernet works great.  When I do a tail /var/log/messages I get:

 ADDRCONF(NETDEV_UP): eth1: link is not ready

Any ideas?  This all worked perfect in Gutsy.  Nothing like upgrading only for things to stop working.  Thanks in advance.

---

### Post by josephmc on 2008-06-18
Wireless is still flaky for me but I did solve this problem. I was using ASCII for wep when it was HEX. I wish they would simplify it a little more.

I also recommend WICD instead of network manager.

---

