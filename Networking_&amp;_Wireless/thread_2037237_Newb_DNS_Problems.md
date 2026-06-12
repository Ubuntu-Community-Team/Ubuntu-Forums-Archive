---
title: "Newb DNS Problems"
date: 2012-08-04
forum: Networking &amp; Wireless
---

### Post by spazlon on 2012-08-04
I am trying to transition from a Windows Server 2008 R2 home lab setup to a Linux setup to force myself to learn Linux. I thought I would start with something easy so I tried to make a DCHP and DNS server. The DHCP works great, but my DNS server doesn't seem to work correctly.

Here is the scenario... I want to have a home DNS name server called the4tress.net. I want to be able to access my machines (we will say server.the4tress.net and pc.the4tress.net for this) on my LAN and I want to be able to access my website (hosted by somebody else) from [www.the4tress.net](www.the4tress.net).

The problem is that my name server doesn't seem to be working at all. All of the machines on my network are able to resolve WAN DNS, but not LAN. I can get to google.com but not server.the4tress.net.

Here are some of my files that I set up using a tutorial I found online. Let me know if you need other files. My server is 192.168.1.10.

**/etc/bind/named.conf.local**
```
zone "the4tress.net" {
  type master;
  file "/etc/bind/zones/the4tress.net.db";
};

zone "1.168.192.in-addr.arpa" {
  type master;
  file "/etc/bind/zones/rev.1.168.192.in-addr.arpa";
};

```

**/etc/bind/named.conf.options**
```
options {
        directory "/var/cache/bind";

        // If there is a firewall between you and nameservers you want
        // to talk to, you may need to fix the firewall to allow multiple
        // ports to talk.  See http://www.kb.cert.org/vuls/id/800113

        // If your ISP provided one or more IP addresses for stable
        // nameservers, you probably want to use them as forwarders.
        // Uncomment the following block, and insert the addresses replacing
        // the all-0's placeholder.

        forwarders {
          8.8.8.8;
          8.8.4.4;
        };

        //========================================================================
        // If BIND logs error messages about the root key being expired,
        // you will need to update your keys.  See https://www.isc.org/bind-keys
        //========================================================================
        dnssec-validation auto;

        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
};

```

**/etc/bind/zones/the4tress.net.db**
```
$TTL 3D
@ IN SOA server.the4tress.net. admin.the4tress.net. (
  2007062001
  28800
  3600
  604800
  38400
);

the4tress.net.  IN      NS      server.the4tress.net.
server          IN      A       192.168.1.10
www             IN      A       74.220.219.109
ftp             IN      A       74.220.219.109
bedroom         IN      A       192.168.1.106
desktop         IN      A       192.168.1.108
downloads       IN      A       192.168.1.12
esther          IN      A       192.168.1.102
zm              IN      A       192.168.1.15

// the4tress.net.       IN      MX      10 mta.the4tress.net.

```

Also, can somebody tell me what those numbers represent in the brackets? 2007062001 and all that. I have seen different numbers in different tutorials but they all say, "DON'T CHANGE THIS!!!".

**/etc/bind/zones/rev.1.168.192.in-addr.arpa**
```
$TTL 3D
@       IN      SOA     server.the4tress.net. admin.the4tress.net. (
  2007062001
  28800
  604800
  604800
  86400
)

        IN      NS      server.the4tress.net.
10      IN      PTR     the4tress.net.

```

I have also seen some tutorials put a ; at the end of each number, or after the ). I have tried both ways and it didn't work for me.

**/etc/resolv.conf**
```
search the4tress.net.
nameserver[CODE]
``` 192.168.1.10
[/CODE]

I'm not sure if you need it, but here is my dhcp config. I removed all the commented stuff.
**/etc/dhcp/dhcpd.conf**
```
#
ddns-update-style none;

option domain-name "the4tress.net";
option domain-name-servers 192.168.1.10;

default-lease-time 600;
max-lease-time 7200;

authoritative;
log-facility local7;

subnet 192.168.1.0 netmask 255.255.255.0 {
  range 192.168.1.100 192.168.1.150;
  option routers 192.168.1.1;
  option subnet-mask 255.255.255.0;

  option broadcast-address 192.168.1.0;
  option domain-name-servers 192.168.1.10;
}

host Download-PC {
  hardware ethernet 00:0c:29:08:0a:20;
  fixed-address 192.168.1.12;
}

host MacBookPro {
  hardware ethernet 68:a8:6d:1f:cc:24;
  fixed-address 192.168.1.20;
}

host Downloads {
  hardware ethernet 00:0c:29:c6:3c:d8;
  fixed-address 192.168.1.13;
}

```

Thanks for any help! I really want to like Linux, but I'm having a hard time getting some momentum on this learning curve.

---

### Post by Doug S on 2012-08-04
I think your reverse zone file is O.K.
I would suggest something like this for your zone file:```
;
; BIND data file for the4trees.net
;
$TTL 3D
@ IN SOA the4tress.net. admin.the4tress.net. (
  2012080403     ; Serial
  28800              ; Refresh
  3600                ; Retry
  604800            ; Expire
  38400 )           ; Negative Cache TTL
                IN      A       74.220.219.109
;
@               IN      NS      server.the4tress.net.
server         IN      A       192.168.1.10
www          IN      A       74.220.219.109
ftp              IN      A       74.220.219.109
bedroom     IN      A       192.168.1.106
desktop       IN      A       192.168.1.108
downloads   IN      A       192.168.1.12
esther         IN      A       192.168.1.102
zm              IN      A       192.168.1.15
; the4tress.net.       IN      MX      10 mta.the4tress.net.
```
I have added comments saying what the numbers are. What I showed will have the two URL's [www.the4trees.net](www.the4trees.net) and the4trees.net resolve to the same address.
You need to increment the serial number any time you edit the zone files, otherwise they won't be re-parsed when you re-start bind. The example you gave seems to have been a YYYYMMDDSS type serial number, which many people use. SS is merely the serial number for that day, i.e. 00, 01, 02, 03 and on and on depending on how bad a day you are having.
One way to check your files is to use named-checkzone. For example:```
doug@doug-64:~/config/bind/temp3$ named-checkzone the4tress.net the4tress.net.db
zone the4tress.net/IN: loaded serial 2012080403
OK
doug@doug-64:~/config/bind/temp3$ 
```and```
doug@doug-64:~/config/bind/temp3$ named-checkzone 1.168.192.in-addr.arpa rev.1.168.192.in-addr.arpa
zone 1.168.192.in-addr.arpa/IN: loaded serial 2012080402
OK
doug@doug-64:~/config/bind/temp3$
```A good reference is the [ubuntu server guide - DNS section]("https://help.ubuntu.com/12.04/serverguide/dns.html"). (I gave the link to the 12.04 guide on purpose, as it contains some important updates).
The ";" just means the rest of the line is comment.
 
Hope this helps.

---

### Post by spazlon on 2012-08-04
Thanks for the help. The problem was that I was using the wrong comment delimiter. I was using // instead of ; and it was causing an error.

Thanks again for the help!

---

