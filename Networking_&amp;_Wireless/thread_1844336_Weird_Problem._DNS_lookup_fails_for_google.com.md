---
title: "Weird Problem. DNS lookup fails for google.com"
date: 2011-09-15
forum: Networking &amp; Wireless
---

### Post by saks13 on 2011-09-15
I just installed ubuntu 11.04 on my computer and everything has been working great except that I cannot access any search engine on either chromium or firefox. when I try to go to google.com, bing.com, or yahoo.com chromium tells me that the DNS lookup failed but any other website works. 
Thanks for any help

---

### Post by lmarmisa on 2011-09-15
> **saks13 said:**
> I just installed ubuntu 11.04 on my computer and everything has been working great except that I cannot access any search engine on either chromium or firefox. when I try to go to google.com, bing.com, or yahoo.com chromium tells me that the DNS lookup failed but any other website works. 
Thanks for any help

Try to edit the network configuration. Select Automatic (DHCP) addresses only and use [the Google public DNS servers 8.8.8.8 and 8.8.4.4]("http://code.google.com/speed/public-dns/docs/using.html").

---

### Post by fdrake on 2011-09-15
can you also post the result for
```

sudo aptitude install traceroute
ping google.com
traceroute google.com

```

this is a pretty odd situation. Did you make sure that these domains aren't blacklisted in your browsers?

---

### Post by saks13 on 2011-09-15
I edited my network configuration and it seem to have done the trick! I can access those websites now.
Thank you so much for all the help.

---

### Post by Cincinnatux on 2012-04-13
> **lmarmisa said:**
> Try to edit the network configuration. Select Automatic (DHCP) addresses only and use [the Google public DNS servers 8.8.8.8 and 8.8.4.4]("http://code.google.com/speed/public-dns/docs/using.html").

I experienced a similar problem in the past week, where other computers (Windows-based) on my home network had no difficulties accessing the Internet, but my Natty machine was struggling sporadically.  Specific web sites were not especially problematic; most websites failed the first time I tried to access them.  Repeatedly hitting 'reload' eventually got the page to load up.  Making this change in my DHCP settings appears to have resolved my problem, too.  Thanks, lmarmisa!

---

### Post by jonobr on 2012-04-13
Hi All


The best way to solve something like this is to do a wireshark trace and see whats going on at a packet level.

```
sudo tcpdump -vvv -i any port 53
```

also when the problem is occurring do an 

```
nslookup google.com
```
and put in the ip of google directly into your browser.


What could be happening is that your ISP may have an erroneous entry for google.com.
Sites like google have multiple Ips in the return for the dns lookup and if one is wrong, this may work sometimes and not others.

Even if thats not the issue, performing the above steps will hopefully localise where the issue is.
You can continue using 8.8.8.8 if it works for you, but for me, that would be like a splinter in my mind knowing my resoltuion was failing periodically

Cheers

jonobr

---

