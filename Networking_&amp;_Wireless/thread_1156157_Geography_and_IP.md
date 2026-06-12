---
title: "Geography and IP"
date: 2009-05-11
forum: Networking &amp; Wireless
---

### Post by Rij on 2009-05-11
Hello,

I am curious about the connection between geographic location and IP address. This is not Ubuntu specific so if there is a more appropriate forum, please direct me to it.

However, if the network gurus on this forum is in a particularly generous mood, maybe you can take a stab at my query below?

I understand that it's impossible to accurately predict the geographical location of an IP address. However, is it possible that given two IP addresses allocated to two different ISPs, we can tell if they are in the same neighborhood/city?

So let's say I have IP a.b.c.d allocated by Comcast and w.x.y.z allocated by ATT. Can I take a look at them and say hey, these are both located in the same place? Place can be Santa Monica or Mogadishu, doesn't matter. Just how close the two IPs are to each other.  

Thanks.

---

### Post by pauna on 2009-05-11
> **Rij said:**
> 
I understand that it's impossible to accurately predict the geographical location of an IP address. However, is it possible that given two IP addresses allocated to two different ISPs, we can tell if they are in the same neighborhood/city?

So let's say I have IP a.b.c.d allocated by Comcast and w.x.y.z allocated by ATT. Can I take a look at them and say hey, these are both located in the same place? Place can be Santa Monica or Mogadishu, doesn't matter. Just how close the two IPs are to each other.  


It depends.

If you get your hands on the traceroute data from you to the target addresses, you could try to guess whether the routing to these IP addresses go to the same city. The ATT & Comcast router names shown in the traceroute will not be similar, but they usually contain some kind of locative information.

Then again, there are services on the net that claim to know where a particular IP address is geographically located (for example [http://www.geoiptool.com/](http://www.geoiptool.com/) and commercial [http://www.maxmind.com/app/ip-location](http://www.maxmind.com/app/ip-location)). They have built up a database of address location information, which may or may not be accurate.

---

### Post by Rij on 2009-05-13
Yeah. I did check out maxmind. They essentially depend on a multitude of techniques in combination, including collecting user data, to make the guess as accurate as possible. Although, like I have mentioned before, I don't necessarily care about the location of a IP, rather the location relative to each other with multiple IPs. 

So I guess, the answer is there is no sure-shot way.

---

