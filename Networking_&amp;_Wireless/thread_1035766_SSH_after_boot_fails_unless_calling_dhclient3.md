---
title: "SSH after boot fails unless calling dhclient3"
date: 2009-01-10
forum: Networking &amp; Wireless
---

### Post by mquintos on 2009-01-10
I'm having problems with OpenSSH and wifi at boot.  I hope someone can help.

Problem:
After system loads, I cannot login to SSH until I do a 
'sudo dhclient3 ath0'.  
However, while at the box, the internet is available (I can ping www.google.com and wget pages)

System:
ubuntu 8.10 server-i386 (new install)

How to Repeat:
1 ) Restart Server (linux box having problems)
2 ) Wait for Server to finish loading
3 ) SSH to Server (macbook ssh to Server)
4 ) Observe SSH fails (times out)
5 ) Run on Server 'wget www.google.com'
6 ) Observe index.html downloaded to local directory
7 ) Reattempt SSH to Server.  
8 ) Observe timeout failure.
9 ) Run on Server 'sudo dhclient3 ath0'
10) Reattempt SSH to Server
11) Success.  (But don't understand why)

Any ideas?

---

### Post by mquintos on 2009-01-11
For future reference, I temporarily solved the problem by editing my /etc/init.d/rc.local file and adding the 'dhclient3 ath0' command at startup.

Although, I'd still like to know why this is needed.

---

### Post by lswb on 2009-01-11
Is this server using a different interface to connect to the internet or does it use ath0 for everything?

---

### Post by kevmitch on 2009-01-11
Does restarting the ssh service help?

/etc/init.d/ssh restart

You might want to see how soon ssh is starting on boot. It might get started before the interface is up. I don't think this SHOULD cause a problem, but I would believe if someone told me it did. Try making ssh start later using something like BUM.

---

