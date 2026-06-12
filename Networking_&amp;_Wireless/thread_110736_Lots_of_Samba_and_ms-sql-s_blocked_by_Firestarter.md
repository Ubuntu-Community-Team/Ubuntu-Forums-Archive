---
title: "Lots of Samba and ms-sql-s blocked by Firestarter"
date: 2005-12-31
forum: Networking &amp; Wireless
---

### Post by Luke771 on 2005-12-31
Hi everybody,
On my Firestarter Events tab, I get a lot of red lines showing blocked Samba  connection attempts on port 139 and some less, but still many,  black lines showing blockad connection attempts from ms-sql-s.
Both (samba and sql)  source IPs begin with the same 2-digit number shown in the Home Tab as Source of my outbound connections- the digits before the first dot are the same, the rest is different. 
I' sorry I'm not a networking expert, I can only report what I see.
I connect to the Internet by fiber, ethernet and router, 10Meg nominal (more or less two real), I have a single PC, no home network, I don't even know what SMB and SQL do, let alone using them, all I want to know is why I get all those red Samba (and black ms-sql-s) lines in my Firestarter, what does that mean and how I am supposed to react. (Maybe some extra word about Samba and sql?)
The Firestarter manual says something like "you should react" to red lines blahblahblah, but it does not really tell what to do, or maybe i'm too muck of a  rookie to understand that, maybe someone here can put it in more simple words
Thanks and happy New Year

---

### Post by cwaldbieser on 2005-12-31
[QUOTE=Luke771]Hi everybody,
On my Firestarter Events tab, I get a lot of red lines showing blocked Samba  connection attempts on port 139 and some less, but still many,  black lines showing blockad connection attempts from ms-sql-s.
Both (samba and sql)  source IPs begin with the same 2-digit number shown in the Home Tab as Source of my outbound connections- the digits before the first dot are the same, the rest is different. 
I' sorry I'm not a networking expert, I can only report what I see.
I connect to the Internet by fiber, ethernet and router, 10Meg nominal (more or less two real), I have a single PC, no home network, I don't even know what SMB and SQL do, let alone using them, all I want to know is why I get all those red Samba (and black ms-sql-s) lines in my Firestarter, what does that mean and how I am supposed to react. (Maybe some extra word about Samba and sql?)
The Firestarter manual says something like "you should react" to red lines blahblahblah, but it does not really tell what to do, or maybe i'm too muck of a  rookie to understand that, maybe someone here can put it in more simple words
Thanks and happy New Year[/QUOTE]

Well, if you have a single PC, I am guessing you don't have a samba sever running, so you probably don't need to worry about SMB or SQL attacks affecting your PC.

Basically, Firestarter is alerting you to the fact that some entity is probing your network for open ports, and it is searching 2 very commonly used ports in the Windows world.

You may want to send an email to your ISP, alerting them to the fact that you are receiving a lot of inbound traffic that you don't think should be reaching you.

When Firestarter intercepts those requests, it drops them, so the attacker does not receive a reply.

---

### Post by Luke771 on 2005-12-31
SO it *is* basically what it looks like; hacker attacks. You got any idea about how to hit them back?
I run tor  and privoxy, so they should see a fake IP address when I try something, I was thinking about setting up some kind of honeypot but I gave up after the first two pages of documantation on La Brea and another program (dont remember the name), they would do really cool things but I am not enough a geek enough to get that right, well, at least not yet.
Is there something out there that is newbie friendly and still can give those attackers something to worry about?
(hmmm...maybe I should post this topic as a new thread)

---

