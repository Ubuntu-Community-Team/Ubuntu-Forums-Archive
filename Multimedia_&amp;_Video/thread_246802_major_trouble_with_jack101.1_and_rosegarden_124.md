---
title: "major trouble with jack101.1 and rosegarden 124"
date: 2006-08-29
forum: Multimedia &amp; Video
---

### Post by zettberlin on 2006-08-29
Hello,

today i had decided to make some upgrades and installed new versions of jackd and rosegarden from recent sources. Both gave mixed results:

jack started OK(showed no hints regarding any problems) but allowed no clients to connect. Starting the clientapps as root via sudo did not help. As i restart qjackctl with /usr/bin/jackd the older version from synaptic worked OK again. 

Rosegarden123 showed weired behaviour when i did some bigger GUI-Stuff like opening windows or switching desktops so i built/installed rg as well in the recent version 124 and these annoyances where gone. But now rg does not find the running jackd anymore (even though it triggers Zynaddsubfx-that is connected to jackd whithout any complaints) furthermore all the pluginsynths are gone - no dssi, no vst anymore...

is there anybody out there, that has had  these problems too (and maybe solved them :-))?

---

### Post by dolson on 2006-08-30
You are braver than I. :)

I would probably switch to a source-based distro for things like that, to be honest. Not that I'm suggesting that.

---

