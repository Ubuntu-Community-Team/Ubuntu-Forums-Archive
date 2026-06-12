---
title: "SIS191: No wired network"
date: 2010-03-04
forum: Networking &amp; Wireless
---

### Post by urustu on 2010-03-04
Hi,

I have a 100% Ubuntu laptop, Asus X73SL equipped:
- An Ethernet network card: Silicon Integrated Systems [SiS] 191
- And a wireless card: Atheros Communications Inc. AR928X (ath9k)

The wireless connection is good but my wired connection does not always work.  I must remove the battery to reset the power card for the connection is restored or that I uninstall and reinstall the package 'network-manager' and 'network-manager-gnome'.

Here the trace screen by command line :
```
$ /usr/bin/nm-applet --sm-disable

** (nm-applet:1591): WARNING **: _nm_object_get_property: Error getting 'WwanHardwareEnabled' for /org/freedesktop/NetworkManager: (16) No such property WwanHardwareEnabled

** (nm-applet:1591): DEBUG: foo_client_state_changed_cb
** (nm-applet:1591): DEBUG: foo_client_state_changed_cb
```Then when the message "Wired Network disconnected" appears on the screen:
```
** (nm-applet:1591): WARNING **: _nm_object_get_property: Error getting 'State' for /org/freedesktop/NetworkManager/ActiveConnection/0: (19) Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:1591): WARNING **: _nm_object_get_property: Error getting 'Default' for /org/freedesktop/NetworkManager/ActiveConnection/0: (19) Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist


** (nm-applet:1591): DEBUG: old state indicates that this was not a disconnect 9
** (nm-applet:1591): DEBUG: going for offline with icon: notification-network-ethernet-disconnected
```

---

### Post by prcxjb on 2010-08-27
Same problem.I'm using ASUS F81E84SE and all the devices are the same to yours except that my CPU is Intel P8400 and my graphic card is ATI 4570.Sis cards are really  bad.I regretted buying this notebook.And I think your notebook can melt your hand during summer:p

---

### Post by tankdriver on 2010-08-27
Another "me too" comment.
Asus N90SC Notebook, same SIS Networkcard, must remove Battery every time to have Ethernet.

---

### Post by Mixo on 2010-11-13
Hi guys. My english as bad as exp in use Ubuntu)
i deside activate this resent thread because i have the same problem with my asus x61SL(f50sl) ethernet sis191. i have found very much info about this problem, but there is no success result and i try to have solution myself.

my ubuntu 10.04 kernel version is 2.6.32-24
I find source of ethernet driver sis190.c changed by 2008 and source of kernel 2.6.32-25. if in this kernel source driver is a different from one I find I'll try to compile kernel with different sis190.c and update my eth driver. news will be soon)

---

### Post by Mixo on 2010-11-13
well, i compare both versions of sis190.c whey are ident. that mean sis190 driver in kernels 2.6.32-24,25 is actual. then i try disable ipv6 support. i can do that but it's have no effect too.
now i almost have no idea how resolve this problem, but there is one moment wired network between two notebooks with static ip addresses can be established!!! and its work. meanwhile when i connect to the lan with dhcp connection losls.

---

### Post by Mixo on 2010-11-14
I find what was my problem) but now i guess i don't need decide this. My notebook don't establish connection when i use a MAC address from my desktop PC(change MAC address) like this

[HTML]ifconfig eth0 down
ifconfig eth0 hw ether aa:bb:cc:dd:ee:ff
ifconfig eth0 up[/HTML]

now i use router and it works for wired and wireless connections! I don't know whats the problem then i change MAC address and why connection is lost in this case.

---

### Post by urustu on 2011-11-04
I dug up this old topic to tell you what it is. In fact my laptop has been supported by the manufacturer warranty. Since my new Asus laptop, I have this problem. I assume that the network card or the motherboard had a weakness.

---

