---
title: "how to set up a 2-NIC machine with an wireless AP?"
date: 2010-09-01
forum: Networking &amp; Wireless
---

### Post by hillofbeans on 2010-09-01
[FONT=Courier New]Hi All,

Although not new to linux or ubuntu, I am having real trouble getting a machine's networking to work properly.  I'm using a desktop machine with ubuntu lucid.

The problem is that wireless clients can't pass data back and forth through the desktop machine to the net.  However, when I log onto the machine at the console, I can browse the net fine.  That is, eth0 is working.  I can also ping machines which connect to the wireless AP hanging off eth1.  But those machines which connect via the AP can't browse the net.

Here is picture of the config.

(Internet) --- (desktop with two NICs: eth0 + eth1) --- (DWL-2100AP Access Point)

The "Internet" connects to eth0, the AP connects to eth1.  Here is the relevant stuff from the ifconfig output:

eth0      Link encap:Ethernet  HWaddr 00:1d:60:3f:c3:1f  
          inet addr:10.10.199.222  Bcast:10.10.199.255        Mask:255.255.248.0
          inet6 addr: fe80::21d:60ff:fe3f:c31f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
eth1      Link encap:Ethernet  HWaddr 00:14:78:0e:63:c5  
          inet addr:192.168.0.222  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::214:78ff:fe0e:63c5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1


The dlink dwl-2100AP is set to have IP 192.168.0.50, Gateway 192.168.0.222 (ie. eth1), and subnet mask of 255.255.255.0.  

The AP also is set to be a dhcp server, and gives out IPs from 192.168.0.100, with subnet mask 255.255.255.0, Gateway 192.168.0.222 (eth1), and DNS of 211.67.177.65.

These assignments seem to be working because I can see the assigned IPs on wireless devices such as my ipod touch.

Can anybody let me know how I should be setting this up?  It just seems that packets aren't getting through the desktop, and I can't figure out why.

Any help really greatly appreciated.
[/FONT]

---

### Post by BkkBonanza on 2010-09-01
You will need to add at least one routing rule to allow traffic to pass from one interface to the other. I have this working on my Ubuntu based router/wifi AP. I'm not sure how similar our setups would be though as I do it all manually. Not a default setup. 

Post output of **route** command.

Mine looks like,

```
$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     *               255.255.255.0   U     0      0        0 eth1
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.1.254   0.0.0.0         UG    100    0        0 eth0
```

But at the moment I disabled wifi so it doesn't show up here. I was using it on wlan0 and it was in the table too. Anyway, you want to get this table correct and may need one or more **route add ...** commands.

To annotate this, it says: for traffic going to 192.168.2.* send it to eth1 and for traffic going to 192.168.1.* send it to eth0, and for anything else send it to 192.168.1.254 (gateway) where it will figure it out.

---

