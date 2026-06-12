---
title: "Unable to ping in or out but DHCP has grabbed a new address?"
date: 2012-02-10
forum: Networking &amp; Wireless
---

### Post by Crispness on 2012-02-10
Hiya

I'm trying to move a physical Ubuntu installation to become a Hyper-V virtual machine.

I have already successfully installed multiple Ubuntu installations (9, 10.04LTS and 11.04 - server and desktop) to this particular Hyper-V machine. But they were all clean installs from Ubuntu .iso files.

Now I'm trying to migrate a working physical machine across using Acronis Backup and Recovery. With lots of tech help from Acronis we managed to create a live virtual image on the Hyper-V machine, but unfortunately the network connection is misbehaving. Eventually this morning, I cleaned out /etc/network/interfaces just leaving the loopback definition
auto lo
iface lo inet loopback

and I shutdown the VM. In the Hyper-V Manager I removed the Legacy Network Adapter and restarted the machine totally disconnected from the network. It came up quite happily. So I shut it down again and added the legacy network adapter back in to the Hyper-V config and restarted. She came up nicely and grabbed a new DHCP address - in the process passing the correect machine name to the DHCP manager. 

But it doesnt respond to a ping, and neither does it ping out to the network.
And if I run ifconfig -a I get definitions for both eth0 and lo. eth0 as follows:
eth0    Link encap:Ethernet HWaddr blahblah
           Inet addr: 192.168.0.212 Bcast:192.168.0.255 Mask 255.255.255.0
           inet6 addr blahblah
           RX packets:134 errors:0 dropped:17687 overruns:0 frame:0
           TX packets:106 errors:249 dropped:0 overruns:0 frame:0
           blah blah

I have added to /etc/network/interfaces
auto eth0
iface lo inet dhcp


The mask and subnet are correct. So why cant I ping in or out?

When I try to ping 192.168.0.1 I get
192.168.0.212 icmp_seq=11 Destination host unreachable
etc

 and similar when trying to ping in.

So the system is recognising it has a network card when coming up, it grabs an IP address, but that IP address is not pingable and doesnt ping out.

I'm stumped.

Any suggestions?

---

### Post by jonobr on 2012-02-10
Could you post your routing table,

also could you

```
sudo tcpdump -w trace.pcap -s 1600 -i any 
```

do a few pings and then upload the trace.pcap file here?

Given your addressing I dont think there should be anything confidential on there?

Cheers
Jonobr

---

### Post by Crispness on 2012-02-14
Routing table
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=212659&stc=1&d=1329233041[/IMG]

---

### Post by Crispness on 2012-02-14
Of course with no network connectivity, nor any USB connection, I'm not sure how I can get the trace.pcap file off the machine.

Any suggestions?

Its a binary format by the looks of it.

---

