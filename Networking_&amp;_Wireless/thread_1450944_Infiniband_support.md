---
title: "Infiniband support"
date: 2010-04-09
forum: Networking &amp; Wireless
---

### Post by udosoft on 2010-04-09
Hi, 

Will support ubuntu server edition support infiniband in the future?

The kernel modules and basic libs are present, major parts are missing:

for example
infiniband-diags ---> to able to test if it works

and the SDP kernel patch ---> DRBD can use this in the leatest version, but the kernel module ib_sdp is needed


Is it possible to port this to ubuntu?
[http://pkg-ofed.alioth.debian.org/](http://pkg-ofed.alioth.debian.org/)

for example the infiniband-diags-1.4.4_20090314 needs following modification for ubuntu: perl -pi -e 's/function //' scrips/*
due function keyword is not supported in ubuntu's sh

Or is there any infiniband ubuntu repo?
And why not?

---

### Post by freekey on 2010-04-19
I am really interested in an Ubuntu Infiniband/OFED package too.. what's the deal? Should I give up on the search and just make one from scratch?

---

### Post by jsimon on 2010-05-04
I am interested in this as well.

---

### Post by afspear on 2010-07-23
I, too, am interested.

---

### Post by mrpg99 on 2010-09-17
Also very interested in infiniband support for Ubuntu! (at least in the server versions)

---

