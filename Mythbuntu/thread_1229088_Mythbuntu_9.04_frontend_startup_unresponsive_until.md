---
title: "Mythbuntu 9.04 frontend startup unresponsive until lots of keys pressed"
date: 2009-08-01
forum: Mythbuntu
---

### Post by bd1 on 2009-08-01
Using Mythbuntu 9.04 on power up when the frontend has started it doesn't respond until a key has been pressed many times. It doesn't matter how long the PC has been left since power up - tried half an hour or so. If I quit the frontend and restart it, it is fine.

Any suggestions? The same hardware worked fine under 8.04. I have just re-installed after installing a new hard disk.

---

### Post by SiHa on 2009-08-02
Not wanting to sound glib, but, maybe go back to 8.04 if it works fine?

Me, I'm sticking with 8.04 until someone gives me a damn good reason to upgrade. This forum is littered with so many variations on "it was working until I patched it / updated it / upgraded to 8.10, 9.04....".

Now, I know that I'm probably going to get flamed at this point, and bd1, this one isn't aimed at you, but I just have to say this to everyone out there. If you have a working setup, **leave it alone**. Why risk screwing it up, because Ubuntu is telling you that there are 3,543 updates available - would you like to install them? 

If it ain't broke...

Climbing down off my high horse now.

---

### Post by bd1 on 2009-08-03
I think I would have to agree. Although it is faster to boot, the remote now doesn't work properly (see lanuchpad [https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/305321](https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/305321)) and now this start-up problem. I re-installed because I brought a new much larger hard disk. Fortunately, with 9.04 I installed using lwn, a separate boot partition and separate media partition and I have an image of the 8.04 partition, so I should be able to re-create the 8.04 set-up and then modify it to work with my current partition set-up.

---

### Post by bd1 on 2009-08-17
I've finally worked out what is happening. The Update Manager is running in the background and although it is not visible it is taking the keypresses. I think I was just getting lucky eventually and managing to quit it. As I do most of my testing via VNC I wasn't able to do Alt-TAB to bring it into the foreground. I don't know exactly how it was getting started, but I suspect I managed to stupidly put in it in a save session. Now it isn't running everything is fine.

---

