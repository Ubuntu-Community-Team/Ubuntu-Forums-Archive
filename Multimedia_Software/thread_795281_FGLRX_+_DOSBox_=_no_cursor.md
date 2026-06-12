---
title: "FGLRX + DOSBox = no cursor"
date: 2008-05-15
forum: Multimedia Software
---

### Post by markekeller on 2008-05-15
I'd kind of like to install the [FONT="Monospace"]fglrx[/FONT] graphics driver, because 3D acceleration with the open-source [FONT="Monospace"]ati[/FONT] driver doesn't work too well (8-30 fps in Planet Penguin Racer, as opposed to 80 fps, if I remember right, the last time I tried it with [FONT="Monospace"]fglrx[/FONT]); and it has screen-refreshing problems with Blender.

However, there's one major (for me) problem - when I run DOSBox with [FONT="Monospace"]fglrx[/FONT], the DOS cursor doesn't work.  The mouse remains stuck to the lower right-hand corner of the screen, and thus is entirely nonfunctional.  Once I unfocus the cursor from DOSBox (Ctrl-F10), it works fine, of course, but within DOSBox, it doesn't.  Not Nice.

Anyone know how to fix this?

---

### Post by Gunman1982 on 2008-05-15
Does the mouse work when you use the ati driver instead of fglrx? Maybe try to turn of compiz too to test if the error origins there (which I doubt but anyway)

If the mouse sticks to one corner it sounds more like a problem with the mouse driver in dosbox. Or is just the appearance of the mouse cursor in the corner and you can click somewhere in a dos application like with a hidden mouse?

---

### Post by markekeller on 2008-05-15
Yes, it works fine with the [FONT="Monospace"]ati[/FONT] driver. I did have Compiz on when I ran it in [FONT="Monospace"]fglrx[/FONT], so perhaps that had some effect, but it works fine with [FONT="Monospace"]ati[/FONT] whether I have Compiz enabled or not.

The mouse cursor does appear to stick in the bottom of the DOSBox window (with [FONT="Monospace"]fglrx[/FONT]), but I don't think the mouse is actually moving around invisibly.

---

### Post by Gunman1982 on 2008-05-16
found something in the archive, don't know if it helps but its worth a shot I guess
[http://ubuntuforums.org/archive/index.php/t-187907.html]("http://ubuntuforums.org/archive/index.php/t-187907.html")

---

