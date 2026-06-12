---
title: "Forwarding DNS nameserver with a few hosts"
date: 2011-09-15
forum: Networking &amp; Wireless
---

### Post by felipe1982 on 2011-09-15
I have a domain "example.com" and its zone is managed by a third-party company.

Inside our network, we would like to have a few hosts (wiki.example.com) to point to private addresses 192.168.x.x. However, clients will still query the master external nameserver and get real public address when queried from the 'outside' (e.g. wiki.example.com 200.3.2.1 )

How can I configure BIND to resolve a few addresses internally for my domain 'example.com', but forward the unknown hosts for my domain (unknown.example.com) to the 'master' hosted by third-party company?

At the moment, my server is 'master' and gives NXDOMAIN for hosts that are not found in my own zone file. It doesn't attempt to 'forward' and ask the 3rd party NS.

The 3rd party NS is not configured to update slaves (axfr fails)

---

### Post by SeijiSensei on 2011-09-15
> **felipe1982 said:**
> How can I configure BIND to resolve a few addresses internally for my domain 'example.com', but forward the unknown hosts for my domain (unknown.example.com) to the 'master' hosted by third-party company?

You can't.  Just replicate the A and similar records from the public server in your private zone file.  For instance, if you want "www.example.com" to point your off-site web hosting service, use the same A record for the "www" entry in your local zone file as you do on the public server.

Usually my local zone files have local NS and MX records, but the A records include both private and public addresses.

I assume you have DHCP configured to give the clients the local DNS server's address.

---

