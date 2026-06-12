---
title: "ubuntu 12.10 and mythtv"
date: 2012-12-02
forum: Mythbuntu
---

### Post by wayneandleanne on 2012-12-02
Hi gang,


just installed mythtv and setup the backend (same machine) now i get an error 

"Cold not connect to the master backend server, Is it running? Is the ip address set for it in myth-setup correct?" 

Can anybody help?
What do i do next?

Wayne

---

### Post by tgm4883 on 2012-12-02
> **wayneandleanne said:**
> Hi gang,


just installed mythtv and setup the backend (same machine) now i get an error 

"Cold not connect to the master backend server, Is it running? Is the ip address set for it in myth-setup correct?" 

Can anybody help?
What do i do next?

Wayne

We'll need a bit more info. What did you set the backend IP address to in mythtv-setup? Did you set it to 127.0.0.1, or did you set it to your private network IP? If the latter, you'll need to fire up mythbuntu-control-centre and activate the mysql service on the mysql tab (it makes it able to connect from external IP addresses).

---

### Post by wayneandleanne on 2012-12-03
It's set to 127.0.0.1, I've tried to purge the mythtv package's and re-install but to the same effect.
What am i doing wrong?

---

