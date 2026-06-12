---
title: "Gnome seems to crash constantly"
date: 2011-12-04
forum: Multimedia Software
---

### Post by osarusan on 2011-12-04
I'm using 11.10 x64, running gnome shell, 4 gigs of RAM, and an ATI HD 4770 using the fgrlx-updates driver from the Ubuntu repos. Fresh install from yesterday morning.

Seemingly at random, without any obvious reason, my gnome keeps crashing. The window borders disappear, the screen gets garbled, and then a second or two later, it usually reloads without any problems. Sometimes this happens when browsing with nautilus, sometimes it happens when moving a window, sometimes it happens simply when I move the mouse and nothing is open at all. Most of the time gnome successfully restarts so it's little more than an oddity and a slight waste of time, but occasionally it crashes and fails to restart, and I have to reboot.

Sorry that it's a vague description, but does anyone have any idea as to what might be causing this? It is rather frustrating.

---

### Post by wolfen69 on 2011-12-04
I would start by doing MemTest and go from there.

---

### Post by alphacrucis2 on 2011-12-04
Try the latest version of the catalyst driver from AMD. ie Cat 11.11.

---

### Post by osarusan on 2011-12-05
Okay, I have done both of those things now. Memtest ran fine, came up with no errors. And I just installed the AMD drivers from the website. After rebooting, about 30 seconds in the crashing happened again. Again it recovered itself, but it doesn't look like either of those fixed the problem.

I'm fairly convinced this has to be a drivers or a compiz problem. I don't have any troubles like this using the No Effects version of Gnome. Are there some settings in ccsm that I need to change in order to prevent this from happening?

---

### Post by vanlong441 on 2011-12-05
> **osarusan said:**
> 
I'm fairly convinced this has to be a drivers or a compiz problem.

+ gnome-shell uses mutter as desktop manager, not compiz.

> The window borders disappear, the screen gets garbled, and then a second or two later

+ the latest fglrx only works for NVIDIA card, not ATI card. You should be fine using the open source driver.

+ those symptoms might be from bad driver, gnome-shell theme, or extensions. But mostly I think they are from the driver.

---

### Post by osarusan on 2011-12-05
> + the latest fglrx only works for NVIDIA card, not ATI card. You should be fine using the open source driver.
This doesn't make sense to me, as fglrx is the ATI driver, not the nvidia one. I would be happy using the open source driver except that it is barely supported on my bard, the HD 4770, and I wouldn't be able to play Minecraft or do pretty much anything else that uses 3D. So I've go to stick with fglrx for now.

I've heard that Gnome Shell uses Mutter and not Compiz, yet compiz is installed? I guess that would be for Unity, but there's no chance of it interfering with Gnome Shell then, is there?

I'm using the default gnome shell theme and extensions, so unless there are problems with the default ones that shouldn't be the cause of the problem either.

How this can be considered a release version is beyond me, considering the number of crashes I get when not even doing anything.

---

