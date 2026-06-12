---
title: "how do I manually add additional DNS search domains?"
date: 2010-02-25
forum: Networking &amp; Wireless
---

### Post by miatawnt2b on 2010-02-25
I am having trouble adding additional search domains to ubuntu.  I can add them to resolve.conf, but networkmanager will keep overwriting it. Is there somewhere else I can add the search domains?

Thanks,
-J

---

### Post by doas777 on 2010-02-25
well, I usually add them to resolv.conf, but then disable network-manager.

---

### Post by miatawnt2b on 2010-02-25
Yea, I really don't want to do that since it's a laptop and I migrate to several different wireless/wired networks.  The only thing I want to hard code are the search domains.

Thanks!
-J

---

### Post by Iowan on 2010-02-25
Network Manager gives you the option to add DNS servers... well, add may not be the right word. Under Edit connections, IPv4 settings, you can opt for DHCP-address only, which will then let you specify the DNS address manually.

---

### Post by doas777 on 2010-02-25
> **Iowan said:**
> Network Manager gives you the option to add DNS servers... well, add may not be the right word. Under Edit connections, IPv4 settings, you can opt for DHCP-address only, which will then let you specify the DNS address manually.

and on the same page you can add search domains, comma delimited.

---

### Post by miatawnt2b on 2010-02-26
> **Iowan said:**
> Network Manager gives you the option to add DNS servers... well, add may not be the right word. Under Edit connections, IPv4 settings, you can opt for DHCP-address only, which will then let you specify the DNS address manually.

The problem with this is that it also will not grab the DNS servers from DHCP.  This is bad for instance if you are going between two different domains which use two different Akamai webcache server farms.

So I need to get ALL dhcp addresses from the DHCP server in the domain I am in, but I also need to manually add search domains which remain constant.

-J

---

### Post by Iowan on 2010-02-26
You can add nameservers via the "prepend" in */etc/dhcp3/dhclient.conf* if you get an address via DHCP.

---

### Post by miatawnt2b on 2010-02-27
> **Iowan said:**
> You can add nameservers via the "prepend" in */etc/dhcp3/dhclient.conf* if you get an address via DHCP.

that's exactly what i did (though i used append) 

thanks!
-J

---

### Post by RonakG on 2010-06-10
> **miatawnt2b said:**
> that's exactly what i did (though i used append) 

thanks!
-J

Can you post your dhclient.conf file for reference?  I need to add entries for two search domains so that addresses like abc.com gets resolved to abc.com.xxx.com.

Thanks,
-R

---

### Post by miatawnt2b on 2010-06-10
stock dhclient.conf except for the addition of this line.

```

append domain-search "foo.net", "aero.foo.net", "aqua.aero.foo.net";

```

so if you run the command 'ssh dexter'  it will try dexter, dexter.foo.net, dexter.aero.foo.net, and dexter.aqua.aero.foo.net as well as you current local domains if you're in a different location.

-J

---

### Post by RonakG on 2010-06-11
> **miatawnt2b said:**
> stock dhclient.conf except for the addition of this line.

```

append domain-search "foo.net", "aero.foo.net", "aqua.aero.foo.net";

```

-J

It worked.  Thanks a lot.

---

### Post by SamTzu on 2010-08-21
This used to work simply by entering the additional search domains to /etc/resolv.conf.tail
Why was this made so difficult and obscure?

---

### Post by btindie on 2011-01-14
If you're using NetworkManager you can manually add additional DNS search domains by editing the configuration file for the connection.

E.g.
     /etc/NetworkManager/system-connections/Auto\ eth0
```
[ipv4]
method=auto
dns-search=my.domain.com;my.subdomain.com
```[https://help.ubuntu.com/community/NetworkManager0.7](https://help.ubuntu.com/community/NetworkManager0.7)
[http://projects.gnome.org/NetworkManager/developers/settings-spec-08.html](http://projects.gnome.org/NetworkManager/developers/settings-spec-08.html)

---

