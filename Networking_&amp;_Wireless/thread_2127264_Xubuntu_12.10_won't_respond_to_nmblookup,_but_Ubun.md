---
title: "Xubuntu 12.10 won't respond to nmblookup, but Ubuntu 12.04 Lts server does"
date: 2013-03-19
forum: Networking &amp; Wireless
---

### Post by conoral11 on 2013-03-19
Hi there,

I am in the process of setting up Backuppc on my server to backup a host of windows / non windows systems.

I've used it in the past very well, until my server was stolen one day....

So i've got a new server (Ubuntu 12.04 LTS x64) all nicley setup.

I've installed backuppc

Setup a host (Neptune) Xubuntu 12.10

The thing is, the server with backuppc doesn't get a responce when doing a nmblookup -A Neptune, Neither does the host Neptune itself.

Both can resolve the server (Mars)

Both can't resolve the host (Neptune)

On the Server (Mars):

```
$nmblookup -A Neptune
Looking up status of 192.168.1.138
No reply from 192.168.1.138
```

```
$nmblookup -A Mars
Looking up status of 127.0.1.1
MARS    <00> -    B <ACIVE>
""
""
WORKGROUP <1e> - <GROUP> B <ACTIVE>

```


And on the Host (Neptune)
```
$nmblookup -A Neptune
Looking up status of 192.168.1.138
No reply from 192.168.1.138
```

```
$nmblookup -A Mars
Looking up status of 192.168.1.70
MARS    <00> -    B <ACIVE>
""
""
WORKGROUP <1e> - <GROUP> B <ACTIVE>

```

What have I over looked?

Kind Regards

Conoral11

---

### Post by wrzomar on 2014-01-09
I had similar problem between 10.04 and 12.04, both desktop versions. When running nmblookup from precise lucid was sending back response and precise wasn't in the other way, but in wireshark I saw that precise was sending responses but problem was lucid's firewall. I added one rule to lucid's firewall and it's working now.
Use some packet sniffer to check out what the problem really is and then solve it.

Best Regards,

wrzomar

---

