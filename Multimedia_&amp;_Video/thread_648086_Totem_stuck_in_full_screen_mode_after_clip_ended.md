---
title: "Totem stuck in full screen mode after clip ended"
date: 2007-12-23
forum: Multimedia &amp; Video
---

### Post by raydar on 2007-12-23
A few times now I've had a movie finish in Totem in full screen mode, and Totem refuse to go back to windowed mode.  When I move the mouse, the hidden controls appear, but clicking the one to leave full screen mode only shows me a flash of desktop before returning me to full screen mode.  I have to F4 to close Totem.  

Anyone else have this happen on occasion?

---

### Post by sharris203 on 2007-12-29
yes, me, right now. i'm searching for the answer...
update: fixed!
Open  terminal and enter:

metacity --replace

Then, go to Prefs>Appearance and re-enable visual effects (if you had them on).
Worked for me.

---

### Post by loell on 2007-12-29
i think its a bug, one work a around could be , is to press **esc** indefinitely until it returns to normal mode.

---

### Post by Lemon on 2008-01-11
> **sharris203 said:**
> yes, me, right now. i'm searching for the answer...
update: fixed!
Open  terminal and enter:

metacity --replace

Then, go to Prefs>Appearance and re-enable visual effects (if you had them on).
Worked for me.

I had the same problem, and this solved it :)

---

