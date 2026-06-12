---
title: "bridge routing problem"
date: 2012-03-06
forum: Networking &amp; Wireless
---

### Post by okinobk on 2012-03-06
Hello,
  I have one virtual host server with KVM and Cloudmin (ubuntu server  11.04) with many guests system (also ubuntu server). On host I installed  OpenVPN server (with working routing local network to vpn client).
  From vpn client I can make any connection to virtual guests without  problems, but only one guest is problem. I can ping (icmp)  it but can't make any other network (tcp or udp) connection.


  So I try to debug it and check network transfer in virtual host and get this:


  TEST SSH from VPN client to working virtual guests
  Jan 28 19:51:36 virthost kernel: [7680080.105160] IN=tun0 OUT=br1  SRC=10.8.3.6 DST=192.168.3.8 LEN=56 TOS=0x00 PREC=0x00 TTL=63 ID=16872  DF PROTO=TCP SPT=55065 DPT=22 WINDOW=5840 RES=0x00 SYN URGP=0
Jan 28 19:51:36 virthost kernel: [7680080.105303] IN=br1 OUT=tun0  PHYSIN=tap5 SRC=192.168.3.8 DST=10.8.3.6 LEN=40 TOS=0x00 PREC=0x00  TTL=63 ID=0 DF PROTO=TCP SPT=22 DPT=55065 WINDOW=0 RES=0x00 ACK RST  URGP=0


  TEST SSH from VPN client to problem virtual guests
  Jan 28 19:51:54 virthost kernel: [7680097.630987] IN=tun0 OUT=br1  SRC=10.8.3.6 DST=192.168.3.251 LEN=56 TOS=0x00 PREC=0x00 TTL=63 ID=32723  DF PROTO=TCP SPT=56350 DPT=22 WINDOW=5840 RES=0x00 SYN URGP=0
Jan 28 19:51:54 virthost kernel: [7680097.631224] IN=br1 OUT=br1  PHYSIN=tap0 PHYSOUT=eth1 SRC=192.168.3.251 DST=10.8.3.6 LEN=40 TOS=0x00  PREC=0x00 TTL=64 ID=0 DF PROTO=TCP SPT=22 DPT=56350 WINDOW=0 RES=0x00  ACK RST URGP=0


  TEST PING from VPN client to working virtual guest
  Jan 28 21:29:31 virthost kernel: [7685954.655049] IN=tun0 OUT=br1  SRC=10.8.3.6 DST=192.168.3.8 LEN=84 TOS=0x00 PREC=0x00 TTL=63 ID=0 DF  PROTO=ICMP TYPE=8 CODE=0 ID=2025 SEQ=3
Jan 28 21:29:31 virthost kernel: [7685954.655218] IN=br1 OUT=tun0  PHYSIN=tap5 SRC=192.168.3.8 DST=10.8.3.6 LEN=84 TOS=0x00 PREC=0x00  TTL=63 ID=39056 PROTO=ICMP TYPE=0 CODE=0 ID=2025 SEQ=3


  TEST PING from VPN client to problem virtual guest
  Jan 28 21:26:24 virthost kernel: [7685767.387514] IN=tun0 OUT=br1  SRC=10.8.3.6 DST=192.168.3.251 LEN=84 TOS=0x00 PREC=0x00 TTL=63 ID=0 DF  PROTO=ICMP TYPE=8 CODE=0 ID=2017 SEQ=3
Jan 28 21:26:24 virthost kernel: [7685767.387700] IN=br1 OUT=br1  PHYSIN=tap0 PHYSOUT=eth1 SRC=192.168.3.251 DST=10.8.3.6 LEN=84 TOS=0x00  PREC=0x00 TTL=64 ID=39097 PROTO=ICMP TYPE=0 CODE=0 ID=2017 SEQ=3
Jan 28 21:26:24 virthost kernel: [7685767.387861] IN=br1 OUT=tun0  PHYSIN=eth1 SRC=192.168.3.251 DST=10.8.3.6 LEN=84 TOS=0x00 PREC=0x00  TTL=62 ID=39097 PROTO=ICMP TYPE=0 CODE=0 ID=2017 SEQ=3


  Please help. Thank You.

---

