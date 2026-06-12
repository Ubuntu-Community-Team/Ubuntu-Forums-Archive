---
title: "Filter Remote Syslog Mesages Into Seperate File"
date: 2005-12-27
forum: Networking &amp; Wireless
---

### Post by ubuntuuser on 2005-12-27
Hey guys. I started a related thread a few days ago, but didn't receive any replies, and the overall situation has changed, so I start a new one. I have set up my router/firewall to send its system logs to my PC, where I have the syslogd configured to receive remote syslog messages. I know that the router is sending the messages to the PC cause I checked the various log files in /var/log/ for messages from my router. Ok, what I would like to setup is something to filter all my router messages, and only these, into one seperate file.

Is there a way I could make syslogd save all remotely received messages to a file, for example /var/log/router.log?
I thought about different workarounds, like setting up a cronjob that regularly reads all logs and does a ```
grep routerIPhere /var/log/* > /var/log/router.log
``` BUT I would like to have the router log displayed inside a terminal via ```
tail -f /var/log/router.log
```
and so the solution above is not practical, cause permantently scanning my logs is of course not possible ;-)
I am open for any qualified suggestions, thanks in advance.

---

### Post by Susana on 2005-12-27
> **ubuntuuser]
and so the solution above is not practical, cause permantently scanning my logs is of course not possible  said:**
> 

Did you try adding a rule to syslog.conf. Something like 
*routerIPhere*     -/var/log/router.log

[QUOTE=ubuntuuser]I am open for any qualified suggestions, thanks in advance.

hmm this is not a qualified suggestion, i have no idea if this will work. But try man syslog.conf it must be a rule in there that you're missing.

---

### Post by ubuntuuser on 2005-12-28
Just in case somebody has the same problem in the future, I found an acceptable workaround.

I did some packet monitoring while provoking some action that was definitely going to be logged and sent to my PC. This way I was able to find out that the sent messages all were LOCAL0.* messages. So all I had to do was telling syslogd to write all messages with that facility to a new log file. This way, at least most messages are logged in router.log (except things like AUTH, CRIT. and so on, but I can live with that).

---

