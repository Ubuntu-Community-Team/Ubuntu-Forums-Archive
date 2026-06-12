---
title: "Ubuntu, Bind DNS, and IPv6"
date: 2012-10-10
forum: Networking &amp; Wireless
---

### Post by Abu_Dayya on 2012-10-10
I'm trying to test IPv6 in an ubuntu installation with BIND installed. And I have a very beginner question here, How do I give an IPv6 to the public DNS is addition to its IPv4 address? to make myself clearer, I'm not talking about the IP of the ubuntu box itself, I'm talking about the IP that the internet identifies my DNS with (e.g.81.xx.xx.xx)?

for example my ubuntu box ip is 192.168.1.220, but the IP that the world sees is 11.11.11.11. How do I make the DNS dual-stack? as in if anyone tried to nslookup my DNS, it will reply with both IPs.

I know this is more of a DNS question than its an ubuntu question. But any help is appreciated.

Thanks

---

### Post by lemming465 on 2012-10-10
There are at least three independent questions here; let's see if we can untangle them a little.

One issue is whether you are simplying running BIND as a local DNS caching recursive resolver, or if it is providing authoritative iterative DNS for domains you control.  In the former case your named.conf files will have "forwarder" clauses; in the latter a bunch of non-default non-RFC5735 (special use) zone paragraphs.  The serve zones to the outside world case can be further complicated by whether or not you are in a split-horizon scenario with different inside and outside views.  Outside service typically would be for static IP subnets, and involve domain delegation from a DNS provider.  Most DNS providers these days will do both IPv4 A glue records and IPv6 AAAA glue records pointing at your dual-stack DNS server.  Glue records are a set of NS, A, AAAA resource records in the parent domain indicating where the name service for a child domain lives.

To have a dual-stack DNS server, regardless of whether or not you have domain delegations, you need IPv6 service from your ISP. Preferably native, but possibly 6rd or 6in4 tunneled.  It's not a good idea to try to offer services over automatic IPv6 tunnels from automatic local 6to4 or Teredo addresses.

If you upstream router isn't sending IPv6 ICMPv6 Router Advertisement messages, you don't have dual-stack uplink, and should run a monostack BIND service, e.g. supply the command line option "-4".  You can test for router advertisements with rdisc6.
If "ip address show" doesn't have any inet6 family addresses starting with "2" (global scope), rather than just "fe80" (automatically generated LAN local scope), you don't have native IPv6 support from your ISP.

Clients querying your DNS server can ask IPv4 questions like A lookups or PTR lookups under in-addr.arpa, or IPv6 questions like AAAA lookups or PTR lookups under ip6.arpa.   They can pose these questions over either IPv4 transport or IPv6 transport.  What the client question is - A or AAAA, whether the question is asked over UDP (typical) or TCP (required for large answers like zone transfers), whether the LAN transport from the client to the DNS server is IPv4 or IPv6, and whether the uplink transport via the ISP to outside DNS servers is IPv4 or IPv6 are all completely independent issues.

---

### Post by lemming465 on 2012-10-10
Sorry, to answer your original question, if your host has BIND installed, by default the named process should be listening on all available IP interfaces, both v4 and v6.  See what "netstat -aln | grep -w 53" shows.  named.conf can have *listen-on* and *listen-on-v6* clauses to control this more specifically.  Typically you would find something like:```
listen-on port 53 { localhost; };
listen-on-v6 port 53 { localhost; };
```
for local-only DNS caching, or```
listen-on port 53 { any; };
listen-on-v6 port 53 { any; };
```
for providing name servers to reachable clients.  We're ignoring the potential complexities of iSCSI or other NIC interfaces you don't want to listen on, ACL's restricting which clients get which services, etc.

---

### Post by Abu_Dayya on 2012-10-14
> **lemming465 said:**
> There are at least three independent questions here; let's see if we can untangle them a little.

One issue is whether you are simplying running BIND as a local DNS caching recursive resolver, or if it is providing authoritative iterative DNS for domains you control.  In the former case your named.conf files will have "forwarder" clauses; in the latter a bunch of non-default non-RFC5735 (special use) zone paragraphs.  The serve zones to the outside world case can be further complicated by whether or not you are in a split-horizon scenario with different inside and outside views.  Outside service typically would be for static IP subnets, and involve domain delegation from a DNS provider.  Most DNS providers these days will do both IPv4 A glue records and IPv6 AAAA glue records pointing at your dual-stack DNS server.  Glue records are a set of NS, A, AAAA resource records in the parent domain indicating where the name service for a child domain lives.

To have a dual-stack DNS server, regardless of whether or not you have domain delegations, **you need IPv6 service from your ISP**. Preferably native, but possibly 6rd or 6in4 tunneled.  It's not a good idea to try to offer services over automatic IPv6 tunnels from automatic local 6to4 or Teredo addresses.

If you upstream router isn't sending IPv6 ICMPv6 Router Advertisement messages, you don't have dual-stack uplink, and should run a monostack BIND service, e.g. supply the command line option "-4".  You can test for router advertisements with rdisc6.
If "ip address show" doesn't have any inet6 family addresses starting with "2" (global scope), rather than just "fe80" (automatically generated LAN local scope), you don't have native IPv6 support from your ISP.

Clients querying your DNS server can ask IPv4 questions like A lookups or PTR lookups under in-addr.arpa, or IPv6 questions like AAAA lookups or PTR lookups under ip6.arpa.   They can pose these questions over either IPv4 transport or IPv6 transport.  What the client question is - A or AAAA, whether the question is asked over UDP (typical) or TCP (required for large answers like zone transfers), whether the LAN transport from the client to the DNS server is IPv4 or IPv6, and whether the uplink transport via the ISP to outside DNS servers is IPv4 or IPv6 are all completely independent issues.

Wow. now that was a bunch of DNS related stuff that I absolutely don't know anything about. But out of your post, I got the answer. The record for my public DNS IP is at the ISP. makes complete sense now. 

Thank you very much sir, and have a good day

---

