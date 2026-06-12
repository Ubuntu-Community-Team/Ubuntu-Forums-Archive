---
title: "Wireless card has gone missing"
date: 2013-01-26
forum: Networking &amp; Wireless
---

### Post by Warthaug on 2013-01-26
I am running ubuntu on a laptop where ubbuntu has worked for at least 4 years.  I updated in early Jan to 12.10, and it too worked flawlessly until a few days ago.  Out of nowhere, the wireless card stopped working.  A lot of googeling later and I only found examples of similar cases where the card had never previously worked, and running those fixes didn't seem to help.

What appears to have happened is that the wireless card (formerly eth1) is no longer being 'claimed' by a driver.

Output of sudo lshw -C network
```
 *-network UNCLAIMED     
       description: Network controller
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f0900000-f0903fff
  *-network
       description: Ethernet interface
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth0
       version: 10
       serial: f0:4d:a2:4c:23:59
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.123 duplex=full firmware=sb v2.19 ip=192.168.0.16 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:49 memory:f0d00000-f0d0ffff
```

Output of grep -i eth1 /var/log/syslog | tail
```
Jan 23 21:12:35 bryan-Studio-XPS-1645 NetworkManager[1181]: <info> Activation (eth1) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Jan 23 21:12:35 bryan-Studio-XPS-1645 NetworkManager[1181]: <info> Activation (eth1) Stage 5 of 5 (IPv4 Commit) started...
Jan 23 21:12:36 bryan-Studio-XPS-1645 NetworkManager[1181]: <info> (eth1): device state change: ip-config -> activated (reason 'none') [70 100 0]
Jan 23 21:12:36 bryan-Studio-XPS-1645 NetworkManager[1181]: <info> Policy set 'Goobernet' (eth1) as default for IPv4 routing and DNS.
Jan 23 21:12:36 bryan-Studio-XPS-1645 NetworkManager[1181]: <info> Activation (eth1) successful, device activated.
Jan 23 21:12:36 bryan-Studio-XPS-1645 NetworkManager[1181]: <info> Activation (eth1) Stage 5 of 5 (IPv4 Commit) complete.
Jan 23 21:12:52 bryan-Studio-XPS-1645 NetworkManager[1181]: <info> (eth1): IP6 addrconf timed out or failed.
Jan 23 21:12:52 bryan-Studio-XPS-1645 NetworkManager[1181]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Jan 23 21:12:52 bryan-Studio-XPS-1645 NetworkManager[1181]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) started...
Jan 23 21:12:52 bryan-Studio-XPS-1645 NetworkManager[1181]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) complete.
```

Jan 23rd is the last entry - despite me using the laptop today (Ja 26, plugged into a wired connection) to send this message.

Anyone know how to get this thing working again?  Its not the card - I can load up my win7 partition and its wireless functions perfectly.

Bryan

EDIT: "ifconfig -a | grep eth" only shows the wired connector...

EDIT 2: the contents of /etc/network are
```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
```

---

### Post by Warthaug on 2013-01-27
Much googling has found the answer:
[http://askubuntu.com/questions/214156/wireless-does-not-work-anymore-after-software-update-with-ubuntu-12-10-on-a-dell](http://askubuntu.com/questions/214156/wireless-does-not-work-anymore-after-software-update-with-ubuntu-12-10-on-a-dell)

Hopefully this'll help others....

---

