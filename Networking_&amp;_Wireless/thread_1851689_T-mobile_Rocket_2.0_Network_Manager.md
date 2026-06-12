---
title: "T-mobile Rocket 2.0 Network Manager"
date: 2011-09-28
forum: Networking &amp; Wireless
---

### Post by exsysprog on 2011-09-28
I'm running a rocket 2.0 on 11.04 and I'm close but not quite there.

the rocket is an Onda MF691

I've accomplished the modeswitch stuff although I have to issue a usb_modeswitch command manually even though I've set up the configuration files. Network manager recognizes the rocket and connects with it.  When I right click the broadband connection icon and check the connection properties I see that I have an assigned IP address that appears appropriate for the tmobile network but the DNS addresses are a little odd.  The primary DNS address is listed as my machines IP address.  The secondary and ternary addresses are appropriate for the network I'm on. I am unable to ping any of the dns addresses.  The only gateway listed in the routing table for the usb interface in question is 0.0.0.0.  Needless to say the "connected" rocket 2.0 isn't doing much talking on the network.

The mobilee broadband is my only network connection so I'm having to switch back and forth to windows to get to the net.  Pain ...

Thanks in advance for any help

---

### Post by exsysprog on 2011-10-19
As written elsewhere such as:

[http://www.fogel.ca/2010/10/05/t-mobile-webconnect-rocket-2-0-on-debianubuntu/](http://www.fogel.ca/2010/10/05/t-mobile-webconnect-rocket-2-0-on-debianubuntu/)


and

[http://ubuntuforums.org/showthread.php?t=1585498&highlight=mobile+broadband+tt-mobile](http://ubuntuforums.org/showthread.php?t=1585498&highlight=mobile+broadband+tt-mobile)

One must use a dialer and not the stock network manager to get these things working.  wvdial did the trick for me.

---

