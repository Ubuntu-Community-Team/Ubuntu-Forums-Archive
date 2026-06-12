---
title: "For people familiar with barry. and blackberrys."
date: 2009-09-20
forum: Networking &amp; Wireless
---

### Post by sent17inel on 2009-09-20
I am trying to get my blackberry tour to work as a usb modem using barry. I have been following this thread here.  and have followed the directions as best I can. I even changed my network manager to WICD just like the guy who wrote the tutorial. It seems to work but here is my terminal output. Maybe you can see what im doing wrong?  Please and thank you.   


daniel@2ls49r:~$ sudo pppd call barry-sprint
Script /usr/sbin/chat -f /etc/chatscripts/barry-sprint.chat finished (pid 24666), status = 0x0
Serial connection established.
using channel 3
Using interface ppp0
Connect: ppp0 <--> /dev/pts/4
sent [LCP ConfReq id=0x1 <asyncmap 0x0>]
rcvd [LCP ConfReq id=0x6 <asyncmap 0x0> <magic 0x4bbfbd80> <pcomp> <accomp>]
sent [LCP ConfRej id=0x6 <magic 0x4bbfbd80> <pcomp> <accomp>]
rcvd [LCP ConfNak id=0x1 <magic 0x4bbfb158> <pcomp> <accomp>]
sent [LCP ConfReq id=0x2 <asyncmap 0x0>]
rcvd [LCP ConfReq id=0x7 <asyncmap 0x0>]
sent [LCP ConfAck id=0x7 <asyncmap 0x0>]
rcvd [LCP ConfNak id=0x2 <magic 0x4bbfb158> <pcomp> <accomp>]
sent [LCP ConfReq id=0x3 <asyncmap 0x0>]
rcvd [LCP ConfNak id=0x3 <magic 0x4bbfb158> <pcomp> <accomp>]
sent [LCP ConfReq id=0x4 <asyncmap 0x0>]
rcvd [LCP ConfAck id=0x4 <asyncmap 0x0>]
sent [IPCP ConfReq id=0x1 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
rcvd [LCP DiscReq id=0x8 magic=0x4bbfbd80]
rcvd [IPCP ConfReq id=0x2 <addr 68.28.57.69>]
sent [IPCP ConfAck id=0x2 <addr 68.28.57.69>]
rcvd [IPCP ConfNak id=0x1 <addr 173.116.232.20> <ms-dns1 68.28.58.92> <ms-dns2 68.28.50.91>]
sent [IPCP ConfReq id=0x2 <addr 173.116.232.20> <ms-dns1 68.28.58.92> <ms-dns2 68.28.50.91>]
rcvd [IPCP ConfAck id=0x2 <addr 173.116.232.20> <ms-dns1 68.28.58.92> <ms-dns2 68.28.50.91>]
Cannot determine ethernet address for proxy ARP
local  IP address 173.116.232.20
remote IP address 68.28.57.69
primary   DNS address 68.28.58.92
secondary DNS address 68.28.50.91
Script /etc/ppp/ip-up started (pid 24709)
Script /etc/ppp/ip-up finished (pid 24709), status = 0x0
^Cselect(): Interrupted system call
Terminating on signal 2
Connect time 1.0 minutes.
Sent 0 bytes, received 0 bytes.
Script /etc/ppp/ip-down started (pid 25189)
sent [LCP TermReq id=0x5 "User request"]
Script /etc/ppp/ip-down finished (pid 25189), status = 0x0
sent [LCP TermReq id=0x6 "User request"]
Connection terminated.
Modem hangup
Waiting for 1 child processes...
  script /usr/sbin/pppob, pid 24664
sending SIGTERM to process 24664
daniel@2ls49r:~$

---

### Post by sent17inel on 2009-09-20
I also think it could have to do with the fact that I dont have the correct "Carrier specific APN/TCP settings" on my blackberry. Right now those are left as blank. I searched at this site here  [http://www.blackberryfaq.com/index.php/Carrier_specific_APN/TCP_settings](http://www.blackberryfaq.com/index.php/Carrier_specific_APN/TCP_settings) and they dont have sprints settings listed. any ideas?

---

