---
title: "iptables basics?"
date: 2012-08-15
forum: Networking &amp; Wireless
---

### Post by essefbx on 2012-08-15
I'm setting up a system on ubuntu-server 12.04 and I want to secure my server. I'm nervous to start melding with iptables because the server I want to secure is an active ftp, samba, and web server.

Also the ftp is interesting as audio files are uploaded regularly from a remote program, and I'm not sure through which port. (I'm guessing because of the authentication that it's 20, 21)

Also the server is under a massive subdomain within my university, so it has dns, dhcp assigned.

I have started with this:
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

I was wondering what kind of options I have to block/monitor ssh? (I work within a large changing group so allowing specific hosts may be too tedious)and there is no external firewall.

So if anyone knows of a good guide or has some tips, I'd be very grateful! 

Thanks.

---

### Post by unevenflow on 2012-08-15
Have a look at these:
[http://serverfault.com/questions/128962/denyhosts-vs-fail2ban-vs-iptables-best-way-to-prevent-brute-force-logons](http://serverfault.com/questions/128962/denyhosts-vs-fail2ban-vs-iptables-best-way-to-prevent-brute-force-logons)

[http://serverfault.com/questions/17870/hundreds-of-failed-ssh-logins/17879#17879](http://serverfault.com/questions/17870/hundreds-of-failed-ssh-logins/17879#17879)

[http://blog.mypapit.net/2011/05/iptables-rule-to-safeguard-ssh-server-from-crackers.html](http://blog.mypapit.net/2011/05/iptables-rule-to-safeguard-ssh-server-from-crackers.html)

---

### Post by essefbx on 2012-08-23
thanks!! These were really helpful!

---

