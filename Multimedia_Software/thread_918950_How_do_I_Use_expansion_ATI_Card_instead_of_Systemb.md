---
title: "How do I Use expansion ATI Card instead of Systemboard Intel Card?"
date: 2008-09-13
forum: Multimedia Software
---

### Post by jalfan on 2008-09-13
I have a motherboard with an on-board Intel Graphics card,but I want to use my ATI Radeon 9250....

I have tried installing the drivers for the ATI but I don't know how to Switch to using the ATI instead of the Intel.

There is no place in my BIOS to disable my onboard Intel card, but I can have the ATI  (PCI) card as first boot device... the only problem is that when I chang the ATI to be primary my system won't boot, the kernel crashes or something.

I had to switch to the Intel card in order to install the OS (same problems when ATI was primary)

Is there a utility or a config file somewhere I can edit to get this changed?


I am on Xubuntu's latest release as of now..
(p.s. I think I would like to change it back to normal Ubuntu and Gnome instead of Xfce, can someone direct me to the right thread?)


Thanks, 

The Jalfan

---

### Post by cariboo on 2008-09-13
Start up in recovery mode and choose xfix from the menu that appears.

Jim

---

### Post by jalfan on 2008-09-13
> **cariboo907 said:**
> Start up in recovery mode and choose xfix from the menu that appears.

Jim
I tried that xfix, but when I try to boot using my ATI Expansion card the OS still won't boot.

I tried booting into recovery mode with the ATI Card set as primary, but after the Grub loads and I select the recovery mode (or try to boot into Xubuntu) I get the following:

init: rc-default main proocess (3937) killed by SEGV signal

I also get: 

init: rcS-sulogin mainprocess (3922) terminated with status 127

I ran the xfix from recovery mode with my Intel as the primary and it did its stuff, but when I try to boot into linux with the ATI set as the primary I also get the following:

tty1 respawning too fast, stopped

The above comments are surrounded by all sorts of other output:

[     43.247082] etc. etc.

I assume that most of the information above means almost nothing, but I though I would post it in any case.

I am not familiar wiht all the utilities that are available for Linux as I have not been able to use the OS for quite a while.

I would like to get this Video card working if there are any other suggestions.

Thanks, 

The Jalfan

---

### Post by jalfan on 2008-09-14
Well, I was able to get my ATI Expansion Graphics card working by using the "Configure" button when Ubuntu started in Low Resolution Mode.  It did see my graphics card and I was able to set it as the default screen.

So I checked my xorg.conf file and found that it want to use the "ati" driver for the screen, which works, but only for most graphics.

Some games like openarena, warzone2100 and one of my online games Runescape, either won't open or (for runescape) say that my monitor has too few Textile somethings in order to work and that I have to use the low-graphics mode.  Arrrr! 

If anyone has an ATI 9200 (mine is 9250) let me know what driver is best to use so I can try and get that one.... thanks.

---

