---
title: "OpenVPN: Using multiple subnets with OpenVPN"
date: 2011-10-26
forum: Networking &amp; Wireless
---

### Post by sc0g on 2011-10-26
Hello!

**MY PROBLEM**
Right now, I am using 10.8.0.0 as the subnet for my end-users and their OpenVPN clients. However, I am adding users so quickly, I will probably run out of IP addresses on the 10.8.0.0 subnet!!!

**MY QUESTION**
What is the appropriate configuration parameter in server.conf in order to use multiple subnets? Is it this one?
```
# Configure server mode and supply a VPN subnet
# for OpenVPN to draw client addresses from.
# The server will take 10.8.0.1 for itself,
# the rest will be made available to clients.
# Each client will be able to reach the server
# on 10.8.0.1. Comment this line out if you are
# ethernet bridging. See the man page for more info.
server 10.8.0.0 255.255.255.0

```

**THE SOLUTION??????**
So--for example--if I wanted to choose between the 10.8.0.0 or 10.8.1.0 subnets, would I add an _additional "server" entry_ like the one below??
```
# Configure server mode and supply a VPN subnet
# for OpenVPN to draw client addresses from.
# The server will take 10.8.0.1 for itself,
# the rest will be made available to clients.
# Each client will be able to reach the server
# on 10.8.0.1. Comment this line out if you are
# ethernet bridging. See the man page for more info.
server 10.8.0.0 255.255.255.0
server 10.8.1.0 255.255.255.0

```


**BACKGROUND**
I am running OpenVPN on Ubuntu 10.04.3 LTS - it works great. I'm using a custom IPTABLES script to filter access to the various subnets I'm routing.
I am also assigning static/persistent IP addresses to my OpenVPN end-users using the ipp.txt file:
```
ifconfig-pool-persist ipp.txt 0

```

**Thanks a lot!** :D

---

### Post by jonobr on 2011-10-26
Hello



Im going to answer the subnetting part, not the configuration of your server that handles the subnets or the configuration of openvpn,
I would love to test it but again, Im going to stick with the sub netting portion.


If you control that entire space and have only hosts to worry about and the ability to change it, you could try creating a class B address for your clients.

server 10.8.0.0 and subnet  255.255.0.0 (This is a /16 subnet)
This will give you over 65,000 IP addresses.

10.8.0.1 - 10.8.255.254

If you didnt want to allocate that many and wanted to increment up in a smaller step you could use
10.8.0.0 with a subnet of  255.255.254.0  (/23 subnet mask)
Valid hosts in this range would be 
10.8.0.1 - 10.8.1.254
which would give you 510 hosts to use

As mentioned at the start though, you would need to check the configuration of your system before you change subnet masks, and ensure things would work after a change like this 
(especially if you have 250+ users to worry about)

If you wanted to create the second subnet, you would be getting into configuring a second subnet including default gateway for that subnet as well as its own specific routing , thats why I didnt want to get into those details as I didnt know the config of your server


Cheers


Jonobr

PS- I mention 250 users, You probably know this but your subnet above allows you 254 valid hosts)

---

### Post by jonobr on 2011-10-26
While re-reading my response, I notice I gave you a lot of detail about subnetting but it looks as if I didn't really answer your question, and it appears your question was not about subnetting at all :( <--- that's a face of shame.....


Anyway, I think your kungfu is strong, given you appear to have your routing under control using IPtables- adding the second subnet in can only be done that way.
I looked for similar examples but there are none, but it seems logical.

I would however recommend if you have that many users, you should get your self a small scale system that mirrors your setup.
Any changes you make should be implemented and tested on the small setup before rolling to the large.

---

### Post by sc0g on 2011-10-27
> **jonobr said:**
> server 10.8.0.0 and subnet  255.255.0.0 (This is a /16 subnet)
This will give you over 65,000 IP addresses.

10.8.0.1 - 10.8.255.254

If you didnt want to allocate that many and wanted to increment up in a smaller step you could use
10.8.0.0 with a subnet of  255.255.254.0  (/23 subnet mask)
Valid hosts in this range would be 
10.8.0.1 - 10.8.1.254
which would give you 510 hosts to use

Well how about that... It was staring me in the face the whole time. Don't you hate it when that happens?

Thanks a lot for the excellent reply. I think I'm going to use a 255.255.252.0 mask so I have a range of 10.8.0.0 - 10.8.3.255. This way I'll have 4 different "groups" of users each on different subnets and I can assign the IP addresses statically using shell scripts that modify the persistent ipp.txt file.

Thanks again. I really appreciate it.

---

### Post by jonobr on 2011-10-27
:guitar: Rock and roll baby !

Again, no harm giving it a test run on a test machine if you have it 

Cheers


Jonobr

---

