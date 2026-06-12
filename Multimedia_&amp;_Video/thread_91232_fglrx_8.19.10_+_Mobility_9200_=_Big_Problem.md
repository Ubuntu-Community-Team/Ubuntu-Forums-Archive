---
title: "fglrx 8.19.10 + Mobility 9200 = Big Problem?"
date: 2005-11-16
forum: Multimedia &amp; Video
---

### Post by alump on 2005-11-16
I can't get the newest Ati driver (8.19.10) to work with my lapptop's (HP Compaq nx7010) Ati Mobility Radeon 9200. The older and default Breezy driver (8.16.20) works fine. Working suspend and PowerPlay would be nice features to have with lapptop.

Installation went ok... and I have tried several different xorg.confs. But always the result I get is like this: [http://alump.iki.fi/ati1small.jpg]("http://alump.iki.fi/ati1small.jpg") Xorg's log doesn't have anything suspicious.

Anyone with similar problem? Is this just a bug in this version?

Edit: Problem seems to be non working EDID. Manually added ModeLines don't solve the issue :(

---

### Post by linuxNewb01 on 2005-11-17
I had the same proplem with v. 8.19.10 on a Compaq x1000.  I also have a friend with the HP version of the same laptop (not sure of the model number, they both have the Ati Mobility Radeon 9200 card though), who had the same problem as well running gentoo.  Right now we're both back on v. 8.16.20.  With 8.16.20 my card is recognized as a Ati Mobility Radeon 9000, not a 9200, and my resolution would not go above 1280x1024.  My friend went in and added 1680x1050 by editing a file or two, (i tried to follow it, i got lost) and now my resolution is fine in X if i skip the login screen, but goes back to 1280x1024 permenantly if i view the login screen. Any idea's on how to fix this would be great.  Did i somehow instal the driver wrong?

---

### Post by alump on 2005-11-17
When I copied the correct(?) modeline that older driver got via EDID...
```
Modeline       "1680x1050"  121.00  1680 1704 1792 1872  1050 1051 1054 1065 +CSync
```
...I almoust got it to work  (the output was  [http://alump.iki.fi/fglrxsucks.jpg]("http://alump.iki.fi/fglrxsucks.jpg"))
Xorg.conf shows that "+CSync" part didn't get loaded up. :(

---

### Post by SuperBOB on 2006-02-18
Because you guys have used pictures which are not linked anymore, its hard for me to definitely say I have the same problem

But if your pictures showed screen corruption, then the chances are we are all suffering from the same bug.

I have an NX 7010 laptop with 9200 mobility I have posted all my logs in a seperate topic already.  If either of you fix this problem I would be grateful of an email to [email]superbob@ps-aux.org[/email]
Actually I suppose you have given me a solution, revert to the older ati driver... ill give that a whirl

---

### Post by SuperBOB on 2006-02-18
Ahh there we go,
DRI is working without any display problems :)

It has to be a bug in the new FGLRX?

---

### Post by kf_man on 2006-02-23
It's probably not a but at all.  This problem has been going on for quite some time on the windows side of things.  Any Catalyst driver newer than 5.6 will cause a screen corruption that I can imagine is very similar to this one.  There is a rumor that the drivers changed drastically and support for our card was broken.  I know that in my case it was only when using the internal laptop display, any external display worked fine.  There may be a solution, but I seriously doubt it.

---

### Post by alump on 2006-02-28
Yes. I can't get my mobility 9200 work with the newest drivers at all - with DRI or without. And it might really be that problem is only with laptop's own display. It's amazing that Ati's Linux support can get even worse than it was before ;) 

Well... open source radeon driver works ok on desktop usage. I can live with that.

---

