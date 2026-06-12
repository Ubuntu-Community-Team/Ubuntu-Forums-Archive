---
title: "DNS Problems After Server Migration"
date: 2009-06-05
forum: Networking &amp; Wireless
---

### Post by Clodaus on 2009-06-05
I recently switched over from an older server running cPanel to a plain Ubuntu server with no special software. I adjusted all the DNS settings to point to the new server, but as soon as the old server was taken down, suddenly none of the domain names would resolve!

Bind appears to be properly set up on the new server. The domains in question are many, but I'm primarily concerned with otherkincommunity.net. The primary IP address of the new server is 70.38.37.113, and the domain is hosted on the IP 70.38.44.174.

The nameservers are: ns1.otherkincommunity.com, ns2.otherkincommunity.com

Here's some output:

```
$ nslookup otherkincommunity.net
;; connection timed out; no servers could be reached
```

```
$ nslookup otherkincommunity.net 70.38.44.174
Server:		70.38.44.174
Address:	70.38.44.174#53

Name:	otherkincommunity.net
Address: 70.38.44.174
```

The domains are set up to forward to the new host (as are the nameservers) through my registrar. Would anyone be able to assist me in diagnosing this problem? If anyone is able to successfully resolve the domain, that would also be very helpful information (I'm actively attempting to resolve the issue and hoping I get some sleep this morning).

---

### Post by Clodaus on 2009-06-05
Going back to my registrar's website and simply re-applying the DNS settings (no modifications, just getting it to update it again) seemed to begin to solve the problem. So my question would be - why wasn't this being considered the authority for the DNS record? It was being entirely ignored. I assume the authority was still the old server.

---

