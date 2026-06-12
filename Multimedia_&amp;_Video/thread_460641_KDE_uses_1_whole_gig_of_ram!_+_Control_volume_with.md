---
title: "KDE uses 1 whole gig of ram?! + Control volume with multimedia keyboard"
date: 2007-05-31
forum: Multimedia &amp; Video
---

### Post by moljac024 on 2007-05-31
I am using Ubuntu Feisty Fawn (default DE GNOME) but i installed kde-core and some apps (amarok,k3b,kget,ktorrent...)

Everything works fine but i didn't know KDE is such a resource hog - it is using approx. 800 MB of my RAM !! Gnome uses about 200. Anyway i have a multiemedia keyboard with volume up and down buttons and how can i set them to control my volume in KDE ?

EDIT : Now it's using all of my RAM memory (1 gig) and half of that is X, yes X is using 500 megs of ram - what gives ??

---

### Post by tgm4883 on 2007-05-31
Linux uses RAM differently than Windows.  It doesn't unload things from RAM that aren't being used anymore unless it needs that space.

---

### Post by moljac024 on 2007-06-01
But why is Xorg (/etc/X11/X) using more than 500 megs of ram ?
Can someone explain this ?

---

### Post by bom28 on 2007-06-01
I don't think there much difference in memory usage between kde and gnome, but of course it depends on what programs are running. How do you measure memory usage ?

About the X memory usage, X use a client-server model, where the client and server can be on different machine. So, for efficiency, clients can store pixmaps on the X server, that explains why the X process can use a lot of memory : a lot of it actually belongs to clients and will be freed when the clients quits.
Do you use 3D effects ? I haven't checked, but I'd say they probably use a lot of X memory.

---

