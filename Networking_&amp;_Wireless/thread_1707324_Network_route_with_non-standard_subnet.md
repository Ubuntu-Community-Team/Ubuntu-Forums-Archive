---
title: "Network route with non-standard subnet"
date: 2011-03-15
forum: Networking &amp; Wireless
---

### Post by CoRfr on 2011-03-15
Hi !

So I've installed a brand new ubuntu on a live usb, this thing is working fine on my home network, but I've got some problem here.

I've just started working at my new company (~80 people), and ... well, somehow, they decided to use 192.1.6. ips for the LAN instead of a standard IPV4 subnet for private network . :shock:

I don't understand this choice, but for now, it seems to work fine. A small part of the Internet is not available thanks to that, but the problem is that I simply don't have access to the Internet on my Ubuntu.

```
$route
Destination		Gateway		Genmask			Indic	Metric	Ref	Use	Iface
192.1.6.0		*			255.255.255.0	U		0		0	0	eth0
default			192.1.6.254	0.0.0.0			UG		0		0	0	eth0

```

If I ping something on the LAN or on the Internet, it works.
If I try to download something, or access a website, it fails.
Wget says "échec: Aucun chemin d'accès pour atteindre l'hôte cible." which means "failed: No route to host".

Any idea how to get things working for now ?

---

### Post by nicolasdiogo on 2011-03-15
hi,

as i understand this subnet is fine:
> 192.168.0.0/16 (192.168.0.0 - 192.168.255.255) reserved for Private-Use Networks [here]("http://en.wikipedia.org/wiki/List_of_assigned_/8_IPv4_address_blocks")

it seems odd to be able to ping something on the web. i understand that you are running:
ping bbc.co.uk

which get the DNS correct.

could you please run a tracepath like 
# tracepath bbc.co.uk/80

my results look like this:
 1:  mypc                                                  0.182ms pmtu 1500
 1:  192.168.13.1                                          6.239ms 
 1:  192.168.13.1                                          8.898ms 
 2:  192.168.13.1                                          5.811ms pmtu 1480
 2:  no reply
 3:  no reply
 4:  no reply
 5:  bbc-gw1-linx.prt0.thdoe.bbc.co.uk                    29.624ms 
 6:  212.58.238.149                                       30.667ms 
 7:  212.58.238.149                                       31.068ms !H

NOTE: good to see BBC saving money by using linux (bbc-gw1-linx)

---

### Post by CoRfr on 2011-03-15
Indeed, a 192.168.[0->254]. subnet would be fine for a private network.

I did ping few websites using their names, so it is actually able to use the DNS server correctly, but I checked resolv.conf and the DNS server is actually a local one, 192.1.6.4.

Here is the output of the tracepath:

```

$ tracepath bbc.co.uk/80
 1: ubuntu             0.283ms pmtu 1500
 1: 192.168.1.254      1.573ms
 1: 192.168.1.254      1.475ms
 2: 86.79.0.117       39.870ms
 3: no reply
[cropped]
31: no reply
  Too many hops: pmtu 1500
  Resume: pmtu 1500

```

I also checked out with Wireshark, when first contacting the server to establish the TCP connection, the router answer and says "Destination unreachable (Communication administrtively filtered)".

The exact same request from my desktop PC works fine.

It might not be the weird subnet after all, I will check things with the network administrator. ;)

---

### Post by ant2ne on 2011-03-15
That subnet choice is unusual, but it is not necessarily incorrect. If you can ping the interenet then your network is up. You say "A small part of the Internet is not available thanks to that" and that isn't true. Nothing in the information you have supplied is going to limit your network connectivity. You then say "but the problem is that I simply don't have access to the Internet on my Ubuntu" These two statements points to the possibility that your network administrator is using a proxy / filter (probably on .254) which restricts some websites on all valid network  devices and completely blocks all invalid network devices. Your ubuntu machine probably is not a valid device.

---

### Post by CoRfr on 2011-03-16
You are right, using Wireshark I saw that my packets were filtered (the gateway sent me a packet saying "Communication Administratively Filtered").

I just talked with the networking manager, and he said that addresses below 200 have access to the Internet, while addresses above are restricted.

They have few addresses left in that range so he didn't want my laptop to be binded in the non-restricted range ... I can deal with it (that laptop is for development purpose, ie USB / Ethernet analyser for a product I'm developing). Plus, only the 80 port is filtered, so I still can use ftp for apt update/upgrade/install. :)

PS: About the small part of the Internet I was referring to, I was talking about the tiny tiny part of computers located in the subnet 192.1.6. that are serving content on the Internet, which are probably located in the US as from what I found on Google.

Just for fun, does anyone know a website providing information about the IP allocation of an ISP/Organisation ?
Ie, some website that says "Range 88.22.0.0 / 255.255.0.0 is allocated to Acme Inc.".
The most precise db I have for now is [http://xkcd.com/195/]("http://xkcd.com/195/"):D

EDIT: And Thank You BTW ;)

---

### Post by ant2ne on 2011-03-17
> PS: About the small part of the Internet I was referring to, I was talking about the tiny tiny part of computers located in the subnet 192.1.6. that are serving content on the Internet, which are probably located in the US as from what I found on Google.That address range is not on the internet. It would be probably the intranet (notice the spelling) and the intranet is again controlled by your network administrator.

---

### Post by CoRfr on 2011-03-21
My brain is not following here :D

According to the [RFC1918](http://tools.ietf.org/html/rfc1918):

```
   The Internet Assigned Numbers Authority (IANA) has reserved the
   following three blocks of the IP address space for private internets:

     10.0.0.0        -   10.255.255.255  (10/8 prefix)
     172.16.0.0      -   172.31.255.255  (172.16/12 prefix)
     192.168.0.0     -   192.168.255.255 (192.168/16 prefix)
```

As I understand it, all Intranets, or Local Area Networks, **should** be subnets of these blocks.

However, in my case, the Intranet of my company uses another subnet, the 192.**1**.6.0/24 block.

With correct route tables, it isn't a problem (which I thought was at first :p ).

The thing is that the 192.1.6.0/24 block is allocated to [BBN](http://bbn.com/) according to [arin.net](http://whois.arin.net/rest/net/NET-192-1-6-0-1) (which, btw, is the exact kind of website I was looking for ;) ).

Therefore, from my company Intranet, I don't see how I can, without any hacks (tunneling, route editing ?) access any computer hosted with a 192.1.6.x IP on the Internet.

---

### Post by SeijiSensei on 2011-03-21
Short answer is, you can't.  However it appears you're not missing much.  Running "nmap -sP 192.1.6.0/24" returns "host is down" for all 255 addresses.

If the entire network is served by DHCP, it wouldn't be hard to migrate to a proper RFC1918 address structure.  Of course, it might hard to convince network administrators who don't seem to care about proper addressing.

---

### Post by emiller12345 on 2011-03-22
There is a chance that they may be overtaking someone elses ip range. I've been reading about problems that can occur in routing like this. 
[http://www.renesys.com/tech/presentations/pdf/blackhat-09.pdf](http://www.renesys.com/tech/presentations/pdf/blackhat-09.pdf)

---

### Post by ant2ne on 2011-03-22
You are correct. I miss read what you typed. Sorry.

The network 192.**1**.6.0/24 would be a public class A network. 192.**168**.6.0/24 would be a private class A network. I would find it hard to believe that your company owns all 255 addresses of the 192.1.6.0/24 network. So I'm betting that your network admin screwed up and should be using a 192.168.1.0/24 network.

This networking error should be a major embarrassment to your network admins. I don't see how an error of this type could go unnoticed for long. They must know about it, but are too lazy to try to fix it. Instead they just keep on going on like nothing is wrong. If the network grows they will regret not having fixed it. How many devices to they have on their network now? They can hire me and I'll go fix it for them.

---

