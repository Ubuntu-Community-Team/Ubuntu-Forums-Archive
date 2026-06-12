---
title: "(Wired) Computer loses Internet connection and requires many reboots to re-connect"
date: 2010-09-05
forum: Networking &amp; Wireless
---

### Post by michaelducharme on 2010-09-05
Hello

I am using Ubuntu Studio 10.04 LTS and I am experiencing the following problem:
my computer loses its Internet connection and appears to require several reboots to re-establish an Internet connection.

As suggested on a similar post relating to wireless connection loss, I supply the output of sudo lshw -C network


  *-network              
       description: Ethernet interface
       product: NetLink BCM5789 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 11
       serial: 00:16:e6:44:3b:f4
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 duplex=full firmware=5789-v3.29a ip=192.168.1.101 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:18 memory:e3000000-e300ffff


Note that I have REMOVED my wireless card in case there was some kind of hardware conflict or failure. I am using a wired connection through a Linksys WRT54G router that is supplying an Internet connection to another computer and an IP phone without any problem.

When I run the command network-admin (or select System > Administration > Network) I can see only 3 tabs (General, DNS and Hosts) It seems that the Connections tab has disappeared (and I believe this happened when I upgraded from Ubuntu 9/Karmic Koala). If I click Help it shows me that there should be 4 tabs, not 3.

The connection dropping began prior to my decision to upgrade. In fact it took several attempts to complete the upgrade. Should I attempt to re-install the upgrade? I am not sure how to do it without losing my connection. When I visit System > Administration > Update Manager, I am informed that my system is up to date.



Thank you,
Michael

---

### Post by michaelducharme on 2010-09-10
Did I post incorrectly? I am wondering why there are no replies after 4 days. Most posts seem to get replies within hours. Was I not specific enough or too specific? Forgive me... this is the first time I've posted to the Ubuntu community. Usually I hire someone to take the computer away then I get it back several days later with the same problem as before. Hopefully someone here can help.

Also in this same computer the sound sometimes works but often goes away without notice. Maybe this should be a separate post but perhaps the two problems are related.

---

### Post by grahammechanical on 2010-09-10
I am sorry no one noticed your problem. The people on this forum are not paid workers for the most part. This is a help one another way of solving problems. And I most certainly will not be a great help. I do not know if I am giving you the best advice. Sorry. I am using 10.04 but not the studio version. Things should not be too different but they seem to be from what you report. Perhaps you can try this.

Go to Ubuntu Software Centre and search for Network manager. If it is installed you will see a green circle with a white tick mark in the centre. Remove Network Manager and re-boot. Then Install it again. This may give you a network icon in notification area of the top panel. It should show you an option for Connection Information as well as Edit Connections. There should be five tabs = Wired, Wireless, Mobile Broadband, VPN, DSL.

This may or may not work. If it does then it is just a lucky guess. Well, it may be a bit more than that. This is all that I can offer.

Regard

---

### Post by dineshs on 2010-09-11
When your connection is not working ,please post the output of
```
ping -c3 4.2.2.1
```and
```
route -n
```
```
ping -c3 192.168.1.1
```
Assuming that the gateway IP is 192.168.1.1 which you can confirm from *route -n* output

---

