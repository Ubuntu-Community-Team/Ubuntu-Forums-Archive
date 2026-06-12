---
title: "Installed FGLRX now screen is all white and Ubuntu does nothing"
date: 2009-10-26
forum: Multimedia Software
---

### Post by dorush on 2009-10-26
Hi,

I just installed FGLRX in the hope that it would make my Radeon HD4800 (or something) video card a bit faster. But instead it totally screwed ubuntu. I can go to recovery mode with no problems, but when I start ubuntu normally I get freckles, and then an all white screen. I don' t hear the login sound either...

Im using ubuntu 9.04, AMD chipset/triplecore

Excuse my for my newbiness :(
How do I go back to my original settings? Let's say uninstall FGLRX via the recovery mode?
Or any other way, everything is appreciated..!

greetings,

Dorush

---

### Post by dorush on 2009-10-26
Pfffeew, I have mixed feelings. I feel bad for posting this topic, and VERY happy that I solved it so quickly, and that I solved it at all ^^

This post was the answer to my problem:
> **cadwill said:**
> I'm having the same problem with the ATI 2400 pro card, and had to re-install ubuntu a couple times before I tried booting in the repair mode and trying
sudo apt-get remove --purge xorg-driver-fglrx
or 
sudo apt-get remove xorg-driver-fglrx fglrx-kernel-source

then sudo apt-get update
and run
sudo dpkg-reconfigure xserver-xorg

It gets me back into safe graphics mode, so I can try something else (still working on getting the graphic card to work!) at least and saves me from the entire reinstall. I'm sure others know more about this, but good luck.

Solved :)

---

### Post by Zoot7 on 2009-10-26
Just to add if it's any good to you. Here's a good guide to get fglrx up and running using a packaged based install. Following these steps got Catalyst 9.8 up and running flawlessly on my HD4870 under Hardy and then Jaunty for me.

[http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

---

### Post by markbuntu on 2009-10-28
I just run the installer myself and have had no problems for a long time with any generic kernels from Hardy(which I still use) to Jaunty, except with the rt or custom built kernels which...well I will no go into that, it is a long nightmarish story.

Be sure to run the usr/share/ati/uninstall-fglrx.sh before installing a new driver or you will have problems with kernel updates, guaranteed.

---

### Post by Zoot7 on 2009-10-29
> **markbuntu said:**
> I just run the installer myself and have had no problems for a long time with any generic kernels from Hardy(which I still use) to Jaunty, except with the rt or custom built kernels which...well I will no go into that, it is a long nightmarish story.
Ditto that. Took me a long time to get 2.6.30 up and running under my home built desktop, the fglrx driver being the source of the problems. I'm thinking of picking up maybe a GTX 260 or GTX 275 as a result, it'll all depend on how the fglrx plays under Karmic for me.

---

### Post by markbuntu on 2009-10-30
Karmic comes with the catalyst 9.10 which does work with the .30 and .31 kernels as will future drivers. I had 9.10 working with the 2.6.31-8rt kernel for a while after an update that patched the kernel but not with the newer 2.6.31-9 rt kernel that is in karmic/ubuntustudio...sigh...I think the ubuntustudio devs are reluctant to implement the patch for whatever reason... 

It took almost a year to get the fglrx rt patch put in the proper directory in fglrx so the kernel modules would build properly with the rt kernels(/patches instead of /patches/patches) but that was the fglrx package maintainers fault.

---

