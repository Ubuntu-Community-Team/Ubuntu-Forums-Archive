---
title: "How to allow file transfer on MSN using Squid/Iptables?"
date: 2009-09-28
forum: Networking &amp; Wireless
---

### Post by richterlevania3 on 2009-09-28
Hi there,

I have a squid/iptables running good, but I want it to allow MSN file transfers and a program that uses some random port to send content over the web. Currently, both doesn't do it. Here is my pertinent iptables and squid .conf files:

```
#!/bin/sh
# 
# this script requires iptables package to be
# installed on your machine


# Where to find iptables binary
IPT="/sbin/iptables"

# The network interface you will use
# WAN is the one connected to the internet
# LAN the one connected to your local network
WAN="eth1"
LAN="eth0"
# First we need to clear up any existing firewall rules
# and chain which might have been created
$IPT -F
$IPT -F INPUT
$IPT -F OUTPUT
$IPT -F FORWARD
$IPT -F -t mangle
$IPT -F -t nat
$IPT -X

# Default policies: Drop any incoming packets
# accept the rest.
$IPT -P INPUT DROP
$IPT -P OUTPUT ACCEPT
$IPT -P FORWARD ACCEPT

# To be able to forward traffic from your LAN
# to the Internet, we need to tell the kernel
# to allow ip forwarding
echo 1 > /proc/sys/net/ipv4/ip_forward

# Masquerading will make machines from the LAN
# look like if they were the router
$IPT -t nat -A POSTROUTING -o $WAN -j MASQUERADE

# If you want to allow traffic to specific port to be
# forwarded to a machine from your LAN
# here we forward traffic to an HTTP server to machine 192.168.0.2
#$IPT -t nat -A PREROUTING -i $WAN -p tcp --dport 3389 -j DNAT --to 189.51.195.11:80
#$IPT -A FORWARD -i $WAN -p tcp  --dport 80 -m state --state NEW -j ACCEPT
# For a whole range of port, use:
$IPT -t nat -A PREROUTING -i $WAN -p tcp --dport 1:9999 -j DNAT --to 189.51.195.11
$IPT -A FORWARD -i $WAN -p tcp  --dport 1:9999 -m state --state NEW -j ACCEPT

# Do not allow new or invalid connections to reach your internal network
$IPT -A FORWARD -i $WAN -m state --state NEW,INVALID -j DROP

# Accept any connections from the local machine
$IPT -A INPUT -i lo -j ACCEPT
# plus from your local network
$IPT -A INPUT -i $LAN -j ACCEPT

# Here we define a new chain which is going to handle
# packets we don't want to respond to
# limit the amount of logs to 10/min
$IPT -N Firewall
$IPT -A Firewall -m limit --limit 10/minute -j LOG --log-prefix "Firewall: "
$IPT -A Firewall -j DROP

# log those packets and inform the sender that the packet was rejected
$IPT -N Rejectwall
$IPT -A Rejectwall -m limit --limit 10/minute -j LOG --log-prefix "Rejectwall: "
$IPT -A Rejectwall -j REJECT
# use the following instead if you want to simulate that the host is not reachable
# for fun though
#$IPT -A Rejectwall -j REJECT  --reject-with icmp-host-unreachable

# here we create a chain to deal with unlegitimate packets
# and limit the number of alerts to 10/min
# packets will be drop without informing the sender
$IPT -N Badflags
$IPT -A Badflags -m limit --limit 10/minute -j LOG --log-prefix "Badflags: "
$IPT -A Badflags -j DROP

# A list of well known combination of Bad TCP flags
# we redirect those to the Badflags chain
# which is going to handle them (log and drop)
$IPT -A INPUT -p tcp --tcp-flags ACK,FIN FIN -j Badflags
$IPT -A INPUT -p tcp --tcp-flags ACK,PSH PSH -j Badflags
$IPT -A INPUT -p tcp --tcp-flags ACK,URG URG -j Badflags
$IPT -A INPUT -p tcp --tcp-flags FIN,RST FIN,RST -j Badflags
$IPT -A INPUT -p tcp --tcp-flags SYN,FIN SYN,FIN -j Badflags
$IPT -A INPUT -p tcp --tcp-flags SYN,RST SYN,RST -j Badflags
$IPT -A INPUT -p tcp --tcp-flags ALL ALL -j Badflags
$IPT -A INPUT -p tcp --tcp-flags ALL NONE -j Badflags
$IPT -A INPUT -p tcp --tcp-flags ALL FIN,PSH,URG -j Badflags
$IPT -A INPUT -p tcp --tcp-flags ALL SYN,FIN,PSH,URG -j Badflags
$IPT -A INPUT -p tcp --tcp-flags ALL SYN,RST,ACK,FIN,URG -j Badflags

# Accept certain icmp message, drop the others
# and log them through the Firewall chain
# 0 => echo reply
$IPT -A INPUT -p icmp --icmp-type 0 -j ACCEPT
# 3 => Destination Unreachable
$IPT -A INPUT -p icmp --icmp-type 3 -j ACCEPT
# 11 => Time Exceeded
$IPT -A INPUT -p icmp --icmp-type 11 -j ACCEPT
# 8 => Echo
# avoid ping flood
$IPT -A INPUT -p icmp --icmp-type 8 -m limit --limit 1/second -j ACCEPT
$IPT -A INPUT -p icmp -j Firewall

# Accept ssh connections from the Internet
$IPT -A INPUT -i $WAN -p tcp --dport 22 -j ACCEPT
# or only accept from a certain ip
#$IPT -A INPUT -i $WAN -s 125.124.123.122 -p tcp --dport 22 -j ACCEPT

# Accept related and established connections
$IPT -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT

# Drop netbios from the outside, no log, just drop
$IPT -A INPUT -p udp --sport 137 --dport 137 -j DROP

# Finally, anything which was not allowed yet
# is going to go through our Rejectwall rule
$IPT -A INPUT -j Rejectwall
```

```
http_port 192.168.0.100:3128

visible_hostname Servidor
mail_from richterlevania3@gmail.com
client_netmask 255.255.255.0
dns_nameservers 172.16.7.53
snmp_incoming_address 0.0.0.0
snmp_outgoing_address 255.255.255.255
udp_incoming_address 0.0.0.0
udp_outgoing_address 255.255.255.255
icp_port 3130 proxy-only
cache_replacement_policy lru
memory_replacement_policy lru
cache_dir ufs /var/spool/squid 100 16 256
hierarchy_stoplist cgi-bin ?
access_log /var/log/squid/access.log squid
cache_log /var/log/squid/cache.log
cache_store_log /var/log/squid/store.log
pid_filename /var/run/squid.pid
hosts_file /etc/hosts
icon_directory /usr/share/squid/icons
error_directory /usr/share/squid/errors/English
diskd_program /usr/lib/squid/diskd-daemon
unlinkd_program /usr/lib/squid/unlinkd
debug_options ALL,1
ftp_user Squid@
uri_whitespace strip
cache_effective_user squid
cache_effective_group squid
cache_mgr root
mail_program mail
umask 027
announce_host tracker.ircache.net
as_whois_server whois.ra.net
wccp_address 0.0.0.0
wccp2_address 0.0.0.0
wccp_router 0.0.0.0
store_dir_select_algorithm least-load
coredump_dir /var/spool/squid
icp_query_timeout 0
maximum_icp_query_timeout 2000
mcast_icp_query_timeout 2000
dead_peer_timeout 10 seconds
forward_timeout 4 minutes
connect_timeout 1 minutes
peer_connect_timeout 30 seconds
read_timeout 15 minutes
request_timeout 5 minutes
persistent_request_timeout 1 minutes
pconn_timeout 120 seconds
ident_timeout 10 seconds
dns_timeout 2 minutes
dns_retransmit_interval 5 seconds
snmp_port 0
cache_mem 64 MB
cache_swap_low 90
cache_swap_high 95
maximum_object_size 4096 KB
minimum_object_size 0 KB
maximum_object_size_in_memory 8 KB
ipcache_size 1024
ipcache_low 90
ipcache_high 95
fqdncache_size 1024
ftp_list_width 32
memory_pools_limit 5 MB
request_header_max_size 20 KB
request_body_max_size 0 KB
quick_abort_min 16 KB
quick_abort_max 16 KB
quick_abort_pct 95
read_ahead_gap 16 KB
negative_ttl 5 minutes
positive_dns_ttl 6 seconds
negative_dns_ttl 1 seconds
range_offset_limit 0 KB
refresh_stale_hit 0
client_lifetime 1 day
shutdown_lifetime 30 seconds
reply_header_max_size 20 KB
announce_period 0
announce_port 3131
logfile_rotate 0
tcp_recv_bufsize 0 bytes
minimum_direct_hops 4
minimum_direct_rtt 400
store_avg_object_size 13 KB
store_objects_per_bucket 20
netdb_low 900
netdb_high 1000
netdb_ping_period 5 minutes
maximum_single_addr_tries 1
wccp_version 4
wccp2_forwarding_method 1
wccp2_return_method 1
wccp2_assignment_method 1
wccp2_service standard 0
wccp2_weight 10000
max_open_disk_fds 0
digest_bits_per_entry 5
digest_rebuild_period 1 seconds
digest_rewrite_period 1 seconds
digest_swapout_chunk_size 4096 bytes
digest_rebuild_chunk_percentage 10
high_response_time_warning 0
high_page_fault_warning 0
high_memory_warning 0
sleep_after_fork 0
minimum_expiry_time 60 seconds
max_filedesc 1024
authenticate_cache_garbage_interval 1 seconds
authenticate_ttl 1 seconds
authenticate_ip_ttl 0
check_hostnames on
dns_defnames off
emulate_httpd_log off
log_ip_on_direct on
log_mime_hdrs off
log_fqdn off
ftp_passive on
ftp_sanitycheck on
ftp_telnet_protocol on
allow_underscore on
memory_pools on
acl_uses_indirect_client on
half_closed_clients on
httpd_suppress_version_string off
delay_pool_uses_indirect_client on
log_uses_indirect_client on
via on
forwarded_for on
log_icp_queries on
httpd_accel_no_pmtu_disc off
client_db on
icp_hit_stale off
query_icmp off
test_reachability off
buffered_logs off
reload_into_ims off
global_internal_static on
short_icon_urls off
offline_mode off
nonhierarchical_direct on
prefer_direct off
strip_query_terms on
redirector_bypass off
ignore_unknown_nameservers on
client_persistent_connections on
server_persistent_connections on
persistent_connection_after_error off
detect_broken_pconn off
balance_on_multiple_ip on
pipeline_prefetch off
request_entities off
ie_refresh off
vary_ignore_expire off
relaxed_header_parser on
cache_vary on
retry_on_error off
collapsed_forwarding off
wccp2_rebuild_wait on
digest_generation on

acl all src 0.0.0.0/0.0.0.0
acl our_networks src 192.168.0.0/24 192.168.1.0/24
acl localhost src 127.0.0.1/255.255.255.255
acl to_localhost dst 127.0.0.0/8
acl manager proto cache_object
acl QUERY urlpath_regex cgi-bin \?
acl apache rep_header Server ^Apache
acl MSNBlock port 1863
acl MSNAllow port 6891-6900
acl CONNECT method CONNECT
acl blockedsites url_regex "/home/administrador/block"
acl msnmime req_mime_type ^application/x-msn-messenger
acl msngw url_regex -i gateway.dll
http_access allow MSNAllow
http_access allow all
http_access allow localhost
http_access allow our_networks
http_reply_access allow all
broken_vary_encoding allow apache
icp_access allow all
miss_access allow all
http_access deny all


```

Someone can give me a clue?

---

### Post by richterlevania3 on 2009-09-29
Bump.

Please guys, my work is at a halt until I solve this.

---

