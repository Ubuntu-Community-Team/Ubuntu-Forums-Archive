---
title: "Internal networking not working"
date: 2009-10-14
forum: Networking &amp; Wireless
---

### Post by steev182 on 2009-10-14
Hi,

When I try to SSH/access uShare from my xbox 360 or even ping my main PC (which is now a Ubuntu box) I am unable to get to them or even ping the address.

I previously had OSX86 running on this PC and internal networking worked really well, when I had a Macbook, it would be able to access the website, xbox sharing worked and everything was fine.

When I forward an external port through to the desktop/home server, connecting from my mini9 to the desktop works when I put in my external ip address. I then tested forwarding ssh to the VM and I am able to access it using the external ip as well.

The network is like this:

Router - Netgear DG834N 802.11n ADSL2+ Router
Desktop/Home server - Ubuntu 9.10 - Linksys PCI Wireless N - 192.168.1.51 (set by DHCP reserved by the router's DHCP Server)
External Server VM - Debian 5.03 - VirtualBox 192.168.1.40
XBox 360 - Apple Airport Express 802.11n - DHCP
Mini9 - Kubuntu - Broadcom Propriety drivers - DHCP

I'm just wondering if there's a way to get internal network access to this computer, as a whole reason for it to be running isn't working for me. ufw isn't running at the moment, but I'm not 100% on what else it could be as I am able to access my mum's laptop using it's internal ip address when it is switched on.

Thanks

---

### Post by steev182 on 2009-10-14
No suggestions?

---

