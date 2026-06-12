---
title: "eth0 doesn't load when I change kernel"
date: 2012-08-26
forum: Networking &amp; Wireless
---

### Post by jefranca on 2012-08-26
Hi Guys,

I'm using:
[LIST]
xen 4.1 installed from source (I followed this tutorial [URL="http://wiki.xen.org/mediawiki/images/f/f1/Building_and_Installing_Xen_4.x_and_Linux_Kernel_3.x_on_Ubuntu_and_Debian_Linux_-_Version_1.7_-_REDUCED.pdf"]/URL]);
[/LIST]
[LIST]
dom0 or OS is ubuntu server 12.04 kernel 3.2.x 
[/LIST]
All works well, but when I change kernel to 2.6.32.40-jeremy (I installed with this tutorial <http://remusha.wikidot.com/#toc3>) the eth0 doesn't load. I ran these commands:
```

$ lspci | grep -i ethernet
02:00.0 Ethernet controller: Broadcom Corporation Netlink BCM57780 Gigabit Ethernet PCIe (rev 01)

$ lsmod
dcdbas
serio_raw

$ dmesg | grep -i eth
"no response"

$ dmesg | grep -i eth
"only lo"

# ifup eth0
Cannot find device "eth0"
Failed to bring up eth0.

```

Does someone have a suggestion?
Thanks

---

