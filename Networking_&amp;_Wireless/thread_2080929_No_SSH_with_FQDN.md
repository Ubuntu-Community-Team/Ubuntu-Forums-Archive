---
title: "No SSH with FQDN"
date: 2012-11-05
forum: Networking &amp; Wireless
---

### Post by deljones on 2012-11-05
Hi all..

Suddenly my ssh access does not work using my FQDN...

I know that the first thing is port forwarding but port 22 is forwarded. (see jpeg) The other services are fine.

If i use the local ip its ok but with the FQDN...? nothing.

It has suddenly happened.... 

Anyone any ideas?

Del

---

### Post by elliotbeken on 2012-11-05
Have you tried using the external IP address ?

Do this ever work?

---

### Post by Lars Noodén on 2012-11-05
Just to check, your internal address is the same one that is the target of the forward you show in the attachment, right?

How are you getting the FQDN for your site?  Use [dig](http://manpages.ubuntu.com/manpages/precise/en/man1/dig.1.html) or [host](http://manpages.ubuntu.com/manpages/precise/en/man1/host.1.html) to check that the ip address being returned for your FQDN is actually the one that your router is using just right now.  It's possible that they are out of sync.

---

### Post by deljones on 2012-11-06
Hi Lars...

After an update anything with my FQDN is no longer working. 

Using the FQDN I get :
getfile: Cannot open URL(/etc_ro/web/zenphoto,No such file or directory) as an example.


If I use the server ip number internally 192.168.0.20/zenphoto it is all good.
If I uses the external ip address I get the same result as the FQDN. Errors...



This happens on all of my server apps using port 80 it would seem. 

FTP is fine, FTP over SSH is fine,  port forwarding on my router is ok. A port checker tells me they are all open



The strange thing is is that when I put in my front page from my webserver I get the username/password box for one of my ip cameras...! which is very odd.


My FQDN is through dyndns.org which must be ok as ftp works. It would appear to be a webserver routing issue or something I dont know but its very frustrating...


Any help you can give would be great...


Del

---

### Post by Lars Noodén on 2012-11-06
Can you get the external ip address directly from you router and compare it to what DynDNS is providing?

---

### Post by deljones on 2012-11-06
Hi Lars...

Sorry Im to sure what you mean...

If I try my external ip address I get nothing.

So: as an example 219.111.222.333/piwigo I get the same as if I put my FQDN in but only for web stuff. Everything else is ok. Im thinking apache?

Del

---

### Post by Lars Noodén on 2012-11-06
Ok.  It sounds like either you're getting the wrong external IP for some reason or you router is not forwarding the ports correctly.  How long has this been going on?  You should be able to check your router/modem and see what your current external address is.  Then if forwarding is set up correctly, you should be able to connect directly to that address.  If DynDNS is out of sync it will return an ip address that does not match the one currently in use by your router.

---

### Post by deljones on 2012-11-06
Ok Lars Im going to check the router out but it doesnt explain why FTP using the FQDN is working but let me see whats going on.

I use Webmin. It told me that 17 updates where available for my system so stupidly I agreed and now I have this problem :(

Del

---

