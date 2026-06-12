---
title: "ESP fails for openswan"
date: 2010-04-09
forum: Networking &amp; Wireless
---

### Post by who_cares on 2010-04-09
Hey everyone,
I'm trying to set up an ipsec/l2tp VPN using openswan, xl2tpd, and ppp.
Right now I can get a client to connect to the gateway but the ESP fails as it negotiates the connection.
I have the output from tcpdump as it tries to negotiate:
> 10:22:21.858680 IP rpi-wl-854.dynamic.rpi.edu.ipsec-msft > cpe-72-231-173-41.nycap.res.rr.com.ipsec-msft: UDP-encap: ESP(spi=0xd3d21a1d,seq=0x5), length 116
10:22:26.513637 IP cpe-72-231-173-41.nycap.res.rr.com.ipsec-msft > rpi-wl-854.dynamic.rpi.edu.ipsec-msft: isakmp-nat-keep-alive
10:22:26.513829 IP cpe-72-231-173-41.nycap.res.rr.com.ipsec-msft > rpi-wl-854.dynamic.rpi.edu.ipsec-msft: isakmp-nat-keep-alive
10:22:26.926735 IP rpi-wl-854.dynamic.rpi.edu.ipsec-msft > cpe-72-231-173-41.nycap.res.rr.com.ipsec-msft: isakmp-nat-keep-alive
10:22:27.367866 IP rpi-wl-854.dynamic.rpi.edu.ipsec-msft > cpe-72-231-173-41.nycap.res.rr.com.ipsec-msft: NONESP-encap: isakmp: phase 2/others I inf[E]
10:22:27.368599 IP rpi-wl-854.dynamic.rpi.edu.ipsec-msft > cpe-72-231-173-41.nycap.res.rr.com.ipsec-msft: NONESP-encap: isakmp: phase 2/others I inf[E]
10:22:27.401024 IP cpe-72-231-173-41.nycap.res.rr.com.ipsec-msft > rpi-wl-854.dynamic.rpi.edu.ipsec-msft: NONESP-encap: isakmp: phase 2/others R inf[E]
10:22:27.408485 IP cpe-72-231-173-41.nycap.res.rr.com.ipsec-msft > rpi-wl-854.dynamic.rpi.edu.ipsec-msft: NONESP-encap: isakmp: phase 2/others R inf[E]
Has anyone ever encountered this problem or does anyone know how to fix it?

---

### Post by who_cares on 2010-04-12
bump

---

