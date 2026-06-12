---
title: "I wish to re-task my old PC as a network Gateway"
date: 2012-10-14
forum: Networking &amp; Wireless
---

### Post by Vektor67 on 2012-10-14
My Home Network is small but I have an old PC just sitting around and I've been wanting some sort of a Real Deal Hardware Firewall. Beyond that which exists on my Belkin N750DB Router. I have an old wireless router(Netgear WNR2000) and PC (ASUS P5Q Deluxe, E8600,4GB Ram lots of storage ect) I'd like to be able to have a Home Server as well as a hardware firewall for DHCP,DNS,NAT,Ad Blocking. I'd like to consolidate as many of these functions on one spare machine and not have to run a separate firewall on each device and ad blocking on each browser. I'm not aware of whats available or even possible. My first thought was to just build an Ubuntu Box and use some sort of free VMware Appliance guest to manage my home network, but thats probably not feasable for some good reason or why isn't everyone doing it?  Any ideas or tips to point me in the right direction would be greatly appreciated. I'd just hate to waste my time crash coursing on stuff that ultimately won't meet my needs.
Thanks

---

### Post by 2F4U on 2012-10-14
You could use Ubuntu Server as a basis. 

[https://help.ubuntu.com/12.04/serverguide/index.html](https://help.ubuntu.com/12.04/serverguide/index.html)

Some ideas what can be done with a Ubuntu home server:

[http://www.howtoforge.com/creating-a-home-media-and-file-server-with-ubuntu](http://www.howtoforge.com/creating-a-home-media-and-file-server-with-ubuntu)
[http://kdmurray.net/2012/06/21/home-server-build-part-1-introduction-ubuntu-school/](http://kdmurray.net/2012/06/21/home-server-build-part-1-introduction-ubuntu-school/)

And finally, how to use Ubuntu as a router:

[https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)

---

### Post by Cheesemill on 2012-10-14
Take a look at SmoothWall.

It's much easier to set up than Ubuntu Server and has a nice web interface.

[http://www.smoothwall.org/about/](http://www.smoothwall.org/about/)

---

### Post by ahallubuntu on 2012-10-14
I used to use an old PC as a firewall/gateway, but once I discovered the ability to run DD-WRT (Linux-based) firmware on an old router, I dumped the PC.  Typically these routers only consume 4-5 watts of power whereas an old PC is likely to consume far more.  DD-WRT runs on many routers, most commonly the Linksys WRT54G (old now but still very reliable, easy to find used and cheap).  You may feel good about re-purposing your old PC, but if you leave it on 24/7 as a gateway, you may be wasting a lot of power needlessly, too.

FYI, there is a version of DD_WRT available for the WNR2000 (V2) - go to [www.dd-wrt.com](www.dd-wrt.com) and check it out.  DD-WRT is awesome - it has most of the features you would want in a firewall, most likely, far beyond the manufacturer's firmware.

I'm not aware of any way to block ads on a firewall; I guess you could try to block various websites that serve them up, but I'm not sure how practical that is...

---

