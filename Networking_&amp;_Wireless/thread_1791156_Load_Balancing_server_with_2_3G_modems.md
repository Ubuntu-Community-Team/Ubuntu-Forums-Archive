---
title: "Load Balancing server with 2 3G modems"
date: 2011-06-26
forum: Networking &amp; Wireless
---

### Post by joeizang on 2011-06-26
Hi y'all,

I would like to say first and foremost that I have tried to lookup what I can find about this thing I am doing and most of the time all I have found are either un-replied posts or vaguely explained answers but here is what I want to do:

I want to setup a small gateway for my new office using two 3G internet providers offering Huawei usb modems. So I would like to have two internet links active per time and have one LAN consuming from the two links. I have seen the phrase Load Balancing all over the place but they all show their examples using ethernet and static IP's. My providers give DHCP ip addresses so is there anything I need to know and can anyone point me in the direction of some tutorial or howto i can follow to do this? 

God Bless

Joe

---

### Post by Steve.the.Goolie on 2011-06-26
Hi Joe,

The first thing you need to do is contact your service provider and tell them what you want to do, as it is not possible just to do it from your end.
They will probably tell you they cannot do it, or will charge you a ridiculous amount for the service, and specify what equipment you need (probably Cisco).

I know it sounds as if it should be simple, but I'm afraid it is not.

Sorry to be negative, but I have just been through the process!

Steve

---

### Post by Sylslay on 2011-06-26
Hi all

get 2 usb huaweii 3 G.
get 2 Dlink DIR - 635 or something simillar - update.

Then plug each Huaweii 3g into Dlink DIR-635, check if routers (internet) working thru 3g modems.

After that get balancing router [http://www.amazon.com/Cisco-RV082-8-port-100-Router/dp/B0000ZI1FG](http://www.amazon.com/Cisco-RV082-8-port-100-Router/dp/B0000ZI1FG)
Spec: 
[http://www.wireless-router-net.com/cisco-rv082-load-balancing-router](http://www.wireless-router-net.com/cisco-rv082-load-balancing-router)


 and connect both D-link on Lan network to that balancing router.

So: need 5 pice of hardwere and 3 lan cables. Routers need be power-on all the time.


3g                        3g
|                          |
|                          |
Dlink-lan-router          Dlink lan-router
|                          |
|                          |
   Cisco  balancing router
          |
          |
          Lan with Yours PC


check manaul of fiew routers, some maight works as balancig router too.

---

