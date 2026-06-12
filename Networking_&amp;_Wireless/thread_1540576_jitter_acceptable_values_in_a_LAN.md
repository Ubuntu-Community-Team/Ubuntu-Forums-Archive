---
title: "jitter acceptable values in a LAN"
date: 2010-07-28
forum: Networking &amp; Wireless
---

### Post by sulekha on 2010-07-28
Hi all,

I measured jitter values for a LAN about 30 computers using iperf as follows:-


iperf -c 192.168.0.210 -ub 100m
------------------------------------------------------------
Client connecting to 192.168.0.210, UDP port 5001
Sending 1470 byte datagrams
UDP buffer size: 110 KByte (default)
------------------------------------------------------------
[ 3] local 192.168.0.17 port 45559 connected with 192.168.0.210 port 5001
[ ID] Interval Transfer Bandwidth
[ 3] 0.0-10.0 sec 109 MBytes 91.3 Mbits/sec
[ 3] Sent 77631 datagrams
[ 3] Server Report:
[ 3] 0.0-10.0 sec 109 MBytes 91.2 Mbits/sec 0.405 ms 0/77630 (0%)
[ 3] 0.0-10.0 sec 1 datagrams received out-of-order



[root@backup ~]# iperf -su -i 1
------------------------------------------------------------
Server listening on UDP port 5001
Receiving 1470 byte datagrams
UDP buffer size: 126 KByte (default)
------------------------------------------------------------
[ 3] local 192.168.0.210 port 5001 connected with 192.168.0.17 port 45559

[ ID] Interval Transfer Bandwidth Jitter Lost/Total Datagrams
[ 3] 0.0- 1.0 sec 10.9 MBytes 91.1 Mbits/sec 0.041 ms 0/ 7745 (0%)
[ 3] 1.0- 2.0 sec 10.9 MBytes 91.4 Mbits/sec 0.027 ms 0/ 7768 (0%)
[ 3] 2.0- 3.0 sec 10.8 MBytes 90.8 Mbits/sec 0.059 ms 0/ 7722 (0%)
[ 3] 3.0- 4.0 sec 10.9 MBytes 91.3 Mbits/sec 0.175 ms 0/ 7761 (0%)
[ 3] 4.0- 5.0 sec 10.9 MBytes 91.3 Mbits/sec 0.031 ms 0/ 7763 (0%)
[ 3] 5.0- 6.0 sec 10.9 MBytes 91.3 Mbits/sec 0.026 ms 0/ 7762 (0%)
[ 3] 6.0- 7.0 sec 10.9 MBytes 91.3 Mbits/sec 0.161 ms 0/ 7762 (0%)
[ 3] 7.0- 8.0 sec 10.9 MBytes 91.3 Mbits/sec 0.034 ms 0/ 7760 (0%)
[ 3] 8.0- 9.0 sec 10.9 MBytes 91.3 Mbits/sec 0.039 ms 0/ 7763 (0%)
[ 3] 9.0-10.0 sec 10.9 MBytes 91.2 Mbits/sec 0.027 ms 0/ 7759 (0%)
[ 3] 0.0-10.0 sec 109 MBytes 91.2 Mbits/sec 0.405 ms 0/77630 (0%)
[ 3] 0.0-10.0 sec 1 datagrams received out-of-order


Now what I want to know is what are the acceptable values/limits/ranges for Jitter ?

what is the unit for measuring jitter or what is meant by this ms is it metre per second ?

---

