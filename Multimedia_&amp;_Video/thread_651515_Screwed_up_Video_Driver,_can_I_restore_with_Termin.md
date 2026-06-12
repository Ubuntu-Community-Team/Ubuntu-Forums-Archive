---
title: "Screwed up Video Driver, can I restore with Terminal?"
date: 2007-12-27
forum: Multimedia &amp; Video
---

### Post by dillonish on 2007-12-27
So I was unintelligently toying with the system options under Administration, came to a section on Video Drivers... 

There was (obviously) something already in use, but I clicked some little box that said "Find by Model" or something like that, scrolled to find my graphics chip (the driver name in the box changed) and I hit OK. It then told me to log out for changes to take effect. 

So I hit logout and nothing loads anymore.
Just a couple text lines that flicker twice and then stop doing anything. The last line says something like "loading Boot scripts [OK]" and then there's a little insert space and I can type, etc, but nothing happens so I have to shutdown.

I'm pretty sure I enabled a driver incompatible with my chip.

I need a way to restore the default driver. I can boot into "Recovery Mode" and it gives me Terminal, so I figure that's what I need to accomplish my task.

Thanks for the help!

---

### Post by Yellow Pasque on 2007-12-27
Hit Ctrl+Alt+F1 when you get stuck at the "Boot Scripts" part.

If it's an ATI card, and you were using the restricted drivers, run:
```
sudo aticonfig --initial --overlay-type=Xv
```

Otherwise, this should work for you:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by dillonish on 2007-12-27
> **Temüjin said:**
> Hit Ctrl+Alt+F1 when you get stuck at the "Boot Scripts" part.

If it's an ATI card, and you were using the restricted drivers, run:
```
sudo aticonfig --initial --overlay-type=Xv
```

Otherwise, this should work for you:
```
sudo dpkg-reconfigure xserver-xorg
```

Whoops forgot to specify, its an Intel GMA X3100 (GM965 chipset). Well, anyways, i'll try those commands and edit this post with an update...

---

