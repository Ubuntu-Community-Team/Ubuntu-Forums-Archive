---
title: "Static IP with DNS Servers from DHCP?"
date: 2009-02-05
forum: Networking &amp; Wireless
---

### Post by sparks13 on 2009-02-05
I have been searching all morning in an effort to find an answer to this and I am officially stumped. At home, I have a router with numerous machines behind it. In an effort to go easy on my roommates, I let the router use DHCP to auto-assign IP's to their computers so they don't have to alter any settings. However, I have one machine that acts as a server for me which I would like to have a static ip address. However, I'd prefer not to have to specify which IP's my server uses for DNS because I move to a new apartment/city about every 6 months. This would get old having to change DNS servers everytime and quite frankly, I don't care what they are. Therefore, I would like to be able to set a static IP while still having the nameservers for the machine determined automatically. Is this possible? If so, how?

Thanks for any assistance.

---

### Post by Iowan on 2009-02-05
Consider setting up a static lease.  The router (if capable) will issue the same address - based on MAC address. The server will be set up for DHCP and *should* get the same info as the other DHCP clients. Like the current static address (could/should even be the same address), the static lease should be outside the range of the router's address pool.

---

### Post by aesis05401 on 2009-02-05
> **Iowan said:**
> ...the static lease should be outside the range of the router's address pool.

+1. This is how I run, works perfectly.  The OS always tries to renew the last active lease before applying for a new one, so being outside the normal range means never getting stepped on by other dynamically addressed machines.

---

### Post by sparks13 on 2009-02-05
Is the static lease set in the /etc/dhcp3/dhclient.conf?

Good to see another Iowan by the way.;)

---

### Post by sparks13 on 2009-02-05
So here's what I ended up doing that actually seems to be working.

I edited my /etc/dhcp3/dhclient.conf file by removing subnet-mask from the request options as such:
```

#request subnet-mask, broadcast-address, time-offset, routers,
#        domain-name, domain-name-servers, domain-search, host-name,
#        netbios-name-servers, netbios-scope, interface-mtu;
request broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, domain-search, host-name,
        netbios-name-servers, netbios-scope, interface-mtu;

```

Then I edited my /etc/network/interfaces file by adding this at the end:
```

iface eth0 inet static
   address 192.168.1.2
   netmask 255.255.255.0
   network 192.168.1.0
   gateway 192.168.1.1

```


**THIS DID NOT SOLVE THE PROBLEM.**
I was messing with the server today and it had since stopped functioning. I am not sure what changed overnight to disrupt it, but the solution ultimately failed. I finally gave in and assigned static DNS servers too.

---

