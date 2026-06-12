---
title: "Shrew Soft VPN client problems"
date: 2011-02-18
forum: Networking &amp; Wireless
---

### Post by knottshawk on 2011-02-18
I'm trying to use Shrew Soft VPN client (just installed the one available in synaptic... 1.5 I believe) on 10.10. I could connect to the VPN, but could not connect to our site (or any other site for that matter)
I made the suggested edits in sysctl.conf and 10-network-security.conf (changing filters to 0) and rebooted.

I can now access basic sites, like google, though they're quite slow. DNS is still unable to resolve my companies servers and nslookup fails on all attempts stating "nslookup: parse of /etc/resolv.conf failed"

If I disconnect from Shrew Soft, nslookup starts working again, and my speed to common websites (google) returns.

Ideas?

---

