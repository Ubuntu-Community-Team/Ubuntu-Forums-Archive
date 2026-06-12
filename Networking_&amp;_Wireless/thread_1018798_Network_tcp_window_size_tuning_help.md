---
title: "Network tcp window size tuning help"
date: 2008-12-22
forum: Networking &amp; Wireless
---

### Post by rogerwilcos on 2008-12-22
I have an application that uses IBM websphere on a centralized server to send webpages out to 100's of client machines (appliances) in the field. The server is running Redhat EL 5 (kernel 2.6.18-92.1.13.el5) and all of the clients are running Ubuntu (vanilla kernel 2.6.24). 

Our customer is telling us that our setup of server and clients is saturating their network at a location that has no other devices installed. Their explanation from looking at router and switch logs is that our tcp window size is not set correctly on the server and clients and is causing the additional traffic. 

I am by no means an expert in ipv4 or networking so I am looking for any helpful hints as to what might be going on. Here are the outputs of some of the ipv4 config files:

Server
------
rmem_max = 131071
wmem_max = 131071
rmem_default = 109568
wmem_default = 109568

Client
------
rmem_max = 108544
wmem_max = 108544
rmem_default = 108544
wmem_default = 108544

I had also read that in kernel 2.4 and 2.6 there are supposed to be mechanisms in place to negotiate between servers with different window size settings. How does this work?

---

### Post by mpokrywka on 2008-12-22
You can check actual tcp settings issuing:
**grep . /proc/sys/net/ipv4/tcp_***

Maybe try to remove all tweaking and check if linux kernel would sort it all by itself by default.
Maybe you have some features, like window scaling, turned off?

---

### Post by rogerwilcos on 2008-12-29
Here is the information requested for the Kiosk and the Server. I am not sure why this is acting up. These are both very standard installs of Ubuntu and Redhat. I have not changed any of the default tcp/ip settings. If there is nothing that looks incorrect about the setup we have, could I please ask for suggestions as to how to work with our customer to verify any problems that may be in their switches and routers? Thanks!

KIOSK

/proc/sys/net/ipv4/tcp_abc:0
/proc/sys/net/ipv4/tcp_abort_on_overflow:0
/proc/sys/net/ipv4/tcp_adv_win_scale:2
/proc/sys/net/ipv4/tcp_allowed_congestion_control:cubic reno
/proc/sys/net/ipv4/tcp_app_win:31
/proc/sys/net/ipv4/tcp_available_congestion_control:cubic reno
/proc/sys/net/ipv4/tcp_base_mss:512
/proc/sys/net/ipv4/tcp_congestion_control:cubic
/proc/sys/net/ipv4/tcp_dsack:1
/proc/sys/net/ipv4/tcp_ecn:0
/proc/sys/net/ipv4/tcp_fack:1
/proc/sys/net/ipv4/tcp_fin_timeout:60
/proc/sys/net/ipv4/tcp_frto:2
/proc/sys/net/ipv4/tcp_frto_response:0
/proc/sys/net/ipv4/tcp_keepalive_intvl:75
/proc/sys/net/ipv4/tcp_keepalive_probes:9
/proc/sys/net/ipv4/tcp_keepalive_time:7200
/proc/sys/net/ipv4/tcp_low_latency:0
/proc/sys/net/ipv4/tcp_max_orphans:8192
/proc/sys/net/ipv4/tcp_max_ssthresh:0
/proc/sys/net/ipv4/tcp_max_syn_backlog:1024
/proc/sys/net/ipv4/tcp_max_tw_buckets:180000
/proc/sys/net/ipv4/tcp_mem:42528        56704   85056
/proc/sys/net/ipv4/tcp_moderate_rcvbuf:1
/proc/sys/net/ipv4/tcp_mtu_probing:0
/proc/sys/net/ipv4/tcp_no_metrics_save:0
/proc/sys/net/ipv4/tcp_orphan_retries:0
/proc/sys/net/ipv4/tcp_reordering:3
/proc/sys/net/ipv4/tcp_retrans_collapse:1
/proc/sys/net/ipv4/tcp_retries1:3
/proc/sys/net/ipv4/tcp_retries2:15
/proc/sys/net/ipv4/tcp_rfc1337:0
/proc/sys/net/ipv4/tcp_rmem:4096        87380   1814528
/proc/sys/net/ipv4/tcp_sack:1
/proc/sys/net/ipv4/tcp_slow_start_after_idle:1
/proc/sys/net/ipv4/tcp_stdurg:0
/proc/sys/net/ipv4/tcp_synack_retries:5
/proc/sys/net/ipv4/tcp_syncookies:0
/proc/sys/net/ipv4/tcp_syn_retries:5
/proc/sys/net/ipv4/tcp_timestamps:1
/proc/sys/net/ipv4/tcp_tso_win_divisor:3
/proc/sys/net/ipv4/tcp_tw_recycle:0
/proc/sys/net/ipv4/tcp_tw_reuse:0
/proc/sys/net/ipv4/tcp_window_scaling:1
/proc/sys/net/ipv4/tcp_wmem:4096        16384   1814528
/proc/sys/net/ipv4/tcp_workaround_signed_windows:0

SERVER

/proc/sys/net/ipv4/tcp_abc:0
/proc/sys/net/ipv4/tcp_abort_on_overflow:0
/proc/sys/net/ipv4/tcp_adv_win_scale:2
/proc/sys/net/ipv4/tcp_app_win:31
/proc/sys/net/ipv4/tcp_base_mss:512
/proc/sys/net/ipv4/tcp_congestion_control:bic
/proc/sys/net/ipv4/tcp_dma_copybreak:4096
/proc/sys/net/ipv4/tcp_dsack:1
/proc/sys/net/ipv4/tcp_ecn:0
/proc/sys/net/ipv4/tcp_fack:1
/proc/sys/net/ipv4/tcp_fin_timeout:60
/proc/sys/net/ipv4/tcp_frto:0
/proc/sys/net/ipv4/tcp_keepalive_intvl:75
/proc/sys/net/ipv4/tcp_keepalive_probes:9
/proc/sys/net/ipv4/tcp_keepalive_time:7200
/proc/sys/net/ipv4/tcp_low_latency:0
/proc/sys/net/ipv4/tcp_max_orphans:32768
/proc/sys/net/ipv4/tcp_max_syn_backlog:1024
/proc/sys/net/ipv4/tcp_max_tw_buckets:180000
/proc/sys/net/ipv4/tcp_mem:98304        131072  196608
/proc/sys/net/ipv4/tcp_moderate_rcvbuf:1
/proc/sys/net/ipv4/tcp_mtu_probing:0
/proc/sys/net/ipv4/tcp_no_metrics_save:0
/proc/sys/net/ipv4/tcp_orphan_retries:0
/proc/sys/net/ipv4/tcp_reordering:3
/proc/sys/net/ipv4/tcp_retrans_collapse:1
/proc/sys/net/ipv4/tcp_retries1:3
/proc/sys/net/ipv4/tcp_retries2:15
/proc/sys/net/ipv4/tcp_rfc1337:0
/proc/sys/net/ipv4/tcp_rmem:4096        87380   4194304
/proc/sys/net/ipv4/tcp_sack:1
/proc/sys/net/ipv4/tcp_slow_start_after_idle:1
/proc/sys/net/ipv4/tcp_stdurg:0
/proc/sys/net/ipv4/tcp_synack_retries:5
/proc/sys/net/ipv4/tcp_syncookies:1
/proc/sys/net/ipv4/tcp_syn_retries:5
/proc/sys/net/ipv4/tcp_timestamps:1
/proc/sys/net/ipv4/tcp_tso_win_divisor:3
/proc/sys/net/ipv4/tcp_tw_recycle:0
/proc/sys/net/ipv4/tcp_tw_reuse:0
/proc/sys/net/ipv4/tcp_window_scaling:1
/proc/sys/net/ipv4/tcp_wmem:4096        16384   4194304
/proc/sys/net/ipv4/tcp_workaround_signed_windows:0

---

### Post by mpokrywka on 2008-12-30
Yeah, your config looks like default settings. I am, too, no expert of tcp tuning, but I think you should ask for more specific explanation.
Maybe they should state what exactly the problem is?
Do you have "KIOSK" at your customer, and communiction KIOSK<->SERVER is causing problems?
What "problems" mean? Too much bandwidth used? Too much upload (by KIOSK)? Too much download (by KIOSK)? Too many connections? Too many packets per second sent/received?
Maybe this customer has some firewall/router that chokes on some tcp options and tcp connection is degraded?
Maybe this is problem with window scaling, like: [http://inodes.org/blog/2006/09/06/tcp-window-scaling-and-kernel-2617/](http://inodes.org/blog/2006/09/06/tcp-window-scaling-and-kernel-2617/)
Maybe you have MTU set very low and there is high transmission overhead?

---

