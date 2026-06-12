---
title: "Configure IPTables to allow Outlook and other programs access internet"
date: 2011-03-22
forum: Networking &amp; Wireless
---

### Post by shahbg on 2011-03-22
Hi All,

After nearly 3 years and over 150 installations with Ubuntu (possibly a small number), I am still unable to configure something as simple as letting Outlook and any such software access internet.

Several posts referring to NAT and port mapping and like lay scattered all over the internet for doing it but no precise step-by-step guide to follow.

Over the years, since it is evident from the volume of the posts, can someone at Ubuntu think upon a wizard which will let  people like me configure IPTABLES in the simplest way? If it does exist, can someone please lead me to it?

I did refer the thread at : [http://ubuntuforums.org/showthread.php?t=1482115&highlight=proxy+outlook](http://ubuntuforums.org/showthread.php?t=1482115&highlight=proxy+outlook)

but to no avail.

My requirement is simple:

I've setup a ubuntu 10.10 which is running fine as a proxy with squid installed.

What I need is that users should also be able to use other programs which require access to specific ports like outlook, skype, etc...

The ubuntu 10.10 has the following ips:
eth0 - 192.168.1.5 (internal -  broadband)
eth1 - 192.168.0.100 (external - lan)

All users in (lan) are able to surf the internet but are not able to use outlook to send/receive mail.

I've experimented with numerous configurations - flushed - rewritten - flushed IPTABLES several times.

Someone please help me with a step-by-step guide in setting up the required configuration?

Thank you.

---

