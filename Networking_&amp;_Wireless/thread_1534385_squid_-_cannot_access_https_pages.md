---
title: "squid - cannot access https pages"
date: 2010-07-19
forum: Networking &amp; Wireless
---

### Post by Axrst on 2010-07-19
Hello.

I'm running a squid proxy in my ubuntu server, and I must have mess it up with the squid configuration. Users, cannot, access https pages. Can you tell me what to change in my squid.conf, so, to fix this?

Here is my squid.conf (witch is a friends conf, that i have change for my needs...)

```
http_port 8888
#http_port 3128
icp_port 3130
acl QUERY urlpath_regex cgi-bin \?

#httpd_accel_host virtual
#httpd_accel_port 80
#httpd_accel_with_proxy on
#httpd_accel_uses_host_header on

no_cache deny QUERY
cache_mem 1024 MB
cache_swap_low 95
cache_swap_high 98
minimum_object_size 0 KB
maximum_object_size 20480 KB
maximum_object_size_in_memory 1024 KB
ipcache_size 10240
fqdncache_size 10240
cache_dir diskd /var/spool/squid 20000 16 256
cache_access_log /var/log/squid/access.log
cache_log /var/log/squid/cache.log
cache_store_log /var/log/squid/store.log
dns_nameservers 208.67.222.222 208.67.220.220 10.224.3.35 195.170.0.1
redirect_rewrites_host_header off
acl public snmp_community public
acl wana_proxy src 10.224.6.30/255.255.255.255
#acl localnet src 192.168.0.0/255.255.255.0
#acl localnet src 10.148.0.0/255.255.0.0
acl localnet src 10.224.0.0/255.255.0.0
acl localhost src 127.0.0.1/255.255.255.255
#acl SSL_ports port 443          # https
acl SSL_ports port 563          # snews
acl SSL_ports port 873          # rsync
acl Safe_ports port 80          # http
acl Safe_ports port 81          # http
acl Safe_ports port 84          # http2
acl Safe_ports port 21          # ftp
acl Safe_ports port 443         # https
acl Safe_ports port 70          # gopher
acl Safe_ports port 210         # wais
acl Safe_ports port 1025-65535  # unregistered ports
acl Safe_ports port 280         # http-mgmt
acl Safe_ports port 488         # gss-http
acl Safe_ports port 591         # filemaker
acl Safe_ports port 777         # multiling http
acl Safe_ports port 631         # cups
acl Safe_ports port 873         # rsync
acl Safe_ports port 901         # SWAT
acl purge method PURGE
acl CONNECT method CONNECT
acl all src 0.0.0.0/0.0.0.0
#http_access allow manager localhost
#http_access deny manager
# Only allow purge requests from localhost
http_access allow purge localhost
http_access deny purge
http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports
http_access allow localhost
http_access allow localnet
http_access deny all
##sibling me kalamata
#icp_access  allow  kalamata_proxy
#icp_access  allow  localnet
#icp_access  deny  all
snmp_port 3401
snmp_access allow public localhost
snmp_access allow public localnet
snmp_access deny all
quick_abort_min 16 KB 
quick_abort_max 16 KB 
quick_abort_pct 95 
cache_mgr axrst@xxxxxx.gr
cache_effective_user proxy
cache_effective_group proxy
visible_hostname wana.gr_FUTUREKIDS
log_icp_queries off
cachemgr_passwd disable all
buffered_logs on
memory_pools on
memory_pools_limit 128 MB
#offline_mode on
refresh_pattern ^ftp:         1440    20%     10080
refresh_pattern ^gopher:      1440    0%      1440
refresh_pattern .              360    40%     10080 
#refresh_pattern .              360    40%     10080    reload-into-ims  
#refresh_pattern .              0    20%     10080  
negative_ttl 1 second
negative_dns_ttl 1 second
positive_dns_ttl 10 second
acl only5Musers src 10.224.0.0/255.255.0.0
        delay_pools 1
        delay_class 1 3
        delay_access 1 allow only5Musers
        delay_access 1 deny all
        delay_parameters 1 1200000/1200000 -1/-1 800000/1200000

```

---

### Post by madeulook967 on 2010-09-22
Did you manage to resolve this?  I have the very same problem.  :(

---

### Post by nutznboltz on 2010-11-05
From [http://ubuntuforums.org/showpost.php?p=2641035&postcount=3](http://ubuntuforums.org/showpost.php?p=2641035&postcount=3)

> "No, unfortunately. The OpenSSL and Squid licences [sic] are not compatible hence cannot be distributed as a compiled package." 

---

### Post by theHAAG on 2013-04-15
solution: never_direct allow all

---

### Post by gorkypah on 2013-04-16
...

---

