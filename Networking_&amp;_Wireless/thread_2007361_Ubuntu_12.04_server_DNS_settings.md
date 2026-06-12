---
title: "Ubuntu 12.04 server DNS settings"
date: 2012-06-20
forum: Networking &amp; Wireless
---

### Post by meshman on 2012-06-20
I'm running Ubuntu 12.04 and cannot get DNS to work for the life of me. I mean, just setting up the DNS servers for lookup, I'm not trying to install a DNS server. I've read so many variations on how to do this I'm completely confused:
 
resolve.conf - If I add the name server addresses here it works but the file always gets erased.
 
interfaces - I've added the line "dns-nameservers 192.168.72.6", to the primary (only) interface. This makes no difference.
 
dhclient.conf - I've changed the #prepend domain-name-servers line to reflect our 2 DNS servers. Still doesn't work but I'm not using DHCP, IP setup is static.
 
I can ping the name server IP addresses no problem, basic networking appears to be working other than DNS lookups.
 
How do I configure DNS servers for this version of Ubuntu?
 
Thanks!

---

### Post by meshman on 2012-06-20
Never mind, typo.  Thanks.

---

### Post by pctx on 2012-06-29
> **meshman said:**
> I'm running Ubuntu 12.04 and cannot get DNS to work for the life of me. I mean, just setting up the DNS servers for lookup, I'm not trying to install a DNS server. I've read so many variations on how to do this I'm completely confused:
 
resolve.conf - If I add the name server addresses here it works but the file always gets erased.
 
interfaces - I've added the line "dns-nameservers 192.168.72.6", to the primary (only) interface. This makes no difference.
 
dhclient.conf - I've changed the #prepend domain-name-servers line to reflect our 2 DNS servers. Still doesn't work but I'm not using DHCP, IP setup is static.
 
I can ping the name server IP addresses no problem, basic networking appears to be working other than DNS lookups.
 
How do I configure DNS servers for this version of Ubuntu?
 
Thanks!
You must edit: /etc/network/interfaces and add this to the bottom of your config:
```
# dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 192.168.1.1
        dns-search lcl

```

If you have multiple DNS servers (like I do) put a space in between each one.  I'm holding off on Ubuntu 12.04 LTS Server because of this bug.  Multiple DNS bugs are listed in the launchpad to be fixed I believe end of summer or early fall.
-A

---

