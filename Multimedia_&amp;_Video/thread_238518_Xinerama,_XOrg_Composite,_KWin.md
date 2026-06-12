---
title: "Xinerama, XOrg Composite, KWin"
date: 2006-08-17
forum: Multimedia &amp; Video
---

### Post by KlausU on 2006-08-17
Hi,

(not sure this is the right forum here but i suppose this is a low-level problem)
I am trying to enhance my dual monitor xinerama setup with KWins transparency. Doing so I get the following problems when KDE is started:

- The primary screen is black, except the mouse cursor, the cursor changes its shape when hover buttons etc.
- The secondary screen shows its background image (had no window open there), but the context menu and an opened select-box flickers very strong. The shadows do not flicker.


I would guess there is something wrong with the "zbuffer" or whatever xorg/kwin? uses to determine the visibility of elements.

- The login screen seems to work correct -> I thought, maybe no problem with X...
- Transparency works perfectly with only one screen -> I thought X problem...
- I can not find any problem in the xorg.0.log, here it is:
[http://www.ubuntuusers.de/paste/2926/](http://www.ubuntuusers.de/paste/2926/)

and my xorg.conf [http://www.ubuntuusers.de/paste/2927/](http://www.ubuntuusers.de/paste/2927/)

Any ideas what the problem is and maybe how to solve it?
Will the chance for success be better in 6.10?

I have tried xgl/compiz before. Basically it does work (and looks WOW) and seems performant but I can't get it configured and it seems unstable to me (it freezed, ARGH!)

Best Regards
P.S. Is there an official ubuntu nopaste service?

---

### Post by KlausU on 2006-08-26
Uhm sorry for pushing, no ideas?

---

