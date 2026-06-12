---
title: "So I installed Ubuntu Server... apparently not wireless-tools. (How to get on wifi)"
date: 2011-04-12
forum: Networking &amp; Wireless
---

### Post by sirspazzolot on 2011-04-12
On a laptop with some Atheros card, don't remember exactly which one. Wireless works OTB in Ubuntu 11.04, but there isn't wireless-tools installed when I boot into the server (10.10 if you were wondering.) I downloaded a deb off somewhere on the interwebs, ran dpkg on it, etc, and it said that I need to install libiw30 first and I REALLY REALLY don't wanna spend hours searching for and installing dependencies and I'll inevitably wind up in dependency hell (I always do) so if anyone knows of anything to do, that would be awesome.

I haven't installed or done anything so I wouldn't mind reinstalling if that would install wireless-tools for me. I would ask how to connect to wifi through terminal now so I can know how once I get wireless-tools installed, but something tells me if I ask that then nobody will give my wireless-tools issue any attention.

---

### Post by sanguinoso on 2011-04-12
You can't just plug it in with an ethernet cable? Otherwise if you have a Desktop iso you may be able to set up a local repository with the Desktop iso and install all the dependencies from there.

---

