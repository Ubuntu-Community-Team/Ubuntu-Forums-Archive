---
title: "Squid/Networking"
date: 2011-12-20
forum: Networking &amp; Wireless
---

### Post by MGUbunt on 2011-12-20
Hi to all

This is my first post please forgive if I have put it in the wrong place...

OK here we go...

I am having proplems connecting clients to the internet... who must go via the proxy!

I have a project which is rather large, but I will go stright in and tell you my set up

I have a server running Ubuntu on this server I have installed squid

The server has 2 network cards eth0, which is connected to the internet
and eth1 which is connected to my LAN

connection to the internet is estabilshed and working no problem

I have set the LAN IP address as 192.168.0.3
the WAN is set to <staticIP> address

the LAN connects to a router
The Router IP address is 192.168.0.2

The router is set to dish out IP addresses from 192.168.0.12 to 192.168.0.253

My routing table is set with the following script

<>
#!/bin/sh
# squid server IP

SQUID_SERVER="192.168.0.3"

# Interface connected to Internet
INTERNET="eth0"

# Interface connected to LAN
LAN_IN="eth1"

# Squid port
SQUID_PORT="3128"

# DO NOT MODIFY BELOW
# Clean old firewall
iptables -F
iptables -X
iptables -t nat -F
iptables -t nat -X
iptables -t mangle -F
iptables -t mangle -X

# Load IPTABLES modules for NAT and IP conntrack support
modprobe ip_conntrack
modprobe ip_conntrack_ftp
# For win xp ftp client
#modprobe ip_nat_ftp
echo 1 > /proc/sys/net/ipv4/ip_forward

# Setting default filter policy
iptables -P INPUT DROP
iptables -P OUTPUT ACCEPT

# Unlimited access to loop back
iptables -A INPUT -i lo -j ACCEPT
iptables -A OUTPUT -o lo -j ACCEPT

# Allow UDP, DNS and Passive FTP
iptables -A INPUT -i $INTERNET -m state --state ESTABLISHED,RELATED -j 
ACCEPT

# set this system as a router for Rest of LAN
iptables --table nat --append POSTROUTING --out-interface $INTERNET -j 
MASQUERADE
iptables --append FORWARD --in-interface $LAN_IN -j ACCEPT

# unlimited access to LAN
iptables -A INPUT -i $LAN_IN -j ACCEPT
iptables -A OUTPUT -o $LAN_IN -j ACCEPT

# DNAT port 80 request comming from LAN systems to squid 3128 
($SQUID_PORT) aka transparent proxy
iptables -t nat -A PREROUTING -i $LAN_IN -p tcp --dport 80 -j DNAT --to 
$SQUID_SERVER:$SQUID_PORT

# if it is same system
iptables -t nat -A PREROUTING -i $INTERNET -p tcp --dport 80 -j 
REDIRECT 
--to-port $SQUID_PORT

# DROP everything and Log it
iptables -A INPUT -j LOG
iptables -A INPUT -j DROP

<>

Im not 100% sure if this script is correct but i have it on good authority that it is...
However I am open to suggestions

my squid.conf
<>
http_port 192.168.0.3:3128

visible_hostname SomeDomaine
mail_from [EMAIL="squid@anemail.com"]squid@anemail.com[/EMAIL]
client_netmask 255.255.255.255
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
error_directory /usr/share/squid/errors/en
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
cache_mem 8 MB
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
client_lifetime 1 day
shutdown_lifetime 30 seconds
reply_header_max_size 20 KB
announce_period 50 seconds
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
high_memory_warning 60 MB
sleep_after_fork 0
minimum_expiry_time 60 seconds
authenticate_cache_garbage_interval 1 seconds
authenticate_ttl 1 seconds
authenticate_ip_ttl 20 seconds
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
half_closed_clients on
httpd_suppress_version_string off
via on
forwarded_for on
log_icp_queries on
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
retry_on_error off
wccp2_rebuild_wait on
digest_generation on

acl our_networks src 192.168.0.3
acl localhost src 127.0.0.1/32
acl to_localhost dst 127.0.0.0/8
acl all src 0.0.0.0/0.0.0.0
acl manager proto cache_object
acl QUERY urlpath_regex cgi-bin \?
acl apache rep_header Server ^Apache
acl SSL_ports port 443
acl Safe_ports port 80        # http
acl Safe_ports port 21        # ftp
acl Safe_ports port 443        # https
acl Safe_ports port 70        # gopher
acl Safe_ports port 210        # wais
acl Safe_ports port 1025-65535    # unregistered ports
acl Safe_ports port 280        # http-mgmt
acl Safe_ports port 488        # gss-http
acl Safe_ports port 591        # filemaker
acl Safe_ports port 777        # multiling http
acl Safe_ports port 5110     # skype
acl CONNECT method CONNECT

auth_param basic program /usr/lib/squid/ncsa_auth /etc/squid/passwd
auth_param basic children 5
auth_param basic realm kumbonet
auth_param basic credentialsttl 2 hour
auth_param basic casesensitive off

acl need_auth proxy_auth REQUIRED

http_access allow need_auth
http_access allow localhost
http_access allow our_networks
http_reply_access allow all
icp_access allow all
http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports
cache deny QUERY
#ident_lookup_access deny all
http_access allow all

<>

my clients use the proxy server IP address of 192.168.0.3 and should be prompted for a username and password

Any ideas why the clients can not connect to the internet?

I have ran out of ideas please help!!!

---

