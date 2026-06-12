---
title: "netstat question"
date: 2006-06-09
forum: Networking &amp; Wireless
---

### Post by keithjr on 2006-06-09
This is fairly simplistic but I can't seem to find an answer, not even in docs, mans or google...

I want to know what I have to issue to the "netstat" command to make it only display the "Active Internet connections (w/o servers)" field, without displaying the "Active UNIX domain sockets (w/o servers)."  The information in the latter isn't terribly important to me, but it is VERY cumbersome.  

Thanks!

---

### Post by ns2048 on 2006-06-09
Hello,

# Active Internet connections (w/o servers) TCP
netstat -tn

# Active Internet connections (w/o servers) UDP
netstat -un

--ns2048

---

### Post by keithjr on 2006-06-09
aha!  thank you.  -tn is nice but it also shows time-wait connections... but I can do this...

netstat -tn | grep ESTABLISHED

I indend to make a nice monitoring script with these... more on this later

---

