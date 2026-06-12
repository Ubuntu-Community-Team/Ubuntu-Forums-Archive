---
title: "Separated DNS config for tun0/eth0 while using vpnc"
date: 2011-09-05
forum: Networking &amp; Wireless
---

### Post by glomack on 2011-09-05
Hi, I'm using vpnc which it is working just fine. However every time I connect to the vpn server resolv.conf is "overridden" with new information returned by the current DHCP server. I'd need to keep the DHCP configuration I had for eth0 while still accepting the new config for the tun0 interface. This way I'll be able to access resources from both ends by their names because even I can access them by IP I'd need to keep using their names. How can this be achieved?

Thanks for your help!

---

### Post by glomack on 2011-09-09
As per what I've investigated, within Unix/linux systems we just have one DNS configuration (resolv.conf) at a time and this is the way it works. As a workaround we may have two options:

1 - use hosts file to statically map the names we need. This is a well known, quick and simple solution if we just have few resources to map.

2 - the second solution would be to install and configure a local name server to forward request to the desired name servers based on customized rules. After that, avoid the resolv.conf file to be overridden and setup the local name server as name resolver.

If anyone else is aware of any other way to do it please let me know.

---

### Post by SeijiSensei on 2011-09-09
One simple solution might be to add a "prepend" directive to /etc/dhcp3/dhclient.conf.  The standard file gives the example:

```
prepend domain-name-servers 127.0.0.1;
```

If you use a similar command with the IP address of the DNS server supporting queries over the tunnel, it will put that at the top of the list of servers in resolv.conf.  Queries will then be sent first to that server, but if it cannot be reached, the resolver will try the next server in the list.

You can control other things like whether the client should ignore DNS configuration data sent via DHCP by editing the "request" directive in dhclient.conf.  See "man dhclient.conf" for details.  One solution would be to remove the "domain-name-servers" and "domain-search" entries from that list, then create a static resolv.conf that meets your needs.

---

