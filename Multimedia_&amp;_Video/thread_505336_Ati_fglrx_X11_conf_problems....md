---
title: "Ati fglrx X11 conf problems..."
date: 2007-07-20
forum: Multimedia &amp; Video
---

### Post by NachoMas on 2007-07-20
Hi all,
I have a weird problem with my X11 configuration that is driving me crazy. I have a radeon mobility 9660 integrated card in my laptop, which I use both at work and at home. At work I have a wide flat panel which I use at 1920x1200, while I home I have a smaller LCD that I can use at 1280x1024.

- First problem: at work, when I shutdown the system and I am at 1920x1200, the X server stops and then the screen goes blank and the computer freezes. I can imagine that it has to do with the console driver not being able to recover itself or change resolution? I really have no idea how to fix it. The only think I can do is change the X resolution to 1280x1024 before clicking on shutdown, and then it works without problem...

- Second problem: I have tried configuring my X11 so that I can use both resolutions depending on which screen I am using, but if I leave the higher res scren entry, my screen at home is unable to display anything and the resolution does not automatically adjust. The only option I have is having two screen entries in X11 and commenting in and out the relevant one whether I am at home or not. I am sure there has to be a better way of doing this!

I am including my xorg.conf file so that you get pinpoint my mistakes and help me out with it!
Thanks in advance!
/Nacho

---

