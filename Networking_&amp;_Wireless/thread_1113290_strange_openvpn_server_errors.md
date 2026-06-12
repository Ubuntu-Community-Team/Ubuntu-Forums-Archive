---
title: "strange openvpn server errors"
date: 2009-04-01
forum: Networking &amp; Wireless
---

### Post by andrewftw on 2009-04-01
Hi there,

When I start up openvpn (successfully) my openvpn.log shows the following errors:

Wed Apr  1 11:32:10 2009 us=626231 SCHEDULE: schedule_find_least NULL
Wed Apr  1 11:32:20 2009 us=626534 MULTI: REAP range 112 -> 128
Wed Apr  1 11:32:20 2009 us=626606 MULTI TCP: multi_tcp_action a=TA_TIMEOUT p=0
Wed Apr  1 11:32:20 2009 us=626621 MULTI TCP: multi_tcp_dispatch a=TA_TIMEOUT mi=0x00000000
Wed Apr  1 11:32:20 2009 us=626636 MULTI TCP: multi_tcp_post TA_TIMEOUT -> TA_UNDEF
Wed Apr  1 11:32:20 2009 us=626650 SCHEDULE: schedule_find_least NULL

When I try to connect with my client I get this:

Wed Apr  1 12:21:28 2009 us=164376 myip:49344 TCPv4_SERVER READ [42] from myip:49344: P_CONTROL_HARD_RESET_CLIENT_V2 kid=0 sid=e21bca5b de2fe979 tls_hmac=e45b7524 2a1097fa b53944f7 ea012b89 ef5c9f3c pid=[ #1 / time = (1238613411) Wed Apr  1 12:16:51 2009 ] [ ] pid=0 DATA 
Wed Apr  1 12:21:28 2009 us=164396 myip:49344 TLS: control channel, op=P_CONTROL_HARD_RESET_CLIENT_V2, IP=myip:49344
Wed Apr  1 12:21:28 2009 us=164425 myip:49344 TLS: initial packet test, i=0 state=S_PRE_START, mysid=c573a1d5 eed06a76, rec-sid=e21bca5b de2fe979, rec-ip=myip:49344, stored-sid=00000000 00000000, stored-ip=myip:49344
Wed Apr  1 12:21:28 2009 us=164452 myip:49344 TLS: initial packet test, i=1 state=S_INITIAL, mysid=74b2d6c6 d57461a3, rec-sid=e21bca5b de2fe979, rec-ip=myip:49344, stored-sid=00000000 00000000, stored-ip=[undef]
Wed Apr  1 12:21:28 2009 us=164485 myip:49344 TLS: initial packet test, i=2 state=S_UNDEF, mysid=00000000 00000000, rec-sid=e21bca5b de2fe979, rec-ip=myip:49344, stored-sid=00000000 00000000, stored-ip=[undef]
Wed Apr  1 12:21:28 2009 us=164506 myip:49344 TLS: Initial packet from myip:49344, sid=e21bca5b de2fe979
Wed Apr  1 12:21:28 2009 us=164526 myip:49344 Authenticate/Decrypt packet error: packet HMAC authentication failed
Wed Apr  1 12:21:28 2009 us=164543 myip:49344 TLS Error: incoming packet authentication failed from myip:49344
Wed Apr  1 12:21:28 2009 us=164572 myip:49344 TLS: tls_multi_process: i=0 state=S_PRE_START, mysid=c573a1d5 eed06a76, stored-sid=00000000 00000000, stored-ip=myip:49344
Wed Apr  1 12:21:28 2009 us=164587 myip:49344 TLS: tls_process: chg=0 ks=S_PRE_START lame=S_UNDEF to_link->len=0 wakeup=604800
Wed Apr  1 12:21:28 2009 us=164603 myip:49344 ACK reliable_can_send active=1 current=0 : [1] 0
Wed Apr  1 12:21:28 2009 us=164632 myip:49344 ACK reliable_send_timeout 2 [1] 0
Wed Apr  1 12:21:28 2009 us=164646 myip:49344 TLS: tls_process: timeout set to 2
Wed Apr  1 12:21:28 2009 us=164668 myip:49344 TLS: tls_multi_process: i=1 state=S_INITIAL, mysid=74b2d6c6 d57461a3, stored-sid=00000000 00000000, stored-ip=[undef]
Wed Apr  1 12:21:28 2009 us=164710 myip:49344 TLS: tls_multi_process: i=2 state=S_UNDEF, mysid=00000000 00000000, stored-sid=00000000 00000000, stored-ip=[undef]
Wed Apr  1 12:21:28 2009 us=164727 myip:49344 Fatal TLS error (check_tls_errors_co), restarting
Wed Apr  1 12:21:28 2009 us=164743 myip:49344 SIGUSR1[soft,tls-error] received, client-instance restarting

No luck from google, any one see this before?

---

### Post by andrewftw on 2009-04-01
BTW I checked the md5sum on the ta.key and they are the same on both the client and server.

---

### Post by andrewftw on 2009-04-02
I'm able to connect to the vpn now but it drops my internet connection.  Also the openvpn.lon file is constantly running:

Thu Apr  2 14:59:27 2009 us=430097  read from TUN/TAP returned 60
Thu Apr  2 14:59:27 2009 us=430111 MULTI TCP: multi_tcp_post TA_TUN_READ -> TA_UNDEF
Thu Apr  2 14:59:27 2009 us=430124 SCHEDULE: schedule_find_least NULL
Thu Apr  2 14:59:27 2009 us=646977 EP_WAIT[0] rwflags=0x0001 ev=0x00000001 arg=0x00000
002
Thu Apr  2 14:59:27 2009 us=646994 MULTI TCP: multi_tcp_action a=TA_TUN_READ p=0
Thu Apr  2 14:59:27 2009 us=647007 MULTI TCP: multi_tcp_dispatch a=TA_TUN_READ mi=0x00
000000

to the point of making a huge log file.

---

