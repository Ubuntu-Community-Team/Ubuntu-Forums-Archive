---
title: "Switch Graphics Drivers"
date: 2009-02-08
forum: Multimedia Software
---

### Post by baudday on 2009-02-08
I'm really not sure if this is something that can be done easily, and maybe there's a better way to achieve what I am looking for. Either way, I would really appreciate some help on this.

At first I had trouble setting up dual monitors in Ubuntu. I have an ATI Radeon Platinum X850 card. So the problem was that I was using fglrx, and trying to do Big Desktop with the Catalyst Control Center. So this was not working for me. So I followed this guide < [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) >, and was able to set up dual monitors successfully. But now I try to run WoW, which I was able to successfully run with the fglrx drivers, and it's just awful. 

My question is:
Is there a way I can switch between drivers easily? Or else, does someone know of a guide or something I can follow to successfully get dual monitors to work using fglrx and Catalyst Control Center and Big Desktop. Else, does anyone have any other suggestions of how I can solve this dilemma? 

Thanks

---

### Post by baudday on 2009-02-08
bump

---

### Post by Melcar on 2009-02-08
The beauty of open source drivers is that they're so easy to switch on and of.  It really is awesome.  However, since you're planning to install fglrx again, I would recommend cleaning your entire xorg.conf and start fresh.  Open a terminal and type the following:

```
sudo dpkg-reconfigure xserver-xorg
```

Follow the on-screen  instructions (simply accept the default values, unless you want to specify them yourself).  This will revert X to the default settings and generate a new xorg.conf.  Now simply ctrl+alt+backspace to restart X, and proceed to install fglrx (either do it manually or simply check the box in the hardware drivers box).  If you ever want to go back to the open source drivers simply uninstall fglrx (how depends on how you installed them) and rebuild X again like above, which will load radeon by default (or you can edit xorg.conf just to make sure).

---

### Post by baudday on 2009-02-09
I appreciate the help. I suppose this is about as easy as it gets. I was hoping there would be some kind of easy way I could swap between each other. Since I plan on playing the game at least a couple times a week, it would be really inconvenient to continually install and uninstall in that way. I guess I'll just have to abandon the dual monitors. Thanks again for the help.

---

