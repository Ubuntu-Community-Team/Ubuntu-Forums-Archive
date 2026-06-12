---
title: "Odd problem with NVidia's drivers"
date: 2009-10-08
forum: Multimedia Software
---

### Post by Neoranger on 2009-10-08
Hello.

A couple of years ago I bought a small box to use as a download center (AMD LE1620, ECS GeForce 7050/610i). I eventually abandoned the idea and left the computer entirely unused for the most time. The last couple of times I used it, I noticed that it would just freeze after a while and require a reset (I was running an older version of Xubuntu).

I had assumed it was the hard drive, which was due to fail, so now that I decided to go back to that box, I swapped the HDD, installed Kubuntu and then the NVidia drivers found in the Hardware Manager. As it turned out, the system would still freeze. I was afraid it was hardware malfunction, but a little googling properly encouraged me to get rid of the restricted drivers. So I went and installed the latest drivers from NVidia's site (185.xx).

That's where it gets weird, though. When I log in everything looks fine (picture's sharp, sound works properly as opposed to before), but a few seconds in, the screen flickers and the system throws me into low-res, on some corner of the screen, where I have no access to the GUI. I've reinstalled a million times, but the result is the same. Only if I get rid of xorg.conf can I work the damn thing, but of course that pretty much gets rid of res over 800x600. I tried looking into the file, I didn't see anything out of the ordinary. Every time I let nvidia recreate (either via reinstallation or nvidia-xconfig), the same thing happens.

I generally like to search around for solutions, but this particular one is a bit... peculiar. Anybody has any idea what's going on?

---

