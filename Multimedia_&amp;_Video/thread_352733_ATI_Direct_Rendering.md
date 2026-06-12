---
title: "ATI Direct Rendering"
date: 2007-02-03
forum: Multimedia &amp; Video
---

### Post by Andrew331 on 2007-02-03
I am having consistent problems with direct rendering.  I at first attempted to play World of Warcraft using Crossover by Codeweavers.  The installation proceeded smoothly, but I would either get a terminal error immediately upon starting the game or receive a message stating that 3d acceleration could not be initialized.  I eventually found out that this was due to DRI not being properly enabled and thus causing Windows games to have problems.

Andrew@Andrew - Laptop ~ $ glxinfo|grep direct
direct rendering: No

I messed around with all kinds of tutorials to the point that my GUI failed to load, and with no success.

I have run several native 3d linux games with very high framerates.

I have just cleanly installed Ubuntu 6.10, and done absolutely nothing to the system.

I am using a Dell Inspiron 8600c with an ATI Mobility Radeon 9600 Pro Turbo.

Any help would be appreciated.  I'm guessing there are a lot of threads about this so if you could even point me to one in which the case was resolved that would be great.  I am relatively new to linux.

---

