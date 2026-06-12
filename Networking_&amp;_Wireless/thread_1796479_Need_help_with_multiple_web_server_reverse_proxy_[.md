---
title: "Need help with multiple web server reverse proxy [Squid]"
date: 2011-07-03
forum: Networking &amp; Wireless
---

### Post by RobinBones on 2011-07-03
I have a squid reverse proxy working for all the domains that I specify in the squid.conf file. I would like to add an additional default rule, if the domain does not match one of the known domains.

I am mapping the domains to the particular servers using the following config lines.

```

cache_peer 10.10.20.15 parent 80 0 no-query no-digest originserver name=lamp_server login=PASS

acl sites_lamp dstdomain (list of domain names here)

cache_peer_access lamp_server allow sites_lamp

```is there an acl line that I can use for Other?

---

### Post by RobinBones on 2011-07-06
I was able to get it working by specifying 'all' instead of an acl, and also denying the other acl's on that server.

```

acl sites_lamp dstdomain (list of domain names here)
cache_peer_access lamp_server allow sites_lamp

cache_peer_access default_server deny sites_lamp
cache_peer_access default_server allow all

```

---

