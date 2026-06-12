---
title: "DNS is not working"
date: 2010-03-02
forum: Networking &amp; Wireless
---

### Post by jbredariol on 2010-03-02
I've installed squirrelmail and bind on my ubuntu 9. the squirrelmail is working only with the ip address (192.168.0.254/webmail) on the network, and i want it to work like sbamail.com/squirrelmail. Bellow are my bind files configurations.
---------------------------------------
/etc/resolv.conf
nameserver 192.168.0.254
---------------------------------------
/etc/bind/named.conf.local
#File: /etc/bind/named.conf.local
options {
     listen-on port 53 { any; };
};

zone "sbamail.com" {
  type master;
  notify no;
  allow-query { any; };
  file "/etc/bind/db.sbamail.com";
};

zone "0.168.192.in-addr.arpa" {
  type master;
  notify no;
  file "/etc/bind/db.192";
};
--------------------------------------------------------
/etc/bind/db.sbamail.com
$TTL  604800
@ IN SOA ns254.sbamail.com. root.sbamail.com. (
 2006020201;Serial
  604800;Refresh
  86400;Retry
  2419200;Expire
  604800);Negative Cache TTL
;
@ IN NS ns254
    IN MX 254 mail
    IN A 192.168.0.254
nsl IN A 192.168.0.254
mail IN A 192.168.0.254

------------------------------------------
/etc/bind/db.192
$TTL  604800
sbamail.com IN SOA ns254.sbamail.com. root.sbamail.com. (
 1;Serial
  604800;Refresh
  86400;Retry
  2419200;Expire
  604800);Negative Cache TTL
;
sbamail.com IN NS ns254
254   IN PTR ns.sbamail.com

    IN A 192.168.0.254
nsl IN A 192.168.0.254
mail IN A 192.168.0.254

---

