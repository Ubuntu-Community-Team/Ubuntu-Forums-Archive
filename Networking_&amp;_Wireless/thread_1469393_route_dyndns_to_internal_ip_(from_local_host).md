---
title: "route dyndns to internal ip (from local host)"
date: 2010-05-02
forum: Networking &amp; Wireless
---

### Post by kingrolo on 2010-05-02
I'm struggling to solve this one even though I think it must be a common problem.

I'm happily running a Ubuntu 10.04 server including a mailserver at home and can access it either internally (LAN/WIFI) or externally (using a dyndns service). I've got my iPhone configured to work off the dyndns domain name and that seems to work fine both internally (WIFI) and externally (3GS). I get my emails synced to my iPhone and all is good.

Now, when I ping my dyndns name from inside the network (from any local client) I want to see the local IP address of my server (192.168.0.2) and NOT the public IP address provided by the dyndns service. That way I know that local traffic is going directly between client and server.

I have put an entry in my server's bind9 zones file "xxxx.dyndns.org   IN  A 192.168.0.2" and when I ping this address from the server I get 192.168.0.2..great! But when I ping from any other local client I still get the external IP address. :confused:

I appreciate there may be some gaping holes in my knowledge of this whole setup but solving this would be the icing on the cake as it's taken a lot of effort to get this far. 

TIA. :)

---

### Post by kingrolo on 2013-04-17
I was just looking at some old posts of mine and realised that I solved this one a long time ago.
It was just a simple entry in the bind9 zone. :P

```
$TTL 3600
$ORIGIN yourdomain.com.

@       IN SOA localhost. lars.localhost. (
        2010011800 ; sn = serial number
        172800     ; ref = refresh = 2d
        900        ; ret = update retry = 15m
        1209600    ; ex = expiry = 2w
        3600       ; min = minimum = 1h
        )

        ; we need one nameserver
        IN NS ns0

        ; and we're overriding the public ip address with
        ; this address.
        IN A 192.168.1.2

ns0     IN A 127.0.0.1
```

and this in the named.conf
```

zone "yourdomain.com" {
        type master;
        file "/etc/bind/zones/override.db";
};
```

---

### Post by wildmanne39 on 2013-04-17
Thread closed. Please do not post in old threads.

---

