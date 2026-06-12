---
title: "Network Card Disabled"
date: 2010-02-07
forum: Networking &amp; Wireless
---

### Post by badco67 on 2010-02-07
Wireless network card is showing as "disabled"...How can I enable it through Ubuntu?

product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
 *-network DISABLED

---

### Post by chili555 on 2010-02-07
If you have a network connection, please do, in a terminal:```
sudo apt-get install b43-fwcutter
```When prompted, accept installation of the needed Broadcom firmware. Reboot. Is it still disabled?

---

### Post by thor187 on 2010-02-07
Also try the below in terminal

> sudo ifdown -a
sudo ifup -a

---

### Post by applejay on 2011-09-01
This is an old thread, but I just want to share my solution so it doesn't get lost. I installed a new NIC and it was disabled when I started my Ubuntu server.

Doing a 

> sudo lshw -C network

I get this for my disabled NIC

>  *-network:0 DISABLED
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1

I scoured over the internet to try to find a solution, but no luck. Most problems had to do with the NIC being unclaimed (drivers), but mine was just a simple NIC disabled. I found a reference to look at /etc/network/interfaces ([http://fixunix.com/ubuntu/351212-disabled-one-network-device-%3D%3D-disabled-ubuntu.html#post916165]("http://fixunix.com/ubuntu/351212-disabled-one-network-device-%3D%3D-disabled-ubuntu.html#post916165")), which the intention of the post is to disable the NIC.

> sudo vim /etc/network/interfaces

This file contains all the enabled adapters, and the new NIC was not on the list. I added an entry for my new NIC (using the logical name from the lshw command)

> # The secondary network interface
auto eth1
iface eth1 inet dhcp


Then executed this command

> sudo /etc/init.d/networking restart

and all is good now =)

---

