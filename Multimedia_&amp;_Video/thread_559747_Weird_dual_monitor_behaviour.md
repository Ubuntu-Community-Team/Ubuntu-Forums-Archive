---
title: "Weird dual monitor behaviour?"
date: 2007-09-25
forum: Multimedia &amp; Video
---

### Post by Karahana on 2007-09-25
I'm not really new to Ubuntu, just haven't used it in a while. :) I finally got fed up with WIndoze (again) and decided to do a dual boot. The only problem I've stumbled upon so far is weird dual monitor behavior. 

Ok, so I installed xubuntu and NVIDIA propietary drivers, set xorg.conf to "nvidia" and X starts OK. My problem is not being able to change the resolution of my other (right) display to anything higher than 640x480. I'm guessing the drivers installed OK since I didn't get any lifesigns from the other monitor before installing them. Editing the resoultion in xorg doesn't seem to do anything!  Using GeForce MX 640. Any ideas?

Cheers! .

---

### Post by veloce on 2007-09-26
Try setting the horizontal synch and vertical refresh for your monitor.  The dual monitors seems to prevent the system finding the monitor specs.

Veloce.

---

### Post by Karahana on 2007-09-27
Donw... It took some major xorg settings! :)  Tnx!

---

