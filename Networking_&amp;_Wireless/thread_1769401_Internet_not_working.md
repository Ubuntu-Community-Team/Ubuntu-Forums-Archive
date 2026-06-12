---
title: "Internet not working"
date: 2011-05-27
forum: Networking &amp; Wireless
---

### Post by Mewist2 on 2011-05-27
Hi guys, I am new to Linux, so hi :D.
But, I installed it, all went well, but now, I can't access the Internet.
So, I don't know what info you guys need, so just ask.
Also, if it helps, I am using Ethernet (Well, I think it's Ethernet, it is a yellow cable with a rectangle end.
Thanks in advance, Mew.

---

### Post by dineshs on 2011-05-28
Connect your cable , switch on modem/router then go to applications-accessories-terminal and post the result of the following commands.
```
route -n
sudo lshw -C network
ping 4.2.2.1 -c4
```
Do you have a username and password to connect to internet.If yes, did you try
[http://ubuntuforums.org/showpost.php?p=9611335&postcount=9](http://ubuntuforums.org/showpost.php?p=9611335&postcount=9)

---

### Post by Iowan on 2011-05-28
It's the yellow cable - blue ones work better (just kidding...)

From a terminal (Applications>Accessories>Terminal):```
ifconfig -a
```
Does the interface have an IP address?
Can you **ping** the router?

---

### Post by Mewist2 on 2011-05-28
> **Iowan said:**
> It's the yellow cable - blue ones work better (just kidding...)

From a terminal (Applications>Accessories>Terminal):```
ifconfig -a
```
Does the interface have an IP address?
Can you **ping** the router?
No, it doesn't have an IP address, and I don't know how to PING the router, I don't even know what PING means >.<.

Sorry I took so long to reply, thanks for your help.

---

### Post by Mewist2 on 2011-05-28
Anyone have any ideas?

---

### Post by Mewist2 on 2011-05-28
Help please?

---

### Post by Mewist2 on 2011-05-29
Can someone help me please? I really want to get this running soon.

---

### Post by Iowan on 2011-05-29
PATIENCE! Once/day is adequate for bumping.

You can check **man ping** for a (brief) description of the **ping** command or visit Wikipedia for more information, but without an IP address, the machine can't communicate.

It would be helpful if you could post the results of the commands listed in post #2.

---

### Post by Mewist2 on 2011-05-29
Thanks guys, but I have given up, I ran it under windows 2000 and the internet still didn't work, so thanks for trying, bye.
EDIT: but if you guys know what's wrong, tell me and I will try it out.

---

