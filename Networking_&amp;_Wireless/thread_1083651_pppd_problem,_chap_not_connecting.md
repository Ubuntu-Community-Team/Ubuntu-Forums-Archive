---
title: "pppd problem, chap not connecting"
date: 2009-03-01
forum: Networking &amp; Wireless
---

### Post by siddharthgarg on 2009-03-01
Hi

I have been trying to connect to internet using cable dsl for past 2 days but without any luck...

My provider file (name=sonali2) looks like this
[B][COLOR="Red"]
# Minimalistic default options file for DSL/PPPoE connections

pty "/usr/sbin/pppoe -I eth0 -T 80 -m 1452 -S sonali2 -C sonali2"
user "lapsy"
crtscts
remotename sonali2
ipparam sonali2
noipdefault
defaultroute
replacedefaultroute
hide-password
lcp-echo-interval 30
lcp-echo-failure 4
persist
mtu 1492
show-password
default-asyncmap

noaccomp
debug
passive
usepeerdns
noauth
[/COLOR][/B]


Here is my syslog[B][COLOR="DarkRed"]

Mar  1 18:27:50 abeautifulmind pppd[8967]: using channel 216
Mar  1 18:27:50 abeautifulmind pppd[8967]: Using interface ppp0
Mar  1 18:27:50 abeautifulmind pppd[8967]: Connect: ppp0 <--> /dev/pts/5
Mar  1 18:27:50 abeautifulmind pppd[8967]: Script /usr/sbin/pppoe -I eth0 -T 80 -m 1452 -S sonali2 -C sonali2 finished (pid 9023), status = 0x1
Mar  1 18:27:50 abeautifulmind pppoe[9031]: PADS: Service-Name: 'sonali2'
Mar  1 18:27:50 abeautifulmind pppoe[9031]: PPP session is 336 (0x150)
Mar  1 18:27:50 abeautifulmind pppd[8967]: rcvd [LCP ConfReq id=0x1 <auth chap MD5> <magic 0x70fa6fed>]
Mar  1 18:27:50 abeautifulmind pppd[8967]: sent [LCP ConfReq id=0x1c <magic 0xc5c08fd6> <pcomp>]
Mar  1 18:27:50 abeautifulmind pppd[8967]: sent [LCP ConfAck id=0x1 <auth chap MD5> <magic 0x70fa6fed>]
Mar  1 18:27:50 abeautifulmind pppd[8967]: rcvd [LCP ConfRej id=0x1c <pcomp>]
Mar  1 18:27:50 abeautifulmind pppd[8967]: sent [LCP ConfReq id=0x1d <magic 0xc5c08fd6>]
Mar  1 18:27:50 abeautifulmind pppd[8967]: rcvd [LCP ConfAck id=0x1d <magic 0xc5c08fd6>]
Mar  1 18:27:50 abeautifulmind pppd[8967]: sent [LCP EchoReq id=0x0 magic=0xc5c08fd6]
Mar  1 18:27:50 abeautifulmind pppd[8967]: rcvd [LCP EchoReq id=0x0 magic=0x70fa6fed]
Mar  1 18:27:50 abeautifulmind pppd[8967]: sent [LCP EchoRep id=0x0 magic=0xc5c08fd6]
Mar  1 18:27:50 abeautifulmind pppd[8967]: rcvd [CHAP Challenge id=0x1 <19b9f138267f08d2ef0cad580a7de647>, name = "sonali"]
Mar  1 18:27:50 abeautifulmind pppd[8967]: sent [CHAP Response id=0x1 <023ec961f7eabe920ae397d4140f2b7b>, name = "lapsy"]
Mar  1 18:27:50 abeautifulmind pppd[8967]: rcvd [LCP EchoRep id=0x0 magic=0x70fa6fed]
Mar  1 18:27:52 abeautifulmind pppd[8967]: rcvd [CHAP Failure id=0x1 "I don't like you.  Go 'way."]
Mar  1 18:27:52 abeautifulmind pppd[8967]: CHAP authentication failed: I don't like you.  Go 'way.
Mar  1 18:27:52 abeautifulmind pppd[8967]: CHAP authentication failed
Mar  1 18:27:52 abeautifulmind pppd[8967]: sent [LCP TermReq id=0x1e "Failed to authenticate ourselves to peer"]
Mar  1 18:27:52 abeautifulmind pppd[8967]: rcvd [LCP TermReq id=0x2 "Authentication failed"]
Mar  1 18:27:52 abeautifulmind pppd[8967]: sent [LCP TermAck id=0x2]
Mar  1 18:27:52 abeautifulmind pppd[8967]: rcvd [LCP TermAck id=0x1e]
Mar  1 18:27:52 abeautifulmind pppd[8967]: Connection terminated.
Mar  1 18:27:52 abeautifulmind pppd[8967]: Waiting for 1 child processes...
Mar  1 18:27:52 abeautifulmind pppoe[9031]: read (asyncReadFromPPP): Session 336: Input/output error
Mar  1 18:27:52 abeautifulmind pppoe[9031]: Sent PADT
Mar  1 18:27:52 abeautifulmind pppd[8967]:   script /usr/sbin/pppoe -I eth0 -T 80 -m 1452 -S sonali2 -C sonali2, pid 9029
Mar  1 18:27:52 abeautifulmind pppd[8967]: Script /usr/sbin/pppoe -I eth0 -T 80 -m 1452 -S sonali2 -C sonali2 finished (pid 9029), status = 0x1
Mar  1 18:27:52 abeautifulmind pppd[8967]: Exit.[/COLOR][/B]


I am quite sure that the password I am supplying through chap-secrets is correct. After reading about CHAP, i got to know that chap while sending the password, takes an hash of the password with the challenge. Is it possible that this hash being supplied is somehow incorrect

Can someone please help. Thanks!

Sid

---

