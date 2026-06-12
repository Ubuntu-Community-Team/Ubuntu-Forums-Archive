---
title: "Two Ethernet Cards help"
date: 2011-01-21
forum: Networking &amp; Wireless
---

### Post by joolzg on 2011-01-21
I have 2 cards installed in my machine, one is for general use to the outside world whilst the other is doing my Multicast transcoding stream.

Problem is that because of ffmpeg i need to have multicast data on ETH0 but this causes the internet to crawl so what i am looking at is how to setup the network route settings so that multicast is ONLY found on ETH0 and ALL OTHER traffic is on ETH1

Ive gone into the network settings and "editing IPV4 routes for ETH0" but i cant figure out exactly what to put in the boxes

my idea was 224.0.0.0. 224.0.0.0 * *

but what do i put in gateway and metric

joolz

---

### Post by adoniasv on 2011-10-22
Try this

[http://kindlund.wordpress.com/2007/11/19/configuring-multiple-default-routes-in-linux/](http://kindlund.wordpress.com/2007/11/19/configuring-multiple-default-routes-in-linux/)

or

[http://www.linuxhorizon.ro/iproute2.html](http://www.linuxhorizon.ro/iproute2.html)

Wks 4 me!

@adoniasv

---

