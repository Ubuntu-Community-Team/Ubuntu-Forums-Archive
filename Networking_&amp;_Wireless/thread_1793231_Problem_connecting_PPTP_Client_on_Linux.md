---
title: "Problem connecting PPTP Client on Linux"
date: 2011-06-29
forum: Networking &amp; Wireless
---

### Post by muradcsc on 2011-06-29
[FONT=Calibri][SIZE=3]Hi all[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]I am trying to connect my pptp client Linux to a pptp Linux server using modem but no success. I can only tweak ppp linux side[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Observing the following log I found it’s due to MPPE Support configuration mismatch in pppd, pppd (linux client) is refusing to accept MPPE encryption. [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Can anyone tell me to have that support what to do??[/SIZE][/FONT]
pppd[24545]: pppd 2.4.5 started by root, uid 0
chat[24547]: abort on (NO CARRIER)
chat[24547]: abort on (NO DIALTONE)
chat[24547]: abort on (ERROR)
chat[24547]: abort on (NO ANSWER)
chat[24547]: abort on (BUSY)
chat[24547]: send (++++++++++++++++++++++++++++++++++++++++++++++++++++^M)
chat[24547]: send (++++++++++++++++++++++++++++++++++++++++++++++++++++^M)
chat[24547]: send (+++AT^M)
chat[24547]: send (ATHn^M)
chat[24547]: expect (OK)
chat[24547]: ^M^MAT^M^M
chat[24547]: OK
chat[24547]: -- got it
chat[24547]: send (AT&D2^M)
chat[24547]: expect (OK)
chat[24547]: ^M
chat[24547]: ATHn^M^M
chat[24547]: OK
chat[24547]: -- got it
chat[24547]: send (AT&K3^M)
chat[24547]: expect (OK)
chat[24547]: ^M
chat[24547]: AT&D2^M^M
chat[24547]: OK
chat[24547]: -- got it
chat[24547]: send (AT+CBST=71,0,1^M)
chat[24547]: send (AT+CLCC?^M)
chat[24547]: expect (+CLCC:006)
chat[24547]: ^M
chat[24547]: AT&K3^M^M
chat[24547]: OK^M
chat[24547]: AT+CBST=71,0,1^M^M
chat[24547]: OK^M
chat[24547]: AT+CLCC?^M^M
chat[24547]: +CLCC:006
chat[24547]: -- got it
chat[24547]: send (^M)
chat[24547]: timeout set to 100 seconds
chat[24547]: expect (OK)
chat[24547]: ^M
chat[24547]: ^M
chat[24547]: 000^M
chat[24547]: ^M
chat[24547]: OK
chat[24547]: -- got it
chat[24547]: send (ATDT XXXXXXXXXXXX^M)
chat[24547]: expect (CONNECT 19200)
chat[24547]: ^M
chat[24547]: ^MATDT 008816000025^M^M
chat[24547]: CONNECT 19200
chat[24547]: -- got it
chat[24547]: send ()
pppd[24545]: Script /usr/sbin/chat -v -f /etc/ppp/chat-modem1 finished (pid 24546), status = 0x0
pppd[24545]: Serial connection established.
pppd[24545]: using channel 19
pppd[24545]: Using interface ppp0
pppd[24545]: Connect: ppp0 <--> /dev/ttyS0
pppd[24545]: Warning - secret file /etc/ppp/pap-secrets has world and/or group access
pppd[24545]: sent [LCP ConfReq id=0x1 <asyncmap 0xa0000> <magic 0xd953febc> <pcomp> <accomp>]
pppd[24545]: rcvd [LCP ConfReq id=0x92 <asyncmap 0xa0000> <auth chap MD5> <magic 0x1e724e3e> <pcomp> <accomp>]
pppd[24545]: sent [LCP ConfNak id=0x92 <auth pap>]
pppd[24545]: rcvd [LCP ConfAck id=0x1 <asyncmap 0xa0000> <magic 0xd953febc> <pcomp> <accomp>]
pppd[24545]: rcvd [LCP ConfReq id=0x93 <asyncmap 0xa0000> <auth pap> <magic 0x1e724e3e> <pcomp> <accomp>]
pppd[24545]: sent [LCP ConfAck id=0x93 <asyncmap 0xa0000> <auth pap> <magic 0x1e724e3e> <pcomp> <accomp>]
pppd[24545]: Warning - secret file /etc/ppp/pap-secrets has world and/or group access
pppd[24545]: sent [PAP AuthReq id=0x1 user="abcd" password=<hidden>]
pppd[24545]: rcvd [PAP AuthAck id=0x1 ""]
pppd[24545]: PAP authentication succeeded
[COLOR=red]pppd[24545]: sent [CCP ConfReq id=0x1 <deflate 15> <deflate(old#) 15> <bsd v1 15>][/COLOR]
pppd[24545]: sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0>]
pppd[24545]: rcvd [IPCP ConfReq id=0x1 <addr 192.168.13.254>]
pppd[24545]: sent [IPCP ConfAck id=0x1 <addr 192.168.13.254>]
[COLOR=red]pppd[24545]: rcvd [CCP ConfReq id=0x1 <mppe -H -M -S -L -D +C>][/COLOR]
[COLOR=red]pppd[24545]: sent [CCP ConfRej id=0x1 <mppe -H -M -S -L -D +C>][/COLOR]
[COLOR=red]pppd[24545]: rcvd [CCP ConfRej id=0x1 <deflate 15> <deflate(old#) 15> <bsd v1 15>][/COLOR]
pppd[24545]: sent [CCP ConfReq id=0x2]
pppd[24545]: rcvd [IPCP ConfRej id=0x1 <compress VJ 0f 01>]
pppd[24545]: sent [IPCP ConfReq id=0x2 <addr 0.0.0.0>]
pppd[24545]: rcvd [CCP ConfReq id=0x2 < 17 06 00 01 02 00>]
pppd[24545]: sent [CCP ConfRej id=0x2 < 17 06 00 01 02 00>]
pppd[24545]: rcvd [CCP ConfAck id=0x2]
pppd[24545]: rcvd [IPCP ConfReq id=0x2 <addr 192.168.13.254>]
pppd[24545]: sent [IPCP ConfAck id=0x2 <addr 192.168.13.254>]
pppd[24545]: rcvd [IPCP ConfNak id=0x2 <addr 192.168.13.54>]
pppd[24545]: sent [IPCP ConfReq id=0x3 <addr 192.168.13.54>]
pppd[24545]: rcvd [CCP ConfReq id=0x3 < 11 05 00 01 01>]
pppd[24545]: sent [CCP ConfRej id=0x3 < 11 05 00 01 01>]
pppd[24545]: rcvd [IPCP ConfAck id=0x3 <addr 192.168.13.54>]
pppd[24545]: not replacing existing default route via 166.130.109.1
pppd[24545]: local IP address 192.168.13.54
pppd[24545]: remote IP address 192.168.13.254
pppd[24545]: Can't execute /etc/ppp/ip-up: Invalid argument
pppd[24545]: rcvd [CCP ConfReq id=0x4 < 11 05 00 01 03>]
pppd[24545]: sent [CCP ConfRej id=0x4 < 11 05 00 01 03>]
pppd[24545]: sent [CCP ConfReq id=0x2]
pppd[24545]: rcvd [CCP ConfReq id=0x5 <predictor 1>]
pppd[24545]: sent [CCP ConfRej id=0x5 <predictor 1>]
pppd[24545]: rcvd [CCP ConfAck id=0x2]
pppd[24545]: rcvd [CCP TermReq id=0x6]
pppd[24545]: sent [CCP TermAck id=0x6]
pppd[24545]: sent [CCP ConfReq id=0x2]
pppd[24545]: rcvd [CCP TermReq id=0x7]
pppd[24545]: sent [CCP TermAck id=0x7]
pppd[24545]: sent [CCP ConfReq id=0x2]
pppd[24545]: last message repeated 8 times
[COLOR=red]pppd[24545]: CCP: timeout sending Config-Requests[/COLOR]
 
Any Help will be appriciated.
 
Thanks 
 
Murad

---

### Post by amauk on 2011-06-29
quick google threw this up
[http://pptpclient.sourceforge.net/howto-diagnosis.phtml#ccp_confrej_deflate](http://pptpclient.sourceforge.net/howto-diagnosis.phtml#ccp_confrej_deflate)

Seems you need modify the client config to specify that MPPE is required

> Diagnosis: your pppd is suggesting only deflate and bsdcomp compression options, and not MPPE. The PPTP Server rejects the suggestions and disconnects.

Solution: make sure the require-mppe option is provided to the pppd command, such as in the options file. For versions of pppd prior to and including 2.4.0, provide the options mppe-40, mppe-128 and mppe-stateless. See also Why are the pppd options different?. Make sure the nobsdcomp and nodeflate options are provided, so that pppd does not suggest them.

---

