---
title: "Why won't most CD/DVD burn apps let you manually set burning speed?"
date: 2019-02-23
forum: Multimedia Software
---

### Post by raphaell2 on 2019-02-23
I've got three GUI CD/DVD burn apps installed on the Linux side of my desktop pc: Brasero, which comes preinstalled with my Ubuntu flavour, Mate; K3b, which I use for multisession projects because as far as I can tell, it's the only Linux GUI CD/DVD burn app that handles those well; and Xfburn, which I use for reasons I'm about to get into. 

As far as I can tell, Xfburn is the only one of those three that allows you to manually set the burn speed. The other two usually try to burn at the maximum speed the DVD drive is physically capable of, which, for me, is usually faster than what the DVDs themselves can take, which usually leads to burn errors and messed up DVDs. (While I'm at it, I might mention that over on the Windows side, the inbuilt burner for Windows Explorer causes the same problem.)

So - why hasn't anyone on the Brasero and K3b projects noticed that and fixed it?

---

### Post by Autodave on 2019-02-23
I only use xfburn and have so for several years after having problems with Brasero.  However, I know that when I quit using Brasero, it still gave you the option for controlling the burn speed.

---

### Post by freemedia2018 on 2019-02-23
I used k3b then brasero then xfburn, and finally wodim. Of course the gui tools are nice for creating images, but no command line tool worth anything would ever drop an option as obvious as that, and they dont tend to move them around very much, either.

Guis on the other hand, go through absurd fits of fashion where they follow ridiculous design ideas like "you know what users really hate? FEATURES!" "Yeah, lets get rid of those!" 

It's not that I'm against minimalism, I'm a huge fan. What I'm not a fan of is design fads that take mainstream things people rely on, and turn them into something unrecognisable where all existing documentation and experience is worthless. That's a huge pet peeve of mine, and when a project gets taken over by sabs who love this sort of overhaul (if it's a fork, it's no problem at all. If it affects the main version, that's when I dislike it intensely) I tend to drop those projects for good.

---

### Post by raphaell2 on 2019-02-23
> **Autodave said:**
> I only use xfburn and have so for several years after having problems with Brasero.  However, I know that when I quit using Brasero, it still gave you the option for controlling the burn speed.

Wait, you're right. I just checked brasero, and that option is still there.

---

### Post by raphaell2 on 2019-02-23
> **freemedia2018 said:**
> What I'm not a fan of is design fads that take mainstream things people rely on, and turn them into something unrecognisable where all existing documentation and experience is worthless. That's a huge pet peeve of mine,

I completely agree with you on that point. Working with some kinds of software (both FOSS and proprietary) is as if you would have a job where you're a messenger in a big building, and every once in a while, just when you've learned well where all your important destinations are and the easiest ways to get there, a team of magicians arrives and casts some magic spells that completely rearrange the layout of the building.

---

### Post by scdbackup on 2019-02-24
Hi,

well, at least with Brasero and the libburn plugin, it is/was about a
wrong sequence of parameters for libburn call burn_drive_set_speed().
See my comment
  [https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/656297/comments/18](https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/656297/comments/18)
of
  [https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/656297](https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/656297)

As far as i can see in Debian's copy of Brasero's souce, the problem
is still present. I.e. Brasero orders libburn to set write speed to
value 0, which means maximum speed, and the read speed to the speed
that Brasero plans to use for writing.
  [https://codesearch.debian.net/search?q=package%3Abrasero+burn_drive_set_speed](https://codesearch.debian.net/search?q=package%3Abrasero+burn_drive_set_speed)

The first match in plugins/libburnia/burn-libburn.c line 705
```

burn_drive_set_speed (priv->ctx->drive, burn_drive_get_write_speed (priv->ctx->drive), 0);

```
is just another way to express the desire of
```

burn_drive_set_speed (priv->ctx->drive, 0, 0);

```

But the second match in line 560
```

burn_drive_set_speed (priv->ctx->drive, rate, 0);

```
could indeed set a Brasero-supplied write speed if it was changed to
```

burn_drive_set_speed (priv->ctx->drive, 0, rate);

```

--------------------------------------------------------------------------

In K3B it looks like growisofs, cdrecord, wodim, or cdrskin get set some
speed value, if the higher GUI levels set it to a value larger than 0.
See
  [https://codesearch.debian.net/search?q=package%3Ak3b+speed%3D](https://codesearch.debian.net/search?q=package%3Ak3b+speed%3D)
where program options "speed=" or "-speed=" get set.

(Somebody else would have to explore the GUI for the control element
 which offers to set the speed value > 0.)

--------------------------------------------------------------------------

As for wodim and DVD: The program is deprecated for DVD by its last
maintainer (Steve McIntyre, in charge of Debian ISOs, former Debian Project
Leader).

Classic program for DVD is growisofs. I deem my cdrskin and xorriso not
worse with DVD and slightly better with Blu-ray. Their main advantage
might be that growisofs is unmaintained since about 10 years.

Have a nice day :)

Thomas

---

