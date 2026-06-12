---
title: "DHCP/DNS Question"
date: 2012-04-26
forum: Networking &amp; Wireless
---

### Post by Jake.Debord on 2012-04-26
I have a server with eth0 and eth1

eth0 is connected to my modem with a public IP assigned to it and is also assigned x.mydomain.com

eth1 is setup as a DHCP server with the network 10.1.7.x and is connected to a switch.

DHCP correctly hands out IP addresses to devices attached to the switch. 

My problem:

I need to be able to route devices to x.mydomain.com from the eth1 network. What do I need to change for devices connected to eth1 to type in x.mydomain.com and be able to connect to eth0. 
Is this possible? 

Or, is it possible to assign x.mydomain.com to eth1 as well? If so, how?

---

### Post by Jake.Debord on 2012-04-26
Also, for what it is worth I have tried to enter the IP of eth1 of 10.1.7.103 in the hosts file and gave it the x.mydomain.com hostname.

---

### Post by SeijiSensei on 2012-04-26
You can use the same hostname for both interfaces, though the name must be resolvable by DNS queries to be usable from the Internet.  

> **Jake.Debord said:**
> I need to be able to route devices to x.mydomain.com from the eth1 network. What do I need to change for devices connected to eth1 to type in x.mydomain.com and be able to connect to eth0.

I don't really know what you mean by "connect" here.  Can you ping x.mydomain.com from external hosts, and from the internal host with that entry in its "hosts" file? Can you ping the IP addresses on either side, but not ping the hostname?  If so, that's a DNS problem.  If you're talking about connecting with a web browser, that's another story entirely.  Are you running Apache?  Have virtual hosts configured correctly?

Do you have packet forwarding enabled in /etc/sysctl.conf?  Edit that file as root with sudo and set "net.ipv4.ip_forward=1" as the instructions in that file explain.  Are you trying to connect from internal hosts to the external Internet?  Do you have masquerading enabled with iptables?

---

### Post by Jake.Debord on 2012-04-26
Yes I can ping x.mydomain.com from external hosts.
x.mydomain.com uses an A Record that points to the public IP of eth0

I cannot ping x.mydoman.com from hosts connected through eth1. 
eth1 is assigned 10.1.7.103 and works as a DHCP server
eth1 does not appear to have Internet access. Only local.
hosts on the 10.1.7.x network cannot ping x.mydomain.com even when I add 10.1.7.103 and x.mydomain.com to the hosts file.

I do not want to bridge the connections because eth1 needs to stay 10.1.7.103 and assign IP to hosts

---

### Post by Jake.Debord on 2012-04-26
> **SeijiSensei said:**
> You can use the same hostname for both interfaces, though the name must be resolvable by DNS queries to be usable from the Internet.  



I don't really know what you mean by "connect" here.  Can you ping x.mydomain.com from external hosts, and from the internal host with that entry in its "hosts" file? Can you ping the IP addresses on either side, but not ping the hostname?  If so, that's a DNS problem.  If you're talking about connecting with a web browser, that's another story entirely.  Are you running Apache?  Have virtual hosts configured correctly?

Do you have packet forwarding enabled in /etc/sysctl.conf?  Edit that file as root with sudo and set "net.ipv4.ip_forward=1" as the instructions in that file explain.  Are you trying to connect from internal hosts to the external Internet?  Do you have masquerading enabled with iptables?

I checked my /etc/sysctl.conf file here are the contents:

```

net.ipv4.ip_forward=1
kernel.msgmnb=65536
kernel.msgmax=65536
kernel.shmmax=68719476736
net.ipv4.conf.default.rp_filter=1
kernel.sysrq=0
net.ipv4.conf.default.accept_source_route=0
kernel.shmall=4294967296
net.ipv4.tcp_syncookies=1
kernel.core_uses_pid=1

```

---

### Post by SeijiSensei on 2012-04-26
I suspect that if you add a masquerading rule you'll be able to see the external interface (and the Internet) from machines in the 10 network.  Try this:

```
sudo iptables -t nat -A POSTROUTING -o eth0 -j SNAT --to-source ip.addr.on.eth0
```

replacing ip.addr.on.eth0 with the external IP address.

I just checked on a router I maintain, and I can ping its external address from inside with this rule in place.

Oh, and I wouldn't use bridging either.  The only time I've ever used bridging is when I had a virtual machine that needed to be visible from outside its host machine.

---

### Post by Jake.Debord on 2012-04-27
It tells me that --to-source is an unknown option

---

### Post by SeijiSensei on 2012-04-27
Hmm.  Maybe it's because I included "-t nat".  Try removing that; I noticed it isn't in the options list of the command on the router I checked.

---

### Post by Jake.Debord on 2012-04-27
No luck, do I have to restart iptables? Is that a permanent change or will it go away if I restart iptables. I checked iptables file and did not see any change

*edit* Could I just add some sort of forward rule to iptables and it do sortof the same thing?

---

### Post by newbie-user on 2012-04-27
> **Jake.Debord said:**
> I have a server with eth0 and eth1

eth0 is connected to my modem with a public IP assigned to it and is also assigned x.mydomain.com

eth1 is setup as a DHCP server with the network 10.1.7.x and is connected to a switch.

DHCP correctly hands out IP addresses to devices attached to the switch. 

My problem:

I need to be able to route devices to x.mydomain.com from the eth1 network. What do I need to change for devices connected to eth1 to type in x.mydomain.com and be able to connect to eth0. 
Is this possible? 

Or, is it possible to assign x.mydomain.com to eth1 as well? If so, how?

What you need is either an internal DNS server on your network or you need to manually specify on each device where x.mydomain.com is. Since your server is already a DHCP server, it should be easy enough to install a DNS server on it and then tell the network clients to use it as their primary DNS within the DHCP config.

---

### Post by collisionystm on 2012-04-27
> **Jake.Debord said:**
> It tells me that --to-source is an unknown option

use this

-A POSTROUTING -o eth0 -j MASQUERADE


iptables -A POSTROUTING -o eth0 -j MASQUERADE


I have 7 sites, each with an ubuntu 10.04 box as the firewall/router. They each have 2 nic cards. eth0 has the external address, eth1 has the internal.

I use UFW as my firewall.

You already have ip forwarding enabled in your sysctl, so thats good.

Once masquerade is in place, you will be able to browse the internet from any client that is using your box as its gateway.


your domain name is simply a record on an internet root dns server. You control where things go by doing an IP forward on your firewall.

---

### Post by Jake.Debord on 2012-04-27
> **newbie-user said:**
> What you need is either an internal DNS server on your network or you need to manually specify on each device where x.mydomain.com is. Since your server is already a DHCP server, it should be easy enough to install a DNS server on it and then tell the network clients to use it as their primary DNS within the DHCP config.

That is an option I have been playing with. I cannot get the DNS server to work correctly though. I set it up through webmin and I'm afraid I chose the wrong option when I started and now I can't figure out how to change it. The DNS server uses the root servers and for this ALL I care about is the DNS to point the url to the private IP. I can get my laptop to get an IP from the DHCP server but I'm not sure if it is successfully connecting to the DNS server.

---

### Post by Jake.Debord on 2012-04-27
> **collisionystm said:**
> use this

-A POSTROUTING -o eth0 -j MASQUERADE


iptables -A POSTROUTING -o eth0 -j MASQUERADE


I have 7 sites, each with an ubuntu 10.04 box as the firewall/router. They each have 2 nic cards. eth0 has the external address, eth1 has the internal.

I use UFW as my firewall.

You already have ip forwarding enabled in your sysctl, so thats good.

Once masquerade is in place, you will be able to browse the internet from any client that is using your box as its gateway.


your domain name is simply a record on an internet root dns server. You control where things go by doing an IP forward on your firewall.

I will try the masquerade again but what I was trying to do is keep traffic on eth1 from hitting the internet before it got to eth0

It sounds like I have to, I was hoping I could take traffic on eth1 and forward it to eth0 somehow. My clients on eth1 need to connect to server operation on eth0 BUT eth0 is dhcp and it gets assigned a static public IP from my modem. So, sounds like i have put DNS server on eth1 and assign a dns record the ip of eth1 to the same URL as assigned to eth0 

My big problem is that I have voip phones that use a URL to connect with. People like to just leave that so they can take their phone and work from home or on the road and not have to change the details for the server.

---

### Post by newbie-user on 2012-04-27
> **Jake.Debord said:**
> That is an option I have been playing with. I cannot get the DNS server to work correctly though. I set it up through webmin and I'm afraid I chose the wrong option when I started and now I can't figure out how to change it. The DNS server uses the root servers and for this ALL I care about is the DNS to point the url to the private IP. I can get my laptop to get an IP from the DHCP server but I'm not sure if it is successfully connecting to the DNS server.

In your dhcpd.conf, add this line to your subnet declaration:

```
option domain-name-servers [ip of your local dns], [ip of public dns]; 
```

That will tell your network clients to use your local DNS as the primary DNS.

Now for your DNS server, inside /etc/bind, you should have a db.[your network] file for your network. Add the following line to that db file:

```
x.mydomain.com IN A [internal ip address]
```

Then restart DNS and it should work (fingers crossed!).

---

### Post by newbie-user on 2012-04-27
> **Jake.Debord said:**
> I will try the masquerade again but what I was trying to do is keep traffic on eth1 from hitting the internet before it got to eth0

It sounds like I have to, I was hoping I could take traffic on eth1 and forward it to eth0 somehow. My clients on eth1 need to connect to server operation on eth0 BUT eth0 is dhcp and it gets assigned a static public IP from my modem. So, sounds like i have put DNS server on eth1 and assign a dns record the ip of eth1 to the same URL as assigned to eth0 

My big problem is that I have voip phones that use a URL to connect with. People like to just leave that so they can take their phone and work from home or on the road and not have to change the details for the server.

Wait, I think we're all trying to do two separate things here. So let me get this straight. You want to:

1) use your ubuntu server as a router/gateway to the internet
2) create an internal DNS server

Are those the two issues you're trying to get resolved?

---

### Post by Jake.Debord on 2012-04-27
> **newbie-user said:**
> Wait, I think we're all trying to do two separate things here. So let me get this straight. You want to:

1) use your ubuntu server as a router/gateway to the internet
2) create an internal DNS server

Are those the two issues you're trying to get resolved?

We are doing two things here. Either thing will work. Just working until I get one of them to work for me lol... 

I thought just forwarding packets from eth1 to eth0 would be much easier but turns out setting up a DNS server to resolve one host is going to be what I do lol

---

### Post by newbie-user on 2012-04-27
Forwarding packets from eth1 to eth0 is how you allow your lan network to connect to the Internet through your server. That's it. 

Having a local DNS server allows your local network to match ip addresses with hostnames on your local network.

I don't use webmin, so I don't know how to set up DNS using that method, but if you want, we can set up DNS manually. It's not hard.

---

### Post by Jake.Debord on 2012-05-02
Okay, I am willing to try that. Will the forward setting set to 1 will that forward traffic from eth0 to eth1 as well as forward eth1 traffic to eth0?

---

