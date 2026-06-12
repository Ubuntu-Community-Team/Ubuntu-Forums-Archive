---
title: "Unity slow to respond"
date: 2011-04-02
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by dmillerw on 2011-04-02
Don't quite know how to explain this, but basically whenever I'm interacting with the unity interface (opening a lens, or the main dash, or even using the new ALT-F2 interface) it seems to take a second before actually opening.

This isn't a huge deal, but it does kinda bug me a bit.

This happening to anyone else?

System Specs:
Pentium 4 2.8Ghz Hyper Threaded
1.5GB RAM
NVIDIA GeForce 6200 - Have the latest drivers installed, 260.something or other

---

### Post by 3Miro on 2011-04-03
It is smooth enough for me. Must be settings/hardware/bug. I have tried it on both Nvidia GTX260 and ATI 4250 (integrated).

How does regular compiz work for you, can you usually turn on a lot of animations, transparency and such.

---

### Post by dmillerw on 2011-04-03
> **3Miro said:**
> It is smooth enough for me. Must be settings/hardware/bug. I have tried it on both Nvidia GTX260 and ATI 4250 (integrated).

How does regular compiz work for you, can you usually turn on a lot of animations, transparency and such.

Within reason, yeah

---

### Post by 3Miro on 2011-04-03
> **dmillerw said:**
> Within reason, yeah

This has to be a bug. I remember when KDE 4 first came out, NVIDIA has some bugs in their drivers that made KDE almost inoperable. Then they sure too their time fixing them. Hopefully your problem is with Unity itself as Canonical can address this one much faster.

---

### Post by Sef on 2011-04-03
Moved to Natty.

---

### Post by cariboo on 2011-04-03
I'd suggest you try the nouveau driver with the ligl1-mesa-dri-experimental package, on some systems when using the nVidia drivers libcairo causes a memory leak, that could cause your system to start using swap, which will slow the system down

---

### Post by dmillerw on 2011-04-03
> **cariboo907 said:**
> I'd suggest you try the nouveau driver with the ligl1-mesa-dri-experimental package, on some systems when using the nVidia drivers libcairo causes a memory leak, that could cause your system to start using swap, which will slow the system down

I've already got the nouveau driver installed (apparently) how would I go about disabling the current driver, and switching to that.

Also, I tried searching for "ligl1-mesa-dri-experimental" and couldn't find it...

---

### Post by Orographic on 2011-04-03
> **dmillerw said:**
> Don't quite know how to explain this, but basically whenever I'm interacting with the unity interface (opening a lens, or the main dash, or even using the new ALT-F2 interface) it seems to take a second before actually opening.

This isn't a huge deal, but it does kinda bug me a bit.

This happening to anyone else?

System Specs:
Pentium 4 2.8Ghz Hyper Threaded
1.5GB RAM
NVIDIA GeForce 6200 - Have the latest drivers installed, 260.something or other

I also get this on my system, Core i3 540, H55 USB-3 Gigabyte board, 4GB RAM. I'm using the onchip GPU. Its very stable but yeah, just a slight delay in some menus.

---

### Post by cariboo on 2011-04-03
Could either of you check your ram usage and post it here? Open a terminal and type:

```
free -m
```

---

### Post by Orographic on 2011-04-03
total       used       free     shared    buffers     cached
Mem:          3768        701       3066          0         36        364
-/+ buffers/cache:        300       3468
Swap:         3832          0       3832


It seems to have improved for me after the latest updates. All menus are faster now.

---

### Post by dmillerw on 2011-04-03
dylan@whitebox:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1504       1431         73          0         69        350
-/+ buffers/cache:       1011        493
Swap:         1532        208       1324

I've installed all updates available (last check, one hour) and am still having this issue.

---

### Post by cariboo on 2011-04-04
> **dmillerw said:**
> I've already got the nouveau driver installed (apparently) how would I go about disabling the current driver, and switching to that.

Also, I tried searching for "ligl1-mesa-dri-experimental" and couldn't find it...

Sorry there was a spelling error that should be **libgl1-mesa-dri-experimental**, you should have had the choice of installing nvidia-current, or the experimental drivers, when selecting the additional drivers.

---

### Post by hackel on 2011-04-13
I, too, have been experiencing this issue since upgrading to Natty (I didn't run Unity before).  When I click on the Ubuntu icon in the upper-right, hit the super key, or F2, it takes a full two seconds for the unity screen to appear.  Three full seconds for either the Applications or Files and Folders windows to appear after clicking on the button.  I'm using a Dell Mini 9, Intel 945GME graphics, 2GB RAM, fast SSD.  I had no problem enabling basic effects with Compiz in the past and have run with this configuration for the past couple years without any problems.  If I had to take a guess, it seems as if Unity does not cache the information needed to render these windows, and so is hitting the hard disk each time you click on one of the buttons.  Needless to say, it severely affects the usability of Unity for me.  I hope it is just a bug that can be fixed and not a fundamental design limitation!

---

### Post by Sashin on 2011-04-13
In Compiz unity experimental settings, make sure static blur is not enabled.

---

### Post by cariboo on 2011-04-13
It's not a design limitation, as on my Compaq Mini 1100, Alt-F2 works instantly, Atom 270, 1GiB ram, Samsung 160GiB mechanical hard drive 945GME graphics.

---

### Post by nasp on 2011-04-18
> **Sashin said:**
> In Compiz unity experimental settings, make sure static blur is not enabled.

That fixed it for me :)

---

