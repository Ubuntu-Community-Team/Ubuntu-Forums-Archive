---
title: "Weird looking screensaver on i915"
date: 2006-10-01
forum: Multimedia &amp; Video
---

### Post by terrax on 2006-10-01
Hello ubuntuforum

I got a problem with the dri / openlgide driver I think? I have a i915 (i810 driver) chipset on a dell 630m

I just made a fresh installation with dapper, and den made i update with every repos enabled.

The weird thing is, that I can only see the half of the opengl screensavers?

I can see there has been posted some old topics about the problems, but non of them really come with a solution.

Anybody know a solution?

BTW. I tried once to install aiglx with compiz. Then all the screensavers etc. worked. But i got some other issue, like direct rendering crashing when running glxgears. So I really like to keep the original kubuntu packages, but using some sort of a fix to the problem?

Could I install latest dri drivers from Xorg?

---

### Post by tamagotono on 2006-10-01
I too am having the same problem.  I am running with an intel 865 chipset using the i810 video driver.  I am currently experimenting with some ideas, if I find anything that helps I'll be sure to post it.

---

### Post by terrax on 2006-10-17
If you install the newest driver from:
deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) dapper main aiglx

Your screensavers will work. But you will get some other bugs described here:

[https://launchpad.net/bugs/61306](https://launchpad.net/bugs/61306)

But in the newest cvs, it should have been fixed.
Now we just have someone to make a package for dapper xorg 7,0.

---

