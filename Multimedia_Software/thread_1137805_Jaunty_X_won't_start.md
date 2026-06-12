---
title: "Jaunty X won't start"
date: 2009-04-25
forum: Multimedia Software
---

### Post by lambdacore on 2009-04-25
first off, yes i googled and checked the forums and i didn't find anything that worked.

so i installed Jaunty yesterday, and all went well (i'm on a laptop and it seems that everything was running even faster than before). but then i plugged my laptop in my tv to watch a movie and it didn't work. 

i thought it might be the drivers, so, using Envy-ng, i installed the recommended ATI drivers (that's what i always did on that laptop and it always worked). then i rebooted and, upon the login screen, there are only like two small ubunto logos, green, barred and the upper screen if all fuzzy : my X is *****d up.

i rebooted in recovery mode and then root shell.
i looked at my xorg.conf and, strangely, most of it was gone. i tried dpkg-reconfigure -phigh xserverblablabla. didn't work.

i then tried to use some backup xorg.conf that were there. there was a couple from yesterday and before i changed the graphic drivers. so i thought using one of them might work. it doesn't.

TL : DR : so when i boot, the display bugs and freezes and using old xorg.conf backup doesn't work.

i'm at a loss here.

---

### Post by lambdacore on 2009-04-26
ah, it's k.

i did a lot of ati drivers intensive removal/purge.
then deleted my current xorg.conf and used a somewhat older.

i reinstalled the drivers. 
reboot.
????
PROFIT

---

### Post by DitchingMS on 2009-06-10
Hi, I have a similar problem, not getting anywhere, my post is at [http://ubuntuforums.org/showthread.php?p=7431645](http://ubuntuforums.org/showthread.php?p=7431645)
 
Help Please?!

---

