---
title: "Ubuntu Server unable to reach outside LAN"
date: 2010-03-17
forum: Networking &amp; Wireless
---

### Post by Landslide on 2010-03-17
I have just set up a server on the LAN to host some internal projects. It has two NICs which I will call eth0 and eth1, since that's what they are in ifconfig. They're both the same kind of NIC. Everything on the network reaches the external internet by way of a Windows 2003 gateway server, which is the DNS and firewall.

I'd like the server to be able to install security updates automatically, so it needs to be able to reach the ubuntu repos, but I also need it to have a static IP so I can host a database and some other stuff on it that I can access on the LAN.

When I first booted the server, I was able to install security updates just fine, because only eth0 was configured and it was set to DHCP. I changed /etc/network/interfaces to set both eth0 and eth1 as static IPs one digit apart, and specified in each interface definition the IP of the Windows gateway. I also verified in /etc/resolv.conf that the only name server defined was the IP of the Windows server. I then added DNS records on the Windows server to match the IPs I specified in the interfaces file.

Now I was able to access the server by hostname (using SSH from my local machine) but when I tried to get to the outside from the server, it's not working. Like so:
```

$ ping ubuntu.com
PING ubuntu.com (91.189.94.156) 56(84) bytes of data.
^C
--- ubuntu.com ping statistics ---
9 packets transmitted, 0 received, 100% packet loss, time 8003ms

```

So it's able to resolve ubuntu.com into an IP, but none of the pings I send ever reach the destination, even though when I was using DHCP, it works just fine.

Just to test, I set one of the two NICs to use DHCP and the other to declare a static IP-- I thought I might be able to get through the gateway with the DHCP interface to get updates, and still reach the server internally via the static interface. My /etc/network/interfaces thus looked like this:
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1
iface eth1 inet dhcp

auto eth0
iface eth0 inet static
address 192.168.100.7
netmask 255.255.255.0
gateway 192.168.100.1

```

With both interfaces up, I can reach the static address on the LAN, but I cannot reach the outside. If I take down eth0 but leave eth1 up, I can magically reach the outside again, but I don't have the static IP I need. 

Have I misconfigured something? Is there a good solution to my problem? Or is it perhaps some problem with the Windows box? I have been secretly hoping that it isn't, because I have barely any knowledge of Windows server administration. I had to fumble through a variety of menus just to figure out how to add the DNS records.

Thanks for any help you can give.

---

### Post by Grenage on 2010-03-17
Can you post the details (IP/GW/DNS) that DHCP gives you, please?

---

### Post by Landslide on 2010-03-17
Here's what happens when I bring down the interface that's set to use DHCP and then bring it back up.

```

$ sudo ifdown eth1
There is already a pid file /var/run/dhclient.eth1.pid with pid 2532
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:11:43:ea:b5:57
Sending on   LPF/eth1/00:11:43:ea:b5:57
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.100.1 port 67

$ sudo ifup eth1
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:11:43:ea:b5:57
Sending on   LPF/eth1/00:11:43:ea:b5:57
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 18
DHCPOFFER of 192.168.100.34 from 192.168.100.1
DHCPREQUEST of 192.168.100.34 on eth1 to 255.255.255.255 port 67
DHCPACK of 192.168.100.34 from 192.168.100.1
bound to 192.168.100.34 -- renewal in 303586 seconds.

```

---

### Post by Grenage on 2010-03-17
A quick fix here would be to assign a DHCP reservation on the Windows DHCP server for the IP's you want.  What that won't tell you is why it's not currently working; are you sure the DNS/Gateway assigned by DHCP is the same as the one you're using for the static?  Is it possible that there's a gateway router that is being used as the gateway?

---

### Post by Landslide on 2010-03-17
I told the administrator of the Windows box that it might be an ISA issue and he seemed to know what that meant, so I'm thinking a solution is close at hand. Thanks for all your help!

---

### Post by Grenage on 2010-03-17
Here's hoping, good luck!

---

