---
title: "Setting Up a home VPN"
date: 2013-01-05
forum: Networking &amp; Wireless
---

### Post by nd456 on 2013-01-05
Hello All, Looking to set up a vpn server off the the ubuntu desktop edition, it would be on 10.04

---

### Post by ahallubuntu on 2013-01-05
I recommend and use OpenVPN.  I've set it up on a couple of Ubuntu 10.04 boxes.  There are a couple of "How To" guides you can find by googling.  I actually use OpenVPN at the moment via my DD-WRT router and leave my home servers in sleep until I need to wake them remotely via WOL.  Not all versions of DD-WRT include OpenVPN, only versions for routers that have enough NVRAM.  You can sometimes find old Linksys WRT54G routers cheap (use them as gateways, you can disable wireless if you have an N router, use that instead).  But get version 4 or older or get a WRT54GL router to use DD-WRT with OpenVPN.

If you use an Ubuntu client (laptop?), be sure to install the network manager OpenVPN plug-in so you can connect to the VPN that way.

---

### Post by nd456 on 2013-02-10
I ironicly have an extra Linksys WRT54G from back in the day. Can you send me a tutorial link?
It'd be setup behind a gateway though, as I don't want to disturb my gigabit setup
Thanks, Andy

---

### Post by ahallubuntu on 2013-02-10
Try this:

[http://www.dd-wrt.com/wiki/index.php/VPN_(the_easy_way)_v24%2B](http://www.dd-wrt.com/wiki/index.php/VPN_(the_easy_way)_v24%2B)

Check the version, though: if the version is 5 or higher, you can't run the OpenVPN-enabled image of DD-WRT - not enough RAM/NVRAM.  Not that these routers are expensive to buy.  Our local Goodwill thrift store had a stack of them today (version 1.1 or version 2) for $7.99 USD.

If you want to use this as your gateway, though, you'll need to put everything on your network on the new LAN you'll be creating with the WRT54G.  Then forward port 1194 through your existing router to the WAN of the WRT54G.

---

### Post by nd456 on 2013-03-13
Turns out it's a V8. (I do like dd-wrt though) Gonne lookfurther into seting it up on a desktop after that didn't work out.

---

