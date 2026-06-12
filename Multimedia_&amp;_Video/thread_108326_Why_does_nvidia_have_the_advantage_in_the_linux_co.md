---
title: "Why does nvidia have the advantage in the linux community?"
date: 2005-12-25
forum: Multimedia &amp; Video
---

### Post by Brachabre on 2005-12-25
As the title asks, I wanna know how come Nvidia always has the upperhand whenever it comes to having pre-loaded drivers in distros instead of ati (if even that). Also in distros with user loadable modules (i.e. slax) why do they have nvidia drivers and not ati? Is it b/c nvidia is open-source friendly? ATI makes crappy drivers? hehe

Just tryin to gain a little philosophy behind open-source :smile:

---

### Post by The Warlock on 2005-12-25
[QUOTE=Brachabre]As the title asks, I wanna know how come Nvidia always has the upperhand whenever it comes to having pre-loaded drivers in distros instead of ati (if even that). Also in distros with user loadable modules (i.e. slax) why do they have nvidia drivers and not ati? Is it b/c nvidia is open-source friendly? ATI makes crappy drivers? hehe

Just tryin to gain a little philosophy behind open-source :smile:[/QUOTE]


nVidia used to have open-source drivers, and so everyone in the Linux community loved them. Then they closed-sourced them, so they're not installed by default. Still, they suck a lot less than ATi's drivers right now, so they're still the recommended company if you're getting a new graphics card.

And every distro has user-loadable modules, (or root-loadable modules; I mean, you don't want just any user using modprobe!)

---

### Post by az on 2005-12-25
I do not think Nvidia ever opened their source code.  If they ever had, we would have open-source 3d drivers for some of their cards.

A lot of the hardware drivers that exist for linux are reverse-engineered.  When you think of it, it is an impressive collection of supported hardware despide the lack of vendor-support.

The 3D acceletation in video cards is an aspect of the hardware that is difficult to reverse-engineer.  A lot of the technology involves guarded trade-secrets which each company wants to keep under wraps - not something you can easily share with the free-libre-open source community.  Well, maybe.  Both ATI and Nvidia feel that the open-source model is not profitable right now.

ATI have shared more hardware information so that the community can develop drivers than Nvidia.  In the long run, this may prove to be beneficial.  In the short term, people who want to play FPS games in linux buy nvidia cards because their closed-source drivers work better than ATI's closed-source and open source drivers.

This is probably good business strategy for Nvidia for the moment, since much of open source is developed because of the "scratch-your-own-itch" principle.  Basically, a hacker will solve a certain problem with greater zeal than someone working nine-to-five to solve that problem among many other problems.  By providing a better binary driver for Nvidia cards, a lot fewer FPS fans are writing code for the ati drivers because their itch has been scratched by using Nvidia cards.

Binary-only drivers are evil (okay, not ideal) for two reasons.  One, they do not follow the pronciples of FLOSS (the gpl - get the source code and improve it)  and Two, since it is partly a kernel driver, it's development is behind the kernel development.  You can upgrade your kernel one day and your video card stops working until the people who make the driver spoon-feed the driver to your distribution.

So, if either company feels that they will sell more cards by providing open-source drivers for their hardware, they will do it.  Until then, use a games console.  Both company's closed-source drivers cause your computer to crash anyway.  For non-gaming desktop use, you are far better off using the open source default non-3D driver anyway.

---

