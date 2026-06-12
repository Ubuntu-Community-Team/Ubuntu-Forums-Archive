---
title: "Multiple Static IPs on one server"
date: 2009-12-29
forum: Networking &amp; Wireless
---

### Post by cooki3s on 2009-12-29
Hey everyone,

Just gonna start this off by saying that I'm far from an expert at anything linux, but I do have some experience and I'm getting there. I'm renting a server from ovh.com, to set-up, amongst other things, some gameservers for my clan. I've set these things up before, but I learned now that I have 3 extra IPs I can assign to my server, which would make the management of these servers quite a bit easier. Here is where my problem starts; I'm unable to add these IPs to my server. A bit of googling showed me that I need to bind them in /etc/network/interfaces. I edited the file to reflect these extra ips, and I can ping them locally, but not from a web-tool or from my home pc.

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
        address 188.165.192.*
        netmask 255.255.255.0
        network 188.165.192.0
        broadcast 188.165.192.255
        gateway 188.165.192.254

auto eth0:0
iface eth0:0 inet static
address 91.121.219.*
netmask 255.255.255.255

auto eth0:1
iface eth0:1 inet static
address 91.121.219.*
netmask 255.255.255.255

auto eth0:2
iface eth0:2 inet static
address 91.121.219.*
netmask 255.255.255.255

```When I restart the networking interface it gives no errors or anything, just the usual OK. 
I tried netmask 255.255.255.0 before, but that gives one or more ```
SIOCSIFFLAGS: Cannot assign requested address
```Any ideas on how to fix this?

Thanks,

Cooki3s

---

### Post by Lord_ on 2009-12-29
What happens when you try to traceroute to one of those IPs from your home machine. Also have you configured default gateways for your new IP addresses. The new IPs need a gateway on their own subnet to route out from.

---

### Post by cooki3s on 2009-12-29
Thanks for the quick reply,

A traceroute gives this ```
tracert 91.121.219.*

Traceren van de route naar ***.cooki3s.com [91.121.219.*]
via maximaal 30 hops:

  1     1 ms     1 ms   <1 ms  192.168.1.1
  2    11 ms     8 ms     7 ms  78-23-96-1.access.telenet.be [78.23.96.1]
  3    12 ms    19 ms    13 ms  dD5E0C2C1.access.telenet.be [213.224.194.193]
  4    11 ms    11 ms    11 ms  dD5E0FD41.access.telenet.be [213.224.253.65]
  5    12 ms    11 ms    11 ms  dD5E0FDA9.access.telenet.be [213.224.253.169]
  6     9 ms    11 ms    11 ms  212.3.232.9
  7    14 ms    13 ms    12 ms  ae-11-11.car2.Brussels1.Level3.net [4.69.136.250]
  8    13 ms    15 ms    15 ms  ae-4-4.ebr1.Amsterdam1.Level3.net [4.69.136.254]
  9    15 ms    14 ms    15 ms  ae-1-51.edge4.Amsterdam1.Level3.net [4.69.139.138]
 10    14 ms    15 ms    15 ms  64.215.195.169
 11    13 ms    14 ms    15 ms  po1-20G.ar6.AMS2.gblx.net [67.16.134.142]
 12    22 ms     *       21 ms  20g.ams-1-6k.routers.ovh.net [94.23.122.133]
 13    25 ms     *      247 ms  20g.vss-2-6k.routers.chtix.eu [94.23.122.113]
 14     *        *        *     Time-out bij opdracht.
```Then it just continues to time-out until hop 30. When I do the same for the main server ip, it gives me the same traceroute but hop 14 is the main ip.

About the gateways, which one should I configure? I was only given these "fail-over" ips with no further info, and the only info I get from my providers manager is that they router on my main server ip.

Thanks,

---

### Post by timZZ on 2009-12-29
You said static?

But you have supplied IP ranges (the same one) to all 3 interfaces.

---

### Post by cooki3s on 2009-12-29
The * are to hide the exact ip ;) .

---

### Post by timZZ on 2009-12-29
Can you please confirm which version of Ubuntu you are using.

Does this issue happen during ifdown?

---

### Post by timZZ on 2009-12-29
If you ubuntu version <= 8.04 try the following.

1. Making sure you are up to date patch wise.
2. Removing 'wireless-tools' see if this resolves your alias issue.

(This may or may not work)

---

### Post by cooki3s on 2009-12-29
Hey,

I'm using the latest version, 9.10 . The package is not installed.
How would I go about using ifdown? I added everything manually to my /etc/network/interfaces .

Thanks,

---

### Post by timZZ on 2009-12-29
to invoke ifdown you simple type at command

```
sudo ifdown eth0
```

I believe there was an alias issue I.e. eth0:1 is an alias for eth0.  I am not aware of this in 9.10.

The problem was demonstrated in the ifdown command (it isn't 100%) I was just curious if your issue was showing the same "side effects".

Sorry if I think of something else I will let you know. (I am at work.. and not on a linux box)

---

### Post by cooki3s on 2009-12-29
Hey,

I'm afraid I can't try that since I'm SSHing into the server (its in the ovh datacentre).

Thanks for your reply,

---

### Post by Iowan on 2009-12-29
Having all aliases in the same subnet would seem to be a problem, and having them in their own subnet may make it difficult for them to do anything.  What are you trying to set up?

---

### Post by cooki3s on 2009-12-29
Well it's not really for me but some members of my clan have problems with the IP Port thing (not everyone is as acquainted with servers and the way it all works unfortunately) so having multiple IPs would allow for using the default port for some programs, like voice comms or gameservers, which would then allow for easier connection to these services.

I was told by ovh support to use this guide: [http://help.ovh.com/IpAlias](http://help.ovh.com/IpAlias) but it doesn't work, not even for just one alias. But I am able to ping them locally on the server, so maybe I'm missing some details for a remote connection? Atleast some part of the config works. Any idea if that could be the case and what I would need?

---

