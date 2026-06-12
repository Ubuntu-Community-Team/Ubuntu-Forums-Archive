---
title: "iptables and DNAT problem"
date: 2011-03-10
forum: Networking &amp; Wireless
---

### Post by ant2ne on 2011-03-10
I'm having a complicated iptables problem. And it is complicated in that I can't google a solution, because I can't describe the problem in a simple way.

I'm using a linux poweredge 1750 with 4 ethernet interfaces and 1 wireless interface as a router/firewall/wireless access point. 

The Computers on the inside can connect and communicate just fine. The access the outside world and other internal devices with no problems.

DNAT from the outside works just fine for things like ssh, webmin and http. But some protocols and services (ftp with filezilla and runuo) use ports to connect. And then, it is like they hand off the rest of the communication to other seemingly randomly determined ports. And that is when the conversation gets dropped. How do I configure my router to notice these port changes and continue to DNAT the conversation?

Or am I misinterpreting what is going on?

And I swear if someone links me to [http://ubuntuforums.org/newthread.php?do=newthread&f=336]("http://ubuntuforums.org/newthread.php?do=newthread&f=336") I'm going to scream!!

---

### Post by SeijiSensei on 2011-03-10
FTP is a notoriously difficult service to configure to work with firewalls.  One set of solutions is to use "[passive mode]("http://slacksite.com/other/ftp.html")" where possible.  Other solutions rely on application-level proxies like [http://www.ftpproxy.org/](http://www.ftpproxy.org/).

---

### Post by ant2ne on 2011-03-15
well this got runuo to work

```
iptables -t nat -A PREROUTING -p tcp --dport 2593 -j DNAT --to $_RUNUO:2593
iptables -t nat -A POSTROUTING -s $_RUNUO -p tcp --sport 2593 -j SNAT --to-source $_GATEWAY
iptables -A INPUT -d $_RUNUO -p tcp --dport 2593 -j ACCEPT
iptables -A OUTPUT -s $_RUNUO -p tcp --dport 2593 -j ACCEPT
```still working on ftp

---

