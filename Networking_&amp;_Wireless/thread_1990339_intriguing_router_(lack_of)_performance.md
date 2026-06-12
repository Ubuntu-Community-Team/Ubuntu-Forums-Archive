---
title: "intriguing router (lack of) performance"
date: 2012-05-29
forum: Networking &amp; Wireless
---

### Post by berlusconi on 2012-05-29
Hi all,  I have a home network going through an Ubuntu router. I am failing to download a TV show using rtmpdump.  Issuing ```
 rtmpdump -r "rtmpe://big02.mediadirect.ro:1935/recb1?id=65635241" -a "recb1?id=65635241" -f "WIN 11,2,202,235" -W "http://static1.mediadirect.ro/player-preload/swf/b1_1_1002/player.swf?app=FlUZRhMBChBU&data=D1Q7WA==&str=X1VVW05UXF1XW1sAFVBTAwUHEQwWK19VVVtMVFxfV1srX1ZJWVFJWUI6DxsaSwkZVQ==" -p "http://inregistrari.b1.ro/view-lumea_lui_banciu-85.html" -C O:1 -C O:0 -y "2012/05/28/mp4:banciu_2012-05-28_23-00-00_low.mp4" -o mp4_banciu_2012-05-28_23-00-00_low.flv  
``` fails everytime I routed my request through any of my computers in the home network. Heck, it fails even on the router.  It fails using either of two different network card. It fails when the computers in the home network are tunnelled through OpenVPN.  In contrast, it works when I launch the same command from Windows computers that above were described as failing. The only way it works is if they go on a different network, or if I plug them in the Ethernet outlet which normally hooks the Ubuntu router to the Internet.  The error is ```
ERROR: RTMP_ReadPacket, failed to read RTMP packet body.
``` Ufw is stopped, pgl is stopped, dns is 8.8.8.8, but I still suspect it must be some firewall-like filter in Ubuntu. It may be even some sort of limiting capacity, low RAM or similar.  Do you have any suspects?

---

