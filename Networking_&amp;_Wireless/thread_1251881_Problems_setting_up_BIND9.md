---
title: "Problems setting up BIND9"
date: 2009-08-28
forum: Networking &amp; Wireless
---

### Post by jon64 on 2009-08-28
Yesterday I purchased corruptedmedias.com(a GoDaddy domain name) and I wanted to use my ubuntu machine to be used as a legitimate DNS/NameServer(I also want my DNS/NameServer to be accessed across the internet. I have my router port forwarding port 53). So I read up a bunch of how-to's on BIND9 and came across [http://www.ubuntugeek.com/dns-server-setup-using-bind-in-ubuntu.html](http://www.ubuntugeek.com/dns-server-setup-using-bind-in-ubuntu.html) the how-to is a bit old(2007) but it gave me a understanding on how BIND9 works and also DNS.

Here are my configurations.

**-Here is my up-to-date "_working_" setup**(updated August 30 2009)

**named.conf**
```
acl "trusted" { 127.0.0.1/32;MY_INSIDE_IP/32; };

#--------------------------------------------------#

options {
    directory "/var/cache/bind";
    recursion yes;allow-recursion {trusted;};
    listen-on {MY_INSIDE_IP;};
    version    "{secured}";
    auth-nxdomain no;
    
    // If there is a firewall between you and nameservers you want
        // to talk to, you may need to fix the firewall to allow multiple
        // ports to talk.  See http://www.kb.cert.org/vuls/id/800113

        // If your ISP provided one or more IP addresses for stable
        // nameservers, you probably want to use them as forwarders.
        // Uncomment the following block, and insert the addresses replacing
        // the all-0's placeholder.

        forwarders { 68.87.69.150;68.87.85.102;68.87.66.204; }; // MY ISP DNS SERVERS 
};
#--------------------------------------------------#
// This is the primary configuration file for the BIND DNS server named.
//
// Please read /usr/share/doc/bind9/README.Debian.gz for information on the 
// structure of BIND configuration files in Debian, *BEFORE* you customize 
// this configuration file.
//
// If you are just adding zones, please do that in /etc/bind/named.conf.local

include "/etc/bind/named.conf.options";

// prime the server with knowledge of the root servers
zone "." {
    type hint;
    file "/etc/bind/db.root";
};

// be authoritative for the localhost forward and reverse zones, and for
// broadcast zones as per RFC 1912

zone "localhost" {
    type master;
    file "/etc/bind/db.local";
};

zone "127.in-addr.arpa" {
    type master;
    file "/etc/bind/db.127";
};

zone "0.in-addr.arpa" {
    type master;
    file "/etc/bind/db.0";
};

zone "255.in-addr.arpa" {
    type master;
    file "/etc/bind/db.255";
#------------------------------------------------------------#
#My Zone#
};

zone "ns1.corruptedmedias.com" {
        type master;
        file "/etc/bind/zones/ns1.corruptedmedias.com.db";
};
#------------------------------------------------------------#
#Reverse Zone#
zone "0.168.192.in-addr.arpa" {
       type master;
       file "/etc/bind/zones/rev.0.168.192.in-addr.arpa";
};
#------------------------------------------------------------#

include "/etc/bind/named.conf.local";

# Use with the following in named.conf, adjusting the allow list as needed:
 key "rndc-key" {
     algorithm hmac-md5;
     secret "MY_SECRECT_KEY";
};

controls {
     inet 127.0.0.1 port 953
         allow { 127.0.0.1; } keys { "rndc-key"; };
};
# End of named.conf
```[B]

named.conf.local[/B]
```
//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

# This is the zone definition. replace example.com with your domain name

#zone "ns1.corruptedmedias.com" {
#    type master;
#    file "/etc/bind/zones/ns1.corruptedmedias.com.db";
#};

# This is the zone definition for reverse DNS. replace 0.168.192 with your network address in reverse notation – e.g my network address is 192.168.0

#zone "0.168.192.in-addr.arpa" {
#    type master;
#    file "/etc/bind/zones/rev.0.168.192.in-addr.arpa";
#};

```

**named.conf.options**
```
#options {
    #directory "/var/cache/bind";

    // If there is a firewall between you and nameservers you want
    // to talk to, you may need to fix the firewall to allow multiple
    // ports to talk.  See http://www.kb.cert.org/vuls/id/800113

    // If your ISP provided one or more IP addresses for stable 
    // nameservers, you probably want to use them as forwarders.  
    // Uncomment the following block, and insert the addresses replacing 
    // the all-0's placeholder.

    // forwarders {
    //     68.87.64.204;68.87.76.228;68.87.66.204; // MY ISP DNS SERVERS
    // };

    #auth-nxdomain no;    # conform to RFC1035
    #listen-on-v6 { any; };
#};
```[B]

zones(ns1.corruptedmedias.com.db)[/B]
```
$TTL 38400
ns1.corruptedmedias.com. IN SOA corruptedmedias.com. admin.corruptedmedias.com. (
    2007031001 ; serial number
    28800 ; refresh
    3600 ; update retry
    604800 ; expires
    38400 ; minimum
    )


ns1.corruptedmedias.com. IN NS corruptedmedias.com.
            IN A MY_INSIDE_IP

www            IN A MY_INSIDE_IP
ns1            IN A MY_INSIDE_IP
```

**reverse(rev.0.168.192.in-addr.arpa)**
```
$TTL 86400

@ IN SOA corruptedmedias.com. admin.corruptedmedias.com. (
2007031001;
28800;
604800;
604800;
86400
)

@ IN NS corruptedmedias.com.
IN NS ns1.corruptedmedias.com.
104 IN PTR corruptedmedias.com.
```[B]

/var/log/daemon.log[/B]
```
Aug 30 09:49:36 ubuntu904 named[26809]: starting BIND 9.5.1-P2 -u bind
Aug 30 09:49:36 ubuntu904 named[26809]: found 2 CPUs, using 2 worker threads
Aug 30 09:49:36 ubuntu904 named[26809]: using up to 4096 sockets
Aug 30 09:49:36 ubuntu904 named[26809]: loading configuration from '/etc/bind/named.conf'
Aug 30 09:49:36 ubuntu904 named[26809]: max open files (1024) is smaller than max sockets (4096)
Aug 30 09:49:36 ubuntu904 named[26809]: using default UDP/IPv4 port range: [1024, 65535]
Aug 30 09:49:36 ubuntu904 named[26809]: using default UDP/IPv6 port range: [1024, 65535]
Aug 30 09:49:36 ubuntu904 named[26809]: listening on IPv4 interface eth0, 192.168.0.104#53
Aug 30 09:49:36 ubuntu904 named[26809]: automatic empty zone: 254.169.IN-ADDR.ARPA
Aug 30 09:49:36 ubuntu904 named[26809]: automatic empty zone: 2.0.192.IN-ADDR.ARPA
Aug 30 09:49:36 ubuntu904 named[26809]: automatic empty zone: 255.255.255.255.IN-ADDR.ARPA
Aug 30 09:49:36 ubuntu904 named[26809]: automatic empty zone: 0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
Aug 30 09:49:36 ubuntu904 named[26809]: automatic empty zone: 1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
Aug 30 09:49:36 ubuntu904 named[26809]: automatic empty zone: D.F.IP6.ARPA
Aug 30 09:49:36 ubuntu904 named[26809]: automatic empty zone: 8.E.F.IP6.ARPA
Aug 30 09:49:36 ubuntu904 named[26809]: automatic empty zone: 9.E.F.IP6.ARPA
Aug 30 09:49:36 ubuntu904 named[26809]: automatic empty zone: A.E.F.IP6.ARPA
Aug 30 09:49:36 ubuntu904 named[26809]: automatic empty zone: B.E.F.IP6.ARPA
Aug 30 09:49:36 ubuntu904 named[26809]: command channel listening on 127.0.0.1#953
Aug 30 09:49:36 ubuntu904 named[26809]: zone 0.in-addr.arpa/IN: loaded serial 1
Aug 30 09:49:36 ubuntu904 named[26809]: zone 127.in-addr.arpa/IN: loaded serial 1
Aug 30 09:49:36 ubuntu904 named[26809]: zone 0.168.192.in-addr.arpa/IN: loaded serial 2007031001
Aug 30 09:49:36 ubuntu904 named[26809]: zone 255.in-addr.arpa/IN: loaded serial 1
Aug 30 09:49:36 ubuntu904 named[26809]: zone ns1.corruptedmedias.com/IN: loaded serial 2007031001
Aug 30 09:49:36 ubuntu904 named[26809]: zone localhost/IN: loaded serial 2
Aug 30 09:49:36 ubuntu904 named[26809]: running
```

**resolv.conf**
```
# Generated by NetworkManager
domain corruptedmedias.com
search corruptedmedias.com
nameserver MY_INSIDE_IP
nameserver 68.87.69.150 // MY ISP DNS
```

**dig ns1.corruptedmedias.com**
```
; <<>> DiG 9.5.1-P2 <<>> corruptedmedias.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 16397
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 13, ADDITIONAL: 13

;; QUESTION SECTION:
;corruptedmedias.com.        IN    A

;; ANSWER SECTION:
corruptedmedias.com.    3600    IN    A    MY_OUTSIDE_IP

;; AUTHORITY SECTION:
.            515648    IN    NS    C.ROOT-SERVERS.NET.
.            515648    IN    NS    L.ROOT-SERVERS.NET.
.            515648    IN    NS    D.ROOT-SERVERS.NET.
.            515648    IN    NS    A.ROOT-SERVERS.NET.
.            515648    IN    NS    E.ROOT-SERVERS.NET.
.            515648    IN    NS    K.ROOT-SERVERS.NET.
.            515648    IN    NS    B.ROOT-SERVERS.NET.
.            515648    IN    NS    J.ROOT-SERVERS.NET.
.            515648    IN    NS    G.ROOT-SERVERS.NET.
.            515648    IN    NS    I.ROOT-SERVERS.NET.
.            515648    IN    NS    H.ROOT-SERVERS.NET.
.            515648    IN    NS    M.ROOT-SERVERS.NET.
.            515648    IN    NS    F.ROOT-SERVERS.NET.

;; ADDITIONAL SECTION:
A.ROOT-SERVERS.NET.    602048    IN    A    198.41.0.4
A.ROOT-SERVERS.NET.    602050    IN    AAAA    2001:503:ba3e::2:30
B.ROOT-SERVERS.NET.    602230    IN    A    192.228.79.201
C.ROOT-SERVERS.NET.    602049    IN    A    192.33.4.12
D.ROOT-SERVERS.NET.    602297    IN    A    128.8.10.90
E.ROOT-SERVERS.NET.    602078    IN    A    192.203.230.10
F.ROOT-SERVERS.NET.    602050    IN    A    192.5.5.241
F.ROOT-SERVERS.NET.    602053    IN    AAAA    2001:500:2f::f
G.ROOT-SERVERS.NET.    602049    IN    A    192.112.36.4
H.ROOT-SERVERS.NET.    602084    IN    A    128.63.2.53
H.ROOT-SERVERS.NET.    602099    IN    AAAA    2001:500:1::803f:235
I.ROOT-SERVERS.NET.    602282    IN    A    192.36.148.17
J.ROOT-SERVERS.NET.    602047    IN    A    192.58.128.30

;; Query time: 132 msec
;; SERVER: MY_INSIDE_IP#53(MY_INSIDE_IP)
;; WHEN: Sun Aug 30 09:51:54 2009
;; MSG SIZE  rcvd: 508
```[B]

nslookup ns1.corruptedmedias.com[/B]
```
Server:        MY_INSIDE_IP
Address:    MY_INSIDE_IP#53

Non-authoritative answer:
Name:    corruptedmedias.com
Address: MY_OUTSIDE_IP
```cheers! :popcorn:

---

### Post by jon64 on 2009-08-29
If I could get some help I'd appreciate it. Plus I know I'm close, I just don't know exactly where my problem is! :(

---

### Post by jon64 on 2009-08-30
Eureka! After 2 days(4 days total) of trying to find a fix for my problem I finally came upon a solution! I've successfully configured my bind9 to load without any error's what so ever! I'll post my current setup conf's for the people that are looking for help in setting up bind9(I'm thinking on making a HowTO soon :P)

Cheers!:popcorn::P

---

