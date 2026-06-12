---
title: "Dual Monitor ubuntu 12.10 AMD Radeon 7500 HDMI"
date: 2013-02-02
forum: Multimedia Software
---

### Post by claven123 on 2013-02-02
I have a second monitor I would like to use.  I have two outputs on my AMD radeon 7500 series graphics card.  I have the one connected via a DVI output that is converted to svg.  The second output is HDMI and this is connected to the second monitor via a HDMI to DVI connection.

I have tried to use the HDMI output alone and it still doesn't detect the monitor.

Is there something I have to do to enable the HDMI output?  The system settings does not detect the monitor.  

I see post about AMD Catalyst Control Centre, do I need to install this?  I have read some post with reference to the HDMI, but most seem to be related to TV's and or laptops.  I have a Dell XPS 8500 desktop.  I'm using the proprietary drivers already.

Any advice?

I know a few years ago it took quite a bit of work to get the nvidia drivers to work, so I expect a bit of work.

D

---

### Post by Mark Phelps on 2013-02-03
I have an HD4290 and the documentation indicates that I can use the any of the three connectors, two at a time, with the following limitation: both DVI and HDMI can NOT be used simultaneously.

I don't know if your 7500 has the same limitation, but it might.

IF there is documentation that came with the card, you should check that to see if that is the case.

---

### Post by claven123 on 2013-02-03
That is all I have, one DVI and one HDMI.  So, I hope this is not the case.

Ironically, I inspected the connector on the monitor and it is an SVG output, the end of the cord is DVI.  So, it will never connect via the HDMI on the graphics card.


D

---

### Post by claven123 on 2013-02-08
So, I have the correct cables and I now can see mirror on both monitors!

I am unable to get dual monitors to work outside of mirror.  I get the error


required virtual size does not fit available size: requested[B].....  

[/B]I have attempted to choose almost every combination allowed and nothing works.  I have been reading and there are several solutions, but seem quite complicated.  I was hoping something simple would work and wondered if there were any solutions. Such as making changes to the xorg.conf file.  I heard you can change the size resolution and this would fix the issue, but I don't remember how to to do that.

Thanks,

D

---

