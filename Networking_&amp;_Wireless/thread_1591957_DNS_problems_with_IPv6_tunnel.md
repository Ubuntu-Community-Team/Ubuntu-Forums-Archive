---
title: "DNS problems with IPv6 tunnel"
date: 2010-10-10
forum: Networking &amp; Wireless
---

### Post by Sarek23 on 2010-10-10
Hi!

I configured a static SixXS IPv6 tunnel on my server. The tunnel is up and running flawlessly, also IPv4 still works.

But: It seems I have a DNS problem. When I try to resolve a hostname using nslookup and it does not have an AAAA record (aka IPv6 address) I get the answer that the domain does not exist. This is correct so far:

```

# nslookup
> set type=AAAA
> security.ubuntu.com
Server:8.8.8.8
Address:8.8.8.8#53

Non-authoritative answer:
*** Can't find security.ubuntu.com: No answer

Authoritative answers can be found from:
ubuntu.com
origin = ns1.canonical.com
mail addr = hostmaster.canonical.com
serial = 2010100902
refresh = 10800
retry = 3600
expire = 604800
minimum = 3600
```But when I do a ping6 on the exact same host, it gets resolved to the address of my local tunnel endpoint:

```

# ping6 security.ubuntu.com
PING security.ubuntu.com(cl-735.ham-02.de.sixxs.net) 56 data bytes
64 bytes from cl-735.ham-02.de.sixxs.net: icmp_seq=1 ttl=64 time=0.036 ms
64 bytes from cl-735.ham-02.de.sixxs.net: icmp_seq=2 ttl=64 time=0.060 ms
```This also happens when I try to do "apt-get update". Apt then prints out this message:

```

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/binary-i386/Packages.gz  404  Not Found [IP: 2001:6f8:1c00:2de::2 80]
```Does anyone of you know how I can stop those wrong DNS resolutions so that application fall back to using IPv4?

---

### Post by Sarek23 on 2010-10-10
I did a little more digging and found the error:

I had the following two lines in my /etc/resolv.conf:

```

domain mydomain.tld
search mydomain.tld

```

My domain also has a wildcard AAAA entry in its zone, so that all subdomains get resolved to my IPv6 address.

Apparently, after being unable to resolve a domain, Linux tried appending mydomain.tld to the hostname and then got an answer, resolving that name to my endpoint, thus not falling back to IPv4.

I removed those two lines and everything is in order now. The other obvious solution would have been to remove the wildcard.

Maybe this helps someone else having the same problem.

---

