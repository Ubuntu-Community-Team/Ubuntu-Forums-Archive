---
title: "Installing Mythbuntu on a laptop with a broken monitor; No Signal on TV monitor"
date: 2011-07-31
forum: Mythbuntu
---

### Post by justin.romaine on 2011-07-31
Patial linux n00b. installed Mythbuntu on a laptop with a stuffed monitor (back light blown).
Though i could use my Bravia as the main monitor for the device via VGA port.
Install went fine using TV as monitor but on inital boot after install monitor shows "no signal" at around logon, screen init time.
I figured this was just an issue with the monitor selection so i found a way to move the monitor to the exteral device. 
Section "Screen"
[INDENT][/INDENT]Option		"UseDisplayDevice" "CRT"

Although this seems to select the monitor, i never get to the login screen.
It just sits on boot up Mythbuntu splash screen and no keyboard action responds including Alt-Ctrl-F1 or Ctrl-Alt-Del

I suspect the device is crashing somehow.

I can get back in using F6 and navigating to root console but i cant get the screen system up.

System:
Toshiba Tecra
nvidia g72m

Any help would be appreciated.
Cheers.

---

