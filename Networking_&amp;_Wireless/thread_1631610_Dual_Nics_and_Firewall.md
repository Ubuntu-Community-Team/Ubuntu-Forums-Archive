---
title: "Dual Nics and Firewall"
date: 2010-11-26
forum: Networking &amp; Wireless
---

### Post by keb329 on 2010-11-26
Please help.  This is driving me over the deep end.

I have an Ubuntu 10.04 machine with two nics, one for inside network and one for outside.  IPs are configured manually and correctly.  Inside nic is eth0, outside is eth1.  Both work properly when firewall is turned off.

I am using firestarter and have it configured with eth1 as internet connection and eth0 as lan connection.  If the firewall is enabled I cannot go to the internet unless I turn on internet connection sharing on the lan connection in the firestarter settings.  I also cannot even ping this machine from elsewhere on the network without turning that setting on or turning the firewall off.

This machine is intended to be a mail and ftp server so having both inside and outside connections is very desireable.

Obviously I am configuring something wrong and need some help.  I know there has to be lots of people with this same scenario and doing it successfully.

Help! Help! Help!

Anything would be most appreciated,
Kim

---

### Post by chopinhauer on 2010-11-26
> **keb329 said:**
> 
I am using firestarter and have it configured with eth1 as internet connection and eth0 as lan connection.  If the firewall is enabled I cannot go to the internet unless I turn on internet connection sharing on the lan connection in the firestarter settings.  I also cannot even ping this machine from elsewhere on the network without turning that setting on or turning the firewall off.


That is a completely normal behaviour: unless you have a (public) IP address for every machine on your network their traffic can not be routed on the Internet. Addresses in the private ranges 192.168.0.0/16, 172.16.0.0/12 and 10.0.0.0/8 are local only and their use is permitted without any registration.

Obviously that means that an Internet server cannot send a packet to 192.168.0.1, because such a host is not unique.

What Internet Connection Sharing does is to replace the machines private address with his own public address as packets come and go through the router.

---

### Post by e79 on 2010-11-26
I hope my knowledge is sufficient and my logic is not wrong, but here how I see it :

> I have an Ubuntu 10.04 machine with two nics, one for inside network and  one for outside.  IPs are configured manually and correctly.  Inside  nic is eth0, outside is eth1.  Both work properly when firewall is  turned off.Do I understand your Internet connexion (coming straight from the ISP modem) is plugged into your eth1  and you have another card, eth0, plugged into your LAN (switch, hub etc)? Do you intend to make this machine act as a router ?

> I am using firestarter and have it configured with eth1 as internet  connection and eth0 as lan connection.  If the firewall is enabled I  cannot go to the internet unless I turn on internet connection sharing  on the lan connection in the firestarter settings.  I also cannot even  ping this machine from elsewhere on the network without turning that  setting on or turning the firewall off. This answer my previous question. Having 2 NICS and configuring Firestarter this way would mean configuring it as a router. This is why you need to turn on the internet connection sharing to go on the web with this machine because if not, queries from eth0 are not being relayed to eth1. As for the ping, most firewalls are configured out of the box not to answer ping queries (I'm not sure for Firestarter).

> This machine is intended to be a mail and ftp server so having both inside and outside connections is very desirable. I'm not sure what you mean here, but if you mean 'separating/securing the inside LAN from the World Wicked Web, only  a router with a a firewall can do that, or a machine configured to do so. You don't need 2 NICs to achieve what you want IMHO. You either need to :

1. Have a router, configure a LAN address for your server, and forward the queries from the router (WAN) to it. Forward port 21 for FTP , port 25 for SMTP, port 110 for PoP3 and so on.
or
2. Put your server in a DMZ and lock it down properly (having a firewall, AIDE, Snort and else). But I would be scared to put anything in a DMZ other than Front-ends servers to be honest, so I would not recommend this configuration in your case.

Or did I misunderstood and you want this server to be a Mail and FTP server AND act as a router ?

---

### Post by SeijiSensei on 2010-11-27
Run the command

```
cat /proc/sys/net/ipv4/ip_forward
```

If the result is zero, your machine doesn't allow traffic to pass from one network interface to another.  This is the default for security reasons.  To fix this, edit (as root) the file /etc/sysctl.conf, set the parameter net.ipv4.ip_forward to one, and reboot.

---

### Post by keb329 on 2010-11-27
I think I didn't explain my topology very well so I'll do better this time I hope.

My mail server has 2 nics.  eth0 is on my inside network with a 192.x.x.x address and is connected to my inside router.  eth1 has a public ip of 173.x.x.x and is connected to my outside router/business gateway.  I have 5 ip's available through this gateway.

My goal is to be able to have local access to this server without having to go through the internet to get to it.  The server is not intended to be a router or used for ics.

There should be no need to pass packets between the nics.  

I think this is a routing issue but not sure.  My route says that the 192.x.x.x gw is the default which would not be what I want.  All internet traffic on this server should go out the public nic.  

Thanks,
Kim

---

### Post by chopinhauer on 2010-11-27
So, if I understand you correctly, the machines on the local network use another gateway (let's call it B) to reach the Internet (which probably connects to the 173.y.y.y router, A).

If your mail server M cannot reach the Internet with passing through B, your default route is probably messed up. If you use **NetworkManager** to configure the network on M, that might be the problem : when two gateways are available (like in your case A and B), NetworkManager sets the default route to the last discovered.

You have to activate an option called something like *Use this connection only for the resources of this network* in route option of your **eth0** interface to tell **NetworkManager** never to use this NIC for the default Internet routing.

If moreover you have problems with your clients connecting the SMTP server on M, you should check if the port 25 is authorized or dump the **iptables** rules and post them here :
```

sudo iptables-save

```

---

