---
title: "Lost 3D capability.... trying to aoid complete reinstall"
date: 2008-06-29
forum: Multimedia Software
---

### Post by djmoore85 on 2008-06-29
Hey yall, here's what happened. I had Compiz running perfect, the ATI catalyst and driver runnin fine for 3D rendering to be able to run cairo-dock and the cube and all that wonderful stuff, then I did something bad. I went to add a second monitor, just to play around with it cause I couldn't leave well enough alone, and now I have some real problems. I cannot get the ATI catalyst to work properly at all, I have lost my 3D rendering, and the ATI driver I downloaded from the ATI site weeks ago when I got it all working is no longer installing properly. My question is this: is there a way to completely remove all of ATI's stuff and reset all the display things to a barebones fresh install without actually reinstalling Hardy and starting from scratch? I tried ```
dpkg-reconfigure -phigh xserver-xorg
``` already with no satisfactory results. Any help is much appreciated, I am lost on where to go next

---

### Post by pytheas22 on 2008-06-29
It might help to use [envy]("http://www.albertomilone.com/nvidia_scripts1.html") and tell it to automatically configure your ATI card.  Install envy with:
```

sudo apt-get install envyng envyng-gtk
```

then run it with:
```

sudo envyng-gtk
```

and select the option for auto-configuration.  Envy's usually pretty smart about what it does and might be able to solve the problem on its own.  In a worst case, envy provides a go-back option, so you can always undo any changes it makes.

---

