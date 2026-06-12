---
title: "DRBL/Clonezilla help 12.04"
date: 2012-08-26
forum: Networking &amp; Wireless
---

### Post by theunfrailhale on 2012-08-26
it seems to be my modus operandi to reinstall when I get to a point of frustration and confusion I cant resolve.

this is an attempt to break that cycle and I appreciate any help offered.

I am trying to see if I can avoid the $3k cost of Ghost for my school by setting up a Clonezilla server. I have a box at home that I am using to test it, a dell Pentium D, 80GB HD, and 3GB ram. Onboard Gbit NIC and an addin 10/100nic for management.

I have the machine wired into my network.
My home router is managing DHCP on the network and is in the same logical grouping as my DRBL server. I have manually assigned an address to both of my interfaces.
eth0 is the onboard Gbit.
192.168.1.70
255.255.255.0
192.168.1.1

eth1 is the addin FeNIC
192.168.1.60
255.255.255.0
192.168.1.1

I have successfully booted my primary desktop to the DRBL server ONCE, just after I set it up, and prior to trying to get the clonezilla server up.

when I run "sudo /opt/drbl/sbin/dcs" to initiate the Clonezilla server I go through the procedure and I seem to make it through ok, but there are some things that I think i have mis configured.

One, I dont ever have an option to pick a MAC address client list. Only IP list, but that seems like a silly way to define clients, as IPs are dynamic, or at least post OS initialized, which is no good cause Im trying to pxe boot them PRE OS

when I get through the dcs config, I constantly get an  error that I have googled over and over and cant seem to find an answer. 

drbl "" is not a suitable IP_List

then it says its quitting. and i get nowhere.

I am sure that I have something misconfigured, probably in the DRBL setup, so I could use some help combing through my configurations and understandings to help me figure this one out.

I am using the DRBL stable, and 12.04 server, no GUI.

thanks in advance.



*edit* more info

******************************************************
The Layout for your DRBL environment:
******************************************************
          NIC    NIC IP                    Clients
+-----------------------------+
|         DRBL SERVER         |
|                             |
|    +-- [eth1] 192.168.1.60 +- to WAN
|                             |
|    +-- [eth0] 192.168.1.70 +- to clients group 0 [ 10 clients, their IP
|                             |            from 192.168.1.5 - 192.168.1.14]
|    +-- [virbr0] 192.168.122.1 +- to clients group virbr0 [ 1 clients, their IP
|                             |            from 192.168.122.1 - 192.168.122.1]
+-----------------------------+
******************************************************
Total clients: 11
******************************************************
Press Enter to continue...

---

