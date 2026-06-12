---
title: "Remote Controls"
date: 2008-09-12
forum: Mythbuntu
---

### Post by mark467 on 2008-09-12
I love Mythbuntu and have everything working well but I can not get a remote to work. I have an ati usb rf remote that I have to the point of being seen and can even get responses from irw but it does nothing in myth. I also bought a Pinnacle MCE remote and cant get anywhere with it yet. I would love to get at least one working remote if anyone has any time to help with these issues I would really appreciate it. Having a cool media center and having to walk over to the keyboard to pause, change channels and such like an old tv is kinda lame. I have spent so many hours working on it I am almost fed up (almost). At this point I am willing to go out and buy another remote if someone can tell me of one that works right out of the box (or almost). If you suggest one please give brand and model and what it took to get it working. If you want to help get one oof mine working tell me what you need to know.

---

### Post by newlinux on 2008-09-12
So you have IRW output? You shouldn't need to buy a new remote. You must be very close. How did you configure your lircrc file (did you use mythbuntu control center)? Can you post the contents of the ~/.mythtv/lircrc file for the user you run mythfrontend from? also if just to get ahead of the curve (although if irw is working then these files are probably setup correctly) but you could go ahead and post /etc/lirc/lirc.conf and /etc/lircd/hardware.conf in case someone spots a problem in one of those. What is the exact model of your ati USB rf remote?

I'm sure there are plenty of people here who would like to help. What things have you tried? Have you confirmed lircd is running? I hope to be able to help you.

---

### Post by bmwman on 2008-09-12
I believe the Pinnacle MCE remote should work right out the box. You need to select Media center remotes (Phillips and newer) from the Mythbuntu Configuration and it should at least give you the basic buttons.

---

### Post by mark467 on 2008-09-16
Ok some progress. I can now get the ATI remote to work in myth front end. However there is long delay(sometimes 30 sec) after buttons are pressed and it stores the keypresses then does a bunch at once.

The pinnacle remote does not work when set up vi mcc using media center new or old. It is this model :

[http://www.pinnaclesys.com/PublicSite/us/Products/Consumer+Products/PCTV+Tuners/PCTV+Vista+Companion/Pinnacle+Remote+Kit+for+Windows+Media+Center+Documents/Technical+Specifications/Technical+Specifications+Remote+Kit.htm](http://www.pinnaclesys.com/PublicSite/us/Products/Consumer+Products/PCTV+Tuners/PCTV+Vista+Companion/Pinnacle+Remote+Kit+for+Windows+Media+Center+Documents/Technical+Specifications/Technical+Specifications+Remote+Kit.htm)

---

### Post by uopjohnson on 2008-09-18
The queued button presses is *probably* not a remote issue.  This seems to be some other bug that a few people are experiencing on many different systems.

---

