---
title: "Problems connecting"
date: 2010-03-30
forum: Networking &amp; Wireless
---

### Post by ror on 2010-03-30
Hello, I bought a wireless card (Edimax EW-7128g) that I could use on ubuntu. It worked well, until I moved back home - when I couldn't connect at all to the router. I gave up for a few months, until I decided to have another go. I'm using the same card and ubuntu 9.10. The network is detectable, but when I put in the key it doesn't connect. I'm definitely putting in the right key, and all other computers running on windows connect with no problems. 

So I'm wondering if some routers are not compatible with linux? Would installing the driver suggested by the site have any difference? Or am I going to have to buy a new router?

---

### Post by Iowan on 2010-03-30
[Here]("http://ubuntuforums.org/showpost.php?p=8703594&postcount=26") is kind of a kludge you can try...

---

### Post by ror on 2010-04-01
> **Iowan said:**
> [Here]("http://ubuntuforums.org/showpost.php?p=8703594&postcount=26") is kind of a kludge you can try...
Thanks for the suggestion. I couldn't find the dhconfig.conf file, so I added 
    send vendor-class-identifier "MSFT 5.0";
to /etc/dhcp3/dhclient.conf, but it still doesn't connect. I take it dhclient.conf and dhconfig.conf are essentially the same files?

---

### Post by Iowan on 2010-04-01
*/etc/dhcp3/dhclient.conf* is the correct file. I was trying to give credit where due - but missed that the filename was wrong. I'll edit the post with right information - sorry it didn't work for you.

---

