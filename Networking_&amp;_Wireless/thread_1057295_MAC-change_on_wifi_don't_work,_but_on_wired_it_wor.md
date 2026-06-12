---
title: "MAC-change on wifi don't work, but on wired it works?!?"
date: 2009-02-01
forum: Networking &amp; Wireless
---

### Post by 8pia on 2009-02-01
Trying to change MAC on my wireless, but can't get it to work. On the wired it works without any problems.
I get no errors, just liked it worked..But when I check it is still the original MAC.

This is what I tried:

#ifconfig "wlan0" down
#ifconfig "wlan0" hw ether "00:11:22:33:44:55"
#ifconfig "wlan" up

have also tried:
#/etc/init.d/networking stop

# 3X ifconfig....

#/etc/init.d/networking start

and I tried this too: 

#ifconfig "wlan0" down
#macchanger "wlan0"
#ifconfig "wlan0" up

What's wrong? A little help would be very appreciated :)

!! EDIT !!

I read on [http://www.macgeekery.com/gspot/2006-04/mac_address_spoofing](http://www.macgeekery.com/gspot/2006-04/mac_address_spoofing) that:

"you wont see the change in the terminal or the network utility. but it lets me on to the network once i tried it&#8230;"

Can this be true? and if so... why can the change of the wired-MAC be seen in the terminal?

---

