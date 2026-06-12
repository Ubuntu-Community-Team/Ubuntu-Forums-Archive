---
title: "BIND issues"
date: 2009-04-21
forum: Networking &amp; Wireless
---

### Post by jebathan on 2009-04-21
I have searched the forums and the web trying to find ways to properly configure BIND. After several tries I have it working to a certain point, there is just one last problem I am having.

If I run the following:

```
jon@cybersec3:/etc/bind$ dig localhost

; <<>> DiG 9.5.0-P2 <<>> localhost
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 20191
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 1

;; QUESTION SECTION:
;localhost.                     IN      A

;; ANSWER SECTION:
localhost.              604800  IN      A       127.0.0.1

;; AUTHORITY SECTION:
localhost.              604800  IN      NS      localhost.

;; ADDITIONAL SECTION:
localhost.              604800  IN      AAAA    ::1

;; Query time: 10 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Tue Apr 21 16:54:57 2009
;; MSG SIZE  rcvd: 85

jon@cybersec3:/etc/bind$ dig @localhost

; <<>> DiG 9.5.0-P2 <<>> @localhost
; (1 server found)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 14029
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;.                              IN      NS

;; Query time: 204 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Tue Apr 21 16:54:59 2009
;; MSG SIZE  rcvd: 17

```

Notice how dig @localhost fails, but dig localhost does not. I have no idea why it is doing this. I also have zones for my domain, but I get the same kind of results. Maybe I am misunderstanding something about dig, but I feel like they should both be returning results. Any help will be greatly appreciated. 

Thanks.

Here are some of my other named files for help.

my named.conf looks like this:

```
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
};

include "/etc/bind/named.conf.local";
```

and named.conf.options:

```
options {
        directory "/var/cache/bind";
        pid-file "/var/run/bind/run/named.pid";

        // If there is a firewall between you and nameservers you want
        // to talk to, you might need to uncomment the query-source
        // directive below.  Previous versions of BIND always asked
        // questions using port 53, but BIND 8.1 and later use an unprivileged
        // port by default.

        //      query-source address * port 53;

        // If your ISP provided one or more IP addresses for stable
        // nameservers, you probably want to use them as forwarders.
        // Uncomment the following block, and insert the addresses replacing
        // the all-0's placeholder.

        // forwarders {
        //      10.0.0.1;
        // };

        version "DNS Server";
        listen-on { 127.0.0.1; 10.0.200.15; };
        allow-query { any; };
        allow-transfer { 10.0.0.0/16; 10.0.200.0/24; 127.0.0.1; };
        allow-recursion { 10.0.0.0/16; 10.0.200.0/24; 127.0.0.1; };
        recursion yes;
//      auth-nxdomain no;    # conform to RFC1035
        // listen-on-v6 { any; };
};
```

All of this is running on a private network with no access to the internet.

---

