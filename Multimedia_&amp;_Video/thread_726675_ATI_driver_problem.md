---
title: "ATI driver problem"
date: 2008-03-16
forum: Multimedia &amp; Video
---

### Post by cuulcars on 2008-03-16
Oh, the infamous ATI graphics card on linux. It never seems to work for anyone. I've searched other threads, and they've been having problems, just not the same as mine. I have a adequate graphics card, yet 3D software like Nexuiz and Celestia go slowly, and some 3D programs on my PC don't even run at all. I enabled my restricted drivers, but all that did was make ubuntu not display anything after start-up (just a blank, black screen). I eventually had to go into the recovery mode listed on GRUB and put in:

```
sudo dpkg-reconfigure server-xorg
```

and it messed up my xorg.conf file and I can't deactivate the restricted driver (although for some reason its got the check mark, but its disabled).

I honestly really have no idea what to do.

---

### Post by Poleh on 2008-03-17
I too have had so many probs with ATI drivers and no amount of following instructions fixed it for me.

The good news is that there is an awesome tool that does it for me every time, including 3 recent upgrades: [Envy]("http://www.albertomilone.com/nvidia_scripts1.html")

Hope this works out for you as it did for me. Good luck!

---

### Post by cuulcars on 2008-03-17
It still didn't work. All it did was make my computer go blank after startup (right before the GDM screen) and I had to go into recovery mode and do

```
sudo dpkg-reconfigure server-xorg
```

again. BTW, I have a Radeon x1600 Pro if that helps any.

---

### Post by Melcar on 2008-03-17
I hope that's not an AGP card.  Last I heard, the current drivers did not work on some AGP cards.

---

### Post by cuulcars on 2008-03-17
Thats exactly what it is... dang. So theres no hope?

---

