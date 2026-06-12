---
title: "bind program to network interface?"
date: 2011-06-17
forum: Networking &amp; Wireless
---

### Post by trift on 2011-06-17
Is there any way in a machine with 2 (or more) network devices to only allow 1 program to use interface1 and force all other programs to use the other?

---

### Post by trift on 2011-07-20
bump

---

### Post by karlson on 2011-07-20
> **trift said:**
> Is there any way in a machine with 2 (or more) network devices to only allow 1 program to use interface1 and force all other programs to use the other?

A little more information needed about your configuration but put the interface you want a single program to on a different subnet from the default interface.

---

### Post by trift on 2011-09-09
My situation has changed since my first post but I think I would still like to know for future reference, here is the outline:

My laptop has two network interfaces, a wired and a wireless. The company I worked for allowed me to connect to their internal network via wireless. This meant I could have programs relating to work connecting via the company network (FTP client, CVS etc) and stuff not relating to work connecting via my home connection on the wired interface (bittorrent, firefox, whatever).

At least that was the theory. The bottom line is that I didn't want personal stuff going through the company network and I didn't want to waste my home bandwidth with company related things. But since I couldn't find a way of doing this I ended up having to either be doing work stuff OR home stuff.

I'm not sure how to go about setting up different subnets, nor whether I can configure programs to run on them. I suppose I was just hoping for a "magic" utility that would do it for me, kinda like proxychains or so, eg:

```
magicprogram firefox eth0
```Might be an example command to run firefox allowing it access only to eth0.

---

### Post by HermanAB on 2011-09-09
Yesh...

You can launch the program with a special group ID and then configure IPTables to filter on the group.

There is an example of such a rule here:
[http://www.aeronetworks.ca/howtos/skype-ssh-tunnel-howto.html](http://www.aeronetworks.ca/howtos/skype-ssh-tunnel-howto.html)

---

