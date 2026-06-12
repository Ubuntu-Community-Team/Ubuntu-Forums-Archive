---
title: "Finding MAC addresses"
date: 2010-01-23
forum: Networking &amp; Wireless
---

### Post by dougHines on 2010-01-23
I am attempting to setup a cluster, and I need to find the MAC addresses of the nodes I'm attempting to put on the cluster's network.

I do not have a way to view the node information locally, and my cluster setup is diskless/server centric.

I was curious if any of you gurus knew of a way to view MACs without having to sit at each node and find them through the BIOS or something.


Just a note, I will at some point have to go in and make sure the boot priority in the BIOS is set to network/LAN as the primary.  I was just hoping to get around to setting up the server before I did the node BIOS setup.

Thanks
Doug

---

### Post by gnometorule on 2010-01-23
I'm probably misunderstanding your question, and am surely no network administrator, but you can find the MACs using something like

dmesg | fgrep eth

You still need to go to the nodes - as said, no network expert at all, but how could you avoid that if the nodes aren't linked yet? Gl.

---

### Post by JackRock on 2010-01-23
Unless you already have them hooked and connected to the node, you're not going to be able to see each MAC address without physically sitting at each one.  Do you have phone connectivity to each site?  Perhaps you can guide somebody who is local at each site.

---

### Post by him610 on 2010-01-23
> a way to view MACs

From a terminal:
```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:30:1b:bc:51:b8  
....
```

HWaddr is the MAC

---

### Post by dougHines on 2010-01-23
> **JackRock said:**
> Unless you already have them hooked and connected to the node, you're not going to be able to see each MAC address without physically sitting at each one.  Do you have phone connectivity to each site?  Perhaps you can guide somebody who is local at each site.

These nodes are in the same room as I am.  They are linked through a switch to a tower I am attempting to setup as a server.  I simply did not wish to have to connect a monitor/keyboard to each one in turn in order to find out the MAC address.  Is there even a method to finding the MAC address through the BIOS?

> From a terminal:
 	Code:
 	$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:30:1b:bc:51:b8  
.... 
HWaddr is the MAC 	
I do know how to find the MAC locally.  But is there a way to find the address through a remotely linked node ?  Like list the connections of say... a switch for example (And I do realize that I have to be able to tele into said switch in order to find out the configuration tables)  But perhaps something like a broadcast through the network that might return said MAC addresses?

---

