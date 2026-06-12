---
title: "GPRS - LCP terminated by peer"
date: 2010-11-20
forum: Networking &amp; Wireless
---

### Post by fanus on 2010-11-20
[COLOR=Blue]Greetings Friends, Unices, Countrymen,

I am trying to get pppd/chat working with an internal Wavecom modem, but PPP terminates with message "LCP terminated by peer".

But, same pppd/chat configuration is working on my own Linux OS with Huawei 3G modem.

I tried several options to get it working, but no luck.


The problem is happening during the PPP negotiation with the Modem:[/COLOR]
[FONT=Courier New]rcvd [LCP TermReq id=0x2]
LCP terminated by peer[/FONT]

[COLOR=Blue]But this only mean that there was a failure during PPP setup between Linux and the Modem.

I tested the modem with manual AT commands via minicom to further investigate to problem, but could not even activate the PDP context:

Modem is registered and attached to Vodacom's network:[/COLOR]
[FONT=Courier New]at+cops=?
+COPS: (2,"VodaCom-SA","VODA","65501"),(3,"MTN-SA","MTN","65510"),(3,"","","65502"),(3,"Cell C","C)

at+cops?                                                      
+COPS: 0,2,65501   

at+cgreg?
+CGREG: 0,1[/FONT]
[COLOR=Blue]

The signal level is very good (-113+2*22= -69 dBm)
[/COLOR][FONT=Courier New][COLOR=Black]at+csq
+CSQ: 22,0[/COLOR][/FONT]
[COLOR=Blue]
It is a Wavecom modem,  and supports only 900 and 1800 GSM/EDGE:[/COLOR]
[FONT=Courier New]at+cgmi                                                       
 WAVECOM MODEM                                                
at+cgmm
 MULTIBAND  900E  1800 [/FONT]
[COLOR=Blue]
Configure the PDP context for internet APN:[/COLOR]
[FONT=Courier New]at+cgdcont=1,"IP","internet"                                                       
OK       [/FONT]                                                                          
[COLOR=Blue]
The PDP context is currently deactivated:[/COLOR]
[FONT=Courier New]at+cgact?
+CGACT: 1,0
[/FONT][COLOR=Blue]
Request the modem to activate the PDP session without initiating PPP - unsuccessful:
[/COLOR][FONT=Courier New]at+cgact=1,1
[COLOR=Red]ERROR[/COLOR][/FONT]
[COLOR=Blue]This [COLOR=Red]**ERROR**[/COLOR] could be the root-cause.[/COLOR]

[COLOR=Blue]Test if the modem can start PPP - OK:
[/COLOR][FONT=Courier New]atd*99***1#
CONNECT 115200
~}#.!}!}!} }6}!}$}%}"}&} } } } }'}"}(}"}#}$.#&.~~}#.!}!}!} }6}!}$}%}"}&} } } } }'}"}(}"}#}$.#&~
[/FONT][COLOR=Blue]

The modem is therefore not able to connect to the network.    Maybe the USIM-card is not compatible with the GSM/EDGE modem?  Any other advice to further troubleshoot the problem?

Can anybody please assist?

_pppd debug stdout:_[/COLOR]
[FONT=Courier New]root@ubuntu:/etc/ppp/peers# pppd call vodacom
ATZ
OK
AT
OK
ATE0V1
OK

OK

CONNECTScript /usr/sbin/chat -V -f /etc/ppp/chat/vodacom finished (pid 4371), status = 0x0
Serial connection established.
using channel 50
Using interface ppp0
Connect: ppp0 <--> /dev/ttyACM0
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <pcomp> <accomp>]
rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x1 <mru 1500> <asyncmap 0x0> <pcomp> <accomp> <auth pap>]
sent [LCP ConfAck id=0x1 <mru 1500> <asyncmap 0x0> <pcomp> <accomp> <auth pap>]
sent [PAP AuthReq id=0x1 user="ubuntu" password=<hidden>]
rcvd [PAP AuthAck id=0x1 "Welcome!"]
Remote message: Welcome!
PAP authentication succeeded
sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0>]
rcvd [IPCP ConfReq id=0x1 <addr 192.168.111.111>]
sent [IPCP ConfAck id=0x1 <addr 192.168.111.111>]
rcvd [IPCP ConfRej id=0x1 <compress VJ 0f 01>]
sent [IPCP ConfReq id=0x2 <addr 0.0.0.0>]
rcvd [IPCP ConfNak id=0x2 <addr 192.168.111.112>]
sent [IPCP ConfReq id=0x3 <addr 192.168.111.112>]
rcvd [IPCP ConfAck id=0x3 <addr 192.168.111.112>]
not replacing existing default route via 10.155.32.1
local  IP address 192.168.111.112
remote IP address 192.168.111.111
Script /etc/ppp/ip-up started (pid 4373)
Script /etc/ppp/ip-up finished (pid 4373), status = 0x0
rcvd [LCP TermReq id=0x2]
LCP terminated by peer
Connect time 0.0 minutes.
Sent 0 bytes, received 0 bytes.
Script /etc/ppp/ip-down started (pid 4378)
sent [LCP TermAck id=0x2]
Script /etc/ppp/ip-down finished (pid 4378), status = 0x0
Modem hangup
Connection terminated.
root@ubuntu:/etc/ppp/peers# [/FONT]


_[COLOR=Blue]pppd configuration:[/COLOR]_
[FONT=Courier New]root@ubuntu:/etc/ppp/peers# cat vodacom
noproxyarp
nodetach
noauth
connect "/usr/sbin/chat -V -f /etc/ppp/chat/vodacom"
disconnect "/usr/sbin/chat -V -s -S -f /etc/ppp/chat/gprs-disconnect"
debug
crtscts
/dev/ttyACM0
115200
defaultroute
noipdefault
#user vodacom
lcp-echo-interval 0
#usepeerdns
#novjccomp
#noaccomp
nopcomp
noccp
nomagic
maxfail 3
passive[/FONT]

_[COLOR=Blue]chat configuration:[/COLOR]_
[FONT=Courier New]root@ubuntu:/etc/ppp/chat# cat vodacom
ABORT BUSY
ABORT 'NO CARRIER'
ABORT VOICE
ABORT 'NO DIALTONE'
ABORT 'NO DIAL TONE'
ABORT 'NO ANSWER'
ABORT DELAYED
'' ATZ
OK AT
OK ATE0V1
OK AT+CGDCONT=1,"IP","internet"
OK ATDT*99***1#
CONNECT ''
'' \d\c[/FONT]

_[COLOR=Blue]global pppd configuration:[/COLOR]_
[FONT=Courier New]root@ubuntu:/etc/ppp# cat options | sed -e '/^#\|^$/d'
asyncmap 0
noauth
crtscts
lock
hide-password
modem
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4
noipx[/FONT]

_[COLOR=Blue]pap/chat configuration:[/COLOR]_
[FONT=Courier New]root@ubuntu:/etc/ppp# grep vodacom *ap-secrets
chap-secrets:vodacom    *       vodacom
pap-secrets:vodacom     *       vodacom *[/FONT]


[COLOR=Blue](The same pppd configuration works on my linux laptop with a Huawei K3715 HSPA USB stick[/COLOR][COLOR=Blue]:[/COLOR]
[FONT=Courier New]root@schoonees:/etc/ppp/peers# pppd call toets
ATZ
OK
AT
OK
ATE0V1
OK

OK

CONNECTScript /usr/sbin/chat -V -f /etc/ppp/chat/toets finished (pid 12330), status = 0x0
Serial connection established.
using channel 11
Using interface ppp0
Connect: ppp0 <--> /dev/ttyUSB0
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x18 <asyncmap 0x0> <auth chap MD5> <magic 0x1afccda> <pcomp> <accomp>]
sent [LCP ConfRej id=0x18 <magic 0x1afccda>]
rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x19 <asyncmap 0x0> <auth chap MD5> <pcomp> <accomp>]
sent [LCP ConfNak id=0x19 <auth pap>]
rcvd [LCP ConfReq id=0x1a <asyncmap 0x0> <auth pap> <pcomp> <accomp>]
sent [LCP ConfAck id=0x1a <asyncmap 0x0> <auth pap> <pcomp> <accomp>]
sent [PAP AuthReq id=0x1 user="schoonees" password=<hidden>]
rcvd [LCP DiscReq id=0x1b magic=0x1afccda]
rcvd [PAP AuthAck id=0x1 ""]
PAP authentication succeeded
sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0>]
rcvd [IPCP ConfNak id=0x1 <ms-dns1 10.11.12.13> <ms-dns2 10.11.12.14> <ms-wins 10.11.12.13> <ms-wins 10.11.12.14>]
sent [IPCP ConfReq id=0x2 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns2 10.11.12.14>]
rcvd [IPCP ConfNak id=0x2 <ms-dns1 10.11.12.13> <ms-dns2 10.11.12.14> <ms-wins 10.11.12.13> <ms-wins 10.11.12.14>]
sent [IPCP ConfReq id=0x3 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns2 10.11.12.14>]
rcvd [IPCP ConfReq id=0xc]
sent [IPCP ConfNak id=0xc <addr 0.0.0.0>]
rcvd [IPCP ConfRej id=0x3 <compress VJ 0f 01>]
sent [IPCP ConfReq id=0x4 <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns2 10.11.12.14>]
rcvd [IPCP ConfReq id=0xd]
sent [IPCP ConfAck id=0xd]
rcvd [IPCP ConfNak id=0x4 <addr 41.16.138.155> <ms-dns1 196.207.36.251> <ms-dns2 196.207.36.254>]
sent [IPCP ConfReq id=0x5 <addr 41.16.138.155> <ms-dns1 196.207.36.251> <ms-dns2 196.207.36.254>]
rcvd [IPCP ConfAck id=0x5 <addr 41.16.138.155> <ms-dns1 196.207.36.251> <ms-dns2 196.207.36.254>]
Could not determine remote IP address: defaulting to 10.64.64.64
not replacing existing default route via 10.155.1.1
local  IP address 41.16.138.155
remote IP address 10.64.64.64
primary   DNS address 196.207.36.251
secondary DNS address 196.207.36.254
Script /etc/ppp/ip-up started (pid 12334)
Script /etc/ppp/ip-up finished (pid 12334), status = 0x0
[FONT=Arial][COLOR=Blue])

[/COLOR][/FONT][/FONT]

---

