---
title: "Firewall Issues"
date: 2009-12-06
forum: Networking &amp; Wireless
---

### Post by moranned on 2009-12-06
I am attempting to configure a spamtrap on my home network so that I can safely test malicious code without spamming the Internet.

I have built a dual-homed ubuntu server with two NICs. NIC 1 connects to the Internet via my router and is assigned a 10.0.1.X address. I assigned NIC 2 with a static IP address of 192.168.1.X. I configured a windows machine with a static IP at 192.168.1.X. The windows machines uses my Ubuntu server as its gateway. Im using Guarddog and Guidedog to configure my firewall rules. 

The windows machine can connect through the Ubuntu server to browse the Internet with no problems. However, when I attempt to send email I get connection errors on my windows machine.

My syslog throughs the following errors:
DROPPED IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:24:e8:f2:68:67:08:00 SRC=192.168.1.2 DST=192.168.1.255 LEN=236 TOS=0x00 PREC=0x00 TTL=128 ID=1116 PROTO=UDP SPT=138 DPT=138 LEN=216

As Im able to get http outbound on my windows machine, I suppose my firewall is dropping SMTP packets but I dont see anything in my log to indicate this is happening.

Any ideas?

---

