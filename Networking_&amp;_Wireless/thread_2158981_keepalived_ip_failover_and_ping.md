---
title: "keepalived ip failover and ping"
date: 2013-07-01
forum: Networking &amp; Wireless
---

### Post by nhybgtvfr on 2013-07-01
Hi, i am trying to configure two Ubuntu servers as failover load-balancers using haproxy and keepalived, I've not done anything with haproxy yet, concentrating on the ip-failover configuration in keepalived. i have what appears to me to be the right configuration, with one external interface (also has 2 vlan interfaces), and 3 internal interfaces, each physical and virtual interface has it's own floating ip on it's own subnet. (everything is currently configured with private ip addresses during testing). when disconnecting an Ethernet cable, or rebooting the keepalived master server to test failover, all the ip addresses are failed over as expected. i can ping all the floating ip's without issues. there may be one 'request timed out' at worst. however, i'm also trying to ping to a server behind the load-balancer, this gets interrupted at the time of failover, and will not work until the master keepalived is back up and running and has taken back the floating ip.  is this normal behaviour until haproxy is configured? i was expecting the ping to continue working uninterrupted, and am loath to continue configuring anything until i know this is working properly.         the keepalive configuration is below.   sorry if the display is messed up, my enter key isn't working on here, not sure if it's the forum software, ie10, or a combination                                                       ! Configuration File for keepalived
global_defs {
lvs_id HALB1
}
vrrp_script chk_haproxy {
script "killall -0 haproxy"
interval 2
weight 2
}
vrrp_sync_group LB1 {
group {
VI_webservers
VI_DatabaseServers
VI_Public_180
VI_Public_191
VI_Xen_MGMT 
VI_Local
}
smtp_alert
}
vrrp_instance VI_Local {
state MASTER
interface eth2
garp_master_delay 10
virtual_router_id 41
priority 101
advert_int 1
authentication {
auth_type PASS
auth_pass 0000
}
virtual_ipaddress {
192.168.0.27
}
track_script {
chk_haproxy
}
}
vrrp_instance VI_webservers {
state MASTER
interface eth0
garp_master_delay 10
virtual_router_id 51
priority 101
advert_int 1
authentication {
auth_type PASS
auth_pass 1111
}
virtual_ipaddress {
192.168.100.250
}
track_script {
chk_haproxy
}
}
vrrp_instance VI_DatabaseServers {
state MASTER
interface eth1
garp_master_delay 10
virtual_router_id 52
priority 101
advert_int 1
authentication {
auth_type PASS
auth_pass 2222
} 
virtual_ipaddress {
192.168.101.250
}
track_script {
chk_haproxy
}
}
vrrp_instance VI_Public_180 {
state MASTER
interface eth2.10
garp_master_delay 10
virtual_router_id 61
priority 101
advert_int 1
authentication {
auth_type PASS
auth_pass 3333
}
virtual_ipaddress {
10.10.10.250
}
virtual_ipaddress_excluded {
10.10.10.1
10.10.10.2
10.10.10.3
10.10.10.4
10.10.10.5
10.10.10.6
10.10.10.7
10.10.10.8
10.10.10.9
10.10.10.10
10.10.10.11
10.10.10.12
10.10.10.13
10.10.10.14
10.10.10.15
10.10.10.16
10.10.10.17
10.10.10.18
10.10.10.19
10.10.10.20
10.10.10.21
10.10.10.22
10.10.10.23
10.10.10.24
10.10.10.25
}
track_script {
chk_haproxy
}
}
vrrp_instance VI_Public_191 {
state MASTER
interface eth2.20
garp_master_delay 10
virtual_router_id 62
priority 101
advert_int 1
authentication {
auth_type PASS
auth_pass 4444
}
virtual_ipaddress {
10.10.20.250
}
virtual_ipaddress_excluded {
10.10.20.51
10.10.20.52
10.10.20.53
10.10.20.54
10.10.20.55
10.10.20.56
10.10.20.57
10.10.20.58
10.10.20.59
10.10.20.60
} 
track_script {
chk_haproxy
}
}
vrrp_instance VI_Xen_MGMT {
state MASTER
interface eth3
garp_master_delay 10
virtual_router_id 71
priority 101
advert_int 1
authentication {
auth_type PASS
auth_pass 5555
}
virtual_ipaddress {
192.168.50.250
}
track_script {
chk_haproxy
}
}
&#12288;

---

