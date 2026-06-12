---
title: "dhcp address"
date: 2013-02-20
forum: Networking &amp; Wireless
---

### Post by sniper8752 on 2013-02-20
How do I find the DHCP address that my desktop is using?

---

### Post by CharlesA on 2013-02-20
Run this from a terminal:

```
ifconfig
```

---

### Post by sniper8752 on 2013-02-20
which one is the DHCP address?

---

### Post by CharlesA on 2013-02-20
If you are asking about the IP address you got from DHCP, it is listed after "inet addr:"

[http://en.wikipedia.org/wiki/Ifconfig](http://en.wikipedia.org/wiki/Ifconfig)

---

### Post by sniper8752 on 2013-02-20
I just want the IP address of the DHCP server.

---

### Post by CharlesA on 2013-02-20
Here you go:
[http://www.cyberciti.biz/faq/linux-find-out-dhcp-server-ip-address/](http://www.cyberciti.biz/faq/linux-find-out-dhcp-server-ip-address/)

---

### Post by sniper8752 on 2013-02-20
i tried this and it told me that it doesn't exist.

i am running 12.0.4.

---

### Post by CharlesA on 2013-02-20
Try this:
```
cat /var/lib/dhcp/dhclient.leases
```

---

### Post by steeldriver on 2013-02-20
I think it's now

```
/var/lib/dhcp/dhclient.*<iface>*.leases
```where *<iface>* is the interface you want to know the lease for; e.g.

```
$ tail /var/lib/dhcp/dhclient.wlan0.leases
  option subnet-mask 255.255.255.0;
  option routers 192.168.1.1;
  option dhcp-lease-time 86400;
  option dhcp-message-type 5;
  option domain-name-servers 192.168.1.1;
  option dhcp-server-identifier 192.168.1.1;
  renew 3 2013/02/20 14:15:29;
  rebind 4 2013/02/21 01:01:27;
  expire 4 2013/02/21 04:01:27;
}

```

---

### Post by sniper8752 on 2013-02-21
Now this works with the server, but how would I find out the DHCP address that the client is contacting?

would it be in the dhclient.conf file?

---

### Post by steeldriver on 2013-02-21
The **leases file on the client** tells you which **server** it got its lease from
> **steeldriver said:**
> 
```
$ tail /var/lib/dhcp/dhclient.wlan0.leases
  option subnet-mask 255.255.255.0;
  option routers 192.168.1.1;
  option dhcp-lease-time 86400;
  option dhcp-message-type 5;
  [B][COLOR=Blue]option domain-name-servers 192.168.1.1;
  option dhcp-server-identifier 192.168.1.1;
[/COLOR][/B]  renew 3 2013/02/20 14:15:29;
  rebind 4 2013/02/21 01:01:27;
  expire 4 2013/02/21 04:01:27;
}

```

AFAIK there's nothing in the client configuration that can determine ahead of time what server is going to get used - a client just accepts its lease from whatever server answers its DHCPDISCOVER broadcast message with an acceptable DHCPOFFER - that's the way DHCP is designed

---

### Post by sniper8752 on 2013-02-21
it says that the file/directory could not be found.

---

### Post by redmk2 on 2013-02-21
> **sniper8752 said:**
> Now this works with the server, but how would I find out the DHCP address that the client is contacting?

would it be in the dhclient.conf file?
The client doesn't "contact a server".  It broadcasts a [COLOR="Red"]request[/COLOR] for an IP address on the subnet it is assigned to.  In your case that would be 192.168.1.0 /24.  The server responds to the broadcast and [COLOR="Blue"]offers[/COLOR] an IP address from a pool that is configured on the DHCP server.

---

### Post by CharlesA on 2013-02-21
> **redmk2 said:**
> The client doesn't "contact a server".  It broadcasts a [COLOR="Red"]request[/COLOR] for an IP address on the subnet it is assigned to.  In your case that would be 192.168.1.0 /24.  The server responds to the broadcast and [COLOR="Blue"]offers[/COLOR] an IP address from a pool that is configured on the DHCP server.

Yep. If there is more than one DHCP server on the network, it gets the IP from the one that responds first.

---

### Post by sniper8752 on 2013-02-21
oh ok.  thanks!

---

