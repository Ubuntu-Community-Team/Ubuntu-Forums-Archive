---
title: "WOL weird behavior depending on how i suspend the computer"
date: 2010-02-09
forum: Networking &amp; Wireless
---

### Post by dislodge112 on 2010-02-09
i have some odd behavior happening, i'd like to get some opinions to help troubleshoot.  the gist is that WOL works, but after waking the machine it is only usable through SSH.

specifically, if i use ```
acpitool -s
``` to put the computer to sleep (remote or local), then i can use WOL to wake it up, but when i do this the actual desktop does not come back fully to an awake state.  essentially, after waking up i can still ssh to the machine and use it, but the monitor stays off no matter what (press power button, keyboard, move mouse...).

if i use the menu in gnome to put the computer to sleep (suspend), then WOL doesn't work, but when i press the power button to wake it up it comes back to a fully usable state.

using karmic koala ubuntu 9.10 x64 linux v 2.6.31-19-generic

any help appreciated, thanks!

---

