---
title: "Change of default MTU value in Ubuntu 8.10"
date: 2008-12-20
forum: Networking &amp; Wireless
---

### Post by Pidgin on 2008-12-20
Has anyone noticed a change of the dafault MTU value from 1500 to 576 since 8.10? That has caused my Firefox and Opera randomly failing to open web pages. After setting the value to 1500, Firefox and Opera works well. Hope that would be helpful to some people.

---

### Post by jonobr on 2008-12-21
Actually yes, 

I have noticed a few people posting whos MTU values are something other then 1500 when using eth0.
I saw a few with ETH and 576 which I thing per standard is the default min MTU size and is for dialup.

Most of those people mentioned 8.10

I have seen a few other odd ones, however, interesting you say and saw that....

Wondering if there are others out there the same

---

### Post by lensman3 on 2008-12-21
Take a look at the "tracepath" program.  On my system if is found in /usr/sbin.  It purpose is to discover the MTU across a path.  It does return the path even if the path is asymmetric. 

The smaller MTU sounds like a holdover from the days of dial up modems.  It get a faster interactive response, the MTU is shortened  to around 512 bytes.

---

### Post by Harry_Iyer on 2008-12-21
> **Pidgin said:**
> Has anyone noticed a change of the dafault MTU value from 1500 to 576 since 8.10? That has caused my Firefox and Opera randomly failing to open web pages. After setting the value to 1500, Firefox and Opera works well. Hope that would be helpful to some people.


Thank you so much for bringing this to light. I had tried almost every other thing suggested in this forum to speed up a slow internet connection on Ubuntu (disable IPv6, openDNS etc.) but only today did I notice that my MTU was smaller than the vatican. Setting it to 1500 sent my system monitor resources graphs skywards!

Special thanks to **_[SIZE="7"][COLOR="Red"]jonobr[/COLOR][/SIZE]_** - I have been following all your helpful posts regarding internet related issues and dare I say they have come in handy.

_

---

