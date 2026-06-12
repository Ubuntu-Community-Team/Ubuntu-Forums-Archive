---
title: "Ubuntu 13.04 dnsmasq problem with local dns server"
date: 2013-08-12
forum: Networking &amp; Wireless
---

### Post by yokey on 2013-08-12
Hi!

I just installed Ubuntu 13.04 and I had some problems when resolving hosts in my lan.

In my lan i have a domain suffix like: network.local

When i try to lookup a host like myserver.network.local with the command:

```
host server
```

I sometimes get *host not found* and sometimes i get the IP address as expected.

With my old ubuntu 12.04 all dns lookups were directly sent to my local DNS server 10.0.0.1 but now all requests go to dnsmasq running on localhost (127.0.0.1).

And that is the problem. My DHCP server does not offer only one DNS server.

It returns my lan DNS server and some others. Like

```
# /etc/resolvconf/resolv.conf.d/original
nameserver 10.0.0.1
nameserver 8.8.8.8
nameserver 8.8.4.4
```

The other nameservers are the google public nameservers (just as a fallback if 10.0.0.1 is unreachable).

But dnsmasq seems to use the nameservers arbitiary.

I could bypass the problem by manually adding /etc/NetworkManager/dnsmasq.d/dnsmasq.conf

```
server=/network.local/10.0.0.1
```

Is there any other solution for this problem?

---

### Post by papibe on 2013-08-12
Hi yokey.

I run DHCP server and DNS (bind9) on my home network.

Here a few tips:
[LIST]
[*]Set your DHCP server to send just one nameserver: 10.0.0.1
[*]Set your DHCP server to send a 'search' domain, so all hostnames (e.g. server) are translated into the local domain (server.localnet):
```
option domain-name "localnet.";
```
and
```
subnet 10.0.0.0 netmask 255.255.255.0 {
    ...
    option domain-name "localnet.";
}
```
(set proper netmask)


[*]Set your DNS to receive updates from the DHCP server (using a key).
[*]Set your DNS to use Google as forwarders:
```
forwarders {
    8.8.8.8; 8.8.4.4;
};

```
[/LIST]
Hope that helps. Let us know how it goes.
Regards.

---

