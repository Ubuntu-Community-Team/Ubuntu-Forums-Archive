---
title: "Connection trouble, Gateway."
date: 2009-10-31
forum: Networking &amp; Wireless
---

### Post by MagusZero on 2009-10-31
I was quite pleased upon buying my Gateway P-6860FX gaming laptop, as it'd quite obviously a decent computer. I'm generally a windows user, but I generally have some version of linux around... until 9.04. 8.10 worked, and I was able to connect to networks and recieve updates and drivers allowing my computer to function. HOWEVER! On installing 9.04, I noticed that while my computer DID, in fact, connect to both my wireless and wired networks and successfully aquired IP addresses for each of them, I cannot, in fact, use any internet applications. It's not impossible that a driver update could, in fact, solve the problem, but considering it hasn't always been a problem for this model and that I can't really update without internet, I decided to look for assistance here.

---

### Post by Iowan on 2009-10-31
I didn't think Network Manager would enable two devices simultaneously, but (like you) I recently discovered otherwise.  Do both networks connect to Internet? You can check **route** from a terminal to see where traffic is going, and contents of */etc/resolv.conf* should show which nameservers are being used (but not necessarily which interface).

---

### Post by MagusZero on 2009-10-31
They're the same two networks I'm connected to on windows: the same router, by ethernet and wireless. Both do connect to the internet perfectly on windows; in fact that's how I'm typing this now. That's why it's so odd that I don't get network access on kubuntu. I successfully join, but no internet. Both connections say active. I'll check the route and such later.

---

### Post by Oropher8598 on 2009-10-31
There used to be a problem where, with more than one network connection active, Ubuntu broadcasts some stuff that upsets routers... maybe it's worth trying just one connection?

---

### Post by MagusZero on 2009-11-01
Well, of course I tried that; wasn't any different though. And my hardware was at least somewhat suppored in 8.10, where I had full network access; 9.04 wouldn't connect at all. This one does but... doesn't work.

---

### Post by MagusZero on 2009-11-01
Oddly enough, I have connection at the university, with their horribly slow internet. When I got home, I connected to our wireless and had a connection of sorts... but not for long. I was able to recieve the package list, for instance, but it couldn't find it when I tried downloading packages, and when I tried to go to a website, it still didn't work. It had right when I booted. Quite odd indeed.

---

### Post by Iowan on 2009-11-02
When you lose the connection (at home), does it lose connection with router (ping?) or *just* internet? Do contents of */etc/resolv.conf* change?

---

### Post by MagusZero on 2009-11-03
I can still ping the router, and that file's contents are it's ip.

---

### Post by MagusZero on 2009-11-06
...Would still like to get some idea of what's going wrong and more importantly how to go about fixing it.

---

### Post by steff123 on 2009-11-06
Got the same problem. Wireless works but wired connections fail. Though I can see all machines and printers in my home-network, also the gateway but dial out is impossible. So I got no internet. The resolv.conf can't be edited because avahi overwrites all changes, also in /etc/hosts (why do I have the feeling that I gonna hate avahi?).

Any ideas?

Cheers,
Steff

---

### Post by MagusZero on 2009-11-09
To clarify, all websites, including google, return "Server refused connection." Since the package manager does this, kubuntu is unuseable atm.

---

### Post by MagusZero on 2009-11-16
Real great help guys.

---

### Post by Iowan on 2009-11-16
Thought you fixed it - or gave up.  
Post results of **route -n** That should show where traffic *should* be going.

---

### Post by MagusZero on 2009-12-02
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
10.0.0.0        0.0.0.0         255.0.0.0       U     2      0        0 wlan0
0.0.0.0         10.1.1.1        0.0.0.0         UG    0      0        0 wlan0
```

[IMG]http://i140.photobucket.com/albums/r6/MagusSergeX/snapshot1.png[/IMG]

---

### Post by Iowan on 2009-12-02
I presume a **ping** of google.com (or 74.125.67.100) doesn't work?

---

### Post by MagusZero on 2009-12-02
Okay, this time when I booted linux, it wouldn't connect to our wireless connection; kept asking for the passphrase endlessly, ineffectively. So I plugged in the ethernet and it said activated, so I pinged google. No problem.

Used the google search again, same as the picture before.

---

### Post by MagusZero on 2009-12-05
Couple days have passed.

---

### Post by MagusZero on 2009-12-08
Couple more days have passed.

---

### Post by Iowan on 2009-12-08
The last line under Possible Causes mentions a firewall. 
What are the results of **sudo iptables -L**?

---

### Post by MagusZero on 2009-12-09
Got 3 things that said accepted. My firewall is off in my router, just some filtering things that were there by default are on. 

[IMG]http://i140.photobucket.com/albums/r6/MagusSergeX/snapshot3.jpg[/IMG]

Also, checking other websites, there's exactly one that works, homestarrunner.com. Some sites manage to give their basic info on the titlebar, but since I don't have flash player none of it really matters. 

Booted in windows like now, no problems at all.

---

### Post by Iowan on 2009-12-09
> **MagusZero said:**
> Got 3 things that said accepted.Could you post hte results?

---

### Post by MagusZero on 2009-12-11
^[[AChain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

---

### Post by Iowan on 2009-12-11
Thanks - that looks plain enough. It would seem that Ubuntu's firewall isn't blocking anything.
<scratching head> Wonder what else might be causing server to refuse connection...

---

### Post by Iowan on 2009-12-13
I really doubt this will help, but I hate to give up...
I stumbled across a thread that mentioned having problems connecting to websites. Their solution was to change MTU from 1500 to 1492.
This machine works fine with MTU 1500...

---

### Post by MagusZero on 2009-12-14
How would I do that?

---

### Post by Iowan on 2009-12-14
Good question...
I haven't tried it, but from what **man ifconfig** suggests, **sudo ifconfig eth0 MTU 1492** looks like the command. If it works - it may only work until the next reboot. On the other hand, if it messes up, a reboot should fix it...
Again, I don't expect that to fix it - but I'd be delighted to be wrong.

---

