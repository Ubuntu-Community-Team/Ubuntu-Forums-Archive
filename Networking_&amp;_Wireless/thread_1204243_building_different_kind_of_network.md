---
title: "building different kind of network"
date: 2009-07-04
forum: Networking &amp; Wireless
---

### Post by nivke2000 on 2009-07-04
hi,
 
i am trying to build an irregular kind of network at home. i want it to be like this: internet>modem>computer a>router>other computers. "comupter a" has 2 nic's and should act as Proxy. does anyone knows how i configure this kind of thing? do i need any other equipment from what i already have?
 
thanks,
niv

---

### Post by bobbob1016 on 2009-07-04
I don't know exactly how to make this type of network, but the better way would be internet>modem>computer a>*switch*>other computers.  A switch instead of router would be preferred since 'computer a' should give IPs to the other computers, it becomes more complex with a router, since 'computer a' and the router want to give IPs.

It might help if you say why you want to do this too, so someone could suggest other ways of doing it.

---

### Post by cariboo on 2009-07-04
You need to set up internet connection sharing, have a look at this [page]("https://help.ubuntu.com/community/Internet/ConnectionSharing").

---

