---
title: "OpenVPN &amp; BIND"
date: 2010-12-15
forum: Networking &amp; Wireless
---

### Post by PoZZyX on 2010-12-15
Hi,

On my server I've a OpenVPN gateway and a DNS bind9 serveur

At the moment, OpenVPN send opendns address to the clients and it works fine.

I would like to use my DNS server for my clients to work with any DNS address.

Here is OpenVPN config :
```

server 10.154.251.0 255.255.255.0
push "dhcp-option DNS 10.154.251.1" // I've tried with my public ip address, it doesn't work neigher

```

Bind9 options :
```

options {
        directory "/var/cache/bind";

        auth-nxdomain no;    # conform to RFC1035
        listen-on { 127.0.0.1; PUBLIC_IP; };
        allow-query { 127.0.0.1; 10.154.251.0/24; };
        allow-transfer { SECONDARY_DNS; };
        notify yes;
};

```

It would be nice if someone can help me.

Thanks ;)

++

---

### Post by PoZZyX on 2010-12-15
Found my error.

I needed to add 10.154.251.1 in listen-on.

Thanks

---

