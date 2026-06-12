---
title: "IP Address Lost After a Few Seconds"
date: 2013-03-14
forum: Networking &amp; Wireless
---

### Post by alpah39 on 2013-03-14
Hello, bit of a weird issue here.  I'm booting from a LiveCD, and when I set up the IP, netmask and hostname, either via ifconfig or /etc/network/interfaces, it only holds onto it for a few seconds before it just disappears.  Right after doing it by either method and then restarting networking, everything looks good when running ifconfig.  After it stops working, I run ifconfig again and the inet4 addr line is gone.

While it's up, I can ping out to the internet and ping to the machine from elsewhere in my network, but then it just stops working.  Any idea what is going on?

Please see screenshots (sorry, can't copy the text, VM console.)

[ATTACH=CONFIG]240178[/ATTACH]
[ATTACH=CONFIG]240179[/ATTACH]

---

### Post by sanderj on 2013-03-14
"VM console"? Are you running Ubuntu in a virtual machine? If so, which virtualisation software, which host OS? What kind of network layer: NAT, bridged, ... ?

Why do you assign an IP address? What if you use DHCP?

What does dmesg say?

---

### Post by alpah39 on 2013-03-14
It's running on Hyper-V under Server 2008 R2.  Virtual network.  Assigning IP as DHCP unavailable on the network it's on. 

Thanks for the point to check dmesg.  When it's going down I see: addrconf(netdev_up): eth0: link is not ready

So it looks like it thinks the network connection is being disconnected.  This is actually a live CD for a particular product, AppAssure, OS version is ubuntu 3.2.0-38-generic.  My normal Ubuntu VM's don't have this issue.

Could this be some sort of incompatibility with the drivers on the live CD and running in a hyper-v VM?

---

### Post by alpah39 on 2013-04-04
Here is the resolution for this issue in case anyone encounters this in the future.  Network Manager was calling the DHCP client every minute or so, and getting no reply to DHCP requests, was then causing the network configuration to be dumped.  Was resolved by renaming the dhclient binaries in /sbin so they would not get executed.  

This is not normal Ubuntu behavior and seems to be an issue specific to the Dell AppAssure live DVD.

---

