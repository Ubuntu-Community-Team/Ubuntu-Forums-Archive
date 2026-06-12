---
title: "The major X breakage was now  :)"
date: 2010-07-06
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by xeizo on 2010-07-06
I was not careful enough when I upgraded today, apt removed everything Xorg related and it is not even possible to force install Xorg again.   Granted, I run Xorg-edgers ppa but I guess this mess will come downstream to Maverick only later.  If I'm lucky, there will been some fixed packages from even further upstream when I log in tomorrow, so I can get X up and running again ;)

---

### Post by psyke83 on 2010-07-06
> **xeizo said:**
> I was not careful enough when I upgraded today, apt removed everything Xorg related and it is not even possible to force install Xorg again.   Granted, I run Xorg-edgers ppa but I guess this mess will come downstream to Maverick only later.  If I'm lucky, there will been some fixed packages from even further upstream when I log in tomorrow, so I can get X up and running again ;)

You could try using the ppa-purge tool, and then re-installing Maverick's default Xorg packages. See the Xorg-edgers PPA's description if you've never used it before.

---

### Post by hikaricore on 2010-07-06
So the error exists between the keyboard and the chair...
That's doesn't qualify as breakage.

---

### Post by cecilpierce on 2010-07-06
I did the same thing and didnt notice anything until all of a sudden REMOVING bla bla bla, so before I rebooted I tried all kinds of stuff, kept saying broken this and that. Something made it reinstall X. When I go back to Maverick Ill look and see what did the trick.

---

### Post by autocrosser on 2010-07-06
That's why you use Aptitude or Synaptic---you can PREVIEW what is going to be installed/removed/upgraded BEFORE you "really" do it.......

---

### Post by hikaricore on 2010-07-06
Or bothering to pay attention to the section labelled "To be REMOVED".

---

### Post by ranch hand on 2010-07-06
Oh come on guys, you are no FUN at all.  This has been pretty damned smooth, so far, if you want breakage you pretty much have to manufacture it your self.

This way the OP has some practice for when (we can always hope) things get hairy.

---

### Post by autocrosser on 2010-07-06
BRING ON THE BREAKAGE!!!!!:popcorn::popcorn::popcorn:


LOL----:lolflag::guitar:

---

### Post by dagrump on 2010-07-07
Didn't remove anything, but I can't get past plymouth. Ugly, depressing muddy purple screen w/ ubuntu in white, & did I see an orange logo?
I really ain't pleased to boot to recovery mode, but the default plymouth screen is one homely beast. The reporting tool sent me to an old bug, w/ lots of dupes?
So there might be breakage. 
It is piddly breakage, if it's breakage. It could just be a bit of under cooked potato.

---

### Post by ranch hand on 2010-07-07
Plymouth just generally suck canal water.

If you go to /etc/default/grub you can edit the boot string so that it does not contain "splash".  This will probably fix your problem.

You can try that ahead of doing it by just hitting e and editing your boot entry right on the menu screen and see if that helps.  If it does just do the edit above and run update-grub.

---

### Post by dagrump on 2010-07-07
We'll give it a shot, I don't have a lot to lose on this drive.

---

### Post by xeizo on 2010-07-07
There was "working" X packages this morning, but they do not work with nvidia-current at all. 

They do work with Nvidias own 256.35 driver, except there's no 3D, only 2D-acceleration. GLX/OpenGL has gone missing completely.

I guess I will have to remove xorg-edgers for now and downgrade to Maverick default, I have some reading about how to to do :) 

I don't complain, it's my own fault believing a Alpha isn't unstable enough for me :D

edit. I did the ppa-purge thing and got back to an older Xorg, but nvidia-current still doesn't work. Luckily Nvidias own 256.35 driver do work, and now in 3D as well. But instead the gnome-settings-daemon doesn't like the driver too much. It's better than before though ....

---

### Post by andrewthomas on 2010-07-07
The rest of the xorg packages are now in the xorg-edgers ppa.  Should be ok to update to 1.9

```
X.Org X Server 1.8.99.904 (1.9.0 RC 4)
Release Date: 2010-07-01
Build Date: 06 July 2010  07:54:29AM
xorg-server 2:1.8.99.904+git20100705.9f0b193a-0ubuntu0sarvatt3
```

---

### Post by xeizo on 2010-07-07
Nice, things back on track! Personally I did a fresh install of todays Ubuntu Studio "daily" on another disk, Xorg/3D works just fine of course. I'm not sure I'm going back to edgers  ;)

It was not possible to install grub during the install(a bug!), so I had to revert to lilo, and because of that I can't boot back into my old system. I guess, now I have to read some about how to switch from lilo to grub2 ...

No big deal, but I have to change back to grub sooner or later anyway, to have all the supposed boot features avalable in Maverick.

---

### Post by hikaricore on 2010-07-07
Edgers is still working fine here as it has all month.

---

### Post by andrewthomas on 2010-07-07
> **hikaricore said:**
> Edgers is still working fine here as it has all month.
I never said that anything was not working.  Just that an update was now possible because all the necessary packages had been rebuilt.

---

### Post by hikaricore on 2010-07-07
You didn't, other people did.  :p

---

### Post by aviramof on 2010-07-08
I guess it's good that i use fglrx from x-swat ppa it prevent me from all the x breakage problems.:)

---

### Post by recluce on 2010-07-08
> **ranch hand said:**
> Oh come on guys, you are no FUN at all.  This has been pretty damned smooth, so far, if you want breakage you pretty much have to manufacture it your self.

This way the OP has some practice for when (we can always hope) things get hairy.

If I really wanted breakage, I would install Windows! :rolleyes:

---

### Post by ranch hand on 2010-07-08
> **recluce said:**
> If I really wanted breakage, I would install Windows! :rolleyes:
This is a very good point.  Breakage in MS, however, is not fun.

Breakage in an Ubuntu testing OS is FUN.

---

