---
title: "SDL Error: x11 driver not configured with opengl"
date: 2010-05-18
forum: Multimedia Software
---

### Post by scarypajamas on 2010-05-18
Ok, so I installed Ubuntu 9.04 Jaunty fresh about a week ago.  Since then, I've ungraded the OS to the latest version, 10.04 LTS.

I've installed the NVIDIA drivers via the NVIDIA website.  I know the drivers are working because I can type "glxgears" in the terminal and I will see the spinning gears demo.  I've also installed Compiz Desktop Effects and it runs just fine.

The problem is when I try to use SDL with OpenGL...

What I've done is I downloaded SDL via libsdl.org and did a ./configure, make, make install.

Now, when I try and run any application that uses SDL/OpenGL combination, I get the error: "x11 driver not configured with opengl"

I've been reading around, and the error seems to be an issue with SDL itself.  Normally, I would continue googling until I found a solution, but the problem is I haven't been able to find a solution that works yet.

It would be awesome if someone who's had a similar problem could share there experience and how they fixed it.

EDIT:
Egg on my face....

I did a complete uninstall and re-install of SDL and it seems to be working now.

I hope this helps someone: If you already have SDL installed, uninstall it with "make uninstall"
Then enter "./configure --prefix=/usr" "make" "make install"

---

