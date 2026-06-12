---
title: "Screen goes black in Mythbuntu 8.10"
date: 2008-11-12
forum: Mythbuntu
---

### Post by Neofree on 2008-11-12
Hello,

I just booted up the Mythbuntu 8.10 install CD on a system that worked fine with 8.04.  It has a Nvidia GeForce FX 5200 video card.  After the splash screen with the scrolling bar thing the monitor just shuts off.  Isn't there a way to boot into a safe graphics mode?  

Thanks,

Neofree

---

### Post by mrand on 2008-11-13
> **Neofree said:**
> Hello,

I just booted up the Mythbuntu 8.10 install CD on a system that worked fine with 8.04.  It has a Nvidia GeForce FX 5200 video card.  After the splash screen with the scrolling bar thing the monitor just shuts off.  Isn't there a way to boot into a safe graphics mode?  

Thanks,

Neofree

You can change the command line options and turn off quiet mode (as well as the splash screen) and maybe seen what is going wrong.  The 5200 is a pretty standard card, so I'd kinda suspect something else.

Also, can you switch to a terminal console (Ctrl-Alt-F1)?

[INDENT]Marc[/INDENT]

---

### Post by Neofree on 2008-11-15
Sorry to be a newb..  how do I change the command line options?

It's been a couple days but I dont think CTR-ALT-F1 worked..

can try later..

Thanks!

Neofree

---

### Post by mrand on 2008-11-18
> **Neofree said:**
> Sorry to be a newb..  how do I change the command line options?

It's been a couple days but I dont think CTR-ALT-F1 worked..

can try later..

Thanks!

Neofree

Launch your kernel from grub without "quiet splash".
If you can't figure out how to do it manually, you can edit /boot/grub/menu.lst and change it there.

Also, does selecting "recovery mode" in grub at boot-up not work?

[INDENT]Marc[/INDENT]

---

### Post by Neofree on 2008-12-03
Thanks for the reply... I just finally got around to trying this again..

I tried to boot again and it wouldn't even boot... So I burned the CD again at a lower speed and now I am not having any trouble.  It's installing right now..  

Thanks,

Neofree

---

