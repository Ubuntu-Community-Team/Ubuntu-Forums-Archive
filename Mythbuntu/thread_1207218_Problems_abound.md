---
title: "Problems abound"
date: 2009-07-07
forum: Mythbuntu
---

### Post by Madman6510 on 2009-07-07
I installed Mythbuntu on an old computer so I could watch my videos from the network. However I can't figure out how to get the network share that the videos are on to automatically mount so it can be read by MythTV on startup. (I tried editing /etc/fstab, but it's not working)

Also, whenever I start the machine, xfce loads, MythTV starts to load, and then I'm asked for a keyring password, then it asks me for my wireless network key. Is there a way to just allow it to automatically connect without it having to ask me every time?

Also, my TV has a native resolution of 1360x768. I changed the resolution to that, but whenever I restart the computer the resolution changes back to 1280x1024.

Thanks in advance.

---

### Post by Jayy on 2009-07-08
To make it not ask for your keyring password on boot, do the following:
right-click on the network thing next to the time, and click "Edit Connections..."
then, find your network, and press "edit".
at the bottom check "Available to all users".

Hope it helps!

---

