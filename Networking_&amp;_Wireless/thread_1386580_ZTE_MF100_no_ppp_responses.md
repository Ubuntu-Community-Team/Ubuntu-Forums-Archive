---
title: "ZTE MF100: no ppp responses"
date: 2010-01-20
forum: Networking &amp; Wireless
---

### Post by jamapii on 2010-01-20
Hi,

connect '/usr/sbin/chat -t 8 -v ABORT BUSY ABORT ERROR ABORT "NO CARRIER" "" AT OK-AT-OK ATZ OK AT+ZCDRUN=9 :1 "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0" OK AT+CGDCONT=1,,\\"internet\\" OK "ATDT*99#" CONNECT'

I'm using this chat script in ppp-options, and it succeeds (only for the first time after plugging in). Then, ppp starts sending packets and gets no response.

Jan 21 03:06:08 laptop10 chat[16823]: CONNECT
Jan 21 03:06:08 laptop10 chat[16823]:  -- got it
Jan 21 03:06:08 laptop10 pppd[16822]: Serial connection established.
Jan 21 03:06:08 laptop10 pppd[16822]: using channel 2
Jan 21 03:06:08 laptop10 pppd[16822]: Using interface ppp0
Jan 21 03:06:08 laptop10 pppd[16822]: Connect: ppp0 <--> /dev/ttyUSB1
Jan 21 03:06:09 laptop10 pppd[16822]: sent [LCP ConfReq id=0x1 <asyncmap 0x0>]
...

Other connect scripts, baud rates, ZDRUN=8 etc. make no difference.

It works in Windows, but with special software, I couldn't extract any information yet except that the GUI claims there is an option to run either PPP or IP over GPRS. The option is on IP! as if IP is directly run over the serial emulation, without PPP, but the ipconfig output mentions PPP in the adapter name.

What is happening there, does it work for anyone, what options or chat scripts or whatever might work?

---

