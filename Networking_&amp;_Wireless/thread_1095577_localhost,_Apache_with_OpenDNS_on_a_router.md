---
title: "localhost, Apache with OpenDNS on a router"
date: 2009-03-13
forum: Networking &amp; Wireless
---

### Post by jestal on 2009-03-13
I have Apache2 installed.

I open Firefox 3.0x, and type "localhost".
I then get an openDNS screen that looks like a Google search result.

same thing if I type 127.0.0.1.


Here's my network:
DSL router 192.168.1.1
a wireless router (linksys) 192.168.1.2
both routers are configured with OpenDNS.


Here's my host file:
127.0.0.1 localhost
127.0.1.1 possumx.workgroup

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

Here's my resolv.conf:
nameserver 192.168.1.1


Why does "localhost" get sent to the router?
I thought that should stay on my computer and open the internal webpage.

---

### Post by Hobgoblin on 2009-03-13
Is Firefox configured to use a proxy?

If so you should have in the "No Proxy for:" box, at least ```
localhost, 127.0.0.1
```

---

### Post by jestal on 2009-03-13
i logged onto Root, and it works fine there.

any ideas?

---

### Post by jestal on 2009-03-13
in reply to your question, that statement is there, and it is set to Autodetect.

---

### Post by Hobgoblin on 2009-03-13
> **jestal said:**
> in reply to your question, that statement is there, and it is set to Autodetect.

To who's question, and what statement?

Assuming you mean the Firefox setting, try changing it to Use system proxy settings

If that doesn't work then try No Proxy.

---

