---
title: "Would like 2 NICs with one LAN, one NET and no sharing"
date: 2009-04-03
forum: Networking &amp; Wireless
---

### Post by cackles on 2009-04-03
Hi, Ive just set up Ubuntu and would like to have it set so one of my NICs is for the LAN only and the other the internet connection but absolutely no internet connection sharing except via squid, though squid is being avoided for now till these are sorted.

When I looked it up I have this in my config:

```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
```

I thought I could change it to this:

```
# The primary network interface
auto eth0
iface eth0 dhcp

auto eth1
iface eth1 inet dhcp
```

But, well, it dont work.

eth0 is the LAN side and eth1 the modem.

Any help appreciated, thanks.

---

### Post by superprash2003 on 2009-04-03
does your modem/router and your other NIC which is connected to your network have the ability to get an ip via DHCP?

---

### Post by Iowan on 2009-04-03
I presume the two interfaces don't wind up in the same subnet... the modem has (is) a dhcp server, and the LAN has a different one?

---

### Post by CyberMando on 2009-04-03
You do not want to remove lo from /etc/network/interfaces. Both NICs must be inet, whether going to the internet or not. dhcp says get an address automatically from dhcp server, such as your modem/router. You probably need to set a static ip for the internal interface. Try something like this
************************************************************************
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo eth0 eth1
iface lo inet loopback

# The primary network interface
face eth0 inet static
      address 192.168.0.100
      broadcast 192.168.0.255
      netmask   255.255.255.0
      network   192.168.0.0
      gateway   192.168.0.1

iface eth1 inet dhcp
****************************************************************
Be aware that which NIC is eth0 or eth1 is probably set in 
/etc/udev/rules.d/70-persistent-net.rules.

---

### Post by cackles on 2009-04-03
Both the LANs router and the modem can/will assign IPs, so Im assuming both should be DHCP. Its connected to the LAN just now and can talk to all the machines via eth0. I still need to add the adpater for the internet connection for eth1.

My main concern is a LAN machine being able to use the server for ics, I dont want that.

Can anyone point me to a list of parameters for NICs please? A big problem of mine is not even knowing what search strings to use to find things. Ive found tons of people that want their connections and need help but not what Im looking for.

---

### Post by CyberMando on 2009-04-03
If I understand this you are worried that computers on the LAN might get Network Address Translation or masquerading and be able to access the internet through this machine. Run
```
sudo iptables -L
```
and you will see a list of packet filter/firewall rules. There will almost certainly be none, so the NAT will not happen.

I am afraid I do not understand what you are asking for in the last part of your post.

---

### Post by kpatz on 2009-04-03
NAT/connection sharing is not enabled by default in Ubuntu.  You would have to set up iptables rules or set up ufw to enable it.

I assume the LAN gets its internet access through some other means (e.g. a router)?  Or no internet access whatsoever?

As long as the LAN machines' default gateway isn't set to the Ubuntu box's IP, they won't attempt to connect to the internet through it, even if NAT were enabled.

---

### Post by cackles on 2009-04-03
Ahhhh, excellent. I thought the whole loopback thing was it setting up for sharing, its disabled by default, thanks for rtelling me that.

Can I tell eth0 it is not allowed to even try to access the net? I have its MAC blocked to the net via the router, but would prefer to know how to disable something like on the server.

This is my setup, maybe make things clearer:

```

Internet connection1              Internet connection2
        |                                  |
        |                             Server eth1
        |                                  |
        |                               Server
        |                                  |
   4 Port Router---------------------Server eth0
        |                                   
    3 Clients      
```

Internet connection 1 is my cable connection and connection 2 adsl.

So now I should just need to add eth1 for the net.

I have cable modem and tv with one company and now the company that supplies the phone is giving us a free adsl connection to try and get us to move over and upgrade with them.

In last part of my post I mean I dunno the proper words to search for when looking things up in here on search engines. I havent used Ubuntu much because of time.

---

### Post by kpatz on 2009-04-03
So, just to get this straight:  the 3 clients access the net via the router to the cable internet.  The server is also connected to the router via eth0, but you don't want it to access the cable internet, you want it to access the internet via eth1 and the DSL connection.  Conversely, you don't want the 3 clients to access the DSL internet.

What you'll have to do is play around with the DHCP client on the server.  You'll want it to get an IP, gateway, and DNS from eth1 (the DSL connection).  You'll also want eth0 to get an IP from the router, but *not* a gateway address or DNS.  (Alternatively, if this really is a server, you may want to give it a static IP on eth0).

A machine access a local network via whatever ethernet port is connected to that network.  A machine accesses other networks via the default gateway.  So, you want your clients to use the router as a gateway (which they will by default, since the router will provide this info via DHCP), but you want the server to use a different gateway, the one on eth1.  So you'll have to tell dhclient on the server to not pull gateway or DNS info via DHCP when it pulls an IP on eth0, only on eth1.

The other thing to make sure is that the DSL modem and the router give out IPs in different ranges.  Many DSL modems have routers built in, that hand out private IPs like a router does.  For example, if your router issues 192.168.1.x IPs, and the DSL modem also issues 192.168.1.x IPs, you'll have to change either the router or the DSL modem to use a different IP range (such as 192.168.2.x).

Just wondering, what's the purpose of the setup?  Why will the server have its own separate internet connection?  What is the purpose of connecting the server to the router?  Is it providing services to the rest of the network (e.g. webserver, samba?)  Curious I am...

---

### Post by CyberMando on 2009-04-03
In this case you want to make sure you do not establish a default route on the eth1 connections. Probably the DHCP transaction will try to set a default route. If I were doing this I would set the eth1 ip static to make sure I did not establish that default route. If yo udi that make sure you give it an ip address that will not conflict with any other hosts on your network.

It is probably possible to avoid a default route on eth1 by editing /etc/dhcp3/dhclient.conf also but I do not know how to do that.

---

### Post by cackles on 2009-04-03
Thanks for the replies.

kpatz, your curiosity, I shall satisfy.

You actually hit the nail right on the head kpatz. The server will be an over glorified NAS [as per my tut]("http://ubuntuforums.org/showthread.php?t=799712").

The idea being I can use my tut version to do everything it has to and not get my backside throttled by my cable ISP and enjoy my gaming, also leaving the computers on the network to samba. ADSL will take the throttled bandwidth for downloads and my webserver, which is mainly text anyways.

---

### Post by tenmoi on 2009-04-03
> **cackles said:**
> 

Can I tell eth0 it is not allowed to even try to access the net? I have its MAC blocked to the net via the router, but would prefer to know how to disable something like on the server.



Let me clarify things a little bit here: So you want to serve the 3 clients but do not want the server to go to the internet via the cable modem, dont you?

YOu can use iptables, which comes default with ubuntu I think (I am on debian lenny right now so I dont know). You CAN TELL ETH0 and all interfaces on the server THAT they are NOT ALLOWED to access the net via eth0 by:

iptables -I INPUT -s gate_way_to_cable_modem (ip addresss) -j DROP
# this will not allow you server to receive any connection from the cable modem
 or

iptables -I OUTPUT -d gate_way_to_cable_modem (ip addresss) -j DROP
# this will not allow you server to get to this address of the cable modem, which is what you want I suppose.

I dont have a cable connection so I can just give you all this. I recommend you read iptables basics on netfilter.org.

---

### Post by cackles on 2009-04-04
Thanks tenmoi, I'll have a look at that.

---

