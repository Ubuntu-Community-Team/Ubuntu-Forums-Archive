---
title: "Ubuntu has become a graphical nightmare"
date: 2007-11-06
forum: Multimedia &amp; Video
---

### Post by gcrussell1 on 2007-11-06
Everything that happens on the screen of my Ubuntu desktops is lingering, by which I mean that every keystroke, every drag trail from a moving window, and everything else (save mouse trails) is lingering, creating an absolute nightmare of graphics - I can't function on Ubuntu when it's running like this. I'm writing this post on it right now, and it's taken me 2 or 3 times as long as it should, as well as producing a massive headache (figurative and a bit literal as well...) . Compiz is installed, and I'm using the extra level of effects, but even when I turned compiz off entirely the problem persisted, so I don't think it's an issue with Compiz. I'm using an ATI Mobility 9600 with the latest 8.42.3 drivers, which I installed 2 or 3 days ago with no trouble - everything ran just fine before and after restarts, so I also doubt that it's a driver issue (would an issue like that lie in wait for a couple days before showing itself?). My best guess is that it's got to do with Kubuntu - I installed the Kubuntu meta-package yesterday to give it a try, and I decided that I didn't really care for Kubuntu - too cartoony and it makes my PC run slower than Vista Ultimate with a dozen major virii on a computer with 512 MB of RAM - so I uninstalled it - unfortunatelythat meant going through add/remove apps and synaptic to search for everything KDE that was installed, since I don't know of any particular way to uninstall a meta-package and all of its related packages at once. As I uninstalled everything this way, I didn't notice any problems, and Ubuntu worked fine all evening afterward - however, when I started the computer up today, it started having this problem, so that's where I stand. I've attached a screenshot if that helps.

Let me add that not *everything* lingers - certain colors and windows disappear completely (such as when I closed the upload manager for the forums, it left the other firefox window clear outside of the typing forms), but the screenshot clearly shows the issue and how much of a menace it is.

Please, any ideas?


[SOLVED] - I hadn't removed the KDE Splash Screen manager, the removal of which ended my problems... go figure. Incidentally, I have no idea how or why that would have caused any problems, but isn't that always the way?

---

### Post by gcrussell1 on 2007-11-19
The problem has returned... I haven't done anything with KDE since the original occurence, but it's back all the same. The symptoms are the exact same, and it's probably an issue with something I downloaded off Synaptic last time the computer was on - offhand, I downloaded an apt-get get-dep type command for Zangband (it was something like sudo apt-get install get-dep zangband - someone mentioned it in my post about trouble compiling Zangband, I took it straight off that) and I downloaded the gtk 1.2 dev tools, also trying to get zangband working. I can't think of anything else I added, but that doesn't mean there wasn't anything else.

Does anyone have any ideas this time? I figure that it must be something I added, since that seemed to be the problem last time too, but anyone have any ideas about what that might be?

---

### Post by RealG187 on 2007-11-19
> **gcrussell1 said:**
> [SOLVED] - I hadn't removed the KDE Splash Screen manager, the removal of which ended my problems... go figure. Incidentally, I have no idea how or why that would have caused any problems, but isn't that always the way?

[http://ubuntuforums.org/showthread.php?t=597937](http://ubuntuforums.org/showthread.php?t=597937)
I have had trouble too.

---

### Post by angryfirelord on 2007-11-20
Does your card have adquate ventilation? Cards that overheat tend to display artifacts and do weird things.

If that's not the issue, then change your driver to the open-source one (ati). If you used aticonfig's utility to set up your xorg, run this instead:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by gcrussell1 on 2007-11-20
> **RealG187 said:**
> [http://ubuntuforums.org/showthread.php?t=597937](http://ubuntuforums.org/showthread.php?t=597937)
I have had trouble too.
Thanks, but the issue this time has nothing to do with the splash screen manager for KDE - that's been gone for a couple weeks now.
> **angryfirelord said:**
> Does your card have adquate ventilation? Cards that overheat tend to display artifacts and do weird things.

If that's not the issue, then change your driver to the open-source one (ati). If you used aticonfig's utility to set up your xorg, run this instead:
```
sudo dpkg-reconfigure xserver-xorg
```
I try to keep the laptop pretty clean, so it should ventilate as well as can be expected. I'm using the open-source ATI driver, and have been for a week and a half or so, so I don't think that's the source of the problem, but it's a definite possibility.

Actually, I found that removing libgtk1.2-dev (I think that's the name) fixed the issue - even before I removed it really - I selected it for removal in Synaptic and the issue went away, and after completing the removal, it hasn't come back since. However, I've had this problem twice now, and it's been fixed each time by removing two entirely unrelated programs... it seems like I should have a better idea of what's going wrong when the problem occurs, instead of just removing programs at random until the problem goes away. Does anyone know what's causing this?

---

### Post by angryfirelord on 2007-11-20
I still believe it's a driver issue because I ran into a similar situation with PCLinuxOS. It wanted to load the ati driver on my X1600, which isn't compatible, so I was getting that distortion. 

Change your driver to **vesa** and run that for a little bit. Your computer may feel a little slower, but if the distortion goes away, then the ati driver is the problem.

---

