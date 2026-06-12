---
title: "Crazy problem with Ebay links!"
date: 2009-02-13
forum: Networking &amp; Wireless
---

### Post by DanGent on 2009-02-13
Firstly, this isnt an Ubuntu problem, but i love Ubuntu (using it now) and i'm hoping this is an excuse to install ubuntu on someones computer!

On a computer I have a problem where I can get onto ebay.com, .co.uk, .ie or etc.  but when any link is clicked;  computers.ebay.com or an item for sale, it gets a timed out/this document contains no data error. on pinging, the DNS gave back the correct IP address but there was no reply from the ping to computers.ebay.com or etc

tried everything i could think of over the course of 4 hours; taking off norton, disabling all firewalls, scanning for spyware.  flushing the DNS cache, reenableing the DNS service. turned off all internet security settings.  turned down the fragmentation threshold on the wireless card (MTU). plugged the PC in by cable to the BT homehub. disabled IPv6 on the wireless card, reenabled and enabled it in the browser.  tried IE and firefox. tried another user profile

a laptop wired into the BT homehub router could browse any ebay page, so doesnt seem a router/BT problem.

only thing left to try (as i ran out of time), is to boot into knoppix with it wired up to the router and see if that works. i think thats the most important thing to try as it will tell me whether its a windows problem.

also, which confuses me further, i managed to get hold of a 3G dongle, and when the PC was accessing the internet thru this, it worked. so it was something to do with the PC connected into the router. i might have to get a 3G dongle for reasons like this....

The PC's IP was being assigned by DHCP, haven't tried setting up a static IP, though the BT homehubs IP by wasn't the usual 192.168.1.1 but something like 192.168.254.1, i think, or similar, maybe it ends in 100+. does that sound normal?

in the event viewer and netstat there wasnt anything suspect. using a proxy server could be an idea but i think booting into the knoppix live CD (which should automatically support the ethernet port) will tell me whether its a software problem or not. just dont really want to reinstall windows for something that looks like its not a big problem!

i tried loads of different websites as well but couldnt find any, do you lot know if ebay uses any specific web technologies that other sites dont?
gonna email BT and ebay and see if they can shed any light on this!

---

