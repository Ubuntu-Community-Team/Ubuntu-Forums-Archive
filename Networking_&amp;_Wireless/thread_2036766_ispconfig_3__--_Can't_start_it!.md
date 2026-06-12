---
title: "ispconfig 3  -- Can't start it!"
date: 2012-08-02
forum: Networking &amp; Wireless
---

### Post by AlexBooton on 2012-08-02
I followed Falco's great instructions ([The Perfect Server - Ubuntu 12.04 LTS (Apache2, BIND, Dovecot, ISPConfig 3)]("http://www.howtoforge.com/perfect-server-ubuntu-12.04-lts-apache2-bind-dovecot-ispconfig-3")) pretty much to the letter but when I get to the last page which says to go here: ```
http(s)://192.168.0.100:8080/ 
``` FireFox just says "Unable to connect".

I actually used localhost:8080 and [https://localhost:8080](https://localhost:8080) and got the same non-result with both.

The installation also says you can start the service as a startup job but doesn't give the name of the job?  Is it ispconfig, ispconfig3, ispconfig 3 or what?

The installation also set up a cron job.  I tried running the command as root ```
/usr/local/ispconfig/server/server.sh > /dev/null 2>> /var/log/ispconfig/cron.log
```.  It didn't seem to do anything and made no entry in /var/log/ispconfig/cron.log

Also, ps -e | grep isp shows nothing.

So what's going on?  How do you get ispconfig running?

Thanks

---

