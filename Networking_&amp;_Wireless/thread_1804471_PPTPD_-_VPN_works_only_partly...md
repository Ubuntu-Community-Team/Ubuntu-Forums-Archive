---
title: "PPTPD - VPN works only partly.."
date: 2011-07-14
forum: Networking &amp; Wireless
---

### Post by OpEn_SoUrCe_RoCkS on 2011-07-14
Hey all!

I configured a PPTP server on Ubuntu 10.10.

It works fine! Sort of...

My MacBook running OS X 10.6 connects fine.

But my iPhone can't seem to connect! The iPhone settings seem to be correct.

Here is the output of the Ubuntu syslog when I try to connect with the iPhone:

```
Jul 14 20:17:04 Ubuntu-Backup-Server pptpd[2601]: CTRL: Client 192.168.1.1 control connection started
Jul 14 20:17:04 Ubuntu-Backup-Server pptpd[2601]: CTRL: Starting call (launching pppd, opening GRE)
Jul 14 20:17:04 Ubuntu-Backup-Server pppd[2602]: Plugin /usr/lib/pptpd/pptpd-logwtmp.so loaded.
Jul 14 20:17:04 Ubuntu-Backup-Server pppd[2602]: pppd 2.4.5 started by root, uid 0
Jul 14 20:17:04 Ubuntu-Backup-Server modem-manager: (net/ppp0): could not get port's parent device
Jul 14 20:17:04 Ubuntu-Backup-Server NetworkManager[860]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Jul 14 20:17:04 Ubuntu-Backup-Server NetworkManager[860]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Jul 14 20:17:04 Ubuntu-Backup-Server pppd[2602]: Using interface ppp0
Jul 14 20:17:04 Ubuntu-Backup-Server pppd[2602]: Connect: ppp0 <--> /dev/pts/2
Jul 14 20:17:04 Ubuntu-Backup-Server pptpd[2601]: GRE: Bad checksum from pppd.
Jul 14 20:17:04 Ubuntu-Backup-Server pptpd[2601]: GRE: read(fd=7,buffer=80524a0,len=8260) from network failed: status = -1 error = Protocol not available
Jul 14 20:17:04 Ubuntu-Backup-Server pptpd[2601]: CTRL: GRE read or PTY write failed (gre,pty)=(7,6)
Jul 14 20:17:04 Ubuntu-Backup-Server pptpd[2601]: CTRL: Reaping child PPP[2602]
Jul 14 20:17:04 Ubuntu-Backup-Server pppd[2602]: Modem hangup
Jul 14 20:17:04 Ubuntu-Backup-Server pppd[2602]: Connection terminated.
Jul 14 20:17:04 Ubuntu-Backup-Server avahi-daemon[863]: Withdrawing workstation service for ppp0.
Jul 14 20:17:04 Ubuntu-Backup-Server NetworkManager[860]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Jul 14 20:17:04 Ubuntu-Backup-Server pppd[2602]: Exit.
Jul 14 20:17:04 Ubuntu-Backup-Server pptpd[2601]: CTRL: Client 192.168.1.1 control connection finished
```

Any ideas?

Thanks.

---

### Post by OpEn_SoUrCe_RoCkS on 2011-07-18
Ok, well after trying a few things and changing a few configs, the error message is different. Now I get a "timeout sending Config-Requests"...

I tried disabling compression (noaccomp and nopcomp), not refusing pap, chap and all that stuff.. 

Any suggestions? Thanks!
For what it's worth, I'm running iOS 4.3.3 on the iPhone.

---

### Post by jmoorse on 2011-07-18
Hello!  I am not an IOS expert, but I can help with the networking portion.

I am most concerned about this:

> 
Jul 14 20:17:04 Ubuntu-Backup-Server pptpd[2601]: GRE: Bad checksum from pppd.


Are you on 3G data or wifi with the phone?  If wifi, is it the same network the Macbook works from?

---

### Post by OpEn_SoUrCe_RoCkS on 2011-07-18
That output is when I try a connection from 3G.
Actually, I get a different message when I try from the same network as my server.

Here's the output from iPhone + Wifi:
```
Jul 18 15:09:54 Ubuntu-Backup-Server pptpd[3462]: CTRL: Client 192.168.1.1 control connection started
Jul 18 15:09:54 Ubuntu-Backup-Server pptpd[3462]: CTRL: Starting call (launching pppd, opening GRE)
Jul 18 15:09:54 Ubuntu-Backup-Server pppd[3464]: Plugin /usr/lib/pptpd/pptpd-logwtmp.so loaded.
Jul 18 15:09:54 Ubuntu-Backup-Server pppd[3464]: pppd 2.4.5 started by root, uid 0
Jul 18 15:09:54 Ubuntu-Backup-Server modem-manager: (net/ppp0): could not get port's parent device
Jul 18 15:09:54 Ubuntu-Backup-Server NetworkManager[1057]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Jul 18 15:09:54 Ubuntu-Backup-Server NetworkManager[1057]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Jul 18 15:09:54 Ubuntu-Backup-Server pppd[3464]: Using interface ppp0
Jul 18 15:09:54 Ubuntu-Backup-Server pppd[3464]: Connect: ppp0 <--> /dev/pts/3
Jul 18 15:09:54 Ubuntu-Backup-Server pptpd[3462]: GRE: Bad checksum from pppd.
Jul 18 15:09:54 Ubuntu-Backup-Server pptpd[3462]: GRE: read(fd=7,buffer=80524a0,len=8260) from network failed: status = -1 error = Protocol not available
Jul 18 15:09:54 Ubuntu-Backup-Server pptpd[3462]: CTRL: GRE read or PTY write failed (gre,pty)=(7,6)
Jul 18 15:09:54 Ubuntu-Backup-Server pptpd[3462]: CTRL: Reaping child PPP[3464]
Jul 18 15:09:54 Ubuntu-Backup-Server pppd[3464]: Modem hangup
Jul 18 15:09:54 Ubuntu-Backup-Server pppd[3464]: Connection terminated.
Jul 18 15:09:54 Ubuntu-Backup-Server avahi-daemon[927]: Withdrawing workstation service for ppp0.
Jul 18 15:09:54 Ubuntu-Backup-Server NetworkManager[1057]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Jul 18 15:09:54 Ubuntu-Backup-Server pppd[3464]: Exit.
Jul 18 15:09:54 Ubuntu-Backup-Server pptpd[3462]: CTRL: Client 192.168.1.1 control connection finished

```

From iPhone + 3G:
```
Jul 18 15:06:10 Ubuntu-Backup-Server pptpd[3449]: CTRL: Client [iPhone IP address] control connection started
Jul 18 15:06:11 Ubuntu-Backup-Server pptpd[3449]: CTRL: Starting call (launching pppd, opening GRE)
Jul 18 15:06:11 Ubuntu-Backup-Server pppd[3451]: Plugin /usr/lib/pptpd/pptpd-logwtmp.so loaded.
Jul 18 15:06:11 Ubuntu-Backup-Server pppd[3451]: pppd 2.4.5 started by root, uid 0
Jul 18 15:06:11 Ubuntu-Backup-Server modem-manager: (net/ppp0): could not get port's parent device
Jul 18 15:06:11 Ubuntu-Backup-Server NetworkManager[1057]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Jul 18 15:06:11 Ubuntu-Backup-Server NetworkManager[1057]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Jul 18 15:06:11 Ubuntu-Backup-Server pppd[3451]: Using interface ppp0
Jul 18 15:06:11 Ubuntu-Backup-Server pppd[3451]: Connect: ppp0 <--> /dev/pts/3
Jul 18 15:06:11 Ubuntu-Backup-Server pptpd[3449]: GRE: Bad checksum from pppd.
Jul 18 15:06:41 Ubuntu-Backup-Server pppd[3451]: LCP: timeout sending Config-Requests
Jul 18 15:06:41 Ubuntu-Backup-Server pppd[3451]: Connection terminated.
Jul 18 15:06:41 Ubuntu-Backup-Server avahi-daemon[927]: Withdrawing workstation service for ppp0.
Jul 18 15:06:41 Ubuntu-Backup-Server NetworkManager[1057]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Jul 18 15:06:41 Ubuntu-Backup-Server pppd[3451]: Modem hangup
Jul 18 15:06:41 Ubuntu-Backup-Server pppd[3451]: Exit.
Jul 18 15:06:41 Ubuntu-Backup-Server pptpd[3449]: GRE: read(fd=6,buffer=805a540,len=8196) from PTY failed: status = -1 error = Input/output error, usually caused by unexpected termination of pppd, check option syntax and pppd logs
Jul 18 15:06:41 Ubuntu-Backup-Server pptpd[3449]: CTRL: PTY read or GRE write failed (pty,gre)=(6,7)
Jul 18 15:06:41 Ubuntu-Backup-Server pptpd[3449]: CTRL: Reaping child PPP[3451]
Jul 18 15:06:41 Ubuntu-Backup-Server pptpd[3449]: CTRL: Client [iPhone IP address] control connection finished

```

And MacBook Pro + Wifi (after successful connection and disconnection):
```
Jul 18 15:02:35 Ubuntu-Backup-Server pptpd[3372]: CTRL: Client 192.168.1.1 control connection started
Jul 18 15:02:35 Ubuntu-Backup-Server pptpd[3372]: CTRL: Starting call (launching pppd, opening GRE)
Jul 18 15:02:35 Ubuntu-Backup-Server pppd[3373]: Plugin /usr/lib/pptpd/pptpd-logwtmp.so loaded.
Jul 18 15:02:35 Ubuntu-Backup-Server pppd[3373]: pppd 2.4.5 started by root, uid 0
Jul 18 15:02:35 Ubuntu-Backup-Server modem-manager: (net/ppp0): could not get port's parent device
Jul 18 15:02:35 Ubuntu-Backup-Server NetworkManager[1057]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Jul 18 15:02:35 Ubuntu-Backup-Server NetworkManager[1057]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Jul 18 15:02:35 Ubuntu-Backup-Server pppd[3373]: Using interface ppp0
Jul 18 15:02:35 Ubuntu-Backup-Server pppd[3373]: Connect: ppp0 <--> /dev/pts/1
Jul 18 15:02:35 Ubuntu-Backup-Server pptpd[3372]: GRE: Bad checksum from pppd.
Jul 18 15:02:35 Ubuntu-Backup-Server pppd[3373]: MPPE 128-bit stateless compression enabled
Jul 18 15:02:35 Ubuntu-Backup-Server pppd[3373]: found interface eth40 for proxy arp
Jul 18 15:02:35 Ubuntu-Backup-Server pppd[3373]: local  IP address 192.168.1.10
Jul 18 15:02:35 Ubuntu-Backup-Server pppd[3373]: remote IP address 192.168.1.100
Jul 18 15:02:44 Ubuntu-Backup-Server pppd[3373]: LCP terminated by peer (MPPE disabled)
Jul 18 15:02:44 Ubuntu-Backup-Server pppd[3373]: Connect time 0.2 minutes.
Jul 18 15:02:44 Ubuntu-Backup-Server pppd[3373]: Sent 2160 bytes, received 3474 bytes.
Jul 18 15:02:44 Ubuntu-Backup-Server pptpd[3372]: CTRL: EOF or bad error reading ctrl packet length.
Jul 18 15:02:44 Ubuntu-Backup-Server pptpd[3372]: CTRL: couldn't read packet header (exit)
Jul 18 15:02:44 Ubuntu-Backup-Server pptpd[3372]: CTRL: CTRL read failed
Jul 18 15:02:44 Ubuntu-Backup-Server pptpd[3372]: CTRL: Reaping child PPP[3373]
Jul 18 15:02:44 Ubuntu-Backup-Server pppd[3373]: Modem hangup
Jul 18 15:02:44 Ubuntu-Backup-Server pppd[3373]: Connection terminated.
Jul 18 15:02:44 Ubuntu-Backup-Server avahi-daemon[927]: Withdrawing workstation service for ppp0.
Jul 18 15:02:44 Ubuntu-Backup-Server NetworkManager[1057]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Jul 18 15:02:44 Ubuntu-Backup-Server pppd[3373]: Exit.
Jul 18 15:02:44 Ubuntu-Backup-Server pptpd[3372]: CTRL: Client 192.168.1.1 control connection finished

```

As you can see, I get bad checksum with the MacBook too... Yet it works. So I'm not too concerned about this message. Perhaps I should be though... This is outside of my field of expertise, so I don't really know what's happening!

What puzzles me is that I get two different errors, depending on if I connect through 3G or Wifi...



Here's the content of my config files.

/etc/ppp/options:
```

asyncmap 0
noauth
crtscts
lock
hide-password
modem
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4
noipx
```


/etc/ppp/options.pptp:
```
lock
noauth
nobsdcomp
nodeflate
noaccomp
nopcomp
```

/etc/ppp/pptpd-options:
```
name pptpd
require-mschap-v2
require-mppe-128
ms-dns 192.168.1.1
proxyarp
nodefaultroute
lock
nobsdcomp 
noaccomp
nopcomp
```

---

### Post by jmoorse on 2011-07-18
Are all your tests from the same network as the PPTP server?  

Did you test your macbook from an external network?  

Some router / firewalls require you to turn on GRE forwarding / passthrough in their firewall options.  (This will only affect PPTP requests from external networks)

---

### Post by OpEn_SoUrCe_RoCkS on 2011-07-18
I have a Linksys E1200 router, and I have enabled the PPTP passthrough in the settings...

---

### Post by jmoorse on 2011-07-18
Ok:

Are all your tests from the same network as the PPTP server? 

Did you test your macbook from an external network? 

Have you tested iPhone Wifi from an external network?

---

### Post by OpEn_SoUrCe_RoCkS on 2011-07-18
Well, iPhone on 3G is external.. 216.xx.xx.xx. And it doesn't work. But it shows in my logs, so it means that the router passes it on to my server.. The problem is serverside, I would tend to think...

---

### Post by jmoorse on 2011-07-18
Yeah I need to know if you have ever successfully tested (not with the iPhone) it from an external network, otherwise we cannot rule out your router right?

I have seen SOHO routers break PPTP before, apparently for fun :)

---

### Post by OpEn_SoUrCe_RoCkS on 2011-07-18
Hmmm.. Interesting. I'm away from home right now, but what I'll do when I get back, is tether my 3G to my MacBook and try it then.. 
Thanks for your help so far!

---

### Post by OpEn_SoUrCe_RoCkS on 2011-07-18
Okay, it didn't work!!

MacBook through iPhone's 3G connection:
```
Jul 18 23:32:52 Ubuntu-Backup-Server pptpd[7670]: CTRL: Client 216.218.29.209 control connection started
Jul 18 23:32:52 Ubuntu-Backup-Server pptpd[7670]: CTRL: Starting call (launching pppd, opening GRE)
Jul 18 23:32:52 Ubuntu-Backup-Server pppd[7671]: Plugin /usr/lib/pptpd/pptpd-logwtmp.so loaded.
Jul 18 23:32:52 Ubuntu-Backup-Server pppd[7671]: pppd 2.4.5 started by root, uid 0
Jul 18 23:32:52 Ubuntu-Backup-Server modem-manager: (net/ppp0): could not get port's parent device
Jul 18 23:32:52 Ubuntu-Backup-Server NetworkManager[1057]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Jul 18 23:32:52 Ubuntu-Backup-Server NetworkManager[1057]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Jul 18 23:32:52 Ubuntu-Backup-Server pppd[7671]: Using interface ppp0
Jul 18 23:32:52 Ubuntu-Backup-Server pppd[7671]: Connect: ppp0 <--> /dev/pts/3
Jul 18 23:32:52 Ubuntu-Backup-Server pptpd[7670]: GRE: Bad checksum from pppd.
Jul 18 23:33:22 Ubuntu-Backup-Server pppd[7671]: LCP: timeout sending Config-Requests
Jul 18 23:33:22 Ubuntu-Backup-Server pppd[7671]: Connection terminated.
Jul 18 23:33:22 Ubuntu-Backup-Server avahi-daemon[927]: Withdrawing workstation service for ppp0.
Jul 18 23:33:22 Ubuntu-Backup-Server NetworkManager[1057]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Jul 18 23:33:22 Ubuntu-Backup-Server pppd[7671]: Modem hangup
Jul 18 23:33:22 Ubuntu-Backup-Server pppd[7671]: Exit.
Jul 18 23:33:22 Ubuntu-Backup-Server pptpd[7670]: GRE: read(fd=6,buffer=805a540,len=8196) from PTY failed: status = -1 error = Input/output error, usually caused by unexpected termination of pppd, check option syntax and pppd logs
Jul 18 23:33:22 Ubuntu-Backup-Server pptpd[7670]: CTRL: PTY read or GRE write failed (pty,gre)=(6,7)
Jul 18 23:33:22 Ubuntu-Backup-Server pptpd[7670]: CTRL: Reaping child PPP[7671]
Jul 18 23:33:22 Ubuntu-Backup-Server pptpd[7670]: CTRL: Client 216.218.29.209 control connection finished

```

So it only works through Wifi on my Mac, if in the same network... Which sort of defeats the purpose of a VPN lol.

---

### Post by jmoorse on 2011-07-19
It looks like we can consider the firewall here.  Can you walk me through what steps you went through to forward the ports for PPTP?  Did you do TCP/1723 as well as IP protocol 47 (GRE)?

---

### Post by OpEn_SoUrCe_RoCkS on 2011-07-19
I enabled all VPN passthroughs in the router settings.
I forwarded port 1723 to my server.

GRE, I'm not sure about. I thought that enabling the passthroughs would take care of that... Perhaps not? 
But I was assuming that since my server is picking up the requests, then the problem must not be on the router's side.. If it were, my server wouldn't see anything, right?


Here are the settings on my router.
[IMG]http://db.tt/niKqKTG[/IMG]
[IMG]http://db.tt/BbnefYB[/IMG]
[IMG]http://db.tt/95bRKEv[/IMG]

Sorry for the orientation..

---

### Post by jmoorse on 2011-07-19
Firewall config looks fine to me.  Have you tested the macbook from an external network that isn't 3G tethered?  Like a friend's wifi or such?

---

### Post by OpEn_SoUrCe_RoCkS on 2011-07-19
Okay, so after further research, I realized that iOS support for PPTP is broken. 
I'm going with L2TP instead, using OpenSwan and xl2tpd.

After configuring everything, I get this when trying to connect, either from my local network, or from outside...

What am I doing wrong!!

```
Jul 19 15:42:50 Ubuntu-Backup-Server xl2tpd[15713]: Connection established to 216.218.29.182, 59888.  Local: 37760, Remote: 24 (ref=0/0).  LNS session is 'default'
Jul 19 15:42:50 Ubuntu-Backup-Server xl2tpd[15713]: start_pppd: I'm running: 
Jul 19 15:42:50 Ubuntu-Backup-Server xl2tpd[15713]: "/usr/sbin/pppd" 
Jul 19 15:42:50 Ubuntu-Backup-Server xl2tpd[15713]: "passive" 
Jul 19 15:42:50 Ubuntu-Backup-Server xl2tpd[15713]: "nodetach" 
Jul 19 15:42:50 Ubuntu-Backup-Server xl2tpd[15713]: "192.168.1.10:0.0.0.0" 
Jul 19 15:42:50 Ubuntu-Backup-Server xl2tpd[15713]: "auth" 
Jul 19 15:42:50 Ubuntu-Backup-Server xl2tpd[15713]: "debug" 
Jul 19 15:42:50 Ubuntu-Backup-Server xl2tpd[15713]: "file" 
Jul 19 15:42:50 Ubuntu-Backup-Server xl2tpd[15713]: "/etc/ppp/options.xl2tpd" 
Jul 19 15:42:50 Ubuntu-Backup-Server xl2tpd[15713]: "/dev/pts/2" 
Jul 19 15:42:50 Ubuntu-Backup-Server xl2tpd[15713]: Call established with 216.218.29.182, Local: 46448, Remote: 1777, Serial: 1
Jul 19 15:42:50 Ubuntu-Backup-Server pppd[15961]: pppd 2.4.5 started by root, uid 0
Jul 19 15:42:50 Ubuntu-Backup-Server pppd[15961]: using channel 98
Jul 19 15:42:50 Ubuntu-Backup-Server modem-manager: (net/ppp0): could not get port's parent device
Jul 19 15:42:50 Ubuntu-Backup-Server NetworkManager[838]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Jul 19 15:42:50 Ubuntu-Backup-Server NetworkManager[838]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Jul 19 15:42:50 Ubuntu-Backup-Server pppd[15961]: Using interface ppp0
Jul 19 15:42:50 Ubuntu-Backup-Server pppd[15961]: Connect: ppp0 <--> /dev/pts/2
Jul 19 15:42:50 Ubuntu-Backup-Server pppd[15961]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <auth chap MS-v2> <magic 0xfafe3aa2> <pcomp> <accomp>]
Jul 19 15:42:50 Ubuntu-Backup-Server pppd[15961]: rcvd [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x9346ac3> <pcomp> <accomp>]
Jul 19 15:42:50 Ubuntu-Backup-Server pppd[15961]: sent [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0x9346ac3> <pcomp> <accomp>]
Jul 19 15:42:50 Ubuntu-Backup-Server pppd[15961]: rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <auth chap MS-v2> <magic 0xfafe3aa2> <pcomp> <accomp>]
Jul 19 15:42:50 Ubuntu-Backup-Server pppd[15961]: sent [LCP EchoReq id=0x0 magic=0xfafe3aa2]
Jul 19 15:42:50 Ubuntu-Backup-Server pppd[15961]: sent [CHAP Challenge id=0x19 <22c27f498e70e41647d41d7a8524b369>, name = "l2tpd"]
Jul 19 15:42:51 Ubuntu-Backup-Server pppd[15961]: rcvd [LCP EchoReq id=0x0 magic=0x9346ac3]
Jul 19 15:42:51 Ubuntu-Backup-Server pppd[15961]: sent [LCP EchoRep id=0x0 magic=0xfafe3aa2]
Jul 19 15:42:51 Ubuntu-Backup-Server pppd[15961]: rcvd [LCP EchoRep id=0x0 magic=0x9346ac3]
Jul 19 15:42:51 Ubuntu-Backup-Server pppd[15961]: rcvd [CHAP Response id=0x19 <11580e702ef304f5d82ad82e972c64ca0000000000000000998bbf8b98daac64a1a933080ced9c106b050ea559dbf8c800>, name = "olivier"]
Jul 19 15:42:51 Ubuntu-Backup-Server pppd[15961]: sent [CHAP Success id=0x19 "S=E992584E434E3594029ADBF82FBD563EF544EA05 M=Access granted"]
Jul 19 15:42:51 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfReq id=0x1 <addr 192.168.1.10>]
Jul 19 15:42:51 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x1 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:42:51 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x1 <addr 0.0.0.0>]
Jul 19 15:42:51 Ubuntu-Backup-Server pppd[15961]: rcvd [IPV6CP ConfReq id=0x1 <addr fe80::f05c:357f:51b4:3c4f>]
Jul 19 15:42:51 Ubuntu-Backup-Server pppd[15961]: Unsupported protocol 'IPv6 Control Protovol' (0x8057) received
Jul 19 15:42:51 Ubuntu-Backup-Server pppd[15961]: sent [LCP ProtRej id=0x2 80 57 01 01 00 0e 01 0a f0 5c 35 7f 51 b4 3c 4f]
Jul 19 15:42:51 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfAck id=0x1 <addr 192.168.1.10>]
Jul 19 15:42:51 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x2 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:42:51 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x2 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:42:51 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x3 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:42:51 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x3 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:42:51 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x4 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:42:51 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x4 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:42:51 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x5 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:42:51 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x5 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:42:51 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x6 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:42:51 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x6 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:42:51 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x7 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:42:51 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x7 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:42:51 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x8 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:42:51 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x8 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:42:51 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x9 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:42:51 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x9 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:42:52 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xa <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:42:52 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xa <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:42:52 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xb <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:42:52 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xb <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:42:52 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xc <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:42:52 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xc <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:42:52 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xd <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:42:52 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xd <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:42:52 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xe <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:42:52 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xe <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:42:52 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xf <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:42:52 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xf <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:42:52 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x10 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:42:52 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x10 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:42:52 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x11 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:42:52 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x11 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:42:52 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x12 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:42:52 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x12 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:42:53 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x13 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:42:53 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x13 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:42:53 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x14 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:42:53 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x14 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:42:53 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x15 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:42:53 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x15 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:42:53 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x16 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:42:53 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x16 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:42:54 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfReq id=0x1 <addr 192.168.1.10>]
Jul 19 15:42:54 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x17 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:42:54 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x17 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:42:54 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfAck id=0x1 <addr 192.168.1.10>]
Jul 19 15:42:54 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x18 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:42:54 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x18 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:42:54 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x19 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:42:54 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x19 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:42:55 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x1a <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:42:55 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x1a <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:42:55 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x1b <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:42:55 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x1b <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:42:55 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x1c <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:42:55 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x1c <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:42:55 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x1d <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:42:55 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x1d <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:42:56 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x1e <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:42:56 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x1e <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:42:56 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x1f <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:42:56 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x1f <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:42:56 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x20 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:42:56 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x20 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:42:57 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x21 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:42:57 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x21 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:42:57 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfReq id=0x1 <addr 192.168.1.10>]
Jul 19 15:42:57 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x22 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:42:57 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x22 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:42:57 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfAck id=0x1 <addr 192.168.1.10>]
Jul 19 15:42:57 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x23 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:42:57 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x23 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:42:58 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x24 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:42:58 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x24 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:42:58 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x25 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:42:58 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x25 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:42:58 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x26 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:42:58 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x26 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:42:59 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x27 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:42:59 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x27 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:42:59 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x28 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:42:59 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x28 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:42:59 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x29 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:42:59 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x29 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:42:59 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x2a <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:42:59 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x2a <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:00 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x2b <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:00 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x2b <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:00 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfReq id=0x1 <addr 192.168.1.10>]
Jul 19 15:43:00 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x2c <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:00 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x2c <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:00 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfAck id=0x1 <addr 192.168.1.10>]
Jul 19 15:43:00 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x2d <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:00 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x2d <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:00 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x2e <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:00 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x2e <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:01 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x2f <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:01 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x2f <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:01 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x30 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:01 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x30 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:01 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x31 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:01 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x31 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:01 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x32 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:01 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x32 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:01 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x33 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:01 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x33 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:01 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x34 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:01 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x34 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:02 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x35 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:02 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x35 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:02 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x36 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:02 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x36 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:02 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x37 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:02 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x37 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:02 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x38 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:02 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x38 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:02 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x39 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:02 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x39 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:03 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x3a <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:03 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x3a <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:03 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfReq id=0x1 <addr 192.168.1.10>]
Jul 19 15:43:03 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x3b <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:03 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x3b <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:03 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfAck id=0x1 <addr 192.168.1.10>]
Jul 19 15:43:03 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x3c <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:03 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x3c <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:03 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x3d <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:03 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x3d <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:03 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x3e <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:03 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x3e <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:03 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x3f <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:03 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x3f <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:04 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x40 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:04 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x40 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:04 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x41 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:04 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x41 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:04 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x42 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:04 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x42 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:04 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x43 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:04 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x43 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:04 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x44 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:04 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x44 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:04 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x45 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:04 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x45 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:04 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x46 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:04 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x46 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:04 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x47 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:04 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x47 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:04 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x48 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:04 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x48 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:04 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x49 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:04 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x49 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:05 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x4a <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:05 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x4a <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:05 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x4b <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:05 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x4b <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:05 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x4c <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:05 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x4c <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:05 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x4d <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:05 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x4d <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:05 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x4e <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:05 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x4e <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:05 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x4f <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:05 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x4f <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:05 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x50 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:05 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x50 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:05 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x51 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:05 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x51 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:05 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x52 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:05 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x52 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:05 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x53 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:05 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x53 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:05 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x54 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:05 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x54 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:05 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x55 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:05 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x55 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:05 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x56 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:05 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x56 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:05 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x57 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:05 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x57 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:05 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x58 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:05 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x58 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:06 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x59 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:06 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x59 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:06 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x5a <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:06 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x5a <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:06 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfReq id=0x1 <addr 192.168.1.10>]
Jul 19 15:43:06 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x5b <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:06 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x5b <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:06 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfAck id=0x1 <addr 192.168.1.10>]
Jul 19 15:43:06 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x5c <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:06 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x5c <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:06 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x5d <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:06 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x5d <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:06 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x5e <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:06 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x5e <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:06 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x5f <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:06 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x5f <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:06 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x60 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:06 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x60 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:06 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x61 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:06 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x61 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:06 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x62 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:06 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x62 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:06 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x63 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:06 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x63 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:06 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x64 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:06 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x64 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:06 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x65 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:06 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x65 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:06 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x66 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:06 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x66 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:06 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x67 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:06 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x67 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:07 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x68 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:07 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x68 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:07 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x69 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:07 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x69 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:07 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x6a <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:07 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x6a <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:07 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x6b <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:07 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x6b <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:07 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x6c <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:07 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x6c <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:07 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x6d <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:07 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x6d <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:07 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x6e <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:07 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x6e <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:07 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x6f <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:07 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x6f <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:07 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x70 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:07 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x70 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:07 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x71 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:07 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x71 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:07 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x72 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:07 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x72 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:07 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x73 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:07 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x73 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:07 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x74 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:07 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x74 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:08 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x75 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:08 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x75 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:08 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x76 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:08 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x76 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:08 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x77 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:08 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x77 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:08 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x78 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:08 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x78 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:08 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x79 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:08 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x79 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:08 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x7a <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:08 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x7a <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:08 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x7b <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:08 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x7b <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:08 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x7c <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:08 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x7c <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:08 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x7d <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:08 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x7d <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:08 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x7e <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:08 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x7e <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:08 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x7f <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:08 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x7f <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:08 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x80 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:08 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x80 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:08 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x81 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:08 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x81 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:08 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x82 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:08 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x82 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:09 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x83 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:09 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x83 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:09 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x84 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:09 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x84 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:09 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfReq id=0x1 <addr 192.168.1.10>]
Jul 19 15:43:09 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x85 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:09 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x85 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:09 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfAck id=0x1 <addr 192.168.1.10>]
Jul 19 15:43:09 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x86 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:09 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x86 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:09 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x87 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:09 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x87 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:09 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x88 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:09 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x88 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:09 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x89 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:09 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x89 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:09 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x8a <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:09 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x8a <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:09 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x8b <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:09 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x8b <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:09 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x8c <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:09 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x8c <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:09 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x8d <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:09 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x8d <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:09 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x8e <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:09 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x8e <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:09 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x8f <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:09 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x8f <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:09 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x90 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:09 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x90 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:10 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x91 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:10 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x91 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:10 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x92 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:10 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x92 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:10 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x93 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:10 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x93 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:10 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x94 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:10 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x94 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:10 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x95 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:10 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x95 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:10 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x96 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:10 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x96 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:10 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x97 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:10 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x97 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:10 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x98 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:10 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x98 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:10 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x99 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:10 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x99 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:10 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x9a <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:10 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x9a <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:10 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x9b <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:10 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x9b <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:10 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x9c <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:10 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x9c <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:10 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x9d <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:10 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x9d <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:10 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x9e <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:10 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x9e <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:11 Ubuntu-Backup-Server pppd[15961]: rcvd [LCP EchoReq id=0x1 magic=0x9346ac3]
Jul 19 15:43:11 Ubuntu-Backup-Server pppd[15961]: sent [LCP EchoRep id=0x1 magic=0xfafe3aa2]
Jul 19 15:43:11 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0x9f <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:11 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0x9f <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:11 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xa0 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:11 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xa0 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:11 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xa1 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:11 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xa1 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:11 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xa2 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:11 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xa2 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:11 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xa3 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:11 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xa3 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:11 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xa4 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:11 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xa4 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:11 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xa5 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:11 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xa5 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:11 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xa6 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:11 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xa6 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:11 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xa7 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:11 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xa7 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:11 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xa8 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:11 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xa8 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:11 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xa9 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:11 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xa9 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:11 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xaa <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:11 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xaa <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:11 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xab <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:11 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xab <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:12 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xac <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:12 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xac <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:12 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xad <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:12 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xad <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:12 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfReq id=0x1 <addr 192.168.1.10>]
Jul 19 15:43:12 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xae <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:12 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xae <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:12 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfAck id=0x1 <addr 192.168.1.10>]
Jul 19 15:43:12 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xaf <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:12 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xaf <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:12 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xb0 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:12 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xb0 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:12 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xb1 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:12 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xb1 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:12 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xb2 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:12 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xb2 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:12 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xb3 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:12 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xb3 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:12 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xb4 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:12 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xb4 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:12 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xb5 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:12 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xb5 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:12 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xb6 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:12 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xb6 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:12 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xb7 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:12 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xb7 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:12 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xb8 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:12 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xb8 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:13 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xb9 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:13 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xb9 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:13 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xba <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:13 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xba <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:13 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xbb <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:13 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xbb <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:13 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xbc <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:13 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xbc <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:13 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xbd <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:13 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xbd <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:13 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xbe <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:13 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xbe <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:13 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xbf <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:13 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xbf <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:13 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xc0 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:13 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xc0 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:13 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xc1 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:13 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xc1 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:13 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xc2 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:13 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xc2 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:13 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xc3 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:13 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xc3 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:13 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xc4 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:13 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xc4 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:13 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xc5 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:13 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xc5 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:13 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xc6 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:13 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xc6 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:14 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xc7 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:14 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xc7 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:14 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xc8 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:14 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xc8 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:14 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xc9 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:14 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xc9 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:14 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xca <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:14 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xca <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:14 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xcb <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:14 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xcb <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:14 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xcc <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:14 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xcc <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:14 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xcd <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:14 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xcd <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:14 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xce <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:14 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xce <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:14 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xcf <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:14 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xcf <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:14 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xd0 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:14 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xd0 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:14 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xd1 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:14 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xd1 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:14 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xd2 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:14 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xd2 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:14 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xd3 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:14 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xd3 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:14 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xd4 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:14 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xd4 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:14 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xd5 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:14 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xd5 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:15 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xd6 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:15 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xd6 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:15 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xd7 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:15 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xd7 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:15 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xd8 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:15 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xd8 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:15 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfReq id=0x1 <addr 192.168.1.10>]
Jul 19 15:43:15 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xd9 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:15 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xd9 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:15 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfAck id=0x1 <addr 192.168.1.10>]
Jul 19 15:43:15 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xda <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:15 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xda <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:15 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xdb <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:15 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xdb <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:15 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xdc <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:15 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xdc <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:15 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xdd <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:15 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xdd <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:15 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xde <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:15 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xde <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:15 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xdf <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:15 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xdf <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:15 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xe0 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:15 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xe0 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:15 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xe1 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:15 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xe1 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:15 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xe2 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:15 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xe2 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:15 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xe3 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:15 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xe3 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:15 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xe4 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:15 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xe4 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:15 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xe5 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:15 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xe5 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:16 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xe6 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:16 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xe6 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:16 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xe7 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:16 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xe7 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:16 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xe8 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:16 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xe8 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:16 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xe9 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:16 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xe9 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:16 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xea <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:16 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xea <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:16 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xeb <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:16 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xeb <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:16 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xec <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:16 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xec <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:16 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xed <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:16 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xed <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:16 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xee <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:16 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xee <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:16 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xef <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:16 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xef <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:16 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xf0 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:16 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xf0 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:16 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xf1 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:16 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xf1 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:16 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xf2 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:16 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xf2 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:16 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xf3 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:16 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xf3 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:16 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xf4 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:16 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xf4 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:16 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xf5 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:16 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xf5 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:17 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xf6 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:17 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xf6 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:17 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xf7 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:17 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xf7 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:17 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xf8 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:17 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xf8 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:17 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xf9 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:17 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xf9 <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:17 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xfa <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:17 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xfa <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:17 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xfb <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:17 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xfb <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:17 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xfc <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:17 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xfc <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:17 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xfd <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:17 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xfd <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:17 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xfe <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:17 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xfe <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:17 Ubuntu-Backup-Server pppd[15961]: rcvd [IPCP ConfReq id=0xff <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 19 15:43:17 Ubuntu-Backup-Server pppd[15961]: sent [IPCP ConfRej id=0xff <addrs 0.0.0.0 0.0.0.0>]
Jul 19 15:43:17 Ubuntu-Backup-Server pppd[15961]: rcvd [LCP TermReq id=0x2 "No network protocols running"]
Jul 19 15:43:17 Ubuntu-Backup-Server pppd[15961]: LCP terminated by peer (No network protocols running)
Jul 19 15:43:17 Ubuntu-Backup-Server pppd[15961]: sent [LCP TermAck id=0x2]
Jul 19 15:43:18 Ubuntu-Backup-Server xl2tpd[15713]: result_code_avp: result code out of range (768 0 14).  Ignoring.
Jul 19 15:43:18 Ubuntu-Backup-Server xl2tpd[15713]: control_finish: Peer tried to disconnect without specifying result code.
Jul 19 15:43:18 Ubuntu-Backup-Server xl2tpd[15713]: result_code_avp: result code out of range (256 0 14).  Ignoring.
Jul 19 15:43:18 Ubuntu-Backup-Server xl2tpd[15713]: control_finish: Peer tried to disconnect without specifying result code.
Jul 19 15:43:20 Ubuntu-Backup-Server pppd[15961]: Connection terminated.
Jul 19 15:43:20 Ubuntu-Backup-Server pppd[15961]: Connect time 0.5 minutes.
Jul 19 15:43:20 Ubuntu-Backup-Server pppd[15961]: Sent 3656 bytes, received 6730 bytes.
Jul 19 15:43:20 Ubuntu-Backup-Server avahi-daemon[836]: Withdrawing workstation service for ppp0.
Jul 19 15:43:20 Ubuntu-Backup-Server NetworkManager[838]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Jul 19 15:43:21 Ubuntu-Backup-Server pppd[15961]: Modem hangup
Jul 19 15:43:21 Ubuntu-Backup-Server pppd[15961]: Exit.
Jul 19 15:43:21 Ubuntu-Backup-Server xl2tpd[15713]: child_handler : pppd exited for call 1777 with code 16
Jul 19 15:43:21 Ubuntu-Backup-Server xl2tpd[15713]: call_close: Call 46448 to 216.218.29.182 disconnected
Jul 19 15:43:26 Ubuntu-Backup-Server xl2tpd[15713]: Maximum retries exceeded for tunnel 37760.  Closing.
Jul 19 15:43:50 Ubuntu-Backup-Server xl2tpd[15713]: Terminating pppd: sending TERM signal to pid 15961
Jul 19 15:43:50 Ubuntu-Backup-Server xl2tpd[15713]: pppd 15961 successfully terminated
Jul 19 15:43:50 Ubuntu-Backup-Server xl2tpd[15713]: Connection 24 closed to 216.218.29.182, port 59888 (Timeout)
Jul 19 15:43:55 Ubuntu-Backup-Server xl2tpd[15713]: Unable to deliver closing message for tunnel 37760. Destroying anyway.
```


Here are my L2TP config files...

/etc/xl2tpd/xl2tpd.conf 
```
[global]
ipsec saref = yes

[lns default]
ip range = 192.168.1.110-192.168.1.115
local ip = 192.168.1.10
refuse chap = no
refuse pap = no
require authentication = yes
ppp debug = yes
pppoptfile = /etc/ppp/options.xl2tpd
length bit = yes
```

/etc/ppp/options.xl2tpd 
```
require-mschap-v2
ms-dns 8.8.8.8
ms-dns 8.8.4.4
asyncmap 0
auth
crtscts
lock
hide-password
modem
debug
name l2tpd
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4
noccp
novj
```

/etc/ppp/pptpd-options:
```
name pptpd
proxyarp
nodefaultroute
lock
nobsdcomp 
noaccomp
nopcomp
noauth
mtu 1400
mru 1400
default-asyncmap

```

/etc/ppp/chap-secrets:
```
"root"   l2tpd   linux   *
"olivier"   l2tpd   linux   *
l2tpd   olivier   linux *
test l2tpd testpassword *
```

I'm going crazy right about now..

---

### Post by jmoorse on 2011-07-19
Auth is working fine, it is having problems doing IP control protocol negotiation.

Found something here that might help: [http://ubuntuforums.org/showthread.php?t=1645473&page=3](http://ubuntuforums.org/showthread.php?t=1645473&page=3)

> 
A value in the "ip range" must be used in the /etc/ppp/chap-secrets file. In this case, I used 233. You can add additional users until you fill up the range you specified. You can always expand the range to accommodate more users. Originally I had a * in this file instead of an IP address, I believe this was deprecated in the latest version.


So try:
```

"olivier"   l2tpd   linux   192.168.1.115

```

in /etc/ppp/chap-secrets

---

### Post by OpEn_SoUrCe_RoCkS on 2011-07-20
OMG!! It works :D

I can connect from my MacBook, form my iPhone through Wifi, and through 3G.

However, I have a problem: after I connect to the VPN one time, if I want to reconnect, no matter using which device, I have to restart the ipsec service...
If I dont, the connection times out.

Here's the outout after I connect my iPhone through Wifi the first time (successful):
```
Jul 20 09:38:46 Ubuntu-Backup-Server xl2tpd[25848]: control_finish: Peer requested tunnel 36 twice, ignoring second one.
Jul 20 09:38:46 Ubuntu-Backup-Server xl2tpd[25848]: Connection established to 192.168.1.1, 58360.  Local: 17424, Remote: 36 (ref=0/0).  LNS session is 'default'
Jul 20 09:38:46 Ubuntu-Backup-Server xl2tpd[25848]: start_pppd: I'm running: 
Jul 20 09:38:46 Ubuntu-Backup-Server xl2tpd[25848]: "/usr/sbin/pppd" 
Jul 20 09:38:46 Ubuntu-Backup-Server xl2tpd[25848]: "passive" 
Jul 20 09:38:46 Ubuntu-Backup-Server xl2tpd[25848]: "nodetach" 
Jul 20 09:38:46 Ubuntu-Backup-Server xl2tpd[25848]: "192.168.1.10:0.0.0.0" 
Jul 20 09:38:46 Ubuntu-Backup-Server xl2tpd[25848]: "auth" 
Jul 20 09:38:46 Ubuntu-Backup-Server xl2tpd[25848]: "debug" 
Jul 20 09:38:46 Ubuntu-Backup-Server xl2tpd[25848]: "file" 
Jul 20 09:38:46 Ubuntu-Backup-Server xl2tpd[25848]: "/etc/ppp/options.xl2tpd" 
Jul 20 09:38:46 Ubuntu-Backup-Server xl2tpd[25848]: "/dev/pts/3" 
Jul 20 09:38:46 Ubuntu-Backup-Server xl2tpd[25848]: Call established with 192.168.1.1, Local: 64305, Remote: 2156, Serial: 1
Jul 20 09:38:46 Ubuntu-Backup-Server pppd[27541]: pppd 2.4.5 started by root, uid 0
Jul 20 09:38:46 Ubuntu-Backup-Server pppd[27541]: using channel 111
Jul 20 09:38:46 Ubuntu-Backup-Server modem-manager: (net/ppp1): could not get port's parent device
Jul 20 09:38:46 Ubuntu-Backup-Server NetworkManager[838]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp1, iface: ppp1)
Jul 20 09:38:46 Ubuntu-Backup-Server NetworkManager[838]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp1, iface: ppp1): no ifupdown configuration found.
Jul 20 09:38:46 Ubuntu-Backup-Server pppd[27541]: Using interface ppp1
Jul 20 09:38:46 Ubuntu-Backup-Server pppd[27541]: Connect: ppp1 <--> /dev/pts/3
Jul 20 09:38:46 Ubuntu-Backup-Server pppd[27541]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <auth chap MS-v2> <magic 0xc205c5c0> <pcomp> <accomp>]
Jul 20 09:38:46 Ubuntu-Backup-Server pppd[27541]: rcvd [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x3b02a005> <pcomp> <accomp>]
Jul 20 09:38:46 Ubuntu-Backup-Server pppd[27541]: sent [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0x3b02a005> <pcomp> <accomp>]
Jul 20 09:38:46 Ubuntu-Backup-Server pppd[27541]: rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <auth chap MS-v2> <magic 0xc205c5c0> <pcomp> <accomp>]
Jul 20 09:38:46 Ubuntu-Backup-Server pppd[27541]: sent [LCP EchoReq id=0x0 magic=0xc205c5c0]
Jul 20 09:38:46 Ubuntu-Backup-Server pppd[27541]: sent [CHAP Challenge id=0xe2 <53d65e372ef3f9fe53ce55c6c5b99505>, name = "l2tpd"]
Jul 20 09:38:46 Ubuntu-Backup-Server pppd[27541]: rcvd [LCP EchoReq id=0x0 magic=0x3b02a005]
Jul 20 09:38:46 Ubuntu-Backup-Server pppd[27541]: sent [LCP EchoRep id=0x0 magic=0xc205c5c0]
Jul 20 09:38:46 Ubuntu-Backup-Server pppd[27541]: rcvd [LCP EchoRep id=0x0 magic=0x3b02a005]
Jul 20 09:38:46 Ubuntu-Backup-Server pppd[27541]: rcvd [CHAP Response id=0xe2 <68abd3899e5bd20cfd102a00f2bf165b00000000000000006731af798aca180b0c8c98eb1965d5a912bc49a9421f03bb00>, name = "olivier"]
Jul 20 09:38:46 Ubuntu-Backup-Server pppd[27541]: sent [CHAP Success id=0xe2 "S=2D9C1B31DAAC5167612822E72C970AAEA0E1C3D0 M=Access granted"]
Jul 20 09:38:46 Ubuntu-Backup-Server pppd[27541]: sent [IPCP ConfReq id=0x1 <addr 192.168.1.10>]
Jul 20 09:38:46 Ubuntu-Backup-Server pppd[27541]: rcvd [IPCP ConfReq id=0x1 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 20 09:38:46 Ubuntu-Backup-Server pppd[27541]: sent [IPCP ConfNak id=0x1 <addr 192.168.1.115> <ms-dns1 8.8.8.8> <ms-dns2 8.8.4.4>]
Jul 20 09:38:46 Ubuntu-Backup-Server pppd[27541]: rcvd [IPV6CP ConfReq id=0x1 <addr fe80::0095:8874:1794:1657>]
Jul 20 09:38:46 Ubuntu-Backup-Server pppd[27541]: Unsupported protocol 'IPv6 Control Protovol' (0x8057) received
Jul 20 09:38:46 Ubuntu-Backup-Server pppd[27541]: sent [LCP ProtRej id=0x2 80 57 01 01 00 0e 01 0a 00 95 88 74 17 94 16 57]
Jul 20 09:38:46 Ubuntu-Backup-Server pppd[27541]: rcvd [IPCP ConfAck id=0x1 <addr 192.168.1.10>]
Jul 20 09:38:46 Ubuntu-Backup-Server pppd[27541]: rcvd [IPCP ConfReq id=0x2 <addr 192.168.1.115> <ms-dns1 8.8.8.8> <ms-dns2 8.8.4.4>]
Jul 20 09:38:46 Ubuntu-Backup-Server pppd[27541]: sent [IPCP ConfAck id=0x2 <addr 192.168.1.115> <ms-dns1 8.8.8.8> <ms-dns2 8.8.4.4>]
Jul 20 09:38:46 Ubuntu-Backup-Server pppd[27541]: found interface eth40 for proxy arp
Jul 20 09:38:46 Ubuntu-Backup-Server pppd[27541]: local  IP address 192.168.1.10
Jul 20 09:38:46 Ubuntu-Backup-Server pppd[27541]: remote IP address 192.168.1.115
Jul 20 09:38:46 Ubuntu-Backup-Server pppd[27541]: Script /etc/ppp/ip-up started (pid 27544)
Jul 20 09:38:46 Ubuntu-Backup-Server pppd[27541]: Script /etc/ppp/ip-up finished (pid 27544), status = 0x0
Jul 20 09:38:48 Ubuntu-Backup-Server pppd[26651]: rcvd [LCP EchoReq id=0x5 magic=0x190047f2]
Jul 20 09:38:48 Ubuntu-Backup-Server pppd[26651]: sent [LCP EchoRep id=0x5 magic=0x2bcc1444]
Jul 20 09:38:48 Ubuntu-Backup-Server pppd[26651]: sent [LCP EchoReq id=0x4 magic=0x2bcc1444]
Jul 20 09:38:48 Ubuntu-Backup-Server pppd[26651]: rcvd [LCP EchoRep id=0x4 magic=0x190047f2]

``` 

And this is when I try the second time, unsuccessfully:
```
Jul 20 09:40:39 Ubuntu-Backup-Server xl2tpd[25848]: control_finish: Peer requested tunnel 37 twice, ignoring second one.
Jul 20 09:40:44 Ubuntu-Backup-Server xl2tpd[25848]: last message repeated 2 times
Jul 20 09:40:44 Ubuntu-Backup-Server xl2tpd[25848]: Maximum retries exceeded for tunnel 38525.  Closing.
Jul 20 09:40:48 Ubuntu-Backup-Server xl2tpd[25848]: control_finish: Peer requested tunnel 37 twice, ignoring second one.
Jul 20 09:40:48 Ubuntu-Backup-Server xl2tpd[25848]: Connection 37 closed to 192.168.1.1, port 64072 (Timeout)
Jul 20 09:40:48 Ubuntu-Backup-Server pppd[26651]: sent [LCP EchoReq id=0x8 magic=0x2bcc1444]
Jul 20 09:40:48 Ubuntu-Backup-Server pppd[26651]: rcvd [LCP EchoRep id=0x8 magic=0x190047f2]
Jul 20 09:40:52 Ubuntu-Backup-Server xl2tpd[25848]: control_finish: Peer requested tunnel 37 twice, ignoring second one.
Jul 20 09:40:53 Ubuntu-Backup-Server xl2tpd[25848]: Unable to deliver closing message for tunnel 38525. Destroying anyway.
Jul 20 09:40:56 Ubuntu-Backup-Server xl2tpd[25848]: control_finish: Peer requested tunnel 37 twice, ignoring second one.
Jul 20 09:41:08 Ubuntu-Backup-Server pppd[26651]: rcvd [LCP EchoReq id=0xb magic=0x190047f2]
Jul 20 09:41:08 Ubuntu-Backup-Server pppd[26651]: sent [LCP EchoRep id=0xb magic=0x2bcc1444]
```

If I restart the ipsec service, everything is fine... Until I try to reconnect the second time.

What could be causing this? I'm guessing the "maximum retries" bit is a hint??

---

### Post by jmoorse on 2011-07-20
How quick between tunnels are you trying?  It looks like it still has your old connection lingering, and because there is a single IP bound to the username it denies further connections.  Can you let it sit idle for a few min, or perhaps allocate a range of IPs to the username to test?

---

### Post by entropictrophy on 2011-07-20
[FONT=Arial, sans-serif][SIZE=2]Hey, I feel your pain. I just dove into setting up a poptop vm recently for andriod devices. Now, it works so well, that I use it with windows, linux, and android phones. Here is a helpful guide: [http://eran.sandler.co.il/2010/08/30/pptp-vpn-on-ubuntu-10-04-for-your-iphone-ipad/](http://eran.sandler.co.il/2010/08/30/pptp-vpn-on-ubuntu-10-04-for-your-iphone-ipad/)

Unfortunately, I was still having problems with web traffic until the MTU was changed to accommodate the extra protocol overhead . If you find that you can connect clients to the vpn successfully (i.e. access shares and intranet sites), but have trouble with external sites - try adjusting the MTU in "/etc/ppp/ip-up". Add a line after the header with:[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2] [/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]"ifconfig[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2] [/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]$1 mtu 1400". 
[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]
[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]
[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]
[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]If you are just using wanted to use windows clients, you could also do a split-tunnel by changing the default gateway option on ppp settings under vpn properties. However, this method is not ideal.
[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]


[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]Hope this helps.[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2] [/SIZE][/FONT]

---

### Post by jmoorse on 2011-07-20
Just to clarify, reconnection problems are _not_ related to MTU issues.

---

### Post by entropictrophy on 2011-07-20
> **jmoorse said:**
> Just to clarify, reconnection problems are _not_ related to MTU issues.

Thanks, I more or less just wanted to make a suggestion in the event L2TP/IPsec was becoming too burdensome to set up and troubleshoot. The OP had given up on pptp, but I (being ever so green) had mine set up in 30min.

---

### Post by OpEn_SoUrCe_RoCkS on 2011-07-21
> **jmoorse said:**
> How quick between tunnels are you trying?  It looks like it still has your old connection lingering, and because there is a single IP bound to the username it denies further connections.  Can you let it sit idle for a few min, or perhaps allocate a range of IPs to the username to test?

Well I tried waiting a bit, but it still doesn't change anything.

I tried changing the chap-secrets file to allocate an IP address range to the user "olivier", but without success. I tried:
192.168.1.100-199
192.168.1.100-192.168.1.199
192.168.1.100/27

Nothing worked!!
I then repeated the line one time for each address, up to .115, but still to no avail.

```
"olivier"   l2tpd   linux   192.168.1.100
"olivier"   l2tpd   linux   192.168.1.101
"olivier"   l2tpd   linux   192.168.1.102
"olivier"   l2tpd   linux   192.168.1.103
"olivier"   l2tpd   linux   192.168.1.104
"olivier"   l2tpd   linux   192.168.1.105
"olivier"   l2tpd   linux   192.168.1.106
"olivier"   l2tpd   linux   192.168.1.107
"olivier"   l2tpd   linux   192.168.1.108
"olivier"   l2tpd   linux   192.168.1.109
"olivier"   l2tpd   linux   192.168.1.110
"olivier"   l2tpd   linux   192.168.1.111
"olivier"   l2tpd   linux   192.168.1.112
"olivier"   l2tpd   linux   192.168.1.113
"olivier"   l2tpd   linux   192.168.1.114
"olivier"   l2tpd   linux   192.168.1.115
```

When I disconnect and attempt to reconnect, I still get the dreaded "maximum retries" error. 
And say I connect using my MacBook, it gets 192.168.1.100... And if I connect my iPhone at the same time, it alos gets .100... So I'm guessing I did something wrong.

Could my woes have something to do with this message I get when starting ipsec?
```
Jul 21 10:32:36 Ubuntu-Backup-Server ipsec_setup: ...Openswan IPsec started
Jul 21 10:32:36 Ubuntu-Backup-Server ipsec__plutorun: adjusting ipsec.d to /etc/ipsec.d
Jul 21 10:32:36 Ubuntu-Backup-Server pluto: adjusting ipsec.d to /etc/ipsec.d
Jul 21 10:32:36 Ubuntu-Backup-Server ipsec__plutorun: 002 added connection description "L2TP-PSK-NAT"
Jul 21 10:32:36 Ubuntu-Backup-Server ipsec__plutorun: 002 added connection description "L2TP-PSK-noNAT"
Jul 21 10:32:36 Ubuntu-Backup-Server ipsec__plutorun: 003 NAT-Traversal: Trying new style NAT-T
Jul 21 10:32:36 Ubuntu-Backup-Server ipsec__plutorun: 003 NAT-Traversal: **ESPINUDP(1) setup failed for new style NAT-T family IPv4 (errno=19)**
Jul 21 10:32:36 Ubuntu-Backup-Server ipsec__plutorun: 003 NAT-Traversal: **Trying old style NAT-T**
```

Just wondering...

Here is my ipsec.conf:
```
# /etc/ipsec.conf - Openswan IPsec configuration file

# This file:  /usr/share/doc/openswan/ipsec.conf-sample
#
# Manual:     ipsec.conf.5


version	2.0	# conforms to second version of ipsec.conf specification

# basic configuration
config setup
	# Do not set debug options to debug configuration issues!
	# plutodebug / klipsdebug = "all", "none" or a combation from below:
	# "raw crypt parsing emitting control klips pfkey natt x509 dpd private"
	# eg:
	# plutodebug="control parsing"
	#
	# enable to get logs per-peer
	# plutoopts="--perpeerlog"
	#
	# Again: only enable plutodebug or klipsdebug when asked by a developer
	#
	# NAT-TRAVERSAL support, see README.NAT-Traversal
	nat_traversal=yes
	# exclude networks used on server side by adding %v4:!a.b.c.0/24
	virtual_private=%v4:10.0.0.0/8,%v4:192.168.0.0/16,%v4:172.16.0.0/12
	# OE is now off by default. Uncomment and change to on, to enable.
	oe=off
	# which IPsec stack to use. netkey,klips,mast,auto or none
	protostack=netkey
	

# Add connections here

# sample VPN connection
# for more examples, see /etc/ipsec.d/examples/
#conn sample
#		# Left security gateway, subnet behind it, nexthop toward right.
#		left=10.0.0.1
#		leftsubnet=172.16.0.0/24
#		leftnexthop=10.22.33.44
#		# Right security gateway, subnet behind it, nexthop toward left.
#		right=10.12.12.1
#		rightsubnet=192.168.0.0/24
#		rightnexthop=10.101.102.103
#		# To authorize this connection, but not actually start it, 
#		# at startup, uncomment this.
#		#auto=start

conn L2TP-PSK-NAT
    #rightsubnet=vhost:%priv
    rightsubnet=vhost:%no
    also=L2TP-PSK-noNAT

conn L2TP-PSK-noNAT
    authby=secret
    pfs=no
    auto=add
    keyingtries=3
    rekey=no
    ikelifetime=8h
    keylife=1h
    type=transport
    left=192.168.1.10
    leftprotoport=17/1701
    leftnexthop=%defaultroute
    rightnexthop=%defaultroute
    right=%any
    rightprotoport=17/%any
```

EDIT: I found this page which looks promising (perhaps?) but I can't make head nor tail of it!!
[http://lists.virus.org/users-openswan-0702/msg00161.html](http://lists.virus.org/users-openswan-0702/msg00161.html)
The guy has a similar problem, and he found a solution it seems... If only I could figure out what the solution is! xD

---

### Post by jmoorse on 2011-07-21
Not sure what is going on here.  Have you tried openVPN?

---

### Post by OpEn_SoUrCe_RoCkS on 2011-07-22
No, OpenVPN isn't an option for me; iOS allows for PPTP, L2TP, and IPSec VPN connections. OpenVPN uses some sort of SSL authentication. An OpenVPN client for iOS isn't a viable solution for me..

---

