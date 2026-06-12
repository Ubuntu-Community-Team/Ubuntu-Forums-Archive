---
title: "Three comuputers on LAN, only 2 get WAN"
date: 2009-03-24
forum: Networking &amp; Wireless
---

### Post by Bucky Ball on 2009-03-24
Hi all,

This problem has changed enough to warrant opening a new, clearer thread I think. The previous one can be found here:

[http://ubuntuforums.org/showthread.php?t=1103695](http://ubuntuforums.org/showthread.php?t=1103695)

* I have two D-Link routers, DI-704P with a print server and no wireless, DI-524 with wireless and no print server. Two computers are plugged via ethernet cable into the 704P along with the printer into the print server. This router has it's DHCP server enabled and is serving IP addresses to the two machines.

The wireless router has the DHCP server disabled and is plugged into the 704P via a regular ethernet port, not the WAN port. The laptop connects to this access point and is served an IP from the 704P and can access the printer. Sweet. This has been working fine for over a year. But ... After numerous other problems over the last few days, we arrive at my ...

* Current problem. All three machines are visible on the LAN, but only two (the wired ones) are accessing the WAN. The laptop (wireless and only machine going through the wireless router) is getting served an IP from the 704P and is visible on the WAN, but cannot access the WAN. How can I access WAN with the laptop? Hard to pick the problem when everything seems to be working okay (picks up correct ap, served address, network icon fine). The only signs it gives of having any kind of problem is when I try to do anything on the LAN. Oh, and it keeps printing a blank page every 2 or 3 minutes from when I was trying to fix these problems last night. The instruction seems to have stuck. How do I kill that apart from disconnecting from the network (the problem is still there even then, of course).

I have tested to make sure the IP is coming from the 704P and not from the wireless access point, the DI-524. 704P it is.

I really hope someone has an explanation or a fix 'cos this is starting to send me nutty (er)! :)

---

### Post by Bucky Ball on 2009-03-24
Should the IP address of the second router be set to static and a number outside the range of the DHCP server? I don't remember altering this setting but if both routers are set to 192.168.0.1, that can't be good.

I am obviously missing something fairly straighforward perhaps?

---

