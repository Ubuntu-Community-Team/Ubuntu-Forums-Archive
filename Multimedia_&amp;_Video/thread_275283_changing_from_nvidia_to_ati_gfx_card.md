---
title: "changing from nvidia to ati gfx card"
date: 2006-10-11
forum: Multimedia &amp; Video
---

### Post by daylight on 2006-10-11
recently i bought a brand new radeon x550 graphic card(pci-e) and now my ubuntu doesnt boot successfully.

previously i was using the onboard nvidia gfx 6100, which works fine on ubuntu 6.06.

how do i make my ati gfx card work ?
how do i uninstall my old nvidia drivers and install new ati drivers so that my radeon card can work ?

---

### Post by bigken on 2006-10-11
boot into single user mode and type sudo dpkg-reconfigure xserver-xorg
and select ati as your driver ;)

---

### Post by tseliot on 2006-10-11
> **bigken said:**
> boot into single user mode and type sudo dpkg-reconfigure xserver-xorg
and select ati as your driver ;)

Exactly.

Boot in RECOVERY MODE from the GRUB Menu (select it using your keyboard) almost as soon as you turn on your computer (it will take you to the command line).

Then you will need to type:
```
dpkg-reconfigure xserver-xorg
```

and select the "ati" driver. Press ENTER whenever you don't know the answer to a question.

Type:
```
reboot
```

On next reboot the Xserver should work fine

---

### Post by daylight on 2006-10-13
tks.
it works after i followed the instructions given.

---

### Post by ubuntuross on 2007-02-28
Many thanks.  This saved my bacon!

---

