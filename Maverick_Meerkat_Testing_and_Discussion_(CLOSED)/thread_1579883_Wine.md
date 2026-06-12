---
title: "Wine"
date: 2010-09-22
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Yrvyne on 2010-09-22
After upgrading to 10.10 (from 10.04), wine has encountered issues.  

My problem is that "A debugger has been found running in your system.  Please, unload it from memory and restart your program."

Any help is much appreciated,
Thank you.

---

### Post by Vigh on 2010-09-23
Upgrading can break particular packages that had previously been installed.

Open terminal-
type

sudo apt-get remove --purge wine

sudo apt-get install wine
restart

try running your wine programs again, dont worry your installed wine programs should remain, it is simply refreshing the wine program by doing that

---

### Post by Yrvyne on 2010-09-24
I did the two steps mentioned but the result was the same, I got that notice again...

also, I trid to uninstall the wine from the applications/wine/uninstall wine and a dialog box appeared giving me options to uninstall the programs I put on the wine layer...

is there anything else I can do as I see no other way than to completely remove wine and its installs

thank you very much
:)

---

### Post by Vigh on 2010-09-24
You could.....

try the same thing again purge the installation

but instead when you go to reinstall type

sudo apt-get install wine1.2

which will install maverick version of wine

---

### Post by Yrvyne on 2010-09-24
Did that and the same pop up appeared...

so, notepad, works, 

web album generator works

only the game Battle of the Immortals gives me the afore mentioned popup,

guess i should uninstall the game, right?

---

### Post by Vigh on 2010-09-24
Hey mate, sounds like a config issue with that particular program. Try doing a google for the program followed by WINE HQ. Someone may have already worked out how to get it working. But first try, backing up any saved games you may have, uninstalling the game through wine uninstall, reinstalling the game through wine install.

thats the url you want there- [http://appdb.winehq.org/objectManager.php?sClass=version&iId=20196](http://appdb.winehq.org/objectManager.php?sClass=version&iId=20196)

looks like they have got it working, follow the tips, click on the different setups and try combining all the tips and hopefully the game will run

looks like it was working perfectly through wine by the way, however you may need to upgrade to wine-1.3.1, i can explain how to do this if you require assistance

---

### Post by movieman on 2010-09-24
> **Yrvyne said:**
> only the game Battle of the Immortals gives me the afore mentioned popup,

Some Windows games refuse to run if they think they're in a debugger: which used to make debugging hardware driver incompatibilities real exciting when they involved one of those games.

I presume something that Wine is doing is triggering whatever bizarre, nonstandard and unreliable check they're performing to try to see if it's running in a debugger.

---

### Post by Yrvyne on 2010-09-24
[LIST]
[*]Uninstalled wine
[*]Installed wine 1.3 from their website
[*]uninstalled game
[*]installed game again
[*]several restarts and updates
[*]ran the game
[*]dreaded message appears again
[/LIST]

so what must i do to overcome this windows/ubuntu debugger thing?

thanks guys for your help

---

