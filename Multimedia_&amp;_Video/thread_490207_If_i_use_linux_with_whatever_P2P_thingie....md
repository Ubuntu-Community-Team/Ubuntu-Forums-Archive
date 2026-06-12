---
title: "If i use linux with whatever P2P thingie..."
date: 2007-07-02
forum: Multimedia &amp; Video
---

### Post by -=Viper=- on 2007-07-02
If i use linux with whatever P2P thingie linux uses will my ip be sent out?  Thanks everyone!

---

### Post by -=Viper=- on 2007-07-02
well does anyone know??  Thanks everyone!

---

### Post by Alex Fernandez on 2007-07-02
Works the same damn way a p2p program on any other OS works.

And IPs are not sent out, its part of how network traffic is routed (go learn about networking both local and wider like the internet). So unless you are bouncing off proxies then yer your IP is visible, as it should be.

---

### Post by MCSE_Crossover on 2007-07-02
> **-=Viper=- said:**
> If i use linux with whatever P2P thingie linux uses will my ip be sent out?  Thanks everyone!

Yes, it does. By default, there is no masking done on your IP traffic. It is part of the data payload that traverses over the internet. There are way's around it, such as mentioned bouncing through proxies, "anonymizers" or onion routing. Do a google search for "TOR" and you'll learn a bit. The OSI model can be complex at times, but that is a good place to learn as well...particularly layers 1-4. That will give you a good idea of data encapsulation and delivery.

[http://en.wikipedia.org/wiki/OSI_model](http://en.wikipedia.org/wiki/OSI_model)

---

