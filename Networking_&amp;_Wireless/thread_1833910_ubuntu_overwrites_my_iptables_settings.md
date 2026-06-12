---
title: "ubuntu overwrites my iptables settings"
date: 2011-08-26
forum: Networking &amp; Wireless
---

### Post by bobdobbs on 2011-08-26
Hi all.

I have ubuntu 10.04 on my desktop computer.
A while ago I noticed that I couldn't connect to a website I need to use, using a particular port (not port 80). This is really annoying.

I also noticed that I couldn't ssh in to my desktop.

No matter what I did with ufw, the firewall wouldn't permit my use of target ports. iptables just ignores whatever instructions I give to it from ufw. So I removed ufw.

I flushed and then cleared all of my iptables chains and rules. I used an online service to generate an iptables script. My script allows the use of whatever ports I want, includeing ssh.

However, 10 minutes after I run the script that installs my desired iptables rules, the old rules kick back in. They return from the dead and block ssh and whatever else I want to use.


This is really frustrating. I can't work when my operating system abitrarily decides to stop me from connecting to things in the way I want and need.

Why does this happen?
What do I do to get ubuntu to keep the iptables rules I want, and not add any other rules?

---

### Post by NoBugs! on 2011-08-26
Have you tried
```

sudo ufw disable
```

---

