---
title: "security logging program to view realtime incoming connections?"
date: 2013-01-06
forum: Networking &amp; Wireless
---

### Post by sdowney717 on 2013-01-06
Does this exist?

I see this in one of my routers, that it logs incoming connections.
And it helped me figure out why an incoming connection was being 
blocked.

I want to see what is happening to an incoming connection as I ping my ubuntu PC

AND

Does a program like that exist for windows?

---

### Post by chadk5utc on 2013-01-06
Most commercial routers have the option for remote syslog which allows you to setup a central logging server. There are a number of apps that will do I think what your looking for I believe one of which is "Splunk" it does take some setup to get it going. If in linux goto a terminal 
> 
cd /var/log
tail -f somelogfile
This will show all connections in and out and can scroll pretty fast. Also on command you can use "iftop"

---

