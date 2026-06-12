---
title: "Gnome: 2D still a tad slow?"
date: 2006-07-31
forum: Multimedia &amp; Video
---

### Post by Robvdl on 2006-07-31
Hi, I am running Ubuntu 6.06 LTS, I have the following hardware working perfectly fine on it:

P4 2.8 HT (Using 686 kernel)
MSI 865PE Mobo, AGP 8x
NVidia GeForce FX 5600, 256Mb @ AGP 8x, SBA & Fastwrites
1024MB RAM, Dual DDR 400

I'm running the latest 686 kernel, tweaked the services, am running the latest NVidia drivers and have turned on SBA & Fastwrites.

Everything works fine and I am very happy with Ubuntu in general, however I still feel 2D graphics are a tad slow (Quake 3 for example works a dream), but 2D graphics (i.e. window rendering) in Gnome seems a lot slower than Windows was.

Are there any more ways to tweak the 2D graphics, is this because of the NVidia drivers, or because of the underlying X windows system?

Does compiling your own kernel make *that* much of a difference for 2D graphics or not really? What about getting a later version of X, will that help? Maybe I just have to wait for newer NVidia drivers?

Any clues or pointers on how to squeeze more 2D graphics performance out, I will be very grateful :p

---

### Post by evil_elman on 2006-08-01
Exactly the same behaviour from my Ubuntu installation.

I'm personally running i386 with a Mobility Radeon X600 instead. Running the Dapper i686 kernel is impossible on my laptop for some reason (it gets slow and unresponsive).

The funny things is that when I tried both SUSE, Mepis and Ubuntu Edgy the 2D performance is _vastly_ improved for some reason. I first noticed this when I tried SUSE but I'm not completely sure of the reason. These also worked fine with the i686 kernel...

3D has been flawless on all Linux installations I've tried so far...

---

### Post by Robvdl on 2006-08-01
Hey that's cool, gives me something to look forward to when Edgy comes out, so I'll just have to wait for now. all good things take time they say. I will continue using Dapper for now, even if the graphics are a little slower than Windows :-).

Next thing for me would be to try to figure out how to compile Freepascal from source and create .DEB files, I notice a lot of people have been asking for it in the forums, and there aren't any for Ubuntu, and the ones from Debian are old. It would be cool to become a package maintainer for Freepascal and Lazarus.

---

### Post by evil_elman on 2006-08-01
Well... You could try the Edgy Knot 1 'release' if you dare... ;-)

---

### Post by Robvdl on 2006-08-01
I would love to 'try' it out, but I'd rather wait because I use my PC for software development too. I successfully compiled Free Pascal for Ubuntu Dapper like I mentioned I was going to do in my above post. I have started a new thread for this , to anyone that may be interested:

[http://www.ubuntuforums.org/showthread.php?t=227501](http://www.ubuntuforums.org/showthread.php?t=227501)

---

### Post by Robvdl on 2006-08-05
I've found out that the 2D speed in Gnome is largely affected by the GTK theme/engine you use.

I downloaded another GTK theming "engine" called "Murrine" (there was a Dapper package), and a GTK theme to go with that "MurrinaCool", this greatly improved the speed Gnome apps are redrawn, as well as it gave me a really awesome looking theme 8) To top if off, I used the "Clearlooks Hack" metacity theme, and a modification of the icon set "Neu" (I mixed some Tango icons with it, for the icons I didn't like). The wallpaper I used came from Deviantart and was called _Sable_.jpg, I forgot the author I'm afraid as I saved the wallpaper a while back. I also made my own GDM to match the new theme.

Anyway, I am very happy with the speed improvements and as a bonus, having an awesome looking desktop. I am not sure why this theme is much faster (maybe because it says it uses Cairo, or maybe it is just written more optimally). Hopefully the default themes like Clearlooks, Human and Nature can be optimised for speed in the future too.

One thing I found is that gtk themes, icons, and metacity themes are better copied into the /usr/share directory, instead of the ~/.themes directory (which is what the theme installer does). The reason being, if you place them in the home folder and run an application as root, those applications won't get themed. However, if you place them in the /usr/share folder, they will get themed.

---

