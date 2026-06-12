---
title: "Help with BIND error"
date: 2010-12-11
forum: Networking &amp; Wireless
---

### Post by magneticstain on 2010-12-11
Hi, I'm trying to set up a DNS server using bind using [this]("http://ulyssesonline.com/2007/11/07/how-to-setup-a-dns-server-in-ubuntu/") tutorial. After setting up named.conf.local and named.conf.options, I get this error:

rndc: connect failed: 127.0.0.1#953: connection refused

Here is my named.conf.local file
```

//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

zone "magneticstain.doesntexist.org" {
        type master;
        file "/etc/bind/zones/magneticstain.doesntexist.org.db;
};

zone "0.168.192.in-addr.arpa" {
        type master;
        file "/etc/bind/zones/rev.0.168.192.in-addr.arpa";
};


```

and here is my named.conf.options file:
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

        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
};


```

Thank you for all your help.

---

