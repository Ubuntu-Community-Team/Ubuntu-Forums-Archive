---
title: "Weird DNS client issues"
date: 2010-10-04
forum: Networking &amp; Wireless
---

### Post by nopcode on 2010-10-04
I'm having really weird and frustrating DNS issues with my clients unable to properly resolve the server's ip address. They can resolve each other's, and outside systems, but not the server - at least, not correctly, and not all the time.

I have one Ubuntu server set up that does both DHCP and DNS serving to the Windows systems. The server has DNS forwarding turned on to forward to OpenDNS's servers (I've tried using my ISP's dns servers but the problem remains).
The server is *not* set up as a firewall; I am actually using a DLink router for that, and the Dlink is *not* set up to serve up DHCP nor DNS.

What I am getting is that my clients - and there are nothing but Windows clients - will not resolve the name of the server. For example, if I do:

ping linuxserver

I get back a false IP address of 192.168.0.64 (and I've seen once a 192.168.2.49).

If, however, I put a dot in there:

ping linuxserver.

I get back the *correct* IP address of 192.168.0.2, and thereafter, ping'ng linuxserver without the dot will work. Until the dns cache expires, either naturally or with ipconfig /flushdns on the windows clients.

The client *are* getting valid dhcp leases and can resolve everything happy-happy, they just will not get the proper address of the server 100% of the time.

Any suggestions/clues/places to look? Can post configs if needbe.

---

### Post by SeijiSensei on 2010-10-04
Is this an internal server?  If you don't need to resolve names against it from outside, why are you using OpenDNS?  Just run bind9 on the server and make it the default nameserver for your Windows machines in dhcpd.conf.  Add a zone file for your domain and internal hosts, and you should be all set.  The server will query the root nameservers for anything it can't resolve locally and build a local cache of all the hostnames and addresses it has resolved.

Most of my clients have an internal DNS server for their LANs and an external server for public hostnames like [www.example.com](www.example.com).  You just need to make sure that any of those public hosts are also included in the internal zone file.

---

### Post by nopcode on 2010-10-04
Yes, it is an internal server, forwarding the dns queries - it is not running opendns locally, and is the name server for all of the clients. It's also behind a firewall brick, and is not accessible from the outside world. So basically, it's not configured at all like you think it is.

---

### Post by SeijiSensei on 2010-10-04
No, it's configured as I thought it was.  It's just not running a local nameserver but forwarding the queries out to OpenDNS.  As I said, instead of forwarding the queries, install bind9 so your server can reply to DNS requests locally, then add a zone file for your internal domain.

---

### Post by nopcode on 2010-10-04
Bind is installed, and is running, and it's the local name server. All the Windows client see 192.168.0.2 as the dns server address. If I stop bind on the linux server, they can't resolve anything, inside or out.

Here's the contents of named.conf.options for what it's worth:

options {
	directory "/var/cache/bind";

	forwarders {
		208.67.220.220;
		208.67.222.222;
		};
	forward first;
};


I've tried switching forward first to forward only and didn't get any different results.

named.conf.local is empty, and named.conf.zones, along with the zone files, are the stock defaults that comes when you install bind on Ubuntu.

---

