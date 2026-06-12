---
title: "New Wired Connection Problem"
date: 2009-03-26
forum: Networking &amp; Wireless
---

### Post by lazius on 2009-03-26
Hi everybody out there, I'm having a very rare issue with my wired network since I change the provider. I'm at a building and the new modem is connected to a router that supposedly is properly configured and gives us internet to different nodes at the office. 
We were able to connect to the wired network with the provider that we had before, but with this new one we can't just with Ubuntu 8.10 because the machines that have Ubuntu 8.04 can do it, even thou they are virtual machines and the host computer doesn't have internet jeje is wierd, no ip, no connection..the two computer marked an X saying that is disconnected but still the virtual machines with 8.04 have internet.

But well my machine also have 8.10 so i can't connect,a friend of mine has 8.04 and he can connect without problem, even if we test a windows machine it works fine with the network on the same node and with the same cable.

Somebody can help me with this please??

I have no IP and my wired connection says: "disconnected" eventhou I have the option of Auto eht0 to select. (if i selected i can't connect)

I execute the command lshw -class network to see my interface and here it is the result:

>  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:16:d3:4d:f6:f8
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 module=r8169 multicast=yes


---

### Post by sammy_pal on 2009-03-26
Well, your problem is really weird. :(
First of all, just to ensure that there is no problem in the network, is the network router configured to hand out IP address, DNS address, gateway address using DHCP?
Secondly, in the case of the Host machine running 8.10 with 8.04 as guest, can you kindly post the outputs of ```
ifconfig
``` and ```
cat /etc/resolv.conf
``` in both the host and the virtualized guest. This might help to figure out the trouble, why things are allright in 8.04 but not in 8.10. :)

---

### Post by davecgs on 2009-03-27
The realtek drivers are a nightmare in linux.  Fedora just chokes.  I would strongly suggest grabbing a PCI network card and just working with that.

---

