---
title: "iptables-webmin and string module."
date: 2013-04-07
forum: Networking &amp; Wireless
---

### Post by Samuel86 on 2013-04-07
So before I start apologies for being new to Ubuntu and Linux as a whole, I've been working out bits most of the day but have hit a snag.

The issue is in syntax really, I cannot find any documentation that I can understand on how to use a certain part of iptables, I've installed the webmin interface for ease of use and this has made life extremely simple in that regard.
I need to use the string module for a specific reason but cannot figure out how this part of webmin works and was hoping someone could explain.

This is the rule creation screen on webmin:
[IMG][http://i.imgur.com/oyUitRv.png](http://i.imgur.com/oyUitRv.png)[/IMG]

It's all fairly self explained and within seconds I can create the rules I required. My issues is needing to have webmin create string matching rules. However the last 2 entry boxes might be the answer, they appear to be for iptables modules such as the one I'm trying to use 'string', but I've no idea how they work.

So if anyone could help then it would be great. For example how would I create a rule to match against packets with the string 'w00t.block.me.i.be.a.flood' inside them.

---

### Post by Doug S on 2013-04-07
Hi, and welcome to Ubuntu forums.

First, please be aware that use that use of the iptables string module can be somewhat CPU intensive. There was a time, years ago, where one had to compile the kernel to be able use the iptables string function, as the default didn't have it.

There might be other, less CPU intensive, ways, such as connection rate limiting, to do what you want. Maybe we can help with some ideas if you give more information or examples.

Anyway, for your actual question, I do not use webmin, but here is an example of an iptables string rule that I made and tested for [another forums thread]("http://ubuntuforums.org/showthread.php?t=2106879&highlight=iptables+string").
```
sudo iptables -A INPUT -m string --algo bm --string "HzDxFvGb" -j DROP
```Maybe you can convert that to whatever webmin needs, or just enter something similar in a terminal command line.

---

