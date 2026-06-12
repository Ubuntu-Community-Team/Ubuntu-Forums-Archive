---
title: "Cannot boot into X w/ ATI x800XL"
date: 2007-02-05
forum: Multimedia &amp; Video
---

### Post by zjd on 2007-02-05
Hi,

I aplogize for making yet another ATI thread but I this is my first attempt at installing Ubuntu and I've tried most of the solutions on these boards but I must be doing something wrong. I am running an ATI x800XL and I have never been able to boot or install using the LiveCD. Both times they begin by stating something about not being able to allocate resources to a certain device and the busID is that of my video card. Then at the load screen it usually gets about a tenth of the way done before becoming pixellated and freezing. I was able to boot the GParted LiveCD so I am hoping this problem is fixable.

After installing Ubuntu 6.10 through the alternate install in text mode I have been fooling around w/ the terminal in recovery mode. I have gotten my ethernet connection working and have done all the updates. I have tried to change to the fglrx drivers by doing this: 
```

sudo apt-get install xorg-driver-fglrx

sudo depmod -a

sudo aticonfig --initial

sudo aticonfig --overlay-type=Xv
```

in xorg.conf I also added:
```

Section "Extensions"
            Option "Composite" "Disable"
EndSection
```

I then restart but am still having the same problems. Also when I try "fglrxinfo" in the terminal I get "Error: unable to open display"

Sorry for making this desperate post but I am at a dead end as to what to do. Thanks for any help!

---

### Post by Detson on 2007-04-05
I had the same problem, although my main issue was getting fglrx installed. I ended up going to /etc/X11/xorg.conf and changing the driver to 'radeon' and removing all resolutions except 800x600 at depth 24. It worked on the first try. Once in gnome I updated all my packages and switched the driver to fglrx.

---

