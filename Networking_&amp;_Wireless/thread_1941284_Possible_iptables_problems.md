---
title: "Possible iptables problems"
date: 2012-03-15
forum: Networking &amp; Wireless
---

### Post by Go3Team on 2012-03-15
Yesterday, my asterisk server quit connecting to my voip provider.  I'm not sure what caused the problem, but it now won't connect.  I've tried connecting to the provider from another computer on the network and that won't connect either.  I have a mirror of the router the network is using, and I switched the routers out and now it works.  I've cut down the rules on the problem router to bare minimum and still nothing.  I did some packet sniffing with Wireshark and it appears there were some Code 3"No Route To Host" & Code 3 Port Unreachable errors, however I can ping it with no problem.  


Maybe someone can make sense of these as well:


```
Mar 15 09:16:47 s_all@router kernel: [ 1676.777971] BANDWIDTH_OUT:IN=eth1 OUT=eth0 SRC=xxx DST=yyy LEN=84 TOS=0x00 PREC=0x00 TTL=63 ID=0 DF PROTO=ICMP TYPE=8 CODE=0 ID=5396 SEQ=1 
Mar 15 09:16:47 s_all@router kernel: [ 1676.815261] BANDWIDTH_IN:IN=eth0 OUT=eth1 SRC=yyy DST=xxx LEN=84 TOS=0x00 PREC=0x20 TTL=54 ID=24046 PROTO=ICMP TYPE=0 CODE=0 ID=5396 SEQ=1 
Mar 15 09:16:48 s_all@router kernel: [ 1677.778207] BANDWIDTH_OUT:IN=eth1 OUT=eth0 SRC=xxx DST=yyy LEN=84 TOS=0x00 PREC=0x00 TTL=63 ID=0 DF PROTO=ICMP TYPE=8 CODE=0 ID=5396 SEQ=2 
Mar 15 09:16:48 s_all@router kernel: [ 1677.804192] BANDWIDTH_IN:IN=eth0 OUT=eth1 SRC=yyy DST=xxx LEN=84 TOS=0x00 PREC=0x20 TTL=54 ID=24047 PROTO=ICMP TYPE=0 CODE=0 ID=5396 SEQ=2 
Mar 15 09:16:49 s_all@router kernel: [ 1678.779156] BANDWIDTH_OUT:IN=eth1 OUT=eth0 SRC=xxx DST=yyy LEN=84 TOS=0x00 PREC=0x00 TTL=63 ID=0 DF PROTO=ICMP TYPE=8 CODE=0 ID=5396 SEQ=3 
Mar 15 09:16:49 s_all@router kernel: [ 1678.807371] BANDWIDTH_IN:IN=eth0 OUT=eth1 SRC=yyy DST=xxx LEN=84 TOS=0x00 PREC=0x20 TTL=54 ID=24048 PROTO=ICMP TYPE=0 CODE=0 ID=5396 SEQ=3 
Mar 15 09:35:06 s_all@router kernel: [ 2776.009908] BANDWIDTH_OUT:IN=eth1 OUT=eth0 SRC=xxx DST=yyy LEN=84 TOS=0x00 PREC=0x00 TTL=63 ID=0 DF PROTO=ICMP TYPE=8 CODE=0 ID=16925 SEQ=1 
Mar 15 09:35:06 s_all@router kernel: [ 2776.038869] BANDWIDTH_IN:IN=eth0 OUT=eth1 SRC=yyy DST=xxx LEN=84 TOS=0x00 PREC=0x20 TTL=54 ID=46854 PROTO=ICMP TYPE=0 CODE=0 ID=16925 SEQ=1 
Mar 15 09:35:07 s_all@router kernel: [ 2777.010512] BANDWIDTH_OUT:IN=eth1 OUT=eth0 SRC=xxx DST=yyy LEN=84 TOS=0x00 PREC=0x00 TTL=63 ID=0 DF PROTO=ICMP TYPE=8 CODE=0 ID=16925 SEQ=2 
Mar 15 09:35:07 s_all@router kernel: [ 2777.035075] BANDWIDTH_IN:IN=eth0 OUT=eth1 SRC=yyy DST=xxx LEN=84 TOS=0x00 PREC=0x20 TTL=54 ID=46855 PROTO=ICMP TYPE=0 CODE=0 ID=16925 SEQ=2 

```

Thanks.

---

