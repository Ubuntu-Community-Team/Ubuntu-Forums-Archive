---
title: "How to acccess Multicast IP in local network? (IPs not the same range!)"
date: 2009-07-27
forum: Networking &amp; Wireless
---

### Post by janmartin on 2009-07-27
Hi all,

I got a new Network Camera with a Web-Interface.

IPs:
192.168.178.200   Camera Web-Interface
192.168.178.24    PC
192.168.178.1     Router (FritzBox! Fon 7170)

I can access the camera web interface from my PC.

225.128.1.128    Multicast IP of network camera

Multicast addresses are always in the range
224.0.0.0 through 239.255.255.255.

Question:
How do I connect to the Multicast stream of the camera?
Just entering 225.128.1.128 into Firefox, VLC or MPlayer does not work. 

I am clearly not a network guy.

Thanks,
Jan

---

### Post by ndoggac on 2010-09-02
It should be something along the lines of:

sudo route add -net 224.0.0.0/4 dev eth1

Although I've been having problems with getting to this to work properly.  It's much more difficult than performing the same operation in Solaris Unix.

The /4 means 224 through 239 on the first address octet is matched. The 'eth1' would change for your ethernet device.  Run the following command to get a list of your network interfaces

sudo ifconfig -a

you can also use the following command to view the routing table:

sudo netstat -rnv

The route add command is not persistent between reboots, to make it persistent you need to add an entry in the following file...

/etc/network/interfaces

Google around for proper formatting of this file...

you will use 'post-up' and 'pre-down' in the file along with the "route add" and "route del" commands.

---

