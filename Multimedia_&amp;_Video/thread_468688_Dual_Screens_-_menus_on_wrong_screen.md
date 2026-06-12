---
title: "Dual Screens - menus on wrong screen"
date: 2007-06-09
forum: Multimedia &amp; Video
---

### Post by wombat20 on 2007-06-09
I've got dual screens setup on Feisty with my NVidia 8800 GTS using the NVidia driver and TwinView (Separate X screen didn't seem to work), but I have a few remaining issues.

1. Despite saving it to my X Configuration file, it doesn't remember it and I have to re do it each time (just tried launching NVidia settings via gksudo, so maybe that will work).

2. If I use my Right-hand monitor, then any menus (from Firefox etc) popup on the OTHER screen, which is very annoying!

3. New windows - Shutdown dialog, gksudo etc appear ACROSS the screen boundary, which is also annoying.

Are these obvious things to fix or does everyone put up with them?

Any ideas appreciated!  :)

---

### Post by wombat20 on 2007-06-09
**UPDATE:** Looks like running the NVidia settings program as root (gksudo nvidia-settings) helps a lot. This means it can actually save your changes to the X config file and you don't loose them when you reboot!

I now have two separate X displays, which works pretty well except that as far as I can tell there's no way to drag windows between them!

---

### Post by wombat20 on 2007-06-09
OK, just managed to enable Xinerama and everything is fine.  :)

I seem to have solved my own problems, but perhaps this information will be useful to someone else. ;)

---

### Post by RTrev on 2007-06-09
> **wombat20 said:**
> OK, just managed to enable Xinerama and everything is fine.  :)

I seem to have solved my own problems, but perhaps this information will be useful to someone else. ;)

Glad you solved it.  Did you manage to prevent things from showing up on the wrong screens?  If so, how?  I have Xinerama enabled too, but things just appear wherever they want to.  Removing a USB thumb drive always results in a message right across the boundary of the two monitors.  :-/

Here is the drill I go through on each install:

```

sudo dpkg-reconfigure -phigh xserver-xorg

sudo nvidia-glx-config enable

sudo nvidia-xconfig --twinview

```

After that I manually clean up the file a bit, like taking out the references to pointing devices I don't have, and adding options like "NoLogo" and "Coolbits".  

Anyway, the only thing I use nvidia-settings for is if I want to overclock the card a bit.  I've found that it has little use beyond that.  But maybe I'm missing something, if you managed to keep things on the correct screens, and not having them overlap screens?

Bob

---

### Post by wombat20 on 2007-07-01
Most things tended to behave once they'd appeared, but it's still anyone's guess as to where they appear. I have heard that KDE handles this better.

What I'm annoyed about at the moment is that after an update (not sure which one), I got a X config BSOD on reboot. I think next time I won't let it update anything.

I'm back to one monitor only!! Can't get the nvidia drivers working at all. Anyone else had problems after an update recently?

---

### Post by RTrev on 2007-07-01
> **wombat20 said:**
> Most things tended to behave once they'd appeared, but it's still anyone's guess as to where they appear. I have heard that KDE handles this better.

What I'm annoyed about at the moment is that after an update (not sure which one), I got a X config BSOD on reboot. I think next time I won't let it update anything.

I'm back to one monitor only!! Can't get the nvidia drivers working at all. Anyone else had problems after an update recently?

Oh, yes!  My wife's machine couldn't get X running after a recent update.

She said she had to run:

```

sudo dpkg-reconfigure xserver-xorg

```

And then she was okay again.  I gather a lot of people had trouble with this recent update.

---

### Post by wombat20 on 2007-07-01
Thanks for the tip. I have done that, but the only thing that works currently is (sigh) Vesa. I trawl the forums later and find that proper solution, just can't face the effort right now!

---

