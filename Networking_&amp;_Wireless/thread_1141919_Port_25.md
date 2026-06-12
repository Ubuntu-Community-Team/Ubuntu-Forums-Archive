---
title: "Port 25"
date: 2009-04-28
forum: Networking &amp; Wireless
---

### Post by drhiii on 2009-04-28
Here's a new one...

Am trying to get Postfix/Dovecot/TLS working.  I am able to telnet to port 25 from localhost.  But I am not able to telnet to it from the outside.

NMAP returns the following:

PORT     STATE    SERVICE
25/tcp   filtered smtp
53/tcp   open     domain
80/tcp   open     http
110/tcp  open     pop3


Filtered???  I have turned off all firewalling, no IP tables.  Nuttin.  Where in the world is this getting, filtered?  I can connect to the POP on 110.  But cannot to SMTP on 25.  Have never had this before.  

Help anyone?

---

### Post by drhiii on 2009-04-28
Or... why can I telnet to    telnet localhost 25

but I can't telnet to        telnet abcxyz.com 25

assuming abcxyz is the localhost machine?

---

### Post by drhiii on 2009-04-28
Now it gets very odd...

I am on machine A.  The server is on machine B.  I have other servers, C, D and E, available tome.

I can telnet to port 110 from Machine A to Machine B.

I cannot telnet to port 25 from Machine A to Machine B.

However, I can ssh into machines C, D and E, and telnet to port 25 on Machine B.  

Finally, I can telnet to port 25 on other machines from Machine A.  Just not B.  

This is really perplexing.

---

### Post by drhiii on 2009-04-28
Seriously, I cannot telnet to port 25 or hit an smtp port, anywhere.  This on a 9.04 box.  

WHat am I missing?  I have never seen this before??

---

### Post by Dy1anW on 2009-04-29
I've been trying to do the same thing as you (Postfix/Dovecot) and haven't been able to send/receive anything.  Nmap shows port 25 is open (as are ports 80 and 21), yet the only protocol that doesn't have any problems is ftp.  So no one can send me mail, no one can view my site (not that there's anything there) but people can upload files.

How does that work?!  I'm wondering if it's actually down to my ISP blocking ports 25 and 80.  Oh, I can't send mail either, keep getting connection timeouts (but I can ping destination mail servers just fine...).

---

### Post by drhiii on 2009-04-29
> **Dy1anW said:**
> I've been trying to do the same thing as you (Postfix/Dovecot) and haven't been able to send/receive anything.  Nmap shows port 25 is open (as are ports 80 and 21), yet the only protocol that doesn't have any problems is ftp.  So no one can send me mail, no one can view my site (not that there's anything there) but people can upload files.

How does that work?!  I'm wondering if it's actually down to my ISP blocking ports 25 and 80.  Oh, I can't send mail either, keep getting connection timeouts (but I can ping destination mail servers just fine...).


I took a laptop and went to an open wireless circuit, and was able to connect to port 25 straight away.  It appears the problem is not necessarily my ISP, but my router.  I am able to telnet to every port EXCEPT 25.  110 goes straight in. I am NATTed so wonder if this is where the problem resides.  You may want to try this as well.  Connecting to your server from another location.

---

### Post by Dy1anW on 2009-04-29
> **drhiii said:**
> I took a laptop and went to an open wireless circuit, and was able to connect to port 25 straight away.  It appears the problem is not necessarily my ISP, but my router.  I am able to telnet to every port EXCEPT 25.  110 goes straight in. I am NATTed so wonder if this is where the problem resides.  You may want to try this as well.  Connecting to your server from another location.

Aye, I read in a distant forum somewhere that it's most likely due to a NAT problem.  I went to the extreme and replaced my router (needed a change anyway, had no end of problems with Linksys), and was then able to connect to port 25.  I can now receive incoming mails (as far as I can tell from logs), but can't store them yet (that's a whole other issue).  Still can't send emails to any server other than my ISP, but as I've read [here](http://aplawrence.com/Blog/B961.html) it's most likely down to a mismatch of PTR records; as the reverse lookup doesn't match the domain name of the sent email, the recipient server refuses the connection, thinking it's spam.

---

### Post by drhiii on 2009-04-29
> **Dy1anW said:**
> Aye, I read in a distant forum somewhere that it's most likely due to a NAT problem.  I went to the extreme and replaced my router (needed a change anyway, had no end of problems with Linksys), and was then able to connect to port 25.  I can now receive incoming mails (as far as I can tell from logs), but can't store them yet (that's a whole other issue).  Still can't send emails to any server other than my ISP, but as I've read [here](http://aplawrence.com/Blog/B961.html) it's most likely down to a mismatch of PTR records; as the reverse lookup doesn't match the domain name of the sent email, the recipient server refuses the connection, thinking it's spam.


Ya, NAT issue.  Odd that it would work for every port I tried except 25.  Sigh.  I have a work around tho.  

My issue now is to correct my DNS.  I don't have that knowledge, yet, so will have to go looking about for how to correct my DNS.  Might you have a place to find a Tutorial on this?

tx

---

### Post by Dy1anW on 2009-04-29
> **drhiii said:**
> Ya, NAT issue.  Odd that it would work for every port I tried except 25.  Sigh.  I have a work around tho.  

My issue now is to correct my DNS.  I don't have that knowledge, yet, so will have to go looking about for how to correct my DNS.  Might you have a place to find a Tutorial on this?

tx

If you're referring to MX records so you can send emails without them being rejected, then no, I've got nothing...  Another method would be to edit /etc/postfix/main.cf and set relayhost = your.isp.com but bear in mind that most ISPs (including mine) won't accept emails from non-provider domain names.

Which DNS provider are you using?  I heard easydns.com is supposed to be hassle free, and thus quite popular.  I'm using dyndns.org, but apparently it won't allow me to direct MX records at my free domain name.

---

### Post by drhiii on 2009-04-29
> **Dy1anW said:**
> If you're referring to MX records so you can send emails without them being rejected, then no, I've got nothing...  Another method would be to edit /etc/postfix/main.cf and set relayhost = your.isp.com but bear in mind that most ISPs (including mine) won't accept emails from non-provider domain names.

Which DNS provider are you using?  I heard easydns.com is supposed to be hassle free, and thus quite popular.  I'm using dyndns.org, but apparently it won't allow me to direct MX records at my free domain name.


I am running my own primary and secondary servers.  DNS was not something I became proficient in.  I just used Webmin to set up the records, but apparently they are incorrect.  I will look into easydns yes.  But not before I see if I can correct the problem with these records on my machines.  Sigh...

---

### Post by Dy1anW on 2009-04-29
> **drhiii said:**
> I am running my own primary and secondary servers.  DNS was not something I became proficient in.  I just used Webmin to set up the records, but apparently they are incorrect.  I will look into easydns yes.  But not before I see if I can correct the problem with these records on my machines.  Sigh...

Ahh, I tried that once before, found it to be more hassle than it's worth :P  If you're hosting your own DNS for speed, you may want to consider [OpenDNS](http://www.opendns.com).

Going back to the MX/PTR issue, DynDns provides a [mailhop](https://www.dyndns.com/services/mailhop/outbound.html) service (where you can relay via SMTP), but they charge $15p.a. for blocks of 150 relays per day.  Unfortunately there are no free mailhop services anywhere, as all evil spammers on the planet would just abuse the system.

---

### Post by [pl]ice on 2009-05-08
guys, i got the same problem, I set up the postfix, but can't connect from internet, only the localnet will do.
Scanning with nmap shows that the port is blocked, yet, i haven't blocked it; got full VPS server, so they won't be blocking it.
Funny enough i get the port 80 through Nmap as blocked, yet my browser works nicely when i connect to it. Don't get it :/

---

