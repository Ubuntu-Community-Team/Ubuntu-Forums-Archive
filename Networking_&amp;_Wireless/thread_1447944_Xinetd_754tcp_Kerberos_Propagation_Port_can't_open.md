---
title: "Xinetd 754/tcp Kerberos Propagation Port can't open"
date: 2010-04-06
forum: Networking &amp; Wireless
---

### Post by romeroc24 on 2010-04-06
Hi, I can't open 754/tcp por for kerberos propagation, the service is krb_prop.

The file /etc/xinetd.conf:
```

defaults
{

}

includedir /etc/xinetd.d

```

The file /etc/xinetd.d/krb_prop:

```

service krb_prop
{
        disable         = no
        socket_type     = stream
        protocol        = tcp
        user            = root
        wait            = no
        server          = /usr/sbin/kpropd
}

```

Restaring the service:

```

$sudo /etc/init.d/xinetd restart

```

When I do:

```

$sudo nmap -sU -sT localhost

```

Can see some ports, but no krb_prop 754/tcp.

---

