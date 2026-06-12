---
title: "Help Debugging NATed  box read time outs with tcpdump"
date: 2009-09-19
forum: Networking &amp; Wireless
---

### Post by jukes on 2009-09-19
Hi People

I have a box that connects to internet through a gateway. From recent days I started to have random read timeouts when sending requests to a specific host. Those are HTTPS requests done through java code running on this private machine. It seems that my box connects correctly but reads fail after several retries with Read Time Out error.

This happens in a somewhat random way because sometimes i have several successful requests but then a new one will fail.

My machine is 192.168.25.4 and requests are made to host 'clubworld.com'. My gateway is a Linux machine with IPTABLES masquerade.

These are outputs of tcpdump for both successful and failed requests, hope you guys can help me with a clue of what is happening here based on the outputs.

Thanks for your help.


FAILED
----------
[root@frontend1:~]#  tcpdump 'host clubworld.com'
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth1, link-type EN10MB (Ethernet), capture size 96 bytes
04:31:35.840805 IP 192.168.25.4.35299 > clubworld.com.https: S 330065403:330065403(0) win 5840 <mss 1460,sackOK,timestamp 1178820306 0,nop,wscale 7>
04:31:35.842071 IP clubworld.com.https > 192.168.25.4.35299: S 2620296529:2620296529(0) ack 330065404 win 16384 <mss 1460,nop,wscale 0,nop,nop,timestamp 0 0,nop,nop,sackOK>
04:31:35.842107 IP 192.168.25.4.35299 > clubworld.com.https: . ack 1 win 46 <nop,nop,timestamp 1178820308 0>

04:31:35.918815 IP 192.168.25.4.35299 > clubworld.com.https: P 1:101(100) ack 1 win 46 <nop,nop,timestamp 1178820384 0>
04:31:36.120433 IP 192.168.25.4.35299 > clubworld.com.https: P 1:101(100) ack 1 win 46 <nop,nop,timestamp 1178820586 0>
04:31:36.524280 IP 192.168.25.4.35299 > clubworld.com.https: P 1:101(100) ack 1 win 46 <nop,nop,timestamp 1178820990 0>
04:31:37.331977 IP 192.168.25.4.35299 > clubworld.com.https: P 1:101(100) ack 1 win 46 <nop,nop,timestamp 1178821798 0>
04:31:38.947376 IP 192.168.25.4.35299 > clubworld.com.https: P 1:101(100) ack 1 win 46 <nop,nop,timestamp 1178823414 0>
04:31:42.178158 IP 192.168.25.4.35299 > clubworld.com.https: P 1:101(100) ack 1 win 46 <nop,nop,timestamp 1178826646 0>
04:31:48.640724 IP 192.168.25.4.35299 > clubworld.com.https: P 1:101(100) ack 1 win 46 <nop,nop,timestamp 1178833110 0>
04:32:01.563861 IP 192.168.25.4.35299 > clubworld.com.https: P 1:101(100) ack 1 win 46 <nop,nop,timestamp 1178846038 0>
04:32:27.412131 IP 192.168.25.4.35299 > clubworld.com.https: P 1:101(100) ack 1 win 46 <nop,nop,timestamp 1178871894 0>
04:32:35.902220 IP 192.168.25.4.35299 > clubworld.com.https: FP 101:108(7) ack 1 win 46 <nop,nop,timestamp 1178880387 0>


SUCCESS
-----------
[root@frontend1:~]#  tcpdump 'host clubworld.com'
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth1, link-type EN10MB (Ethernet), capture size 96 bytes
04:18:27.011470 IP 192.168.25.4.44771 > clubworld.com.https: S 3784488812:3784488812(0) win 5840 <mss 1460,sackOK,timestamp 1178031239 0,nop,wscale 7>
04:18:27.013940 IP clubworld.com.https > 192.168.25.4.44771: S 3260039476:3260039476(0) ack 3784488813 win 16384 <mss 1460,nop,wscale 0,nop,nop,timestamp 0 0,nop,nop,sackOK>
04:18:27.013972 IP 192.168.25.4.44771 > clubworld.com.https: . ack 1 win 46 <nop,nop,timestamp 1178031242 0>

04:18:27.091889 IP 192.168.25.4.44771 > clubworld.com.https: P 1:101(100) ack 1 win 46 <nop,nop,timestamp 1178031320 0>
04:18:27.094852 IP clubworld.com.https > 192.168.25.4.44771: . 1:1449(1448) ack 101 win 65435 <nop,nop,timestamp 87109346 1178031320>
04:18:27.094867 IP 192.168.25.4.44771 > clubworld.com.https: . ack 1449 win 69 <nop,nop,timestamp 1178031323 87109346>
04:18:27.094871 IP clubworld.com.https > 192.168.25.4.44771: P 1449:1498(49) ack 101 win 65435 <nop,nop,timestamp 87109346 1178031320>
04:18:27.094877 IP 192.168.25.4.44771 > clubworld.com.https: . ack 1498 win 69 <nop,nop,timestamp 1178031323 87109346>

---

