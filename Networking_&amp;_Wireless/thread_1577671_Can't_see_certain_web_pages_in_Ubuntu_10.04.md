---
title: "Can't see certain web pages in Ubuntu 10.04"
date: 2010-09-19
forum: Networking &amp; Wireless
---

### Post by nsiva007 on 2010-09-19
Hi folks,
       I'm using a wired DSL broadband connection on ubuntu 10.04,the problem is i am unable to see certain web pages in my firefox and chrome as well... some web pages aren't loading at all.. but these webpages loads in windows..! what's this problem because of?? any solutions?? eg of pages not loading [http://sourceforge.net/ ]("http://sourceforge.net/")[http://shaastraiq.heroku.com ]("http://shaastraiq.heroku.com/"),[http://speedtest.net]("http://speedtest.net/")
 and some other pages...!! any fix available???

---

### Post by realzippy on 2010-09-19
All examples load fine here (chromium and firefox)....

---

### Post by lovinglinux on 2010-09-19
Have you tried to disable ipv6? See the fifth item on [this list]("http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html").

---

### Post by nsiva007 on 2010-09-19
hey i disabled ipv6 too but still these pages and some others are not loading... not even in chrome..!

---

### Post by lovinglinux on 2010-09-19
Can you ping those addresses IP numbers or access the sites via IP address? Do you have any issues with the Update Manager when downloading packages?

---

### Post by nsiva007 on 2010-09-20
I can ping those sites.. some have 0% packet loss while some has 9 or 10 % packet loss.... but still these pages aren't showing up on any of my browsers in ubuntu..!
And i have absolutely no problems whatsoever with update manager,its downloading packages at the max speed possible....!

---

### Post by lovinglinux on 2010-09-21
> **nsiva007 said:**
> I can ping those sites.. some have 0% packet loss while some has 9 or 10 % packet loss.... but still these pages aren't showing up on any of my browsers in ubuntu..!
And i have absolutely no problems whatsoever with update manager,its downloading packages at the max speed possible....!

Should be a DNS issue then. Try a different DNS server, like Google DNS or OpenDNS.

---

### Post by nsiva007 on 2010-09-22
I'm using OpenDNS ... and this problem still persist...!
[http://sourceforge.net/](http://sourceforge.net/) is still not opening..! so are the other pages i mentioned..!

---

### Post by lovinglinux on 2010-09-22
Create a new Ubuntu test user account and test it. If the problem does not persists, then it might be some Gnome settings messing with your connection.

---

### Post by nsiva007 on 2010-09-26
what user account are you talking about and what test???

---

### Post by lovinglinux on 2010-09-27
> **nsiva007 said:**
> what user account are you talking about and what test???

I'm talking about a new Ubuntu user account. When you create a new user, it will start with the default settings for everything, so if the problem doesn't persist, then you will know is a problem in your personal configurations.

---

### Post by nsiva007 on 2010-09-28
I created a guest account also and there also it was not displayed..! i could use wget command but when i open the html file its is also not showing up on the browser...!! plz help me out with this problem...!!!

---

### Post by lovinglinux on 2010-09-28
> **nsiva007 said:**
> I created a guest account also and there also it was not displayed..! i could use wget command but when i open the html file its is also not showing up on the browser...!! plz help me out with this problem...!!!

Most likely your problem is the network then. If you have a router, change the mtu to 1492 instead of 1500.

BTW, have you checked if your Ubuntu CD was defective before installing?

---

### Post by Todamont on 2010-09-28
bump

---

### Post by nsiva007 on 2010-09-29
Nope my ubuntu cd wasn't defective at all.... i was able to see all the pages before a recent update for firefox..! i.e now i'm running firefox 3.6.10..! i think my mtu is set at 1492 only i've checked it also...! is there a code to check it??
I'm not able to see the pages in chromium also..! what could the problem possibly be...!!
I'm still not able to access [URL="http://sourceforge.net/"]http://sourceforge.net 
[/URL]

---

### Post by lovinglinux on 2010-09-29
> **nsiva007 said:**
> I'm still not able to access [URL="http://sourceforge.net/"]http://sourceforge.net 
[/URL]

Can you access it using a proxy like [http://hidemyass.com](http://hidemyass.com) ?

---

### Post by nsiva007 on 2010-09-30
Yea yea i can access all these sites through the proxy site [http://hidemyass.com]("http://hidemyass.com/")
no problems.. but i can't use proxy all the time na...! what is the problem actually???? kindly help sort out the trouble

---

### Post by lovinglinux on 2010-09-30
> **nsiva007 said:**
> Yea yea i can access all these sites through the proxy site [http://hidemyass.com]("http://hidemyass.com/")
no problems.. but i can't use proxy all the time na...! what is the problem actually???? kindly help sort out the trouble

The proxy was just for troubleshooting. Since you can access the site, then I think the problem is on your DNS queries.

I'm not sure it will help, but you could do the third item on [this list.]("http://firefox-tutorials.blogspot.com/2010/05/preferences-tweaks.html"). This will reduce the frequency of DNS querying. But first, make sure you flush the browser cache (Tools >> Clear Recent History) and then the DNS cache using [DNS Flusher]("https://addons.mozilla.org/en-US/firefox/addon/7408/").

---

### Post by nsiva007 on 2010-10-01
I Tried the above steps but its not working too...! I'm using openDNS and i'm unable to visit the pages in my chromium also ..! think from that perspective...!

---

### Post by nsiva007 on 2010-10-01
bump

---

### Post by nsiva007 on 2010-10-07
bump

---

### Post by nsiva007 on 2010-10-14
bump

---

### Post by nsiva007 on 2010-10-14
now i upgraded to ubuntu 10.10 and still the problem persists....!

---

### Post by nsiva007 on 2010-11-16
> **nsiva007 said:**
> now i upgraded to ubuntu 10.10 and still the problem persists....!
bump

---

