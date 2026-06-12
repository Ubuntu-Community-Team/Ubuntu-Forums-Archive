---
title: "setting up ubuntu server for wccp"
date: 2009-11-26
forum: Networking &amp; Wireless
---

### Post by bealzz on 2009-11-26
Plain and simple, wondering if anyone here is using a squid box (ubuntu) with their fortigate firewall. I've been trying to get it to work to no avail.
 
I've got my fortigate internal port and firewall policy setup with "set wccp enable" and the system wccp config setup to look for the cache server as follows;
 
```

config system wccp
    edit "0"
        set router-id 10.100.11.2
        set server-list 10.4.8.2 255.255.255.255
        set authentication enable

```
 
 
The linux side is where I'm having the most problems, I've got squid.conf setup correctly (I think) with the following options;
 
```

acl manager proto cache_object
acl localhost src 127.0.0.1/32
acl to_localhost dst 127.0.0.0/8
acl localnet src 10.0.0.0/8                                        
acl fortigate src 38.xxx.xxx.3/32 
 
acl SSL_ports port 443
acl Safe_ports port 80          # http
acl Safe_ports port 21          # ftp
acl Safe_ports port 443         # https
acl Safe_ports port 70          # gopher
acl Safe_ports port 210         # wais                
acl Safe_ports port 1025-65535  # unregistered ports             
acl Safe_ports port 280         # http-mgmt
acl Safe_ports port 488         # gss-http
acl Safe_ports port 591         # filemaker
acl Safe_ports port 777         # multiling http
acl CONNECT method CONNECT
 
http_access allow manager localhost
http_access deny manager
http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports
http_access allow localnet
http_access allow localhost
http_access allow fortigate
http_access deny all
 
icp_access deny all
htcp_access deny all
 
http_port 3128 transparent
 
hierarchy_stoplist cgi-bin ?
 
cache_dir ufs /var/spool/squid3 4096 16 256
maximum_object_size 8192 KB
 
access_log /var/log/squid3/access.log squid
cache_log /var/log/squid3/cache.log
cache_store_log /var/log/squid3/store.log
 
refresh_pattern ^ftp:           1440    20%     10080
refresh_pattern ^gopher:        1440    0%      1440
refresh_pattern (cgi-bin|\?)    0       0%      0
refresh_pattern .               0       20%     4320
 
wccp2_router 10.100.11.2
wccp2_forwarding_method 1
wccp2_return_method 1
wccp2_assignment_method 1
 
icp_port 3130
coredump_dir /var/spool/squid3

```
 
Now I'm trying to setup the tunnel on the squid server but it is not staying after a reboot. I'm imputting the commands, I think this is the part thats causing all my problems as the intructions from Fortigate were written awhile ago and probably do not reflect the changes that have been made to the command structure.
 
```

modprobe ip_gre # create gr tunnel
ip tunnel add wccp0 mode gre remote 10.100.11.2 local 10.4.8.2 dev eth0 # 10.100.11.2 is the internal fortigate, 10.4.8.2 is the cache
ip addr add 10.4.8.2/32 dev wccp0 # add squid ip to wccp0 interface
route add 38.xxx.xxx.3/32 dev wccp0 # route to send data out the external interface of the fortigate
iptables -t nat -F
iptables -t nat -A PREROUTING -i wccp0 -m tcp -p tcp -j REDIRECT --to-ports 3128

```
 
 
I've also changed under /etc/sysctl.conf an entry and added an entry;
 
```

# changed from =0 to =1
net.ipv4.ip_forward=1
# added
net.ipv4.conf.wccp0.rp_filter=0

```
 
Are the iptables and route add commands correct?
Is this beyond the scope of the guys here, would another forum be better? Am I delousional thinking that I could've gotten this working??  Thank you so much for reading.

---

