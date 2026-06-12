---
title: "openGL draw &amp; fullscreen errors on intel GMA"
date: 2008-10-05
forum: Multimedia Software
---

### Post by Dthdealer on 2008-10-05
Whenever I run a windowed-openGL application, the program will flicker when I click my mouse. On full screen openGL applications, most of them have redraw errors when the gnome toolbars redraw (eg time changing every minute).
Another problem linked to this is that fullscreen openGL applications stay windowed if they are set at my resolution (1280*1024) but not if I set them lower, and that they will become windowed every now and then before returning to full-screen.  On some screen-savers, z-drawing errors occur where polygons furthest away from the camera draw above the closer ones.

I have reason to believe this is due to my use of Intel GMA. Unfortunately my case is tiny, and the graphics cards I have are for different slots than what my computer has.
Is there a way around these problems without installing new hardware? They don't occur on my XP partition on openGL applications.

I've also heard rumours the intel GMA support will be fixed in 8.10. Is this true?

Ubuntu 8.04 current updates (Monday, October 06 2008 GMT+10) on a HP compaq desktop computer running intel GMA @ 1280*1024 60hz.

---

### Post by nikarul on 2008-10-10
I have the same problem with my Intel 945 integrated graphics on my HP laptop.  I was running Kubuntu 8.04.1 and upgraded to 8.10 beta in hopes that it would fix it, but it still has the same problems.  Its particularly a problem for me because the OpenGL app I'm working on tries to draw a regular menu over the OpenGL window in certain circumstances.  This works fine on my desktop with the Nvidia binary drivers, but the menu disappears behind the OpenGL window on my laptop.

BTW, I had some problems getting X running on the 8.10 beta that required poking around with kernel modules and such, so I don't recommend it for the faint of heart.

  -Michael

---

