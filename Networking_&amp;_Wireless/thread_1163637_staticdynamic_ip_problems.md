---
title: "static/dynamic ip problems"
date: 2009-05-18
forum: Networking &amp; Wireless
---

### Post by Mike V on 2009-05-18
Can someone help me with this, first of all, I have the following files:

/etc/network/interfaces
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet static
address 172.24.123.189
netmask 255.255.254.0
gateway 172.24.122.1

```

/etc/hostname
```

SERVER-QTLBX-001

```

/etc/hosts
```

127.0.0.1	localhost
127.0.1.1	SERVER-QTLBX-001 SERVER-QTLBX-001.corp.mycompany.org


# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

The problem is that I can NOT connect to my station by name only by IP, I have another station within the same network the only difference is that the IP is dynamic and obviously the name (SERVER-QTLBX-002), here is the interfaces file:


/etc/network/interfaces
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

```

That terminal is using Ubuntu 7.10 and the other one (that fail) is using 8.04, anyone has any idea what I'm I doing wrong.

Note: also, both servers show the apache error of "apache could not reliably determine the server's fully qualified domain name".

Any help would be appreciated...

---

### Post by Iowan on 2009-05-19
[Here]("http://ubuntuforums.org/showpost.php?p=5678825&postcount=7") is  one hint. It's simpler than [this]("https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting%20Apache") help page suggestion... but another option.

---

### Post by Mike V on 2009-05-19
Thanks Iowan that solves the apache problem.

Does someone know how to resolve the other problem?

---

### Post by Iowan on 2009-05-19
Is the DHCP server also the DNS server? My old (Freesco) router used DNSMasq and could tie hostnames to DHCP leases. If the DHCP server can handle it, consider setting up a MAC address-based static lease.  That *should* put the "static-addressed" server in the same boat as the dynamic-addressed one... except it will have a predictable address. (BTW, make sure it's outside the DHCP server's range.)

---

### Post by Mike V on 2009-05-20
Thanks again Iowan but unfortunately I'm unable to move any aspect of the DCHP nor DNS server I need to find a way to do it in Ubuntu just like the dynamic IP addressed machine :(

---

