---
title: "Networking waiting for headers"
date: 2009-09-17
forum: Networking &amp; Wireless
---

### Post by alphaone on 2009-09-17
Hi Guys,

I've installad a new ubuntu server 8.04.3 installation and when I try to update the system i get the following error:

# apt-get update
Get:1 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) hardy Release.gpg [189B]
98% [waiting for headers]

I've tried to change source.list with at list 4 or 5 different sources (us, gb, etc) but with no luck.

I've also tried to use uptitude update and still doesn't work.

I've no proxy.

A similar server is on a machine in the same network and it's working.

I've tried to copy/paste files over the network and it works fine. I can use it over ssh with no problem.

I'm running ubuntu over vmware ESXi 3.5.

Could you please help me?

Thanks

---

### Post by alphaone on 2009-09-17
I've also tried [http://mirrors.uwa.edu.au/ubuntu/](http://mirrors.uwa.edu.au/ubuntu/) but still doesn't work...

---

### Post by alphaone on 2009-09-21
any help?

---

### Post by alphaone on 2009-09-23
up

---

### Post by alphaone on 2009-09-23
Ok guys,

SOLVED!

For me at least...

the problem was the MTU parameter of my NIC changed from 1500 to 1480.

so:

```
ifconfig eth0 mtu 1480
```

and now everything works perfectly!

Thanks to me :P

---

### Post by tom4everitt on 2010-03-02
Hmm, the same trick did not work for me. Any idea of why changing the mimimun transfer unit would work? Could it have been just luck?


EDIT: In my case it was actually just the google repos (that I use for google chrome), that were slow. It took aptitude 2 min to ignore them. Removing them from software sources made it work fine again...

---

### Post by tyce on 2010-03-15
^That was my issue as well.  Funny to see google slipping that badly.

---

### Post by WMercier on 2010-06-02
Thanks for the fix bro! I've never had this issue with any other install in the past... good work! Does this have any relationship to the router, as in too high of an mtu pulling too much data for a crappy router to handle?

---

