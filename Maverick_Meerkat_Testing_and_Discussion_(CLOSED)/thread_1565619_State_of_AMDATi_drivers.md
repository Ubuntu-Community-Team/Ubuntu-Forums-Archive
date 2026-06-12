---
title: "State of AMD/ATi drivers"
date: 2010-09-01
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by napsy on 2010-09-01
Hello.

I'm sorry if I missed a thread about this but I'm wondering what is the corrent state for Radeon drivers in Maverick?

Can be power saving enabled with KMS for opensource radeon drivers now? Are the catalyst drivers ready for xserver 1.9?

Greets.

---

### Post by Tracy177 on 2010-09-01
> **napsy said:**
> Hello.

I'm sorry if I missed a thread about this but I'm wondering what is the corrent state for Radeon drivers in Maverick?

Can be power saving enabled with KMS for opensource radeon drivers now? Are the catalyst drivers ready for xserver 1.9?

Greets.

i have lucid and use latest catalyst everything work just good.

i dont think maveric will have 1.9 xorg doesnt look like if it will than ati will be late with new diver u'll need wait 1 or two months for a driver.

i dont bother myself about power saving open or not 

and i dont use open source drivers  

and catalyst does support maveric cuz maveric has the same xorg as lucid

---

### Post by napsy on 2010-09-01
Oh ok. I was wondering because I currently use arch and it supports basic power management for the opensource radeon drivers on linux 2.6.35. Since I have the system on a laptop, power management is relevant to me.

---

### Post by evilkastel on 2010-09-01
Actually maverick will have xorg 1.9, it is in the updates avaliable for a couple of weeks now. The reason i haven't updated is because the drivers are not ready. And about the power saving, i don't really know, but xorg 1.9 has many improvements i hear, so if in arch you are getting it, it's possible they will implement it in ubuntu.

---

### Post by xir_ on 2010-09-02
I've generally found a 25% battery life improvement in maverick. My wattage went down from 22 to around 18, but this is a long way away from the catalyst which was running at around 9 watts.

I have tried different profiles, but as of yet haven't found any consumption change between the profile setting and the dynpm setting.

---

### Post by cottfcfan on 2010-09-06
Sorry to hijack this thread somewhat, but what is the state of the radeon opensource driver in Maverick.
 In Lucid it works reasonably well, although 3D acceleration is limited.
 Have the opensource drivers improved in Maverick or not?

---

### Post by PGHammer on 2010-09-06
> **cottfcfan said:**
> Sorry to hijack this thread somewhat, but what is the state of the radeon opensource driver in Maverick.
 In Lucid it works reasonably well, although 3D acceleration is limited.
 Have the opensource drivers improved in Maverick or not?

FOSS drivers improved with *Lucid* (exception: R8xx/HD5xxx).

Unless you have HD5xxx, you can use the FOSS drivers for everything with Maverick Meerkat.  (However, Maverick Meerkat includes Xorg 1.9, which AMD Catalyst doesn't support, and the 3D support is still a work in progress, with a lot of functionality still missing.)

Surprisingly, the 2D support (HD5xxx) in Maverick is actually faster than it is in Lucid.

Warning: Do *not* update Kubuntu in Maverick beta 1 or beyond the initial beta 1 install (this applies only to KDE, as there is major breakage that renders KDE 4.5.x unusable).  I have *not* filed a bug report as I have no idea what broke or why.

---

### Post by Jim March on 2010-09-06
OK, I finally have all the kinks sorted out from a 'pooter I've only owned for about a week: an IBM Thinkpad T60p with an ATI FireGL V5250.  This is very similar to the AT X1700 and supposedly the open-source drivers consider them the same thing.  This in turn is similar to the X1600 except I think more dedicated RAM - the X1600 has 256megs, the X1700 has 512megs.

Out of the box I had no problem at all except Compiz, and that turned out to be just a problem of lacking compiz-gnome.  With or without Compiz I got native 1680x1050 support, very fast gaming in Warzone 2100 at full res full screen, good full-screen video playback in flash, VLC and others.  Basically, the open-source driver support seems rock solid.

At the moment I'm on the xorg-edgers PPA only because it's something I tried as a Compiz fix and stayed with it because it fixed a bizarre problem with the touchpad.  I don't think edgers is necessary for support on my video card and I'll probably remove it once Maverick goes fully live.

I picked a high-performance vintage ATI card expecting strong open source support and I'm absolutely convinced this was the right answer.

As an aside: for $360 on Ebay as an off-corporate-lease blanked-hard-disk special, this is BY FAR the best lappy I've ever owned.  Built like a tank, dual PCMCIA and Expresscard/54 slots, Intel T7400 Core 2 Duo CPU with 64bit and hardware virtualization support...it just kicks the pants off of anything available as a "consumer grade" lappy for $600 or less.  Check the specs: the X1600 video card just destroys anything made by Intel (ever) and even stomps the best modern ATI "integrated" video chipsets like the 4250, which is otherwise pretty respectable.

Go here to pull up details on any video chipset made in the long column in the middle:

[http://www.notebookcheck.net/ATI-Mobility-Radeon-X1700.2157.0.html](http://www.notebookcheck.net/ATI-Mobility-Radeon-X1700.2157.0.html)

...or go here to get a side-by-side comparo:

[http://www.notebookcheck.net/Computer-Games-on-Laptop-Graphic-Cards.13849.0.html](http://www.notebookcheck.net/Computer-Games-on-Laptop-Graphic-Cards.13849.0.html)

The best vintage ATI video cards just rock.

---

### Post by cottfcfan on 2010-09-07
PGHammer
Thanx for your reply.

---

### Post by BlueJayofEvil on 2010-09-07
> **PGHammer said:**
> Warning: Do *not* update Kubuntu in Maverick beta 1 or beyond the initial beta 1 install (this applies only to KDE, as there is major breakage that renders KDE 4.5.x unusable).  I have *not* filed a bug report as I have no idea what broke or why.

Did you also get the X boot-crash-repeat issue?

---

### Post by PGHammer on 2010-09-07
> **BlueJayofEvil said:**
> Did you also get the X boot-crash-repeat issue?

Yep; rather painful that.

The odd thing is that only KDE was affected (GNOME on the same setup was fine).

---

### Post by sxmaxchine on 2010-09-07
a little bit of topic but does anyone know when the radeon drivers will support the mobility radeon hd 5650

---

### Post by BlueJayofEvil on 2010-09-07
> **PGHammer said:**
> Yep; rather painful that.

The odd thing is that only KDE was affected (GNOME on the same setup was fine).

I found a way to fix it but I'm not sure what I did. I'm doing a fresh install of Kubuntu Maverick Beta now to try and reproduce what I did.

UPDATE 1: Ok, it didn't happen this time. Here's what I did (in order) -
1) After a fresh install, open Konsole and enter **sudo apt-get update** then **sudo apt-get dist-upgrade**
2) Wait for updates to finish and do not install anything else after that (yet)
3) Reboot
4) All should have gone well. You can resume normal activity now

I'm thinking last time I tried installing some experimental updates before the reboot and that caused the issue in my case.

UPDATE 2: The bug happened again to me after I installed Xorg-Edgers and updated. I'm thinking it must be related to the experimental Xorg-related packages/drivers.

---

### Post by BlueJayofEvil on 2010-09-07
> **sxmaxchine said:**
> a little bit of topic but does anyone know when the radeon drivers will support the mobility radeon hd 5650

Radeon Evergreen drivers are just now gaining acceleration. 2D/3D acceleration will likely be in the default stack for 11.04.
If you want open-source acceleration sooner, you can keep track of Xorg-Edgers or compile from git. It's not very stable right now, so doing so would likely introduce many bugs on your system.

---

