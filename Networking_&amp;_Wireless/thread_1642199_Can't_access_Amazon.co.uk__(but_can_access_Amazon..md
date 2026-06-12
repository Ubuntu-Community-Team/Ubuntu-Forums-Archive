---
title: "Can't access Amazon.co.uk  (but can access Amazon.com?)"
date: 2010-12-10
forum: Networking &amp; Wireless
---

### Post by Canuknucklehead on 2010-12-10
G'day,

I'm having strange Internet problems (Firefox 3.6.13 / Ubuntu 10.04) that have left me completely stumped.

For example, I can no longer view amazon.co.uk.  But I can still view amazon.com.

When I attempt to load amazon.co.uk , Firefox will time out with a "Problem loading page" error.

This also happens on other sites such as gsmarena.com and jamesallenonf1.com.  If I access these sites through a proxy such as hidemyass.com, I can view them.

I also can no longer view hotmail.com.  However, no error occurs, simply a blank page.  Yet most other websites, such as ubuntuforums.org, work fine.

If I do an nslookup on those sites I receive the DNS information.

After a fruitless night searching the web, the only useful suggestion I could find was to disable IPv6.  I did, and no change.

Curiously, I've noticed on the sites that I cannot load my firewall is blocking incoming connections from those sites.

[FONT=Verdana]For example, with amazon.co.uk my firewall is blocking the following requests from Amazon:
[/FONT][FONT=Verdana]> Inbound connection attempts
> Port 39201, 178.236.6.39, Protocol TCP, Service Unknown
> Port 58172, 178.236.4.29, Protocol TCP, Service Unknown
> Port 58195, 178.236.4.29, Protocol TCP, Service Unknown
> Port 46133, 178.236.4.29, Protocol TCP, Service Unknown

My firewall is configured to run in 'stealth' mode, that is to drop rejected packets silently and to enable ICMP filtering.  However, temporarily changing these had no effect.

Any suggestions you might have would be appreciated!  Thanks a million!
[/FONT]

---

### Post by sandra mclean on 2010-12-29
hello,
glad to see i'm not the only one!!
i've got probs accessing amazon.co.uk too, but i can get amazon.com no prob,
but i'm also tring to download docs from a dcsf website and that keeps timing out too
so please let me know if you find a solution, i'd be grateful to
see if it works for me too ):P

---

### Post by howefield on 2010-12-29
> **sandra mclean said:**
> but i'm also tring to download docs from a dcsf website and that keeps timing out too

Hmm, not a problem here with a stock install of Ubuntu 10.10 and Firefox 3.6.13 (nor with any of the sites the OP mentions).

If I can help with downloading your docs for you, let me know.

---

