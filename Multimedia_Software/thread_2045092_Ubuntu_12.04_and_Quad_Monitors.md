---
title: "Ubuntu 12.04 and Quad Monitors?"
date: 2012-08-20
forum: Multimedia Software
---

### Post by mtclare on 2012-08-20
Hello, I am very interested in getting a quad monitor setup using Ubuntu 12.04.  Is this possible with Unity?  Will Nvidia X Server automatically detect and configure all 4 monitors making things easy?

I have dug up some bits and pieces of information here and there but don't know what to make of everything.

---

### Post by Spice002 on 2012-08-21
It will not auto-configure everything (sadly). To get it all set up, go to the dash, Type "NVIDIA" and open the NVIDIA X Server Settings. Go to "X Server Display Configuration" and press "Detect Displays." Next,  go through each screen and set then to what you want (TwinView if you want something like what Windows does, Separate X screen if you want them each to be a separate desktop view (Each monitor will have it's own Unity bar)) and where they are. After that press apply and make sure to press "Save to X Configuration File" or else you'll have to do the same thing all over again.
Someone may have a better guide that's much easier, but I hope this helps.

---

