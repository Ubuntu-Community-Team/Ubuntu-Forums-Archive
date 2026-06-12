---
title: "ftp via Kerberos access Webserver via Dyndns to QNAP"
date: 2011-12-08
forum: Networking &amp; Wireless
---

### Post by AfrikaDietmar on 2011-12-08
Hi Ubuntu!

i have setup a webserver on a QNAP machine accessible through a sub domain from dyndns. I can access the webserver via FTP and was wondering and trying to comphrehend how to possible connect more securely via Kerberos. SFTP and https are things that will not work on a subdomain of dyndns. I understood that Kerberos can make a secure connection, i have installed it from the software centre and thought it will be like an ftp program :confused: Looking at the threads it looks more its a program to create and ftp server ?

Your input is welcome.

Bye bye,
Dietmar

---

### Post by Lars Noodén on 2011-12-08
Both SFTP and HTTPS will work.  Give them a try, you'll find that they work just fine.

DynDNS only has to do with the name that the machine is contacted with.

---

### Post by AfrikaDietmar on 2011-12-08
Hi Lars!

your short answer made me ponder and indeed it works after portforwarding in my router the required SSH and SFTP ports an SFTP connection worked! And i have trying to do this since ages! After contacting DynDns i was told > No, there is no way of using an official SSL certificate with the Dynamic DNS services. For that you'd need Standard DNS and your own domain, or to create a self-signed certificate. which made me believe that no SFTP is possible.

Now, when i connected via FileZilla i got the following response when using SFTP:

> ACHIEVED FIRST SFTP connection! Got this message in FileZilla
Uknown host key
The server's host key is unknown. You have no guarantee that the server is the computer you think it is.
Deatails:
Host: subdomain url
Fingerprint: ssh-rsa 2048 ...and numbers with digits: 85:bb:etc.

Trust this host and carry on connecting?
tick box Always trust this host, add this key to the cacheAnd i got connected, does it mean its working correctly and my connection is safe and encrypted ? I land directly into root on the server.

How do you get https to work ? in using a proxy like [http://kproxy.com/](http://kproxy.com/) ?

---

### Post by Lars Noodén on 2011-12-08
Yes, SFTP is safe and encrypted.  Remember [SFTP is not the same as FTPS](http://en.wikibooks.org/wiki/OpenSSH/SSH_Protocols#SFTP_is_not_FTPS).  Maybe that's where the confusion is from.  

With HTTPS, you should still be able to make self-signed certificates.

---

### Post by AfrikaDietmar on 2011-12-08
> With HTTPS, you should still be able to make self-signed certificates. 

Would be interesting how to get the https working on the subdomain of dyndns. Like using an OPEN SSL certificate - but how to do that ? Usually if add and s after http, i.e.:
[https://subdomain.dynddns.org](https://subdomain.dynddns.org) doesn't work, my browser says "Unable to connect".

---

