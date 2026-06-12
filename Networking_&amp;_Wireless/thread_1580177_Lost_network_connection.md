---
title: "Lost network connection"
date: 2010-09-23
forum: Networking &amp; Wireless
---

### Post by Jaydman on 2010-09-23
Hello all.
Here is my problem. I have a duel boot Ubuntu 10 and windows 7 on my desktop and a duel boot ubuntu 10 and windows 7 on my lap top. I have a wireless router dlink 524 for all the connections and have never had a problem. I have connection on all now but my Ubuntu 10 desktop. I tried everything I can think of to get it back. I tried to use my browser to ping the router, but no luck. On a hunch I put in my live disk of Ubuntu 10 and I have a connection. Anyone have an idea what this problem can be? Could it be a bad update?

Thanks for the help
Jay

---

### Post by SaintDanBert on 2010-09-23
First, do you have Intel network parts?
```

lspci | grep -i intel | grep -i net

```

Next, which driver are you using?
```

sudo lsmod | less

```
Search for "network" then scan down looking for parts that read "driver=something". 
[color=orange]There are known issues with the [highlight] iwlagn [/highlight] driver for Intel wireless.[/color] I do not know about a resolution for the driver issue.

Based on what I read in other postings (that I cannot find right now), there is a work around if you use Intel network hardware.
[list]
[*]connect to wired network
[*]use package manager to **completely remove** network-manager.
[*]reboot -- the wired network takes over
[*]make sure that network-manager, and its parts are gone
[*]install **wicd** package -- fetched from the repositories
[*]disconnect the wired network and reboot
[*]use wicd to find and connect to wireless
[*]drink your health and success (grin)
[/list]
I had several lost connections per day with network-manager.
I've not had a lost connection since loading wicd.
I have Intel 4965AGN hardware with the iwlagn driver.

If you have other network hardware, the switch to wicd may or may not help. There are lots of posts about these issues for all sorts of Intel network hardware.

I also had some troubles with D-Link routers and access points. They play some interesting and useful games with DNS and caching that would sometimes not play well with linux (vs. win-doze). Eventually, I left D-Link for Netgear parts. That and wicd have sent my tribulations packing.

Bonne chance,
~~~ 0;-Dan

By the way:  "duel" is a contest between persons over a matter of honor.
I think you mean "dual" meaning "two of something".

---

### Post by Jaydman on 2010-09-23
Thanks for the reply. I will look those items up. The problem is occuring with my wired computer. If I switch over to my windows 7 there is no problem. If I put in my live disk there is no problem. So my guess is that its a software issue.

P.s. your right it is dual, however there is a duel going on with Ubuntu and Windows 7 on my system. Ubuntu usually wins but right now, well not sure..lol

Jay

---

### Post by SaintDanBert on 2010-09-23
I completely missed the pun -- intentional or otherwise. I'm think like that
... sometimes.

Let us know how you sort this out.
~~~ 0;-Dan

---

