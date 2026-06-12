---
title: "Multiple NIC Card's (enable connection between Networks)"
date: 2010-12-31
forum: Networking &amp; Wireless
---

### Post by bmasotti on 2010-12-31
I have been trying to enable my desktop to have connectivity between (2) networks i.e. internet accessible and internal only 

example /etc/network/interfaces

auto lo 
iface lo inet loopback

auto eth0
iface etho inet dhcp

auto eth1
iface eth1 inet static
address 10.xx.x.x
netmask 255.255.248.0
gateway 10.xx.x.x

*****************************************

ethernet 0 - IP range default 192.168....
ethernet 1 - IP range default 10.40.....

*****************************************

Both of these card seem to be active as when I 'ifconfig' both are up and active. 

But when I try to connect or ping a web server on the internal network (I expect it to return, but am getting issues in connecting) 

I am relatively new to configuring these NIC card, Can anyone provide any advise or material that I might find of help 

Thanks in advance for your help !!! 

Brian

---

### Post by Iowan on 2010-12-31
Check (post) results of *ifconfig -a* to see if interfaces have the IP address. I haven't followed progress recently, but early in the release cycle, there was discussion that Network Manager needed to be disabled (or completely removed) for */etc/network/interfaces* to work properly. Dunno if that's still the case...

(You should be able to set up a static address for eth1 via NM as well)

---

### Post by bmasotti on 2010-12-31
Both eth0 & eth1 have IP's 

eth0 192.168.2.x
eth1 10.40.0.x

I've removed Network Manager because I read the previous post on this topic; I've been updating the interfaces file directly. 

Both Ethernet Card seem to state: 
....
...
UP BROADCAST RUNNING MULTICAST 

**************

Do I need to configure any DNS information ? 

Is there a way to peg an application to use one over the other ? Just wondering, because browser = eth0 and vlc eth1 ? please advise

---

