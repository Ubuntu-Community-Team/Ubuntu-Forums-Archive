---
title: "Connected, But no internet"
date: 2009-02-05
forum: Networking &amp; Wireless
---

### Post by luig1 on 2009-02-05
I already have local access. I can ping in my local network but not an external ip. I have figured out how to solve the atheros driver problem after 3 hours of searching. Heres the solution:[http://blog.hyperandy.com/2008/11/01/atheros-ar242x-ubuntu-810-ibex/]("http://blog.hyperandy.com/2008/11/01/atheros-ar242x-ubuntu-810-ibex/")
I figured out the problem I'm having is that I have no name servers specified but I dont know any method of figuring them out.

---

### Post by superprash2003 on 2009-02-06
you could specify name servers this way [http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html) .. are you able to open [http://209.85.171.100](http://209.85.171.100)

---

### Post by luig1 on 2009-02-06
I guess dns wasn't the problem and no I cant browse that page or ping it. I can only browse or ping on my local network.

---

### Post by madverb on 2009-02-07
Sure the router isn't blocking the wireless connections to external?

---

### Post by superprash2003 on 2009-02-07
could you post ifconfig output from terminal

---

