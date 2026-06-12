---
title: "inetd not running"
date: 2009-08-27
forum: Networking &amp; Wireless
---

### Post by dreadnyah on 2009-08-27
I'm running xubuntu 9.04 x64.  Internet seems slow and when I run ping I get 

"rcvbuf is not enough to hold preload"

My inetd.conf file is empty and when I run 

ps -ef

It indicates that inetd is not running.

My questions are:

Should inetd be running?

Why do I get the warning from ping that "rcvbuf is not enough to hold preload"?  How do I fix this?

Please help.

dreadnyah

---

### Post by i.r.id10t on 2009-08-27
The inetd/xinetd programs start services when someone tries to connect to them - ftp, telnet, etc.  Not needed for a desktop machine.

---

### Post by shredder12 on 2009-08-27
Well, I checked for inetd and it is not runnign in my system either and inetd.conf file is empty too..
I don't have a solution to your problem but its probably not an issue related to inetd.

---

### Post by dreadnyah on 2009-08-27
Thanks to you both for your replies.  Yeah, it doesn't seem to be a problem

---

