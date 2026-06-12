---
title: "DNS LAN/WAN confusion"
date: 2009-01-25
forum: Networking &amp; Wireless
---

### Post by shagymoe on 2009-01-25
Hi all, thanks in advance for any help. It is greatly appreciated.

I'm struggling a bit with setting up master and slave name servers. My goal is just to run my own name servers for mydomain.com.  I am not concerned at all with any internal DNS configuration. There are no workstations or anything like that to worry about.  The name servers are on different networks as you can see from the example WAN ip addresses.  My main confusion stems from what to put in /etc/hosts and also what to use for reverse DNS.  All of the examples I've seen typically use the LAN ip of the server, but some reference the WAN ip.  I've tried various configurations, and sometimes things seem to work, but then they flake out or some things work and some things don't. For example, if I look up ns1.mydomain.com, I'll get the right IP, but if I'm on the terminal of ns1, I cannot ping outside like google.com for instance.  What I really need is for someone to confirm or correct the way I have my various config files set up.  Below is the contents of each config file for both the master and slave servers.  Please let me know if I have anything wrong, especially in regard to reverse dns and /etc/hosts since changing these files seems to have the biggest impact on what works and what doesn't.  Here is the example information for my domain and servers. 

* Note: The master and slave LAN ips are similar, but they are not on the same LAN.
The LAN ip of the master name server (ns1.mydomain.com) is 192.168.0.101
The WAN ip of the master name server (ns1.mydomain.com) is 111.122.133.144 
The LAN ip of the secondary name server (ns2.mydomain.com) is 192.168.0.202
The WAN ip of the secondary name server (ns2.mydomain.com) is 222.233.244.255
The WAN ip of the mail server is 77.77.77.77
The WAN ip of mydomain.com is 88.88.88.88

[B]Master Name Server
ns1.mydomain.com Files[/B]

_File: /etc/hosts_

```


127.0.0.1       localhost.localdomain localhost
111.122.133.144 ns1.mydomain.com      ns1 

# should ^ this be 192.168.0.101 instead?


```

_File: /etc/bind/named.conf.local_

```


zone "mydomain.com" {
  type master;
  file "/etc/bind/zones/mydomain.com.db";
  allow-transfer { 222.233.244.255; };
};


zone "133.122.111.in-addr.arpa" {
     type master;
     file "/etc/bind/zones/rev.133.122.111.in-addr.arpa";
};

// Should the reverse DNS be this instead?:
// zone "0.168.192.in-addr.arpa" {
//      type master;
//      file "/etc/bind/zones/rev.0.168.192.in-addr.arpa";
// };


```

_File: /etc/bind/zones/rev.133.122.111.in-addr.arpa _
(Obviously if the reverse DNS above is wrong, then this file would be named: /etc/bind/zones/rev.0.168.192.in-addr.arpa and the PTR would be 101 instead of 144.)

```


$TTL 1500
@  IN SOA ns1.mydomain.com admin.mydomain.com (
                             2009012324        ;serial
                             28800             ;refresh
                             3600              ;retry
                             604800            ;expire
                             38400 )           ;minimum 25 minutes

                IN    NS     ns1.mydomain.com.
144             IN    PTR    ns1.mydomain.com.


```

_File: /etc/bind/zones/mydomain.com.db_

```


$TTL 1500
@  IN SOA ns1.mydomain.com. admin.mydomain.com (
                             2009012324        ;serial
                             28800             ;refresh
                             3600              ;retry
                             604800            ;expire
                             38400 )           ;minimum 25 minutes

mydomain.com.      IN      NS      ns1.mydomain.com.
mydomain.com.      IN      NS      ns2.mydomain.com.
ns1                IN      A       111.122.133.144
ns2                IN      A       222.233.244.255
mail               IN      A       77.77.77.77
mydomain.com.      IN      A       88.88.88.88
mydomain.com.      IN      MX      10    mail.mydomain.com.


```

_File: /etc/bind/named.conf.options_

```


options {
        directory "/var/cache/bind";

        forwarders {
            123.123.123.123;  // My ISP's DNS server.
        };

        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
};


```

_File: /etc/resolv.conf_

```


domain mydomain.com
search mydomain.com
nameserver 111.122.133.144

# Should ^ this be 192.168.0.101 instead?


```

_File: /etc/hostname_

```


ns1.mydomain.com


```

[B]Secondary Name server
ns2.mydomain.com Files[/B]

_File: /etc/bind/named.conf.local_

```


zone "mydomain.com" {
  type slave;
  file "/etc/bind/zones/mydomain.com.slave.db";
  masters { 111.122.133.144; };
};

zone "244.233.222.in-addr.arpa" {
     type master;
     file "/etc/bind/zones/rev.244.233.222.in-addr.arpa";
};

// Should the reverse DNS be this instead?:
// zone "0.168.192.in-addr.arpa" {
//      type master;
//      file "/etc/bind/zones/rev.0.168.192.in-addr.arpa";
// };

// ALSO: Should the reverse DNS zone type be "slave" instead of master?


```

_File: /etc/bind/zones/rev.244.233.222.in-addr.arpa_
(Obviously if the reverse DNS above is wrong, then this file would be named: /etc/bind/zones/rev.0.168.192.in-addr.arpa and the PTR would be 202 instead of 255.)

```


$TTL 1500
@  IN SOA ns2.mydomain.com admin.mydomain.com (
                             2009012324        ;serial
                             28800             ;refresh
                             3600              ;retry
                             604800            ;expire
                             38400 )           ;minimum 25 minutes
                IN    NS     ns2.mydomain.com.
255             IN    NS     ns2.mydomain.com.


```

_File: /etc/hosts_

```


127.0.0.1         localhost.localdomain localhost
222.233.244.255   ns2.mydomain.com      ns2

# Should ^ this be 192.168.0.202 instead?


```

_File: /etc/bind/named.conf.options_

```


options {
        directory "/var/cache/bind";

        forwarders {
            231.231.231.231;  // My ISP's DNS server.
        };

        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
};


```

_File: /etc/resolv.conf_

```


domain mydomain.com
search mydomain.com
nameserver 222.233.244.255

# Should ^ this be 192.168.0.202 instead?


```

_File: /etc/hostname_

```


ns2.mydomain.com


```

_File: /etc/bind/zones/mydomain.com.slave.db_

```


// To be updated by bind9 automatically from master server's config


```

Thanks so much for any help, I really do appreciate it.

Mark W.

---

### Post by shagymoe on 2009-01-26
For anyone else struggling with this, I believe I found the answer.  The only time the LAN ip should be used is in /etc/resolv.conf. All other ips are WAN ips.

Aslo, if you don't want /etc/resolv.conf to get overwritten when you reboot, you must change some settings in /etc/dhcp3/dhclient.conf

:change
send host-name "<domain-name>";
:to
send host-name "ns1.mydomain.com";

:change
#supersede domain-name "127.0.0.1";
:to
supersede domain-name "mydomain.com";

:change
#prepend domain-name-servers 127.0.0.1;
:to
prepend domain-name-servers <YOUR-LAN-IP-ADDRESS>;

---

