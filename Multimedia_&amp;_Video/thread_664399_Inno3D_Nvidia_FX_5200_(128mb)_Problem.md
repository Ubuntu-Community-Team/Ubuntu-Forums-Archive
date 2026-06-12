---
title: "Inno3D Nvidia FX 5200 (128mb) Problem"
date: 2008-01-11
forum: Multimedia &amp; Video
---

### Post by strata8 on 2008-01-11
I'm trying to use my Nvidia FX 5200 (Inno3D), but the GNOME display manager won't load up at all. It goes past the loading screen and then some text comes up (against a black screen), the screen flashes, and then it finally tells me it can't load the Xwindow server. :confused:

I installed Nvidia drivers using recovery mode, they installed fine, but then nothing loaded at all after the loading screen, it was just a blinking underscore.  :-k

I've tried installing the drivers while ubuntu is working, but the FX overrides the intergrated video, and I can't install them while the card is out. :mad:

I also tried making the Intergrated the priority, but the option says 'Intergrated/AGP', and seeing that the card is an AGP, I can't see a way out of this other that a modified BIOS.

---

### Post by warbread on 2008-01-11
What drivers did you install?  It looks like you'll need the nvidia-legacy drivers and not the newer ones.

And, have you yet tried:

```
sudo dpkg-reconfigure xserver-xorg
```

?

Also, do you know what kernel version you're using?  You may have installed the wrong driver for the kernel.

---

### Post by strata8 on 2008-01-11
I dont' think its a driver problem, because a guide said that the intel intergrated chip will try to override a nvidia card. 

But I'll try it anyway. :)

Which driver version do I need? 1-0.9755 or 100.14.19? :confused:

---

### Post by warbread on 2008-01-11
Nevermind.  You don't need the legacies.  I would slap me silly if I were someone else.

Have you tried disabling the integrated graphics from BIOS?

---

### Post by strata8 on 2008-01-11
never mind, i just installed version 1-0.9755, and everything works perfectly :guitar:. I just also had to enable composite to get desktop effects working. :mrgreen:

---

### Post by Presario on 2008-03-02
hey, where did you get the driver? I'm having the ame problem as you beforeand my card is Inno 3D geforce FX 5200 128MB. My ubuntu boot get stuck at "loading hardware drivers".

It would be great if you were to provide the link. 

Thanks.

---

