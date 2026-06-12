---
title: "Can't load particular website"
date: 2009-11-18
forum: Networking &amp; Wireless
---

### Post by Starcraftmazter on 2009-11-18
Ever since I installed 9.10, I cannot load the following website:
[https://www.funfile.org/](https://www.funfile.org/)

Now here are several details of the problem:
 - The website times out
 - Tried this in firefox and opera
 - Tried on my laptop (which uses the same router/connection), laptop runs 9.10 as well, same problem
 - I installed 9.10 freshly on both my comps (no upgrade)
 - The website worked fine on 9.04
** - The website also _currently_ works fine on windows**
 - I can ping the IP address associated with the website successfully
 - Accessing the website by it's IP (which should be possible) results in the same timeout problem
 - Accessing the website by it's IP however, prompts me to accept it's certificate
 - I can log into the website's IRC, which is ran on the same server
 - I haven't changed any networking settings (that I know of).
 - Other sites seem to work fine.
 - And yes, I've confirmed with several other people on 9.10 that they do not have this problem.
 - I'm totally out of ideas

Please help?

---

### Post by crucialhoax on 2009-11-18
You can try disabling IPv6 in firefox. If the site is ping-able but it can't be browsed but you can browse to other sites. Doesn't make perfect sense.

In the address bar type about:config 
In the filter bar type network.dns.disableIPv6
make that setting "true"

Hope this helps.

---

### Post by realzippy on 2009-11-18
When I try this site on 9.10 firefox 3.5 it loads.

---

### Post by Starcraftmazter on 2009-11-18
> **crucialhoax said:**
> You can try disabling IPv6 in firefox. If the site is ping-able but it can't be browsed but you can browse to other sites. Doesn't make perfect sense.

In the address bar type about:config 
In the filter bar type network.dns.disableIPv6
make that setting "true"

Hope this helps.

Unfortunately that seems to make no difference :(

---

### Post by crucialhoax on 2009-11-18
I have a far fetched idea. I clicked on the link and got the following message.

**Note**: You need cookies enabled to log in. **6** failed logins in a row will result in banning your ip

I wonder...

---

### Post by Starcraftmazter on 2009-11-18
> **crucialhoax said:**
> I have a far fetched idea. I clicked on the link and got the following message.

**Note**: You need cookies enabled to log in. **6** failed logins in a row will result in banning your ip

I wonder...

I'm not banned from the site, I've confirmed this on IRC and I can also log in from windows fine. Also, banned users see a banned message - not timeouts.

Cookies are enabled for me of course, but irrelevant because the site times out before I get a chance to log in obviously.

Also this reminds me, I can access the server's IRC fine.

---

### Post by crucialhoax on 2009-11-18
Hmm... I'm lost. I'm using 9.10 right now and it worked.

---

### Post by lvlint67 on 2009-11-18
> **Starcraftmazter said:**
> I'm not banned from the site, I've confirmed this on IRC and I can also log in from windows fine. Also, banned users see a banned message - not timeouts.

Cookies are enabled for me of course, but irrelevant because the site times out before I get a chance to log in obviously.

Also this reminds me, I can access the server's IRC fine.


$>telnet [www.funfile.org]("http://www.funfile.org") 80
 >GET / HTTP/1.0


That returns a redirect to: https://
and shows the 'click here in case your browser is dumb link' to %a
--------------
Personally I am unimpressed with that litespeed server already but..... it leads me to think that there is a problem with ssl on your end. don't know where to look for the solution though. :(

-=-=-=-=-
This could Possibly be a misconfigured ssl proxy:
firefox>edit>preferences>advanced>network>settings :: If the 'MANUAL etc.' option is selected make sure the ssl entry is correct.

---

### Post by Starcraftmazter on 2009-11-18
> **lvlint67 said:**
> $>telnet [www.funfile.org]("http://www.funfile.org") 80
 >GET / HTTP/1.0


That returns a redirect to: https://
and shows the 'click here in case your browser is dumb link' to %a
--------------
Personally I am unimpressed with that litespeed server already but..... it leads me to think that there is a problem with ssl on your end. don't know where to look for the solution though. :(

-=-=-=-=-
This could Possibly be a misconfigured ssl proxy:
firefox>edit>preferences>advanced>network>settings :: If the 'MANUAL etc.' option is selected make sure the ssl entry is correct.

No proxies, using a direct connection to the internet.

One thing though, I can't seem to telnet into funfile.org or [www.funfile.org](www.funfile.org) on either port 80 or 443. No errors, just never connects - "telnet: Unable to connect to remote host: Network is unreachable".

---

### Post by matt5ash on 2009-11-18
I've noticed a similar problem … some web sites (e.g. google or yahoo) won't connect using firefox or epiphany.  Many times, after a reboot (log out / log on doesn't seem to help) the web sites come up fine.  I've checked using 9.04 to be sure that the trouble is the 9.10 computer and not the Internet connection.  The problem nearly always shows up after a download (e.g. Picasa3, virtualbox, etc).  Sometimes changing to another browser fixes the problem.  The problem remains when using a wired connection, a wireless connection or a broadband connection.

Any ideas would be great !!

---

### Post by lvlint67 on 2009-11-19
> **Starcraftmazter said:**
> No proxies, using a direct connection to the internet.

One thing though, I can't seem to telnet into funfile.org or [www.funfile.org]("http://www.funfile.org") on either port 80 or 443. No errors, just never connects - "telnet: Unable to connect to remote host: Network is unreachable".

ugh sounds like one of those complex network problems... :(
you behind a router? I want to call it a routing problem but I am largely unsure.

---

### Post by Starcraftmazter on 2009-11-24
> **lvlint67 said:**
> ugh sounds like one of those complex network problems... :(
you behind a router? I want to call it a routing problem but I am largely unsure.

Yep - I am behind a router, but it's a simple Ethernet connection, and the site works from windows from the same computer.

---

### Post by Starcraftmazter on 2009-11-24
Fixed the problem with a router reset and firmware upgrade.

---

