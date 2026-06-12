---
title: "unable to use mobile broadband with 9.04"
date: 2009-07-29
forum: Networking &amp; Wireless
---

### Post by fprumbau on 2009-07-29
After several days of research I wasn't able to find an answer. I have the netbook remix of 9.04 on a Samsung NC10 (2.6.28.14, last updates installed).

The modem is recognized, I defined a new broadband mobile access configuration, but the modem always has a hangup when trying to connect, the provide is Vodafone with its websessions offer.

I have disabled the pin, everything is running fine under XP.

So I installed UMTSMon 0.10 and enabled logging. Unfortunately (unlike most other postings I searched) there is no error message, so that leaves me completly clueless...

```

pppd options in effect:
debug debug debug               # (from command line)
updetach                # (from command line)
idle 7200               # (from command line)
dump            # (from command line)
noauth          # (from /etc/ppp/options)
user vodafone           # (from command line)
password ??????         # (from command line)
/dev/ttyACM0            # (from command line)
460800          # (from command line)
lock            # (from command line)
crtscts         # (from command line)
modem           # (from command line)
asyncmap 0              # (from command line)
lcp-echo-failure 4              # (from /etc/ppp/options)
lcp-echo-interval 30            # (from /etc/ppp/options)
hide-password           # (from /etc/ppp/options)
novj            # (from command line)
defaultroute            # (from command line)
proxyarp                # (from /etc/ppp/options)
usepeerdns              # (from command line)
noccp           # (from command line)
nobsdcomp               # (from command line)
noipx           # (from command line)
using channel 1
Using interface ppp0
Connect: ppp0 <--> /dev/ttyACM0
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x5d3478fa> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x0 <asyncmap 0x0> <auth chap MD5> <magic 0x90e7b162> <pcomp> <accomp>]
sent [LCP ConfAck id=0x0 <asyncmap 0x0> <auth chap MD5> <magic 0x90e7b162> <pcomp> <accomp>]
rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0x5d3478fa> <pcomp> <accomp>]
sent [LCP EchoReq id=0x0 magic=0x5d3478fa]
rcvd [LCP DiscReq id=0x1 magic=0x90e7b162]
rcvd [CHAP Challenge id=0x1 <2c9356c66e93d85de44ab73548da9594>, name = "UMTS_CHAP_SRVR"]
sent [CHAP Response id=0x1 <74cbe57696aab1f1efd378699e1d68d5>, name = "vodafone"]
rcvd [LCP EchoRep id=0x0 magic=0x90e7b162 5d 34 78 fa]
rcvd [CHAP Success id=0x1 ""]
CHAP authentication succeeded
CHAP authentication succeeded
sent [IPCP ConfReq id=0x1 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
rcvd [IPCP ConfNak id=0x1 <ms-dns1 10.11.12.13> <ms-dns2 10.11.12.14> <ms-wins 10.11.12.13> <ms-wins 10.11.12.14>]
sent [IPCP ConfReq id=0x2 <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns2 10.11.12.14>]
Modem hangup
Connection terminated.
```

---

### Post by fprumbau on 2009-08-02
Now it seems to be the fault of the Vodafone card. Although working well with XP, no connection could be established with Jaunty. 

In Jaunty, I tried inserting my Klarmobile-Card (which is working on T-Mobile, APN internet.td-1.de). Now the connection can be established without problems (but it is not useful due to cost reason).

After re-inserting the vodafone card, again, no success...

I'm out of ideas, please give me a hint.

(maybe s.o. nows, what software (ppp?) is doing the connect, so a lookup 
on the developers website may be useful? Would it be possible to integrate a new
version of that software in Jaunty?)

Or maybe anyone else has problems connecting via mobile broadband to Vodafone using its websessions offer...

Thank you in advance
  Frank

---

### Post by fprumbau on 2009-08-10
Solved: Anyone, who has the same problem; it was the APN that was not correct. I read it was web.vodafone.de, but event.vodafone.de for websessions was right. Somebody added the option 'Vodafone websessions D2' later, there it correct, too.

Now I only wonder how to book websessions with firefox, it only tries to load the page (windows firefox always redirects me to the given page...)

But this should be a minor problem. 

Thanx anyway for everyone looking at my post.

Frank
:KS

---

