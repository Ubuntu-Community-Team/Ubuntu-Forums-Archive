---
title: "Multi-Questions"
date: 2011-02-05
forum: Networking &amp; Wireless
---

### Post by Xeneth on 2011-02-05
Wasn't sure If I should make a single post or multi-posts for these, and all of them are not 100% Ubuntu, but another Linux based OS interaction.

1: I will eventually have 3 wireless routers in my house with the same SSID just to guarantee wireless signals, and I will be taking advantage of Mac Filtering.  All routers will have dd-wrt on them so all linux based.  was I am looking to do is make a central point in which I can edit the mac table list on my Ubuntu Server.  Having the routers copy that list every few min would be the best so each still has it's own list.  I'm looking for a way to do this.

2: I will have a few computers (Ubuntu and windows), consoles, and other devices on my network, so I want to have access to all logs, even router logs, from a single computer (or all computers have all logs).  My Ubuntu server would be the most obvious centralized point of storage, but I am never on it, so not very useful, and text files don't take enough space to worry about compatibility or disk space.  I figure I can run a bash file on the windows and a script on the linux, but I don't know if there are any permissions issues, or what is the best protocol for this because samba seems to convoluted for simply copying a text file (or whatever format it is).

3:  My internal network is going to be 100% IPv6, to give me practice and make it more secure (since most people do not know the ipv6 ip schema yet), and a Cisco router will be my gateway and doing Nat between IPv6 and IPv4.  What I want to know is there anything I need to do with Ubuntu to prevent errors with no ipv4 address or is it ready to go from install?

Thanks for the help.  Most of this I would learn trial and error but I am at work so cannot do that so I thought I would just ask.  :)

---

### Post by grahammechanical on 2011-02-05
I really do not know what you are talking about except that I have noticed that when I go to Edit Connections in Network Manager there is a tab for IPv6 settings as well as IPv4. I guess that Ubuntu set up for IPv6

Regards.

---

### Post by Xeneth on 2011-02-07
If your want me to clarify any points I will, but the server is CLI only, so there are no tabs or such.  I know it can handle IPv6, but I want IPv6 to be native, and without IPv4 present.

As for the other parts, I'm talking about copying the log files, either through script or maybe having the server coping each then pushing it to all.

---

### Post by pricetech on 2011-02-07
1. depends on your WAPs.  If they can work together you should have no problem.  I'm thinking you'll use one as a master and the other two as repeaters, so they'll all work according to the master WAP'a configuration.

2. Look into setting up a syslog server.

3. IPv6 is supported in Linux natively.

---

