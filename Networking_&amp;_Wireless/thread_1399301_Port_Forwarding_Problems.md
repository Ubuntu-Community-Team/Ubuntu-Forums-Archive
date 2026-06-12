---
title: "Port Forwarding Problems"
date: 2010-02-05
forum: Networking &amp; Wireless
---

### Post by ve4cib on 2010-02-05
At work our main router/firewall is an Ubuntu 9.10 server.  Our resident network admin has recently left, and since I'm the only one here with any kind of Linux experience I've inherited the job.

Unfortunately all of my Linux experience has been desktop-oriented.  The closest to editing iptables I've come is by using Firestarter and Gufw.  And I've been banging my head against this problem for the last hour or so.  So any help would be appreciated!

**The Problem**

We have a server running some web-app demos that a client wants to see.  So we need to forward a port from the internet to our Windows server.  Doesn't really matter which port.  I arbitrarily chose 2900 since it was a nice-looking number and we're not using it for anything else.  I've set up IIS on our windows server to listen on port 2900, and that works from behind our firewall.

So the obvious thing to do is simply forward connections on port 2900 to the Windows server.  Should be easy, right?

I've exported our current iptables rules and backed them up.  I'm editing a copy (and then using iptables-restore to apply the changes).  I've tried several walk-throughs and none of them have worked.  Currently I have the following:

```
*nat
:PREROUTING ACCEPT [x:y] # 2900 is in the range x:y
...
# x.x.x.x is the machine's internet-facing IP address
-A PREROUTING -d x.x.x.x/32 -p tcp -m tcp --dport 2900 -j DNAT --to-destination 192.168.1.165
...

*filter
:INPUT DROP [x:y] #2900 is outside of this range
:FORWARD ACCEPT [0:0]  #I've tried changing this, but it didn't seem to make a difference, so I put it back the way I found it
:OUTPUT DROP [0:0] #do I need to change this?
...
-A FORWARD -d 192.168.1.165/32 -i eth1 -o eth0 -p tcp -m tcp --dport 2900 -m state --state NEW,RELATED,ESTABLISHED,-j ACCEPT
...
```

Now, I will be quite honest and say that I have no idea what those do.  I've copied-and-pasted existing rules and modified them, changed them to follow tutorials, etc... and nothing has worked.

When I nmap the server port 2900 is listed as "filtered".  What am I doing wrong?

---

### Post by ve4cib on 2010-02-08
...anyone? :(

---

