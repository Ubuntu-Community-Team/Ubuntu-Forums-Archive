---
title: "triple monitors"
date: 2007-08-10
forum: Multimedia &amp; Video
---

### Post by jlehn on 2007-08-10
I was wondering if anyone got triple monitors to work.  After much fussing around with config files i was able to get my three monitors to work.  I also enabled xinerama which seemed like a good idea at the start so that i could use and drag windows from monitor to the other.  This also allowed me to maximize windows for just that monitor.  anyway, my problem is that i can not seem to open certain things, like the terminal application, screen saver preferences, etc.  If anyone can give me any help i would appreciate it.  

I have two monitors on my agp card (nvidia 7800 gs, resolution of one monitor 1680x1050, resolution of second monitor 1280x1024)

card number two is a pci nvivida 5200 fx running one 1280x1024 screen.   


please help

---

### Post by broncavfan on 2007-08-11
I have 3 monitors working (fairly well if I do say so myself).  After trying for countless hours to get all 3 to play nicely together I finally gave up and made 1 a seperate X screen.  I have an NVidia 5200FX running twinview on 2 of them, and the third is plugged into an onboard NVidia 6100.  I'm liking how the seperate X screen allows me to be able to see those programs that I want to see all the time (i.e.-Gaim, Amarok, certain terminals, etc).  Unfortunately I spent so much time making it work that I don't remember exactly how I got everything working, but I can say that making the onboard 6100 load first in my BIOS seemed to help a lot.  I run compiz-fusion on the two monitors on the 5200FX and metacity on the seperate X screen.  I mean, with the cube effect enabled, that basically gives me 10 desktops to work with and that's more than enough full screen apps for me.  (4 cube sides * 2 monitors per cube side + 2 on the seperate X screen).  

To answer your question, though, I'm not exactly sure why certain applications won't open.  Might I suggest that you plug both of the monitors that have the 1280x1024 into the 5200FX and keep the AGP seperate (maybe even so much as a seperate X screen).  That way you'd have the better video card running games and more graphic-intensive apps.  I've noticed myself that even though my 5200FX is a better video card, running games when I have it setup in twinview slows down the graphics and overall fun of the games significantly.  It does, however, make compiz-fusion run like a charm.

I guess I'd just need more information about the problem and your overall computer use to be able to help more.  Are the applications opening but not displaying or what?  I'd be willing to change my xorg.conf back to xinerama in order to help, but you might want to reconsider how and why you want to have 3 monitors set up.  Somebody please tell me if I'm wrong for saying that, but it just doesn't seem like ubuntu is ready for more than 2 monitors just yet.  It's a setup straight out of Swordfish, except without a topless Halley Barry (I probably spelled that wrong).  Keep me updated with any progress, it's seems like there are a lot of people interested in getting 3 screens working who might just find this post useful.

---

