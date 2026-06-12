---
title: "No Compiz on Nouveau."
date: 2010-09-03
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by lancest on 2010-09-03
Just gave 10.10 a try. Still no Compiz on the default Nouveau vga driver.

 I really hope they get Compiz going on the Nouveau driver this time around (like Fedora 13 did). It would be much better for Plymouth and my tty's too. Anyone know?

---

### Post by rubenverweij on 2010-09-03
From the nouveau wiki:
> Any 3D functionality that might exist is still unsupported. Do not ask for instructions to try it. But you can read [GalliumHowto]("http://nouveau.freedesktop.org/wiki/GalliumHowto") in case you are brave enough. 
So I would say any 3D support is still experimental and probably won't be included in Ubuntu now. But you could always test it with these instructions of course.

---

### Post by cariboo on 2010-09-03
You need the gallium 3D package in order to get visual effects to work with the nouveau. the driver is available from [xorg-edgers]("https://launchpad.net/~xorg-edgers/+archive/ppa") ppa.

---

### Post by Nullack on 2010-09-03
The open source nvidia driver is slow and is missing many features in comparison to the closed source nvidia one. It's going to take allot of time for it to be comparable but progress is being made such as the latest dev kernel has Fermi chip generation mode setting support.

---

### Post by lancest on 2010-09-03
> **Nullack said:**
> The open source nvidia driver is slow and is missing many features in comparison to the closed source nvidia one. It's going to take allot of time for it to be comparable but progress is being made such as the latest dev kernel has Fermi chip generation mode setting support.

I'm sure this might be true for gaming.

 But when I used Fedora 13, Compiz it worked very well on the basic things that I wanted it for. Scaling etc. 
Seemed faster and cleaner looking than using proprietary Nvidia in fact.

  The occasional "titlebar not loading" issue was solved with FOSS vga driver and other nagging bugs as I mentioned.
 
I desire the FOSS drivers working well as soon as possible on Ubuntu because IMHO it's one of the best real ways to polish up the desktop. 

This ought to be top priority in my mind- instead of the Rhythmbox applet volume control type stuff for example.

---

### Post by Nullack on 2010-09-04
Maybe your better experience with Fedora is due to the main Nouveau dev being Beg Skeggs, well he's a Red Hat employee. I see it as kinda of natural that Red Hat's distro is most current with it.

Generally the big upstream contributors are from Red Hat, Novel, Intel and Apple. Canonical isnt a big player with upstream development contributions.

From my own user point of view though, my humble opinion is that even with dev tree compiles of Nouveau I'm still left with something that is slow, more buggy and has less features than the closed source NVIDIA one. IMHO, it's not about religious obsession to open sourced code, it's about me as a user being able to do what I want and have it work. So thats why personally for me I just use the closed source nvidia module.

---

### Post by kahumba on 2010-09-04
> **lancest said:**
> 
This ought to be top priority in my mind- instead of the Rhythmbox applet volume control type stuff for example.
+1
I have this same feeling for like 2 years. Reinventing notifications and switching from brown to purple while users want/need much better open-source video/audio drivers and better quality key desktop applications. Of course you'd think "it's easy bashing someone", but I'm not, I'm simply stating the truth.

---

### Post by lancest on 2010-09-04
Yes. 

Much as I like Ubuntu- I've got to question it's development direction occasionally. 
.
ATI/Intel open source drivers are great for me on Lucid however.

---

### Post by MacUntu on 2010-09-04
What's wrong with being conservative? Just because it works fine for you in F13 doesn't mean it works fine for everyone else. IMO Ubuntu should stay the hell away from enabling things by default that are called experimental or unsupported by the upstream developers.

---

