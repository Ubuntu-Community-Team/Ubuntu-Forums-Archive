---
title: "CDDB request using HTTP"
date: 2011-02-03
forum: Networking &amp; Wireless
---

### Post by pmatos on 2011-02-03
Hi al,

It might seem strange to have this under networking instead of multimedia but bear with me. 

The problem started with abcde, the cd ripper, hanging on the console and staying there forever.

After digging I traced this to the cddb-tool request to the freedb server.
The following request just hangs:

```
$ wget -e timestamping=off -O - 'http://freedb.freedb.org/~cddb/cddb.cgi?cmd=stat&hello=pmatos+mietzekatze+cddb-tool+0.4.7&proto=6'
--2011-02-03 19:54:44--  http://freedb.freedb.org/~cddb/cddb.cgi?cmd=stat&hello=pmatos+mietzekatze+cddb-tool+0.4.7&proto=6
Connecting to 10.100.100.15:8080...
```

Now, since:
```
$ ping freedb.freedb.org
PING freedb.freedb.org (195.214.216.38) 56(84) bytes of data.
64 bytes from mirror.freedb.org (195.214.216.38): icmp_req=1 ttl=47 time=62.1 ms
64 bytes from mirror.freedb.org (195.214.216.38): icmp_req=2 ttl=47 time=62.2 ms
64 bytes from mirror.freedb.org (195.214.216.38): icmp_req=3 ttl=47 time=68.6 ms
```

Why is my request being done to 10.100.100.15:8080 which just hangs forever? Any tips? 

Can you reproduce this?

Cheers,

Paulo Matos

---

