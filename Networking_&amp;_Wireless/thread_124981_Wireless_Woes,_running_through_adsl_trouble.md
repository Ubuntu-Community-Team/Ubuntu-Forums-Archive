---
title: "Wireless Woes, running through adsl trouble"
date: 2006-02-02
forum: Networking &amp; Wireless
---

### Post by PumpkinSonnema on 2006-02-02
I'm trying to set up a wireless network all ubuntu here.  I didn't anticipate trouble this early.  Here's my setup:

comtrend ct-5621 adsl2+ router-->netgear MR814v2 wireless router-->computer

There will be more computers with wifi adapters once I get things figured out at this step.

My problem:  All was well until I tried going through the netgear to the adsl router.  Now browsing is incredibly slow and some sites don't load at all.  I set up the adsl router in bridge mode but that didn't seem to help anything.  I'm very new to Ubuntu and not at all familiar with what can or has to be done with network settings on the computer to get things flowing.  Is it just the router settings are off?  Or my computer network settings?

Any help is much appreciated,
Pumpkin

---

### Post by PumpkinSonnema on 2006-02-02
I finally got it.  For those with this particular problem in the future...
Make sure the adsl router and the wireless router are on the same network, i.e.  
192.168.0.x  (same first three number sets)  
Set the adsl router to do the DHCP stuff, set the wireless one not to.
Then, the weird thing, or maybe not so (I'm a network newbie)  you can't follow the directions that come with the wireless router.  You have to plug the wire from the adsl into one of the lan ports.  Putting it into the wan just won't work for some reason.  Then any wired computers can go into either the wireless router or the dsl.  

Sorry if some of this is not 100% accurate, as I don't know much on the subject, but this is the only thing I could get to work.

Pumpkin

---

