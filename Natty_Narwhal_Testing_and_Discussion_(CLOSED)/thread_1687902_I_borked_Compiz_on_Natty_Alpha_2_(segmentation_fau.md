---
title: "I borked Compiz on Natty Alpha 2 (segmentation fault)"
date: 2011-02-14
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by mazz0 on 2011-02-14
So I was messing about with the Compiz settings in Natty, I'd just turned on Wobbly Windows, which worked fine (well, like all changes to Compiz settings in the Natty alpha at the moment it crashed Compiz, but I have a desktop shortcut to restarting it so it was ok), then I enabled Ring Switcher, which again crashed Compiz, but now when I try to restart it I get a "Segmentation Fault (Core Dumped)".

I've tried disabling Ring Switcher, but that didn't help, something's gone very bad with Compiz!

Obviously I could just do a re-install, it's only a messing-about-with-the-natty-alpha machine, but I'd like to learn how to debug such problems.

I assume "core dumped" means it's made a big log somewhere? Anyone know where tha would be?

Also, anyone know if there a way t reset Compiz to default settings, or some othernway of fizzing it when it's borked?

---

### Post by ankspo71 on 2011-02-14
Hi,
This link talks about finding core dumps and such.
[https://answers.launchpad.net/ubuntu/+question/10616](https://answers.launchpad.net/ubuntu/+question/10616)

Since you are using a test build, I imagine apport (the crash reporter) is installed and enabled. So if that's true check /var/crash
I'm not testing as early as alpha 2 so I don't know if it is or not. I might join in on the fun later though.

Btw, 99% of the testing discussions for Natty are over in the Developement & Programming section of this forum. Ubuntu Forums > The Ubuntu Forum Community > Other Community Discussions > Development & Programming
[http://ubuntuforums.org/forumdisplay.php?f=394](http://ubuntuforums.org/forumdisplay.php?f=394)

Hope this helps.

---

### Post by mazz0 on 2011-02-14
Spanks dude!

Natty's looking lovely, by the way!

---

### Post by Iowan on 2011-02-14
Moved to Natty Narwhal Testing and Discussion

---

