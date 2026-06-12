---
title: "LibreOffice Min/Max buttons not loading 11.04"
date: 2011-04-19
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by lancest on 2011-04-19
When opening up a previous document or presentation, Unity often does not display the Libreoffice Min/Max buttons. Seen on varied hardware. 
11.04 64 bit, fully updated

---

### Post by ELD on 2011-04-19
I also have this issue, sometimes they are there and other times they are not, frustrating.

---

### Post by beew on 2011-04-19
Yep, same problem here. I think it has to do with the global menu. In order to push the global menu they have to make adjustments to the menu and panel system and now as a result these features are all broken and buggy: no tray icons for applications, no panel applets, menus behave strangely, missing max/min buttons etc. 

Why the hell do they think the global menu is so great other than the MAc has it? It is a pest and a bad design even if it works as intended and is implemented bugs free.  There may be some advantage (the only possible advantage) for netbooks which could gain some small space on top and that's it.

---

### Post by terry_gardener on 2011-04-19
i raised a bug for this while ago. 

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/703278]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/703278")

---

### Post by grahammechanical on 2011-04-19
When this happens to me I just click the Ubuntu icon which brings up the program search thingy (don't know what the offical name is). Then I click it again to disappear the thingy and the maximise/minimise/shutdown buttons of the program appear in the top panel.

Regards.

---

### Post by beew on 2011-04-20
Just updated LO about 5 minutes ago, this seems to be fixed.

EDITED: Oops, spoke too soon, still no max/min button if LO opened maximized.

---

### Post by beew on 2011-04-20
The odd things is those buttons show up if I switch to another desktop and switch back (with alt + left/right) This is very annoying.

---

### Post by lancest on 2011-04-20
Did update- not fixed. Detracts from Unity's goodness. Hope it gets fixed.

---

### Post by beew on 2011-04-20
Tested on two machines, same behaviour. No max/min button if LibreOffice opens maximized. The buttons show up after switching desktop and back by rotating the cube (I have cube enabled in unity) (**EDITED:** switching with Unity bar's "workplace switcher" also works) If LibreOffice opens unmaximized then the buttons are present.

I should add that I have gotten rid of the global menu by removing indicator-appmenu but I don't have similar problems with other applications.

---

### Post by kaldor on 2011-04-20
This has been happening on and off for me since before Beta 1. I find reloading it can sometimes help, but others not.

However, this issue does not exist using Unity-2d on Ubuntu 10.10's PPA.

---

