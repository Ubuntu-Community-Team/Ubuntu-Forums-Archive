---
title: "No luck with GTX280 and getting xorg to work proper"
date: 2008-07-18
forum: Multimedia Software
---

### Post by JLogan on 2008-07-18
I recently got a GTX280 and have been having a blast playing newer games on my vista system.

I started a project recently and want to set up a website. However, when I tried to get apache and php/mysql working on vista, I ran into a mess of problems. So I thought I'd come back to linux and do my web-dev here :)

But I'm stuck at 800x600 and cant get the nvidia drivers to work.

I've tried installing the drivers using the latest from nvidia, tried using envyng, and even the repositories from ubuntu (which I believe are out of date for my card anyways)

Nothing identifies the GTX, or my monitor (gateway FHD2400 native rez 1920x1200) When I boot I end up getting the "low graphics mode" error box, which I can use to achieve 1920x1200 when I hit the test button - but after I hit ok it dumps me back to 800x600

I'm using the latest ubuntu release 8.04 and I update it straight off the bat. I really dont know what else to do! :confused:

Please help!
-J

---

### Post by JLogan on 2008-07-19
still no luck... envy doesn't even identify the card, and when I run nvidia-settings it says no X server is using the driver...

the latest drivers support the GTX 280 so it should be able to be detected yes? Am I just out of luck on this one, or is there a workaround I haven't found yet?

Anyone?

---

### Post by xc3RnbFO8P on 2008-07-19
Try:
atl+f2
> gksudo displayconfig-gtk
Choose Generic
and resolution that your monitor supports

---

