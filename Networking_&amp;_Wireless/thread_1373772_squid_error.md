---
title: "squid error"
date: 2010-01-06
forum: Networking &amp; Wireless
---

### Post by blackcloud on 2010-01-06
my squid show like this when i try create swap directory

```
root@mhku:/etc/squid# squid -f /etc/squid/squid.conf*-z
FATAL: Unable to open configuration file: /etc/squid/squid.conf*-z: (2) No such file or directory
Squid Cache (Version 2.7.STABLE3): Terminated abnormally.
CPU Usage: 0.010 seconds = 0.000 user + 0.010 sys
Maximum Resident Size: 0 KB
Page faults with phy
```

and here my squid configurartion 
```
#==================================$ 
#  Proxy Server Versi 2.7.Stable3 
#  by admin
#==================================$
#################################################################
# Port 
#################################################################
http_port 3128 transparent
icp_port 3130
prefer_direct off
 
#########################################################
# Cache & Object 
########################################################## 
cache_mem 8 MB 
cache_swap_low 98 
cache_swap_high 99 
max_filedesc 8192 
maximum_object_size 1024 MB 
minimum_object_size 0 KB 
maximum_object_size_in_memory 4 bytes 
ipcache_size 4096 
ipcache_low 98 
ipcache_high 99 
fqdncache_size 4096 
 
cache_replacement_policy heap LFUDA 
memory_replacement_policy heap GDSF 

#################################################################
# cache_dir <type> <Directory-Name> <Space in Mbytes> <Level1> <Level2> <options> 
 
cache_dir aufs /home/proxy1 9000 32 128 
cache_dir aufs /home/proxy2 9000 32 128 
cache_dir aufs /home/proxy3 9000 32 128 
 
cache_access_log /var/log/squid/access.log 
cache_log /var/log/squid/cache.log 
cache_store_log none 
pid_filename /var/run/squid.pid 
cache_swap_log /var/log/squid/swap.state 
 
dns_nameservers /etc/resolv.conf 
 
emulate_httpd_log off 
hosts_file /etc/hosts 
half_closed_clients off 
negative_ttl 1 minutes 
 
 
################################################################# 
# Rules: Safe Port 
#################################################################
acl all src 0.0.0.0/0.0.0.0 
acl manager proto cache_object 
acl localhost src 127.0.0.1/255.255.255.255 
acl to_localhost dst 127.0.0.0/8 
 
acl SSL_ports port 443 563 873     # https snews rsync 
acl Safe_ports port 80      # http 
acl Safe_ports port 20 21      # ftp 
acl Safe_ports port 70      # gopher 
acl Safe_ports port 210      # wais 
acl Safe_ports port 1025-65535     # unregistered ports 
acl Safe_ports port 631      # cups 
acl Safe_ports port 10000      # webmin 
acl Safe_ports port 901      # SWAT 
acl Safe_ports port 280      # http-mgmt 
acl Safe_ports port 488      # gss-http 
acl Safe_ports port 591      # filemaker 
acl Safe_ports port 777      # multiling http 
acl Safe_ports port 873      # rsync 
acl Safe_ports port 110      # POP3 
acl Safe_ports port 25      # SMTP 
acl Safe_ports port 2095 2096     # webmail from cpanel 
acl Safe_ports port 2082 2083     # cpanel 
 
acl purge method PURGE 
acl CONNECT method CONNECT 
 
http_access allow manager localhost 
http_access deny manager 
http_access allow purge localhost  
http_access deny purge 
http_access deny !Safe_ports !SSL_ports 
http_access deny CONNECT !SSL_ports !Safe_ports 

 
 
################################################################# 
# Refresh Pattern 
#################################################################
refresh_pattern ^ftp:           1440    20%     10080 
refresh_pattern ^gopher:        1440    0%      1440 
 
refresh_pattern -i \.(gif|png|jpg|jpeg|ico)$ 10080 90% 43200 override-expire ignore-no-cache ignore-private 
refresh_pattern -i \.(iso|avi|wav|mp3|mp4|mpeg|mpg|swf|flv|x-flv)$ 43200 90% 432000 override-expire ignore-no-cache ignore-private 
refresh_pattern -i \.(deb|rpm|exe|ram|bin|pdf|ppt|doc|tiff)$ 10080 90% 43200 override-expire ignore-no-cache ignore-private 
refresh_pattern -i \.(zip|gz|arj|lha|lzh|tar|tgz|cab|rar)$ 10080 95% 43200 override-expire ignore-no-cache ignore-private 
refresh_pattern -i \.(html|htm|css|js|php|asp|aspx|cgi) 1440 40% 40320  
refresh_pattern .               0       20%     4320 
 
 
################################################################# 
# HAVP + Clamav 
#################################################################
cache_peer 127.0.0.1 parent 8080 0 no-query no-digest no-netdb-exchange default 
 
 
################################################################# 
# HIERARCHY (BYPASS CGI) 
#################################################################
#hierarchy_stoplist cgi-bin ? .js .jsp 
#acl QUERY urlpath_regex cgi-bin \? .js .jsp 
#no_cache deny QUERY 
 
 
################################################################# 
# SNMP 
#################################################################
snmp_port 3401 
acl snmpsquid snmp_community public 
snmp_access allow snmpsquid localhost 
snmp_access deny all 
 
 
################################################################# 
# ALLOWED ACCESS 
#################################################################
acl mhku src 192.168.0.0/24  ## Sesuaikan 
http_access allow mhku
http_access allow localhost 
http_access deny all 
http_reply_access allow all 
icp_access allow mhku
icp_access allow localhost 
icp_access deny all 
always_direct deny all 
 
 
################################################################# 
# Cache CGI & Administrative 
#################################################################
cache_mgr admin@mhku.net
cachemgr_passwd 123 all 
visible_hostname mhku.id
cache_effective_user proxy 
cache_effective_group proxy 
coredump_dir /var/spool/squid 
shutdown_lifetime 10 seconds 
logfile_rotate 14
```

---

### Post by puppywhacker on 2010-01-06
you have to add a space in front of the -z. Squid tries to find a file named something something-z ... while the -z is only an option, and options need to be seperated by a space.

```
/etc/squid/squid.conf*-z
```

---

### Post by blackcloud on 2010-01-08
thanks i forget add space :).

---

