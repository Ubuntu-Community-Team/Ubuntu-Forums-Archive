---
title: "Squid3 &amp; SquidGuard"
date: 2010-09-29
forum: Networking &amp; Wireless
---

### Post by LordHexen on 2010-09-29
Hi,



Since few days, i'am trying to configure Squid3 et SquidGuard on ubuntu Server 10.04 for a school.


I'm new in linux, before i post this thread, I searched in the french forum and www.
I found nothing to help me to resolve this issue. 
 




You can see below to configuration file from Squid3. 

Which is stored in /etc/squid3/

```


acl manager proto cache_object acl localhost src 127.0.0.1/32 acl to_localhost dst 127.0.0.0/8 0.0.0.0/32 acl SSL_ports port 443 acl Safe_ports port 80          # http acl Safe_ports port 21          # ftp acl Safe_ports port 443         # https acl Safe_ports port 70          # gopher acl Safe_ports port 210         # wais acl Safe_ports port 1025-65535  # unregistered ports acl Safe_ports port 280         # http-mgmt acl Safe_ports port 488         # gss-http acl Safe_ports port 591         # filemaker acl Safe_ports port 777         # multiling http acl CONNECT method CONNECT acl LocalNet src 192.168.0.0/24 http_access allow manager localhost http_access deny manager http_access deny !Safe_ports http_access deny CONNECT !SSL_ports http_access allow localhost http_access allow LocalNet http_access deny all icp_access deny all htcp_access deny all http_port 3128 hierarchy_stoplist cgi-bin ? access_log /var/log/squid3/access.log squid refresh_pattern ^ftp:           1440    20%     10080 refresh_pattern ^gopher:        1440    0%      1440 refresh_pattern (cgi-bin|\?)    0       0%      0 refresh_pattern .               0       20%     4320 icp_port 3130 coredump_dir /var/spool/squid3 url_rewrite_program /usr/bin/squidGuard -c /etc/squid/squidGuard.conf url_rewrite_children 5

```

And the configuration file from Squiguard, which is stored in /etc/squid

```


# CONFIG FILE FOR SQUIDGUARD dbhome /var/lib/squidguard/db/blacklists logdir /var/log/squid  # SOURCE ADDRESSES:  src admin {         ip              192.168.0.30  } src bar-clients {         ip              192.168.0.0/24 }   # DESTINATION CLASSES:  dest good { }  dest local { }  dest adult {         domainlist      adult/domains         urllist         adult/urls         expressionlist  adult/expressions }  acl {         admin {                 pass     any         }         bar-clients {                 pass !adult any         redirect        http://127.0.0.1/cgi-bin/squidGuard.cgi?clientaddr=%a+clientname=%n+clientident=%i+srcclass=%s+targetclass=%t+url=%u          } }

```The IP server is 192.168.0.15 and the gateway 192.168.0.254
When i'm trying to connect to www from a pc, nothing is autorized.

I've got this log for Squid :

```


oot@CERBERE:/etc/squid# sudo tail /var/log/syslog Sep 25 15:17:04 CERBERE squid[1801]: Squid Parent: child process 1824 started Sep 25 15:17:04 CERBERE (squid): The redirector helpers are crashing too rapidly, need help! Sep 25 15:17:04 CERBERE squid[1801]: Squid Parent: child process 1824 exited with status 1 Sep 25 15:17:07 CERBERE squid[1801]: Squid Parent: child process 1832 started Sep 25 15:17:08 CERBERE (squid): The redirector helpers are crashing too rapidly, need help! Sep 25 15:17:08 CERBERE squid[1801]: Squid Parent: child process 1832 exited with status 1 Sep 25 15:17:11 CERBERE squid[1801]: Squid Parent: child process 1840 started Sep 25 15:17:11 CERBERE (squid): The redirector helpers are crashing too rapidly, need help! Sep 25 15:17:11 CERBERE squid[1801]: Squid Parent: child process 1840 exited with status 1 Sep 25 15:17:11 CERBERE squid[1801]: Exiting due to repeated, frequent failures

```And this for SquidGuard

```

2010-09-25 15:29:00 [1909] loading dbfile /var/lib/squidguard/db/blacklists/adult/domains.db 2010-09-25 15:29:00 [1909] init urllist /var/lib/squidguard/db/blacklists/adult/urls 2010-09-25 15:29:00 [1909] loading dbfile /var/lib/squidguard/db/blacklists/adult/urls.db 2010-09-25 15:29:00 [1909] init expressionlist /var/lib/squidguard/db/blacklists/adult/expressions 2010-09-25 15:29:00 [1909] (squidGuard): default acl not defined in configfile  /etc/squid/squidGuard.conf


```Could please someone help to resolve this issue ? :(

---

### Post by LordHexen on 2010-10-09
Hi,

The subject is closed, it works.:P

The file squidGuard.conf contained some mistake (typing error).

And there was some permissions which was not applyed in the directory of blacklist base.
chown -R proxy:proxy blacklists

Bye

---

