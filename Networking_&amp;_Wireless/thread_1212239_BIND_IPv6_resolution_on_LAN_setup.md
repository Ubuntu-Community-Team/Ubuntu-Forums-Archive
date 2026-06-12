---
title: "BIND IPv6 resolution on LAN setup"
date: 2009-07-13
forum: Networking &amp; Wireless
---

### Post by austinium on 2009-07-13
hi,

I am trying to setup BIND as a DNS server for local IPv6 name resolution within a LAN.

heres the network:
Ubuntu 8.10 running BIND 9.5.0-P2
    IPv4     - 192.168.1.8 
    IPv6     - fe80::a00:27ff:fe56:7f27/64
    hostname - dnsserver
Windows XP SP2
    IPv4     - 192.168.1.7
    IPv6     - fe80::a00:27ff:fea8:81ed%5
    hostname - winclient

Both the IPv6 are autoconfigured, while IPv4 addresses are via DHCP.

As long as iam working with IPv4, things work. I forced dnsserver's IPv4 address on winclient's DNS settings.
i can ping winclient and it resolves its IPv4 address. (i get replies from the IPv4 address)

However, as soon as i add dnsserver's IPv6 address as DNS using ```
netsh interface ipv6 add dns "Local Area Connection" fe80::a00:27ff:fe56:7f27/64 
```
I am no longer able to resolve winclient's IP address (i get replies from IPv6 loopback address ::1).

On dnsserver:
this is the /etc/bind/named.conf.options file 
```
forwarders {
59.179.243.70;
203.94.243.70;
};

auth-nxdomain no;

listen-on-v6 { any; };
```

and this is the /etc/bind/named.conf.local file
```
zone "dnsserver." {
    type master;
    file "/etc/bind/db.dnsserver";
};

zone "1.168.192.in-addr.arpa" {
    type master;
    file "/etc/bind/db.1.168.192";
};
```

this is the zone file 
```
;forward lookup zonefile
$TTL 86400
dnsserver.    IN    SOA    dnsserver. dummy.rms. {
   
        2009071309    ; Serial no., based on date
              21600     ; Refresh after 6 hours
               3600     ; Retry after 1 hour
             604800     ; Expire after 7 days
               3600     ; Minimum TTL of 1 hour
    )
;Name Servers
dnsserver        IN    AAAA fe80::a00:27ff:fe56:7f27/64
dnsserver        IN    A    192.168.1.8
@                IN    NS    dnsserver

;clients
client    IN    A    192.168.1.7    
client    IN    AAAA fe80::a00:27ff:fea8:81ed%5
```

Any help would be greatly appreciated.

Thanks

---

