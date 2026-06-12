---
title: "HOWTO : getting ATI 3D accelleration working on HP Omnibook 6100"
date: 2006-09-28
forum: Multimedia &amp; Video
---

### Post by amgat on 2006-09-28
This has been a real nut to me for a long time now. I've tried alot of the howtos here - some complex, and some so easy that i had to re-install Kubuntu 6.06 over again [-( 

It was really simple actually - well, at least i got it working. This is what i did:

The first thing i noticed was the large resolution used. It was this large from default (1400x).

So i reconfigured x:
sudo dpkg-reconfigure xserver-xorg

Chose ATI as graphics card and the rest was default except resolution size. I set a max resolution at 1024x

I finished the configuring, and rebooted. Now everything works as it should.

As simple as that!

Hope this helps someone else with the same problem :p 

Have a good one.

---

