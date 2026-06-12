---
title: "How often are DNS lookups performed?"
date: 2009-07-05
forum: Networking &amp; Wireless
---

### Post by tomcat2007 on 2009-07-05
How often are DNS lookups performed?  I'll navigate to a website then a few minutes later that infuriating "looking up..." message appears in the lower left hand corner of my browser and stays there for up to 30 seconds.  How can I change the interval at which the cache is refreshed with a new lookup?  Once the lookup is performed, I see no reason to repeat it while on the website.

Am using Jaunty 64 bit with an HP Pavilion dv9000/broadcom 4311.

---

### Post by Boondoklife on 2009-07-05
I think I read somewhere firefox only caches dns lookups for 1 minute. There really is a reason for this and it is if a server goes down and they have a round robin setup going then unless you are asking for a new IP rather frequently then you will not know it and get the server can not be found errors. You may want to lookinto useing a third party dns like opendns to see if it loads faster for you.

---

### Post by superprash2003 on 2009-07-06
if lookups take a long time for you which is noticeable then you should try changing to another DNS Server like opendns

---

### Post by slickflick on 2009-07-06
my linksys router caches DNS lookups, but I'm using that as my primary DNS, not everyone does this.

---

