---
title: "monitering use of other pc on the same network"
date: 2009-04-20
forum: Networking &amp; Wireless
---

### Post by linux newb on 2009-04-20
hi, I have a teen and i want to monitor what kind of, and lentgh of his use of the internet from another computer via same router. just wondering, is this possible?

---

### Post by celthunder on 2009-04-20
wireshark does this..assuming you are on the same router and don't have a switch in between you (so you are in the same collision domains though broadcasts usually don't matter too much (arp/icmp are usually the only broadcasts youll see anyway).  Be prepared to spend some time going through the output though.  Some "routers" (those thingies you buy at walmart they call routers) log web traffic urls so check if yours does that if thats what you are looking for.

---

### Post by linux newb on 2009-04-20
thx alot celthunder

---

