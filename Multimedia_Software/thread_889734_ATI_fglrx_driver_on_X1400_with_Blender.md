---
title: "ATI fglrx driver on X1400 with Blender"
date: 2008-08-14
forum: Multimedia Software
---

### Post by wastvedt on 2008-08-14
Hi.
     I'm having problems using the fglrx driver while running blender.  Here's some info:
 Dell Inspiron 6400 (e1505)
 ATI Mobility Radeon X1400 (R520)
 Ubuntu 8.04
 Blender 2.46

As you can see in the screenshot, I get dashed object lines, which is ok for a cube, but confusing in more complicated scenes.  Also, the lines between areas (in screenshot, the horizontal line between buttons and the 3d view) flash during most operations.  More annoying, selecting objects is often delayed.

Everything works fine with no graphics driver, but I do want to be able to use 3d acceleration.  Also, it seems that x1400 is not supported by the open source radeon driver.

Any ideas?  I did try to look for my issue in current threads.  I didn't find anything, but I might have missed it, sorry if this is a repeat.
Thanks

---

### Post by z0r on 2009-01-05
I had exactly that problem! My computer is the same as yours, too. I filed a bug about it: [Launchpad 220620]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/220620")

Actually my driver problems aren't all gone yet. It works better than before, but buttons still sometimes don't show. Also, the game engine often doesn't draw anything at all, and only quitting and restarting Blender makes it work again. With the open source radeon driver it works well but without GLSL (the radeon driver now supports the Mobility x1400).

Have you managed to fix your issues?
Alex

---

### Post by wastvedt on 2009-01-05
Hey!
I had almost forgotten about this. I think I'm probably still in the same boat. I haven't done much with the game engine, so I'm not sure there, but the dashed lines have disappeared with the newest fglrx release. I still get some flickering in the borders between window panes, and, yes, some disappearing buttons. I haven't tried Radeon recently, I guess I decided fglrx was good enough.
Trygve

---

### Post by Blue Beard on 2009-01-05
I had the similar display problems with an HD3450 & 780G.  

I switched to jaunty alpha2 hoping the latest drivers would clear the issues.  I ended up with xserver bootup failures until I manually configured xorg.conf.

Same problems until I installed the radeonhd 1.24 driver.  All the problems seemed to be resolved that you described earlier.  The performance is much better.

It has solved most of my issues; however: the manual config is tricky and I am not sure I would recommend it to others.

---

### Post by z0r on 2009-01-06
> **Blue Beard said:**
> I had the similar display problems with an HD3450 & 780G.  
...
Same problems until I installed the radeonhd 1.24 driver.

Thanks for the tip! But it looks like my card [isn't supported]("http://wiki.x.org/wiki/radeonhd#head-d0cfd39d1b149a43f0c1d862f21f4b3ddcb43ae2") for 3D acceleration yet. I'll keep an eye on that driver.

---

### Post by Shane Little on 2009-07-13
I also have an e1505 Dell with similar graphix probs. Where exactly do I go to get a good driver? I'm using the new Ubuntu 9.0.2 or something of that nature. I see fglr or something above but... Thanks for a nudge in the right direction.

Shane

---

### Post by z0r on 2009-07-14
> **Shane Little said:**
> I also have an e1505 Dell with similar graphix probs. Where exactly do I go to get a good driver? I'm using the new Ubuntu 9.0.2 or something of that nature. I see fglr or something above but... Thanks for a nudge in the right direction.

That depends on the version of Ubuntu you're using. In 9.04, the fglrx driver no longer supports the Radeon Mobility x1400. The open source radeon driver does, and it works quite well - no dashed lines, and it's fast and stable - but it doesn't support GLSL. So you can use it with Blender, but the 3D view will only show basic materials.

Alex

---

### Post by Shane Little on 2009-07-14
Thanks Alex. I have the 9.04 Ubuntu. I was multitasking at work yesterday and didn't have time to look for the exact version, lol. Appreciate the info.

Shane

---

