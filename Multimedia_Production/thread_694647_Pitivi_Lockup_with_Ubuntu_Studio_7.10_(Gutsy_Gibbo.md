---
title: "Pitivi Lockup with Ubuntu Studio 7.10 (Gutsy Gibbon) and all updates to date."
date: 2008-02-12
forum: Multimedia Production
---

### Post by Themicles on 2008-02-12
As the title says, Pitivi locks up on Ubuntu Studio with all the latest updates through Synaptic.

The program often locks up upon opening it. It will sometimes work for a while, but lock up as I go through menus. I've not yet been able to get to the point of rendering a project. Though I have managed to add clips. There are no errors, as I've let it sit locked up for an hour and forced it to quit.

I've tried reinstalling it. I've tried reinstalling the entire Ubuntu Studio - Video package. I'm at a loss here...

---

### Post by Stochastic on 2008-02-13
are you on a system that has been installed from the Ubuntu Studio DVD? or have you downloaded the meta-packages onto a plain Ubutntu?

---

### Post by Themicles on 2008-02-13
I burned a DVD of the Ubuntu Studio Gutsy Gibbon release.

When I try to reinstall Pitivi, it asks for the DVD. I admit that I am relatively new to Linux, so I do wonder if there is a way to force it to get the package online, instead of from the DVD.

---

### Post by Stochastic on 2008-02-13
hmm it sounds like your apt-get's source listing probably is still using the DVD as a main repository.  You want to make sure that you're using the web instead.  There's a number of ways to fix this, through System->Administration->Software Souces, or by manually editing the /etc/apt/sources.list

I'd get rid of the DVD as a source for software as it invariably contains old code by now.

---

### Post by Themicles on 2008-02-13
Ah, yes, I see it now thanks. :)
I've edited my sources before but missed the checked section in the box at the bottom, because the whole disc list wasn't visible.

---

### Post by Themicles on 2008-02-17
It continues locking up even after reinstalling from the repository. I now have Cinelerra working well, and my source videos in a format Cinelerra agrees with. But I still wonder if it's not Pitivi, but something Pitivi uses that is causing the lockup.

---

