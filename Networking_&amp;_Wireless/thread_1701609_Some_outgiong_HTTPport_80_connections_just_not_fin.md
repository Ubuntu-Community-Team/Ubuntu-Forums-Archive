---
title: "Some outgiong HTTP/port 80 connections just not finishing.."
date: 2011-03-06
forum: Networking &amp; Wireless
---

### Post by thebest45 on 2011-03-06
I'm running Ubuntu 10.04.2 LTS as a production server for a Ruby on Rails application. The application works just fine - incoming traffic always gets to my server, is routed to apache correctly, and then the right response is returned.

Outgoing traffic, however, not so fine. Outgoing email seems to work without trouble, as all the emails my program sends are delivered, but connecting to any external website doesn't always work however.

Here's what I've done to try to test:
wget [www.yahoo.com](www.yahoo.com) -dvS
```

username@www:~/temp$ wget www.yahoo.com -dvS
Setting --verbose (verbose) to 1
Setting --server-response (serverresponse) to 1
DEBUG output created by Wget 1.12 on linux-gnu.

--2011-03-06 17:03:58--  http://www.yahoo.com/
Resolving www.yahoo.com... 67.195.160.76, 69.147.125.65, 209.191.122.70
Caching www.yahoo.com => 67.195.160.76 69.147.125.65 209.191.122.70
Connecting to www.yahoo.com|67.195.160.76|:80... connected.
Created socket 3.
Releasing 0x0000000001d88ba0 (new refcount 1).

---request begin---
GET / HTTP/1.0
User-Agent: Wget/1.12 (linux-gnu)
Accept: */*
Host: www.yahoo.com
Connection: Keep-Alive

---request end---
HTTP request sent, awaiting response... 

```

And then it sits at "awaiting response..." forever (well, it reaches the timeout in about 30 seconds and tries again). It will complete about 1 out of 25 or so times, though. But it's not the website I'm connecting to that has anything wrong with it.

I have a separate Ubuntu machine, same version, connected to the same router. The commands always work there. The exact same wget command will download any webpage just fine.

I've played with a few tools to try to diagnose the problem. "mtr" doesn't seem to say there's any ping loss.

Netstat lists and "ESTABLISHED" connection to the Yahoo IP (your yahoo IP will probably be diff than mine, because of location routing).
netstat -WvnNepa
```
tcp        0      0 192.168.0.2:48290       69.147.125.65:80        ESTABLISHED 1000       10499597    17151/wget
```

But here's another interesting point I found. If I run "sudo nast", usually the connection will work a few times (eg wget will fully/finish downloading the file)... then sometimes it won't.


Possible ideas:
* Maybe the amount of incoming traffic for the webserver is causing a TCP limit to be reached or some other kind of network error
* Too much incoming traffic clogs up outgoing traffic
* Any of a million other things.

Any good ideas?

---

### Post by thebest45 on 2011-03-07
Anything?

---

