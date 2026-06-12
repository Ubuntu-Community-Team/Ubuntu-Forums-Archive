---
title: "DNS Lookup order"
date: 2009-05-08
forum: Networking &amp; Wireless
---

### Post by fa2k on 2009-05-08
Hi! After I upgraded to 9.04, DNS lookups have been horribly slow. I suppose this is only a problem when IPv6 is enabled. I believe that this can be fixed without disabling IPv6, because Windows does it much better, both on Firefox and Internet Explorer. Let's say I am trying to go to <domain> with a web browser.

**Firefox and IE on Windows Vista and 7:**
```
1.  Send A (v4) query for <domain> and wait for reply.
2.  If it got some reply, send AAAA query for <domain>.
3.  Choose whether to use IPv6 or IPv4 domain according to some algorithm.
```
*(if <domain> does not contain a dot, it searches the "local" search domain, <domain>.getinternet.no in my case)*

**Firefox on Ubuntu**
```
1.  Send AAAA (v6) query for <domain> and wait for reply
2. If it is not found, send AAAA (v6) for <domain>.getinternet.no (*)
3. If it is not found, send A query for <domain> (which usually works)

(*) getinternet.no is what appears in the search line in my 
/etc/resolv.conf, this will depend on your ISP.
```
If an AAAA record is found, then an A request is sent, but the AAAA is generally chosen.


The problem is that the AAAA request seems to upset my router (a D-Link) at some times, so the lookups takes a very long time. The search for the subdomain of getinternet.no is never in the cache, so it needs to do an extra , unncessary lookup.

Is there any way to suppress the subdomain lookup, and possibly also make Firefox send an A lookup first? The ideal way would be to send the A and the AAAA query in parallel, but I suppose that would require a major rewrite.

---

### Post by lpd on 2009-05-08
If I set my hostname to a FQDN (ubuntu.mydomain.org) and try to surf to banana.ubuntu.com I get a message from my domain registrar saying that banana.ubuntu.com is registred with them. Not likely and not true. I get the same message if Firefox/Konqueror/Opera reaches a timeout even for a visit to [www.ubuntu.com]("http://www.ubuntu.com").

If I set my hostname to "ubuntu" and try to reach banana.ubuntu.com I get the standard error message from Firefox/Konqueror/Opera. 

I think this must have something to do with subdomain lookups.


[https://bugs.launchpad.net/bugs/373909](https://bugs.launchpad.net/bugs/373909)

---

### Post by fa2k on 2009-05-09
> **lpd said:**
> If I set my hostname to a FQDN (ubuntu.mydomain.org) and try to surf to banana.ubuntu.com I get a message from my domain registrar saying that banana.ubuntu.com is registred with them. Not likely and not true. I get the same message if Firefox/Konqueror/Opera reaches a timeout even for a visit to [www.ubuntu.com]("http://www.ubuntu.com").

If I set my hostname to "ubuntu" and try to reach banana.ubuntu.com I get the standard error message from Firefox/Konqueror/Opera. 

I think this must have something to do with subdomain lookups.


[https://bugs.launchpad.net/bugs/373909](https://bugs.launchpad.net/bugs/373909)

I think this is related, but not exactly the same. Also, as you may already realise, the solution would be the same; to stop subdomain lookups (I don't know if that is the correct term). Your browser tries to go to banana.ubuntu.com.mydomain.com before giving up. This is actually standard practice for DNS resolvers, but it is counterproductive for web browsing (as I argued above), especially when the mydomain.com DNS servers are not local to you.

Your DNS registrar should return proper NXDomain (Domain not found) messages for subdomains of mydomain.com that do not exist, rather than resolving them to a web server with a page that says the domain is registered with them. This can possibly be set in the control panel of the DNS registrar. 

Depending on your preference, any one of the above solutions will be right. I think there should be an option to suppress the **search** line in **/etc/resolv.conf**. Normally, one would edit this file directly, but now Ubuntu replaces the file on each reboot. There may be a setting for the resolvconf program that I am not aware of.

---

### Post by lpd on 2009-05-14
OK, thanks, changed my DNS settings, removed *.mydomain.org from the DNS... Silly of me, should've thought of that earlier. Thanks.
-----
I too am experiencing sometimes slow DNS lookups after the upgrade to Ubuntu 9.04. And most definitely my recently fixed problem is a symptom.

There two directives called 'search' and 'domain' in /etc/resolv.conf. I have been toying with them but as far as I can see, adding a 'domain' directive before the nameservers in /etc/resolv.conf only builds up more dns lookups than before.

I found that these two sites had some information on how to configure the /etc/resolv.conf file: [http://www.cyberciti.biz/tips/linux-how-to-setup-as-dns-client.html](http://www.cyberciti.biz/tips/linux-how-to-setup-as-dns-client.html) and [http://tldp.org/LDP/nag/node84.html](http://tldp.org/LDP/nag/node84.html) .

Maybe you should try to comment out the 'search' directive in your /etc/resolv.conf file??? Only leaving the nameservers.

---

