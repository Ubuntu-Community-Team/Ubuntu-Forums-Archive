---
title: "Allow services only through specific IPs"
date: 2013-08-13
forum: Networking &amp; Wireless
---

### Post by ryan-coakley93 on 2013-08-13
Hello,

I have a server with 2 Ethernet ports that are enable to different IP addresses. I need to block SSH services on one, but allow from the other side. I also have another service on one side that needs to only run through the one ethernet port. Would I have to do this in network configs or through UFW?

Thanks

---

### Post by GwL3eNC on 2013-08-13
hi,

think you can do that with ufw/iptables.

---

### Post by prodigy_ on 2013-08-13
You can specify SSH settings in **/etc/ssh/sshd_config** file including which interfaces/addresses it should bind itself to.

---

### Post by SeijiSensei on 2013-08-13
If one of the interfaces connects to the public Internet, it should have a firewall with an INPUT DROP policy to block all incoming connections.  Then you can add individual rules to open specific ports.

```

/sbin/iptables -P INPUT DROP
/sbin/iptables -A INPUT -i eth1 -p tcp --dport 22 -j ACCEPT

```

The first rule blocks everything by default.  The second rule allows SSH connections that arrive on eth1.  You might also want to consider whether to block forwarding by default (if you permit forwarding in /etc/sysctl.conf) and only allow packets to be forwarded in specific circumstances.  See "man iptables" for details.

---

