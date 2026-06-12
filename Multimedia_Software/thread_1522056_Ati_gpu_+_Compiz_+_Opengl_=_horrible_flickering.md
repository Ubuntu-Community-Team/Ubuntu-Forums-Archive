---
title: "Ati gpu + Compiz + Opengl = horrible flickering?"
date: 2010-07-01
forum: Multimedia Software
---

### Post by Doeke on 2010-07-01
I recently got a new computer, did a fresh install of the newest linux mint (it's pretty much exactly the same as ubuntu 10.04), and have a ati gpu now, (radeon HD5850). But I've noticed opengl windows flicker whenever compiz is enabled (visual effects normal). For example glxgears and the demo of the love2d game engine flicker.

I've tried changing settings in compiz, but nothing seemed to fix it. I've also attempted to remove fglrx and install the open ati driver, but I couldn't get that one working.

I'm sure this must be a common problem, but google did not help me this time.

So does anyone know what else I could try to fix this, or if there is a better workaround besides just using metacity?

---

### Post by rockdj on 2010-08-17
I've got the same issue and looking for a solution.  I've got a Radeon HD 2400 XT and using the latest ATI drivers (10.7) on Ubuntu 10.04.

Currently, my only option is to disable Compiz when trying to use OpenGL apps.  Not a really nice workaround or a solution, unfortunately.

---

### Post by rockdj on 2010-08-17
> **rockdj said:**
> I've got the same issue and looking for a solution.  I've got a Radeon HD 2400 XT and using the latest ATI drivers (10.7) on Ubuntu 10.04.

Currently, my only option is to disable Compiz when trying to use OpenGL apps.  Not a really nice workaround or a solution, unfortunately.

Reverting to the fglrx drivers in the 10.04 repository fixes the issue so I'm guessing ATI broke something in later versions.  Here's hoping things stay fixed for later versions of Ubuntu.

---

### Post by cblanquer on 2010-09-09
Yes. The bad thing is that I tried this (in my case) because Kubuntu, due to a long lasting KDE error, does not manage well 2 screens when not cloned.
Now I have got the perfect setup (a single virtual screen with my 2 physical ones inside) but the execution is poor and Compiz gets constantly disabled.

I shall try to go back to the open drivers and see how configuring my two screens, an actual pain.

---

