---
title: "Trouble with Apache2: localhost not working."
date: 2009-02-10
forum: Networking &amp; Wireless
---

### Post by Amablue on 2009-02-10
I've installed Apache2 and I have it running, but when I try to visit [http://localhost](http://localhost) it doesn't work. Nothing happens. I was expecting at least an "It works!" page. :(

I checked /etc/hosts and it contains "127.0.0.1 localhost". I'm not sure what else to check.

---

### Post by dmizer on 2009-02-10
You will see the "it works" page by browsing to [http://server-ip/apache2-default/](http://server-ip/apache2-default/)

If you look in /var/www you will see why. :)

---

### Post by Iowan on 2009-02-10
Are you visiting "localhost" from the Apache machine itself?

---

### Post by Amablue on 2009-02-10
> **dmizer said:**
> You will see the "it works" page by browsing to [http://server-ip/apache2-default/](http://server-ip/apache2-default/)

If you look in /var/www you will see why. :)

That doesn't work either. I see files there when I navigate there manually, but going to [http://localhost/apache2-default/](http://localhost/apache2-default/) has the same problem as just plain [http://localhost/](http://localhost/). It just doesn't load. 

> Are you visiting "localhost" from the Apache machine itself? 

Yes.

---

### Post by dmizer on 2009-02-11
Any errors when you run the following command:
```
sudo /etc/init.d/apache2 restart
```

---

