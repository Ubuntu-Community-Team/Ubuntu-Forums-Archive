---
title: "Two NIC's Routing ?"
date: 2011-02-27
forum: Networking &amp; Wireless
---

### Post by spike_strip on 2011-02-27
Hello all--

I have a server that has two NIC crads installed eth0 and eth1 we use a linksys router (192.168.2.1) which runs DNS for our LAN. I have installed Squid on the server which runs Ubuntu server (8.04 Hardy) w/ GUI. I can surf the net on the server with google chrome configured to use proxy server localhost:3128...works good. The router is wire directly to eth0.

I have my lap top (running Ubuntu Hardy) wired to eth1 and I want to be able to surf the Internet through my server. From my lap top, I can ping 192.168.2.100 which is the IP address assigned to eth1[?] by my router.   

I assume I need to establish a route from my lap top to my server. I would like to archive this via the CLI and I am not having any luck thus far. I have done many Internet searches and have searched this forum and have made little progress. And the more I read the more confused I get. 

Any help is much appreciated.

If I add static IP addresses to eth1on the server and eth0 on my laptop will this simplify the process? 

How can I add a route which will allow me access to the Internet via my laptop?

Server:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         192.168.2.1     0.0.0.0         UG    100    0        0 eth1
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 eth0
```

ifconfig eth1 on the server:

```
eth1      Link encap:Ethernet  HWaddr 00:30:48:85:cc:1b  
          inet addr:192.168.2.100  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::230:48ff:fe85:cc1b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7701 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7898 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:5572718 (5.3 MB)  TX bytes:1506869 (1.4 MB)
          Base address:0x9000 Memory:ef400000-ef420000 

```

---

### Post by YesWeCan on 2011-02-28
I do not understand your question. I do not understand your configuration description.

---

### Post by spike_strip on 2011-02-28
I am attempting to use my server as a router and gain access to the Internet via a client (e.g. my laptop) machine. 

The server is on line and has a second NIC (eth1) I want to be able to connect my client to eth1 and have access to the Internet; therefore, my server is functioning as a Proxy. My client machine will have access to the Internet only after it is routed through the Proxy Server. 

My question is how is this achieved? 

Do I add a route from the client's eth0 > then to eth1 on the server > then another route from eth1 to eth0 > then out to the Internet?    

The basic LAN configuration I have is the ISP supplied modem > Linksys router > Ubunut Server > Windows client's

My Ubuntu Server and the Windows machine are connected directly to the Linksys router.

---

### Post by YesWeCan on 2011-02-28
You want your Ubuntu server's eth1 to be an internet gateway? Is that what you want?

Your server connects to the internet via eth0 and a router?

You need to enable IP forwarding in the server's kernel.
You need to set up IP Masquerading in iptables OR set the router up to know that the gateway for the eth1 LAN is via eth0.
You need to allow forwarding in iptables (allowed by default).

See: [https://help.ubuntu.com/8.04/serverguide/C/firewall.html](https://help.ubuntu.com/8.04/serverguide/C/firewall.html)

---

### Post by spike_strip on 2011-02-28
> **YesWeCan said:**
> You want your Ubuntu server's eth1 to be an internet gateway?  
I was under the assumption that my router was the Internet Gateway on my LAN? My router is providing DHCP service. 


> **YesWeCan said:**
> 
Is that what you want?

Not sure...If I want/can have my Ubuntu server acting as a gateway. 

> **YesWeCan said:**
> 
Your server connects to the internet via eth0 and a router?



Yes, my server connects directly to the router from eth0 and eth1 is empty at this point.

---

### Post by YesWeCan on 2011-02-28
I may still be misunderstanding...sorry. I need a diagram. :)

Here's how I see it. Your router on the eth0 LAN is an internet gateway for that LAN (that subnet).

What I think you want is for eth1 to be the gateway for the eth1 LAN. The eth1 gateway then routes to the eth0 gateway.

A gateway is just the name for the device that routes between different subnets.

---

### Post by spike_strip on 2011-02-28
> **YesWeCan said:**
> I may still be misunderstanding...sorry. I need a diagram. :)

Here's how I see it. Your router on the eth0 LAN is an internet gateway for that LAN (that subnet).

What I think you want is for eth1 to be the gateway for the eth1 LAN. The eth1 gateway then routes to the eth0 gateway.


Yes, and this might be just my lack of knowledge in this area and me not using the proper terminology.

If my laptop connects to eth1 on my server and eth1 is the gateway for this subnet, then route to the eth0 gateway...yes this is what I am attempting to do.  

And I do not know how to set up the route table to archive this goal.  

I am only running Squid on the server and do not have IP forwarding enabled or any other services you have mentioned.

---

### Post by SeijiSensei on 2011-02-28
You don't need to use the server as a router if you're running Squid.  Just connect the server to the Linksys router and give it an address in the same space as the client machines.  Then configure the clients' browsers to use the server's IP and port 3128 as the proxy.

Using squid actually avoids many routing issues since it accepts HTTP requests, then re-sends them to the remote server. It can do this with just one NIC.  If you can view remote websites on the squid box, the squid daemon should be able to do the same.

If you're trying to set up transparent proxying, that's a different and more complicated matter.  But transparent proxying is only worthwhile if you have a large number of clients that you'd need to configure manually, or if you have people on the client machines who know how to disable the proxy.

---

