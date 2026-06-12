---
title: "Shutdown squid via web page"
date: 2011-02-28
forum: Networking &amp; Wireless
---

### Post by tux43 on 2011-02-28
All,

I would like to be able to shutdown squid (/etc/init.d/squid stop) via a web URL. Does anybody know if something exists like this, or do I need to write a CGI script or equivalent?

FWIW: Yes, I have an 8 year old son that needs some persuasion to GET OFF THE COMPUTER ;-).

---

### Post by SeijiSensei on 2011-02-28
That's actually a bit complicated since you'd need to run the shutdown command as root while Apache runs as the unprivileged "www-data" user.  You could write a web script that would put the request in a queue, and a program that runs from cron to check the queue and shuts down if the request is found.

However, I'd suggest that using SSH to connect to the server and shutting down squid from the command line is a lot easier approach.  If you need to connect from Windows, use the [Putty SSH]("http://www.chiark.greenend.org.uk/~sgtatham/putty/") client.

Another approach is to take advantage of the rich set of "ACL" rules available in squid.conf.  You can write rules that limit when the cache is active by time of day.  You can even combine rules so that IP address 10.1.1.1 can connect only from 4pm to 6pm on weekdays, but other IP addresses have not limits.  The rules are fairly self-evident and detailed in /etc/squid/squid.conf.

I might suggest adding some rules to block executables like this:

```

acl EXE url_regex \.exe$
http_access EXE deny

```

Together these block downloads of files ending in ".exe".  You might want to block .bat, .cab, etc., as well.  If you need to install such files yourself, you can write a rule that exempts the IP of your machine.

---

