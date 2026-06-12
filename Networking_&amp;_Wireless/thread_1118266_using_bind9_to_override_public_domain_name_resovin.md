---
title: "using bind9 to override public domain name resoving to private address"
date: 2009-04-06
forum: Networking &amp; Wireless
---

### Post by cattox on 2009-04-06
Hi,

I have just installed a web application on a local server. This application has the base server name configuration for URL construction, so my configuration points to my public domain.

The thing is I want to be able to access the application within my private network. So I tried to configure an entry for my public domain on bind9 (installed on a server in my private network) that points to the web server private address. No success :(

I have bind9 correctly configured to my private domain and private web server name. This works smoothly, so I tried to follow the same configuration to the external domain.

In /etc/bind/named.conf.local I added:

```

zone "[my public domain gos here]"(
type master;
file "/etc/bind/zones/[my public domain goes here].db"

```

In /etc/bind/zones/[my public domain goes here].db I have:

```

[host name of public domain]. IN SOA [host name of public domain].[public domain] [admin email with dot substituting @](

2007031001
28800
3600
604800
38400
)

[public domain]. IN NS [public host name].[public domain].
[public domain]. IN MX 10 [public host name].[public domain].

[public host] IN A [private address].

```

another thing that could help resolving this is:

from outside my private network my public domain is resolved, from within my private network, my public domain can't be resolved. This is strange since I have bind9 configured to forward requests to external DNS servers... :confused:

Does anyone have any idea on what could be wrong?!?!

thanks in advance

---

