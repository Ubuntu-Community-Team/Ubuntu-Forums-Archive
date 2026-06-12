---
title: "Network Manager ...gone?"
date: 2010-02-17
forum: Networking &amp; Wireless
---

### Post by overandunder on 2010-02-17
Hi All

Sorry for the long story but this is a mess. Long story short I replaced the standard Network Manager with 'Wicd' after a recommendation from this forum on my laptop.

I used this machine for months via wireless at home and it ran perfectly like this..... until today.

I had to take my laptop into work where there is a wired network which is auto dhcp - connect and go type thing, which it did.  wicd had no problem locating the network and off I went.  At lunch time I powered down the laptop and returned to it later on, and then weird things started to happen.

The first was that a message popped up (which I have never come across before) that said 'Wicd requres access to your Computer network cards Password ='. This concerned me but I gave it my usual login password and it continued to load the Desktop.  Unfortunately no Wicd/ Network Manager type icon was present on the top (panel) line. I tried to connect to the Net - nothing. 

I then tried to load 'Wicd' from the Applications; Internet, section.  This flashed up a white box for a second which then disappeared.

After trying different things I discovered that if I said no to the 'network card' password request on boot I did get an icon show on the top line but it just shows 'searching' (never finding anything).  I then got a message saying that 'the Wicd daemon could not be accessed'.  I then went to command line (terminal) and tried 'Sudo wicd'.  This didn't seem to do anything either.

So long story short I'm totally stuck - anyone any ideas how I can repair Wicd or  get good 'ole Network Manager back?

Thanks

---

### Post by overandunder on 2010-02-18
No responses? Oh well.

I had to do a full re-install. 

Lesson learned....don't use Wicd for network management - way too flakey.

---

