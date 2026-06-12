---
title: "Wireless Community BBS?"
date: 2010-04-07
forum: Networking &amp; Wireless
---

### Post by imcookie on 2010-04-07
Hi all,

I'm looking at setting up a community wireless bulletinboard style server. basically i need people to be able to connect to the server and get redirected to the community website.
The client will not be able to access the internet through the server and entering an alternative web address will re-direct them to mine. 

What i have so far:
apache2.2 with www folder and the generic "It work's" message

gadmin-dhcpd to set up dhcpd.conf
```

ddns-update-style ad-hoc;
ddns-updates on;
allow client-updates;
one-lease-per-client true;
allow bootp;
option T150 code 150 = string;

subnet 192.168.1.0 netmask 255.255.255.0 {
    interface at0;
    range 192.168.1.2 192.168.1.12;
    default-lease-time 600;
    max-lease-time 7200;
    option domain-name "comm-bbs.net";
    option subnet-mask 255.255.255.0;
    option broadcast-address 192.168.1.255;
    option routers 192.168.1.254;
    option domain-name-servers 192.168.1.1;
    option ntp-servers 192.168.1.1;
    option netbios-name-servers 192.168.1.1;
}


```

Using airbase-ng to create at0 interface (my wlan card doesn't support master mode).

---
I need help routing the client to the web page once they connect and open their browsers.  Any help would be appreciated

regards

---

### Post by imcookie on 2010-04-07
Maybe this will help me!

```
https://help.ubuntu.com/community/WifiDocs/WirelessBroadcastSystem
```

more help would be appreciated though

---

