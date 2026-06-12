---
title: "How to bypass blocked port 22"
date: 2009-12-30
forum: Networking &amp; Wireless
---

### Post by zereshk on 2009-12-30
Hi guys, I have a grave problem. My conservative uni firewall has blocked many ports including port 22 so I neither can ssh to my ubuntu unmanaged vps nor user other GUI admin tools. I am really really frustrated. Now I have no access to myvps, but it still listens to port 22.

Help me get out of the cage. :confused:  (don't preach me plz, be sure I do very decent deeds)

---

### Post by zereshk on 2009-12-31
Ok, happily I found the answer, and wanna share it:

First off,  from behind the Internet desert,  you need to ssh to your box using a web-based ssh client, like [serfish]("http://www.serfish.com/root/") (it is free, just buggs you each minute to fill a capatcha or pay, if you reach to the first minute!)

After login your box, you need to modify your ssh config file so that it also listens to port 443:

```
nano /etc/ssh/sshd_config 
```and just add

```
Port 443
```Voilà,

finally restart ssh server:

> /etc/init.d/ssh restart

 now you can ssh to the box from behind your bloody firewall:

```
ssh -p 443 YourIPorHostname
```More info about tunneling @ [verot.net]("http://www.verot.net/socks.htm")

Quite handy, but wheather or not this solution may pose a security issue I donno.

---

### Post by cariboo on 2009-12-31
The forums don't condone this type of activity. The restrictions are set in place for a reason. If you have problems withthem, take them up with the IT department.

---

