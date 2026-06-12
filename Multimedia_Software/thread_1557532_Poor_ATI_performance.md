---
title: "Poor ATI performance"
date: 2010-08-20
forum: Multimedia Software
---

### Post by tnenad on 2010-08-20
Months before, I installed Ubuntu 8.04. I installed graphics drivers for ATi (followed a guide for it), and I remember that after I installed it, I rebooted and the screen was like this:
[URL="http://i35.tinypic.com/52avt5.png"]
[IMG]http://i35.tinypic.com/52avt5_th.png[/IMG][/URL]

After that I uninstalled ubuntu.
I heard that there aren't "good" ATi drivers for the 10.04.
My ATi card: Radeon 9600

I reinstalled and after that I tried another drivers (xorg i think), and I was able to launch Warcraft 3 (don't tried Counter Strike) but I remember that it runned very slow and with very low fps...

The problem must be because "bad" drivers. I can play both of these games on XP smoothly with max graphics settings.

The best would be if you give me a solution for this.
I want to install ubuntu with proper graphics driver so I don't have to install XP just because 2 games.

I hope that you understand me and I'm sorry for my bad grammar.

---

### Post by xelasha on 2010-08-21
Make sure proprietary drivers are installed.

System>Administration>Hardware Drivers.

---

### Post by peterthewolf on 2010-08-21
Have installed drivers via ati installer 10 but still no driver as far as ubuntu 10.4 knows. What am I missing.

---

### Post by Icarus315 on 2010-08-21
> **tnenad said:**
> After that I uninstalled ubuntu.
I heard that there aren't "good" ATi drivers for the 10.04.
My ATi card: Radeon 9600

The issue is that in Ubuntu 10.04 a newer version of what is called the "X Server" or "graphical desktop" is used.  This version is not compatible with Ati's Legacy drivers.  Pre-Radeon HD 2000 series are considered legacy.  Your 9600 is legacy.  Since Ubuntu has changed too much since Ati last updated their legacy drivers you cannot use Ati's proprietary drivers.  Therefore, you must use the Open-Source or built-in drivers.  These drivers are improving all the time but in general they are not that great for gaming at the moment.

---

### Post by tnenad on 2010-08-21
Thank you for answers.
What you think, (when) will ATi make proprietary drivers for 9600?

---

