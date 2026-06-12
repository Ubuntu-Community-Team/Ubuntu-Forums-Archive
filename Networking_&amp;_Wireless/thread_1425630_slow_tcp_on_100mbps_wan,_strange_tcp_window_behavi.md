---
title: "slow tcp on 100mbps wan, strange tcp window behaviour on ubuntu 9.10"
date: 2010-03-09
forum: Networking &amp; Wireless
---

### Post by cputoaster on 2010-03-09
Hi there,

I have a strange problem when transmitting from my server to a client. The server does not seem to honor the tcp window advertized from the client, but only sends around 10kB worth of packets without being acked. The link is wan, but fast, and the resulting transfer rate is not. This must be something trivial, but I could not find it for now. I concentrate on information about the server, as you can see in the tcpdump (see url) that the client scales up the advertised tcp window correctly (I think), but somehow the server does not act on it. At least that is what I interpret into the tcptrace tsg graph ;-).

I did try the cubic and reno algos, but I dont think it really has something to do with it.

Transfer rates over the same interface to another GB LAN box shows ca 870Mbps, but the tcpdump shows the same problem.

I also tried playing with the rmem / wmem parameters, but this did not change anything.

It is probably not a tcp windows scaling problem, because the tcpdump shows that the correct scaling factor (9) arrives at the server.

Any ideas? What else could I try?

Cheers,
cputoaster

Details:

HW:
Core i7-920, 6GB RAM, 2 x X25-M SSD 
Gigabyte Technology Co., Ltd.,  EX58-UD5
Linux twin 2.6.31-14-server #48-Ubuntu SMP Fri Oct 16 15:07:34 UTC 2009 x86_64 GNU/Linux
eth0: RTL8168d/8111d at 0xffffc90000c7a000, 00:1f:d0:ae:41:3a, XID 281000c0 IRQ 33

Ping from client to host: 
rtt min/avg/max/mdev = 7.108/7.684/8.035/0.362 ms


UDP test: works fine, no packet loss up to 80Mbps

```

$ iperf -p 12345 -c shibuya -t 1 -u -b 80M
------------------------------------------------------------
Client connecting to shibuya, UDP port 12345
Sending 1470 byte datagrams
UDP buffer size:   126 KByte (default)
------------------------------------------------------------
[  3] local 80.74.147.15 port 56372 connected with 77.58.146.237 port 12345
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0- 1.0 sec  9.54 MBytes  80.0 Mbits/sec
[  3] Sent 6804 datagrams
[  3] Server Report:
[  3]  0.0- 1.0 sec  9.54 MBytes  80.0 Mbits/sec  0.049 ms    0/ 6803 (0%)
[  3]  0.0- 1.0 sec  1 datagrams received out-of-order


```

TCP test: slow

[tcpdump]("http://cputoasters.com/ameyer/dumps/dump_twin_1s.bin")

```

$ iperf -p 12345 -c shibuya -t 1
------------------------------------------------------------
Client connecting to shibuya, TCP port 12345
TCP window size: 64.0 KByte (default)
------------------------------------------------------------
[  3] local 80.74.147.15 port 45135 connected with 77.58.146.237 port 12345
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0- 1.0 sec  1.52 MBytes  12.6 Mbits/sec


```


/proc/sys/net/core$ for a in *; do echo $a = `cat $a`; done
dev_weight = 64
message_burst = 10
message_cost = 5
netdev_budget = 300
netdev_max_backlog = 1000
optmem_max = 20480
rmem_default = 129024
rmem_max = 16777216
somaxconn = 128
warnings = 1
wmem_default = 129024
wmem_max = 16777216
xfrm_acq_expires = 30
xfrm_aevent_etime = 10
xfrm_aevent_rseqth = 2
xfrm_larval_drop = 1


/proc/sys/net/ipv4$ for a in *; do echo $a = `cat $a`; done
cipso_cache_bucket_size = 10
cipso_cache_enable = 1
cipso_rbm_optfmt = 0
cipso_rbm_strictvalid = 1
cat: conf: Invalid argument
conf =
icmp_echo_ignore_all = 0
icmp_echo_ignore_broadcasts = 1
icmp_errors_use_inbound_ifaddr = 0
icmp_ignore_bogus_error_responses = 1
icmp_ratelimit = 1000
icmp_ratemask = 6168
igmp_max_memberships = 20
igmp_max_msf = 10
inet_peer_gc_maxtime = 120
inet_peer_gc_mintime = 10
inet_peer_maxttl = 600
inet_peer_minttl = 120
inet_peer_threshold = 65664
ip_default_ttl = 64
ip_dynaddr = 0
ip_forward = 0
ipfrag_high_thresh = 262144
ipfrag_low_thresh = 196608
ipfrag_max_dist = 64
ipfrag_secret_interval = 600
ipfrag_time = 30
ip_local_port_range = 32768 61000
ip_nonlocal_bind = 0
ip_no_pmtu_disc = 0
cat: neigh: Invalid argument
neigh =
cat: netfilter: Invalid argument
netfilter =
cat: route: Invalid argument
route =
rt_cache_rebuild_count = 4
tcp_abc = 0
tcp_abort_on_overflow = 0
tcp_adv_win_scale = 2
tcp_allowed_congestion_control = reno cubic
tcp_app_win = 31
tcp_available_congestion_control = reno cubic
tcp_base_mss = 512
tcp_congestion_control = reno
tcp_dma_copybreak = 4096
tcp_dsack = 1
tcp_ecn = 2
tcp_fack = 1
tcp_fin_timeout = 60
tcp_frto = 2
tcp_frto_response = 0
tcp_keepalive_intvl = 75
tcp_keepalive_probes = 9
tcp_keepalive_time = 7200
tcp_low_latency = 0
tcp_max_orphans = 65536
tcp_max_ssthresh = 0
tcp_max_syn_backlog = 1024
tcp_max_tw_buckets = 180000
tcp_mem = 573216 764288 1146432
tcp_moderate_rcvbuf = 1
tcp_mtu_probing = 0
tcp_no_metrics_save = 1
tcp_orphan_retries = 0
tcp_reordering = 3
tcp_retrans_collapse = 1
tcp_retries1 = 3
tcp_retries2 = 15
tcp_rfc1337 = 0
tcp_rmem = 4096 87380 16777216
tcp_sack = 1
tcp_slow_start_after_idle = 1
tcp_stdurg = 0
tcp_synack_retries = 5
tcp_syncookies = 1
tcp_syn_retries = 5
tcp_timestamps = 1
tcp_tso_win_divisor = 3
tcp_tw_recycle = 0
tcp_tw_reuse = 0
tcp_window_scaling = 1
tcp_wmem = 4096 65536 16777216
tcp_workaround_signed_windows = 0
udp_mem = 573216 764288 1146432
udp_rmem_min = 4096
udp_wmem_min = 4096


```

$ tc qdisc show
qdisc pfifo_fast 0: dev eth0 root bands 3 priomap  1 2 2 2 1 2 0 0 1 1 1 1 1 1 1 1
qdisc pfifo_fast 0: dev tap1 root bands 3 priomap  1 2 2 2 1 2 0 0 1 1 1 1 1 1 1 1

```

```

$ sudo iptables-save
# Generated by iptables-save v1.4.4 on Tue Mar  9 11:14:25 2010
*mangle
:PREROUTING ACCEPT [456037650:452132252363]
:INPUT ACCEPT [454631424:451976798011]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [386809374:249150364505]
:POSTROUTING ACCEPT [386885387:249177749066]
COMMIT
# Completed on Tue Mar  9 11:14:25 2010
# Generated by iptables-save v1.4.4 on Tue Mar  9 11:14:25 2010
*nat
:PREROUTING ACCEPT [2890854:395374666]
:POSTROUTING ACCEPT [1735647:201926849]
:OUTPUT ACCEPT [1735647:201926849]
COMMIT
# Completed on Tue Mar  9 11:14:25 2010
# Generated by iptables-save v1.4.4 on Tue Mar  9 11:14:25 2010
*filter
:INPUT ACCEPT [476255712:465823687091]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [2205080721:338098852071]
-A INPUT ! -s 127.0.0.1/32 -p tcp -m tcp --dport 389 -j DROP 
COMMIT
# Completed on Tue Mar  9 11:14:25 2010

```

---

### Post by neiby on 2012-05-04
We're running into a similar issue and I ran across your post doing a web search. Did you ever discover the solution?

---

