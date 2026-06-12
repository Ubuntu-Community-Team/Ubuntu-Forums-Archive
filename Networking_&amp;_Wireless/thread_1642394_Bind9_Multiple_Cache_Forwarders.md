---
title: "Bind9 Multiple Cache Forwarders"
date: 2010-12-10
forum: Networking &amp; Wireless
---

### Post by CyberAxe on 2010-12-10
I want to setup bind9 so that IPs from one range will use the Google DNS Servers and IPs from another range will work from Opens DNS but am unable to get it working here are my configs.

anyone that can help me please?

```

  GNU nano 2.2.4                                    File: /etc/bind/named.conf

// This is the primary configuration file for the BIND DNS server named.
//
// Please read /usr/share/doc/bind9/README.Debian.gz for information on the
// structure of BIND configuration files in Debian, *BEFORE* you customize
// this configuration file.
//
// If you are just adding zones, please do that in /etc/bind/named.conf.local

acl "trainers" {
        192.168.0.0/24;
};

acl "devices" {
        192.168.1.0/24;
};

acl "trainees" {
        192.168.2.0/23;
};

include "/etc/bind/named.conf.options";
include "/etc/bind/named.conf.local";
include "/etc/bind/named.conf.default-zones";

view "trainees" {
  match-clients { trainers; trainees; any; };
  forwarders {
    208.67.222.222;
    208.67.220.220;
  };
};


view "trainers" {
  match-clients { devices; any; };
  forwarders {
    8.8.8.8;
    8.8.5.5;
  };
};

```

```

  GNU nano 2.2.4                                  File: /etc/bind/named.conf.local

//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

view "local" {
  zone "local" {
    type master;
    file "/etc/bind/db.local";

    forwarders {
      192.168.0.1;
    };
  };
};

```
```

  GNU nano 2.2.4                                  File: /etc/bind/named.conf.options

options {
        directory "/var/cache/bind";

        // If there is a firewall between you and nameservers you want
        // to talk to, you may need to fix the firewall to allow multiple
        // ports to talk.  See http://www.kb.cert.org/vuls/id/800113

        // If your ISP provided one or more IP addresses for stable
        // nameservers, you probably want to use them as forwarders.
        // Uncomment the following block, and insert the addresses replacing
        // the all-0's placeholder.

        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
};

```
```

  GNU nano 2.2.4                                File: /etc/bind/named.conf.default-zones

// prime the server with knowledge of the root servers
view "master" {
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
};

```

Thanks

---

### Post by CyberAxe on 2010-12-12
Echo

---

