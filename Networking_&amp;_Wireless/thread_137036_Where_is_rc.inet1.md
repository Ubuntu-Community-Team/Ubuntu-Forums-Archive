---
title: "Where is rc.inet1??"
date: 2006-02-27
forum: Networking &amp; Wireless
---

### Post by linuxden on 2006-02-27
Hi all,

Am trying to find my network configuration file... I would like to be able to manually configure my TCP/IP interfaces, using ifconfig and also have a look at it...

what is it called in Ubuntu?? And where can i find it?

Also where could i find my route table?

thank you for you help guys N gals...

---

### Post by claes on 2006-02-27
Network configuration file:
/etc/network/interfaces

Routing table:
route -n

Claes

---

### Post by linuxden on 2006-02-27
Hey Claes,

I realise that route -n gives me my routing table...
My question was is there a file that once i have used route and ifconfig commands i get and i can see the table in a text file...Ie is there an output file for both those commands??

I  have read a bit about rc.inet1 and that seems to be a script where i can input with a text editor and thatr will update my routing table...

Will look more into it...

---

### Post by claes on 2006-02-27
rc.inet1 is for bsd unix. Slackware used that file earlier (or perhaps even now, long time since I used slackware) but sysv init that ubuntu uses don't have that file. It uses /etc/network/interfaces.

In this thread you can read more about static routes:
[http://www.ubuntuforums.org/showthread.php?t=113474](http://www.ubuntuforums.org/showthread.php?t=113474)

Claes

---

### Post by linuxden on 2006-02-27
[http://www.slackbook.org/html/network-configuration-tcpip.html](http://www.slackbook.org/html/network-configuration-tcpip.html)

I just assumed that it would be a similar way... Will look more into sysv tomorrow...

Thanks for your responce

---

