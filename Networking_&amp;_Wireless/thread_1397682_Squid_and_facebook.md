---
title: "Squid and facebook"
date: 2010-02-03
forum: Networking &amp; Wireless
---

### Post by elliotbeken on 2010-02-03
hi all i have squid working well on port 80

i want to know how to get it to work with facebook as it does not work properly

any ideas ??

---

### Post by tripolitan on 2010-02-04
what exactly is the problem..........?

---

### Post by elliotbeken on 2010-02-04
well i use the proxy when i am at college and every other site that is normally blocked works fine but facebook gets to the login page then once you login it just loads and loads

basically facebook wont log in

---

### Post by thecoshman on 2010-02-04
I am rather confused as to what your problem is. Squid is a proxy system is it not... so if you are at uni with your laptop, why are you running squid on it?

If you have squid running on a server at you own home, have you set it up as in such a way that you had to enter proxy details into your laptop, or is it done transparently?

If you have to enter proxy details to use your internet at home, you will need to remember to turn them of when at uni, as you will not be able to connect to the proxy server. You should be able to just un-check the 'use proxy' option, it will save your details, so you can just check it again later.

If it is causing you issues at home, you could try configuring your proxy settings as to not perform any caching (which I believe to be the most common reason to use squid at home) for facbook, you will probably need to find the IP (or IPs) that facebook use to do this.

Their are a lot of things that could be affecting everything, so the more info you can give the easier it will be to help you out.

---

### Post by elliotbeken on 2010-02-04
my squid server is at home and i have put all of the settings in my laptop but facebook dont work

---

### Post by thecoshman on 2010-02-04
By the sounds of it then you need to look into configuring squid to not cache for facebook. But I have not looked up much with squid beyond what it basically dose, so I can't help further.

---

### Post by RawShark on 2010-07-22
I can verify the issue. When caching via squid, Facebook works fine like any other site. However, if you try to LOGIN to Facebook, you get a blank page. This happens even if you use

```
acl facebook dstdomain .facebook.com
cache deny facebook
```

or similar. The only way around is to, as you say, tell your browser to not pass facebook.com to the proxy, but this is not practical for a large network where you are implementing transparent proxying.

---

### Post by diilbert on 2010-07-22
I have the exact same problem.  I implemented the proxy over the weekend and facebook worked fine.  Since yesterday morning I have been getting blank pages and load failures.  My only current fix is to disable the transparent proxy and bypass squid.

I tried the following without success:
1)  Disable caching for all sites
## disable caching
cache deny all
cache_dir null /tmp

2)  Decrease the connect_timeout to 20 seconds and forward_timeout to 1 minute as per [http://www.mail-archive.com/squid-users@squid-cache.org/msg66489.html](http://www.mail-archive.com/squid-users@squid-cache.org/msg66489.html)

3)  Turned off the firewall rules for the transparent proxy and went directly to the proxy via browser configuration

So I can say what it is not, but not what the problem is.

I am running the stock install of Squid on Debian 5.0 --> 2.7.STABLE3 with squidGuard 1.2.0

Hopefully someone has an idea.

---

### Post by diilbert on 2010-07-22
After Googling a bit I found this: [http://www.linuxquestions.org/questions/linux-software-2/facebook-and-squid-privacy-777649/](http://www.linuxquestions.org/questions/linux-software-2/facebook-and-squid-privacy-777649/)

So I changed this setting:
forwarded_for = off

So far, so good.  

More details on why this happens would be useful, so drop them if you have them.

---

### Post by craigslist123 on 2010-07-22
I like facebook more than squidoo   :p

   ---------------
  [FONT=&quot][Craigslist Search](http://www.allofcraigslist.com)[/FONT]

---

### Post by diilbert on 2010-07-22
For me it is getting a handle on what the random people passing through my house are accessing.

---

