---
title: "UFW+OpenVPN: What is being blocked?"
date: 2012-06-03
forum: Networking &amp; Wireless
---

### Post by Artemus on 2012-06-03
I'm running OpenVPN to connect an Ubuntu client to an Ubuntu server using bridged mode. I have port 1194 open in UFW on both sides. Everything seems to be working fine, but I'm getting the following messages in /var/log/ufw.log every two minutes or so:

On the server:

Jun  3 09:00:03 server kernel: [431065.056083] [UFW BLOCK] IN=br0 OUT= MAC=33:33:00:00:00:01:00:1e:c0:a2:34:ba:24:ee SRC=fe80:0000:0000:0000:021e:c0ff:fea2:34ba DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=72 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 

On the client:

Jun  3 09:00:34 client kernel: [ 6104.613525] [UFW BLOCK] IN=tap0 OUT= MAC=33:33:00:00:00:01:00:1e:c0:a2:34:ba:24:ee SRC=fe80:0000:0000:0000:021e:c0ff:fea2:34ba DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=72 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 


Is this something I should be concerned about?


Edit: Nevermind. Missed the part in the HOWTO about opening all traffic to br0 and tap0 using iptables. Fixed now.

---

