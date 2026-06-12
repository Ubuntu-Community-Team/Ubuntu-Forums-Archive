---
title: "differrence between a router, an acces point , and a bridge"
date: 2009-06-27
forum: Networking &amp; Wireless
---

### Post by zopanp on 2009-06-27
hello everyone,
as told in the title i would like to know the difference beetween a router, an acces point, and a bridge?
thanks

---

### Post by anystupidname on 2009-06-27
This isn't really an Ubuntu related question or even linux related...

In laymen's terms, an access point is typically a wireless router. You can have wireless bridges too but that serves a different purpose.

A router (sometimes referred to as a "layer 3 switch") and a bridge are similar network devices but function slightly differently. A bridge is a layer 2 device and a router connects two different networks/subnets and is a layer 3 device ([see OSI model]("http://en.wikipedia.org/wiki/OSI_model"))

See also:
[http://en.wikipedia.org/wiki/Router#Forwarding_plane_.28a.k.a._data_plane.29](http://en.wikipedia.org/wiki/Router#Forwarding_plane_.28a.k.a._data_plane.29)
[http://en.wikipedia.org/wiki/Network_bridge](http://en.wikipedia.org/wiki/Network_bridge)

---

### Post by zopanp on 2009-06-27
thanks for the fast reply and i'm sorry for asking a non ubuntu question on an ubuntu forum, but because i konow that i'll find a fast and competent reply on this forum.
I have an acces point in a part of my house and i want to expand it with an other router or acces point at the other side of the house, is it possible?
thanks.

---

### Post by anystupidname on 2009-06-27
> **zopanp said:**
> thanks for the fast reply and i'm sorry for asking a non ubuntu question on an ubuntu forum, but because i konow that i'll find a fast and competent reply on this forum.
I have an acces point in a part of my house and i want to expand it with an other router or acces point at the other side of the house, is it possible?
thanks.

Certain routers have the aforementioned "wireless bridge" capabilities aka [WDS]("http://en.wikipedia.org/wiki/Wireless_Distribution_System") and/or support alternative firmware that provides those capabilities. You can essentially piggyback your second router onto your internet connected router.

Alternate firmwares that I know of: (* next to ones I'm certain support WDS)
[DD-WRT]("http://www.dd-wrt.com/wiki/index.php/WDS_Linked_router_network")*
[tomato]("http://www.polarcloud.com/tomatofaq#how_do_i_use_wds")*
[http://openwrt.org/](http://openwrt.org/)
freewrt
x-wrt
and others

---

