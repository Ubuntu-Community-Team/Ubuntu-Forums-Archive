---
title: "Videostream for Google Chromecast"
date: 2015-11-03
forum: Multimedia Software
---

### Post by jose85 on 2015-11-03
[FONT=arial]I'm new to Linux and recently ran into Videostream.  I couldn't connect at first because a couple of ports were blocked by my firewall.  So Videostream suggested that I enter the following command to get it to work:

[SIZE=2][COLOR=#000000]sudo /sbin/iptables -A INPUT -p tcp --dport 5556 -j ACCEPT
sudo /sbin/iptables -A INPUT -p tcp --dport 5558 -j ACCEPT

It works now.  But I got to thinking whether this was safe or not.  So I entered the same command afterwards but ended it with DENY instead of ACCEPT. The command went through, but when I tried to use Videostream, it still worked.

I know this is a noob mistake and I shouldn't just be copying commands.  But what did I just do?  Is this safe?  And how do I undo this? 

Tried going to /sbin/iptables but I'm not even sure how to edit that file.[/COLOR][/SIZE][/FONT]

---

### Post by jose85 on 2015-11-10
anyone?

---

### Post by dwbh on 2016-08-08
just replace the A with a D.
you can see the rules before:

sudo iptables -S INPUT 

then remove them like this:

sudo iptables -D INPUT -p tcp -m tcp --dport 5556 -j ACCEPT
sudo iptables -D INPUT -p tcp -m tcp --dport 5558 -j ACCEPT

then verify:

sudo iptables -S INPUT

---

