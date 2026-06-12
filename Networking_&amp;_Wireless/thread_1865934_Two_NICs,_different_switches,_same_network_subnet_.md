---
title: "Two NICs, different switches, same network subnet - HELP"
date: 2011-10-20
forum: Networking &amp; Wireless
---

### Post by BludGeonT on 2011-10-20
Greetings,

I've done some searching but I can't seem to find the solution to my problem and need a bit of help.

Summary:

I have a cluster of HP servers, each has two RAID controller cards housing two different databases on each RAID set.

I am trying to do the following:

Utilize eth0 and eth1, both with static IPs on the same network, going to different switches (both configured for the same network).

eth0 IP:  10.51.4.11

eth1 IP:  10.51.4.31


Both, of course, will use the same default gateway.

I am trying to get the system to work for both interfaces so that eth0 can serve traffic for the one RAID set of data, and eth1 to serve for the other RAID set.

This will allow for redundancy in the even one switch or network interface goes down, it will only take out half of the machine's data availability.

I've tried duplicating the /etc/network/interfaces configuration for eth0 to be set up for eth1.  Both nics have their own unique MAC addresses (these HP servers have 4 physical interfaces).

After hooking both interfaces into their respective switches and restarting the network, eth0 suddenly cannot talk to the network at all and eth1 is able to.

What is the easiest and most conventional way to get both network interfaces to operate properly on the same network, with the same default GW?  

Can someone point me in the right direction?  I would really appreciate it.

(Yah I could do ipaliasing on one NIC, but that defeats the purpose of the redundancy I was hoping to acheive.)

Thank you very much,

Chris

---

### Post by redmk2 on 2011-10-20
> **BludGeonT said:**
> Greetings,

I've done some searching but I can't seem to find the solution to my problem and need a bit of help.

Summary:

I have a cluster of HP servers, each has two RAID controller cards housing two different databases on each RAID set.

I am trying to do the following:

Utilize eth0 and eth1, both with static IPs on the same network, going to different switches (both configured for the same network).

eth0 IP:  10.51.4.11

eth1 IP:  10.51.4.31


Both, of course, will use the same default gateway.

I am trying to get the system to work for both interfaces so that eth0 can serve traffic for the one RAID set of data, and eth1 to serve for the other RAID set.

This will allow for redundancy in the even one switch or network interface goes down, it will only take out half of the machine's data availability.

I've tried duplicating the /etc/network/interfaces configuration for eth0 to be set up for eth1.  Both nics have their own unique MAC addresses (these HP servers have 4 physical interfaces).

After hooking both interfaces into their respective switches and restarting the network, eth0 suddenly cannot talk to the network at all and eth1 is able to.

What is the easiest and most conventional way to get both network interfaces to operate properly on the same network, with the same default GW?  

Can someone point me in the right direction?  I would really appreciate it.

(Yah I could do ipaliasing on one NIC, but that defeats the purpose of the redundancy I was hoping to acheive.)

Thank you very much,

Chris

If you are not routing anything (local LAN), then you can't really use two separate NIC's on the same subnet.  Especially if you are using two separate switches.  Ethernet (layer 2) will not allow it.  Check out [**_[COLOR="Blue"]Spanning Tree Protocol[/COLOR]_**]("http://en.wikipedia.org/wiki/Spanning_Tree_Protocol") used with Ethernet.

---

