---
title: "Weird internet problem"
date: 2009-12-25
forum: Networking &amp; Wireless
---

### Post by ibarash on 2009-12-25
Hello,
 
I am new to ubuntu. Installed 9.10 on my laptop about a week ago.
everything was fine. it automaticly recognized wireless drivers and everything worked just fine untill a power breakdown earlier today.
 
now, my laptop is able to connect the router, but i cant reach the internet.
 
i tried to restart - both laptop and router , and nothing.
 
can anyone help me?

---

### Post by Iowan on 2009-12-25
Ubuntu can ping router? Can it ping internet site by IP address?

---

### Post by ibarash on 2009-12-25
it says unknown host

---

### Post by Iowan on 2009-12-26
"Unknown host" sounds like DNS problem... or was that by IP address?
I suppose a first step would be to check **ifconfig -a** to see if machine has an IP address.

---

