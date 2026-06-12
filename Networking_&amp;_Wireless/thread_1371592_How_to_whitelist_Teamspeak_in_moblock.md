---
title: "How to whitelist Teamspeak in moblock"
date: 2010-01-03
forum: Networking &amp; Wireless
---

### Post by NiksaVel on 2010-01-03
Hi,

can anyone help me with this?  Moblock is blocking my teamspeak server...  only some of my friends cant connect so I assume their ISPs are in the blocklists... I've tried whitelisting TCP IN and OUT for 9987 which is the default port... but still no luck..


any ideas?

---

### Post by jre on 2010-01-06
I don't know teamspeak. So just a general answer:
It depends how teamspeak works, for what I would recommend: if there are many IPs, that probably even change frequently, then it is easier to whitelist the port. But if there is only one or a few servers, with fixed IPs, then you should whitelist IPs.

To learn, what get's blocked I recommend that you use mobloquer, or follow the logfile live
```
tail -f /var/log/moblock.log
```
There you can see which IP gets blocked.

You can even get more information about what is being blocked. Set in /etc/blockcontrol/blockcontrol.conf
```
LOG_IPTABLES="LOG --log-level info"
```
Then do a
```
sudo blockcontrol restart
```
Then you can issue
```
tail -f /var/log/syslog
```
(perhaps you have to add "sudo" here, because syslog sometimes is not readable by normal users). There you see the IP, the port, and protocol of blocked packets. That should help you to find the correct thing to whitelist.

In the logfiles you can also see whether you have to care about **in**coming or about **out**going connections.

---

