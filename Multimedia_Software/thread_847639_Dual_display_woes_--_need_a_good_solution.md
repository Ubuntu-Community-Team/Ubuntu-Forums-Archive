---
title: "Dual display woes -- need a good solution"
date: 2008-07-02
forum: Multimedia Software
---

### Post by jimmy the saint on 2008-07-02
I have an Nvidia 7900gs powering an old 15 inch sharp lcd and a newer 19 inch viewsonic.  The sharp has a native res of 1024x768 and connects via VGA, while the viewsonic has a native resolution of 1280x1024 and connects VIA DVI. 

So far I tried TwinView, Dual X servers and Xinerama.  None of the solutions were very good.  

TwinView
    Pros:  One unified desktop across both screens.  Ability to separate desktop cube into two separate ones to eliminate the crappy look that two mismatched monitors has.  ability to move windows across screens.  Works with Compiz.
    Cons:  Since it creates one huge display, mismatched monitors leave dead space.  This means that things can be present that you can't see (especially when firefox downloads something)... a real pain.  The dead space is the real killer here.

Xinerama
     Pros:  Does most of what twinview does.
     Cons:  Unable to use Compiz effects.  Deal Killer in my opinion.

Seperate X servers
     Pros:  Two seperate environments that can be independently configured.
     Cons:  Inability to move windows between screens.  I found it to be pretty buggy.  Inability to set Larger monitor as the primary monitor (for login, taskbars etc.).  I tweaked xorg.conf to get this to work a little, but it caused more problems than it solved.  Also, the need to employ several workarounds to resolve severe performance issues with menus and the like.  

What I need is simple (I thought).  I like TwinView, but the dead space is a reall killer.  One solution, for me at least. would be to rotate the sharp since it's width is the same as the viewsonics height.  this would eliminate dead space altogether, but I haven't found a way to do that.  If there was a way to eliminate the bugs in present with dual x servers (for instance, try to open compiz fusion icon on the second monitor or add panel applets!!) I would use that.

I appologize for the long post, but I have been working for two days now to get a good display setup and have been unsuccessful.  If anyone has any suggestions I would appreciate it.  I know of the workaround to speed up menus in dual x, but it doesn't fix the other bugs.

Thanks
JTS

---

### Post by jimmy the saint on 2008-07-03
I am playing around with xfce and it seems to do a much better job of paying attention to dead zones than gnome.  I guess whatever they are using to manage their desktop is a little better at it than nautilus.

---

