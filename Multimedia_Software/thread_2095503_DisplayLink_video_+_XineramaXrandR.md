---
title: "DisplayLink video + Xinerama/XrandR"
date: 2012-12-17
forum: Multimedia Software
---

### Post by openit on 2012-12-17
Hi Guys,

I have a laptop which uses intel graphics:
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)

and also a displaylink usb video adaptor:
Bus 002 Device 005: ID 17e9:0360 DisplayLink

I have blacklisted the udl driver and I am using the udlfb module.  UDL caused kernel panicks

I have the intel card driving 2 monitors@1920x1080 and I'd like add a third with the displaylink.  I've tried numerous combinations inside of Xorg but If I have the displaylink enabled, the intel doesn't work and vice versa.  

The best solution I have had so far is to create a second instance of X for the displaylink card and use x2x to forward the mouse and keyboard which I am currently using.

Is this simply a limitation of X not allowing  screens to span across different graphics adaptors or am I meant to be using Xinerama.  I have tried enabling Xinerama in xorg.conf, setting up server layout and setting up a virtual screen size to accommodate this but have had no luck

Can somebody please point me in the right direction or let me know if this is simply not possible?

Thanks in advance

---

