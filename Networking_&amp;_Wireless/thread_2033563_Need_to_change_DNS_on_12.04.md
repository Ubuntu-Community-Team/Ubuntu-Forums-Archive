---
title: "Need to change DNS on 12.04"
date: 2012-07-26
forum: Networking &amp; Wireless
---

### Post by lordbux on 2012-07-26
Hey guys

My ISP has hard wired 2 useless and censored DNS servers into my router.

and my resolv.conf file always rewrites itself to 192.168.1.1 which is my router.
This is pretty anoying because 1 It is a near useless DNS server it uses and 2 It keeps logs and sniffs where it is not suppose to. 

So I need to permanently change my DNS to 8.8.8.8 and 8.8.4.4
as i have few softwares that cache the DNS on startup and then keep using them and the ISP DNS are cripling them.

The new system in place is too inflexible and can be used for censorship if the user is not much techsavy. 

Please help me with this
thnak you in advance :guitar:

---

### Post by bakegoodz on 2012-07-28
Well there is many things you can do. The DNS is set on the client in the /etc/resolv.conf You can modify it, but the dhcp client in Ubuntu will rewrite it on reboot or reconnect this with what it gets from the dhcp server. I would recommend just changing the DHCP server settings in your router. You can have it just tell the clients to use the new DNS ip (Static DNS) or the cacheing DNS server in your router can also get its updates from a different DNS ip too. I setup my router to be a caching DNS server and to get DNS updates from OpenDNS. 
[IMG]http://i47.tinypic.com/6dvoe8.jpg[/IMG]
[IMG]http://i48.tinypic.com/wqwowp.jpg[/IMG]

It does sound like though that may not be an option
You could also set your IP staticly on your computer and disable DHCP

---

### Post by papibe on 2012-07-28
> **bakegoodz said:**
> I would recommend just changing the DHCP server settings in your router.

+1 for router settings, as they will apply to all clients.

Another alternatives:
[LIST]
[*]Set up clients with an static DNS. Check this [guide]("http://www.liberiangeek.net/2012/05/setup-static-dns-servers-in-ubuntu-12-04-precise-pangolin/") for servers, and [this]("http://ubuntuguide.net/google-public-dns-setting-up-an-alternative-to-current-dns-provider-in-ubuntu") one for desktop clients.
[*]Disable DHCP all together on the router, and set up as server for DHCP and DNS caching. 'dnsmasq' can do all that very easily.
[/LIST]
> **lordbux said:**
> i have few softwares that cache the DNS on startup and then keep using them and the ISP DNS are cripling them.

Fortunately, that is not entirely accurate ;)

Both the OS, and all applications that know are DNS agnostic. That means that every single resolution goes through the rules established (/etc/nsswitch.conf). That means that the moment you switch a DNS entry on /etc/resolv.conf, no one will have memory of the previous one.

Let us know how it goes.
Regards.

---

### Post by lordbux on 2012-07-28
Hai guys thank you for the response.

The first idea of editing the Router wont work as it just shows 2 DNS as labels, and does not allow it to be changed anywhere.

The issue that i thought was DNS caching was in reality my connection disconnecting and connecting at various intravels. So must have been rewriting the resolv.conf without my knowledge.


Then i am using 12.04 Precise and in the network client once i reach the connection area, I am unable to edit DNS box as it is greyed out.As Its a Wireless connection I am unable to see the connection when i open connection editor even when it is conencted. 

I tried ```
sudo network-admin
``` and it helped me edit it but again got reset on DHCP. 

And i made a mistake my resolv.conf read as 127.0.0.1 (localhost) but when i go to network settings of localhost i see 192.168.1.1

This is what is totally confusing me

---

### Post by papibe on 2012-07-28
> **lordbux said:**
> Then i am using 12.04 Precise and in the network client once i reach the connection area, I am unable to edit DNS box as it is greyed out.

In the method Automatic (DHCP) they are grey out, as it means 'obtain everything from DHCP'.

You have to change the method to '**Automatic (DHCP) addresses only**', so that the DNS Servers field becomes available.

Regards.

---

### Post by BkkBonanza on 2012-07-28
As of 12.04 the resolv.conf is handled differently. If you want to override it manually without using NetworkManager and keep a static value you can create a file in /etc/resolvconf/resolv.conf.d/

---

### Post by bakegoodz on 2012-07-29
Wow, nice answer. I edited /etc/resolvconf/resolv.conf.d/head and it copied its self to /etc/resolv.conf.

---

