---
title: "IPsec site to site"
date: 2011-03-10
forum: Networking &amp; Wireless
---

### Post by iljab on 2011-03-10
[SIZE=2][COLOR=black]Hi all,[/COLOR][/SIZE]
 
[SIZE=2][COLOR=black]I want to have a site to site connection between two internal networks.[/COLOR][/SIZE]
 
[SIZE=2][COLOR=black]I have 2 locations with 2 different IPs (internal and external) and on both locations I have 1 ubuntu server.[/COLOR][/SIZE]
[SIZE=2][COLOR=black]On the first location with ip: 216.121.38.107 i have no router and this works well.[/COLOR][/SIZE]
 
[COLOR=black][SIZE=2]On the second location [COLOR=#1f497d][FONT=Calibri][FONT=Verdana][COLOR=black]61.133.237.165 i have the ubuntu server connected behind a Speedtouch adsl modem[/COLOR]. [/FONT][/FONT][/COLOR][/SIZE][/COLOR]
 
[COLOR=#1f497d][FONT=Calibri][FONT=Verdana][SIZE=2][COLOR=black]When i start IPsec the server with ip [/COLOR][COLOR=black][COLOR=#1f497d][FONT=Calibri][COLOR=black]61.133.237.165 I can get into the local network of 216.121.38.107[/COLOR]. [/FONT][/COLOR][/COLOR][/SIZE][/FONT][/FONT][/COLOR]
 
[COLOR=#1f497d][FONT=Calibri][COLOR=#1f497d][FONT=Calibri][FONT=Verdana][SIZE=2][COLOR=black]Only not backwords the 216.121.38.107 cannot get in the [COLOR=#1f497d][FONT=Calibri][COLOR=black]61.133.237.165[/COLOR][/FONT][/COLOR] location.[/COLOR][/SIZE][/FONT][/FONT][/COLOR][/FONT][/COLOR]
[COLOR=#1f497d][FONT=Calibri][COLOR=#1f497d][FONT=Calibri][FONT=Verdana][SIZE=2][COLOR=black]Here are my Openswan IPsec config files for both sides:[/COLOR][/SIZE][/FONT][/FONT][/COLOR][/FONT][/COLOR]
 
[COLOR=#1f497d][FONT=Calibri][COLOR=#1f497d][FONT=Calibri][FONT=Verdana][SIZE=2][COLOR=black]Location: 216.121.38.107[/COLOR][/SIZE][/FONT][/FONT][/COLOR][/FONT][/COLOR]
```

[COLOR=#1f497d][FONT=Calibri][COLOR=#1f497d][FONT=Calibri][FONT=Verdana][SIZE=2][COLOR=black]conn vpn[/COLOR][/SIZE][/FONT]
[SIZE=2][FONT=Calibri][COLOR=#1f497d]  left=[FONT=Verdana]61.133.237.165[/FONT][/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Calibri][COLOR=#1f497d]  leftsubnet=192.168.2.0/24[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Calibri][COLOR=#1f497d]  leftsourceip=192.168.2.4[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Calibri][COLOR=#1f497d]  leftnexthop=192.168.1.1[/COLOR][/FONT][/SIZE]
[FONT=Verdana][SIZE=2][COLOR=black]leftid=@olifant[/COLOR][/SIZE][/FONT]
[FONT=Verdana][SIZE=2][COLOR=black]  leftrsasigkey=0sAwEAAeSePhzkkj3ccC6R6IHd5kSWEImKDURKKIeMpTcykvni34ju+3u3coxKVirkZBLe$[/COLOR][/SIZE][/FONT][/FONT][/COLOR][/FONT][/COLOR]
[COLOR=#1f497d][FONT=Calibri][COLOR=#1f497d][FONT=Calibri][FONT=Verdana][SIZE=2][COLOR=black]  right=216.121.38.107[/COLOR][/SIZE][/FONT]
[SIZE=2][FONT=Calibri][COLOR=#1f497d]  rightsubnet=192.168.1.0/24[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Calibri][COLOR=#1f497d]  rightsourceip=[/COLOR][/FONT][/SIZE][/FONT][/COLOR][/FONT][/COLOR][COLOR=#1f497d][FONT=Calibri][COLOR=#1f497d][FONT=Calibri][SIZE=2][FONT=Calibri][COLOR=#1f497d][FONT=Verdana]216.121.38.107[/FONT][/COLOR][/FONT][/SIZE][/FONT][/COLOR][/FONT][/COLOR][COLOR=#1f497d][FONT=Calibri][COLOR=#1f497d][FONT=Calibri]
[SIZE=2][FONT=Calibri][COLOR=#1f497d]  rightnexthop=192.168.2.4[/COLOR][/FONT][/SIZE]
[FONT=Verdana][SIZE=2][COLOR=black]rightid=@server[/COLOR][/SIZE][/FONT]
[FONT=Verdana][SIZE=2][COLOR=black]  rightrsasigkey=0sAQO3TBxQs/oh6XyjmJAw/J91VHrMapXd2+bGyml5dvNhYMXCuzMMLHeA0pvCn9R8IMm$[/COLOR][/SIZE][/FONT][/FONT][/COLOR][/FONT][/COLOR]

```[COLOR=#1f497d][FONT=Calibri][COLOR=#1f497d][FONT=Calibri][FONT=Verdana][SIZE=2][COLOR=black]Location: 61.133.237.165[/COLOR][/SIZE][/FONT][/FONT][/COLOR][/FONT][/COLOR]
```

[COLOR=#1f497d][FONT=Calibri][COLOR=#1f497d][FONT=Calibri][FONT=Verdana][SIZE=2][COLOR=black]conn vpn[/COLOR][/SIZE][/FONT]
[SIZE=2][FONT=Calibri][COLOR=#1f497d]  left=192.168.2.4[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Calibri][COLOR=#1f497d]  leftsubnet=192.168.2.0/24[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Calibri][COLOR=#1f497d]  leftsourceip=192.168.2.4[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Calibri][COLOR=#1f497d]  leftnexthop=[FONT=Verdana]216.121.38.107[/FONT][/COLOR][/FONT][/SIZE]
[FONT=Verdana][SIZE=2][COLOR=black]leftid=@olifant[/COLOR][/SIZE][/FONT]
[FONT=Verdana][SIZE=2][COLOR=black]  leftrsasigkey=0sAwEAAeSePhzkkj3ccC6R6IHd5kSWEImKDURKKIeMpTcykvni34ju+3u3coxKVi$[/COLOR][/SIZE][/FONT][/FONT][/COLOR][/FONT][/COLOR]
[COLOR=#1f497d][FONT=Calibri][COLOR=#1f497d][FONT=Calibri][FONT=Verdana][SIZE=2][COLOR=black]  right=216.121.38.107[/COLOR][/SIZE][/FONT]
[SIZE=2][FONT=Calibri][COLOR=#1f497d]  rightsubnet=192.168.1.0/24[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Calibri][COLOR=#1f497d]  rightsourceip=192.168.1.1[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Calibri][COLOR=#1f497d]  rightnexthop=192.168.2.4[/COLOR][/FONT][/SIZE]
[FONT=Verdana][SIZE=2][COLOR=black]rightid=@server[/COLOR][/SIZE][/FONT]
[FONT=Verdana][SIZE=2][COLOR=black]  rightrsasigkey=0sAQO3TBxQs/oh6XyjmJAw/J91VHrMapXd2+bGyml5dvNhYMXCuzMMLHeA0pvCn$[/COLOR][/SIZE][/FONT][/FONT][/COLOR][/FONT][/COLOR]

``` 
[COLOR=#1f497d][FONT=Calibri][COLOR=#1f497d][FONT=Calibri][FONT=Verdana][SIZE=2][COLOR=black]And this when it starts on 61.133.237.165:[/COLOR][/SIZE][/FONT][/FONT][/COLOR][/FONT][/COLOR]
```

[COLOR=#1f497d][FONT=Calibri][COLOR=#1f497d][FONT=Calibri][FONT=Verdana][SIZE=2][COLOR=black]root@olifant[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2][COLOR=black]:~# sudo ipsec auto --add vpn[/COLOR][/SIZE][/FONT]
[FONT=Verdana][SIZE=2][COLOR=black]root@olifant[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2][COLOR=black]:~# ipsec auto --up vpn[/COLOR][/SIZE][/FONT]
[SIZE=2][FONT=Verdana][COLOR=black]104 "vpn" #37: STATE_MAIN_I1: initiate[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Verdana][COLOR=black]003 "vpn" #37: ignoring unknown Vendor ID payload [4f456d406b6753464548407f][/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Verdana][COLOR=black]003 "vpn" #37: received Vendor ID payload [Dead Peer Detection][/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Verdana][COLOR=black]003 "vpn" #37: received Vendor ID payload [RFC 3947] method set to=109[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Verdana][COLOR=black]106 "vpn" #37: STATE_MAIN_I2: sent MI2, expecting MR2[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Verdana][COLOR=black]003 "vpn" #37: NAT-Traversal: Result using RFC 3947 (NAT-Traversal): i am NATed[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Verdana][COLOR=black]108 "vpn" #37: STATE_MAIN_I3: sent MI3, expecting MR3[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Verdana][COLOR=black]003 "vpn" #37: received Vendor ID payload [CAN-IKEv2][/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Verdana][COLOR=black]004 "vpn" #37: STATE_MAIN_I4: ISAKMP SA established {auth=OAKLEY_RSA_SIG cipher=aes_128 prf=oakley_sha group=modp2048}[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Verdana][COLOR=black]117 "vpn" #38: STATE_QUICK_I1: initiate[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Verdana][COLOR=black]004 "vpn" #38: STATE_QUICK_I2: sent QI2, IPsec SA established tunnel mode {ESP=>0xceaf0f84 <0x1b41ad67 xfrm=AES_128-HMAC_SHA1 NATOA=none NATD=none DPD=none}[/COLOR][/FONT][/SIZE]
[FONT=Verdana][SIZE=2][COLOR=black]root@olifant[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2][COLOR=black]:~# ping 192.168.1.3[/COLOR][/SIZE][/FONT]
[SIZE=2][FONT=Verdana][COLOR=black]PING 192.168.1.3 (192.168.1.3) 56(84) bytes of data.[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Verdana][COLOR=black]64 bytes from 192.168.1.3: icmp_seq=1 ttl=127 time=42.8 ms[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Verdana][COLOR=black]64 bytes from 192.168.1.3: icmp_seq=2 ttl=127 time=64.2 ms[/COLOR][/FONT][/SIZE]
[/FONT][/COLOR][/FONT][/COLOR]
```[COLOR=black][FONT=Verdana][SIZE=2][COLOR=#1f497d][FONT=Calibri][COLOR=#1f497d][FONT=Calibri][COLOR=black]And this when it starts on[/COLOR][/FONT][/COLOR][/FONT][/COLOR] 216.121.38.107[/SIZE][/FONT][/COLOR]
```

[SIZE=2][COLOR=black]root@server[/COLOR][/SIZE][SIZE=2][COLOR=black]:~# sudo ipsec auto --add vpn[/COLOR][/SIZE]
[SIZE=2][COLOR=black]root@server[/COLOR][/SIZE][SIZE=2][COLOR=black]:~# ipsec auto --up vpn[/COLOR][/SIZE]
[SIZE=2][COLOR=black]104 "vpn" #60: STATE_MAIN_I1: initiate[/COLOR][/SIZE]
[SIZE=2][COLOR=black]003 "vpn" #60: ignoring unknown Vendor ID payload [4f45504b7e7a764d4e645f57][/COLOR][/SIZE]
[SIZE=2][COLOR=black]003 "vpn" #60: received Vendor ID payload [Dead Peer Detection][/COLOR][/SIZE]
[SIZE=2][COLOR=black]003 "vpn" #60: received Vendor ID payload [RFC 3947] method set to=109[/COLOR][/SIZE]
[SIZE=2][COLOR=black]106 "vpn" #60: STATE_MAIN_I2: sent MI2, expecting MR2[/COLOR][/SIZE]
[SIZE=2][COLOR=black]003 "vpn" #60: NAT-Traversal: Result using RFC 3947 (NAT-Traversal): peer is NATed[/COLOR][/SIZE]
[SIZE=2][COLOR=black]108 "vpn" #60: STATE_MAIN_I3: sent MI3, expecting MR3[/COLOR][/SIZE]
[SIZE=2][COLOR=black]003 "vpn" #60: received Vendor ID payload [CAN-IKEv2][/COLOR][/SIZE]
[SIZE=2][COLOR=black]004 "vpn" #60: STATE_MAIN_I4: ISAKMP SA established {auth=OAKLEY_RSA_SIG cipher=aes_128 prf=oakley_sha group=modp2048}[/COLOR][/SIZE]
[SIZE=2][COLOR=black]117 "vpn" #61: STATE_QUICK_I1: initiate[/COLOR][/SIZE]
[SIZE=2][COLOR=black]004 "vpn" #61: STATE_QUICK_I2: sent QI2, IPsec SA established tunnel mode {ESP=>0xc5c86af4 <0x653ea50f xfrm=AES_128-HMAC_SHA1 NATOA=none NATD=61.133.237.165:4500 DPD=none}[/COLOR][/SIZE]
[SIZE=2][COLOR=black]root@server[/COLOR][/SIZE][SIZE=2][COLOR=black]:~# ping 192.168.2.4[/COLOR][/SIZE]
[SIZE=2][COLOR=black]PING 192.168.2.4 (192.168.2.4) 56(84) bytes of data.[/COLOR][/SIZE]
[SIZE=2][COLOR=black]^C[/COLOR][/SIZE]
[SIZE=2][COLOR=black]--- 192.168.2.4 ping statistics ---[/COLOR][/SIZE]
[SIZE=2][COLOR=black]4 packets transmitted, 0 received, 100% packet loss, time 3017ms[/COLOR][/SIZE]

```[COLOR=#1f497d][FONT=Calibri][COLOR=#1f497d][FONT=Calibri][FONT=Verdana][SIZE=2][COLOR=black]I have forwarded the port 500 on my speedtouch modem to olifant [/COLOR][/SIZE][/FONT][/FONT][/COLOR][/FONT][/COLOR]

---

