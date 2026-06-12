---
title: "Video Driver Problem? World of Warcraft"
date: 2008-09-25
forum: Multimedia Software
---

### Post by europa on 2008-09-25
[IMG]http://img220.imageshack.us/img220/1182/dsc00022bc3.jpg[/IMG]

Any advice?  Whenever I open up world of warcraft, my screen has double image and is scrambled enough that i can't tell wtf is going on.

long explanation:

World of Warcraft WAS working. However, when I enabled desktop effects, I experienced a flicking screen issue ([http://ubuntuforums.org/showthread.php?t=769983](http://ubuntuforums.org/showthread.php?t=769983) ).

I tried to fix this issue by downloading the newest drivers from ATI's site. (i originally installed with EnvyNG).

After ATI drivers were installed, i got a 'ubuntu is running in low graphics mode' popup which prompted me to select my driver. Choosing fglrx didn't work for me.

I tried re-running EnvyNG but no luck. I finally got it fixed with:

sudo dpkg-reconfigure xserver-xorg

but then no desktop effects worked at all, and warcraft would not run.  I tried EnvyNG once more and now desktop effects work again, but the double image occurs (as seen in the screenshot). Only way to get rid of it is restarting x.

I've tried a few online tutorials trying to get it to work but everything ends up with 'low graphics mode'.  Im not sure what to do next.

Any help would be appreciated. 

Thanks,

Jack

---

### Post by harpazo on 2008-12-14
I'm having exactly the same problem.  Anyone know how to fix this.  After this happens, I have to restart my computer.  Everything is set to opengl but this always happens. I can run Enemy Territory no problem.

Help would be appreciated.

Harpazo

---

### Post by europa on 2008-12-14
This is an ATI driver problem.  You can either roll back to an older version of the driver, or upgrade to Ubuntu 8.10 :P

After installing 8.10 I dont have the problem anymore.

---

